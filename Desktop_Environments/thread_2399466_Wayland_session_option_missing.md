---
title: "Wayland session option missing"
date: 2018-08-25
forum: Desktop Environments
---

### Post by goatboy73 on 2018-08-25
Hi!!


I've just noticed that I'm still running in X11 even though I thought this version of Ubuntu (18.04 LTS) would use Wayland by default.  It's an in-place upgrade so I guess I shouldn't be surprised that it continued to run as the old(er) installation (17.10) did (which was itself an in-place upgrade).  That said, I'm not given the session option to run "GNOME on Wayland".


My only available session options are:



[LIST]
[*]GNOME on Xorg
[*]GNOME Flashback (Metacity)
[*]Ubuntu
[/LIST]


All 3 launch Xorg.  My computer has an nVidia 1080 TI card, with the nVidia drivers loaded (from the Graphics Drivers Team PPA). It's also running in UEFI secure mode. All the wayland stuff seems to be installed properly.

Any ideas on where I can start debugging this?

Thanks!

---

### Post by #&amp;thj^% on 2018-08-25
I think this is correct. Nvidia disables KMS support by default, which means no wayland support.
Wayland and Nvidia are still very  much a work in progress 
Also have a look at this discussion: [https://www.reddit.com/r/linuxquestions/comments/8q1ko0/why_cant_existing_nvidia_drivers_be_used_with/](https://www.reddit.com/r/linuxquestions/comments/8q1ko0/why_cant_existing_nvidia_drivers_be_used_with/)

---

