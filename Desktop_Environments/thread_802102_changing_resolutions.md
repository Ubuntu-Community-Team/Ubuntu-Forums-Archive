---
title: "changing resolutions"
date: 2008-05-21
forum: Desktop Environments
---

### Post by Pyeti on 2008-05-21
hi
i've finally jumped into linux and so far its been all good apart from the occasional hiccup (wireless and sound mainly). my latest problem is that xubuntu doesn't have an option to set the screen to my native resolution (1280 x 800) and instead sticks to 1280x768. i have tried a number of guides but i couldn't find a solution. i also have compiz installed if that makes a difference. thanks in advance to anyone who can help me

---

### Post by morgengenuss on 2008-05-21
well, the first (and maybe most important) step is to have a look into your /etc/X11/xorg.conf

since you're using xubuntu, most probably you have mousepad (text-editor) installed, so open a shell and execute:
```
sudo mousepad /etc/X11/xorg.conf
```
then go to the screen-section, there the SubSection "Display" -> Modes should contain 1280x800, if not add it and save the file. then restart your xserver (either by logging out and in again or rebooting).

anyways, if you're not sure about the above simply post your xorg.conf and i'll have a look at it. (might be a good idea - especially if my instructions don't work. then you might have an issue with the graphic driver in use.)

---

