---
title: "Help: Beryl Keeps Kicking Me Back to Logon"
date: 2007-06-27
forum: Desktop Effects &amp; Customization
---

### Post by apolloxi on 2007-06-27
I just recently installed Ubuntu on the D Drive of my laptop. So, I installed Beryl. When I activated it, it kicked me back to the "Log On" screen, and, every time I entered my name and password, the screen would go black, go back to the "Starting up" looking screen (where it says a bunch of processes on the left and "OK" on the right) for ONE or two seconds, then asks me to log on again. Then, it repeats.

Can anyone help me with this? I'd appreciate it. I installed Ubuntu on my desktop (same hard drive) and I never had a problem with Beryl.

---

### Post by apolloxi on 2007-06-27
Anyone? Please?

---

### Post by bapoumba on 2007-06-27
Hello,

please go to the terminal session before you logon, hit CTRL-ALT-F2, log in, and run:
```
df -H
```
You may be running out of disk space.

If so:
```
sudo aptitude clean
```
will make some room on the root partition. Look also in your /home if you can delete files.

Go back to the graphics session with CTRL-ALT-F7.

---

### Post by apolloxi on 2007-06-27
Tried this. Didn't work. Tried searching solutions but I couldn't find any, either.

I'm just going to reinstall Ubuntu.

Are there any precautions I should take next time to prevent Beryl from screwing up the system (since I'm  certain that activating Beryl caused it, somehow)?

---

### Post by apolloxi on 2007-06-27
Okay. So, I reinstalled Ubuntu, and I tried installing and activating Beryl again.

Thankfully, activating Beryl does not screw up the system; I can still log on after Beryl whacks out. THIS time, though, whenever I activate Beryl, the entire screen whites out, except for the mouse cursor. Ubuntu itself doesn't seem to crash, since I  did a test by putting the cursor over where I thought the Firefox icon would be and activated it. Firefox actually opened: I can see the Firefox logo in the lower right whenever I do the multiple-screen feature (where you can see all the windows you have open at once and can choose which one to go to).

Is there some setting I need to change or fix within Beryl? Any help would be appreciated, again.

---

### Post by kpolice on 2007-06-27
You should give us more info like Ubuntu version, 32 or 64 bit, Beryl version, graphics card and drivers, etc.

---

### Post by tom1g on 2007-06-27
> **apolloxi said:**
> Okay. So, I reinstalled Ubuntu, and I tried installing and activating Beryl again.

Thankfully, activating Beryl does not screw up the system; I can still log on after Beryl whacks out. THIS time, though, whenever I activate Beryl, the entire screen whites out, except for the mouse cursor. Ubuntu itself doesn't seem to crash, since I  did a test by putting the cursor over where I thought the Firefox icon would be and activated it. Firefox actually opened: I can see the Firefox logo in the lower right whenever I do the multiple-screen feature (where you can see all the windows you have open at once and can choose which one to go to).

Is there some setting I need to change or fix within Beryl? Any help would be appreciated, again.

This also happened to me, white screen,  whenever i enabled Desktop Effects. I fixed it by installing restricted driver

---

### Post by apolloxi on 2007-06-27
Sorry for the lack of info.

Ubuntu 7.04 (Feisty Fawn). Graphics card: SiS M760GX integrated 3D graphics. 64-bit. Beryl 0.2.1.

---

### Post by apolloxi on 2007-06-27
> **tom1g said:**
> This also happened to me, white screen,  whenever i enabled Desktop Effects. I fixed it by installing restricted driver

Already have it installed. Tried to open it by going to System>Admin>Restricted Drivers Manager, but it says "Your hardware does not need restricted drivers."

Never once tried to enable desktop effects.

---

### Post by apolloxi on 2007-06-27
Does anyone have any other suggestions? I was unable to find a solution to this on my own.

---

