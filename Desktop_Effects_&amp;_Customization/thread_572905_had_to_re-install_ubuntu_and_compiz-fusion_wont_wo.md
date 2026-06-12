---
title: "had to re-install ubuntu and compiz-fusion wont work"
date: 2007-10-10
forum: Desktop Effects &amp; Customization
---

### Post by chrisruls00 on 2007-10-10
when I type compiz --replace I get

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0175 (rev a3) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity 

```

what do I do?

---

### Post by joshuachad on 2007-10-10
Either you have the world crappiest vid card or compiz isnt getting the amount of vid memory correctly. Sorry but I am too lazy right now to give you an elegant way to fix this so try this in a terminal:

sudo gedit /usr/bin/compiz
One the file is open go to the line where it says:
NVIDIA_MEMORY="65536" # 64MB

and change that line above to this
NVIDIA_MEMORY="0" # 64MB

click save then try starting compiz.

---

### Post by joshuachad on 2007-10-10
tell me what kind of vid card you have also. There may be something else wrong.

---

### Post by Forlong on 2007-10-11
Please run Compiz like this and tell us what it does:
```
SKIP_CHECKS=yes compiz
```

---

### Post by chrisruls00 on 2007-10-11
it works but no window decorations. Thanks!
Have any Idea how to get window decorations?
Nevermind! I was missing some xorg.conf options, i added them and now it works.

---

### Post by chrisruls00 on 2007-10-12
Well the windows go black after a while, but I think I found a fix. I'll try it when I get home from school.

here is the fix:

```
NVIDIA

After a while, windows begin to go black

This is the infamous Black-Window Bug with the NVIDIA driver. It is caused by the graphics card running out of texture memory, and therefore all remaining windows (which are textures) will be black. If you have less than 128MB of video memory, disabling blur, and launching Compiz with --indirect-rendering will reduce the appearance of the bug.
```

Anyone have anything else for me to try?

---

### Post by FuturePilot on 2007-10-12
I think Trevino's version of CF might be the only one that has this, but you could try the --use-copy flag when starting CF.

---

