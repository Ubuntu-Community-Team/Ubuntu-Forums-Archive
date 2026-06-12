---
title: "Unity looks just like Gnome Classic"
date: 2011-05-01
forum: Desktop Environments
---

### Post by Dragonbite on 2011-05-01
I just installed 11.04 and I knew I would have to install the NVidia video drivers. So it was no surprise when it popped up a warning and dropped me into Gnome Classic view.

So I turned on the NVidia drivers and rebooted.

In my desktop selection menu on the login screen I have "Ubuntu" and "Ubuntu Classic".

Unfortunately they look exactly alike, with the Gnome panel along the top, and the panel with the taskbar, desktops and recylce bin on the bottom.

I've gone back-and-forth a few times and nothing has changed.  Some changes in one environment is not set in the other, like they really are 2 different environments.

According to the Software Center, Unity (not Unity 2D) *is* installed..

So how can I boot into the Unity desktop?

---

### Post by Dragonbite on 2011-05-02
So, does anybody have any ideas how I can get Unity to work on my desktop? Is it an NVidia issue?

---

### Post by 3Miro on 2011-05-02
1. Make sure you are running compiz (i.e. desktop effects are on). It is possible that the Nvidia driver did not install properly and you are still defaulting to the Classic-No-Effects mode.

2. Unity is just a couple of plugins for compiz, install CCSM (compizconfig-settings-manager). Then see if those are enabled when you select "Ubuntu".

---

### Post by Frogs Hair on 2011-05-02
I also had to add the Nvidia drivers prior to to booting into Unity . The ccsm was not required to boot into Unity . I installed the ccsm after . Select Ubuntu from the login window and see if either of these work. Sorry my code tags are not shoeing in the reply window.

unity --replace
unity --reset

---

### Post by Dragonbite on 2011-05-02
> **3Miro said:**
> 1. Make sure you are running compiz (i.e. desktop effects are on). It is possible that the Nvidia driver did not install properly and you are still defaulting to the Classic-No-Effects mode.

2. Unity is just a couple of plugins for compiz, install CCSM (compizconfig-settings-manager). Then see if those are enabled when you select "Ubuntu".

I installed CCSM to make sure it was on (darn not being able to just find it under Appearances like usual).  Plus I saw an item for Unity Plugin (or something like that) and made sure that was checked.

> **Frogs Hair said:**
> I also had to add the Nvidia drivers prior to to booting into Unity . The ccsm was not required to boot into Unity . I installed the ccsm after . Select Ubuntu from the login window and see if either of these work. Sorry my code tags are not shoeing in the reply window.

unity --replace
unity --reset

So you suggest ```
unity --replace
unity --reset
``` to see if it will refresh it?  I'll give it a try tonight when I get home.

---

### Post by morrisjones on 2011-05-02
On my system, I can only log in using "Ubuntu Classic (No Effects)".  If I use Ubuntu Classic, I get no task bar. If I use Ubuntu, I get a totally black screen.

On the "No Effects" desktop, System | Preferences | Appearance doesn't even have a tab for "enable effects."

Effects are totally dead in Natty.

Mojo

---

### Post by Dragonbite on 2011-05-02
This is what I got wehn I tried running those commands.

```
$ unity --replace
unity-panel-service: no process found
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Initializing composite options...done
Initializing opengl options...done
Initializing mousepoll options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing wobbly options...done
compiz (unityshell) - Error: OpenGL 1.4+ not supported

compiz (core) - Error: InitPlugin 'unityshell' failed
compiz (core) - Error: Couldn't activate plugin 'unityshell'
Setting Update "main_menu_key"
Setting Update "run_key"
Setting Update "run_command_terminal_key"

```

---

### Post by 3Miro on 2011-05-02
The "Effects" section in Appearance was removed in favor of the login options: "Unity, Classic, Classic-No-Effects".

Dragonbite and morrisjones, both of you guys are having trouble with the Nvidia driver. Dragonbite's error in particular (OpenGL 1.4 is no supported) means the driver in not installed properly.

Try Reinstalling the Nvidia driver. Go to System -> Admin -> Additional Drivers. Then do the following:

1. Disable any Nvidia drivers that may be active.
2. Reboot.
3. Enable the Recommended Nvidia driver.
4. Reboot.

This should fix the issue.

---

### Post by ibbill on 2011-05-02
I ended up removing my Gforce 5500 Nvidia card was the only way Ubuntu 11.04 would install.Said that my computer could not handle the install and would go into a loop reboot. 

