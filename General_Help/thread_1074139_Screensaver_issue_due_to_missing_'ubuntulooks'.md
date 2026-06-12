---
title: "Screensaver issue due to missing 'ubuntulooks'?"
date: 2009-02-18
forum: General Help
---

### Post by RgnKjnVA on 2009-02-18
In 8.10 I'm having an odd issue on my Dell Latitude 610 laptop with the screensaver that I can't find any reference to online. 

The problem is that screensaver never seems to get presented but it doesn't go back to the session as referenced in many duplicate bugs I've seen online. After idle timeout or ctl-alt-L the screen fades as though it's going to screensaver but instead of displaying what's configured, I get a white screen, the exact OPPOSITE of what I want. I want a blank screen however this problem exists even if I chose another screensaver. Also, unlike many other screensaver threads I've seen, I don't have any problem returning to the session once re-activated. I noticed when starting gnome-screensaver 2.24.0 from the command line that I get the following error:

(gnome-screensaver:26088 ): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks"

Does anyone know if that error could be part of the issue? I'm at a loss and can't find anyone with the exact same symptoms...nor a solution.

Here's my graphics controller:
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

---

