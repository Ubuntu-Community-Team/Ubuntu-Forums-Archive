---
title: "turning off desktop"
date: 2009-10-20
forum: Desktop Environments
---

### Post by tar1 on 2009-10-20
I'm new to the forum.  Using the new Ubuntu beta I  am trying to turn the desktop off so I can get different  images on the four sides of the cube.  Everything goes ok until I try to turn  the desktop off in nautilus.  Going to gconf-editor >apps>nautilus>show desktop. I get a series of loop like figures streaming across the bottom of the screen.  These disappear when I repress the show desktop button. Any ideas?  Thanks in advance.

---

### Post by duanedesign on 2009-10-22
The 'show desktop' function toggles the visibility of icons on the desktop. If i understand corectly, it sounds like this is not what you are trying to do. Regardless it should not create "loop like figures".

---

### Post by Dullstar on 2009-10-22
>  Using the new Ubuntu beta I  am trying to turn the desktop off so I can get different  images on the four sides of the cube

I don't think this question has ever been answered throughout the many times it has been asked...

---

### Post by undecim on 2009-10-22
It seems to he that you are following a howto from somewhere. Basically the process to get 4 different wallpapers on 4 different sides of a cube involves turning off nautilus's "show desktop" feature and turning on the wallpaper plugin in compiz

Could you post a screenshot? this could potentially be a graphical glitch or something to do with compiz

---

### Post by tar1 on 2009-11-03
Thanks for the three responses.  I did find a work around that seemed to "cure" the problem-- a loop like series of "starting file manager" streaming across the lower panel.  I simply deleted the hidden file "gnome.desktop" and it worked ok.  Thus I was not able to get the desktop anymore.  I have installed 9.10 through wubi and also from the live disk to a usb disk and have had no problems.

I might add that the problem occurred immediately after I installed 9.04 and before I downloaded a nvidia driver and before installing compiz.  So it seems it was a problem with the gnome desktop manager.

---

