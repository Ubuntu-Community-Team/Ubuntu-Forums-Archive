---
title: "Volume control does not work in kubuntu 12.04"
date: 2012-05-01
forum: Desktop Environments
---

### Post by Pally1 on 2012-05-01
Sound works fine, but volume control on the keyboard, and volume control in the taskbar lower right have no effect. 

Is there any way i can fix this?

---

### Post by Pally1 on 2012-05-02
bump


Does anyone have any solutions?

---

### Post by MrsUser on 2012-05-02
Is it a fresh install? I'm a newbie myself and I tried Kubuntu before. One of the things I did at the start was that I mixed up the WiFi icon with the volume control icon. Maybe this is the case here as well? 

As for the keyboard, I don't know. It depends on the hardware, I guess. But maybe some experienced user is out there to assist you in that.

---

### Post by Pally1 on 2012-05-02
Yap, fresh install, works with gnome, than formatted and reinstalled with kde and volume control does not work.

---

### Post by PaulW2U on 2012-05-02
Have you looked in System Settings | Input devices | Keyboard | Keyboard model?

What do you currently have selected? There's a lot of keyboard models that have "multimedia" in their name. Maybe one of those will work if you can't find an exact match.

---

### Post by Pally1 on 2012-05-03
what im trying to say is that system does react to volume control buttons, i get the animation and everything, but while animation is moving, sound volume has no effected. Same thing when i try to change volume with volume control in the bottom right corner where you have that speaker icon that pops out the slider. I move the volume up and down but it has no effect.

---

### Post by samigina on 2012-05-03
Sounds like you have Kmix using the wrong output, in my setup, Kmix put the HDMI output like default (It should be the Analog one), so I was getting a similar issue.

Right click on the volume icon, then, Select Master Chanels and choose the right one.

---

### Post by Pally1 on 2012-05-03
> **samigina said:**
> Sounds like you have Kmix using the wrong output, in my setup, Kmix put the HDMI output like default (It should be the Analog one), so I was getting a similar issue.

Right click on the volume icon, then, Select Master Chanels and choose the right one.


Thanks a lot m8! spent so much time on this and solution was just that simple :D

---

### Post by samigina on 2012-05-03
Great!

Dont forget to mark the post "Solved"

---

### Post by Duplin on 2012-08-18
Had the same problem, worked for me as well. Thank you.

---

### Post by hydrospheric on 2012-09-15
Had the same problem under Ubuntu 12.04 gnome - so not kmix.

Applications > System Tools > System Settings > Sound

Under the hardware tab select profile at the bottom and select Digital Stereo

---

### Post by sleepee on 2012-09-17
thanks a lot!  i had the same problem under the cinnamon DE and this solution worked for me too!

---

### Post by rybnik on 2012-09-17
btw, another fix is to install Pulseaudio Volume Control, which is greatly adjustable.

---

### Post by Pankke on 2012-12-29
Thanks for the help guys

---

