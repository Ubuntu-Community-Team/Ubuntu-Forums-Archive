---
title: "xorg nvidia"
date: 2007-10-25
forum: Desktop Environments
---

### Post by dmsn on 2007-10-25
Hey
I have new Ubuntu 7.10 and i cant get my screen resolution as i want
1280x1024 with 75Hz.
My graphic card is Nvidia and here is my xorg.conf

[http://paste.ubuntu-nl.org/42059/](http://paste.ubuntu-nl.org/42059/)

What should i do?



Thanks for help.

---

### Post by Ecthelion on 2007-11-02
Hi,

I also installed gutsy gibbon and also have problems with the resolution.
And even more with the video acceleration.

I DO get the resolution as I want, BUT:

1. When I do it with the tool Ubuntu provides "Screens and Graphics", I get no hardware acceleration, so my nvidia isn't used. (when doing glxinfo I see that glx isn't enabled).

2. When I take the drivers on the nvidia website and install them, everything goes fine (untill see next)

But whatever method I try, when I have to reboot my whole computer (not only X), I have to do it all over again. Starts up in low graphs, so I have to change everything then restart X, or install (again) nvidia drivers and restart X.

Anyone experiencing those same problems?

---

### Post by Kuptis on 2007-11-02
I'm having the same problems as Ecthelion.

As for resolution settings are so scattered that sometimes I can get it but most of the time I can't.  I've read the documentation for the monitor and typed them in xorg.conf but to no avail.

I cannot get my onboard HD sound to work at all.

I'm thinking of buying Windows when I can save up enough.

---

### Post by chicoicho on 2007-11-02
> **dmsn said:**
> Hey
I have new Ubuntu 7.10 and i cant get my screen resolution as i want
1280x1024 with 75Hz.
My graphic card is Nvidia and here is my xorg.conf

[http://paste.ubuntu-nl.org/42059/](http://paste.ubuntu-nl.org/42059/)

What should i do?



Thanks for help.
Hello change this section :
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

when a HorizSync  change to 28-85 and 
change the VertRefresh  to 43-85
just try

---

### Post by tuxulin on 2007-11-02
im new to ubuntu just installed it 20 mins ago and i had that problem too
what you need to do is
boot up into terminal mode then 
type this in **dpkg-reconfigure xserver-xorg**

basically follow it through and accept all the pre chosen answers
until you come to the resolution screen choices then at this time
select all screen sizes that you need then continue till all is completed

reboot and then Njoy
Tux

---

### Post by rykel on 2007-11-03
I have tried changing the xorg.conf file manually and through xserver-xorg BUT the problem persists.

I have used both nvidia-glx-new and official nvidia binary, and while it works, the low-resolution problem returns after a reboot.

Can you help me please??

---

### Post by Ecthelion on 2007-11-03
> **tuxulin said:**
> im new to ubuntu just installed it 20 mins ago and i had that problem too
what you need to do is
boot up into terminal mode then 
type this in **dpkg-reconfigure xserver-xorg**

basically follow it through and accept all the pre chosen answers
until you come to the resolution screen choices then at this time
select all screen sizes that you need then continue till all is completed

reboot and then Njoy
Tux

Hi, thanks for the tip, but I already did this, with the same result.
Tried dpkg-reconfigure xserver-xorg -phigh, without phigh, tried doing it with advanced settings, ....
Even manually doing it and editing the xorg.conf file.
Works when you restart your X,
but when you restart your pc you have to do it al over again.

THAT is the whole problem.
Not getting the settings right, but getting them to survive a reboot...

Since we are already a fw with this same problem, I'm going to check if there's no bug report about this.

Everyone with this problem (xorg settings lost after reboot) are using nvidia cards, right?

---

### Post by Ecthelion on 2007-11-03
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/3731](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/3731) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Posting this as double-post because otherswise I can't fill in the Launchpad Bug URL :-)

The bug report that I found and that describes this problem is already rather old:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/3731](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/3731)

2 years old, but since the last message posted is about 18hours ago, it's still not fixed.

Strangly enough I only have this issue since I installed ubuntu 7.10.

---

