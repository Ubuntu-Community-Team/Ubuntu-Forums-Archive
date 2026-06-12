---
title: "My entire partitiontable disappeared!"
date: 2006-05-06
forum: Desktop Environments
---

### Post by trommas on 2006-05-06
After installing from the beta livecd, everything went well. I booted up ubuntu, and sometimes windows (when I wanted to play).

Suddenly I got the message NTLDR missing (the windows boot manager)

I booted up from the livecd and tried to fix the problem, but couldn't figure it out.

Today when I booted from the livecd, my entire partitiontable is gone!!! I can't access any of my partitions.... All my stuff is gone :(

(Booting up with the winxpdisc also shows zero partitions)

HELP!

---

### Post by lha on 2006-05-06
Take a look at[ gpart]("http://www.stud.uni-hannover.de/user/76201/gpart/"). It is quite good at guessing partition tables.

---

### Post by trommas on 2006-05-06
[quote=lha]Take a look at[ gpart]("http://www.stud.uni-hannover.de/user/76201/gpart/"). It is quite good at guessing partition tables.[/quote] 
Thanks for the tip  ;)

I ran into some trouble with gpart:

dmesg returned alot (But I don't know if it's useful).

gpart /dev/hdc - Did not work (neither did ../hda or any other map I tried). 
It generated:

ubuntu@ubuntu:~$ gpart /dev/hdc
*** Fatal error: open(/dev/hdc): No such file or directory.

ubuntu@ubuntu:~$ gpart /dev/hda
*** Fatal error: ioctl(HDIO_GETGEO) failed: Invalid argument.


I'm running all this from the livecd. Would really like to get this working!

---

### Post by lha on 2006-05-06
Try 'sudo fdisk -l' to see device name(s) of your hard drive(s).

---

