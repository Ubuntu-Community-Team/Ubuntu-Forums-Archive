---
title: "compiz suddenly stopped working"
date: 2007-10-21
forum: Desktop Effects &amp; Customization
---

### Post by benhur99ph on 2007-10-21
It happened last night. When I first installed Gutsy, compiz was working fine. I installed the compiz-settings-manager so that I can customize the effects and everthing worked fine. But after a few hours, I decided to adjust the settings again and compiz just stopped working. It took a few minutes before I can work on my screen again and when I checked the Visual effects, it was set to "NONE". I tried to use the "custom" settings again and the same thing happened. Even if I restarted the computer I still can't use the custom settings. I'm planning on to do a fresh install again but decided to look for help here first. Does anyone here experienced the same problem? Any help is appreciated. Thanks.

---

### Post by Beggar on 2007-10-21
```

compiz
emerald --replace

```

Post the output.

---

### Post by benhur99ph on 2007-10-23
upon typing compiz:

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5964 (rev 01) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator

(gtk-window-decorator:6943): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

PS - I don't have emerald installed....

*when I type compiz on the commandline, my screen flickers and I loose all window borders. I need to restart X to have them back. 

Help.... Thanks again.. :D

---

