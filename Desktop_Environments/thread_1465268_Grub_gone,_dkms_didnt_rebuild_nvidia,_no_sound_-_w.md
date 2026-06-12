---
title: "Grub gone, dkms didnt rebuild nvidia, no sound - what's happening?"
date: 2010-04-29
forum: Desktop Environments
---

### Post by ghetto2ivy on 2010-04-29
This week my machine has gone haywire. I run 64bit 9.10 and have been doing so just fine from the start. Then about a week ago things started to wrong after some regular ubuntu updates (I haven't installed anything new...)

[LIST]
[*]Sound -- first thing to have issues. Basically I have no sound unless its a very loud part of a movie, and then its distorted,
[*]Grub -- I run a Raid-1 array for my main data. After today's update Grub disappeared from the main first disk int he array (It says not bootable), I now have to boot to the second.
[*]NVIDIA/ DKMS -- I run Dkms so that the nvidia driver and others will rebuild after a kernel update. Well after today's update it didn't. On reboot, gdm failed to load and I had to drop into a shell and rebuild myself.
[/LIST]

The last one is not a big deal for a techie such as myself but I'd hate to subject someone else to that if its not needed..

I still need to repair the GRUB install (any help for doing htat on the raid 1 disk is appreciated).

I also still do not have sound. (HDA Intel Chip).

---

### Post by ghetto2ivy on 2010-05-02
Progress so far:
[LIST]
[*]Nvidia driver reinstalled
[*]Grub Bootsector copied from cloned drive of the raid array to primary using dd
[/LIST]

The sound problem continues. Reinstalled pulseaudio, didn't help. No one else had these odd issues?

---

