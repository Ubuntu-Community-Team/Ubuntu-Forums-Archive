---
title: "Is thr a solution for my hard disk sound ?"
date: 2006-08-29
forum: Desktop Environments
---

### Post by ss0007 on 2006-08-29
Hi ,
One of my hard disk was crashed due to a bug i recently saw in the post 
[http://ubuntuforums.org/showthread.php?t=79055&page=5&highlight=hard+disk+sound](http://ubuntuforums.org/showthread.php?t=79055&page=5&highlight=hard+disk+sound)

And now, this sound has happened again in my new hdd too ,i tried  to solve it by applying this, 

Edit the /etc/hdparm.conf and add a line at end :
command_line {
       hdparm -q -B255 -q -M128 -q -c1 -q -m16 -q -W0 -q -d1 /dev/hda
}

But stiil , atleast once , i get the sound in my hard drive whenever i boot ubuntu. So i stopped booting to Ubuntu now, until thr exists a clear sloution. 

Can someone help me how to solve this issue ...
I use Samsung hdd to boot Ubuntu ...

TIA

---

