---
title: "Ubuntu freezes after login"
date: 2006-02-02
forum: Desktop Environments
---

### Post by SilentWarrior on 2006-02-02
Hi, I am new to ubuntu, so my info about the problem will be simple and with low details :( 

Anyway,

My ubuntu freezes after i login, it shows the ubuntu logo (i think) all crazy (cant even read nothing) and just stays there...

A friend that uses ubuntu gave me some commands and helped me, but it didnt worked.

Heres what he told me to do :

 dpkg-reconfigure xserver-xorg (did it until the end, but i am not sure if configured it correctly, at least i think so)
 sudo apt-get install xserver-xorg-driver-nv (saied that i already have the lastest drivers)

My system :
AMD 64 bit 3800+ (not dual core)
1GB DDR
BGF GeForce 7800 GT OC with 253 mb GDDR3 (nvidea chip)

Have almost no experience at linux, but both Suse and ubuntu live cds had the same problem.

I am using ubuntu 5.10 64-bit PC, but already tryed with the 32 bit version and had the same error.

Say if you need more information.

With the best regards
SilentWarrior

PS : thx in advance for any reply :)

---

### Post by SilentWarrior on 2006-02-02
Well, i fixed my problem, where is how i done it :
(please refer to [http://ubuntuforums.org/showthread.php?t=101834&highlight=crash+login](http://ubuntuforums.org/showthread.php?t=101834&highlight=crash+login) )

I am not sure what option make my problem be solved as i tryed all of them at the same time :P first :

I tryed to configure with the Vesa driver instead of the NV.

Then I tryed to change my 
HorizSync and VertRefresh 

as the user "taurus" sayed :
> 
After Ubuntu finishes booting, hold down <Ctrl><Alt>F2 and that would put you to a terminal. Log in and use a text editor to edit your /etc/X11/xorg.conf

sudo pico /etc/X11/xorg.conf

Then, make sure both horizontal & vertical are correct (those are the values for my Dell 17" monitor so better use the correct ones from the manual for your monitor),

HorizSync 28-51
VertRefresh 43-60

Then, make sure your video card driver looks like this,

Driver "nv"

Save it and reboot and hopefully, everything is fine now...


Well, I hope I can help someone :)

---

### Post by SilentWarrior on 2006-02-02
Ok, I retested the last settings, and here is what I got :

You cannot use the "nv" driver, use "vesa" instead.

---

### Post by dorath on 2006-02-24
Changing the driver to "vesa" worked for me as well.  No other changes necessary.

Same initial problem: fresh install, screen more or less locks up with a funny bar in the middle after logging in.  7800 card here too.

Thanks for your help.

EDIT:  Setting it to "nvidia" also works.  I was curious, had to try. :-)

---

### Post by MighMoS on 2006-02-24
[QUOTE=dorath]Changing the driver to "vesa" worked for me as well.  No other changes necessary.

Same initial problem: fresh install, screen more or less locks up with a funny bar in the middle after logging in.  7800 card here too.

Thanks for your help.

EDIT:  Setting it to "nvidia" also works.  I was curious, had to try. :-)[/QUOTE]
Yes, but nvidia is the proprietary driver.  It offers 3d acceleration, but due to the fact that it is closed source, merely loading it will taint the kernel, and in the unlikely situation that something goes wrong, you're SOL on finding out why.  nv is the open source driver that offeres no 3d acceleration, but doesn't require a kernel module.  Vesa is a generic driver that should work with any card.

---

