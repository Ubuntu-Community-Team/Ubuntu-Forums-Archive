---
title: "Kubuntu messed up..."
date: 2005-09-07
forum: Desktop Environments
---

### Post by petesmc on 2005-09-07
Hey,

Recently I typed "apt-get upgrade" (i think) because it said it'd update all the libraries and programs I had installed. But now when i boot kubuntu, it just goes to the shell and doesn't open Kde anymore.

How do i fix this?

---

### Post by ltmon on 2005-09-07
[QUOTE=petesmc]Hey,

Recently I typed "apt-get upgrade" (i think) because it said it'd update all the libraries and programs I had installed. But now when i boot kubuntu, it just goes to the shell and doesn't open Kde anymore.

How do i fix this?[/QUOTE]

Try typing into the console:

sudo /etc/init.d/kdm start

And let us know what happens.

L.

---

### Post by petesmc on 2005-09-07
[QUOTE=ltmon]Try typing into the console:

sudo /etc/init.d/kdm start

And let us know what happens.

L.[/QUOTE]
 It just says: 

Starting K Display Manager...             fail.

---

### Post by ltmon on 2005-09-07
[QUOTE=petesmc]It just says: 

Starting K Display Manager...             fail.[/QUOTE]

Nasty :(

Can you look at the file:

/var/log/Xorg.0.log

for any errors (there's a key up the top, something like "ee" indicates an error).  The most likely place to look is at the bottom of the log.

L.

---

### Post by petesmc on 2005-09-07
[QUOTE=ltmon]Nasty :(

Can you look at the file:

/var/log/Xorg.0.log

for any errors (there's a key up the top, something like "ee" indicates an error).  The most likely place to look is at the bottom of the log.

L.[/QUOTE]
 Only error is:

Failed to load the Nvidia kernel module.


I tried to install the nvidia-glx things, but i still get the same error.

---

### Post by ltmon on 2005-09-07
[QUOTE=petesmc]Only error is:

Failed to load the Nvidia kernel module.


I tried to install the nvidia-glx things, but i still get the same error.[/QUOTE]

Edit the file:

/etc/X11/xorg.conf

and change the bit under the "Device" section:

Driver        "nvidia"

to read:

Driver        "nv"

Then do:

sudo /etc/init.d/kdm start

This should get you your graphical display back, but it won't solve the nvidia problem.  You won't have 3d graphics now.

Once that's working I suggest you remove nvidia-glx and reinstall it again following the guide at [https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia).  If that doesn't work post again.

L.

---

### Post by petesmc on 2005-09-07
[QUOTE=ltmon]Edit the file:

/etc/X11/xorg.conf

and change the bit under the "Device" section:

Driver        "nvidia"

to read:

Driver        "nv"

Then do:

sudo /etc/init.d/kdm start

This should get you your graphical display back, but it won't solve the nvidia problem.  You won't have 3d graphics now.

Once that's working I suggest you remove nvidia-glx and reinstall it again following the guide at [https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia).  If that doesn't work post again.

L.[/QUOTE]
 That worked perfectly! THanks!

---

