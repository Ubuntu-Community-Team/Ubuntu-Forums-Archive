---
title: "Graphical fstab editor?"
date: 2009-03-10
forum: General Help
---

### Post by DPic on 2009-03-10
I was wondering if there was gui for editing fstab (...other than a text editor). Mainly, what i want to do it be able to make a drive mount automatically (missed my opportunity to set that upon installaion). If i mount it and right click to access properties, i can view the "Volume" tab where i can set the mount point, but this would be a nice place to have a checkmark for "Mount automatically" or something.

---

### Post by Neo_The_User on 2009-03-10
whats wrong with using gedit?

---

### Post by DPic on 2009-03-10
> **Neo_The_User said:**
> whats wrong with using gedit?

I ended up being able to do it, but it's not good for newbies. Doesn't seem very hard to implemant either. Guess this is a feature suggestion then.

---

### Post by arvevans on 2009-03-10
Using an editor for changing /etc/fstab is a bit daunting for a Linux newbie, and also prone to errors if you don't know exactly what you are doing.
[INDENT]arv@arv-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=df7cf21b-21db-4603-a506-31885dc4c5b6 /               reiserfs defaults        0       1
# /dev/sda1
UUID=5d6289bc-4595-448f-a18d-42bd7a2d4a3d /boot           reiserfs notail          0       2
# /dev/sda4
UUID=5b735312-5ca4-480f-84fe-51c753e04d87 /home           reiserfs defaults        0       2
# /dev/sda3
UUID=141b0601-38e0-43cc-9218-b945f5d6dd2a none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
arv@arv-desktop:~$ 
[/INDENT]
There is a lot of hard to understand stuff there for the inexperienced Linux user.  Breaking this down into individual edit blocks with help for each block could make Linux easier to use for recent converts and for those who don't do Linux as a profession.

So, I'm with "DPic".  Where is the handy GUI for this infrequently performed operation.  Such a GUI would not use up precious real-time resources because it would just lay there as an executable file until called by someone.

Lots of things that many of us do via command line or text editor could probably be converted to a GUI.  It is just a matter of available expertise, time, and interest.

---

### Post by Dr Small on 2009-03-10
When I'm editing /etc/fstab, I generally don't even have X11 installed yet... But if you think it is *necessary*, you can submit an idea to brainstorm.

---

### Post by dcstar on 2009-03-10
> **DPic said:**
> I was wondering if there was gui for editing fstab (...other than a text editor). Mainly, what i want to do it be able to make a drive mount automatically (missed my opportunity to set that upon installaion). If i mount it and right click to access properties, i can view the "Volume" tab where i can set the mount point, but this would be a nice place to have a checkmark for "Mount automatically" or something.

pysdm

---

