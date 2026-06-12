---
title: "Debian 4.0 r5 image number issue"
date: 2008-10-27
forum: Debian
---

### Post by biszkopt on 2008-10-27
Hi i wanted to download Debian 4.0 r5 but before i do that i have 1 question. Anybody know what's with that debian-40r5-i386-DVD-1.iso and then there is debian-40r5-i386-DVD-2.iso and so on. What image i should download (i know that maybe that's a noobbish question but who cares)??

---

### Post by Sorivenul on 2008-10-27
DVD1 is everything the average user would need, and then some.  I personally think the DVDs are overkill for an average user, but that's entirely up to you, the user.  CD1 should be fine for many users, IMO.  Ther are GNOME, KDE, and Xfce editions of CD1.  Any particular reason you think you need the DVD?

---

### Post by kerry_s on 2008-10-28
just grab the net installer:
[http://cdimage.debian.org/debian-cd/4.0_r5/i386/iso-cd/debian-40r5-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r5/i386/iso-cd/debian-40r5-i386-businesscard.iso)

a straight install gives you gnome.

kde version:
[http://cdimage.debian.org/debian-cd/4.0_r5/i386/iso-cd/debian-40r5-i386-kde-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r5/i386/iso-cd/debian-40r5-i386-kde-CD-1.iso)

xfce4 version:
[http://cdimage.debian.org/debian-cd/4.0_r5/i386/iso-cd/debian-40r5-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r5/i386/iso-cd/debian-40r5-i386-xfce-CD-1.iso)

---

### Post by Ozor Mox on 2008-10-28
> **kerry_s said:**
> just grab the net installer:
[http://cdimage.debian.org/debian-cd/4.0_r5/i386/iso-cd/debian-40r5-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r5/i386/iso-cd/debian-40r5-i386-businesscard.iso)

a straight install gives you gnome.

kde version:
[http://cdimage.debian.org/debian-cd/4.0_r5/i386/iso-cd/debian-40r5-i386-kde-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r5/i386/iso-cd/debian-40r5-i386-kde-CD-1.iso)

xfce4 version:
[http://cdimage.debian.org/debian-cd/4.0_r5/i386/iso-cd/debian-40r5-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r5/i386/iso-cd/debian-40r5-i386-xfce-CD-1.iso)

I'm sure you already know this, but just to point out that if you get the netinstall from [here](http://www.debian.org/distrib/netinst) you don't need to worry about default desktop environments because there are none. You can install whichever you like when the base installation is complete.

---

### Post by kerry_s on 2008-10-28
> **Ozor Mox said:**
> I'm sure you already know this, but just to point out that if you get the netinstall from [here](http://www.debian.org/distrib/netinst) you don't need to worry about default desktop environments because there are none. You can install whichever you like when the base installation is complete.

and you've tried it? i don't think debian has just a base installer, you always have to uncheck the desktop packages if you want just the base.
all those links point to the same place as mine->
[http://cdimage.debian.org/debian-cd/4.0_r5/i386/iso-cd/](http://cdimage.debian.org/debian-cd/4.0_r5/i386/iso-cd/)

---

### Post by Sorivenul on 2008-10-28
> **kerry_s said:**
> and you've tried it? i don't think debian has just a base installer, you always have to uncheck the desktop packages if you want just the base.
all those links point to the same place as mine->
[http://cdimage.debian.org/debian-cd/4.0_r5/i386/iso-cd/](http://cdimage.debian.org/debian-cd/4.0_r5/i386/iso-cd/)

If you use the "netinstall" image instead of the "businesscard" image, the complete base system is included.  If you do the install without being connected to the network, only the base system is installed.  Do your manual configuration afterward to get networking running, and you have a ground up system without having to uncheck things you don't want.  This is my preferred way of installing Debian.

---

### Post by kerry_s on 2008-10-28
> **Sorivenul said:**
> If you use the "netinstall" image instead of the "businesscard" image, the complete base system is included.  If you do the install without being connected to the network, only the base system is installed.  Do your manual configuration afterward to get networking running, and you have a ground up system without having to uncheck things you don't want.  This is my preferred way of installing Debian.

ohh, okay, i never tried installing without a network connection. :lolflag:

i always use the "businesscard" and just uncheck the 2 things, no big deal and no need to update after the install, just go straight to installing.

i'll probably try the net 1 on the next install, i'm converting this 1 for mom, the cd drive on her laptop no longer works so i'm doing the setup on mine, than i'll just swap drives.

i always like to try something different for each install.

for moms i'm swallowing rox into the desktop and the icons are all in there, with separate admin and office folders. very light and fast, still not sure if i'm going that way though. 
how's this look? see pic

---

### Post by Sorivenul on 2008-10-28
kerry_s:
Looks good.  That's a nice, simple setup.  I'm not a personal fan of ROX, but I may try to replicate that setup to some extent when I next have time.  

@OP:
Let us know how you decide to go.  If you have more problems, we'll be glad to help.

---

### Post by kerry_s on 2008-10-28
> **Sorivenul said:**
> kerry_s:
Looks good.  That's a nice, simple setup.  I'm not a personal fan of ROX, but I may try to replicate that setup to some extent when I next have time.  

@OP:
Let us know how you decide to go.  If you have more problems, we'll be glad to help.

i just want to try something different than the usual rox pinboard were the icons are on the desktop, every one does that. :lolflag:
the resource use is still super low, i have 450mhz 256mb ram on mine, her's is 1.3mhz 512mb ram, on mine everything opens instantly, her's should look even faster. 
check out my top, i have it auto hiding on the left, but i'll remove it when it go's into hers cause she don't monitor her stuff like i do. i have the radio on(pandora.com), but firefox is usually 0.3 cpu

---

### Post by Ozor Mox on 2008-10-29
> **kerry_s said:**
> and you've tried it? i don't think debian has just a base installer, you always have to uncheck the desktop packages if you want just the base.
all those links point to the same place as mine->
[http://cdimage.debian.org/debian-cd/4.0_r5/i386/iso-cd/](http://cdimage.debian.org/debian-cd/4.0_r5/i386/iso-cd/)

I have tried it, I just didn't really consider the step of unchecking the desktop environment noteworthy, and doing so gives you a base installation of Debian. The default desktop environment is GNOME though, you are right.

---

