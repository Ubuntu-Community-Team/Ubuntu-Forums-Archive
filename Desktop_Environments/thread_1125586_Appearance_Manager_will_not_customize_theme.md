---
title: "Appearance Manager will not customize theme"
date: 2009-04-14
forum: Desktop Environments
---

### Post by Mil Doc Jr on 2009-04-14
I'm having an issue, I had one theme installed that had a black window background with blue font and then i put the bamboo theme on my computer.  Now I want to customize the bamboo to fit in with a different wallpaper.  The only issue that I'm having is my windows all use the bamboo setting except nautilus, which still wants to use the old black and blue setting, and all of the preview images under the controls tab are the same colors just with different looking buttons...whats up with that? Anyone know how to fix it?

---

### Post by BazookaAce on 2009-04-14
Yeah you need to manually copy the gtk-theme-folder that you downloaded (.tar.gz-file) into the themes-folder as root. 

Extract the folder, open nautilus as root, navigate to /usr/share/themes and copy the whole folder in there. Now log out, and then in again, and it should skin all applications like nautilus, synaptic etc since it now have permission to do it from root.

---

