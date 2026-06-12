---
title: "Slight Graphical Glitches in Unity"
date: 2012-02-27
forum: Desktop Environments
---

### Post by Kyomaru on 2012-02-27
Hello. I have been running ubuntu 11.10 for a while now. Every so often, i get some graphical glitches like this:

[IMG]http://ubuntuone.com/2JX74WMiNTINm9T1wQiHdd[/IMG]

now, sometimes its just the tooltips, sometimes its part of the dash. other times its the whole desktop background. i wanted to know, is this truly a glitch, or is it refresh rate, because i've seen that on the internet, and figured this could also be a problem. if anyone could help, that would really please me. i really enjoy using unity, and i want it to be as nice as possible.

so far i've only been able to fix the problems by logging out and logging back in. if there is another way i can do it, that would help also. 

thanks. ~Kyo

---

### Post by typhoon_tip on 2012-02-27
What is your video card and what video driver you are using ?

---

### Post by hildenbrandsteven on 2012-02-27
Have you done all the system updates?

---

### Post by Kyomaru on 2012-02-27
Yes, i have been keeping up with software updates :D

as for the graphics card, i took this screenshot:

[IMG]http://ubuntuone.com/1eEENwk7i9GmPgUvF11tgz[/IMG]

its never asked for additional drivers, so i assume its using the correct ones. How would i find the current driver im using?

---

### Post by typhoon_tip on 2012-02-27
> **Kyomaru said:**
> Yes, i have been keeping up with software updates :D

as for the graphics card, i took this screenshot:

[IMG]http://ubuntuone.com/1eEENwk7i9GmPgUvF11tgz[/IMG]

its never asked for additional drivers, so i assume its using the correct ones. How would i find the current driver im using?

Well there isn't, only the open source driver. What is your screen resolution ?

---

### Post by Kyomaru on 2012-02-27
1440 * 900

---

### Post by typhoon_tip on 2012-02-27
Have you adjusted your font appearance in any way, or reduced the size of the icons in the panel ?

---

### Post by Kyomaru on 2012-02-28
to my knowledge, i have not. It's always done this to me, even on a fresh install.

---

### Post by Kyomaru on 2012-03-12
bump

---

### Post by bobzxr on 2012-03-13
I have the same problem with graphical glitches appearing from time to time. Sometimes I can work for 5 minutes, sometimes its good for hours without glitches.

I did not notice anything particular what could trigger this problem.

After logging out and back again its fine again.

I have an ATI video card, and I did not install any additional drivers, using the built in. Everything is up to date, w/ Ubu 11.10.

---

### Post by typhoon_tip on 2012-03-14
> **bobzxr said:**
> I have the same problem with graphical glitches appearing from time to time. Sometimes I can work for 5 minutes, sometimes its good for hours without glitches.

I did not notice anything particular what could trigger this problem.

After logging out and back again its fine again.

I have an ATI video card, and I did not install any additional drivers, using the built in. Everything is up to date, w/ Ubu 11.10.

Using FGLRX (Proprietary Drivers) or open source ones ?

---

### Post by bobzxr on 2012-03-14
> **typhoon_tip said:**
> Using FGLRX (Proprietary Drivers) or open source ones ?

System info shows that driver is: Gallium 0.4 on AMD CAYMAN.
Installed packages I found in Synaptic package manager which may apply here:

xserver-xorg-video-radeon,
xserver-xorg-video-ati
xserver-xorg-video-mach64
xserver-xorg-video-r128.

These came with the OS itself.

Update: in the additional drivers applictaion, the FGLRX drivers are NOT activated.

Oh and using x64 version of OS.

---

### Post by typhoon_tip on 2012-03-14
> **bobzxr said:**
> System info shows that driver is: Gallium 0.4 on AMD CAYMAN.
Installed packages I found in Synaptic package manager which may apply here:

xserver-xorg-video-radeon,
xserver-xorg-video-ati
xserver-xorg-video-mach64
xserver-xorg-video-r128.

These came with the OS itself.

Update: in the additional drivers applictaion, the FGLRX drivers are NOT activated.

Oh and using x64 version of OS.

Try to activate FGLRX and see if the glitch goes away.

**Important note**: if you are not confident of being able to bring back an eventual dead X from command line, do not do this.

---

