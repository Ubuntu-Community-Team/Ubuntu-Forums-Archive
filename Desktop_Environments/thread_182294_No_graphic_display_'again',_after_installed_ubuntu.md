---
title: "No graphic display 'again', after installed ubuntu 5.10 64bit on my amd64."
date: 2006-05-25
forum: Desktop Environments
---

### Post by sidy on 2006-05-25
On my PC I have one hd40 (slave, where I run ubuntu 6.06) and another hd80 (the master, where I've just installed ubuntu). In other words I have 120GB on my PC.
Now, because my hd40 is full, I w'd like to transfer datos to the 80hd.
I dont know how.

WHAT HAD I TRYED?
Installed ubuntu on the 80hd, but didnt display graphic (again, "it had happened when I installed ubuntu on 40hd as well). So then, I tryed to do what I'd done before, 'ctrl+alt+F1', and logged in:

Typed 'lspci' to get the graphic card details (nVidia Corporation NV34 [GeForce FX5200LP] (rev a1), then:

'sudo dpkg-reconfigure xserver-xorg'

then I choose:

'nv' 

enter:

'nv nVidia FX5200LP' 

And the problem was suppost to be sorted, but it didn't.

So I rebboted and logged in to ubuntu on 40hd.
I've tryed to save datos on hda2, but no allowed.(not saving datos in, or evan deleting the hda1 or 2 or 3 to mount again). (I had mounted them before (hda1 hda2 hda3)).
So on the terminal, I tryed:

'sudo mount /dev/hda2 /mnt/hda2'  (by the way I've tryed without 'sudo')

then enter, came up 

'mount: you must specify the file system file'

then I typed 

'cd hda2' 

enter 

'ls'

Didn't show any thing, because there is nothing there, then nautilus. ... I can only open, but not alowed to copy or even delete to mount again.

So basically, I would like to use both hdds.
WHAT CAN I DO TO USE BOTH HDDS AT THE SAME TIME?
Or](*,) 
HOW CAN I DISPLAY GRAPHIC?

---

