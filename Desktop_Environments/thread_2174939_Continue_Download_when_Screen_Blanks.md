---
title: "Continue Download when Screen Blanks?"
date: 2013-09-16
forum: Desktop Environments
---

### Post by noloader on 2013-09-16
I'm working with Ubuntu 13 (x64):
```
$ uname -a
Linux ubuntu 3.8.0-27-generic #40-Ubuntu SMP Tue Jul 9 00:17:05 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```
When the screen blanks, a 2.5 GB download stops. So far, a 30 minute download is still in progress 3 hours later.

I'm working on a PC, and not a tablet (despite Ubuntu/Fedora/Unity/Gnome/et al wishes). I want to continue the download when Ubuntu puts my PC in low power mode or blanks the screen.

How do I stop Ubuntu from turning off networking when the PC enters low power mode or the screen blanks?

---

### Post by varunendra on 2013-09-17
It is most probably going into suspend mode, not just blanking screen. Goto System Settings > Power and make the settings something like this -

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=246293[/IMG]

The above is from my laptop, not a PC, so ignore the settings regarding "On battery power".

---

