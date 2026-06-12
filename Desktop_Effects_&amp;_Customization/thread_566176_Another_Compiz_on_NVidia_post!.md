---
title: "Another Compiz on NVidia post!"
date: 2007-10-03
forum: Desktop Effects &amp; Customization
---

### Post by fat_larry on 2007-10-03
Compiz doesn't start on Gusty for me, I'm using an Nvidia card:

```

adam@localhost:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 05:04.0 0300: 10de:032a (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2560x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
Segmentation fault (core dumped)
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded
```

Any ideas?  I can provide more detail if necessary. I have already tried purging and reinstalling compiz etc

---

### Post by Soybean on 2007-10-03
> **fat_larry said:**
> Comparing resolution (2560x1024) to maximum 3D texture size (4096): Passed.

2560x1024 sounds like dual monitors. How have you got that set up? TwinView? 

In a lot of cases, setting up dual monitors can break 3d acceleration for one or both of them. So that's the first thing I would check... but... I forget how. 

Did you follow some guide to get Compiz working? Most such guides included a bit about checking your 3d acceleration near the beginning. So you could go back and check that again. 

There are other things it could be too, of course... that's just the first that comes to mind.

---

### Post by FuturePilot on 2007-10-03
This might be one of the problems here. I had that same warning about the Window Manager toggle_shaded thing. Here's the solution.
Press Alt+F2 and type in gconf-editor
Navigate to apps>metacity>window_keybinding 
You should see a bunch of entries in the window on the right. Scroll down to the very bottom and you should see an entry that says toggle_shaded. There should be an empty space next to it. That's the culprit. It needs to say disabled. So edit the value to say disabled. That should do it.

---

