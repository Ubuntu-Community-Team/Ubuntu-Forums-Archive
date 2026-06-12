---
title: "Networking Problems"
date: 2008-09-07
forum: Desktop Environments
---

### Post by blogzzz on 2008-09-07
I am using Xubuntu (UserOS Home Server 8.04) to share files with Windows. It doesn't let me write to the disk through a Windows computer. These are the steps I have taken to do this. Applications > System > Shared Folders. I created the folder I want to share in /home/username/share where share is the folder that I want shared in Windows. Then I opened the containing folder > Properties > Permissions Tab> Others: Read & Write > Recursive? Yes. If Others is set to none, I can't access the folder through Windows. If it is read only, I can only read the disk, just like what situation I am in if I select Read & Write. A link to the snapshot of the properties is at the bottom of the post. I don't seem to be able to get this to work. I have followed the instructions in the October issue of PC User but it doesn't work. Any ideas?

Link to snapshot: [http://cybertown.890m.com/snapshot.bmp](http://cybertown.890m.com/snapshot.bmp)

---

### Post by Xiong Chiamiov on 2008-09-07
You'll be a lot more likely to get help if you post this over in the [Networking forum]("http://ubuntuforums.org/forumdisplay.php?f=336").

---

### Post by gkestrel on 2008-09-14
Try this in a terminal type the following command to change the permissions on the shared folder you made.

sudo chmod 0777 /home/username/share

Are you using samba to share files with windows, if so there is an excellent how to in the forums that helps you to set up samba correctly at

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

its well worth a read and should help you to successfully share files with windows computers.

---

