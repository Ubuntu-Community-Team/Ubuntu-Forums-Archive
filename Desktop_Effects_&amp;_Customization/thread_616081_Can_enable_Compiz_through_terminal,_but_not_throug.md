---
title: "Can enable Compiz through terminal, but not through config dialog"
date: 2007-11-17
forum: Desktop Effects &amp; Customization
---

### Post by Goombie on 2007-11-17
I recently installed the Linux version of Google Earth, which didn't work that well when I ran it with Compiz. I disabled Compiz, and tried again. My computer froze. :confused:
So, then I had to shut off my computer, as none of the keyboard commmands (Ctrl Alt Backspace, etc) worked. When I restarted, I tried to enable Compiz again using the "Visual Effects" tab in the "Appearance Preferences" dialog, but all I got was the error message "Desktop effects could not be enabled". Now, I tried running compiz in a terminal, and it works fine. Here's the output for that:

```

goombie@goombie-laptop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4e50 (prog-if 00 [VGA])
        Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 32, IRQ 18
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator

```

So, I frankly don't get it. Why would Compiz refuse to run from the config dialog, but run fine through the terminal? And, how can I fix this? I already uninstalled Google Earth, too. Thanks for the help!

---

### Post by Forlong on 2007-11-18
That's weird indeed.
Try running
```
gnome-appearance-properties
``` in a terminal, enable the visual effects and tell us about the output.

---

### Post by Goombie on 2007-11-18
Well, I could, but I seem to have the problem fixed now. I just deleted my ~.gconf/apps/compiz folder (I think it was that one), and now Compiz is working again. My theory is that maybe Google Earth somehow managed to muck up a setting in Compiz. I don't know for sure, though. I mean, what do Google Earth/Compiz have in common?

---

### Post by Goombie on 2007-12-01
Sorry for the double-post, but Compiz has broken on me again. 
I'm going to post the output of the gnome-appearance-properties command here. This is when I enable Compiz:

```

goombie@goombie-laptop:~$ gnome-appearance-properties

No nvidia hardware available
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4e50 (prog-if 00 [VGA])
        Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 32, IRQ 18
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator

(gnome-appearance-properties:7465): GLib-CRITICAL **: g_array_free: assertion `array' failed

(gnome-appearance-properties:7465): GLib-CRITICAL **: g_array_free: assertion `array' failed

```
Should I be concerned about those two error messages at the end?
So yeah, same problem as before: I can enable compix when I run gnome-appearance-properties  or compiz in a terminal, but not when I open the appearance preferences dialog through the menu.

---

