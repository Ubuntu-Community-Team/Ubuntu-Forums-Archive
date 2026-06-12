---
title: "sound problems after upgrade of my dapper install?"
date: 2006-07-15
forum: Desktop Environments
---

### Post by kazuya on 2006-07-15
oris@oris-desktop:~$ sudo alsamixer
Password:

alsamixer: function snd_ctl_open failed for default: No such device
oris@oris-desktop:~$

oris@oris-desktop:~$ kmix
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
oris@oris-desktop:~$

I see video file playing, but it does not play any sounds.

How do I restore the initial sound setup prior to upgrade and install of kubuntu and xubuntu, and automatix?

---

### Post by Othersider on 2006-07-16
I have the same problem.  I've looked through these forums, but no suggestions about sound + dapper upgrade seem to work.

> 
$ sudo alsamixer
Password:

alsamixer: function snd_ctl_open failed for default: No such device


---

### Post by kazuya on 2006-07-17
I seemed to have sound working again. I do not know how the fix happened. I installed gamix, alsatools, alsa_oss, and all oss and alsa related stuff. I tried launchingthem all. gamix, I also installed alsamixergui., etc. Eventually upon rebooting, the sound issue was fixed. I also had to raise the volume up on my players.

---

