---
title: "Problem with Kubuntu logout and Compiz Fusion"
date: 2007-09-01
forum: Desktop Effects &amp; Customization
---

### Post by DarkOx on 2007-09-01
I installed Compiz Fusion on Kubuntu Feisty using instructions from [https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion) and it's been working great -- except for when I log out. Then my screen goes black, and is re-drawn as the shade falls down, looking rather ugly. I didn't have this problem with the old KDE logout, so I suspect the new fade is the problem.

I tried to switch to the old style logout by playing with the settings suggested at [http://www.kde-apps.org/content/show.php/KDE+3.5.x+Alternate+logout?content=58881](http://www.kde-apps.org/content/show.php/KDE+3.5.x+Alternate+logout?content=58881) but all that did was keep the screen black while showing the logout dialogue.

Has this happened to anyone else, or better yet, has anyone managed to solve the problem?

---

### Post by FuturePilot on 2007-09-01
Happens to me. Even with KDE's built in composite manager.

---

### Post by Zorael on 2007-10-29
Does a solution exist for this?

It happens for me, running Kubuntu 7.10. It only happens if I use Compiz-Fusion *AND* if I have the Fade Windows plugin activated. KWin and C-F without that plugin active makes the problem disappear, but I'd very much like to keep the window fade.

Is there a way to just, disable that shadowfade thing entirely, leaving the desktop at 100% opacity? Or better yet, have both fade effects work at the same time.


My xorg.conf - and don't mind the comments, they're there to remind me what the hell I'm doing:
```
...

Section "Device"
    Identifier     "nVidia Corporation G70 [GeForce Go 7600]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G70 [GeForce Go 7600]"
    Monitor        "Generic Monitor"
   	Option		"NoLogo" "true"
	Option		"NvAGP" "0" # (Only if not using an AGP card. Yours should be PCI-E I'm pretty sure)
	Option		"AddARGBGLXVisuals" "True"
	Option		"AllowGLXWithComposite" "True"
#	Option		"DisableGLXRootClipping" "True" #Just do NOT use the Option "DisableGLXRootClipping" "True". Unless you have an g86 GPU card(GF 8500-8600etc) and unfortunately have to use 100.14.11 driver...  Cause it produces blinking screen stuff, low performance, sluggish operation and sometimes lockups too.
	Option		"RenderAccel" "True"
	Option		"DamageEvents" "True"
	Option		"UseEvents" "False" # (If you face frequent lockups PLEASE set this to "False". This one causes them for sure!!)
	Option		"TripleBuffer" "True" #increases latency slightly (delay between user input and displayed result).
	Option		"BackingStore" "True" # [Use this one with caution it may NOT work on all systems (freezes when load beryl-manager) but give it a try because it helps performance] It can also break Xinerama, If you get ANY kind of strange stuff(White Windows in Compiz Fusion!) after you applied the settings remove this option and try again.
	Option		"RandRRotation" "on"
    DefaultDepth    24
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050"
    EndSubSection
EndSection

Section "Extensions"
	Option		"DAMAGE" "Enable"
	Option		"RENDER" "Enable"
	Option		"Composite" "Enable"
EndSection
```

---

### Post by mikebela777 on 2008-04-28
There is a solution:

Open: ~/.kde/share/config/ksmserverrc (for example with Kate).

Then you have to enable the new FancyLogout, but you have also reduce the FancyLogoutFadeTime and the FancyLogoutFadeBackTime to 0:

------- snip -------
[Logout]
doFancyLogout=1
doFancyLogoutFadeTime=0
doFancyLogoutFadeBackTime=0
------- snip -------

This works for me. And I have nvidia video card too.

---

### Post by Zorael on 2008-04-29
> **mikebela777 said:**
> [Logout]
doFancyLogout=1
doFancyLogoutFadeTime=0
doFancyLogoutFadeBackTime=0

Worked like a charm, many thanks.

---

