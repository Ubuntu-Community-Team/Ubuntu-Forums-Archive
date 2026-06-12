---
title: "When I drag the mouse, CPU usage shoots up to 100%"
date: 2005-12-23
forum: Desktop Environments
---

### Post by Adam Lee on 2005-12-23
Hi, I just finished fresh install of Breezy and successfully (I think) configured ATI card. The system is updated.

Well, the problem, which is seemingly minor and yet annoying, is that when I drag my mouse across the desktop, the CPU usage goes up to 100%. 

Not only that, as I make the box (you know when you select icons) bigger, the box drawn doesn't get bigger quick enough to catch up the speed of my mouse pointer. It's behind by about 1/3 secs.

Having said this, this wasn't the problem in SuSE10. Although I wasn't able to get the 3D working, this problem disappears when I install the ATI driver.

One last thing I need to mention is that glxgears doesn't give me any output. I can see the 3D animation, but no result whatsoever.
Only fgl_glxgears works and I think it gives me a reasonable result.

Any ideas?

Oh, by the way this is not Gnome specific issue. I tried both Gnome and KDE and both have this problem.

Thanks in advance.
Regards,
Adam

---

### Post by Leigh on 2005-12-23
Open a terminal prompt and type **glxgears -printfps**.

---

### Post by Adam Lee on 2005-12-23
[QUOTE=Leigh]Open a terminal prompt and type **glxgears -printfps**.[/QUOTE]

aha, that worked. But why wouldn't "glxgears" work? 
Thanks

---

### Post by rikai on 2005-12-23
I believe that they disabled the fps because people were trying to use glxgeears as some sort of benchmarking utility, which it isnt.

---

### Post by Adam Lee on 2005-12-23
[QUOTE=rikai]I believe that they disabled the fps because people were trying to use glxgeears as some sort of benchmarking utility, which it isnt.[/QUOTE]

ah...I see 
Thanks : )

---

### Post by markdarb on 2008-02-10
Over two years later and this still seems to be an issue (although perhaps not for the same reason; I don't know).

Sometimes when I try to select things on the desktop the CPU shoots up to 100% (or rather 50%, since my CPU is dual core, but the system still seems to grind to a halt). When this happens the box showing the selected area becomes very jerky: it can freeze for several seconds, and take several seconds more to catch up.

I'm using desktop effects on the "Extra" setting. It's a laptop (Dell Inspiron 1520) with Intel 2.2Ghz duo processor, 3GB RAM, NVidia graphics card (256MB, I think). I see no reason for this to happen.

This doesn't happen all the time, and I don't have any idea what cause it might be associated with. When it last happened (a few minutes ago) I tried changing my desktop from the photo I was using to a solid colour to fix it, and that worked. But then when I changed my wallpaper back to the photo it was still working fine, so using a solid colour instead of a jpeg probably wasn't the solution (although changing the desktop background did seem to instantly fix the problem).

Does anyone know why this happens, or if it will be fixed for good in Hardy?

---

### Post by markdarb on 2008-02-12
When this happens to me it is the Xorg process that hogs the CPU.

Again, changing the desktop background (whether to another very high definition photo or a solid colour) fixes the problem, even if you change it back again.

The last time it happened I was using Firefox, Tomboy Notes and Evolution, none of which should have had anything to do with it.

---

### Post by linux23dragon on 2008-02-15
Well the AtI drivers should be better theses days and it should be a non-issue.  Also the notebooks are not clocked the same as the desktop PC's .  The CPU's will run under clocked to save battery life, unless the applications demand for more CPU cycles or system resources.

---

