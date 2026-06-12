---
title: "no sound from internal speakers on inspiron mini 1018"
date: 2011-02-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ilanesh on 2011-02-03
I got a new dell inspiron mini 1018 a week ago, I searched this forum and googled but not found a solution for my problem, there are similar others but with different netbooks. 
No sound at all from internal speakers, with ubuntu 9.10 installed, I tried from usb ubuntu 10.04, but also the same problem, no sound, the microphone works, and I can hear sound only through usb soundcard with the headset connected. I don`t no what to do? If someone has the same Dell netbook and has sound working, I would appriciate it if the person could help me to fix it, even through remote help, cause I try now the whole week to find out why no sound.
Nothing is muted, all is configured right. I just don`t want to sit here always with a headset connected only for sound. Please help.

---

### Post by mörgæs on 2011-02-03
So does this mean that you have not tried 10.10?

---

### Post by Ptero-4 on 2011-02-03
> **ilanesh said:**
> I got a new dell inspiron mini 1018 a week ago, I searched this forum and googled but not found a solution for my problem, there are similar others but with different netbooks. 
No sound at all from internal speakers, with ubuntu 9.10 installed, I tried from usb ubuntu 10.04, but also the same problem, no sound, the microphone works, and I can hear sound only through usb soundcard with the headset connected. I don`t no what to do? If someone has the same Dell netbook and has sound working, I would appriciate it if the person could help me to fix it, even through remote help, cause I try now the whole week to find out why no sound.
Nothing is muted, all is configured right. I just don`t want to sit here always with a headset connected only for sound. Please help.

Can you type:
```

lspci -v

```
in a terminal window and paste the output here (put it in "CODE" tags by using the "#" button in the reply box. That way it is more readable).
Note that you'll need to unplug your headset before doing this step.

---

### Post by ilanesh on 2011-02-04
Problem solved, I have installed Jolicloud, it works out of the box, exellent sound and video and wirless internet, everything works, and can do everything I can do also on a full desktop, no configuration no nothing recired, I am so glad I have this now installed. Ubuntu team should do the same thing what the jolicloud people doing, to include all the drivers for dell netbooks, so there would not be any problems.
As to Ubuntu 10.10, all of the new buntus it is impossible to install on any of my netbooks, I had also acer one, it would refuse to install to the harddrive,. The only ubuntu I an install everywhere without problem is the ubuntu 9.10. And it is good.
But aniways, am happy with the Jolicloud now and it is exatly made for netbookes.

---

