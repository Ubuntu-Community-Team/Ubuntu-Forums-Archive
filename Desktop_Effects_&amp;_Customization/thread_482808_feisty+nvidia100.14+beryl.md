---
title: "feisty+nvidia100.14+beryl"
date: 2007-06-24
forum: Desktop Effects &amp; Customization
---

### Post by xero 1ne on 2007-06-24
Hello everyone, lovely day:)

Ok, I have a little problem

I am using feisty with kernel 2.6.20-16-generic
I have the propietary drivers from Nvidia (version 100.14.11 or w/e hte newest is)
And I am trying to get Beryl to work.

graphics acceleration is working fine

ok so the first thing that happens when i start up beryl is it tries to load it...then it sits there for a while having all my windows up missing a title bar..then it goes back to metacity.

I do have the "addrbgxglvisuals" "true" option thing in my xorg.conf

Does anyone have any ideas?

Thanks in advance, Ubuntu community FTW!

---

### Post by luisromangz on 2007-06-24
Well, the options name is "addargbglxvisuals", not "addrbgxglvisuals", so that may be the problem.

I think you use an Nvidia card, so you can easily add the option with the command

```

sudo nvidia-xconfig --add-argb-glx-visuals -d 24

```

That should do the trick.

Bye!

---

### Post by xero 1ne on 2007-06-24
Yah I have 

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    Option "AddARGBGLXVisuals" "True"
EndSection

I didn't feel like looking it up at the moment so i just put in what i remembered


despite this beryl doesn't run at all. 

when i run beryl from terminal i get this at the end:

Reloading options
beryl: Failed to load slide: 
beryl: Failed to load slide: 
Initiating splash
Segmentation fault (core dumped)

does htis mean anything to anyone?

I've also tried uninstalling and reinstalling beryl all over again multiple times

---

### Post by xero 1ne on 2007-06-24
BINGO
I found the problem!

I did even more googling of outputs of beryl in terminal and one person deleted the .beryl and .emerald folders from thier home directory and restarted x and it worked fine.

The same happened with me! : D

only downside is i lost my settings, but oh well....IT WORKS

:p

---

