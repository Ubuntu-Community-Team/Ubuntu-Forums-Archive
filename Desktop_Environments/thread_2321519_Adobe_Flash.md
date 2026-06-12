---
title: "Adobe Flash"
date: 2016-04-22
forum: Desktop Environments
---

### Post by Softa on 2016-04-22
On my desktop, I am trying to play some FaceBook games, but the games tell me that I need to upgrade Adobe Flash. I've tried to, but there is nothing to upgrade to in APT. According to the upgrade manager, everything is up to the minute. On my smart-phone, and laptop (which is windows) I am able to play these games. Is it because they're windows based, or what?

Thanks for any help.

---

### Post by sammiev on 2016-04-22
Hi,

I can play Pogo games using this flash but make sure you delete all other versions of flash first.

[Pepper Flash]("http://ubuntuhandbook.org/index.php/2015/10/ipepper-flash-for-firefox-ubuntu-15-10/")

---

### Post by dFlyer on 2016-04-22
If your using Chromium use pepper flash, if your using firefox use browser-plugin-freshplayer-pepperflash and pepper flash. Uninstall adobeflash as it's no longer supported. This is for 16.04. If your using 14.04 use chromium with pepper flash.

---

### Post by buzzingrobot on 2016-04-23
Two versions of Flash exist for Linux.

The version of Flash Adobe releases for general Linux use is supported but Adobe stopped feature updates a few years ago.  Adobe does apply security patches to it, and it's those updated versions that we see in Ubuntu and elsewhere in Linux.

Sites, then, that require the latest version of Flash for Windows won't work with that version of Flash for Linux.  Typically, they will simply check the version number and, assuming you are on Windows, pop up that message about updating.

An alternative is to install Chrome.  Google contracted with Adobe to provide an up-to-date version of Flash for exclusive use in its Chrome browsers.  It's installed by default when you install Chrome. That version of Flash, as mentioned, can also be used in Chromium if you want to set it up yourself.

---

