---
title: "Can't get XGL to work in Kubuntu 6.10 w nvidia driver .."
date: 2006-11-12
forum: Desktop Environments
---

### Post by Slim on 2006-11-12
Hiya,

I'm running Kubuntu 6.10 on a dual monitor system, and am trying to get the nvidia-powered monitor to run XGL.

I've tried various how-tos, but can't get past this:

sauce:jg:~> glxinfo 
name of display: :0.1
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Segmentation fault
sauce:jg:~> 

.. now I'm pretty sure that 3D acceleration is working, as glxgears runs very smoothly indeed, but I'm stuck as to how to get past the above. Any ideas?

xorg.conf and Xorg.0.log.gz  attached. Grateful if anyone can shed some light.

Slim

---

### Post by tamagotono on 2006-11-12
instead of running xgl use the aiglx that is built into Edgy.

Check out the Forums and Howto section on [www.beryl-project.org](www.beryl-project.org) which is a branch of compiz.  Beryl is MUCH easier to install and has progressed much further thanks to the help of quinnstorm.

The basic steps are to install the beta NVidia driver, add the needed repositories to your sources.list file, install beryl (the branch of Compiz), install Emerald (the decoration themer for Beryl,) make a quick entry into your xorg.conf file, restart X and run beryl-manager from the command line.

It doesn't even matter wether you are running Gnome or KDE!

Easy as pie:mrgreen:

---

### Post by Slim on 2006-11-13
> **tamagotono said:**
> Easy as pie:mrgreen:

I'm afraid not. 

I followed the instructions at

[http://forum.beryl-project.org/topic-5021-howto-beryl-aiglx-nvidia-driver](http://forum.beryl-project.org/topic-5021-howto-beryl-aiglx-nvidia-driver)

.. as suggested. The newly compiled nvidia driver is happily running my monitor, but starting beryl-manager gives:

```
sauce:jg:~> beryl-manager 
sauce:jg:~> Error: couldn't find RGB GLX visual
Segmentation fault
compiz.real: Another window manager is already running on screen: 0
compiz.real: Another window manager is already running on screen: 1
compiz.real: No manageable screens found on display :0.1
```

Any ideas welcome. I've attached xorg.conf, in case anyone can see an issue there. I've tried it with the "Composite" extension enabled and disabled. 

Thanks for any help,
Slim

---

### Post by Jongi on 2006-11-13
[Try this](http://ubuntuforums.org/showthread.php?t=263851&highlight=aiglx+beryl)

---

### Post by Slim on 2006-11-14
Thanks! I might try that later. In the meantime, starting beryl seems to have permanently stopped the window manager working in my nvidia screen - I no longer get a working WM on that screen on starting KDE; can start applications but they stick to the top left of the screen, with no borders. And I can't type anything! I'd like to at least restore that, before further tinkering.

Can anyone help? Is it something to do with the stored KDE session?

Thanks
Slim

---

### Post by Slim on 2006-11-15
What's the window manager process called in Edgy / KDE? How to start manually (from a different display)?

Thanks,
Slim

---

### Post by Craig Prevallet on 2006-11-15
kwin

---

### Post by Jongi on 2006-11-15
Try running **emerald --replace** when then border doesn't appear

---

### Post by Slim on 2006-11-15
Cheers. That didn't work, but kwin --replace did the trick, and it seems to run on startup again.

---

