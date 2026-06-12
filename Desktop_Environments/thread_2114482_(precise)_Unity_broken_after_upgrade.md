---
title: "(precise) Unity broken after upgrade"
date: 2013-02-09
forum: Desktop Environments
---

### Post by palm86 on 2013-02-09
Dear all

After a recent upgrade on precise unity stopped working. The launcher is shown with only the Ubuntu button, switcher and trash, but nothing is clickable. The desktop is unresponsive and the panel is without any indicators and unresponsive.

I suspect the problem might have crept in after an upgrade to dropbox, which asked for a nautilus restart, which failed and on reboot the issue appeared. Subsequent sudo apt-get update and dist-upgrades ran to completion with no issues.

The problem goes away if I log into another account and then back into my account, but only until the next reboot.

I was once able to get CCSM open through tty1 with:

export DISPLAY=:0.0
ccsm

The unity plugin and several others were disabled. This solved the problem but only until the next reboot. This also hasn't worked again (can't get into ccsm that way anymore).

I have tried the following:

Purged and reinstalled unity unity-services lightdm dropbox nautilus compiz.

This fixed it until the next reboot.

I've also removed all folders in my home containing 'unity' or 'compiz'. No avail.

I tried unity --reset and several gconftool-2 unset recursive commands.

There must be some setting in my home folder, because the problem doesn't occur in other accounts. However, I can log into Unity2D, which is functional.

I made no hardware changes and my computer has been working fine since I got it in March 2012.

Any help would be greatly appreciated.

Best regards
Daniel

---

### Post by palm86 on 2013-02-10
Dear all

When I log into my account, the Unity launcher only shows the Ubuntu button, windows switcher and trash. No other icons are shown. The panel isn't responsive and neither is the desktop. If I log into unity2d and log back into unity it works, but only until I reboot/suspend/sleep.

Output of **/usr/lib/nux/unity_support_test -p**:

OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Desktop 
OpenGL version string:  3.0 Mesa 8.0.4

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

I have tried **unity --reset**, but it hangs without error messages.

I have made a similar post in General Help, but only later realized there is a more specific forum for desktop issues.

Best regards
Daniel

---

### Post by Frogs Hair on 2013-02-10
The reset command has changed for 12.10 to the following. 

```
setsid unity
``` Reset Compiz ```
sudo apt-get install dconf-tools
``````
dconf reset -f /org/compiz/
```

---

### Post by wildmanne39 on 2013-02-10
Thread merged. Please do not post duplicates, it dilutes community effort.

---

### Post by palm86 on 2013-02-10
Frogs Hair, thanks but I'm running precise 12.04.

Thanks for merging Wild Man.

---

### Post by tclahr on 2013-02-12
Hi there,

I am experiencing the same problem. I am using Precise 12.04.1, and after some updates days ago, my Suspend stopped to work (I cannot resume anymore) and my Unity is broken.

How did you fix that?

---

### Post by Roman.V. on 2013-02-13
Hi everyone.

I have same problem here.
Desktop appears after login but it's unfunctional.
I use following temporary solution: Alt+Ctrl+F1 -> login -> sudo /etc/init.d/lightdm restart
After that it works until next reboot.

Also computer stoped react to anything if screen is turn off when it inactive. Even if I connect to it with ssh and say reboot it drops ssh connection and do nothing. reboot -f works though. So I have to disable turninig off screen.

Addition:
My mouse cursor jumps couple pixels when I press left or right button. It starts just about same time. Not sure if it's related.

---

### Post by palm86 on 2013-02-13
Sounds like tclahr and Roman. V. had the same issues I had (unity broken, mouse jumping after click, not able to wake up after suspend).

I tried everything, but couldn't find a solution. In the end I installed quantal and that solved everything for me. Note I did a reinstall, maybe a simple upgrade will work as well. Mind you, I haven't done all the quantal updates yet, but I'm not sure I want to!

---

### Post by Roman.V. on 2013-02-15
Today I got pack of about 50 new updates.

All my troubles fixed with it.

---

