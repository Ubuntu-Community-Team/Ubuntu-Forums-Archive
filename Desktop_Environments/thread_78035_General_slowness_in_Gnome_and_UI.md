---
title: "General slowness in Gnome and UI"
date: 2005-10-17
forum: Desktop Environments
---

### Post by emil on 2005-10-17
Hi,

just installed Breezy badger on my Dell M20 and I'm quite pleased. Sound, graphics, mouse etc all works. BUT, when I drag windows they lag and leave alot of marks and trails. It's an ATI Mobility FireGL V1300 card in the machine, I've not installed any other drivers or done any tweaking. 

The question is if this is normal behaviour, have any of you others experienced the screen laggings and window trails? Will it help if I install ATI's drivers etc?

thanks

Emil

---

### Post by shidai.liu on 2005-10-17
[QUOTE=emil]Hi,

just installed Breezy badger on my Dell M20 and I'm quite pleased. Sound, graphics, mouse etc all works. BUT, when I drag windows they lag and leave alot of marks and trails. It's an ATI Mobility FireGL V1300 card in the machine, I've not installed any other drivers or done any tweaking. 

The question is if this is normal behaviour, have any of you others experienced the screen laggings and window trails? Will it help if I install ATI's drivers etc?

thanks

Emil[/QUOTE]

I'm not using ati card. I can't help much. But the phenomena is defintely uncommon. Breezy is slow but not that slow:)

---

### Post by nobby_trussin on 2005-10-17
my best bet would be that you need to install your manufacturer's drivers for your graphics card as the ones that come with the OS will hardly be optimal. its the only thing that i could think of that would cause such a slow down

you'd have to look on their site for that and with a bit of luck they'll be straight forward to install

regards

Dan

---

### Post by RustyFox on 2005-10-17
I'm having similar trouble, with an ATI card and with a Matrox G400.

However, I got the ATI card working much better by apt-get install'ng

xorg-driver-fglrx
linux-restricted-modules-k7

(my kernel is the -k7 varient, you may likely want -686 or -386 instead depending on whats running presently)

Change the ati drive to fglrx in /etc/X11/xorg.conf and add fglrx to /etc/modules to load the kernel module (from the restricted package).

Now when X starts, things are much faster, although 2D still feels a little below par. My matrox machine however, after years of sterling service with XFree86, is just as slow as the ati machine without the fglrx driver.

---

### Post by emil on 2005-10-18
Thanks for all replies.

So the general concensus is that performance will/might increase if installing drivers? Because I read somewhere on this forum that 2D performance is not likely to increase by fiddeling with ATI drivers etc.

I'll give it a try tonight.

/Emil

---

### Post by jogi on 2005-10-18
hi rustyfox :)

normally i use an i386 kernel image and xfce
at start up i get a splash screen that says 'Ubuntu'
just "for fun" i installed the linux-restricted-modules-686 package and when i reboot selecting kernel version 686 the splash screen says 'xubuntu'
i found that really strange :)

oh and the slowness of xfce has not changed
i have already tried a lot, but when i move or resize windows the cpu utilization goes through the roof and the movement gets blurry 

it really sucks! otherwise (x)ubuntu is really great

---

### Post by liquid boy on 2005-11-26
i'm having exactly the same troubles :S (prosavage ddr). 
i tried "BeatriX"  - with none of those problems, but there must be a way of fixing it in ubuntu...

---

### Post by dezier on 2005-11-27
I think this is related to what is discussed in this thread [http://ubuntuforums.org/showthread.php?t=18197](http://ubuntuforums.org/showthread.php?t=18197) (... reading it doesn't make you much wiser though)

---

