---
title: "how to solve it?"
date: 2008-03-12
forum: Desktop Effects &amp; Customization
---

### Post by mathslinux on 2008-03-12
after  l updated  my ubuntu  from gutsy to hardy , desktop effects can't work .it shows "Desktop effects could not be enabled", 
when l use the command glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: GeForce FX 5200/AGP/SSE2/3DNOW!
how can l do to make it  work?

---

### Post by Zorael on 2008-03-12
Hardy is under development and should not be installed on your desktop computer as of yet. So this thread might be better located in the [ Hardy Development](http://ubuntuforums.org/forumdisplay.php?f=305) forum. Those who frequent that board will likely be able to offer better help.

That said, what is the output of the following command, entered in a console?
```
compiz --replace
```

"Desktop effects could not be enabled" is a fairly vague error message, heh.

---

### Post by mathslinux on 2008-03-13
compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0322 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

---

### Post by Zorael on 2008-03-13
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/195937](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/195937) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Curious! This could be a Hardy-only thing (as, again, it's still under development and should not be assumed to work at all times).

Could it be related to [this Hardy bug?](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/195937)

It looks like there's a conflict between Compiz and other compositioning services, such as KDE's, Xfce's or Gnome's internal ones.

---

