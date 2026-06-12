---
title: "Thanks guys, best experience with Linux yet"
date: 2005-07-04
forum: Desktop Environments
---

### Post by doogie on 2005-07-04
Finally registered to say "thanks" to everyone in this community. Linux and open source is truly the platform of the near future, and until now it has been such a frustration trying to get any distrobution to work. I've been informally playing around with Linux since 2000. I had yet to have a 100% working install of Linux.

Ubuntu is a sinch to install and setup. Once installed it gives you enough hand-holding yet enough control to do what you need to do. As a Microsoft software user since MS-DOS 2.0, lots of things get lost in translation for me, but I think I am finally coming around, given the latest scenario: my network is primarily Windows so naturally the server runs Windows 2003. I installed and configured Services for UNIX 3.5 including NIS, NFS, User Name Mapping and Password Sync. I had been able to mount and use NFS shares before, but NIS auth never worked. The guide at [https://wiki.ubuntu.com/SettingUpNISHowTo](https://wiki.ubuntu.com/SettingUpNISHowTo) worked beautifully.

Once able to authenticate over NIS, how do you guys set up your NIS users' profiles and security settings for the local machine? What groups do they need to be a part of? Do you mention those users in /etc/group or /etc/passwd or /etc/shadow? I guess I need a follow-on HOWTO once authentication is working. I honestly cheated, made a local user and mv'ed his home directory to my NIS user.
Needless to say, things were jacked up. I added the NIS user to several groups and things worked better, but the NIS user still could not access certain files, including any NFS shares. Any local user can access the shares just fine. Weird!

Anyhow, fixing certain minor issues (broken ALSA/esd) and making the fonts look stunning were easy thanks to this forum and ubuntuguide.org. Long live Debian and Ubuntu!

By the way, if anybody needs help configuring Services for UNIX, I'll be glad to help out. Trying to do my part where I can!

---

### Post by adamb10 on 2005-07-04
[QUOTE=doogie]Finally registered to say "thanks" to everyone in this community. Linux and open source is truly the platform of the near future, and until now it has been such a frustration trying to get any distrobution to work. I've been informally playing around with Linux since 2000. I had yet to have a 100% working install of Linux.

Ubuntu is a sinch to install and setup. Once installed it gives you enough hand-holding yet enough control to do what you need to do. As a Microsoft software user since MS-DOS 2.0, lots of things get lost in translation for me, but I think I am finally coming around, given the latest scenario: my network is primarily Windows so naturally the server runs Windows 2003. I installed and configured Services for UNIX 3.5 including NIS, NFS, User Name Mapping and Password Sync. I had been able to mount and use NFS shares before, but NIS auth never worked. The guide at [https://wiki.ubuntu.com/SettingUpNISHowTo](https://wiki.ubuntu.com/SettingUpNISHowTo) worked beautifully.

Once able to authenticate over NIS, how do you guys set up your NIS users' profiles and security settings for the local machine? What groups do they need to be a part of? Do you mention those users in /etc/group or /etc/passwd or /etc/shadow? I guess I need a follow-on HOWTO once authentication is working. I honestly cheated, made a local user and mv'ed his home directory to my NIS user.
Needless to say, things were jacked up. I added the NIS user to several groups and things worked better, but the NIS user still could not access certain files, including any NFS shares. Any local user can access the shares just fine. Weird!

Anyhow, fixing certain minor issues (broken ALSA/esd) and making the fonts look stunning were easy thanks to this forum and ubuntuguide.org. Long live Debian and Ubuntu!

By the way, if anybody needs help configuring Services for UNIX, I'll be glad to help out. Trying to do my part where I can![/QUOTE]
 Ubuntu is a great distro.  It doesn't come with alot of packages that can slow down the system like FC and uses Apt-get.  I love it.

---

