---
title: "Xubuntu-like laptop from Ubuntu Alternate CD 8.10"
date: 2009-01-14
forum: Desktop Environments
---

### Post by Saul Perdomo on 2009-01-14
Hi guys, just asking for a quick'n'dirty recommendation. I finally managed to install Ubuntu (with only console) from the Ubuntu Alternate 8.10 CD on an old ThinkPad (afer trying and failing using an Ubuntu and then a Xubuntu CD).

Now, I'd like to have a Xubuntu-like system, ultra-light, but don't want the hassle of downloading a Xubuntu Alternate ISO and running to the shop for a blank disc and burning a new image... what packages do you recommend I install? Is it a matter of just installing the **xfwm4** window manager, or do you recommend other packages? And will installing xwfm4 get me the menu as in Xubuntu, you know, all Gnome-like and stuff?
[SIZE=1]
(oh, and btw I still have to get the system to add my eth card, ifconfig only shows the **lo** interface but I'm scouring the forums to see what I can do)[/SIZE]

---

### Post by taurus on 2009-01-14
If you want Xubuntu (XFce4), you can install it from a prompt with

```
sudo apt-get update
sudo apt-get install xubuntu-desktop
```

---

### Post by snowpine on 2009-01-14
Type the following terminal command to get a full Xubuntu install:

```
sudo apt-get install xubuntu-desktop
```

Or, to get a stripped down Xfce desktop:

```
sudo apt-get install xfce4
```

---

### Post by mali2297 on 2009-01-14
If you install the meta package [xubuntu-desktop](http://packages.ubuntu.com/intrepid/xubuntu-desktop), then you will the same setup as if you would install from a Xubuntu CD.

But if you want a lighter option with just the core parts of the desktop environment, then install the package [xfce4]("http://packages.ubuntu.com/intrepid/xfce4") instead.

---

### Post by Saul Perdomo on 2009-01-14
Yes, just what I was looking for! Thank you guys, I had to go with the xfce4 package since sadly I had only allocated 2 gigs in this tiny 10-gig drive... and the base system alone took over 500 megs. I just didn't have enough space for the full xubuntu-desktop installation, which wanted 1.5 gigs I just didn't have.

On a tangent here, I guess I was just stuck on the days where a full Gnome instal took a bit less than 1.5 gigs. Now a xubuntu install wants at least 2 gigabytes? Geez, I thought xubuntu was aimed at older computers. Would it have taken less space if I had just had the patience to download a xubuntu alternate CD? That's starting to sound a lot better now, looking at repartitioning an NTFS partition from XP sounds even more boring.

---

### Post by adamlau on 2009-01-14
You will want to look at the [Ubuntu Minimal CD](https://help.ubuntu.com/community/Installation/MinimalCD) + Xfce :) .

---

