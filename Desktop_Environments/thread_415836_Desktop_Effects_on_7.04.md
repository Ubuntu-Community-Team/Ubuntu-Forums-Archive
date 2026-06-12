---
title: "Desktop Effects on 7.04"
date: 2007-04-20
forum: Desktop Environments
---

### Post by CarlosinFL on 2007-04-20
OK - so I see now 7.04 has an option for Desktop Effects under System > Preferences and I was wondering what exactly does this do? I have nVidia drivers enabled and I enabled both options for "Desktop Effects" which makes my "Terminal" window bouncy and blurry in a cool way but everything thing else still appears the same. I was wondering exactly what else is available and if there is a way to manage this?

Thanks for any info.

---

### Post by jaimz on 2007-04-20
you might like to install beryl for more options

---

### Post by 90Brougham350 on 2007-04-20
I wish mine worked, I enable the drivers and it tells me to restart the computer and then Desktop Effects again, and it never changes, always just enables the drivers and tells me to restart.

---

### Post by CarlosinFL on 2007-04-21
> **jaimz said:**
> you might like to install beryl for more options

Can you explain why I would prefer Beryl of Compiz?

---

### Post by jaimz on 2007-04-21
I haven't used compiz since the dapper days (which is pretty much the same as beryl from what I remember)
but with beryl, you can completely edit the eye candy to how you want it
gives more options to theme your desktop

it's really nice if you want to impress people with your desktop lol

---

### Post by tmasboa on 2007-04-21
Basically, you'll like Compiz... you'll love Beryl. Beryl has lots more effects and plugins and you can use Emerald, a window manger and lots more..

if only I could get Beryl working on my other install, I get a "composite extension" error and on my propority or wahtever drivers window it says my ati driver isn't in use.

---

### Post by jaimz on 2007-04-21
> **tmasboa said:**
> Basically, you'll like Compiz... you'll love Beryl. Beryl has lots more effects and plugins and you can use Emerald, a window manger and lots more..

if only I could get Beryl working on my other install, I get a "composite extension" error and on my propority or wahtever drivers window it says my ati driver isn't in use.

on Feisty, I'm using the ATI open source drivers with aiglx & beryl :) 

you're probably on fglrx, which doesn't work with aiglx and would require xgl for it

---

### Post by CarlosinFL on 2007-04-21
So if you want to try Beryl, do I need to remove Compiz or simply can I just disable it? How does one get or install Beryl? Is it available via APT-GET (CLI)?

```
$ sudo apt-cache search beryl
beryl - Compositing window manager, decorator and theme support - Beryl
beryl-core - Compositing window manager - Beryl Project
beryl-core-dbg - Debug symbols for Beryl
beryl-defaults - Simplified Plugin and configuration tool - Beryl Project
beryl-dev - Development files - Beryl Project
beryl-kubuntu - Simplified Plugin and configuration tool - Beryl Project
beryl-manager - Tray application launcher tool - Beryl Project
beryl-plugins - Collection of plugins for Beryl
beryl-plugins-data - Plugins data - Beryl Project
beryl-plugins-dbg - Collection of plugins for Beryl, debug version.
beryl-plugins-unsupported - Collection of extra plugins for Beryl
beryl-plugins-unsupported-data - Unsupported Plugins Data
beryl-plugins-unsupported-dbg - Collection of plugins for Beryl, debug version.
beryl-settings - Plugin and configuration tool - Beryl Project
beryl-settings-bindings - Plugin and configuration tool - Beryl Project
beryl-settings-simple - Simplified Plugin and configuration tool - Beryl Project
beryl-ubuntu - Simplified Plugin and configuration tool - Beryl Project

```

---

### Post by jaimz on 2007-04-21
just have desktop effects off

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu#Ubuntu_7.04_.28Feisty_Fawn.29]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu#Ubuntu_7.04_.28Feisty_Fawn.29")

there's a few how to's

---

### Post by CarlosinFL on 2007-04-21
Thanks

---

### Post by CarlosinFL on 2007-04-21
SO I have Beryl installed and I am curious how do push back the Desktop as a cube and rotate it? I can press ctl + alt + --> which moves them fast but the cube never gets pushed back to allow me to rotate it. Am I missing something?

---

### Post by tmasboa on 2007-04-21
> **jaimz said:**
> on Feisty, I'm using the ATI open source drivers with aiglx & beryl :) 

you're probably on fglrx, which doesn't work with aiglx and would require xgl for it

Okay so when I get my brand new Feisty install on a C2D w/x1600 should I tell it to do the proprietary ATi driver? And after that hmm I think I used xgl before but I don't remember. You see, now I have an aging SuSE 10.2 on there, but suse is too slow and big for me, and beryl is messed up beyond repair. 

Basically I'm trying to figure out what steps I should take becuase I learned once you monkey up a fresh installation you cannot always make it work well.:guitar: :guitar: :guitar: :guitar: :guitar: :guitar:

---

### Post by jaimz on 2007-04-21
> **Carlwill said:**
> SO I have Beryl installed and I am curious how do push back the Desktop as a cube and rotate it? I can press ctl + alt + --> which moves them fast but the cube never gets pushed back to allow me to rotate it. Am I missing something?

middle click and move the mouse

---

### Post by jaimz on 2007-04-21
> **tmasboa said:**
> Okay so when I get my brand new Feisty install on a C2D w/x1600 should I tell it to do the proprietary ATi driver? And after that hmm I think I used xgl before but I don't remember. You see, now I have an aging SuSE 10.2 on there, but suse is too slow and big for me, and beryl is messed up beyond repair. 

Basically I'm trying to figure out what steps I should take becuase I learned once you monkey up a fresh installation you cannot always make it work well.:guitar: :guitar: :guitar: :guitar: :guitar: :guitar:

yeah you'll have to use the  fglrx  drivers with XGL to get beryl to work, it's how I used to do it during dapper & edgy
I don't know if the open source drivers support the x1k series yet
but they work up to the x850

I'm on an x800 & was happy to see that the open source drivers finally worked out of the box for me on feisty

---

### Post by CarlosinFL on 2007-04-21
> **jaimz said:**
> middle click and move the mouse

Wow - it looks pretty amazing. Do you know where I can get rid of the Beryl icons on the top and bottom when I middle click and I see the cube? I have 4 virtual desktops as normal but the top and bottom are blank or default to a Beryl diamond icon.

---

### Post by jaimz on 2007-04-21
> **Carlwill said:**
> Wow - it looks pretty amazing. Do you know where I can get rid of the Beryl icons on the top and bottom when I middle click and I see the cube? I have 4 virtual desktops as normal but the top and bottom are blank or default to a Beryl diamond icon.

right click beryl & select one of the managers there, I believe it's the first one on top
and just go to desktop cube, and you'll find it on one of the tabs there

---

