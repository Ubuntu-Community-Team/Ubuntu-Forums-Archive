---
title: "My Enemy-Territory Sound is jammed! not the usual sound problem!"
date: 2005-05-01
forum: Gaming &amp; Leisure
---

### Post by Sc0rp3 on 2005-05-01
Hi.

I played yesterday, and i did the cmd:
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss

and it worked.
But now it says:

versatec@versatec:~$ echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
bash: /proc/asound/card0/pcm0p/oss: No access


Someone witht he same problem that can help me? \\:D/ 
Or someone smart?

---

### Post by T. G. Cid on 2005-05-01
You must be root.

Doesn't work:
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

Also doesn't work:
sudo echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

Does work:
sudo su
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

Also works:
su
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

As a side note, I never needed to use the disable line.

In addition, you may also need the command:

(sudo *should* work here)
sudo killall esd

---

### Post by nautilus on 2005-05-02
disabling capture does exactly that.

enemy territory doesn't have a recording facility, so you don't need to allow it to capture.

this is also useful when playing through an out-only device, such as /dev/adsp, which has no capturing facility.

i do this so that i can use teamspeak at the same time as playing et, which uses both channels.

---

