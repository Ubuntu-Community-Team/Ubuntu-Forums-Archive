---
title: "installed Beryl XGL but says AIGLX"
date: 2007-04-26
forum: Desktop Effects &amp; Customization
---

### Post by dlaw on 2007-04-26
Hi,

I'm new to Ubuntu.  I am currently using Ubuntu 6.10.  My graphics card is an ATI Radeon 9800 Pro.  I am having a problem running beryl.  This is not my first time running it.  The first time i had it running fine in edgy.  Then i upgraded to feisty and everything went weird so i decided to go back to edgy.  I used this tutorial to install beryl XGL: [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL#Graphic_Card_Drivers_and_3D_Video_Acceleration]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL#Graphic_Card_Drivers_and_3D_Video_Acceleration")

However, now when i try to run beryl it says in the terminal:

Detected xserver                                : AIGLX
Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

As i have read ATI and AIGLX don't work. I have tried to reinstall a few times already but the same problem keeps coming up.  I read in another post that someone was having the same problem with feisty but no one seemed to know how to fix his problem.

If any one could help it would be greatly appreciated.
Thanks A lot

---

### Post by ronocdh on 2007-04-26
> **dlaw said:**
> Hi,

I'm new to Ubuntu.  I am currently using Ubuntu 6.10.  My graphics card is an ATI Radeon 9800 Pro.  I am having a problem running beryl.  This is not my first time running it.  The first time i had it running fine in edgy.  Then i upgraded to feisty and everything went weird so i decided to go back to edgy.  I used this tutorial to install beryl XGL: [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL#Graphic_Card_Drivers_and_3D_Video_Acceleration]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL#Graphic_Card_Drivers_and_3D_Video_Acceleration")

However, now when i try to run beryl it says in the terminal:

Detected xserver                                : AIGLX
Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

As i have read ATI and AIGLX don't work. I have tried to reinstall a few times already but the same problem keeps coming up.  I read in another post that someone was having the same problem with feisty but no one seemed to know how to fix his problem.

If any one could help it would be greatly appreciated.
Thanks A lot
Are you sure your video driver is providing 3D acceleration? What's the output of **fglrxinfo**?

---

### Post by dlaw on 2007-04-26
hey! thanks for the reply, first time i've reached out to the "linux" community for help.

This if my "fglrxinfo" output;

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.6011 (8.28.8 )

Also my "glxinfo | grep direct" output says:
direct rendering: Yes

---

### Post by ronocdh on 2007-04-26
> **dlaw said:**
> hey! thanks for the reply, first time i've reached out to the "linux" community for help.

This if my "fglrxinfo" output;

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 2.0.6011 (8.28.8 )
That's good in that we know you're drivers are working. I was going to ask how the built-in Compiz effects were working, but I see you've downgraded to Edgy. 

[This]("http://ubuntuforums.org/showthread.php?t=399643&highlight=x200m") is the tutorial I used to get Beryl running; I've since broken it of course ;) but perhaps you can glean some insights from it. I believe the most important thing is that you've probably grabbed your Beryl package from the repositories, and unfortunately the Beryl in the repos doesn't support our cards. =(

That's explained in greater detail in the guide.

---

### Post by dlaw on 2007-04-26
interesting . . . the only thing is that the first time i installed and ran it, it went without a hitch.  Also i used the same tutorial and repositories.  I've only been using Ubuntu for less then a month.  I just upgraded last night and everything was crazy so i reinstalled Edgy hoping that i would be able to just install everything as easy as the first time.  

the weirdest thing is the whole AIGLX thing.

What's the word on beryl + ATI + Feisty? Is it buggy?  maybe I should just upgrade and try to work things out there.

---

### Post by wh0rd on 2007-04-26
Don't use the Ubuntu universe repositories. Uninstall beryl emerald and then **disable the universe repo** and add the beryl repo from beryl-project.org:

```
deb http://ubuntu.beryl-project.org/ feisty main
```

key:
```
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
```

Reinstall beryl emerald with the new repo. Then lock the packages because enabling **universe** repos will try to update them through Ubuntu repos. Then you can re-enable universe. Feisty Ubuntu repos doesn't support Beryl for XGL. Only beryl-project.org repositories do.

---

### Post by dlaw on 2007-04-26
OK, so i guess upgrading to Feisty and reinstaling beryl is the best option.

I was wondering though if there was a way to upgrade to Feisty but have everything at default, have no carry over from Edgy so its a completely clean and new OS.  I only have a few things installed in Edgy so hopefully I can just reinstall them into Feisty if necessary.

Does anyone know if Avant Window Navigator is working well in Feisty?

Thanks for the help everyone!

---

### Post by wh0rd on 2007-04-26
You can find Avant Window Navigator (AWN) for Feisty here:

[http://awn.wetpaint.com/page/Ubuntu+Feisty+Repository](http://awn.wetpaint.com/page/Ubuntu+Feisty+Repository)


I upgraded to Feisty from Edgy, I found that the fresh install was a better choice.

---

### Post by dlaw on 2007-04-27
Thanks everyone for the help.

I did a clean install of Feisty and it seems to be working well.

I just installed Avant window manager and its working perfectly.

I'm still apprehensive about installing and running beryl.  I will probably try to install it later on in the week.

---

### Post by ~SkyBlue~ on 2007-05-05
Thank you very much, now my radeon9800 works too :D

---

