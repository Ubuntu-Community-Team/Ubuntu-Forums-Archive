---
title: "No screen or text terminal"
date: 2009-07-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Krister Johansson on 2009-07-06
Hi. I´ve had Ubuntu 8.10 on my Dell Latitud D630 for a while and it worked fine, but after upgrading to 9.04 I have nothing but a grey screen. 

When turning it on it looks like a normal booting and the Ubuntu colours also appear, but then the screen flashes a couple of times and become grey.

Been looking for solutions in this forum and the rest of www and a lot of people seem to have this problem with Dell or HP. I will avoid theese computers next time. It seems like I need the text terminal but I cannot get the terminal working. (Tried ctrl+alt+f2)

I have also tried some different changes in the booting menues but without success. (I´m attaching the boot menues)

Any good ideas?

---

### Post by coffeeaddict22 on 2009-07-07
Hi Krister,
At a guess, you'll be running an Intel video chip- it's the built in one.  The Intel drivers are part of the Linux kernel, and they're getting a lot of work done on them lately; unfortunately, that translates as "they're broken".  
First, if you aren't sure, then you can try booting into the recovery console (that's the one below the option you usually choose on the GRUB boot menu), and try the "repair my graphics" option in there.  It'll give you a chance to copy out any important files you need to back up as well.

There are apparently working Intel graphics drivers out there, but it'll take a fair bit of work.  If you're intereseted, have a look [here.]("http://webupd8.blogspot.com/2009/05/graphic-video-drivers-ubuntu-repository.html")
The best option at the moment (if you are needing the Intel driver, and that's not 100% certain) is to revert to 8.10 or 8.04 until 9.10 comes out.

---

### Post by Krister Johansson on 2009-07-08
Hi coffeadict22.
Thanks a lot for your answer. I will sit down and give it a try this weekend. For the record I've started from the recovery console without luck. I dont remember now how it looked like in there but, -if there are important files there to copy, which files would that be and where should I put them.?

---

### Post by coffeeaddict22 on 2009-07-09
Hi,
The way Linux sets up, your home folder is where all your personal files are kept.  so, if you can get in to a recovery console, plug in a USB, mount it if need be, and then change into your home directory ( cd /home/xxxx ); pwd stands for print working directory if you need to check where you are; ls lists the files in the directory you're in.  cp is the copy command; cp /home/ian/xxxx /media/disk/yyyy will copy file xxxx from my home directory to a USB key mounted at /media/disk

Post back if you need help manually mounting a USB key.

---

