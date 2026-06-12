---
title: "Compiz problem"
date: 2009-06-30
forum: Desktop Environments
---

### Post by LinuxGreg on 2009-06-30
Ok well i have done a TON of searching and no one has been able to solve my problem...
I had compiz running perfectly on my PC but i had just booted it up this morning and i got an error message that my AWN would not start. Then i found my Effects to not be working. I had thought this was odd so i went to appearance and what do you know? My visual effects were off. i said "oh, well i will just turn them on" only to realize it would not enable.

 I'm running 9.04 Jaunty, my Nvidia grpahics card info...


Graphics Processor: GeForce2 MX/MX 400
VBIOS Version:        03.11.01.30.97
Memory:                 64 MB

Bus Type:                AGP 4X
Bus ID:                   1:0:0 
IRQ:                       16
X Screens:              Screen 0
Display Devices:      Princeton Graphics Systems PrincetonEO705 (CRT-0)

  I got this message when i got to my x server thing

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

so I go off and run "sudo nvidia-xconfig" and reboot

When I log back in I enabled my Custom Desktop Effects.  Once they enabled my awn started, but it was only a blank white bar accross the bottem of my screen.  Also my windows all lost their title bars..

Any help would be apreciated!!!!

---

### Post by ajgreeny on 2009-06-30
Have you updated to a new kernel recently.  If so you may need to reinstall the restricted driver for your graphics card.

---

### Post by GenePayne on 2009-06-30
This isn't a full solution, but it might address your problem of window title bars missing. This used to occasionally happen to me, and when it did I would go into CompizConfig Settings Manager, disable and then re-enable "window decoration" and then my title bars would re-appear.

---

### Post by LinuxGreg on 2009-06-30
dang the window thing did not work.  As for the new kernal I believe i updated to 9.04 about 5 days after it came out, so i do not believe that is the case.  however how would i update it?

Also i ran a compiz check and everything was OK 
|||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||

Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK ]


SOMEONE HELP PLEASE!

---

### Post by LinuxGreg on 2009-07-01
Anyone?

---

