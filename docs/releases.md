# Release notes
Binaries for all releases can be found on the GitHub releases pages for the [ntfy server](https://github.com/binwiederhier/ntfy/releases)
and the [ntfy Android app](https://github.com/binwiederhier/ntfy-android/releases).

## ntfy server v1.16.0
Released Feb 27, 2022

**Features & Bug fixes:**

* Add [auth support](https://ntfy.sh/docs/subscribe/cli/#authentication) for subscribing with CLI (#147/#148, thanks @lrabane)
* Add support for [?since=<id>](https://ntfy.sh/docs/subscribe/api/#fetch-cached-messages) (#151, thanks for reporting @nachotp)

**Documentation:**

* Add [watchtower/shoutrr examples](https://ntfy.sh/docs/examples/#watchtower-notifications-shoutrrr) (#150, thanks @rogeliodh)
* Add [release notes](https://ntfy.sh/docs/releases/)

**Technical notes:**

* As of this release, message IDs will be 12 characters long (as opposed to 10 characters). This is to be able to 
  distinguish them from Unix timestamps for #151.

## ntfy Android app v1.9.1
Released Feb 16, 2022

**Features:**

* Share to topic feature (#131, thanks u/emptymatrix for reporting)
* Ability to pick a default server (#127, thanks to @poblabs for reporting and testing)
* Automatically delete notifications (#71, thanks @arjan-s for reporting)
* Dark theme: Improvements around style and contrast (#119, thanks @kzshantonu for reporting)

**Bug fixes:**

* Do not attempt to download attachments if they are already expired (#135)
* Fixed crash in AddFragment as seen per stack trace in Play Console (no ticket)

**Other thanks:**

* Thanks to @rogeliodh, @cmeis and @poblabs for testing

## ntfy server v1.15.0
Released Feb 14, 2022

**Features & bug fixes:**

* Compress binaries with `upx` (#137)
* Add `visitor-request-limit-exempt-hosts` to exempt friendly hosts from rate limits (#144)
* Double default requests per second limit from 1 per 10s to 1 per 5s (no ticket)
* Convert `\n` to new line for `X-Message` header as prep for sharing feature (see #136)
* Reduce bcrypt cost to 10 to make auth timing more reasonable on slow servers (no ticket)
* Docs update to include [public test topics](https://ntfy.sh/docs/publish/#public-topics) (no ticket)

## ntfy server v1.14.1
Released Feb 9, 2022

**Bug fixes:**

* Fix ARMv8 Docker build (#113, thanks to @djmaze)
* No other significant changes

## ntfy Android app v1.8.1
Released Feb 6, 2022

**Features:**

* Support [auth / access control](https://ntfy.sh/docs/config/#access-control) (#19, thanks to @cmeis, @drsprite/@poblabs, 
  @gedw99, @karmanyaahm, @Mek101, @gc-ss, @julianfoad, @nmoseman, Jakob, PeterCxy, Techlosopher)
* Export/upload log now allows censored/uncensored logs (no ticket)
* Removed wake lock (except for notification dispatching, no ticket)
* Swipe to remove notifications (#117)

**Bug fixes:**

* Fix download issues on SDK 29 "Movement not allowed" (#116, thanks Jakob)
* Fix for Android 12 crashes (#124, thanks @eskilop)
* Fix WebSocket retry logic bug with multiple servers (no ticket)
* Fix race in refresh logic leading to duplicate connections (no ticket)
* Fix scrolling issue in subscribe to topic dialog (#131, thanks @arminus)
* Fix base URL text field color in dark mode, and size with large fonts (no ticket)
* Fix action bar color in dark mode (make black, no ticket)

**Notes:**

* Foundational work for per-subscription settings

## ntfy server v1.14.0
Released Feb 3, 2022

**Features**:

* Server-side for [authentication & authorization](https://ntfy.sh/docs/config/#access-control) (#19, thanks for testing @cmeis, and for input from @gedw99, @karmanyaahm, @Mek101, @gc-ss, @julianfoad, @nmoseman, Jakob, PeterCxy, Techlosopher)
* Support `NTFY_TOPIC` env variable in `ntfy publish` (#103)

**Bug fixes**:

* Binary UnifiedPush messages should not be converted to attachments (part 1, #101)

**Docs**:

* Clarification regarding attachments (#118, thanks @xnumad)

## ntfy Android app v1.7.1
Released Jan 21, 2022

**New features:**

* Battery improvements: wakelock disabled by default (#76)
* Dark mode: Allow changing app appearance (#102)
* Report logs: Copy/export logs to help troubleshooting (#94)
* WebSockets (experimental): Use WebSockets to subscribe to topics (#96, #100, #97)
* Show battery optimization banner (#105)

**Bug fixes:**

* (Partial) support for binary UnifiedPush messages (#101)

**Notes:**

* The foreground wakelock is now disabled by default
* The service restarter is now scheduled every 3h instead of every 6h

## ntfy server v1.13.0
Released Jan 16, 2022

**Features:**

* [Websockets](https://ntfy.sh/docs/subscribe/api/#websockets) endpoint
* Listen on Unix socket, see [config option](https://ntfy.sh/docs/config/#config-options) `listen-unix`

## ntfy Android app v1.6.0
Released Jan 14, 2022

**New features:**

* Attachments: Send files to the phone (#25, #15)
* Click action: Add a click action URL to notifications (#85)
* Battery optimization: Allow disabling persistent wake-lock (#76, thanks @MatMaul)
* Recognize imported user CA certificate for self-hosted servers (#87, thanks @keith24)
* Remove mentions of "instant delivery" from F-Droid to make it less confusing (no ticket)

**Bug fixes:**

* Subscription "muted until" was not always respected (#90)
* Fix two stack traces reported by Play console vitals (no ticket)
* Truncate FCM messages >4,000 bytes, prefer instant messages (#84)

## ntfy server v1.12.1
Released Jan 14, 2022

**Bug fixes:**

* Fix security issue with attachment peaking (#93)

## ntfy server v1.12.0
Released Jan 13, 2022

**Features:**

* [Attachments](https://ntfy.sh/docs/publish/#attachments) (#25, #15)
* [Click action](https://ntfy.sh/docs/publish/#click-action) (#85)
* Increase FCM priority for high/max priority messages (#70)

**Bug fixes:**

* Make postinst script work properly for rpm-based systems (#83, thanks @cmeis)
* Truncate FCM messages longer than 4000 bytes (#84)
* Fix `listen-https` port (no ticket)

## ntfy Android app v1.5.2
Released Jan 3, 2022

**New features:**

* Allow using ntfy as UnifiedPush distributor (#9)
* Support for longer message up to 4096 bytes (#77)
* Minimum priority: show notifications only if priority X or higher (#79)
* Allowing disabling broadcasts in global settings (#80)

**Bug fixes:**

* Allow int/long extras for SEND_MESSAGE intent (#57)
* Various battery improvement fixes (#76)

## ntfy server v1.11.2
Released Jan 1, 2022

**Features & bug fixes:**

* Increase message limit to 4096 bytes (4k) #77
* Docs for [UnifiedPush](https://unifiedpush.org) #9
* Increase keepalive interval to 55s #76
* Increase Firebase keepalive to 3 hours #76

## ntfy server v1.10.0
Released Dec 28, 2021

**Features & bug fixes:**

* [Publish messages via e-mail](ntfy.sh/docs/publish/#e-mail-publishing) #66
* Server-side work to support [unifiedpush.org](https://unifiedpush.org) #64
* Fixing the Santa bug #65

## Older releases
For older releases, check out the GitHub releases pages for the [ntfy server](https://github.com/binwiederhier/ntfy/releases)
and the [ntfy Android app](https://github.com/binwiederhier/ntfy-android/releases).