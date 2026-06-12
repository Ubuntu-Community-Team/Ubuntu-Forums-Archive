---
title: "Blank screena after entire installation - what more can I do?"
date: 2006-03-12
forum: Desktop Environments
---

### Post by Mininna on 2006-03-12
Hi everyone,

Before I begin, here is all the info I could find on my computer:

P4 Intel Celeron
Samsung drive 80GB (only umbuntu installed right now)
Atapi Cd Rom Drive
NVidia GForce
AGP graphics adapter
Logitech usb keyboard
Benq wireless mouse (M306)

Via Pci 10/100Mb Fast ethernet Adapter v3.33
Linksys wired router 

not sure about the memory, but it should be plenty to run Ubuntu - I had Win Xp on the computer before, and everything runs pretty quick

plus, I'm using a projector as my main screen, with a maximum resolution of 1024x768
                                                       
A little background on what I've done so far:

-tried the Knoppix live cd, and I get a black screen before I get a chance to even see the GUI
-tried Fedora 4 and get the black screen very early in the process, before it has a chnce to install
- tried the latest Damn Small Linux and it actually works, but unfortunatelly, is too small...lol

So, my latest attempt is at Ubuntu. I burned the cd, checked the sums, and everything was ok. Popped the cd in, and the installation went pretty smoothly, though it took a long time. Then, after the whole installation was completed, I restarted. It went through the part where you see the Ubuntu logo, and the little line that's apparently loading the whole thing....and then everything went black. That's it. It won't budge.

Restarted a few times and the same thing happens.

I'm almost at my wit's end here. Please help, I really don't want to go back to Windows...it hurts just thinking about it.:cry:

---

### Post by OfficeLinebacker on 2006-03-12
I'm going to have to guess that it's a graphics driver issue.
 
I'd also be willing to bet that there's a solution.  :)

---

### Post by Mininna on 2006-03-12
Ok, that points me in a direction at least. :) Does that mean that it's the graphics card, or something to do with the projector I'm using? I'm guessing the graphics card...

Maybe then I can try to find out how to get the proper driver for my card.

Thanks for the quick answer.

---

### Post by taurus on 2006-03-12
If you can get into a terminal (console) with the <Ctrl><Alt>F* combination, try editing /etc/X11/xorg.conf and replace the driver for your video to "vesa" for now.  Once you have Gnome up and running again, then you can install nVidia driver for your video card.
```

sudo nano /etc/X11/xorg.conf

```

---

### Post by Ramses de Norre on 2006-03-12
EDIT: nevermind:) (possible to delete a post?)

---

### Post by Mininna on 2006-03-12
Could anyone point me in the right direction regarding the terminal/console bit? When do I get a change to access the terminal? While the Ubuntu logo comes up and the whole thing is loading, or before?

Thank you very much.

---

### Post by Ramses de Norre on 2006-03-12
To where do you exactely get? Do you see the log in screen?
If so: press alt+ctrl+F1 there.
If not: boot into recovery mode, which should get you into terminal directly.

---

### Post by OfficeLinebacker on 2006-03-12
[quote=Mininna]Could anyone point me in the right direction regarding the terminal/console bit? When do I get a change to access the terminal? While the Ubuntu logo comes up and the whole thing is loading, or before?
 
Thank you very much.[/quote]
 
I'd say choose the recovery console from the GRUB menu.
 
For the GRUB menu hit escape after the BIOS posts and you see something like "GRUB loading."

---

### Post by Mininna on 2006-03-12
I'm in! :) 

I changed my video driver to "vesa" and it worked right away. Thank you so much for the tip.

Now I'm just working on finding a way to make my mouse less choppy. It looks like it's jumping an inch at a time right now. Even my sound card is working. This is so awesome.

---

### Post by Ramses de Norre on 2006-03-12
I'd also search for the nvidia drivers and install and use them, they will look much beter then vesa ;)

---

### Post by taurus on 2006-03-12
Okay, here the link for your nVidia card...

[http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074)

---

### Post by Mininna on 2006-03-12
I installed the Nvidia drivers, plus a bunch of other things, and now not only is my mouse not choppy anymore, but everything looks great. 

I'm working on figuring out how to play Windows Media and Quicktime files, but I guess the whole thing is going to be a work in progress for me until I figure how everything works.:mrgreen: :mrgreen: 

Thank you again for all the help.

---

### Post by taurus on 2006-03-12
You can use automatix to install all the codecs first before you can play your video files...

---

