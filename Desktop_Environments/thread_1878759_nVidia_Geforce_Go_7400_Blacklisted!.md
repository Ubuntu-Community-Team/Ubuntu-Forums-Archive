---
title: "nVidia Geforce Go 7400 Blacklisted!"
date: 2011-11-10
forum: Desktop Environments
---

### Post by HDave on 2011-11-10
After running compiz for years, I am now unable to run Unity 3d in 11.10. Why? Ubuntu has blacklisted my graphics card!

They did this because the latest (280.13) nVidia driver causes it to freeze upon login. Running a x86 Dell M1210 laptop here.  Running the v273 driver works, but is so slow and buggy it is unusable.

Check it out:

[http://askubuntu.com/questions/64682...eforce-go-7400](http://askubuntu.com/questions/64682...eforce-go-7400)

Other nvidia cards have been blacklisted as well. Any idea when we'll see a newer working driver?   Is there a way to manually install a new version of the driver?

I noticed on the nVidia website they are up to 285.05:

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

---

### Post by 3Miro on 2011-11-10
I am not sure whether the blacklisting is due to a buggy driver or simply Unity using newer effects that are unsupported by the hardware.

Assuming it is the driver, you can try to install a newer driver, however, you should be careful. If you download the driver straight from Nvidia, it is quite likely that the next kernel update would just break it. Your best bet is to look for an unofficial Nvidia ppa. Naturally this would only work if Nvidia has actually fixed the issue, I remember when KDE 4.0 came out, there was a bug in the Nvidia driver that was killing the KDE performance and Nvidia sure took their time fixing it.

---

### Post by HDave on 2011-11-10
Good advice...after considerable searching I found the PPA:

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

Going to try the new version now...

---

### Post by HDave on 2011-11-10
The xorg-edgers took me nvidia driver to 290, but the problem is still there.  Guess I'm waiting for nvidia at this point :-(

---

### Post by 3Miro on 2011-11-10
> **HDave said:**
> The xorg-edgers took me nvidia driver to 290, but the problem is still there.  Guess I'm waiting for nvidia at this point :-(

It may not be Nvidia, but the hardware capabilities of the graphics chip. If it doesn't have the instruction set needed to run Unity, then no driver would ever help.

You can try to run Gnome-classic with Compiz, if the problem is with Unity, then you should still have that available. You can install Gnome-classic by installing gnome-session-fallback. Other alternatives are to try Gnome-shell (gnome-shell package). Other than that, only KDE comes with effects, Unity 2D, xfce and lxde come with nice DE, but no visual effects.

---

