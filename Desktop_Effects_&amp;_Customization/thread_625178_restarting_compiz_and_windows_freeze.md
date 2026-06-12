---
title: "restarting compiz and windows freeze"
date: 2007-11-27
forum: Desktop Effects &amp; Customization
---

### Post by quantumboy85 on 2007-11-27
I was using Amaya, which doesn't display correctly when desktop effects are running. I found that I could disable Compiz by typing the following into the terminal

```
 metacity --replace & killall compiz compiz.real
```

this works. However, when I try to replace metacity with compiz again by typing

```
 compiz --replace 
```

or restarting my computer, some of the the windows lose their boarders and all of them freeze, I can't move them or resize them. Compiz worked without any problems before this. I tried completely removing and then reinstalling all the compiz related packages I could find, this had no effect. Metacity works fine.
This is the output when I try replacing metacity

```

linux:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2562 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: freedesktop

```

---

### Post by quantumboy85 on 2008-02-09
This problem somehow fixed itself.
Doing this through the GUI is safer than with the terminal
System->Preferences->Appearance->Visual Effects

---

