---
title: "desktop weird behavior re. icons not displaying properly and drag and drop hanging th"
date: 2021-01-09
forum: Desktop Environments
---

### Post by quinta65 on 2021-01-09
I am transitioning from windows to ubuntu; I run 20.10 with Gnome in a partition of my disk. I mount the windows ntfs partition's on /home/myname


 My windows desktop, where I have a lot of my stuff, is therefore accessible at /home/myname/Users/myuser/Desktop

 
I configured in .config/user-dirs.dirs the desktop directory to /home/myname/Users/myuser/Desktop

 
Up to this point everything looks ok: all of my windows desktop's files appear within ubuntu like this.

 [[IMG]https://i.stack.imgur.com/TirTd.png[/IMG]]("https://i.stack.imgur.com/TirTd.png")

 
If I change an icon, for example of folder 'Libro', by editing the  folder's properties, it doesn't change on the desktop but if I open a  nautilus browser to that same directory, it correctly displays the new  icon.

 [[IMG]https://i.stack.imgur.com/9vPVz.png[/IMG]]("https://i.stack.imgur.com/9vPVz.png")

 this is the first weird behaviour

 
A second even worse behaviour is that, when I try to drag an icon to  an app (for example a file to be attached to a thunderbird email) the  mouse cursor becomes a closed hand (looks like a fist) and the computer  hangs. the mouse is movable; if I close the notebook it suspends, when I  reopen it, the only possibility is to enter the password in the lock  screen; after the lock screen I get back to exactly the same point with  the computer still hanging.

 
My only possibility is to abruptly power off and reboot.

 
I wonder if the cause of both behaviours can be an issue with permissions/file system mounting.

 
After some trial and error, in my /etc/fstab I entered

 UUID=2E54F0D254F09E31 /media/myname ntfs rw,auto,user,fmask=111,dmask=000,uid=1000,gid=1000 0 0 which works quite ok, except for the to issues above.

 
but if I look at mount, I obtain

 /dev/sda2 on /media/myname type fuseblk  (rw,nosuid,nodev,noexec,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,user)

 
Here goes the question: may it really be an issue with the mounting of the filesystem ? any hints on how to fix it ?

 
any help highly appreciated...

 
happy 2021!

---

### Post by quinta65 on 2021-01-14
it was not an issue related to the filesystem but to the poor handling of Desktop by 20.10
the solution was to use the extension
[https://gitlab.com/rastersoft/desktop-icons-ng](https://gitlab.com/rastersoft/desktop-icons-ng) 

BTW, I like tiny icons, so I had to redefine their size editing ./home/myname/.local/share/gnome-shell/extensions/ding@rastersoft.com/enum.js

---

