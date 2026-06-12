---
title: "Persistant Network Mounts"
date: 2009-02-02
forum: Desktop Environments
---

### Post by slick666 on 2009-02-02
Dear Ubuntu Users,

I'm trying to figure out how to make my network mounts persistent between boots. I use Ubuntu for a development system at work and I have several windows mounts on my desktop to allow me to transfer data and pull down documents. These are mount I add by following:

Places -> Connect to Server... -> then add log on information

The problem I have is that every time I reboot they all go away. I can't seem to find a way to make them permanent and I can't seem to find anything along that line on google or here in the forums. I'm sure it can be done so I think I might be using the wrong terminology.

Any directions or helpful links appreciated.

---

### Post by Old *ix Geek on 2009-02-02
I don't use GNOME so I can't help specifically, but in general you need to create mount points for the shares and then add appropriate entries into your /etc/fstab file to mount them at boot time.  If you search the forums (or the 'net) for something like "mount shares fstab" you should find tutorials that will help.

---

### Post by slick666 on 2009-02-03
I know you can add network mounts to your fstab but I thought there would be a way through gnome so you could have all the icons on the screen.

---

### Post by slick666 on 2009-02-09
*Bump*
No one has any ideas about doing this any other way?

Also what I'm trying to accomplish is have the network mounts like those though gnome on the desktop. I've mounted the system from the command line but it doesn't show up on the Gnome "computer console" and I would have to make a sym-link from the desktop. It seems there should be an easy way to do this from gnome. any ideas appreciated

---

### Post by Coreigh on 2009-02-09
If you edit the fstab to auto mount your network folders you can then create shortcuts in the left panel of the Nautilus window, as well as desktop shortcuts if you wish.

I would post some links but the ubuntuforums are having troubles as I am writing this.

EDIT:
[http://ubuntuforums.org/showthread.php?t=800313](http://ubuntuforums.org/showthread.php?t=800313)
See last post for syntax to mount samba shares from fstab

---

### Post by Yashiro on 2009-02-10
Easy way, make a bookmark to them in Nautilus.
Usual way, add an entry for them in /etc/fstab

---

