---
title: "kde + xgl +compiz = 48 hours of pain"
date: 2006-08-26
forum: Desktop Environments
---

### Post by kdexglpsycho on 2006-08-26
i'm goin' crazy trying to get this installed.

there are a TON of so called "how-to" guides but, not a one has gotten this done for me.

does anyone have ideas where i can find info on how to REALLY make this work?

this = login into kde using xgl and compiz

all the how-tos i've read seem to be monkey's copy pasting until something works. i'd LOVE to write one that explains wtf is going on.

my system = intel 855 with kubuntu/dapper

if not, please, shoot me

/me crying

---

### Post by Crooksey on 2006-08-26
ATI or nvidia?

---

### Post by kdexglpsycho on 2006-08-26
intel

CAN do:
set up an xsession for XGL where i login via kdm and start XGL with an xterm. from here i can "startkde". once in kde i can see Xgl running.

UNABLE to do thus far:
1) "startkde" automagically after logging in through kdm
- when i change the "xterm" to "exec startkde" all i get is an Xgl session
2) start compiz
3) make the cube rotate and all the cool stuff i'll sometime later next week tell myself was well worth the 2 past miserable days with very little sleep.

---

### Post by bullgr on 2006-08-26
i don't know why it is so hard for you.

i done this in a few minutes... it was suprisely so easy.

maybe you use not a good howto...

first of all make sure you have installed the drivers for your graphic card.
better you use the drivers included in dapper to avoid to recompile the kernel...

you can find a howto to install the driver to you graphic card. using the included ones makes it very easy.
here is a howto for ati cards
> [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
and here how to install nvidia drivers
> sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-glx-config enable
you need this because xgl needs to have 3d acceleration of your graphic card.

after you done it and you have 3d acceleration go here > [http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389)
and follow this howto.
it works for sure and is very easy (i advise to use the second method to keep the gnome session, you never know).

---

