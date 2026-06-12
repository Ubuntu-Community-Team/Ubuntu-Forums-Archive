---
title: "Second hard drive"
date: 2006-06-18
forum: Desktop Environments
---

### Post by steveneddy on 2006-06-18
OK-searched the forums, and I may have missed it, but here's what I want to do. I have a second hard drive, and I have it mounted. It shows up in Places under Computer and in the Computer File Browser window. 

It also shows up on my desktop as an icon. I would <b>NOT</b> like to have an icon on my desktop for this hard drive. 

How do I delete the hard drive icon from the desktop?

How do I make this drive writable?

How do I make this hard drive part of the file system? 

I would like for the hard drive to look like it is part of the system. You know, so Linux sees both drives as one large drive. 

Here is my /etc/fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1	/media/hda1	ext3	defaults


The drive labeled /dev/hda1 is the drive I am addressing, the last one on the list.

It is also listed in /media/hda1.

Maybe I need to use RAID for the system to see both drives as one large one?

Any help will be welcomed. Thanks in advance.
-SE

---

### Post by Third Thoughts on 2006-06-18
[QUOTE=steveneddy]
OK-searched the forums, and I may have missed it, but here's what I want to do. I have a second hard drive, and I have it mounted. It shows up in Places under Computer and in the Computer File Browser window. 

It also shows up on my desktop as an icon. I would <b>NOT</b> like to have an icon on my desktop for this hard drive. 
[/QUOTE]

Not sure about this one, I think it has something to do with your nautilus configuration, but I don't know exactly where to make the changes.

> 
How do I delete the hard drive icon from the hard drive?


What do you mean? I'm not sure what you're asking

> 
How do I make this drive writable?


It should be writeable by default. Are you getting some sort of error message when you try to save something to it?

> 
How do I make this hard drive part of the file system? 

I would like for the hard drive to look like it is part of the system. You know, so Linux sees both drives as one large drive. 


I think you will need RAID for that. But you can also change the mount point for the hard drive to something more easily navigated to. For example, you could make the second hard drive mount at /home, that way all your personal files would be on that drive and all the system files would be on the other drive. I'm not sure why you need to have Ubuntu treat the two drives as one, so I don't know if my suggestion is that helpful, but I just thought I'd add it.

~Andrew S.

---

### Post by aysiu on 2006-06-18
These two links should help you:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

As long as the mount point is not within the /media or /mnt folders, the icon should not show up on the desktop.

---

### Post by steveneddy on 2006-06-19
[QUOTE=Third Thoughts]



What do you mean? I'm not sure what you're asking
 
**delete hd icon from the desktop**(my typo)

It should be writeable by default. Are you getting some sort of error message when you try to save something to it?

says I need to be root

I think you will need RAID for that. But you can also change the mount point for the hard drive to something more easily navigated to. For example, you could make the second hard drive mount at /home, that way all your personal files would be on that drive and all the system files would be on the other drive. I'm not sure why you need to have Ubuntu treat the two drives as one, so I don't know if my suggestion is that helpful, but I just thought I'd add it.

~Andrew S.[/QUOTE]
 -se

---

### Post by steveneddy on 2006-06-19
aysiu - thank you very much for all of your help. I know when I see you, poofyhairguy, azz, arnieboy and others, I know I will get good advice on the Ubuntu forums. I actually spend an unhealthy amount of time lurking around the Ubuntu forums. I'm no pro, but things just seem to work well for me regarding Linux upgrades and tweaks. 

I have the second hard drive listed as /storage and I have lightened the load of my primary HD. I also have installed VMware and use it for my Win2k stuff. It works very well. I have KDE, Fluxbox, XFce, XPde, Enlightenment and IceWM for a choice of window managers and desktop environments. I have always felt that choice is a good thing.

I use Wallpapoz because I like the wallpapers on each desktop to be different, like KDE. I have Firefox with Autohide and HideTabBar, the perfect full screnn experience. I have a custom Eterm that is borderless, buttonless, transparant and floating on my desktop.

All of these things I learned about from these forums, & I thank you all. Thank you folks that are giving great advice and answering posts of the confused (me) and steering us in the right direction.

Everyone who runs windows and sees my machine are in awe. It looks beautiful. I even have a little envy from of the folks at my local LUG.

Thanks again! -SE

---

