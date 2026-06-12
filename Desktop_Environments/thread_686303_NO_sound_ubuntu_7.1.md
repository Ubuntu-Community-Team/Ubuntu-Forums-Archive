---
title: "NO sound ubuntu 7.1"
date: 2008-02-03
forum: Desktop Environments
---

### Post by alex_pof on 2008-02-03
hi i just installed ubuntu 7.1 and i have no sound. this is the computer i have and its specs.  [http://reviews.cnet.com/desktops/gateway-gt4022-media-center/4507-3118_7-31975712.html?tag=specs](http://reviews.cnet.com/desktops/gateway-gt4022-media-center/4507-3118_7-31975712.html?tag=specs)

---

### Post by jan quark on 2008-02-04
do you get any error messages? 

did you check the volume control?
right click on it and open the volume control

---

### Post by alex_pof on 2008-02-05
No, no error messages. and i checked the sound settings and they are not muted or at 0.

---

### Post by C-ramm on 2008-02-06
Hi there!

What is your output on:

sudo /etc/init.d/alsasound status

It may be that your drivers arent loaded properly, and there are a few things that you can try.

1. Following the tutorial to load the latest Alsa Drivers:
[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

*NOTE* you will need to install  libncurses5-dev  before you ./configure the 'utils'

OR

2. Try the following:
> sudo vi /etc/modprobe.d/alsa-base

And add

> options snd-hda-intel model=auto

To the end of the file and reboot.

OR ( And this is where I FINALLY got my sound working again )

3.Follow this:

[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/]("http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/")

To check the 'Unsupported Gutsy Backups" go into Synaptic Package Manager and click on the Updates Tab.

If you get any errors, or if this process doesnt work, post your results and we can go from their ;-).

---

