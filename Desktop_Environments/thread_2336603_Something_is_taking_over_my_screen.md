---
title: "Something is taking over my screen"
date: 2016-09-09
forum: Desktop Environments
---

### Post by mfs-h on 2016-09-09
Hi Folks,

I've been trying to debug this for weeks and no results so I'm trying here. :)

Running xubuntu 14.04.5 (yes, I know there is a new version, but haven't upgraded yet).  At seemingly random times, my screen "locks" as if xscreensaver had kicked in.  The screen is replaced with an image (seemly random image on my machine) and it looks like glsideshow is doing it.  I even seen an error message from glslideshow in the corner  But, neither xscreensaver nor glsideshow is running.  I assuming this is something wrong with xfce but I have not been able to detect any errors in logs etc.  If I just click around on the desktop the image "pieces" go away.

Any suggestions on how to fix this?  It's been driving me crazy as it comes up fairly often and always when I am in the middle of something.  

Thanks.

---

### Post by TheFu on 2016-09-09
Is your system clock properly maintained or does it jump around?  In short, is ntp configured and running properly?

---

### Post by mfs-h on 2016-09-09
Thanks for the quick reply TheFu.

I have not been running ntp but I have not noticed anything strange with the various clocks I have running (I always have Orage Global time running as I work with people in many time zones and like to keep track, etc).  But I'll set it up right now and see if that has any effect.

---

### Post by mfs-h on 2016-09-09
Setup ntp but the problem happened again about 10 minutes later. :(

---

### Post by TheFu on 2016-09-09
> **mfs-h said:**
> Setup ntp but the problem happened again about 10 minutes later. :(

Sorry. It was a shot in the dark.  Time jumps cause screen-savers to activate.

---

### Post by Habitual on 2016-09-10
> **mfs-h said:**
> If I just click around on the desktop the image "pieces" go away.
Ghost-like objects "sorta there" and gone after stimulating the screen somewhat....?
Typically referred to as "artifacts" and indicate you maybe should consider switching drivers, IMO. Wait for additional input.
What's the video situation? Card/Driver/Version?

---

### Post by mfs-h on 2016-09-10
> **Habitual said:**
> Ghost-like objects "sorta there" and gone after stimulating the screen somewhat....?
Typically referred to as "artifacts" and indicate you maybe should consider switching drivers, IMO. Wait for additional input.
What's the video situation? Card/Driver/Version?

I have not heard the term "artifacts", but sounds like what I am experiencing.  Video info:

04:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV620 LE [Radeon HD 3450] [1002:95c5]

It's a pretty old system. :)  I should be running the correct driver but I will explore that and confirm.  The wrong driver does make sense as a cause.

Thanks!

---

### Post by coldraven on 2016-09-11
AFAIR there is a Xubuntu utility called Lightlocker. make sure that it is disabled.

---

