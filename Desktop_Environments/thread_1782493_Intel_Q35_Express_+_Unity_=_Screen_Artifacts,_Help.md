---
title: "Intel Q35 Express + Unity = Screen Artifacts, Help?"
date: 2011-06-14
forum: Desktop Environments
---

### Post by Illydth on 2011-06-14
System:  
Dell Optiplex 755
Intel 82Q35 Express Integrated Controller
Intel Core 2 Duo E6550 @ 2.33
2G Memory
2 x Dell 20" Flat Screens working in Extended Desktop Mode.

So I just upgraded to 11.04 today (from 10.04 -> 10.10 -> 11.04). 

Logged into the KDE Desktop (looks nice) without any problems, the system seems to function well and all looks good.

Logged back out and over to "Ubuntu" (Unity Desktop).

Disaster.  The desktop came up but every window that appears leaves an artifact on the screen.  As you drag any window it leaves that window all over the place.  Opening any menu, application, etc. leaves the image of that window up and if you move the window it replicates across the screen.  Obviously, there's no refresh.  Note, however, this only happens on the DESKTOP/Background.  If I pop a menu up within a program the part of the menu inside the program window disappears normally, it's just what's outside the program window that stays on screen.

Logged out of Unity (I'm disappointed, Unity looks cool) and into "Ubuntu Classic" (Gnome).  That TOO leaves artifacts all over the place, same as Unity.  

Logged out, logged into "Ubuntu Classic (No Effects)".  Everything runs perfectly.  Dual screen, no issues, no artifacts.

Is there a way to force the same "no effects" switches into Unity as are being forced into Gnome?  

Anyone else having problems with the Intel Q35 and Unity leaving artifacts?  Am I missing some searches that deals with how to fix that?

--Illydth

---

### Post by SirYasoKuhl on 2011-06-15
I have the same Problem here.

VGA compatible controller: Intel Corporation 82Q35 Express Integrated Graphics Controller on a Fujitsu Esprimo 5925

It seems that the Graiphikkart does not have neough power to handle dualscreen. If u switch off 1 Monitor, unity should run.

Since the update to Natty, i can only run in klassik (safemode) with no 3D accelertaion.

i tried it with a fresh ISO and ran from CD - but it is the same.....


by the way the  Test shows the result, that everything should work


```
/usr/lib/nux/unity_support_test -p
```
```

OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Q35 GEM 20100330 DEVELOPMENT 
OpenGL version string:  1.4 Mesa 7.10.2

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

Unity supported:          yes
```

---

### Post by Illydth on 2011-06-17
So, basically, Unity doesn't work on the Intel Q35 Chipset.  Nicely done.

:(

Thanks, at least, for the answer...not exactly happy about that since one of the main reasons for switching up to 11.04 from the LTS was the inclusion of Unity (I love KDE but after almost 4 years of running it I was hoping to get a different interface for a while), but at least KDE still works.  These days, running in a single screen mode is unacceptable for pretty much any desktop, even the non-techie folks in my family use multiple monitors for more screen real estate.

I guess I'll mark this as "solved" since there's really nothing that can be done.

--Doug

---

### Post by merlin_zaraza on 2011-08-22
I have the same problem. Is there some fix?

---

