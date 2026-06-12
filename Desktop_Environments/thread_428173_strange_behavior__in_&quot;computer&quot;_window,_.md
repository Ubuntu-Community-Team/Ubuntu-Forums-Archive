---
title: "strange behavior  in &quot;computer&quot; window, to mount disk"
date: 2007-04-30
forum: Desktop Environments
---

### Post by 1ino1eum on 2007-04-30
Hi.
ok, I have another ext3 partition.
I want to mount it (but not every time , so without the auto option), and being able to write on it .
So , I open the "computer" window, in gnome.
I can see my disk, unmounted. I mount it. but then I can't write anything in it, and neither I can't even browse folders in this partiton !.
if I right click on the dis, I can see that gnome-volume-manager set those option automaticaly on this disk :
rw nosuid nodev noexec data=ordered.
so, what should I do to be able to browse and write on this disk ?

Another question :
the first time I want to mount this disk, gnome ask me for my root password. Then it s memorized and it doesnt ask anymore.
I would like to be able to mount it without being asked for my root password, even for the first time of my session.

thank you

I know there my be other solutions by editing fstab, but I would like to keep it simple and use only gnome interfaces.

---

### Post by Theimon on 2007-05-05
Pmount lets you mount devices without root privileges. ```
sudo aptitude install pmount
```
Then at the command line use the pmount command instead of sudo mount.

---

### Post by 1ino1eum on 2007-05-05
I dont use any command line to mount my partition, but just click on the icon of the disk ... then it ask for my root password, and the partition is mounted.
How can I use pmount while just cliking on the icon ?
thanks

---

