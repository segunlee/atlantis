![Atlantis: Debug iOS with ease](https://raw.githubusercontent.com/ProxymanApp/atlantis/main/images/cover.png)

A little and powerful iOS framework for intercepting HTTP/HTTPS Traffic from your app. No more messing around with proxy, certificate config. 

## Features
- [x] Automatically intercept all HTTP/HTTPS Traffic with ease
- [x] No need to config HTTP Proxy, Install or Trust any Certificate
- [x] Review traffic log from [Proxyman](https://proxyman.io)
- [x] Categorize the log by project and devices.

## How to use
- Integrate Atlantis with one single line of code:

```swift
// Intercept all traffics and send to Proxyman app
Atlantis.isEnable = true
```

- We suggest to enable Atlantis only in Debug environment
```swift
#if DEBUG
Atlantis.isEnable = true
#endif
```

## Requirement
- macOS Proxyman app 2.11.0+ (Release soon)
- iOS 12.0+ / macOS 10.12+
- Xcode 11+
- Swift 5.0+

## Install
- Add the following line to your Podfile

```bash 
pod atlantis
```

## FAQ
#### 1. How does Atlantis work?

Atlantis uses [Method Swizzling](https://nshipster.com/method-swizzling/) technique to swizzle certain functions of NSURLSession and NSURLConnection that enables Atlantis captures HTTP/HTTPS traffic on the fly.

Then it sends to [Proxyman app](https://proxyman.io) for inspecting later.

#### 2. How can Atlantis stream the data to the Proxyman app?

As soon as your iOS app (Atlantis is enabled) and the Proxyman macOS app are the same **local network**, Atlantis could discover the Proxyman app by using [Bonjour Service](https://developer.apple.com/bonjour/). After the connection is established, Atlantis will send the data via Socket.

#### 3. Is it safe to send my network traffic logs to the Proxyman app?

It's completely **safe** since your data is locally transferred between your iOS app and the Proxyman app, no Internet is required. All traffic logs are captures and send to the Proxyman app for inspecting on the fly. 

Atlantis and Proxyman app do not store any of your data on any server.

#### 4. What kind of data that Atlantis capture?

- All HTTP/HTTPS traffic from your iOS apps, that integrate the Atlantis framework 
- Your iOS app name, bundle identifier, and small size of the logo
- iOS devices/simulators name and device models.

**All the above data are not stored anywhere (except in the memory)**. It will be wiped out as soon as you close the app. 

They are required to categorize the traffic on the Proxyman app by project and device name. Therefore, it's easier to know where the request/response comes from.

## Credit
- FLEX and maintainer team: https://github.com/FLEXTool/FLEX
- @yagiz from Bagel project: https://github.com/yagiz/Bagel

## License
Atlantis is released under the Apache-2.0 License. See LICENSE for details.

