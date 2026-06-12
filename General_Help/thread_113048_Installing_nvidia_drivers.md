---
title: "Installing nvidia drivers"
date: 2006-01-05
forum: General Help
---

### Post by _simon_ on 2006-01-05
I have downloaded the drivers from the nvidia site and have them in /home/simon/Desktop

I have gone into terminal and installed binutils via apt-get as it kept telling me to do

Now when i try and install the drivers by sudu sh NVIDIA-Linux-x86-1.0-8178-pkg1.run it tells me I need to exit X server

I'm told to exit i need to use sudo init 3

When i do this, all it does it drop me to another command line and nothing happens.

What am I doing wrong?

---

### Post by mindwarp on 2006-01-05
[QUOTE=_simon_]I have downloaded the drivers from the nvidia site and have them in /home/simon/Desktop

I have gone into terminal and installed binutils via apt-get as it kept telling me to do

Now when i try and install the drivers by sudu sh NVIDIA-Linux-x86-1.0-8178-pkg1.run it tells me I need to exit X server

I'm told to exit i need to use sudo init 3

When i do this, all it does it drop me to another command line and nothing happens.

What am I doing wrong?[/QUOTE]


Once you do a "sudo init 3", then cd /home/simon/Desktop and do a sudo sh NVIDIA-Linux-x86-1.0-8178-pkg1.run

---

### Post by rjwood on 2006-01-05
see this thread [HOWTO: Latest NVIDIA drivers - Ubuntu Forums]("http://www.ubuntuforums.org/showthread.php?t=75074&highlight=nvidia")
  Good Luck---you'll get it going..

---

### Post by mitchjala on 2006-01-05
Hi!

What's the linux command for Traceroute?


Thanks

---

### Post by _simon_ on 2006-01-05
rjwood, i think i have it installed now but how do i check? (i'm new to linux)

EDIT: Just found Nvidia settings in System Tools so i guess it worked. Driver version 1.0-7667

---

### Post by tim15856 on 2006-01-05
If you see the nVidia splash screen when you login, then the drivers are installed.

---

### Post by handy on 2006-01-06
Automatix makes it all so easy!

Look here:

[http://ubuntuforums.org/showthread.php?t=80295](http://ubuntuforums.org/showthread.php?t=80295)

Cheers,

handy

---

