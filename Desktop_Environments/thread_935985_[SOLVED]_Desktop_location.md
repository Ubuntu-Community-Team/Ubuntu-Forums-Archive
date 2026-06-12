---
title: "[SOLVED] Desktop location"
date: 2008-10-02
forum: Desktop Environments
---

### Post by 311005901 on 2008-10-02
Ok. I accidentally trashed my "/home/user/Desktop" and my files in the folder don't appear on my actual desktop. Gnome now is showing my "/home/user" files on the desktop. 

How do I change the default directory back to "/home/user/Desktop"?

---

### Post by 311005901 on 2008-10-03
Bump?
Any help?

Its driving me crazy with a million folders on my desktop.

---

### Post by 311005901 on 2008-10-06
Bump?

---

### Post by vanadium on 2008-10-06
I am not sure whether this will help. Check the file ~/.config/users.dirs.dirs and check the value for XDG_DESKTOP_DIR. Probably you will need to set this back to
```

XDG_DESKTOP_DIR="$HOME/Desktop"

```
Log out and back in to see whether this was successful.

---

### Post by 3rag0n on 2008-10-06
Download and Install a software "ubuntu-tweak".
After installing, run the program and go to the "Personal" entry. You will see the paths to your desktop directory, pictures , videos directory, etc.
Just change the desktop path to suit your needs.:guitar:

---

### Post by Bucky Ball on 2008-10-06
> **3rag0n said:**
> Download and Install a software "ubuntu-tweak".
After installing, run the program and go to the "Personal" entry. You will see the paths to your desktop directory, pictures , videos directory, etc.
Just change the desktop path to suit your needs.:guitar:

Where is 'ubuntu-tweak'? Couldn't find in Synaptics.

---

### Post by 3rag0n on 2008-10-06
> **Bucky Ball said:**
> Where is 'ubuntu-tweak'? Couldn't find in Synaptics.


Try to reload the list of packages...
else go to ubuntu-tweak.com and download the software and install... very handy tool :):popcorn:

---

### Post by 3rag0n on 2008-10-06
> **Bucky Ball said:**
> Where is 'ubuntu-tweak'? Couldn't find in Synaptics.

Either refresh your package list or
go to ubuntu-tweak.com and download the latest package from there ... really handy tool!:lolflag::guitar::popcorn:

---

### Post by 311005901 on 2008-10-09
Yep.
ubuntu-tweak fixed my problem!

Thanks!

Post marked solved.

---

### Post by Hyvi on 2012-08-27
> **vanadium said:**
> I am not sure whether this will help. Check the file ~/.config/users.dirs.dirs and check the value for XDG_DESKTOP_DIR. Probably you will need to set this back to
```

XDG_DESKTOP_DIR="$HOME/Desktop"

```
Log out and back in to see whether this was successful.

it works

---

### Post by coffeecat on 2012-08-28
Old thread - closed.

---

