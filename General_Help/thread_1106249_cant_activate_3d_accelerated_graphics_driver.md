---
title: "cant activate 3d accelerated graphics driver"
date: 2009-03-25
forum: General Help
---

### Post by ducamie on 2009-03-25
hi.

my video playback is all choppy and my graphics are poor. when i activate the recommended graphics driver i get the black screen on start up. i fixed this however through recovery mode but i'd like to be able to activate it.

is there a way to get it to work without the black screen?

thanks.

---

### Post by evilaim on 2009-03-25
Well, I've had this issue myself a few times, but lets see if we can help you out.

Lets start with what Video card do you have installed?  Can you please paste your xorg.conf and what Ubuntu version are you using?

---

### Post by ducamie on 2009-03-25
hi,

VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go] (rev a3)

how do i paste the contents of my xorg.conf? sorry im a noob.

im using 8.10

---

### Post by evilaim on 2009-03-25
sudo gedit /etx/X11/xorg.conf

then copy the text and paste it in the window you use here.

---

### Post by ducamie on 2009-03-25
weird, its empty. i assume you meant etc not etx but i tried both and the file is empty. :S

i could have messed it up when i tried to revive my screen when it went black. i did mess with that file.

---

### Post by PetterDK on 2009-03-25
> **ducamie said:**
> weird, its empty. i assume you meant etc not etx but i tried both and the file is empty. :S

i could have messed it up when i tried to revive my screen when it went black. i did mess with that file.

Then do

```
sudo nvidia-xconfig
```

---

### Post by ducamie on 2009-03-25
Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a
                  Driver line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

---

### Post by Yellow Pasque on 2009-03-25
Try googling a program called Envyng.

---

