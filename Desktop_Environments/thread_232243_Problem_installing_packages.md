---
title: "Problem installing packages"
date: 2006-08-08
forum: Desktop Environments
---

### Post by simblog on 2006-08-08
Hi there . . . I'm trying to install a package called fluidsynth.  I keep getting this error message :

Error: conflicts with the installed package : 'fluidsynth'

I've checked and fluidsynth is not listed as already installed.  Has anyone ever encountered this problem?

---

### Post by jeff_ on 2006-08-08
How are you trying to install the package? Through Synaptics Package Manager or did you manually download a .deb file?

---

### Post by simblog on 2006-08-09
I manually downloaded the package (.deb) and am using GDebi to install.

---

### Post by jeff_ on 2006-08-09
Try searching for it in the Synaptic Package Manager under System > Administration and installing it that way.

---

### Post by mg3kc on 2006-08-09
> **simblog said:**
> I manually downloaded the package (.deb) and am using GDebi to install.

Why not install it using apt-get...

sudo apt-get install fluidsynth

works for me... now I just need the musical talent! :D

---

### Post by simblog on 2006-08-10
Thanks for the help guys I really appreciate it!!

I tried typing "sudo apt-get install fluidsynth_1.0.6-4_i386.deb"

I got this error message:

"E: Couldn't find package fluidsynth_1.0.6-4_i386.deb"

And synaptics shows me the file but won't let me select it!!

Help - whats happening!?!?

---

### Post by simblog on 2006-08-10
It's ok - I finally got it oworking - I got synaptics to search for and uninstall fluidsynth - and then it re-installed fine.  


Thanks guys.

---

