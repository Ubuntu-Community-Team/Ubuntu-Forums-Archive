---
title: "XFCE&amp;LXDE Tearing issue on Intel HD"
date: 2014-07-09
forum: Desktop Environments
---

### Post by maslacher on 2014-07-09
Hello everyone.
I have a problem which is very annonying. I am using Intel hd 2500 graphics and unfortanately driver acceleration method (SNA) is giving me a tearing in LXDE and XFCE (not tried diffrent DE however i am pretty sure that Ubuntu (compiz) has no tearing, Ubuntu Gnome (mutter?) has tearing and KDE (Kwin) has tearing (not sure about that). Previously i solved that issue with Compton (glx backend) but i am searching for less impact performance workaround(even less than using UXA acc method and TearFree option in intel driver). Any ideas? If i remember well Lubuntu 13.10 has no tearing at all. New Xubuntu option is not working for me.
Adittional question: how bad is TearFree option impacting performance? If this just takes a little bit of the ram than it is no an issue for me  because i have 4 gigs.
Q2: Is there any frames per second counter for Linux?
Q3: VLC is not inhibiting on XFCE power manager, this bug will be ever solved?
I have very bad graphics card (iGPU) so i very care about the performance so Ubuntu(or any BIG DE) is not an option for me.
Sorry for bad english, i may have do some errors down this road. Any response appreciate.

---

### Post by slooksterpsv on 2014-07-09
The tearing issue, I usually resolve for XFCE by loading Window Manager Tweaks in the settings (did you say 13.10? I'm on 14.04 with the Whisker Menu) and go to Compositor and disable it. Do you need the graphical effects?

Q2) FPS would be best tested with an app in the package mesa-utils. ( sudo apt-get install mesa-utils ) then run the following:
glxgears -info

It'll give you the FPS after about 5 seconds: 
2072 frames in 5.0 seconds = 414.317 FPS
2376 frames in 5.0 seconds = 475.052 FPS
2555 frames in 5.0 seconds = 510.925 FPS

Q3) No clue, you could see if the bug has been triaged or what not if it's on launchpad, or wherever their bug site is.

---

