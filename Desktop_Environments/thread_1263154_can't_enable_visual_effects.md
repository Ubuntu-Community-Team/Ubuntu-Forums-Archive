---
title: "can't enable visual effects"
date: 2009-09-10
forum: Desktop Environments
---

### Post by igeek5 on 2009-09-10
:( i just installed ubuntu 9.04 a few months ago and i can't enable visual effects!
All i know right now is that i have a 64mb nvidia geforce2 mx graphics card.

---

### Post by wojox on 2009-09-10
Go to System > Administration > Hardware Drivers and is your driver activated?

---

### Post by igeek5 on 2009-09-10
yes

---

### Post by wojox on 2009-09-10
Ok go to System > Preferences > Appearance > Visual Effects > Extra

---

### Post by igeek5 on 2009-09-10
it flashed alot then poped up with "could not enable visual effects":confused:

---

### Post by wojox on 2009-09-10
In your hardware drivers are you using the 185.XXX

---

### Post by igeek5 on 2009-09-10
i don't know

---

### Post by igeek5 on 2009-09-10
can someone please help please!

---

### Post by kierpaul on 2009-09-25
Go to Accessories----Terminal and paste these in. Paste these directly and your 3d acceleration should work. I spent weeks on this. Here you go:

sudo sh -c "echo 'deb [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) jaunty main' >> /etc/apt/sources.list"

sudo sh -c "echo 'deb-src [http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu](http://ppa.launchpad.net/nvidia-vdpau/ppa/ubuntu) jaunty main' >> /etc/apt/sources.list"

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CEC06767

sudo apt-get update && sudo apt-get install nvidia-185-modaliases nvidia-glx-185

If there is an error go to system-----administration------hardware drivers and enable it there! Take it easy and let me know how it comes out!

---

### Post by tantonovich on 2009-09-26
Worked flawlessly for me!  Thanks for the post!  This one is n00b proof :)

---

### Post by kierpaul on 2009-09-26
Do not forget to mark this thread as solved so others can benefit from it...your very welcome! You can do this by clicking on thread tools and selecting solved! Cheers!

---

