---
title: "unwanted transparancy"
date: 2009-05-28
forum: General Help
---

### Post by jameslite on 2009-05-28
I've recently installed Vbox, and it works fine, but today, I ran it and BAM! the thing goes transparent (see screens 1 and 2 for examples)  

The only other programme that I use that seems to be doing this is Kolourpaint.(screen 3) scribbling the colour black lets me see the background, scribbling with another colour lets me see the background in a pleasing shade. if I resize the picture, it makes the colours solid, but I can go over them to see the background again.

Also, the background on the menu (file, edit etc) seems to have disappeared, it's only the basic shell of a box and white text, which I can't read.

 I use 9.04

what's going on? :?

---

### Post by eldragon on 2009-05-28
2 things:

1st: you are using UXA DRI, which has a transparency bug. thats why a slightly transparent window goes all crazy.

2nd: your window is set to be slightly transparent. do an alt-scroll on it to see if gets fixed.

---

### Post by uidb4056 on 2009-05-28
> **jameslite said:**
> I've recently installed Vbox, and it works fine, but today, I ran it and BAM! the thing goes transparent (see screens 1 and 2 for examples)  

The only other programme that I use that seems to be doing this is Kolourpaint.(screen 3) scribbling the colour black lets me see the background, scribbling with another colour lets me see the background in a pleasing shade. if I resize the picture, it makes the colours solid, but I can go over them to see the background again.

Also, the background on the menu (file, edit etc) seems to have disappeared, it's only the basic shell of a box and white text, which I can't read.

 I use 9.04

what's going on? :?

It seems that there is a bug that temporary can be workaround creating a new menu entry for virtualbox with this command:

env XLIB_SKIP_ARGB_VISUALS=1 VirtualBox

Then you will have another way to start Virtualbox without problems and you can test if is fixed using the standard menu option.

---

### Post by jameslite on 2009-05-28
> **uidb4056 said:**
> It seems that there is a bug that temporary can be workaround creating a new menu entry for virtualbox with this command:

env XLIB_SKIP_ARGB_VISUALS=1 VirtualBox

Then you will have another way to start Virtualbox without problems and you can test if is fixed using the standard menu option.


brilliant, this seems to have fixed it.

Thank you!

---

