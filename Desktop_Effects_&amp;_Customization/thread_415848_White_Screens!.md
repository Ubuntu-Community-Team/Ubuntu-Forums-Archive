---
title: "White Screens!"
date: 2007-04-20
forum: Desktop Effects &amp; Customization
---

### Post by stickperson on 2007-04-20
Hey guys, I get the white screen of death when trying to run Beryl and Desktop Effects.  I'm not sure what kind of card I have,  I'm running feisty fawn.  I did a lot of research but nothing helped.  Can anyone help me out?

---

### Post by Sef on 2007-04-20
Could you please give us your system specs including your graphics card.

---

### Post by stickperson on 2007-04-20
I have an IBM Thinkpad T60, 2.0GHz Intel Core 2 Duo processor, 128MB ATI Mobility Radeon X1400 graphic card.

---

### Post by LostArt on 2007-04-20
I get the same problem, If someone could help me out too that woild be great, I'm running feisty and have a: 

ATI Radeon mobility 9100 IGP

702 Mega bytes of ram

Intel celeron 1.4 ghz processor

Any ideas :-) 
trying to act hopeful...

---

### Post by stickperson on 2007-04-20
Well I just followed the steps here [http://ubuntuforums.org/showthread.php?t=399643&highlight=beryl+200m+feisty](http://ubuntuforums.org/showthread.php?t=399643&highlight=beryl+200m+feisty)
but now when I run beryl the settings just come up.  When i try to run the desktop effects it says that "the composite extension is not available."

---

### Post by LostArt on 2007-04-20
hmmm, do you know what graphics card you are running? And on another note I believe I did this tutorial without success.

Edit, 
oh you listed your graphics card, okay then I'm an idiot. this might work for you, although it did not for me, also, ATI cards have a lot of trouble with wsod's (White screens of death), I've been trying to get mine to work with beryl for two weeks

try this tutorial [http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon) 

It pretty much explains everything step by step.

IMPORTANT
If this causes you to get an x server error upon reboot login type your password, and type 

sudo dpkg-reconfigure xserver-xorg 

Then follow the reconfigurer step by step, It's saved me countless times. ;-)

---

### Post by jiminycricket on 2007-04-20
X1400 means you need to install fglrx and use XGL.  Unfortunately, they're not supported by the offical Xorg drivers because ATI is stubborn.

---

### Post by stickperson on 2007-04-21
> **jiminycricket said:**
> X1400 means you need to install fglrx and use XGL.  Unfortunately, they're not supported by the offical Xorg drivers because ATI is stubborn.

so does that mean I'm screwed?

---

### Post by Oklin on 2007-04-21
I am seeing a lot of people having trouble with ATI Radeon.. And i dont see anyone saying they have SiS AGP, thats the one i got on my Acer, but i get the same white screens as the radeon guys..

---

### Post by Pazin~ on 2007-04-21
I've got a white screen too. 
I clicked to test and confirm that the video card sucks :popcorn: 

At the moment you get a white screen, just hit Esc and the video will return to normal.



Sorry my english... I'm learning.

---

### Post by stickperson on 2007-04-22
Update: I got Ubuntu working!  About time.  Anyway, when I run it my whole system runs sooooo slow.  Anyone know why?

---

