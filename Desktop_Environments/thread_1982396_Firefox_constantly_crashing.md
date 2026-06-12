---
title: "Firefox constantly crashing"
date: 2012-05-18
forum: Desktop Environments
---

### Post by McMuffin1892 on 2012-05-18
EDIT: the smiley face next to the title is because i clicked the button by accident. sorry.

I'm running Ubuntu 11.10 64 bit on an HP Pavilion dv7, and a problem I'm having is that firefox keeps crashing. I'll be browsing around, and many many times, whenever I click a new link, firefox instantly crashes once the page loads, and the "We're Sorry, Firefox has crashed" dialog pops up. I'd say it happens once for every fifteen web pages I load, roughly, although sometimes it seems to more common.

For the last two times it happened, I copied the report dialog. Here's what it is for the first time:
Add-ons: {b9db16a4-6edc-47ec-a1f4-b86292ed211d}:4.9.9,globalmenu@ubuntu.com:2.0.6,langpack-en-GB@firefox.mozilla.org:12.0,langpack-en-ZA@firefox.mozilla.org:12.0,ubufox@ubuntu.com:1.0.4,{972ce4c6-7e08-4474-a285-3208198ce6fd}:12.0
BuildID: 20120423122843
Comments:
CrashTime: 1337357055
EMCheckCompatibility: true
FramePoisonBase: 7ffffffff0dea000
FramePoisonSize: 4096
InstallTime: 1335803549
Notes: OpenGL: ATI Technologies Inc. -- AMD Radeon HD 6500M/5600/5700 Series -- 4.1.11005 Compatibility Profile Context -- texture_from_pixmap

ProductID: {ec8030f7-c20a-464f-9b0e-13a3a9e97384}
ProductName: Firefox
ReleaseChannel: release
SecondsSinceLastCrash: 310
StartupTime: 1337356748
Theme: classic/1.0
Throttleable: 1
URL: [http://www.google.com/url?sa=t&rct=j&q=jnlp%20files&source=web&cd=1&ved=0CGIQFjAA&url=http%3A%2F%2Fwww.fileinfo.com%2Fextension%2Fjnlp&ei=9XK2T9DLF9HogQfK_NC8Cg&usg=AFQjCNHKFOC7H2yyUBwVacNRvuPGL9Hm2Q&cad=rja]("http://www.google.com/url?sa=t&rct=j&q=jnlp%20files&source=web&cd=1&ved=0CGIQFjAA&url=http%3A%2F%2Fwww.fileinfo.com%2Fextension%2Fjnlp&ei=9XK2T9DLF9HogQfK_NC8Cg&usg=AFQjCNHKFOC7H2yyUBwVacNRvuPGL9Hm2Q&cad=rja")
Vendor: Mozilla
Version: 12.0

This report also contains technical information about the state of the application when it crashed.

And the second one:
Add-ons: {b9db16a4-6edc-47ec-a1f4-b86292ed211d}:4.9.9,globalmenu@ubuntu.com:2.0.6,langpack-en-GB@firefox.mozilla.org:12.0,langpack-en-ZA@firefox.mozilla.org:12.0,ubufox@ubuntu.com:1.0.4,{972ce4c6-7e08-4474-a285-3208198ce6fd}:12.0
BuildID: 20120423122843
CrashTime: 1337357298
EMCheckCompatibility: true
FramePoisonBase: 7ffffffff0dea000
FramePoisonSize: 4096
InstallTime: 1335803549
Notes: OpenGL: ATI Technologies Inc. -- AMD Radeon HD 6500M/5600/5700 Series -- 4.1.11005 Compatibility Profile Context -- texture_from_pixmap

ProductID: {ec8030f7-c20a-464f-9b0e-13a3a9e97384}
ProductName: Firefox
ReleaseChannel: release
SecondsSinceLastCrash: 243
StartupTime: 1337357138
Theme: classic/1.0
Throttleable: 1
URL: [http://www.google.com/search?q=ubuntu+firefox+always+crashing&ie=utf-8&oe=utf-8&client=ubuntu&channel=fs](http://www.google.com/search?q=ubuntu+firefox+always+crashing&ie=utf-8&oe=utf-8&client=ubuntu&channel=fs)
Vendor: Mozilla
Version: 12.0

This report also contains technical information about the state of the application when it crashed.

---

### Post by McMuffin1892 on 2012-05-22
Wow, I hate sounding so impatient and rude, but really, there aren't any replies yet? I know that many other people are having this problem: "firefox ubuntu constantly crashes" has 18 million hits on google--and if you start "firefox ubuntu " the autofill has "firefox ubuntu constantly crashes" as the 4th suggestion.

I've done research on this topic, and it appears that dozens of people have posted onto forums with the same problem as me, none of them ever getting a solution. At best there's vague suggestions that it's caused by flash.

Seeing as how this is an extremely crippling and apparently common problem, shouldn't the community be really looking into this one, like as a main problem?

---

### Post by IWantFroyo on 2012-05-22
Uninstall your flash player and try again.
Also:
```
sudo apt-get dist-upgrade
```

> Seeing as how this is an extremely crippling and apparently common  problem, shouldn't the community be really looking into this one, like  as a main problem?
A search for bug reports on Launchpad gave me only 3 reports, none of which really matched your issue. If it persists, file a bug report yourself.

---

### Post by McMuffin1892 on 2012-05-28
Updating doesn't work. It says my package information was last updated 13 days ago, but when I tell Update manager to check for updates it doesn't update the info, it still says "last updated 13 days ago" with no updates available.

run apt-get dist-upgrade failed, it gave me a bunch of errors. Can't remember what they are, but they started with "W:" then mentioned something about "duplicate sources" or something. what exactly does this mean? is this connected to my firefox problem?

---

### Post by McMuffin1892 on 2012-05-28
Okay ran apt-get dist-upgrade  again, and here's what the error messages are:
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) oneiric/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) oneiric/partner amd64 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-amd64_Packages)
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) oneiric/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) oneiric/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_oneiric_partner_binary-i386_Packages)

---

