---
title: "Gnome mouse driver/KVM switch issue"
date: 2006-02-12
forum: Desktop Environments
---

### Post by charman on 2006-02-12
I installed Ubutu v5.10 last night, then installed all the updates I was prompted to install. The problem emerged after I toggled to another machine with my Belkin OmniView SE 4-port KVM switch (model F1D104). The mouse driver had been corrupted and when I tried using the mouse, it would jump all over the screen and randomly click things in the process. After a forced reboot, the problem repeated after toggling around on the KVM.

Is this a known issue with this KVM switch or do I have some other problem with my installation?

Charles

---

### Post by racecat on 2006-02-12
Sorry, I don't know the answer to this. I am a KVM user, also, and haven't had any mouse problems. I can tell you, though, that you should keep your KVM switched to the Ubuntu system during bootup or it won't see your monitor and, unless it's different in Breezy, you will only have the option of 640X480 resolution.

Luck,
Bill

---

### Post by charman on 2006-02-12
I've observed the video drivers issue when booting a machine while switched to another machine before, that wasn't the scenario here. This was boot up, log in, do some stuff, switch around and behold the mess, in that order. Only 640x480 you say? I can probably deal with that for a short while, long enough to see if it will fix the mouse driver issue anyway. I'll do some checking, thank you for the idea.

---

### Post by jacrider on 2006-02-16
I experienced the same problems:  640 x 480 resolution and poor mouse performance.  As an earlier post suggested, I rebooted with the Ubuntu machine selected on the KVM switch and everything (mouse included) now works perfectly.

Thanks.

This forum is the best resource ubuntu has.

---

