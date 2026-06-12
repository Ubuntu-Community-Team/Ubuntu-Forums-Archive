---
title: "Where can I get a working Debian CD?"
date: 2008-06-25
forum: Debian
---

### Post by Jammy4041 on 2008-06-25
I have an iMac G3, (Indigo, slot loading, CD ROM drive) that I wish to put Debian on it, ideally Debian XFCE.

I have tried and tried to find a working Debian CD for my iMac G3, but with no luck. 

When I tried the normal, stable release, I could partition my drive but it came up with a whole host of errors. My Firmware is updated to the most recent version. I have since wiped the hard drive.

Then I tried the Xubuntu CD- this was better but still no luck. 

And yesterday I tried it- it was a CD I burned a 10x (Sadly, it was the lowest I could go in Infra-recorder) It was Debian Testing, and in XFCE. That seemed to worked, until it came to installing Yaboot, where it utterly failed. 

I'll try burning another CD in Brasareo to see if that will work.

---

### Post by kerry_s on 2008-06-25
try the net installer, install the base and apt-get xfce4 after the base install. try and burn at 4x for the best results.
[http://cdimage.debian.org/debian-cd/4.0_r3/powerpc/iso-cd/debian-40r3-powerpc-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r3/powerpc/iso-cd/debian-40r3-powerpc-businesscard.iso)

---

### Post by Jammy4041 on 2008-06-26
OK Kerry_S- I've used the Debian XFCE Lenny beta CD and I managed to get it to go smootly. I then did an apt-get install xfce 4 where it asked me for my cd. 

I've got xfce 4 installed, but I cannot boot into a GUI.

---

### Post by benuski on 2008-06-26
> **Jammy4041 said:**
> OK Kerry_S- I've used the Debian XFCE Lenny beta CD and I managed to get it to go smootly. I then did an apt-get install xfce 4 where it asked me for my cd. 

I've got xfce 4 installed, but I cannot boot into a GUI.

If its asking for a cd when you do an apt-get install, that means you have a CD line in your /etc/apt/sources.list.  You should probably remove that and only have internet sources on there.

Do you have a display manager installed?  Something like gdm?

---

