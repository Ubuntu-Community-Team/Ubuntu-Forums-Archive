---
title: "Compix Fusion Help."
date: 2008-02-28
forum: Desktop Effects &amp; Customization
---

### Post by shooting_rubber on 2008-02-28
Hello,

I was just wondering if it is possible to get Compix Fusion in Ubuntu 7.10?  If it is possible then how do you install it?

Thanks.

---

### Post by igknighted on 2008-02-28
> **shooting_rubber said:**
> Hello,

I was just wondering if it is possible to get Compix Fusion in Ubuntu 7.10?  If it is possible then how do you install it?

Thanks.

It's installed by default (and enabled on all capable systems).  Go to system->preferences->appearance to make sure.

---

### Post by jan quark on 2008-02-28
if you encounter problems enabling the effects please tell us what your graphic card is
and we will find a solution

---

### Post by northern lights on 2008-02-28
If you posted this from Gutsy, you're most likely running compiz-fusion already.

I suppose you're looking to further customize it to what you've seen on a buddy's comp / screenshot / video. Should that be the case run ```
sudo apt-get compizconfig-settings-manager
``` Now "System > Preferences > Appearance" will have a new "custom" entry and "Preferences" button...

---

### Post by jayg1169 on 2008-02-28
Or synaptic> search compiz settings manager

---

### Post by shooting_rubber on 2008-02-28
> **jan quark said:**
> if you encounter problems enabling the effects please tell us what your graphic card is
and we will find a solution

I cannot install it because I don't have the driver installed for my "ATI Accelerated Graphics Driver".  How do you install this driver, along with a "Broadcom 43xx Chipset Family" driver/firmware?

Thanks Again.

---

### Post by jan quark on 2008-02-28
you can use either the application [envy ]("http://albertomilone.com/nvidia_scripts1.html")to install the drivers or

go to

system > administration > restricted driver manager

and check the box to download the needed drivers

I guess you have a wired connection on the linux machine ? and you want to enable wlan?
because without any inet connection it will be tricky

---

### Post by shooting_rubber on 2008-02-28
> **jan quark said:**
> you can use either the application [envy ]("http://albertomilone.com/nvidia_scripts1.html")to install the drivers or

go to

system > administration > restricted driver manager

I guess you have a wired connection on the linux machine ? and you want to enable wlan?
because without any inet connection it will be tricky

Yes, right now I am using a wired connection.  I've already tried using the Restricted Drivers Manager, but it won't work,  When I click enable the ATI Accelerated Graphics Card it says:

> The software source for the package

   xorg-driver-fglrx

 is not enabled.

And when I click install for the Broadcom 43xx Chipset Family it says something along the same lines.

EDIT: When I click enable the Broadcom 43xx Chipset Family Firmware it says:

> The software source for the package

   bcm43xx-fwcutter

 is not enabled.

Thanks.

---

### Post by jan quark on 2008-02-28
see your other post
I also posted there that you probably have to enable the software sources

---

### Post by shooting_rubber on 2008-02-28
> **jan quark said:**
> see your other post
I also posted there that you probably have to enable the software sources

Thanks for your help.  That worked, but now when I try to enable the effects in "Appearance", it won't let me.  A message comes up, but I cannot tell you exactly what it says, as I'm on my XP OS right now.  When I get back onto the Ubuntu OS, I will inform you guys on what it says.

Thanks.

---

### Post by jan quark on 2008-02-28
ok we are waiting here very thrilled

but it will be something with composite extension I guess

---

### Post by shooting_rubber on 2008-02-28
Okay, I'm back on Ubuntu.  When I go to System - Preferences - Appearance - Visual Effects and I click Extra it says:

> The Composite extension is not available

Thanks.

---

### Post by shooting_rubber on 2008-02-28
Any ideas?  I really want to be able to have the cool effects, and it doesn't seem to be working for me?

Thanks.

---

### Post by shooting_rubber on 2008-02-28
Any ideas?  And what is a composite extension?

Thanks.

---

### Post by -gabe-noob- on 2008-02-28
Broadcom 43xx Chipset Family" driver/firmware Is in the system=> administration=>restricted drivers. 


I only know cause I have the same exact thing heh!

---

### Post by shooting_rubber on 2008-02-28
> **-gabe-noob- said:**
> Broadcom 43xx Chipset Family" driver/firmware Is in the system=> administration=>restricted drivers. 


I only know cause I have the same exact thing heh!

Okay, thankyou for your help.  Any ideas on how I can enable the desktop effects?

Thanks.

---

### Post by igknighted on 2008-02-28
> **shooting_rubber said:**
> Okay, thankyou for your help.  Any ideas on how I can enable the desktop effects?

Thanks.

The fglrx driver in gutsy does not support composite.  You then have two options, and it depends on exactly which ATI card you have.  Actually there are three, but I wouldn't recommend the third unless desperate.

please run the command 'lspci | grep VGA' to determine exactly what card you have.  The lspci command prints a list of all hardware on the pci bus, the | is a pipe, which sends the output of the first command to a second one, and the grep VGA is a filter, so it will take the list from lspci and only print out lines that say VGA in them (which is only the graphics card).

---

### Post by shooting_rubber on 2008-02-28
Okay, my graphics card is ATI Radeon Xpress 1150.

Thanks.

---

### Post by jan quark on 2008-03-02
try the following

install this package with this terminal command
```

sudo apt-get install xserver-xgl
```

and then log off, change the session during login to xclient, and try to enable the effects one more time

---

