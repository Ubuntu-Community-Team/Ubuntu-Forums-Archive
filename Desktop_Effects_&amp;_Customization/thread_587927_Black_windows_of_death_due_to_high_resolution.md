---
title: "Black windows of death due to high resolution?"
date: 2007-10-23
forum: Desktop Effects &amp; Customization
---

### Post by jimmyxx on 2007-10-23
Hi all, I've been getting black windows of death whenever i have a few windows maximized. I run dual 1600x1200 via twinview. My computer is AM2 5600+ AMD with a nvidia 6600 gfx card.

My colleague has exactly the same setup except he has a lesser processor and his resolution dual 1280x1024. He is able to run the desktop effects perfectly and can have 20 instances of full screen firefox, nautilus etc and doesn't get any black screens. I'm a notch up on the resolution and can't have more than 2 windows open at full screen.

Do I get the black windows of doom because of my resolution? :confused: :confused: 

Thanks,
Jimmy

---

### Post by renzokuken on 2007-10-23
are you running beryl/compiz?

---

### Post by jimmyxx on 2007-10-23
well ubuntu 7.10

I thought that was compiz fusion or something?


I've attached a screenshot of what happens

---

### Post by MrHippocampus on 2007-10-23
The black window bug occurs on nvidia cards when your graphics card runs out of space in its video ram for new windows, so your resolution is partly to blame as a higher resolution screen uses up more of your video ram.

If you turn off desktop effects completely you shouldn't have any problems, your only other options are buy a new graphics card with more video ram or wait for nvidia to fix the bug in their driver (apparently there were improvements in the last driver, but clearly they haven't helped your situation).

---

### Post by jimmyxx on 2007-10-23
its just crazy that my colleague has the same setup with a slightly lower resolution and he has absolutely no problems :confused:

---

### Post by cavemanf16 on 2007-11-06
> **jimmyxx said:**
> its just crazy that my colleague has the same setup with a slightly lower resolution and he has absolutely no problems :confused:

Hey man, no, you're probably right when it comes to the 6xxx series of nVidia cards.  They are better than the DirectX 7 cards nVidia put out for sure, but mine (MSI 6600 GT?) gives me the black windows problems just like you describe at 1600x1200 on dual monitors in a twinview setup as well, although I only have an AMD 64 3000+ with 1G of RAM so I hit the black windows if I just have The Gimp and Mozilla running at the same time and try to maximize any window. (The Gimp is a big memory hog for image editing, for good reasons of course)

I just set my resolution back to 1280x1024, which sucks, but at least the black screens won't drive me crazy anymore.

---

### Post by belgrave on 2007-11-16
found a full solve to this here:

[http://www.deepnerd.com/node/82](http://www.deepnerd.com/node/82)

---

### Post by jimmyxx on 2007-11-19
yes its true!!!

by installing:  nvidia-glx-new, nvidia-new-kernel-source and nvidia-glx-new-dev the problem is fixed - its awesome! Well done nvidia! 


:KS *Whoo Hoo!* :KS

---

