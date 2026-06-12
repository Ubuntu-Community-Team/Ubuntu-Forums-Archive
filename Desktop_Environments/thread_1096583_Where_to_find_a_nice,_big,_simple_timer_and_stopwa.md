---
title: "Where to find a nice, big, simple timer and stopwatch?"
date: 2009-03-15
forum: Desktop Environments
---

### Post by amylase on 2009-03-15
Hi

For a long time I've used something called Cool Timer. It is very simple and big. It does one of two things: count up, or, count down. If counting down, it can either beep or play a mp3 file when time reached. That's it. Nothing more, nothing less. What I love about this timer is you can blow it up to fit 1/3 or 1/2 of your screen. So I get this nice huge timer sitting on my desktop while I read or do whatever. Here is what it looks like. It is literally this big.
[IMG]http://classroomtech.org.uk/wp-content/uploads/2008/08/cooltimer_screenshot.jpg[/IMG]
or you can shrink it down a bit to
[IMG]http://i.d.com.com/i/dl/media/dlimage/15/42/60/154260_large.jpeg[/IMG]

To my disappointment though this timer runs only on Windows. Tried WINE, didn't work. My question is: can any one recommend a _big_, nice, _simple_ timer and stopwatch for me to use in Ubuntu? (Note that I have underlined big and simple)

Thanks very much. :popcorn:

---

### Post by dusan.saiko on 2009-03-16
There is directly "stopwatch" package in Ubuntu distribution, try that.

sudo apt-get install stopwatch

---

### Post by amylase on 2009-03-17
Thanks. The stopwatch is too tiny. I found a few others which are bigger. Here they are:

Stopwatch
[https://addons.mozilla.org/en-US/firefox/addon/1580](https://addons.mozilla.org/en-US/firefox/addon/1580)

Timers
**dclock** and **sanduhr** both already in repo

Faced clock
**xclock** already in repo

All of above run in Linux natively. 

In addition, incidentally I found a combined stopwatch + timer written by a guy called Geoff Moten back in 1998. The application is also called "**Cool Timer**" - same name as one made by HarmonyHollow I was looking for before but clearly two different authors. It turns out Moten's Cool Timer actually has very good functionality. Runs well via WINE. No need to install. Single .exe file runs straight off WINE. The only downside (apart from not running natively in Linux) is Moten's clock display is no where near as big as HarmonyHollow's. That aside, Moten's clock actually has a few additional features other clocks don't. So here it is. I don't think the author is contactable anymore but nevertheless his nice clock is still downloadable here from [http://www.delphi32.com/vcl/4099/](http://www.delphi32.com/vcl/4099/)

Looks like I just have make do with these for now. Thinking back, it's amazing how many big exams HarmonyHollow's clock has been through with me over these long years...

[B]Addendum
[/B]Managed to get HarmonyHollow's latest Cool Timer 3.6 to work. This thing needs VB Runtime to work. I copied msvbvm50.dll and msvbvm60.dll into c_drive/windows/system prior to installing the clock. Then I installed the clock and it installed flawlessly. You probably don't need both version 5 and 6 DLLs. I couldn't be bothered finding out which one it needs, just gave it both. The clock can be downloaded here [http://www.harmonyhollow.net/cool_timer.shtml]("http://www.harmonyhollow.net/cool_timer.shtml")

---

### Post by steveparbkk on 2011-05-18
Hi,

I wonder if you managed to get Cool Timer to work with an MP3 sound file instead of wav file?

Thanks for the post.  I have been hooked on Cool Timer for years too and the prospect of loosing the use of software I have come to rely upon was one of the major irritation with the prospect of ditching Windows.  Your post gave me encouragement!

Best wishes,

Steve

---

### Post by MountainX on 2011-09-05
> **amylase said:**
> Thanks. The stopwatch is too tiny. I found a few others which are bigger. Here they are:

Stopwatch
[https://addons.mozilla.org/en-US/firefox/addon/1580](https://addons.mozilla.org/en-US/firefox/addon/1580)

Timers
**dclock** and **sanduhr** both already in repo

Faced clock
**xclock** already in repo

All of above run in Linux natively. 



Thank you!

What we also need is something like wine but for Android so that we can easily run Android apps in Ubuntu -- but much snappier than the Android SDK allows.

---

