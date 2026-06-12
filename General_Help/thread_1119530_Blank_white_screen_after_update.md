---
title: "Blank white screen after update"
date: 2009-04-08
forum: General Help
---

### Post by Zireth ZH on 2009-04-08
I run ubuntu 8.04 lts hardy.. after an update of 200 and so mbs.. i was told to reboot... i did that and as soon as a i try to log into any of my sessions the only thing i can see is a blank white screen with a cursor...

At the grub thingy to select the OS when u boot the pc... i selected the recovery option and used all the options in there.. i dun even noe what to do now...

any advice?

thanks

---

### Post by patagonik on 2009-04-08
Hi there!
It happened the same to me after upgrading 8.04 to 8.10... although everything seems to be there (one or two seconds before my screen goes white I'm able to see the gnome-panel, the icon on the desktop, etc) there is no way to see anything else than a white cover over the desktop, plus the mouse pointer.

A curious thing is that I used the water effect from compiz, and it did worked, but reaaaaaaally slowly. Also the surtcut Ctrl+Alt+Right will produce a phantom of the cube rotation (the screen remains white but you can see the shape of the turning cube for a second).

I've entered to gnome in the Terminal mode, and removed Compiz and all its components, and nothing happened, the problem persists.

So I would also like to know if someone knows what to do. I've been suggested to remove the .gnome2 configuration file (or folder... don't know) from the home directory, but as I'm at work I couldn't do it and check what happened.

Suggestions?

Cheers

---

### Post by patagonik on 2009-04-10
bump! 
Anyone??? I'm quite stuck here!

---

### Post by patagonik on 2009-04-12
SOLVED -> sudo aptitude remove compiz-core

cheers

---

