---
title: "cannot stat /etc/X11/xorg.conf"
date: 2010-12-11
forum: Desktop Environments
---

### Post by whatthefunk on 2010-12-11
I've just done a fresh install of Lubuntu 10.10 on an older Sony Vaio laptop. Having learned the hard way about editing xorg files, I wanted to create a backup of the xorg.conf file so that I dont have to do another install when I screw everything up. In a terminal, I typed 
 
```
[FONT=Courier New]sudo cp /etc/X11/xorg.conf /ect/X11/xorg.conf.911[/FONT]
```
 
I got the error message
 
> cp: cannot stat `/etc/X11/xorg.conf': No such file or directory
 
Hmmm.... What does that mean? How can I make a backup? Thanks.

---

### Post by StephenDavison on 2010-12-11
It means there is no xorg.conf.  That file is generally no longer needed by the X server.  I think Ubuntu 9.04 was the last time I saw it (but I skipped 9.10).

---

### Post by whatthefunk on 2010-12-11
Thanks StephenDavison.  So if I need to edit configuration files, but want to make backups of the originals first, what should i do?

---

### Post by bobcollard on 2010-12-11
> **whatthefunk said:**
> Thanks StephenDavison.  So if I need to edit configuration files, but want to make backups of the originals first, what should i do?
If you are hard core, you can create another xorg.conf, make it executable and create your own settings, no guarantees they will all overide the current system though.  Suggest you do a search on the forum to see what replaced xorg.conf.  I don't mess with settings.

---

### Post by StephenDavison on 2010-12-11
you might try 
[http://ubuntuforums.org/showthread.php?t=670645](http://ubuntuforums.org/showthread.php?t=670645)
or
[http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html](http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html)

---

### Post by whatthefunk on 2010-12-11
> **StephenDavison said:**
> you might try 
[http://ubuntuforums.org/showthread.php?t=670645](http://ubuntuforums.org/showthread.php?t=670645)
or
[http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html](http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html)
 
Those two aren't working. 
 
I typed this into a terminal and rebooted.
 
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
 
Same error message after reboot.
 
For the second link, it suggests 
 
```
sudo service gdm stop
```
 
This give me this error message:
 
> gdm: unrecognized service

---

### Post by whatthefunk on 2010-12-11
> **bobcollard said:**
> If you are hard core, you can create another xorg.conf, make it executable and create your own settings, no guarantees they will all overide the current system though. Suggest you do a search on the forum to see what replaced xorg.conf. I don't mess with settings.
 
Thanks bobcollard.  How do I go about doing that?

---

### Post by bobcollard on 2010-12-11
> **whatthefunk said:**
> Thanks bobcollard.  How do I go about doing that?
Sorry, I never worked with Lubuntu and don't know my way around that system.  Hope someone else can help you out.  I have a feeling it does not use GDM (Gnome Desktop Manager)

---

### Post by kgarbutt on 2010-12-11
> **whatthefunk said:**
> I've just done a fresh install of Lubuntu 10.10 on an older Sony Vaio laptop. Having learned the hard way about editing xorg files, I wanted to create a backup of the xorg.conf file so that I dont have to do another install when I screw everything up. In a terminal, I typed 
 
```
[FONT=Courier New]sudo cp /etc/X11/xorg.conf /ect/X11/xorg.conf.911[/FONT]
```
 
I got the error message
 

 
Hmmm.... What does that mean? How can I make a backup? Thanks.

You typed: /ect/X11... When you should have typed /etc...

---

