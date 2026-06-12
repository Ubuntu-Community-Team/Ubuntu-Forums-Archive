---
title: "LIRC no longer works in 18.04 and it's causing major problems, had to revert to 16.04"
date: 2018-07-23
forum: Desktop Environments
---

### Post by Mythological on 2018-07-23
If you run Kodi, or any other multimedia software that can use an infrared remote control, you may have been bitten by this.  In past versions of Ubuntu (<=16.04) you could install the LIRC software and pick your remote type in the configuration menu, and it all worked great.  Now if you try to install LIRC, you don't get the configuration menu and the remote doesn't work.  But if you *don't* install LIRC, you get double button presses on some buttons, no button presses on others (including important ones like the select (or enter or ok)) and just plain poor operation all around, plus you cannot run irexec -d and use a .lircrc file to launch programs from the desktop using the remote.  I REALLY wish there were some way to get LIRC to work in Ubuntu 18.04, but since I couldn't I've had to go back to 16.04.  If the Ubuntu developers are seeing a higher number of *new* installs of Ubuntu 16.04 than they'd expect, this is probably one major reason why.  A home theater PC  is kind of useless if you can't get a remote to work correctly!

Apparently the LibreElec people have also run into this problem, and they put up an article about it at [https://wiki.libreelec.tv/infrared_remotes](https://wiki.libreelec.tv/infrared_remotes) but their solution was apparently to use a small program that runs in the background, eventlircd, which translates Linux input events from remotes into LIRC events.  While the eventlircd program is available on Github at [https://github.com/OpenELEC/eventlircd](https://github.com/OpenELEC/eventlircd) it doesn't help me because I really would have no idea how to install it in Ubuntu 18.04 desktop, or if that is even possible.  It sounds as though if it could be installed it *might* be a solution for other software that wants to see LIRC-style input, such as Kodi and (I believe) MythTV, although I still have no idea if or how it would be used to launch software using the remote from the Ubuntu desktop.  This was all SO EASY in Ubuntu 16.04, but I have spent the better part of two days trying to find a solution that would actually work in Ubuntu 18.04.  There are several pages where people say they have a solution but not a single one that I have tried has made the remote work the way it should; at best I get sporadic double button presses or the opposite problem of having to press a button many times before it is recognized.  And I am not the only one having this issue, I see many posts in different places where people are looking for a solution to this!

My guess is that this is in part a Linux kernel issue but even if that's true, if the LibreElec people can get remotes to work with their software it sure seems like it should be possible when using Ubuntu 18.04.  Is there a solution here that I am missing, that actually works?  Or is there some way to install and use that eventlircd software in Ubuntu, or some other piece of software that does the same thing (at least insofar as translating button presses into something Kodi can properly deal with?).  If someone could figure this out, a lot of home theater PC users would be VERY grateful!  And I'd be even more happy if LIRC could be made to work the way it always has in 18.04, since that was always the big problem solver when it came to making infrared remotes work.

---

### Post by bullwinkle2 on 2018-07-24
See [https://twosortoftechguys.wordpress.com/2018/07/24/make-lirc-work-in-ubuntu-18-04/](https://twosortoftechguys.wordpress.com/2018/07/24/make-lirc-work-in-ubuntu-18-04/)

---

### Post by vidtek on 2018-10-11
Try my solution here in my how-to: [https://ubuntuforums.org/showthread.php?t=2403337]("https://ubuntuforums.org/showthread.php?t=2403337")

Cheers, Tony.

---

