---
title: "Webcam still has the same problem in breezy"
date: 2005-10-13
forum: Desktop Environments
---

### Post by Pekkalainen on 2005-10-13
My Logitech Quickcam pro 3000 works both in Hoary and Breezy... BUT! The image is too dark, even a 60 watt lamp appears as a dark gray blob in it. How do I make the image brighter? The controls in Gnomemeeting does nothing. I am using the pwc driver and I got v4l installed.
Can I alter the driver somehow to make it start with different values or something maybe? Or do I need a new driver?

---

### Post by KingBahamut on 2005-10-13
[http://qce-ga.sourceforge.net/](http://qce-ga.sourceforge.net/)

They produce the GNU/Linux OS driver for the Quickcam Express,  providing support for developers of other quickcam drivers and compatible USB webcams. Based originally on work by Georg Acher, Jean-Frederic Clere produced the first V4L driver so that popular V4L applications such as Xawtv may display pictures from the webcam. Since then a group of developers around the world have helped evolve the driver into its current state, adding support for new cameras and chipsets as they have become available.

---

### Post by Pekkalainen on 2005-10-13
[QUOTE=KingBahamut][http://qce-ga.sourceforge.net/](http://qce-ga.sourceforge.net/)

They produce the GNU/Linux OS driver for the Quickcam Express,  providing support for developers of other quickcam drivers and compatible USB webcams. Based originally on work by Georg Acher, Jean-Frederic Clere produced the first V4L driver so that popular V4L applications such as Xawtv may display pictures from the webcam. Since then a group of developers around the world have helped evolve the driver into its current state, adding support for new cameras and chipsets as they have become available.[/QUOTE]

Thanks! Now I got a newer version of the pwc driver called pwcx :D
Only problem is.. how do I install it and use it instead of the old pwc driver? I need a step by step guide, the readme included with the driver makes no sense to me :(

---

### Post by Pekkalainen on 2005-11-27
Sorry for bringing up my thread again but I have made some progress...

I have gotten the newer pwc module from [http://www.saillard.org/linux/pwc/](http://www.saillard.org/linux/pwc/) that according to other people with the same cam works perfectly.

Still the same dark image in the cam, the cam works but its almost total darkness... only thing that shows up in gnomemeeting or any other cam program is my 60 watt light in the ceiling no matter how much I pump up the brightness setting in gnomemeeting :(

Any idea of how to configure the cam? I suspect it has something to do with the cams own auto brightness adjusting thingie.''

Edit: I finally fixed it!!!! :D

I downloaded setpwc from [http://www.vanheusden.com/setpwc/](http://www.vanheusden.com/setpwc/) and reset the cam to factory settings and it woooooooorkssss!!! :D

---

### Post by matburton on 2007-03-11
Hey Pekkalainen,

I have the same problem with a Logitech Quick Cam for Notebooks under Edgy. Works but the image is just black.

How did you manage to install setpwc? I downloaded the source but upon using make I just got a string of compiler errors. Are there other source files I need? I can't find instructions or dependencies anywhere.

Thanks,
Mat

---

### Post by navaburo on 2007-11-30
I have the opposite problem: my quickcam autoadjusts the brightness, and I dont want it to because I am doing motion detection and comparing against a saved image.

Anyone know how to disable the autoadjust? (either via the command line or in a program ( i am writing code that accesses the camera))

Thanks!

---

### Post by navaburo on 2007-11-30
> **Pekkalainen said:**
> 
I have gotten the newer pwc module from [http://www.saillard.org/linux/pwc/](http://www.saillard.org/linux/pwc/) that according to other people with the same cam works perfectly.


Do you remember what the dependancies were? I am getting build errors.

---

### Post by Znort_Ubern00b on 2007-11-30
my camera has really dark image too...have to have camera right next to light(hurts eyes)...can you tell us how you solved it...

---

