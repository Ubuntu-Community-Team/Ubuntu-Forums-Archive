---
title: "No Sound in dell studio laptop, ubuntu 11.04"
date: 2011-07-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sudeep495 on 2011-07-15
Hi, 
I have dell studio 15 laptop with 11.04 installed. No sound is there whatever I play, whether it is youtube videos or using vlc or others. Any suggestiona,  what is wrong ?  :confused:](*,)](*,)](*,)](*,)](*,)](*,)](*,)

---

### Post by dFlyer on 2011-07-15
Have you tried to turn the volume up? I have a dell studio 1735 and everything just worked out of the box. I did have to turn the volume up though.

---

### Post by sudeep495 on 2011-07-15
Yes have tried that, not working :(

---

### Post by mesidh2k on 2011-08-04
mine also not working with n5010:confused:

---

### Post by cgilbert16 on 2011-08-11
This worked for me: 
 
*sudo vi /etc/modprobe.d/alsa-base.conf*

[FONT=Arial]Go to the bottom and add this line:

[/FONT]*options snd-hda-intel model=dell-m6*

[FONT=Arial]Reboot
Once the system comes up you may have to play with the configurations in System --> Preferences --> Sound


[/FONT]

---

### Post by Maloric on 2011-10-10
> **cgilbert16 said:**
> This worked for me: 
 
*sudo vi /etc/modprobe.d/alsa-base.conf*

[FONT=Arial]Go to the bottom and add this line:

[/FONT]*options snd-hda-intel model=dell-m6*

[FONT=Arial]Reboot
Once the system comes up you may have to play with the configurations in System --> Preferences --> Sound


[/FONT]


Thanks for the pointer - that worked for me after reboot. \\:D/

---

