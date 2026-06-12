---
title: "VirtualBox on ubuntu 8.04 Hardy Heron"
date: 2009-04-16
forum: General Help
---

### Post by Subway on 2009-04-16
Hi :) looking to install VirtualBox can someone c&p the commands to type into the terminal? thanks again.

---

### Post by Peasantoid on 2009-04-16
sudo apt-get install virtualbox-ose
sudo apt-get install virtualbox-ose-modules-$(uname -r) # This is necessary for supporting some features, can't remember what at the moment.

---

### Post by Subway on 2009-04-16
Thanks :) i got virtualbox installed with xp now i want to know how i can get virtualbox to read a usb drive, i tried everything i could with the options.

---

### Post by bodhi.zazen on 2009-04-16
USB do not work with the ose, you need the PUEL from sun.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Simply download the .deb for Hardy, then double click on it.

---

### Post by Subway on 2009-04-16
Thank you :) now how about sharing files from linux to my virtualbox? thanks alot.

---

### Post by Subway on 2009-04-16
Can anyone tell me how to get com port 1 to work in virtualbox the xp will not reconize it :(

---

### Post by bodhi.zazen on 2009-04-16
> **Subway said:**
> Thank you :) now how about sharing files from linux to my virtualbox? thanks alot.

I share files either via a usbv device or samba. Samba works out of the box.

---

### Post by Subway on 2009-04-16
I figured that out but trying to get com port 1 to work on virtualbox xp has got my mind spun out in left field.

---

### Post by bodhi.zazen on 2009-04-16
What is com port 1 and what are you trying to do with it ?

---

### Post by Subway on 2009-04-16
com port 1 is the plug on the back of your computer, i use it for palm. i need to have com1 working in xp on vb i hope someone can help me.

---

### Post by bodhi.zazen on 2009-04-16
I hope this discussion helps :

[http://forums.virtualbox.org/viewtopic.php?t=186](http://forums.virtualbox.org/viewtopic.php?t=186)

Some people also claim this works with a USB interface, is that an option for you ?

---

### Post by Subway on 2009-04-16
Thank you for trying to help me but i think i will need to dual boot windows :( i was hoping i would not half to but i just cant get com 1 to work. thank you for all your help :)

---

### Post by Vaedrah on 2009-04-16
USB support requires that you enter yourself under usbusers via system etc. If you haven't done this already I'll dig out my notes and past the syntax for this.

Some USB devices may be extremely slow to connect though - memory sticks are fine but large drives can take a few minutes - I don't know why.

Shared folders set up in XP using its "explorer" and "mao network drive". Interestingly getting XP to run on Ubuntu is easier than the other way around!

[The only down side to virtualizing is that your RAM is divided from host to guest and it would be great to solve the 3.0 GB reported limit on Ubuntu (despite 4.096GB fitted). Otherwise, 64 bit machines seem like the next logical step for standard PC's and notebooks. Netbooks might remain 32 bits for a while perhaps?]

Interestingly also, I have Xilinx s/w running on XP as a guest on Ubuntu 8.04 and the JTAG comms for FPGA programming works fine.;)

---

### Post by Subway on 2009-04-17
It would be a great help to me if you could tell me how to do this :) i also am running 8.04 thanks alot.

---

### Post by Subway on 2009-04-17
Anyone :(

---

### Post by bodhi.zazen on 2009-04-17
Can you tell me, did you try the things in the link I posted ?

If so , what did you try exactly. Hard to help with insufficient information.

---

### Post by Subway on 2009-04-18
> **bodhi.zazen said:**
> Can you tell me, did you try the things in the link I posted ?

If so , what did you try exactly. Hard to help with insufficient information.

yes i tried it all, i just installed xp first then partition and installed ubuntu dual boot. so im happy now :) thank you for the help much appreciated. when i do figure it out i can get away from windows :D

subway...

---

