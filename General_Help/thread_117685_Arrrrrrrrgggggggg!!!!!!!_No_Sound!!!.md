---
title: "Arrrrrrrrgggggggg!!!!!!! No Sound!!!"
date: 2006-01-15
forum: General Help
---

### Post by pianoboy3333 on 2006-01-15
I'm getting really anoyed, I don't know what to do. The integrated sound hasn't been fully working, and now ubuntu won't detect it. The volume control has this error message:

> The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.

System Specs/Hardware:

149.01 GB Hard Disk (which in reality is 160 GB unformatted)
DVD-ROM Drive
CD R/RW Drive

256 MB ATI RADEON X600
1035 MB of RAM
Intel 4 3.2 GB (3192 MHz)
                1024 KB Cache

I recently had this problem under windows and downloaded the SigmaTel Drivers from Dell (since I have a Dell computer).

I went to the SigmaTel website and tried downloading and installing the linux drivers ([http://www.sigmatel.com/support/#drivers](http://www.sigmatel.com/support/#drivers)) and I tried using make and doing a bunch of things but it didn't work. Here is what was inside the folder after I un-tared it:

/home/alex/Desktop/irda4210/tools
/home/alex/Desktop/irda4210/gpl.txt
/home/alex/Desktop/irda4210/irda-ioctl.h
/home/alex/Desktop/irda4210/irda-usb.c
/home/alex/Desktop/irda4210/irda-usb.h
/home/alex/Desktop/irda4210/Makefile
/home/alex/Desktop/irda4210/README

In tools:

/home/alex/Desktop/irda4210/tools/getargs.c
/home/alex/Desktop/irda4210/tools/Makefile
/home/alex/Desktop/irda4210/tools/sgtlpatch
/home/alex/Desktop/irda4210/tools/stir42xx.c
/home/alex/Desktop/irda4210/tools/stir42xxi.h

I really don't understand y it isn't working, but the weirdest thing is that when I boot ubuntu, when it reaches the login screen it makes the bongo sound, but no other sounds are made.

HELP!

---

### Post by pianoboy3333 on 2006-01-15
Help?

---

### Post by BathroomNinja on 2006-01-15
If it makes the bongo sound, then your soundcard is working.  Where are you getting the Gstreamer message?  What program?  What are you trying to watch/listen to?

---

### Post by pianoboy3333 on 2006-01-16
I get the GStreamer message when I click on the volume icon on the toolbar:

[IMG]http://www.geocities.com/kib57/toolbar.png[/IMG]

And I can't listen to anything. There is no sound when I open programs, or play games or listen to music. The opening sound doesn't even play.

---

### Post by pianoboy3333 on 2006-01-16
Also, when I go to System->Preferences->Sound it can't detect a default sound card, nor can I select one from the drop down list.
*EDIT*
Also, the drivers I found were not for sound controllers, it said that SigmaTel is not authorized or something to give out drivers, and dell doesn't have a linux driver........

---

