---
title: "ATI Radeon X1600 Tutuorial"
date: 2007-11-12
forum: Desktop Effects &amp; Customization
---

### Post by diablo69-0621 on 2007-11-12
7.10 && Ati Radion X1600

First things first--download this

[http://www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-8.42.3-x86.x86_64.run)

1.  Open a term, cd to the file, and type in "sudo bash ati-driver-install-8.42.3-x86.x68_64.run
2.  When the program opens, click the install button.
3.  Open a term and type in "sudo gedit /etc/default/linux-restricted-modules-common"
You should see something like this 

DISABLED_MODULES=""

Change the above to 

DISABLED_MODULES="fglrx"

4.  Open up the restricted driver manger, and put a tick next to the ati box.
5.  Log out and log back in--enjoy 3D gaming

Here is the part where I am suppose to thank all the sites where I got my info from...however--there are far to many sources to list, so thank you to all the sites that I searched to find this information and compile it into this tutorial.

---

### Post by DrSkeezix on 2007-11-12
i've followed all this, but my problem is strange.

everything seems great until i try and watch a video.

no matter what program i use all i get is a blank video window. it plays. i heard sound, but nothing but a black video window.

do you know anything about this?

running the new gutsy with a radeon x1950 pro 512mg on an amd dual core dual cpu 64bit system.

---

### Post by DrSkeezix on 2007-11-12
ha!

i got it fixed.

seems i had to remove the xorg-driver-fglrx, then re-install it.

now my videos play perfectly.

now to try out my steam games.

:popcorn:

---

### Post by diablo69-0621 on 2007-11-12
As much as I hate to admit it---gaming on linux really isn't worth all the trouble--I am going to install vista and dual boot ubuntu...that way I avoid paying $15 dollars every 3 months for cedega.

---

### Post by Drewbkilla on 2008-01-09
Good tutorial, However im a little confused.

I am a Windows user and was introduced to ubuntu really recently. I really dont know linux at all, I do love it and I first was unable to get ANY effects to work  (stretchy windows)

after setting up the ati card, that worked but I've been told the gui looks amazing and even better than vista.

I must be doing something wrong becasue this gui only looks a little better than MAC OS9.   I have no translucence in my windows but I dont get an error,  everything from a visual standpoint does look good.

I have no idea as to testing to see whats even working,  if any of you came from a windows background you should understand the loss im at,  Im use to video cards just working.

any tips on installing a new catalyst driver or anything for that matter would be greatly appreciated,   

ALSO: if it helps,  when I set my visual effects, it seems that the only thing I get at all is the stretchy windows,  but no message that something isnt functioning properly.

Please help this could be ubuntu exclusive user.   lol

Thanks!  :)

---

