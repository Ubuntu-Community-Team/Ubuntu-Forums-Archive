---
title: "Root App's Theme"
date: 2009-01-07
forum: Desktop Environments
---

### Post by fisherm on 2009-01-07
Hello, I am trying to make apps running as root (Synaptic, gksu nautilus, etc.) have a distinctly root-ish look. I was successful in part of this by enabling the root login function and using the GUI to link my chosen icons, and custom red window border into /usr/share/themes and then installing them via System>Appearances. I also changed the color scheme to have active items reddened. While logged in as root everything looks wonderful. When I log out and then back in as myself some things don't work. Icons in Synaptic are fine, as is the control theme (ClearlooksClassic instead of Human). But the color scheme is back to my user's setting, and it doesn't use my red window border. Any ideas would be greatly appreciated. Thanks in advance for any assistance.

---

### Post by weblordpepe on 2009-01-07
> **fisherm said:**
> Hello, I am trying to make apps running as root (Synaptic, gksu nautilus, etc.) have a distinctly root-ish look. I was successful in part of this by enabling the root login function and using the GUI to link my chosen icons, and custom red window border into /usr/share/themes and then installing them via System>Appearances. I also changed the color scheme to have active items reddened. While logged in as root everything looks wonderful. When I log out and then back in as myself some things don't work. Icons in Synaptic are fine, as is the control theme (ClearlooksClassic instead of Human). But the color scheme is back to my user's setting, and it doesn't use my red window border. Any ideas would be greatly appreciated. Thanks in advance for any assistance.

What happens if you run the **gnome-appearance-properties** program with **sudo** within a regular user session?

---

### Post by fisherm on 2009-01-07
I tried that also, and it gets the same result as above with an error message before opening, 

"Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager."

I am too uninformed to know if any of that explains why it isn't working. FWIW I am running an up to date 8.04 with the default GNOME.

---

### Post by Coreigh on 2009-01-07
This is an excellent idea! Any application run as sudo or gksudo should ALWAYS have some visual cue that this is a priviledged application. I have seen other distros do this why doesn't Ubuntu do this? Where do we submit ideas for future releases?

---

### Post by fisherm on 2009-01-07
I wish I could say I had the idea first, but I didn't. I got the fever from someone else mentioning it, but now I feel that I have to figure it out. I just recently got my wife and brother converted to Linux, and I want them to have an OBVIOUS visual cue when working as root. And it's not a bad idea for the more accustomed user anyway in my opinion.

---

