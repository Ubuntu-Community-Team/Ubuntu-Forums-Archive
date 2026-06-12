---
title: "ATI Technologies Inc Rage 128 Pro Ultra TF"
date: 2007-07-26
forum: Desktop Effects &amp; Customization
---

### Post by roxattaq on 2007-07-26
I have an ATI Technologies Inc Rage 128 Pro Ultra TF video card in a Dell Dimension 4400 and I can't enable my desktop effects. Anywhere I go to find drivers I only get drivers for ATI Radeon but mine is a Rage!!!
  I'm new to Ubuntu and I'm getting a little discouraged with all the problems I'm having with my video card and my Linksys WUSB54G V4 wireless adapter. This doesn't work at all. It shows the available networks but signal strenght on all is at "0". 
  Can anybody help???

---

### Post by Waappu on 2007-07-27
Hi

Beryl, Compiz or Compiz Fusion not work with your video card. That means no desktop effects eather can't be enabled

---

### Post by roxattaq on 2007-07-27
Thank you for your help. Now I can focus on installing my wireless USB dapter and don't worry about my ATI card anymore.

---

### Post by dissrom on 2007-08-26
Hi,

Have you solve your problem with your "ATI RAGE 128 Pro Ultra TF" video card ???

I have the same card I can not find the correct driver for it...
In fact my Ubuntu sistem is working but with a lower value of screen resolution (only 1024x768).....that is because the default driver VESA is currently installed.
I`am thinking that if could install the correct driver I can use a greater values for the resolution

Can anybody help me ???

---

### Post by mrmiserable on 2007-08-26
dissrom 

change driver to ati or r128 and you resolution will be better

sudo gedit /etc/X11/xorg.conf

section device change driver

---

### Post by Rupertronco on 2007-08-26
> **mrmiserable said:**
> dissrom 

change driver to ati or r128 and you resolution will be better

sudo gedit /etc/X11/xorg.conf

section device change driver


What? That's not going to help anything. Don't do that at all. Referring to a driver that's not installed in your xorg.conf isn't going to get him anywhere. 

I'm unfamiliar with this card type, but I've had compiz running on some terribly old cards (as low as 32 mb of video ram) , it may be possible, do some research on the card and look through the compiz forums opencompositing.org and see what turns up.

---

### Post by mrmiserable on 2007-08-26
i have this card on old pc 
and it is the driver 
thank you
and no compiz will not work on this card or beryl

---

### Post by gapthemind on 2008-01-22
I have this card too, and I tried to go to the AMD web site to download drivers, but they don't even list the card in the old, unsupported products.

Is there another source for a driver for this card?

---

### Post by keonne on 2008-07-08
Bump.

Any way to get a higher screen resolution than 1024 x 768 on this card?

---

### Post by Hallvor on 2008-07-20
I have 1200x1600 on PCLOS. The only problem I have with it is high CPU and choppy videos on Youtube.

---

