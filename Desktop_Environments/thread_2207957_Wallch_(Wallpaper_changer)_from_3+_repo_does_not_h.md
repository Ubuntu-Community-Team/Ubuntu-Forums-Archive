---
title: "Wallch (Wallpaper changer) from 3+ repo does not have the &quot;Set custom command&quot; optn?"
date: 2014-02-25
forum: Desktop Environments
---

### Post by SweetBearCub on 2014-02-25
I installed the latest version of Wallch from the 3+ repo, as it is supposed to have the "Set custom command" option under the Edit menu, with a dropdown to allow it to be configured to work on Lubuntu (13.10). But the version I have (v3.6) does not have that option anywhere, and so it does not work for me. I tried using a couple different custom scripts I found here on these forums to change my wallpaper, but they did not work. These are the commands I used to get the version of Wallch that I have, which I think is the latest.

```
sudo add-apt-repository ppa:wallch/3+
sudo apt-get update && sudo apt-get install wallch
```

Why is the command to modify it for Lubuntu/LXDE/openbox missing in this version?

Thanks!

---

### Post by hakermania on 2014-02-28
Hello there SweetBearCub!

I am one of the devs of Wallch, and I just want to let you know that Wallch 4.0 is indeed ready (not released anywhere officially) and is already included in 14.04's repos and is downloadable from here: [http://www.ubuntuupdates.org/wallch](http://www.ubuntuupdates.org/wallch)

The package is for 14.04, but the installation goes smoothly in 13.10 as well, without any problems, by my side, at least.

You will not find any Custom Command dialogs (because I considered it a security risk), but Wallch now supports LXDE, XFCE, Gnome and Mate, so you will not need the custom command dialog :D

---

### Post by SweetBearCub on 2014-02-28
Hi there! *Pleased bear sounds*

I installed the 64 bit package of 4.0, and it is set for LXDE in the preferences section, but it doesn't work. :-(

I tried to record my desktop with gtk-recordmydesktop from the software center, but the video only came out halfway, not showing the whole screen, with some kind of diagonal corruption across the resulting video, making it ununsable. I'll try to take some photos with my phone later to show you my settings/etc. It'll have to be later today though, I have some things to attend to.

Thanks for trying - I hope that you don't give up on helping me to get it working. :-)

---

### Post by hakermania on 2014-02-28
Oh :( Well, as I developed the LXDE support, I am not pleased. But, to my defense, LXDE is pretty badly organized as for its settings. One thing that I find completely wrong is that its settings parameters have to be created at first if you have not access them., And they are not the same between systems. For example, you may have to change an option called VLDS1 in order to set the wallpaper, and I will have to change the option VLDS0.

If this is the case (just in case), please open normally your LXDE desktop background switcher and change all the options there: The current wallpaper, the style of it, the background color etc (I don't remember all of them, I use Gnome right now so I can't really check). This will create all the necessary options for Wallch to operate (hopefully).

What about the *Pleased bear sounds* ? I thought everything went fine but then I was disappointed :P Was it about the new interface?

I cannot guarantee that it will work though, Wallch 4.0 was tested under LUbuntu 14.04, so I hope that you will not have any problem using it in a month from now.

---

### Post by SweetBearCub on 2014-03-01
I opened my LXDE settings, a wallpaper was already set there (not from Wallch), I changed it, and the other settings. Wallch still does not set or change the wallpaper for me.

Previously, the only way I have found to change the wallpaper without going into the desktop background options was by using a command line option, something having to do with Lubuntu's default file manager, PCManFM. I found this via one of the wallpaper changing scripts on the forum here. Though the scripts I found did not work properly for my system, the actual meat of the script, the command to PCManFM to change the background image, did work when I tested it.

As far as the "pleased bear sounds", someone said hello, and since a bear cub can't exactly speak, I returned your hello that way, as a nice reference to my persona. :-)

---

### Post by hakermania on 2014-03-01
Oh, I was mistaken. The above was about XFCE, not LXDE. Silly me. Wallch 4.0 uses ```
pcmanfm -w "image"
``` in order to change the image. Proof: [http://bazaar.launchpad.net/~wallch/wallpaper-changer/trunk/view/head:/src/glob.cpp#L487](http://bazaar.launchpad.net/~wallch/wallpaper-changer/trunk/view/head:/src/glob.cpp#L487)

Make sure that in preferences, under Integration, you have set your DE to be LXDE.

This will work 100% as long as it is pcmanfm the one who controls your desktop (as it does in LUbuntu 14.04 by default)

---

