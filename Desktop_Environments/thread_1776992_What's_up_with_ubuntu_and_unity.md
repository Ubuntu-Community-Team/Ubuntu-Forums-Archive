---
title: "What's up with ubuntu and unity"
date: 2011-06-07
forum: Desktop Environments
---

### Post by andrea000 on 2011-06-07
I have been away for a while but I'm back and I've upgraded
to ubuntu 11.04 when I log in to the new desktop there's
nothing just one gnome bar at the top and what I think
is the unity launcher on the side but there is no icons on it
like the screen shots I've seen.I also have the nvidia
driver 275.09 installed but it's saying Driver installed but
not active.Can someone tell me what's going on and how to fix
it.I see a lot of post saying the same thing.Thanks

---

### Post by wildmanne39 on 2011-06-07
> **andrea000 said:**
> I have been away for a while but I'm back and I've upgraded
to ubuntu 11.04 when I log in to the new desktop there's
nothing just one gnome bar at the top and what I think
is the unity launcher on the side but there is no icons on it
like the screen shots I've seen.I also have the nvidia
driver 275.09 installed but it's saying Driver installed but
not active.Can someone tell me what's going on and how to fix
it.I see a lot of post saying the same thing.Thanks
The driver is being used, there is a bug that makes it say that it is not in use, but that is not the case, if your driver was not you would not have the unity desktop with the launcher on the side. The icons are not on the desktop anymore, you can get to your applications by going to the launcher and clicking on applications.Also in my signature there are some guides for using and customizing natty.

---

### Post by andrea000 on 2011-06-07
There are no icon's on the launcher or i guess I should say there not displaying I can use them I just can't see them.

---

### Post by mikewhatever on 2011-06-07
What's the model of your Nvidia card? I think the 275.xx series is the current beta, so, unless your card is very new, you had better stick with the driver from the repositories.

---

### Post by andrea000 on 2011-06-08
it's a GeForce 7400.I also have another driver showing in
additional drivers but I don't know what that one is it's
only saying experimental 3d support for nvidia cards?

---

### Post by VanR on 2011-06-08
Hi, I would just log out and choose Gnome Classic at the bottom of the log-in screen and you will have the old Ubuntu desktop back. I tried Unity, but hated it.

---

### Post by mikewhatever on 2011-06-08
Well, Geforce 7xxx are known to exhibit this bizarre behavior. It seems to be something with the driver or compiz, or xorg, or most probably the combination of the three, and the options are as follows:
- If you want the latest Nvidia driver, don't use Unity or Compiz, cause they don't work. Just switch to the Classic (no effects) interface from the login screen.
- If you want to use Unity, get rid of the 27xxx nvidia driver and install a legacy nvidia-173. While that setup makes Unity sing, people have reported two bugs, external monitors and hibernation don't work.

---

### Post by andrea000 on 2011-06-09
Well i un installed the 270 driver and installed the 173 driver
unity will not even load using that driver just my wallpaper
shows up and nothing else.Ubuntu classic works great with the
270 driver.I wonder about gnome 3 and the 270 driver?I have
read both good and bad things about gnome 3.Could you or anyone
tell me the requirements and the pro's and con's of using it.
Thanks

---

### Post by Crempel on 2011-06-21
The best way to test the Gnome 3 shell is to install Fedora 15; but be warned; I have found it impossible to get any Nvidia driver to work, due to the fact that the Nouveau driver could not be removed. Gnome 3 works with Nouveau, but there is no real 3D performance.

However, talking about Natty, I had similar problems as you (Nvidia 7200 GS), and fixed them by

1. Using the 175.xx driver
2. Adding the line UNITY_FORCE_START=1 to /etc/environment.

Try it and see whether it works.;)

---

