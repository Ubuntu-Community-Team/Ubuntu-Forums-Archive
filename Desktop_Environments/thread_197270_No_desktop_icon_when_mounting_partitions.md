---
title: "No desktop icon when mounting partitions"
date: 2006-06-15
forum: Desktop Environments
---

### Post by regne v on 2006-06-15
I have in my disk to unmounted fat32 partitions.

When I opened "My Computer" in 5.10 only the mountable partitions were showed (see first attachment) and if i doubled click their icons the partition got mounted, the clicked icon changed, an icon appeared on the desktop and nautilus opened showing its contents.

Since I upgraded to ubuntu 6.06 (fresh reinstall) "My Computer" shows all the partitions (see second attachment) and when I double click an unmounted partition the partition gets mounted, but nothing else happens.

I've tried to set the partitions mounted to /media with no luck.

I found [this guide]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_refresh_Places_menu_in_GNOME_.28if_mounts_to_.2Fmedia.2F_in_.2Fetc.2Ffstab_does_not_show_up.29") and run "sudo /etc/init.d/dbus restart" (there's no dbus-1 in my disk) and then I just got the very same "My Computer" from 5.10 but still no icon on desktop, or else. When the computer is restarted the contents of "My Computer" revert to the same in the second attachment.

Any help, please?

---

### Post by bitoiu on 2006-06-15
Hi,

 > I found this guide and run "sudo /etc/init.d/dbus restart" (there's no dbus-1 in my disk) and then I just got the very same "My Computer" from 5.10 **but still no icon on desktop**, or else. When the computer is restarted the contents of "My Computer" revert to the same in the second attachment.


I guess this only solve half of yours problems, because i figure you can't acesss any contents form non-linux drives. But if you want to see mounted volumes in your desktop make sure you go to:

Menu -> Applications -> Configuration Editor, 
then
Apps -> Nautilus -> Desktop

In the right frame check "Volumes Visible" ;) 

Still I can't help you acessing the contents, are the volumes mounted in fstab ?
They don't need to be but it's convinient.

Bye.

---

### Post by Anduu on 2006-06-15
Open gconf-editor and go to apps>nautilus>desktop and make sure the volumes_visible box is checked

HEh too slow

---

### Post by bruce89 on 2006-06-15
Open Gconf editor by pressing Alt+F2, and typing ```
gconf-editor
```

---

### Post by regne v on 2006-06-15
> Menu -> Applications -> Configuration Editor,
then
Apps -> Nautilus -> Desktop

In the right frame check "Volumes Visible" 

Sorry, I had found about it and yes, it is checked. When I uncheck it some icons in the desktop pointing to remote ftp servers dissapear and when checked again they reappear, only these.

> Still I can't help you acessing the contents, are the volumes mounted in fstab ?
There's no problem accessing the contents at all. The partitions get mounted correcty and they can be browsed. The only problem is the desktop icon and the weird behaviour of "My Computer" when dbus is restarted.

---

### Post by regne v on 2006-06-16
I think the problem is related to this [gnome-vfs2 reported bug]("https://launchpad.net/distros/ubuntu/+source/gnome-vfs2/+bug/34886").

Was it really fixed?.

---

