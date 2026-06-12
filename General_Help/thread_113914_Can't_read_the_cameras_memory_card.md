---
title: "Can't read the cameras memory card"
date: 2006-01-07
forum: General Help
---

### Post by Mastodront on 2006-01-07
Today I went and bought a digital camera (a Kodak C330). When I check the system settings I can see that KDE have found a camera. I can also type camera:/ in konqueror and it seems I get something, 2 folders and 2 textfiles (guess it's the internal 16MB memory) but I can't get to the 256MB memory where my pictures are located :/

I installed gtkam and it also finds the camera but the wrong memory :/  Anyone who has any tips?

---

### Post by Mastodront on 2006-01-08
Just wanted to say I found a solution (even though it's not an optimal one);

The camera has two modes; 'Automatic' where it saves the pictures on the memory card (if one exists), otherwise on the integrated memory. The other mode only saves to the integrated memory.

If I take pictures in automatic mode and then connect the camera to my computer it finds the camera but not the pictures...

The (strange) thing is that if I take pictures on the memory card (automatic mode), then switches to the integrated memory and take pictures there (one is enough) and then connect it to the computer. First the computer finds the picture on the integrated memory - the odd but nice thing is that all of a sudden it finds all the pictures on the memory card as well :)

/*The irony is that after a while fighting the camera in Linux I got tired and booted my WinXP-installation (first time since beginning of October). Installing the camera drivers broke my windows installation so now I can't boot it (very weird)...  So the only place I can use my Windows/MacOS camera is in one of the OS:s it doesn't support. :)*/

---

### Post by coolclassic on 2006-01-08
It may be finding the original device first i.e. integrated memory and mounting it as the first device i.e dev/sda1. You may have to create a new mounting point for your memory card this may be dev/sda2.

---

