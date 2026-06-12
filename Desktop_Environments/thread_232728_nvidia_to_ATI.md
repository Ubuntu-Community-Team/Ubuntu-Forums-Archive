---
title: "nvidia to ATI"
date: 2006-08-09
forum: Desktop Environments
---

### Post by terranz on 2006-08-09
I am currently running Dapper with an nvidia card with the nvidia drivers installed.
For years I had used Nvidia cards but on the upgrade I've just made the equivalent ATI was easily $100 cheaper

Anyway I'm about to put it in, my new ATI radeon, and wanted to know what advice you knowledgable ones had for me.

Do I have to remove tbhe nvidia drivers, should I use the ATI drivers or look for a deb file? etc

Thanks in advance

edit:
I switched because I couldn't pass up the price but I don't yet understand the ATI chipsets and models like I do the Nvidia ones.

---

### Post by orb9220 on 2006-08-09
yes you will have to change the drivers and the xorg.conf file,

Good luck and I prefer nvidia becuase it always had less issues in xp and games than ati.

And it appears in the linux world that still is the case. I am not saying nvidia is better just that in my experience the most video issues in xp games and what Ive read on these forums ati seems to have a higher degree of difficult issues to get around.

---

### Post by terranz on 2006-08-09
Thanks for the heads up
A few years ago I wrote a how-to for installing nvidia under mandrake but I know nothing about ATI

---

### Post by thistlebrae on 2006-08-09
Based on everything I have read in various parts of this forum on the ATI vs. Nvidia debate, I would say:

Put the ATI back in its box and run it back to the store for a refund as fast as you can.  There are nothing but problems and issues with ATI video cards on this forum.  How much is your time worth?  For the $100 you saved you probably have a thousand hours ahead of you to get it to work...if you ever do.  

In my book, that isn't worth a savings of $100.00 ... but one needs to make that choice for themselves.

If you stick with the ATI card we'll have our violins ready :-({|=   [-X

---

### Post by scotty2hott2k on 2006-08-09
pretty much what thistlebrae said above really, sorry but ati do really suck on linux.

---

### Post by tseliot on 2006-08-09
After you plug the card in boot in recovery mode and type:
```
dpkg-reconfigure xserver-xorg
```

and select the "ati" or the "vesa" driver

Then install the driver

---

### Post by Hg80 on 2006-08-09
As a gamer i would say depends, it use to be match AMD to Nvidia and Intel to ATI as rule of thumb, but AMD have brought out ATI now so the pairing may change.
Also Nvida have had alot more involement with Linux then ATI have hence why there cards work better and are easier to install

---

### Post by terranz on 2006-08-10
Thankyou tseliot, that was most constructive
---------------

As to time, linux is a hobby of mine and so the time I spend is is of value to me in its spending on problems.

The ATI website has linux drivers and pictorial step through of installing it drivers and linux install wizard.

My concern was/is the change over.

So far it's working wonders on my windows games.

---

### Post by Tom Brokaw on 2006-08-17
> **terranz said:**
> Thankyou tseliot, that was most constructive
---------------

As to time, linux is a hobby of mine and so the time I spend is is of value to me in its spending on problems.

The ATI website has linux drivers and pictorial step through of installing it drivers and linux install wizard.

My concern was/is the change over.

So far it's working wonders on my windows games.

How is it working in Linux?  I've got a nvidia 5900 I'm thinking of replacing with a 9800 Pro.  This is mainly because the ATI is a single-slot card, whereas the 5900 takes up an additional PCI slot.  

Which model did you get, btw?

---

### Post by cptnapalm on 2006-08-17
While I would love to get off of ATi, I have one small problem.  This is a laptop :(

ATi story: There is a Compaq with a Sempron 3100+, 512 MB RAM and an ATi Xpress 200.  Using the ATi drivers, if I switch to a console, the machine dies.  If I restart the X server, the machine dies.  If I try shuttin down, the machine dies.

It is because of ATi's drivers, either the fglrx module itself or possibly their libGL.so.  One way or the other, the machine is practically unusable under Ubuntu because of ATI's drivers.  And the open source driver refuses to use anything other than 640x480.

I'd recommend anything other than ATi, if you can help it.

---

### Post by E-werd on 2006-08-17
I never got my Radeon 9000pro working with hardware acceleration in Linux until the 2.6 kernel came out.  By that time Ubuntu was working at full force and the repositories had the working ATI proprietary drivers in them.  

To be honest, if you're using Ubuntu, its not much of a worry unless you want to install drivers from the manufacturer's site.  This is just from my experience.  I used the 9000pro for years until I just got this GF6600, apt-get install nvidia-glx and away I went.

I've only ever gotten the downloaded drivers to work with my ATI card, but I have had better performance and fewer issues with NVIDIA in Linux. Here is my deciding factor: NVIDIA has nvidia-settings (a very powerful settings tool for your NVIDIA card) whereas ATI really doesn't have much in the way of that--they have their own settings program, but I never got much functionality out of it.

Unless ATI joins the Linux world full-force, I don't see myself switching back.

---

### Post by Tom Brokaw on 2006-08-17
OK, after firing up the ol' grey matter and actually searching the forums and google, the consensus seems to be that nVidia's support is far superior.  So that answers my question.

---

### Post by terranz on 2006-08-17
> **Tom Brokaw said:**
> How is it working in Linux?  I've got a nvidia 5900 I'm thinking of replacing with a 9800 Pro.  This is mainly because the ATI is a single-slot card, whereas the 5900 takes up an additional PCI slot.  

Which model did you get, btw?

ge cube re-released the 9600 pro with 256MB DDR

I'm going to do a re-install of ubuntu after all, when I find out how to keep my downloaded updates

---

### Post by patrick295767 on 2006-08-17
nvidia have amazing driver support and compatibility is very good. 
  
They releeased recently : nvidia-xconfig 

They also provide great downloading website & howto on their official website: [http://download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/index.html](http://download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/index.html)
  Have a try in the download section : [http://www.nvidia.com/content/drivers/drivers.asp](http://www.nvidia.com/content/drivers/drivers.asp)
Easy to find, fast, and lot of chooses.

I think that for linux, nVidia is getting bigger advance than Ati !

I Like my nVidia Card ! One more Happy nvidia user!

---

### Post by Sbarton on 2006-08-17
Although I cannot add to the nvidia-ati  question I can say that my machine has quite a old ATI Radeon 7000 and Ubuntu seems to be quite happy with no problems with the ATI card.
Regards

---

