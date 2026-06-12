---
title: "Ubuntu Wont Startup .Swp or Something"
date: 2009-03-20
forum: General Help
---

### Post by Sugz on 2009-03-20
OK i so recently tried to apply changes to get my touchpad working after resume. 
But i ran into this problem. 
Now During Start-up i get this message

*Configuring network interfaces... [OK]
2 files to edit
E325 ATTENTION
Found a swap file by the name ".:.swp"
            owned by: root dated: Fri Mar 20 09:54:59
            file name: /:
            modified: no
            user name root hot nameL hh206a
            process IDL 30322
while opening file ":"
(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two different instances of the same file when making changes
Quit or continue with caution.
(2) An edit session for this file crashed if this is the case, use ":recover" or "vim -r :" to recover the changes (see ":help recovery").
If you did this already, delete the swap file ".:.swp"
to avoid this message
":" [New File]



I have no idea what to do.. Please Help This is Quite Urgent!!

---

### Post by Sugz on 2009-03-21
im going to bump this, because this problem is rendering my laptop virtually useless

---

### Post by Rallg on 2009-03-21
Are you logged in as more than one user simultaneously? If so, log out all but one user.

Does your /etc/fstab file have more than one reference to a swap file?

Do you have more than one swap partition? If you have several Linux installations on the same computer, you only need one swap file common to all, unless you running 2 Linux simultaneously somehow.

---

### Post by Sugz on 2009-03-22
This message pops up at start up, i can log into the GUI using another user simultaneously.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=46a857d3-ab51-4504-ab7a-b40180eaaf99 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=af8a30d3-0abb-4bba-a0ae-fd93b4eaf7c8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
#usbfs
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0
``` 

Above is my Fstab file. unfortunately, i'm not sure that it means. 

Thanks for your help

---

### Post by Sugz on 2009-03-22
Just a quick update. 
It seems to look like that multiple versions of linux are trying to run at the same time. 

if i press Ctr+a;t+ F1

I am put to a screen with something to do with the Boot rutines of Usplash and Kinit

But the command prompt says

"Doing normal Boot"

Pressing crtl+alt+F8
Sends me to the same command prompt screen as seen on my first post.

and ctrl+alt+F7 is the screen that i am currently typing this post on.

---

### Post by Sugz on 2009-03-30
This is still a problem.
This problem also causes the sound of my system to become inactive 
:confused:

---

