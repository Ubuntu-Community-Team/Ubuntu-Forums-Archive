---
title: "Blender Graphical Glitches?"
date: 2009-04-27
forum: General Help
---

### Post by GolemdX on 2009-04-27
I recently reinstalled ubuntu on my netbook with Netbook Remix, and blender is having some... graphical glitches (it was working fine with normal ubuntu 9.04. I've switched to normal desktop mode too. I'll upload a screenshot with my post and see if anybody can help me.

---

### Post by GolemdX on 2009-04-27
Just tested it with an external monitor. Same glitches, Blender is still usable, but harder on the eyes and brain.

---

### Post by GolemdX on 2009-04-27
Same thing's happening with ANOTHER computer now. Both have Intel integrated graphics cards, this is happening with the netbook, literally fresh install, and the other with a very not fresh install, also downloaded some Intel thing that fixed desktop effects in Jaunty.

---

### Post by GolemdX on 2009-05-02
Still happening... not happening with 8.04 (but that computer sucks).

---

### Post by garythegoth on 2009-05-02
What graphics card do you have?

---

### Post by pg-13(prostitute) on 2009-05-03
hate to go off topic but i love blender and cg and stuph

an d im seeing recently that blender is going windows and im maddd

maybe were negl;ected

im having some dummmm issues ith 9.04 as well considering firefox freezing my system when closed with multiple tabs that i never had with 8.10 along with inskape,,, which doesnt matter cause i mainly work with raster over vector gfx

---

### Post by GolemdX on 2009-05-03
I said above that both computers have Intel Integrated Graphics cards, but they aren't the models said to not work with Jaunty.

---

### Post by -nat- on 2009-05-06
I am also having the same problem with Blender, Ubuntu 9.04 and an integrated Intel graphics chip. there is a thread [here]("http://blenderartists.org/forum/showthread.php?t=153233") on BlenderArtists discussing this issue and a few fixes have been posted in the thread (although none of them have worked for me).

If you do find a solution that works please let me know! :)

---

### Post by demosthene1 on 2009-05-06
I have a Toshiba Laptop L305 and installed Ubuntu 9.04. I love Ubuntu and feel very comfortable with it. But...same problem, Blender isn't usable and Blender is one of my must have programs. I've tried various fixes, none worked for me.

I hate dumping Ubuntu from my laptop but I must. I'm using PCLOS 2009 and Blender works fine.

---

### Post by Proteusiq on 2009-05-06
Go way around it :D, I am using Blender but exe one, Install Wine, then download Blender for Windows ...  run it in Wine! It work Fine there! :D

I had same problem after upgrading to Ubuntu 9.04 :D but now I am happyly using Blender Again! Everything work so fine!

Enjoy

---

### Post by dli8ilb on 2009-05-06
sorry, but it's not working under wine for me.  
it actually looks worse than running it natively:

[[IMG]http://img123.imageshack.us/img123/3370/screenshotblender.th.png[/IMG]](http://img123.imageshack.us/my.php?image=screenshotblender.png)

---

### Post by -nat- on 2009-05-07
When I run it under Wine it looks exactly the same as it does natively, so it's still unusable. 
Proteusiq, could you tell us what your Wine settings are? (find them under Wine->Configure Wine). it might have something to do with them.

Thanks :)

P.S. Just remembered that the 'Static' version of Blender runs without most of the graphical glitches, although it is slower. You can download it [here]("http://download.blender.org/release/Blender2.48a/")

---

### Post by demosthene1 on 2009-05-09
> **-nat- said:**
> 
P.S. Just remembered that the 'Static' version of Blender runs without most of the graphical glitches, although it is slower. You can download it [here]("http://download.blender.org/release/Blender2.48a/")

After days of searching for an answer, your suggestion of using the static version of Blender worked! I just needed to load python and turn off visual effects. Thank you. You really helped.

---

### Post by Proteusiq on 2009-05-10
Windows Version:  Windows Vista
I have attached the changes I made on Wine Conf

[IMG]http://www.adrive.com/home/downloadfile/176470263[/IMG]

[IMG]http://www.adrive.com/home/downloadfile/176470262[/IMG]

[IMG]http://www.adrive.com/home/downloadfile/176470261[/IMG]


Hope it helps :D

---

### Post by Proteusiq on 2009-05-10
> sorry, but it's not working under wine for me.
it actually looks worse than running it natively:

I think you need to configure wine before using it! Some of my friends blender works better than in native! When it comes to Animation and Rendering in Wine :D

Send me your Wine configuration and I can see how to go about them!

---

### Post by -nat- on 2009-05-16
EDIT
Sorry, it turns out uninstalling compiz probably isn't what made blender work. :oops: After uninstalling Compiz I did an update and I think some mesa upgrades were installed, so they are probably what fixed it.

---