Now I have the option of unity or classic.Which I am on classic as I really don't need all the bells and whistles compiz provides.Plus I really not happy about typing in names to find things I want example log on window or monitor.Feels like what you have to do with windows 7

and so it goes

---

### Post by rogue1987 on 2011-05-02
My situation is pretty much like dragon's and I'm getting the same error(s) as he is. i got it to run, but it didn't come back on reboot.

I'm running an HP Pavilion with nVidia graphics. I've tried each of the 3 versions of the drivers, but none seem to let Unity work.

---

### Post by Dragonbite on 2011-05-02
I only got one option for the driver, and removing-reboot-reinstalling-reboot didn't work.

---

### Post by rogue1987 on 2011-05-03
> **Dragonbite said:**
> I only got one option for the driver, and removing-reboot-reinstalling-reboot didn't work.
I had 3 options, but going through that for each didn't work. I had one called 3-D experimental that I could Unity running, but it wouldn't be there on reboot.

Anyway, started messing around with gnome 3 and now can't even log in. sigh...

---

### Post by Dragonbite on 2011-05-03
> **rogue1987 said:**
> I had 3 options, but going through that for each didn't work. I had one called 3-D experimental that I could Unity running, but it wouldn't be there on reboot.

Anyway, started messing around with gnome 3 and now can't even log in. sigh...

I'm waiting for Fedora 15 (out this month) to try out Gnome 3. 

The driver I had listed was listed as "experimental". 

Does it automatically use "nouveau" until you install proprietary drives, or do I need to install those myself.  I've had good luck with those drivers in Fedora (who is ahead of the curve on many of these type of items) and it's worth a shot if they aren't automatically used in Ubuntu as-is.

How would I find out?

---

### Post by rogue1987 on 2011-05-03
> **Dragonbite said:**
> How would I find out?
i don't really know... sorry

---

### Post by 3abdo3asal on 2011-05-03
Um maybe try reinstalling ubuntu itself maybe ,
OR just uninstall unity and reinstall it ,
OR install The 2d version ..
:( :( :( :( Which Ya the Best ;)

---

### Post by Dragonbite on 2011-05-03
My whole purpose of installing this was to try out Unity. I know my laptop will not be able to handle it and I already have Unity 2D running in 10.10 on it so I was really hoping to try out 3D.

So I was doing this on a spare desktop, thinking after the NVidia drivers were updated I would get all the 3D goodness I have with my Family Desktop running an Nvidia card and 10.04 LTS.

Hmm.. must try other angles.

---

### Post by Krytarik on 2011-05-03
> **Dragonbite said:**
> 
The driver I had listed was listed as "experimental". 

Does it automatically use "nouveau" until you install proprietary drives, or do I need to install those myself.  I've had good luck with those drivers in Fedora (who is ahead of the curve on many of these type of items) and it's worth a shot if they aren't automatically used in Ubuntu as-is.

The "experimental" driver *is* "nouveau", you should try it, I heard some users having success with it.

FYI, the "nouveau" driver is available, as well as the OSED for ATI/AMD cards/chips, through Xorg-Edgers' PPA since some time:
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

The OSED is now installed/used by default, and the "nouveau" has been added to the official repos.

Greetings.

---

### Post by NCLI on 2011-05-04
> **Dragonbite said:**
> This is what I got wehn I tried running those commands.

```
$ unity --replace
unity-panel-service: no process found
Backend     : gconf
Integration : true
Profile     : unity
Adding plugins
Initializing core options...done
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 1
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Window created on XQueryTree, map state isViewable? 0
Initializing composite options...done
Initializing opengl options...done
Initializing mousepoll options...done
Initializing gnomecompat options...done
Initializing wall options...done
Initializing wobbly options...done
compiz (unityshell) - Error: OpenGL 1.4+ not supported

compiz (core) - Error: InitPlugin 'unityshell' failed
compiz (core) - Error: Couldn't activate plugin 'unityshell'
Setting Update "main_menu_key"
Setting Update "run_key"
Setting Update "run_command_terminal_key"

```

The problem is actually quite obvious: Your driver doesn't support OpenGL 1.4+:
> compiz (unityshell) - Error: OpenGL 1.4+ not supported
Whether this is because your GPU is too old, or because nVidia are incompetent, I do not know. Try the Open Source driver.

---

