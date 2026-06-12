---
title: "Usplash and GFXBoot - Happy Together?"
date: 2007-11-07
forum: Desktop Effects &amp; Customization
---

### Post by coldstatue on 2007-11-07
I love my GFXBoot, and after doing some considerable research and fiddling to repair it after moving /boot to it's own partition, I really don't want to mess it up. Still, I am interested in usplash. I have seen some really cool boot splashes with progress bars and customized verbose frames, and I'd really like to run it. But, from what I understand, it uninstalls GFXBoot. Is there any way to change the boot splash without messing up gfxboot? I know I can customize the color and size of text and whatnot, but what about graphix? Thanks.

---

### Post by OzzyFrank on 2008-01-17
Usplash is quite separate from the bootsplash that precedes it. You would have noted removing GRUB and putting GfxBoot in its place that this didn't affect the usplash... so feel free to change it!

---

### Post by coldstatue on 2008-01-18
ok, so can i do that without installing Startup Manager? That uses Splashy, right? I think it manages the GRUB graphics as well, which worries me. What method would you suggest? Thanks.

---

### Post by smartboyathome on 2008-01-18
> **coldstatue said:**
> ok, so can i do that without installing Startup Manager? That uses Splashy, right? I think it manages the GRUB graphics as well, which worries me. What method would you suggest? Thanks.

You can use Startup Manager with  either Usplash and Splashy. Since you are using GFXBoot, I would recommend using Splashy, but you don't have to.

---

### Post by coldstatue on 2008-01-18
So what option do i select in Startup manager for GRUB to be sure it won't overwrite my GFXBoot settings or something? i would install Splashy before Startup manager, correct?

Thanks for your help/

---

### Post by coldstatue on 2008-01-18
Also, you said that you recommend splashy *because* I use GFXboot. Why?

---

### Post by OzzyFrank on 2008-01-19
First off, the fact that Startup-Manager has the GRUB themes listed shouldn't mean anything, as you had to uninstall GRUB anyway in order to make way for GfxBoot. As for what handles what comes after, you can go for Splashy, just like you decided on GfxBoot instead of GRUB. I don't know much about Splashy, other than it can support animations. Question is whether there are enough good themes to make it worth the switch (since there are a few good Usplash themes out there).

So don't worry about anything in Startup-Manager... but of course you can't use that to change GfxBoot splashes, you have to do that manually by editing menu.lst. If anyone knows of a program that lets you do it easily, let us know. And interesting to hear you can use Startup-Manager to change Splashy themes as well as Usplash.

---

### Post by OzzyFrank on 2008-01-19
PS: Just making sure you know that in Startup-Manager you can add and change the Usplash? I'd say most of the cool splashes you've seen around are Usplash, not Splashy. So just download some .so files and import them in S-M and change them there. Once again, just making sure you understand altering the boot menu is not connected to altering the bootsplash/usplash. The only problem you'll ever have with usplashes is that some are made for only 1 or 2 specific screen resolutions, so if you just end up with the black screen in verbose mode you'll know what that means (just pick another). There are heaps of good Usplash screens, so check them out at gnomelook.org.

---

### Post by coldstatue on 2008-01-19
I installed SUM last night - using usplash. I am pretty happy with it. Splashy looks like it might have some slick themes, but I can't find too many of them. The only thing I don't like about SUM is that I have to go comment out my unwanted items from the automagic kernels list each time i change a theme - that will be resolved when i finally go delete them, so problems, really.  Just hoping to run across a really nice animated splashy, then I will switch. Thanks for all your help.

---

