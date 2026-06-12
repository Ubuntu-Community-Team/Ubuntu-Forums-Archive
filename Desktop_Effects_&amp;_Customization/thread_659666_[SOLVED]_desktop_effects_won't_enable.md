---
title: "[SOLVED] desktop effects won't enable"
date: 2008-01-05
forum: Desktop Effects &amp; Customization
---

### Post by Phil420 on 2008-01-05
here's my problem.. i try to enable the visual effects but it says it couldn't be
 enabled. I enabled restricted drivers and my ati card works fine.. well, it says
 it is in use. after that it told me the composite extention wasn't available. then
 i used envy to add drivers for my ati card, and when I restarted it, it kinda 
'didn't open properly, as in I couldn't get to the enter account and password 
thing. but, i reconfigured my x server and everything looked alright, except that
 in visual effects, it told me they couldn't be enabled, like at the beginning. 
someone somewhere in some forum page said said to go in the terminal 
and enter 

compiz --replace

and it did

[IMG]http://i263.photobucket.com/albums/ii146/420phil/Screenshot-philPhil-Desktop.png[/IMG]

i tried over two days to have that nice cube desktop, so plz help! :P

thanks

---

### Post by SpookComix on 2008-01-06
I don't want to rain on your parade, but I have this and other ocassional problems because I'm using an ATI card.  Even with the drivers working properly, I believe there is some kind of limitation that prevents Ubuntu's eye candy from having the option to render.  I could be completely wrong, though.  Hopefully someone better qualified will chime in.

I do know that, if you're not sure your ATI card is really pushing out smooth 3D graphics, set your screensaver to something like "Euphoria," or install and run "Chromium" (apt-get install chromium), a game that's a quick test to see if things are running smoothly in 3D land.)

--SpookComix

---

### Post by Surreal Killa on 2008-01-06
I have an ATI Radeon X300 and had some issues with the effects not enabling even after installing the driver, and what I did was installed xserver-xgl which you can do by typing the following into the terminal:

sudo apt-get install xserver-xgl -y

---

