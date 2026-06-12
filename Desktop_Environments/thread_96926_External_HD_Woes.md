---
title: "External HD Woes"
date: 2005-11-29
forum: Desktop Environments
---

### Post by Sly_R on 2005-11-29
When I flip on the power for my external HD, sometimes both of its partitions (one NTFS, one ext2) show on the desktop, sometimes only one or the other.  A power cycle usually remedies the problem, but how can I avoid this to begin with?

---

### Post by dcstar on 2005-11-29
[QUOTE=Sly_R]When I flip on the power for my external HD, sometimes both of its partitions (one NTFS, one ext2) show on the desktop, sometimes only one or the other.  A power cycle usually remedies the problem, but how can I avoid this to begin with?[/QUOTE]
Do you want it to show up when you power it up or not??

---

### Post by Sly_R on 2005-11-30
I want both partitions to show up.

---

### Post by tomwell on 2005-11-30
Have you mounted both partitions so that they are mounted on boot-up?? (note you will only be able to read/write to the ext2 NTFS is read only in Ubuntu...)

peace

Tom

---

### Post by Sly_R on 2005-11-30
I usually prefer to have the HD shut off until it's in use, because it's noisy and it heats up; so I just flip it on sometime after Ubuntu is booted.  Like I said, about half the time, both partitions show up.  The other half of the time, only one or the other shows and I have to flip it off and then back on again.

...and thanks for the tip regarding NTFS, by the way.  You answered my next question.

---

### Post by teaker1s on 2005-11-30
power the hd up then plug in usb-thats how I do mine

---

### Post by tomwell on 2005-12-01
[QUOTE=teaker1s]power the hd up then plug in usb-thats how I do mine[/QUOTE]

Has this resolved your problem..?

Oh and No probs for next question...

Peace

Tom

---

### Post by Sly_R on 2005-12-01
Didn't work.  In fact, after disconnecting the USB cable, turning on the HD and reconnecting the cable, neither partition shows up at all.  A quick power cycle, though, and both appeared.

---

### Post by tomwell on 2005-12-01
Sly R,

Is your HD partition ext2 the one you have installed Ubuntu on?? I am 98% sure its not but if it was then you'd be getting some prob from that...LMAO ;o)

I dont use an extrenal HD but it seems you might have to have it powered on at bootup... since both of them appear that way... Does it really heat up noticeably?? in theory it should only when being used?? but as i said i dont own an external HD so not sure...

Peace

Tom

---

### Post by Sly_R on 2005-12-02
No, it's not the partition containing the install.  It's where I backup my files.

Basically, the external HD makes a lot of noise that I'd rather avoid by keeping it off when not in use.

---

### Post by teaker1s on 2005-12-02
maybe its a mount issue, my external harddisk is Vfat and it works beautifully with both xp and ubuntu ie. maybe ubuntu doesn't see both partitions sometimes with automount. could you unmount and manually mount both partitions.
If that works you can set both to mount on boot

---

