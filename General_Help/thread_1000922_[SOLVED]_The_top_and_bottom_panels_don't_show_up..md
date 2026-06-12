---
title: "[SOLVED] The top and bottom panels don't show up."
date: 2008-12-03
forum: General Help
---

### Post by Dtortot on 2008-12-03
I did a fresh install of Ubuntu 8.10 and after rebooting the system the top and bottom panels don't show up. I have tried right clicking the desktop to select "Add new panel" but that option doesn't show up. I am a newbie, I have access to the Terminal, but I don't know what to do. I've searched the forums and the web and nothing shows up, or at least I haven't found anything useful.

I didn't remove the panels, willingly, I just added some programs (VLC, K3b) and tried to add OpenOffice 3.0. I removed, Rhythmbox, Totem and Evolution. I changed the default theme, and then changed the theme to the normal/default one, it dodn't work and neither did this post didn't really solve it: [http://ubuntuforums.org/showpost.php?p=6092559&postcount=8](http://ubuntuforums.org/showpost.php?p=6092559&postcount=8)

Thanks for your help.

---

### Post by roger_1960 on 2008-12-03
Hi

Try alt-F2 and then in the command line box that appears enter 
gnome-panel

---

### Post by Dtortot on 2008-12-03
What the...? Apparently I uninstalled gnome-panel, I am re-installing right now. Will let you know if it works. Thanks a lot!

LOL! It work, thanks roger_1960 that fixed it!

<--- N00b.

Wait... if I close the terminal the panels disappear.

---

### Post by fooman on 2008-12-03
in a terminal, try:

```
gnome-panel &
```

close the terminal and you should still be good.

---

