---
title: "Problems running Kubuntu 11.10"
date: 2011-10-15
forum: Desktop Environments
---

### Post by fjkraan on 2011-10-15
Hi,

I just wat to report my experiences with installing the new Kubuntu 11.10 version. (X86_32, Nvidia Gforce 8800GT). Previous Kubuntu versions ran without much problems on this configuration.

Installation itself gave no problems, but after reboot, the Xserver failed to start. After some searching on the web (mainly these forums), I found that probably the nvidia-173 module was the problem. I installed nvidia-current too, but the nvidia-173 generated [FONT=Fixedsys]/etc/modprobe.d/nvidia-graphics-drivers.conf[/FONT] had it blacklisted. 
Removing nvidia-173 (sudo apt-get remove nvidia-173 and sudo dpkg-reconfigure nvidia-current) probably solved this problem, as I could succesfully run startX.

But logging in still fails. I prefer an auto login and configured it as such, but I cannot get past the login screen.
Killing Xorg and run startX manually works, but this is not optimal.

---

### Post by ig4cr4ck on 2011-10-16
I have the same problem. Any solution?

---

### Post by elnur on 2011-10-18
I think I'm having a similar problem. If I enable NVIDIA X driver using nvidia-xconfig, my system won't start.

---

### Post by cloudslayer on 2011-10-18
I also think I have a similar problem, although the X server did start.

For me, the solution was to disable compositing, as that seemed to trigger the return to login screen...

This can be changed using the ~/.kde/share/config/kwinrc file and setting Enabled=false for [Compositing]

Off course, that means bye bye nice effects...

---

### Post by elnur on 2011-10-18
I tried lots of things, but all of them can be boiled down to this:
```
sudo aptitude reinstall nvidia-current
```

It helped me. NVIDIA X driver is now enabled on my system.

---

### Post by cavedweller on 2011-12-03
I started off last night installing kubuntu 11.10 on the system we have hooked up to a Visio flat panel TV to stream off the web to avoid a cable bill. P4 3GB, 1 gig sdram, nvidia 5200fx. Could not get it to let me change the resolution to 1224 x 768 which is max for the TV. So I downloaded Mint 12. I fought it most of the day. Installed current, upgraded it to 173, removed 173 and reinstalled current. Basically ended up with Mint 12 running a version of Gnome 2 with no acceleration. So re installing kubuntu, going to put nvidia-current on it and bump it up to KDE4.73. It should be good enough for a tv.

---

### Post by cavedweller on 2011-12-03
There is enough video issues with the distros based on Ubuntu 11.10 and I don't have the time or the desire to fight with them to watch tv online. So I installed Mint 10 on the tv computer and all is good. My laptop runs 11.10 with all the updates and some bleeding stuff fine. I might try to install Mint 12 tomorrow and see if it works ok. Running Kubuntu 11.10 Kde 4.73.

---

### Post by kuckunniwi on 2012-03-11
> **elnur said:**
> I tried lots of things, but all of them can be boiled down to this:
```
sudo aptitude reinstall nvidia-current
```

It helped me. NVIDIA X driver is now enabled on my system.

Same problem here! Will give it a shot and hope it works!

---

