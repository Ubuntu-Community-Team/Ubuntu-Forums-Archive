---
title: "ATI Mobility Radeon X1300 - driver?"
date: 2009-04-30
forum: Desktop Environments
---

### Post by po11ution on 2009-04-30
Hi all
I have an IBM thinkpad T60 running Intrepid - the display works fine, but I can't enable desktop effects (pretty uncool).
How do I go about installing the proper driver for the ATI card?

I can't seem to find this anywhere. I fiddled with some xorg.conf settings, but didnt' have any luck.
Idea's?
Thanks

---

### Post by AlecJ on 2009-04-30
here you are..
[http://news.softpedia.com/news/Latest-ATI-Linux-Driver-Introduces-Support-for-Ubuntu-9-04-109720.shtml](http://news.softpedia.com/news/Latest-ATI-Linux-Driver-Introduces-Support-for-Ubuntu-9-04-109720.shtml)

---

### Post by lvleph on 2009-04-30
ATI put this card on its Legacy List, so it is not really supported anymore. Well, as far as new drivers go. You will have to use the old driver, but if you are on Jaunty it won't work. This is why I am still on Intrepid. I can't believe a less than year old comp has hardware in legacy. What a sham!

EDIT:
> **AlecJ said:**
> here you are..
[http://news.softpedia.com/news/Latest-ATI-Linux-Driver-Introduces-Support-for-Ubuntu-9-04-109720.shtml](http://news.softpedia.com/news/Latest-ATI-Linux-Driver-Introduces-Support-for-Ubuntu-9-04-109720.shtml)
I am pretty sure that driver will not work. And the old driver doesn't work with the new xorg.

---

### Post by AlecJ on 2009-04-30
Thats a blow, I used my old xorg.conf with the latest Nvidia driver on 9.04.
If it's a binary driver it's worth a go?

---

### Post by po11ution on 2009-05-07
I can confirm that the ATI driver detailed in the previous posting did not work with Jaunty.
I did find an updated one from the ATI website - but this also failed to work. There must be some way of getting the Desktop Effects working on this display card.

I also tried using the repair video graphics option when booting - but i had to re-install to get the display operational again.
:-(

---

### Post by wabbalee on 2009-05-07
just a suggestion but have you tried looking for fglrx in the package manager, it states that it supports Radeon and Fire GL cards. I happen to have a machine somewhere that has the latter in it and it works great.

---

### Post by po11ution on 2009-05-07
thanks, will give it a go.
How does one roll-back to the previous video driver...getting tired of re-installing when video drivers fail.

---

### Post by Don1500 on 2009-05-07
I have Jaunty working with an ATI 9600, also discontinued, but I have all the wobbly windows, rotating desktops and 3D working. (Can't get the gears or aquarium to work, but that's probably me).

---

### Post by wabbalee on 2009-05-07
roll-back (a windows expression?) the video driver, the only way I know to get X working again after a failure, is to choose 'recovery mode' in grub on start up and let it 'try to fix X', for me that has worked most of the time. actually in recent times it hasn't failed on me.

if you getting tired of reinstalling, you should look into [clonezilla]("http://clonezilla.org/download/sourceforge/stable/iso-zip-files.php"), I am using version 1.0.10-8 and I think it is excellent. after the first time you have done it, it explains itself very well, it is just a matter of 'hitting the enter key, the arrow keys and change the suggested name a litle to your liking, and off you go. 15 minutes later you have a back up image of the selected partition that copies back even faster! there are many options but I leave everything to what it by default suggests and it just works.

---

### Post by Pifilatakanemu on 2009-05-08
I'm not really into the topic but a guy in a german forum helped my after installing the ati catalyst control center. try this commands to activate the working ati x13000 driver:
**apt-get purge xorg-driver-fglrx**
**apt-get autoremove**
[B]dpkg-reconfigure  -phigh xserver-xorg

so is there hope that the free driver will get good enough to avoid nasty graphical errors? i would rather wait than install 8.10 again.

[/B]

---

### Post by Pifilatakanemu on 2009-05-12
Hey,
what about the radeonhd driver? the wiki says it wasn't tested for 9.04, but might it improve the performance of the ATI X1300 ?

---

### Post by dazman19 on 2009-05-14
This sux man.
This sux so bad. And i tried 9.3, but apparently from what i know:

9.4 is not covering all ati radeon/firegl and 9.3 is the last supported release by ATI. 

==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: X.Org 7.4 and later releases 
Removing temporary directory: fglrx-install.plTsdT
root@daz-laptop:/home/daz/Desktop# aticonfig
aticonfig: No supported adapters detected
root@daz-laptop:/home/daz/Desktop#

Unless someone can tell me why this adapter is not found? 
I got an ati mobility radeon x1300 in this laptop.

---

### Post by wabbalee on 2009-05-15
The system I was referring to that runs good with the fglrx driver is running Hardy with a fireGL card. my daughter has an Acer Laptop TM44xx(?) with ATI video in it and running good as well also running Hardy, may be the problem is in Intrepid or Jaunty for this card.

I installed the fglrx driver with synaptic, I set the adapter and monitor brand and type in system settings, and I enabled the driver in 'hardware drivers'. then I did an X restart and it all worked. both systems are kept up to date.

---

### Post by butterdori on 2009-05-15
That is strange

I also have a thinkpad t60 with x1300 and compiz effects worked fine without any extra settings.. (both fglrx and open source drivers on 8.10, only open source drivers on 9.04)

Perhaps try thinkwiki.org?

---

### Post by OchoHa on 2009-05-18
I have an X1300 in my desktop machine at work, and have been running it with the radeonhd driver.  Compositing works in kwin4 provided I set compositing type to XRender.

I'm planning to try jaunty in the coming week or so.  I'll post my results.

---

### Post by phuturism on 2009-05-22
> **flohmann said:**
> I'm not really into the topic but a guy in a german forum helped my after installing the ati catalyst control center. try this commands to activate the working ati x13000 driver:
**apt-get purge xorg-driver-fglrx**
**apt-get autoremove**
[B]dpkg-reconfigure  -phigh xserver-xorg

so is there hope that the free driver will get good enough to avoid nasty graphical errors? i would rather wait than install 8.10 again.

[/B]

Thanks for this - saved my bacon on a jaunty upgrade.  I don't have any answers about compiz and advanced desktop effects but at least I can boot into gnome now.

---

### Post by tcpage on 2009-05-22
I also have a T60 with the very same graphics card, and I can confirm that I found it pretty much impossible to use in Jaunty.

It worked in Hardy Heron, and seems to work even better in Intrepid now, but I downloaded the restricted driver before updating, so that might be the answer.

---

### Post by deruberhanyok on 2009-05-24
Your display device should be supported by the open source [xorg radeon driver]("http://www.x.org/wiki/radeon") with plenty of acceleration for desktop effects. You don't need catalyst / fglrx. The newer versions have removed support for that class of device so they won't work anyways.

---

