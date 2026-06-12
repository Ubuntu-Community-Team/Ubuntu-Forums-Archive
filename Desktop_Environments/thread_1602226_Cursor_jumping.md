---
title: "Cursor jumping"
date: 2010-10-21
forum: Desktop Environments
---

### Post by johnsd on 2010-10-21
Hi

I have just purchased a Eee 1001PX and have installed Ubuntu 10.4 Netbook edition on it. All is well except took it to my first meeting tonight to take the minutes - very frustrating since every now and again the cursor jumps to a different part of the text while I am typing (using OpenOffice). Particularly annoying when trying to type what people are saying and getting lost!!

When I got home I booted into XP and in OO the same thing happened although probably not as often.

I figure after fiddling that it appears to be when I drag my thumb over the mouse pad when hitting the space bar. When I checked, the setting for disabling the mousepad while typing is turned on (which tends to indicate that this should not be happening).

Anyone else had this issue - might just be training myself not to touch the mouse pad when typing??

---

### Post by P4man on 2010-10-21
Install "pointing devices" from the software center, then go system > preferences pointing devices. It gives you more control over your touchpad. Experiment with palm detection. 

If that doesnt help enough, open a terminal and copy paste this line:

```
xinput --list-props "SynPS/2 Synaptics TouchPad"
```

If you have a synaptics touchpad, it will list all its settings. If it does, you can tweak them and see what works best for you. For instance

```
xinput set-int-prop "SynPS/2 Synaptics TouchPad" "Synaptics Jumpy Cursor Threshold" 32 **110**

```

Play with the 110 value.

---

### Post by johnsd on 2010-10-22
Many thanks for that - the palm settings did the job. I was unaware of this piece of software since my retired laptop was a Thinkpad with no finger pad. It is a wonder that this is not installed by default since the distro is for netbooks.

---

