---
title: "Can't seem to run .run package from command line"
date: 2009-03-18
forum: General Help
---

### Post by mulluysavage on 2009-03-18
Hi,

I'm re-installing my nvidia drivers after my sound went out. My sound is back in, but I'm at 800x600 and each letter is the size of my thumb.

to compile the module for the nvidia proprietary drivers, they recommend stopping gnome and running their .run package. I am able to stop gnome, but then when I say

sudo NVIDIA-Linux-x86-173.14.18.pkg1.run

returned is:

"command not found"

even though I have typed sudo NV and then hit tab, so I know I am in the right directory and the file name is right.

Is there something I have to do to get this thing to run?

Thanks!

Phil

---

### Post by rattking on 2009-03-18
Hi 
if you are sure you want to reinstall from the .run file and not from the ubuntu packages then you can do so by
sudo sh NVIDIA-Linux-x86-173.14.18.pkg1.run

it says "command not found"
because its not executable.. you could make it executable like this
chmod +x NVIDIA-Linux-x86-173.14.18.pkg1.run
then run it
sudo ./NVIDIA-Linux-x86-173.14.18.pkg1.run

---

