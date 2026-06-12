---
title: "xserver-xgl meses up my desktop, but I need it."
date: 2008-03-06
forum: Desktop Effects &amp; Customization
---

### Post by BetterSense on 2008-03-06
I installed compiz fusion, and it didn't work, it complained about needing Xgl in the console. I have an Nvidia onboard 7050 and ran envy, and checked restricted drivers.

 So I sudo apt-get install xserver-xgl, and restarted the Xserver, but when I logged back in, everything on my desktop was in tiny little font, like the resolution was huge, but then the background picture wasn't zoomed out, and my desktop settings said I was still at 1024. 

So I apt-get autoremove xserver-xgl, and restarted the Xserver and it was back to normal.

So, I understand Compiz needs xgl to run. Why is it breaking my desktop?

---

### Post by russo.mic on 2008-03-06
well, you need the package xserver-xgl to run compiz, not xserver-xorg.

sudo apt-get install xserver-xgl

Good Luck!

Russo

---

### Post by BetterSense on 2008-03-06
my mistake, I meant to say xserver-xgl. Post edited appropriately. Problem still unsolved.

---

### Post by ChameleonDave on 2008-06-04
> **BetterSense said:**
> 

So, I understand Compiz needs xgl to run. Why is it breaking my desktop?

Compiz checks for the presence of xgl, but it does not actually require it to run in Hardy Heron.

You should probably remove the "xserver-xgl" package and seek another solution to your 3D effects problem.

---

