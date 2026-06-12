---
title: "Bootup Woes"
date: 2006-07-07
forum: Desktop Environments
---

### Post by PRocker267 on 2006-07-07
Hello everyone, Yes i am new here, and i have been haveing a rather annoying issue with linux ever since i got a new video card last year. before i bought it i enjoyed using kbuntu and ubuntu, but had to get rid of it for personal reasons. How ever during the time that lapsed since i deleted it i had installed a new video card, and i was looking to reinstall it, and unfortunatlly no matter what version or distribution i used, i would always get the same problem, right when the CD begins to start the display manager, it locks up, totally, i figured maybe its the same case with windows, it probly switched to my onboard video card, so i unpluged my moniter and stuck it into the onboard, and my moniter displayed "No signal", i had tried many other linux distro's and all but one gave me the same problem, but i am growing board of that distro and wanted to start using ubuntu again, thinking maybe the 6.0 would work, i was once again let down, So, to the point, Can anyone tell me what is happeining and how i can get the LiveCD to boot?

If its any help, my PCI video card is an Nvidia Geforce 5200 (not sure what the onboard is, will check later)

Thanks in advanced!
-Anthony:mrgreen:

---

### Post by PRocker267 on 2006-07-07
Bump!

---

### Post by PriceChild on 2006-07-07
Maybe some jumper settings to check on the motherboard?

---

### Post by lamego on 2006-07-07
What about installing from the alternate CD ?

---

### Post by panurge77 on 2006-07-07
maybe you left your onboard ON and turning it OFF would help

---

### Post by PRocker267 on 2006-07-07
Turning off my onboard sonds like a good idea, but how would i go about doing so?

---

### Post by PriceChild on 2006-07-07
Check your BIOS settings first, and if no joy there, then check your motehrboard documentation for any physical jumper settings to configure on your board.

---

### Post by PRocker267 on 2006-07-07
i looked in my bios and there was only a setting for the primary boot device, i tried both settings there and none worked, Im chatting with Compaq support to find some info out about my MB and see if theres anything they can do.

---

### Post by PRocker267 on 2006-07-07
Well as always, compaq support is a joke and i got no help there, and he said that there was nothing physical i can do to the card to disable it... Only the BIOS which i have checked, and the Device manager which has already been done.

---

### Post by PRocker267 on 2006-07-08
Well i have googled around all day and nothing, now, when i tried again, i got an error saying X crashed and if i wanted to configure it, but before i can press yes, a command line just stops and overrides the prompt :S

---

### Post by PRocker267 on 2006-07-08
So i take it no one can help me? =\

---

### Post by djheadley on 2006-07-08
What are your computer specs?  What is the name on your computer?  We need more information in order to help.

---

### Post by PRocker267 on 2006-07-08
My PC is a Compaq Presario Internet PC 5000 Series, Model is 5BW250, Has an intel celeron 697 MHz, 13 gig HD, 80 gig external HD, 512 MB RAM, Onboard video card is an intel, not sure of the exact model, and the PCI Video card is an Nvidia Geforce MX 5200.  If you need any more info, the product page is located here: [http://h10025.www1.hp.com/ewfrf/wc/product?product=93699&lc=en&cc=us&dlc=en&submit.y=0&submit.x=0&cc=us&lang=en](http://h10025.www1.hp.com/ewfrf/wc/product?product=93699&lc=en&cc=us&dlc=en&submit.y=0&submit.x=0&cc=us&lang=en)

---

### Post by PRocker267 on 2006-07-08
Also, i was told that if i remove my other video card and boot ubuntu, install it, that i would be able to use another distro or the same live CD to edit and configure my physical installation to use the correct video card, if this is possible, how would i do this?

---

### Post by djheadley on 2006-07-08
Well, I'm using Breezy but this should work;

1  Disable the on-board video:
     [http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&dlc=en&product=93699&lang=en&docname=c00007413](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&dlc=en&product=93699&lang=en&docname=c00007413)

2  Physically install the new video card

3  Boot the machine into Ubuntu and when it kicks you into the console (black screen with white letters) then at the prompt, type;
```
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
```

This is what worked for me when I transfered all my drives from and old machine to my new machine.  Both had built-in video.

Good Luck! ;)

---

### Post by PRocker267 on 2006-07-08
Thanks for the information, but when i tried to start GDM afterwards it just said faild, tried it 3 times, once i gave up i discovered that my windows partition somehow screweed up and wouldent boot, i fixed that then tried ubuntu again and it just messed up windows again!  I don't think i will ever get this working, thanks a lot for all of your help tho!  I think the best way to fix this is to buy a new computer, if only i had the money =\ :-({|=

---

