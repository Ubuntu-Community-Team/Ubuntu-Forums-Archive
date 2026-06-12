---
title: "[SOLVED] some effects of Compiz are not working on 7.10"
date: 2007-10-20
forum: Desktop Environments
---

### Post by bortolozzi on 2007-10-20
Hi all,

The desktop effects are enabled but some things are weird. I couldn't make the cube work, for example. I've tried to hold Ctrl+Alt and move the mouse (exactly the same thing I did with Beryl on another distro), but it didn't work.

There is an item in my System/Preferences called "CompizConfig Settings Manager". Nothing happens when I click on it. Another item, called "Compiz Settings Manager" works, but I can't make the cube work even enabling it on this tool.

Another effects, like Woobly, is also not working.

I've installed some compiz packages in order to try to make the effects work, but I haven't had too much success on my attempts.

Any suggestion?

Thanks,
Juliano

---

### Post by FredB on 2007-10-20
> **bortolozzi said:**
> Hi all,

The desktop effects are enabled but some things are weird. I couldn't make the cube work, for example. I've tried to hold Ctrl+Alt and move the mouse (exactly the same thing I did with Beryl on another distro), but it didn't work.

Have you enabled cube and cube rotation in CCSM ?

> There is an item in my System/Preferences called "CompizConfig Settings Manager". Nothing happens when I click on it. Another item, called "Compiz Settings Manager" works, but I can't make the cube work even enabling it on this tool.

You have to install CompizConfig Setting Manager with synaptic. You can tweak compiz settings after that without problems.

> Another effects, like Woobly, is also not working.

It worked for me out of-the-box. Weird !

> I've installed some compiz packages in order to try to make the effects work, but I haven't had too much success on my attempts.

Any suggestion?

Thanks,
Juliano

Is CCSM installed and working ?

---

### Post by kystorms on 2007-10-20
I have compiz AND Beryl on this install of GG.. which went flawlessly for me
but
should i remove the Beryl? I only see the red gem for Beryl, not the green  one for Compiz, and when i try to do the cube i have to go via beryl to get it

any ideas??
thanks

---

### Post by FredB on 2007-10-20
Beryl is A DEAD project. Both are in war on your computer. Just use compiz-fusion. No green gem ? Normal, I don't have it either on my gutsy (installed since beta time).

---

### Post by bortolozzi on 2007-10-21
Thanks for the prompt repply.

More information: CompizConfig Manager is already installed. Just to make sure, I have reinstalled it and the problem persists.

When I try to open CCSM, I get this error message:

Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

About Woobly, it was also working for me just after the initial setup. Then I installed some compiz packages, like this CompizConfig Manager, and it stopped working. I think I messed something up. 

Another thing that is worring me is that I have two items to configure Compiz: "CompizConfig Settings Manager" and  "Compiz Settings Manager". Only the second one shows a windows, but it doesn't look to be working. Should I uninstall something?

Thanks again,
Juliano

---

### Post by bortolozzi on 2007-10-21
All,

I found a solution for the ccsm issue. There is a problem related to version 0.6.* of compizconfig-settings-manager. It does not work on Ubuntu 7.10. So, I had to select this package, and on the menu Package of Synapctic, click on option "Force Version" and then select version 0.5.2.

Now ccsm is working.

Most of the effects are ok, but Cube is still not 100%. I can enable it, but when I try to rotate (Ctrl+Alt+Right Click and mouse move), it turn around the workspace. So, instead of having a cube with 6 sides, it looks like I have a workspace with 2 sides.

At least now it looks to be a problem of finding the right configuration for compiz.

Thanks a lot for your help.

Juliano

---

### Post by bortolozzi on 2007-10-24
The answer to the last problem is a just a matter of setting the desktop size (a tab under General options in CCSM) to at least 4.

---

