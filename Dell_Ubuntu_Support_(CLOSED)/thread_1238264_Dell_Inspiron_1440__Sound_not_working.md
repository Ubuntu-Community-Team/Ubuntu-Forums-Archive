---
title: "Dell Inspiron 1440 : Sound not working"
date: 2009-08-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by johnjoy on 2009-08-12
Hi,
I've already read the post by alu_card, and tried it too, but with no avail. I have Dell Inspiron 1440 (with Vista as alternative OS) and Jaunty. Only integrated graphics card. I don't get any sound, though video plays fine. Even in login, I don't get any sound. I did some fiddling with preferences, and though it did'nt work at that time, in the next reboot, sound started working. But subsequent reboots (no further fiddling), no sound.
Can anyone please help me? If you want some info on my system, please tell me the command, as I am new to Ubuntu (trying it out).
Any help will be deeply  appreciated, and thanked.

Thanks in advance.
John Joy
Very new to Ubuntu, and anxious not to get disappointed

---

### Post by johnjoy on 2009-08-13
Don't know, but I am a happy man today. I switched on the lappy, and lo and behold, sound started working perfectly. I've set all sound preferences to pulseaudio. But even when I keep the master volume at mute, I can hear sound.
I think this is a bug. Please help me fix it.

---

### Post by johnjoy on 2009-08-13
I restarted my system to see what happens : as expected, no sound. I think someone else had posted the same problem-system has multiple sound drivers, and Jaunty selects one and runs at startup. Is there a permanent fix to this??

---

### Post by garysbasem3nt on 2009-09-24
Did you ever find a solution for this? I'm also facing the same issue - except I'm using the Ubuntu Mint distro - [http://forums.linuxmint.com/viewtopic.php?f=90&t=33312&p=192677#p192677](http://forums.linuxmint.com/viewtopic.php?f=90&t=33312&p=192677#p192677)

My headphones work - but no speaker sound :[

---

### Post by johnjoy on 2009-09-25
No, I couldn't find a solution, though I tried a lot. I thought the Ubuntu community is a very helpful one, but they seem to be stumped on this one. I can't live without sound, so I am starting to quit using Ubuntu. 
Though silly, it is a grave error. Wonder what the developers thought, to make Ubuntu incompatable with Dell systems?? Absurd

---

### Post by garysbasem3nt on 2009-09-28
Sorry for the delayed response - Have you had any luck with other Linux distros in getting sound? I have Windows VIsta on another partition - which I'll be upgrading to Windows 7... But I'd like to keep a separate partition for a Linux OS. It'd be a shame if no distros worked with sound :(

---

### Post by johnjoy on 2009-09-28
I have tried 8.10 also. But no sound. Don't know about the previous distros. But if the newest one is bad, then the older ones can't be better can they?
Where are the pros? Can't no one offer any solid solution to this problem??

---

### Post by dansanti on 2009-09-30
try open on a terminal alsamixer, and there up all sound level, if on master sayd MM(mute) in bar foot, press m, an then this switch to 00(unmute)

---

### Post by astrakhan on 2009-09-30
use alsamixer instead of gnome-volume-control.
for reference, here's what mine looks like.

[ATTACH]130269[/ATTACH]

[ATTACH]130270[/ATTACH]

also check out sound preferences:

[ATTACH]130271[/ATTACH]

this is an inspiron 1525 running jaunty - sound is working just fine.

---

### Post by bigbull13 on 2009-10-02
I'm having the same issues.  I have tried everything on this page as well as a bunch of other things that i've found but nothing is working.

---

### Post by johnjoy on 2009-10-03
Though not consistently working, sound now works 90% of the time when I boot up. I had followed some previous stupid advises and updated my alsa mixer. So I reinstalled linux, and opened alsamixer in terminal. As advised, the master was MM, I un-muted it, and now sound started working. But I am still not satisfied, as there is that 10% not working...

---

