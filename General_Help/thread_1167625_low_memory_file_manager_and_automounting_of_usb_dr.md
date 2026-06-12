---
title: "low memory file manager and automounting of usb drives"
date: 2009-05-23
forum: General Help
---

### Post by keithpeter on 2009-05-23
Hello All

I've got a command line install of ubuntu with dwm on top running without a desktop manager (I log in and type startx). Ram use is 39Mb at the cli prompt and 70Mb at the desktop with no applications running.

I'd like suggestions for a low memory file manager that can also recognise USB sticks when plugged in, so maybe a file manager and a separate automount program.

(The reason for all this messing about is to use a 256Mb laptop without too much swapping)

---

### Post by x33a on 2009-05-23
for low mem file manager, i would suggest midnight commander.

---

### Post by keithpeter on 2009-05-23
> **x33a said:**
> for low mem file manager, i would suggest midnight commander.

Yup, I have installed that one to try. It works in a terminal window and so only adds about 5Mb when running. 

Anyone ideas on what to use as a separate 'automount' application? I'm assuming that would have to run all the time as it would need to detect devices being plugged in and out.

Thanks

---

### Post by x33a on 2009-05-23
> **keithpeter said:**
> Anyone ideas on what to use as a separate 'automount' application? I'm assuming that would have to run all the time as it would need to detect devices being plugged in and out.

i don't understand what you mean, because any device you plug in is automatically mounted in normal ubuntu.

---

### Post by keithpeter on 2009-05-23
> **x33a said:**
> i don't understand what you mean, because any device you plug in is automatically mounted in normal ubuntu.

I'm not using Gnome or KDE, just running command line ubuntu with X and dwm. My understanding is that in Gnome, when you plug a USB drive in, nautilus recognises the event and mounts the volume automatically. When I plug a stick into this minimal system, I'm not seeing anything under /media/, so its not automounting. I'd be delighted to be proved wrong on that one!:D

Anyone else any ideas?

---

### Post by kerry_s on 2009-05-23
you can try pcmanfm or thunar, i prefer thunar on my 450mhz 256mb ram laptop, i use jwm for the window manager.
70mb at the desktop? dwm is heavier than i thought. you might as well run xfce4 i got around 80mb on there.

1st pic no programs
2nd pic with firefox

---

### Post by mcduck on 2009-05-23
pcmanfm is a great one, and supports both automounting of removable drives and desktop (if you want).

---

### Post by kerry_s on 2009-05-23
> **keithpeter said:**
> I'm not using Gnome or KDE, just running command line ubuntu with X and dwm. My understanding is that in Gnome, when you plug a USB drive in, nautilus recognises the event and mounts the volume automatically. When I plug a stick into this minimal system, I'm not seeing anything under /media/, so its not automounting. I'd be delighted to be proved wrong on that one!:D

Anyone else any ideas?

ivman can do that auto stuff, does not depend on a file manager.

---

### Post by keithpeter on 2009-05-23
> **kerry_s said:**
> you can try pcmanfm or thunar, i prefer thunar on my 450mhz 256mb ram laptop, i use jwm for the window manager.
70mb at the desktop? dwm is heavier than i thought. you might as well run xfce4 i got around 80mb on there.x

Hello kerry_s and mcduck

pcmanfm brings Gnome libraries with it and some of those have 'keychain' in the name so I'm steering clear ;) 

Tried ivman using [another post from kerry_s]("http://ubuntuforums.org/showthread.php?t=512281"). Installs pmount. Reads CD-ROMs ok, but warns about device having an entry in /etc/fstab. Won't mount usb sticks, error message says "Error: device /dev/sdd1 is not removable Error: could not execute pmount". Turns out this is a bug,

[https://bugs.launchpad.net/bakery/+bug/157324](https://bugs.launchpad.net/bakery/+bug/157324)

and the workround in Ubuntu Intrepid was to use gnome-mount instead of pmount and change the ivman configuration. Any escape from Gnome dependencies in this area?

Thanks

---

### Post by kerry_s on 2009-05-23
> **keithpeter said:**
> Hello kerry_s and mcduck

pcmanfm brings Gnome libraries with it and some of those have 'keychain' in the name so I'm steering clear ;) 

Tried ivman using [another post from kerry_s]("http://ubuntuforums.org/showthread.php?t=512281"). Installs pmount. Reads CD-ROMs ok, but warns about device having an entry in /etc/fstab. Won't mount usb sticks, error message says "Error: device /dev/sdd1 is not removable Error: could not execute pmount". Turns out this is a bug,

[https://bugs.launchpad.net/bakery/+bug/157324](https://bugs.launchpad.net/bakery/+bug/157324)

and the workround in Ubuntu Intrepid was to use gnome-mount instead of pmount and change the ivman configuration. Any escape from Gnome dependencies in this area?

Thanks


dude, don't worry about libs, gnome or otherwise they don't affect anything. there used when the program is used and removed when the program is closed. trust me on this i work on low resource everyday and barely ever drop into swap. stick with gnome and xfce4 programs and you'll be fine.

i'll drop you some tips when i get on my laptop. i'm working on getting my desktop set backup, had to pop in another drive, the other 1 started to go.

---

### Post by kerry_s on 2009-05-23
that's start with tweaking the memory.
in /etc/sysctl.conf put this:

```

vm.overcommit_memory = 1
vm.overcommit_ratio = 95
vm.dirty_ratio = 5
vm.swappiness = 1

```

that will use more of your actual ram, rather than swap.

putting /tmp and /log in to ram will help prevent disk write slow downs.
in /etc/fstab add these:

```

none 		       /tmp          tmpfs     defaults            0      0
none 		       /var/log      tmpfs     defaults            0      0

```

about the file manager with mounting, trust me grab thunar, it works beautifully, i also use mousepad for the editor, i even use xfce4-shooter to take screen shots.
in fact even if i opened almost every program i might work with in a day at the same time, i'd still have half my memory.

---

### Post by kerry_s on 2009-05-23
here's xfce4 mem usage looks like at startup after tweaking.
so you can do a lot better than 70mb at the desktop.

---

