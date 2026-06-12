---
title: "unity icons huge"
date: 2016-07-15
forum: Desktop Environments
---

### Post by MikeCyber on 2016-07-15
Hi
 after the latest update unity icons are to big. Also nautilus seems older...
Thanks

---

### Post by grahammechanical on 2016-07-15
There are two possibilities that I can think of.

(1) The update included an update to Unity 7 and that reset the Unity icon size. System Settings>Appearance>Adjust the Launcher icon size.

(2) The update was a kernel upgrade and there is now some conflict with a proprietary video driver and the system is now loading with a fallback open source video driver called llvmpipe. System Settings>Details tab. Is Graphics listed as llvmpipe? Go to System Settings>software & Updates>Additional Drivers tab and change video drivers. We need to be connected to the internet to do this and also to allow time for the utility to find the drivers.

I do think that the kernel in 16.04 recently got upgraded to 4.4.0-30-generic. And Nautilus is still at 3.14.3. On my 16.04 system that is.

Regards.

---

### Post by MikeCyber on 2016-07-16
I can't fully scale them back. Nautilus says 3.18.5
Thanks

---

### Post by Frogs Hair on 2016-07-16
It appears you have a newer version of Naultilus , are you using a Gnome PPA ? I'm seeing Nautilus 3.14.3 as default in 16.04.

---

### Post by MikeCyber on 2016-07-16
gnome-session from synaptic. Nautilus seems old and featureless...guess I have to wait for the next update.

---

### Post by Frogs Hair on 2016-07-16
You'll find the newer versions of Nautilus  have less features in keeping with Gnome's new approach. Still interested in how you installed Nautilus 3.18.5 because I think it's the cause of the problem.

---

### Post by PJs Ronin on 2016-07-16
I believe there are still some [problems]("http://www.omgubuntu.co.uk/2016/02/nautilus-3-20-zoom-level-options") with Nautilus 3.18 and the current version has been retrograded to the previous 3.14 version.
```
wayne@yakkety:~/Desktop$ apt-cache policy nautilus
nautilus:
  Installed: 1:3.18.4.is.3.14.3-0ubuntu4
  Candidate: 1:3.18.4.is.3.14.3-0ubuntu4
  Version table:
 *** 1:3.18.4.is.3.14.3-0ubuntu4 500
        500 http://archive.ubuntu.com/ubuntu yakkety/main amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by MikeCyber on 2016-07-17
so updated to 3.2 and guess what. It's unusable. gedit no scroll bar, terminal not readable etc. How to reset all including theme?
Thanks

---

### Post by DragonBoy on 2016-07-19
Go to the following:

System Settings > Appearance > Look tab

There should be an launcher icon bar at the bottom of the window. Adjust the size you prefer. Good luck!

---

### Post by overdrank on 2016-07-21
Solved with today's update :)

---

### Post by leatherneckbiker on 2016-07-25
First, I did try to search for other threads on this same topic and may not have been using good enough keywords, so if this is a duplicate I apologize. 

This is an issue. Some custom icon sets are not scaling properly in Nautilus after upgrade to 16.04.

I've done clean installs of 16.-04 for both Ubuntu and Ubuntu-Gnome on a Dell Inspiron 17-7778 2-in-1. After install I ran update/upgrade and didn't install any other packages. 

for both installs I created a .icons directory under my /home and copied the icon set into that directory. For testing purposes, I used the Azenis Icon set. It worked perfectly in 14. So there's nothing wrong with the icon set itself. When I opened the gnome or unity tweak tools (respectively) the icon set shows up. when I select it, they only display full size in the file manager. For Unity, the launcher scaled correctly and I could adjust the sizes. Same for the Gnome launcher. But no matter what I set the zoom level to in Nautilus, the icons remain full size. 

Not sure what to try. Any assistance would be appreciated.

Update... I did some more playing around and found the same set of icons scales as expected in the "list" view. I can change the scaling and see the effect. It only seems broken when attempting to scale the "icon" view.

---

