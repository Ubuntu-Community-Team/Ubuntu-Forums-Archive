---
title: "gnome performance issues"
date: 2007-07-02
forum: Desktop Environments
---

### Post by eldragon on 2007-07-02
i used to have my ubuntu install on a IDE hdd.........this was done when i was trying to get started with linux, and wasnt sure about getting rid of my windows install, which was on a separate raid-0. everything worked ok (except for a few issues with palm, which now i live with, but thats another story)

i decided to format the raid-0, and install ubuntu 7.04 there. i followed this guide: 
[http://ubuntuforums.org/showthread.php?t=464758](http://ubuntuforums.org/showthread.php?t=464758)

gnome seems unresponsive. so does  xfce...so it appears to be something related to xorg...am i right?

ive got feisty fawn, up to date. no additional package from any external repo, except for pidgin and thunderbird2.

the relevant excerpt from xorg.conf is

```

Section "Device"
        Identifier      "ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"
        Driver          "fglrx"
        Option          "GARTSize"      "64"
#       Option          "EnablePageFlip"        "True"
#       Option          "AccelMethod" "EXA"
        Option          "VideoOverlay" "on"
#       Option          "OpenGLOverlay" "off"
        BusID           "PCI:5:0:0"

```

the commented out sections, have been tried and untried already.

i tested out both the ati open source drivers, and fglrx drivers. same problem. 

with both drivers i had direct rendering enabled. i even used compiz with the open source drivers.

the AccelMethod line, was tried both with EXA and XAA, same problem...

ive already replaced sticks of ram just in case

i have also tried the fix proposed here: [https://launchpad.net/xorg-server/+bug/88815](https://launchpad.net/xorg-server/+bug/88815) but it shouldnt apply since packages have been updated already.....

am i missing anything? i even moved the swap partition to a different drive, thinking it would affect. but nothing happened....

my hardware:
amd athlon64 3000+ socket939
2gb DDR400 (4x512)
2x80gb SATA 8mb 7200 raid-0
dfi lanparty ut nf4 sli-dr
ati raedon x600 128mb

---

### Post by eldragon on 2007-07-03
one thing i found, that might have solved el problema:

my last kernel update was 2.6.20-16-generic but it didnt update the menu.lst for grub.

so, i was actually running 2.6.20-15-generic. i modified menu.lst to include the new kernel, and things seem to be snappy again....just for now....lets hope it lasts.....


EDIT
not much changed....im still having the same performance issues, after 1 hour of usage, everything seems quite sluggish. windows take seconds to redraw... CTRL-ALT-BACKSPACE fixes it for another hour....

im driving nutts....dont know what else to do... can anyone here help please?
EOEDIT

---

### Post by xen on 2007-07-04
I'm having similar problems with my nVidia card, these links seem relevant for you:

[https://bugs.launchpad.net/ubuntu/+source/libx11/+bug/88815](https://bugs.launchpad.net/ubuntu/+source/libx11/+bug/88815)
[https://bugs.launchpad.net/ubuntu/+source/libx11/+bug/88815](https://bugs.launchpad.net/ubuntu/+source/libx11/+bug/88815)

---

### Post by eldragon on 2007-07-04
finally someone replying...too bad ive already visited that link......


ive been trying more stuff...to see whats the problem.

using ati open source drivers + compiz (desktop effects through preferences enables) seems to help a lot. but instead of suffering performance degrading. everything grinds to a halt after 24hs.

ive replaced metacity with xfwm4 using this guide: [http://ubuntuforums.org/showthread.php?t=88393](http://ubuntuforums.org/showthread.php?t=88393)

and it didnt work either..........

agghhhhh what...ohhh what should i do? install vista? :evil: 

cheers

---

### Post by eldragon on 2007-07-05
im bumping again:

there's definately something wrong here........i WANT to use gnome, i like it, its simple, it just works (used to)...but i cant.

ive formated, reinstalled. and right after updates......performance starts degrading again.

now ive installed kde. a couple of hours and still no degrade here.......

its so odd. its killing me. 




kde is so ugly.

EDIT
ok, its definately a gnome/xfce thing. what they got in common. i wouldnt know. but its not metacity or xfwm4......since im running kde WITH metacity..and its blazing fast...

what could possibly be hitting my performance? isnt anywhere else i can ask? considering the lack of help ive attained so far....

---

### Post by xen on 2007-07-06
Yeah its a very annoying problem, I don't know where else to look for help however. When I check the performance monitor, the slowdown seem to be caused by Xorg, however its something particular to GTK/GNOME.

---

### Post by eldragon on 2007-07-06
> **xen said:**
> Yeah its a very annoying problem, I don't know where else to look for help however. When I check the performance monitor, the slowdown seem to be caused by Xorg, however its something particular to GTK/GNOME.

here's another update.

i had remote desktop enabled. this starts the vino server. which, when i killed it. restored performance. even though the cpu was being used by xorg. it appears to be vino's fault.
since last night, ive been running gnome again. with no performance hits...(disabling the vino server). im not sure if this is the cause, but it appears to be working.

i resolved to running x11vnc instead. a bit more troublesome to setup, but nothing the man pages wont fix :)

disable remote desktop and see if it helps..

EDIT
ive posted a bug here: [https://bugs.launchpad.net/ubuntu/+source/vino/+bug/125179](https://bugs.launchpad.net/ubuntu/+source/vino/+bug/125179)

---

