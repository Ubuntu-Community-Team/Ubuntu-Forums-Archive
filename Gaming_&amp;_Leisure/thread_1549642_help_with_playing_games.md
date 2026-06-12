---
title: "help with playing games"
date: 2010-08-10
forum: Gaming &amp; Leisure
---

### Post by Thorbenn on 2010-08-10
hi,

i want to play games on my laptop with ubuntu 10.04 but when i start games like assault cube or open arena they are very very slow. even headgewars is slow. supertuxkart has blue lines all in it that you can't play it but games like wormux or super tux work fine. wine does the same weird thing a 2d shooter called soldat also is verz very slow.

to my laptop specs:

Ati Radeon x1200
Amd Turion 64 x2  2,2 Ghz
2gb DDR2 Ram

could it be the ati driver and if so where do i get the one i need? the games run fine under windows but not ubuntu :(

---

### Post by bergfly on 2010-08-10
Sounds like you are missing the drivers for the ATI card. Go to the hardware drivers section

[IMG]http://static.howtoforge.com/images/compiz_fusion_ubuntu_10.04_nvidia/1.jpg[/IMG]

When this loads it should ask you if you want to activate the ATI drivers. You will need a reboot once it has installed

---

### Post by Thorbenn on 2010-08-10
okay when i go to hardware drivers it tells me searching for drivers and then a window pops up "no proprietary drivers are in use on this system"

---

### Post by Naiki Muliaina on 2010-08-10
ATI Discontinued support for that card on Linux a while ago I believe. Might be able to find some old drivers if you search enough, or downgrade to Jaunty.

---

### Post by Thorbenn on 2010-08-10
hmm :( ,

found a driver that says radeon x1200 is included but doesn't install. and what do you mean with jaunty ? new to ubuntu :)

this is the driver i tried [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx)

---

### Post by efikkan on 2010-08-10
You are either stuck with an old version of Ubuntu or the open source drivers, if the laptop manufacturer does not offer such drivers. Wich model is your computer?

---

### Post by Naiki Muliaina on 2010-08-10
Not entirely sure if this will work (I believe it needs an older kernel... Which might be why they are not installing...).

Open a terminal and copy pasta this into it :

> cd Downloads

chmod +x ati-driver-installer-9-3-x86.x86_64.run

sudo ./ati-driver-installer-9-3-x86.x86_64.run

I think it gives you some instructions. Just follow them and it should work.

---

### Post by Thorbenn on 2010-08-10
computer model is toshiba p305d


comes up an error

Error: ./default_policy.sh does not support version
default:v2:i686:lib::2.6.32-24-generic; make sure that the version is being correctly set up by --iscurrentdistro

---

### Post by LowSky on 2010-08-10
sorry but your really out of luck.

The ATi driver only supports cards series HD2xxx and higher.

All older products have no more support.

If you really need 3d support for that card I believe you will need Ubuntu 8.04, anything higher will not uspport your hardware.

The older driver will not run on the newer verisons of Xorg and that is the problem and why 8.04 ws the last known working version.

---

### Post by Thorbenn on 2010-08-11
isn't there a way that i can get the old xorg on 10.04? and 9.10 won't support my card either?

---

