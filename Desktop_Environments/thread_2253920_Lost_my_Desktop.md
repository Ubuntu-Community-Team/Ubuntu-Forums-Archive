---
title: "Lost my Desktop"
date: 2014-11-23
forum: Desktop Environments
---

### Post by Jonners59 on 2014-11-23
I am on the latest version of Ubuntu and keep it up todate.  I use xfce.
Everything has been fine, but my wife booted up the PC and instead of my normal background, folders, etc, everything is different.  I can not change my background at all, the image files are greyed out.  I have an icon on my desktop called server (it is a pc on the LAN used as a storage device) and it is in the middle of the screen and won't move, and when "touched" creates a local directory copy.  Some apps are not working quite right, such as Evolution, that can not send mail...

Surfing the file system, is slow, but does not give away any clues as to what has happened.

fstab is fine with nothing strange or changed.

I opened gParted and noticed that Root (/) was mapped to a different mount point, a directory deep in etc and it also had a ? after the /.  I deleted the directory it was pointing at and rebooted, but although gparted is still reading correctly, the appearance and usability is still not right.

Any ideas/help....?  What commands should I run to analyse the problem?  What other information is required?

---

