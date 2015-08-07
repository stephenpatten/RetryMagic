# RetryMagic

What is RetryMagic?
--------------------------------
A c# library to retry code with a truncated binary exponential backoff algorithm

[![Build Status](https://img.shields.io/appveyor/ci/JorritSalverda/RetryMagic.svg)](https://ci.appveyor.com/project/JorritSalverda/RetryMagic/)
[![NuGet downloads](https://img.shields.io/nuget/dt/RetryMagic.svg)](https://www.nuget.org/packages/RetryMagic)
[![Version](https://img.shields.io/nuget/v/RetryMagic.svg)](https://www.nuget.org/packages/RetryMagic)

Why?
--------------------------------
To make more robust applications make sure to retry any external call, whether it's a database call or a web request. The truncated binary exponential backoff algorithm is used to avoid congestion and is truncated/capped by default to keep the maximum interval within reason

Usage
--------------------------------
You can retry either an Action or a Func<T>

```csharp
Retry.Action(() => { _databaseRepository.Update(databaseObject); });
```

```csharp
Retry.Function(() => { return _databaseRepository.Get(id); });
```

### Changing defaults

The following defaults are used and can be changed by using the following code with different values

```csharp
Retry.DefaultMaximumNumberOfAttempts = 8;
```

```csharp
Retry.MilliSecondsPerSlot = 32;
```

```csharp
Retry.Truncate = true;
```

```csharp
Retry.MaximumNumberOfSlotsWhenTruncated = 16;
```

Get it
--------------------------------
First, [install NuGet](http://docs.nuget.org/docs/start-here/installing-nuget). Then, install [RetryMagic](https://www.nuget.org/packages/RetryMagic/) from the package manager console:

    PM> Install-Package RetryMagic

RetryMagic is Copyright &copy; 2015 [Jorrit Salverda](http://blog.jorritsalverda.com/) and other contributors under the [MIT license](LICENSE.txt).