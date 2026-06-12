---
title: "File permissions"
date: 2009-01-22
forum: Desktop Environments
---

### Post by Timi 9 on 2009-01-22
Hi,I have some Ubuntu Gnome experience but from some time(from Hardy times to be specific)I'm fighting with a little inconvenience,specially Gnome related.From the Gnome 2.22 series when I copy my data files from my DVD's or CD's(doesn't matter what type of file)it gets locked automatic after the transfer finishes;I can't move them,can't rename them,nothing,the only solution is to go to properties and modify the permission!
All I want to know is if this is a Gnome behaviour(cause I've seen it in other distros as well)and if not is there a fix,because I'm sick of going to the properties,after DVD file transfer,just to be able to manipulate my own files!Thanks!:)

---

### Post by vanadium on 2009-01-22
You should not be sick. Just change permissions to allow writing. You can do this once for all files together.

---

### Post by Timi 9 on 2009-01-22
Yes I know friend,maybe I didn't made my self clear,the thing is when you copy something in a folder,after that,wanting to reorganize that thing just gets you back to properties,only for one itsy bitsy lousy file;when in every other DE,being Kde or whatever this thing doesn't exist!I love Gnome but this thing is idiotic!

---

### Post by vanadium on 2009-01-23
Essentially, I *do* agree with you. I just thought it is not worth being sick of it ;) In my opinion, files copied from a file system that does not support permissions just should acquire default permissions like new files (i.e. as determined by the umask setting).

Anyway, some colleagues of the related operating system have a similar problem: [http://www.aquataskforce.com/view/234](http://www.aquataskforce.com/view/234)

It might indeed be specific to UDF disks, as suggested in the thread I showed and in this one: [http://brainstorm.ubuntu.com/idea/13052/](http://brainstorm.ubuntu.com/idea/13052/)

Here I learn it might be fixed within a year or so: [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/200462/comments/8](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/200462/comments/8)

---

### Post by Timi 9 on 2009-01-24
Thank you very much,now that's something new that I found out!I was thinking that it is a Gnome general related problem,but it's good to know that is hardware related bug!Thank you again,you have been helpful!:D

---

