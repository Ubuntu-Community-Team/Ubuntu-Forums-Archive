---
title: "ATI x1950 + XGL + Beryl + Ubuntu 7.04"
date: 2007-07-07
forum: Desktop Effects &amp; Customization
---

### Post by OneStepAhead on 2007-07-07
Hello everyone this is my first post here. I just made the plunge at the start of the week to the linux world. I had been running Vista prior to now, and while I was pretty happy with it actually, I wanted to see what all the fuss was about with this Ubuntu distro. So far I am really liking it, and I plan to stick with it...that is assuming I can get all my hardware to work. I now realize my recent purchase of a ATI x1950Pro (PCIe) might not of been the best idea, I got it with the idea that I would be using it for folding@home mainly. However I see folding@home GPU support under linux doesnt exist yet, if it ever will. **Ok now on to my question:**

**Is it possible to get the x1950 cards to work with beryl?** I have tried a few different guides now and haven't had any success. I tried starting and XGL session and then launching beryl but all I get is a black screen and a mouse pointer. Can someone tell me is this even possible with the current state of ATI's linux driver? Id hate to have to buy another video card already...if it is not possible can someone tell me if the newer nvidia 8500-8800 series cards will function properly with beryl? If you can help please keep in mind Ive only been running linux for a few days now, so I still need my hand held :) Although I did install it back in 1998, but that was red hat linux. Seems things have changed now, for the better I might add.. Thanks for any and all help!

-Clay

clay@clay-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.0.6334 (8.34.8)

What should my Advanced Beryl Options be set to?

---

### Post by zero244 on 2007-07-07
Could you show us a copy of your xorg.conf
When you run glxinfo in terminal does it say direct rendering yes.

---

### Post by digital_exhaust on 2007-07-07
I have the AGP version of ths same card and it's giving me fits... big time. 

Direct rendering? Yep.

Beryl or Compiz Fusion? Nope. 

I have followed the guides here, and have had no success at all... I have Compiz Fusion up and running on a much older machine, P4 2g, 512m ram and a Radeon 7000/VE... yeah, and it runs *beautifully*.. no tearing, fast, clean and not one crash since Fusion has been installed... Oh yeah, and that's all at 1600x1200.

So, on my other machine, a P4 3g, 2g ram and a X1950pro AGP, I can't seem to get my dual 19" Viewsonic's to run at anything over 2048x768?? In single monitor mode it's all right at 1440X900 like it should be...so I don't know, guess I'm just venting here... If I get it figured out I will post back.......


The one thing you might want to check is System>Administration>Restricted Drivers and see if the ATI driver listed there is in use or not... I know some have had problems with the drivers and the fglrx driver is the fix.. Good Luck!!

---

### Post by OneStepAhead on 2007-07-07
Actually I got it working now. I think I just had some bad settings in beryl. I reinstalled the beryl package and now its working. wooohoooo! Thanks to everyone that wrote guides for beryl + xgl :)

---

