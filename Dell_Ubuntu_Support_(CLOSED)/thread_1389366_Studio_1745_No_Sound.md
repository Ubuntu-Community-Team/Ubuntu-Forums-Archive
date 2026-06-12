---
title: "Studio 1745 No Sound"
date: 2010-01-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by thephant0m on 2010-01-24
Hello all
I have installed Ubuntu 32-bit 9.10 on my new DELL Studio 1745. There is no sound from the 'Internal Audio' device, which is what I assume I should be using for sound via the laptop speakers/headphone.

I also have another device listed 'R700 Audio Device [Radeon HD 4000 Series], which I am assuming is for sound via the HDMI port. I do not have the opportunity to test this at the moment.

I have hearing no sound from the laptop speakers, which is what I'd like to resolve. I have seen another post in this forum related to installing the alsa-base package, I have already checked that this is installed and it is the latest version.

Can anyone help me? Please let me know what additional information/output I need to provide - any help would be greatly appreciated.

Many thanks.

---

### Post by thephant0m on 2010-01-25
I have managed to fix this issue. For all those still experiencing this problem, or who may run into it in the future, the fix is to modify /etc/modprobe.d/alsa-base.conf. There are some posts on other forums relating to this, however the majority of them simply suggest appending the following line to this file:

```
options snd-hda-intel model=dell-m6
```For my setup (Dell Studio 1745) I had to remove all contents in alsa-base.conf and include ONLY the above line. Simply adding to this file did not resolve the issue.

I suggest moving alsa-base.conf out of the way and creating a new one with the above line as the only contents, then reboot. Following the reboot sound should function correctly. This also works on Fedora Core 12, which had the same issue. I actually fixed it on that distro first, but it's so hideously slow and ugly in comparison to Ubuntu, I re-installed 9.10 and applied the same fix there.

---

