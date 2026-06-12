---
title: "Clock For Unity Desktop"
date: 2020-12-21
forum: Desktop Environments
---

### Post by O)9(yo&amp;# on 2020-12-21
I would like to put a nice analog clock on the dock or launcher (the thing on the left, not the top) of the Unity desktop. I am running 16.04 and can't upgrade to 18 due to graphical issues. I tried Up-Clock, it installed easily and locked to the dock fine, but I can't for the life of me find anywhere the instructions for actually setting it. Just articles saying it's a nice-looking clock. Does anyone know of one I can add (and actually set)?

---

### Post by CelticWarrior on 2020-12-21
Ubuntu 16.04 will be EOL in 4 months.

---

### Post by ActionParsnip on 2020-12-21
Why such an old release?

---

### Post by crip720 on 2020-12-21
Seeing that 16.04 has limited time for support, maybe make new question about your graphical issues and someone here can help.

---

### Post by O)9(yo&amp;# on 2020-12-21
To reply to all three responses, yes I know 16.04 is EOL in April. I plan to take advantage of the Extended Security Maintenance at that point. The problem with graphics is that most distros  beyond 16.04 won't work with the 6150SE motherboard on this old Gateway (ca. 2008). I had a dedicated video card at one point (GeForce 8400), but it died. I had also upgraded the original power supply, but it also died. So I am back on the original PS and graphics, and see no point in spending money on such an old machine. So I try to find distros that will work on it. 16.04 based-distros are the last ones that support the Nvidia 304 driver, which is needed for this situation. Severe screen distortions result with Nouveau drivers. The only 18.04-based distro that works on this machine is Bodhi 5. It works fine with the Nouveau drivers, after I disable acceleration in my browser (Vivaldi). 

So Ubuntu 16.04 and Bodhi 5 are my distros going forward. Both will give this machine a few years of life. And so I am looking for a clock for 16.04. The tiny time readout in the upper right is difficult to read for my aging eyes.

---

### Post by Frogs Hair on 2020-12-21
Is cairo clock in the 16.04 repository ?

---

### Post by CelticWarrior on 2020-12-21
You shouldn't be using vanilla Ubuntu in that ancient hardware. If Bodhi works it's because it has a very light DE. If you try Lubuntu, Xubuntu or even Mate or Budgie I think you'll be pleasantly surprised.

---

### Post by O)9(yo&amp;# on 2020-12-21
Duplicate post

---

### Post by O)9(yo&amp;# on 2020-12-21
> **Frogs Hair said:**
> Is cairo clock in the 16.04 repository ?

[COLOR=#000000]Well it's in Synaptic, but latest version is Ubuntu2. I'm going to check into "fdclock," which is also listed in Synaptic. I had checked out Cairo clock, but could not find any download links as it's so old, so I didn't think it was worth pursuing.[/COLOR]

---

### Post by O)9(yo&amp;# on 2020-12-21
> **CelticWarrior said:**
> You shouldn't be using vanilla Ubuntu in that ancient hardware. If Bodhi works it's because it has a very light DE. If you try Lubuntu, Xubuntu or even Mate or Budgie I think you'll be pleasantly surprised.

I did try all those you mentioned, not one of them worked, severe distrortions in every case. (These were the 18.04-based ones; the 16.04-based ones are no longer supported).

---

### Post by Frogs Hair on 2020-12-23
> **michael_diemer said:**
> [COLOR=#000000]Well it's in Synaptic, but latest version is Ubuntu2. I'm going to check into "fdclock," which is also listed in Synaptic. I had checked out Cairo clock, but could not find any download links as it's so old, so I didn't think it was worth pursuing.[/COLOR]

There are still themes being developed for cairo clock as of this year. I don't know what Linux versions it is used on. 
  
[https://www.gnome-look.org/browse/cat/208/order/latest/](https://www.gnome-look.org/browse/cat/208/order/latest/)

---

### Post by mc4man on 2020-12-23
> **michael_diemer said:**
> I would like to put a nice analog clock on the dock or launcher (the thing on the left, not the top) of the Unity desktop. I am running 16.04 and can't upgrade to 18 due to graphical issues. I tried Up-Clock, it installed easily and locked to the dock fine, but I can't for the life of me find anywhere the instructions for actually setting it. Just articles saying it's a nice-looking clock. Does anyone know of one I can add (and actually set)?
If you're looking for an active clock in the unity launcher you can stop now, doesn't exist, never will.
Plank has an active analog clock docklet, works fine though plank doesn't integrate completely with unity desktop, i.e icons on the desktop can overlap it..

---

### Post by O)9(yo&amp;# on 2020-12-24
> **mc4man said:**
> If you're looking for an active clock in the unity launcher you can stop now, doesn't exist, never will.
Plank has an active analog clock docklet, works fine though plank doesn't integrate completely with unity desktop, i.e icons on the desktop can overlap it..

Thanks, I may look into Plank, maybe there's a way I can make it work well enough to be practical.

---

### Post by O)9(yo&amp;# on 2020-12-24
> **Frogs Hair said:**
> There are still themes being developed for cairo clock as of this year. I don't know what Linux versions it is used on. 
  
[https://www.gnome-look.org/browse/cat/208/order/latest/](https://www.gnome-look.org/browse/cat/208/order/latest/)

Thanks, I'll explore these options.

---

### Post by Nikisch on 2020-12-24
The latest release 20.04 also lacks a dock clock

---

### Post by mc4man on 2020-12-24
> **michael_diemer said:**
> Thanks, I may look into Plank, maybe there's a way I can make it work well enough to be practical.

It can be set up to be pretty useful, I think it's best on bottom though can go anywhere (noting you can hide default unity launcher but you can't get rid of it.
See screen, a quick set up, notice I added the home scope.. 
(- while plank supports desktop actions the right click on 'real' home scope isn't as it's not a desktop.. those right clicks could be added as actions to the plank version of the home scope..

---

### Post by O)9(yo&amp;# on 2020-12-24
> **mc4man said:**
> It can be set up to be pretty useful, I think it's best on bottom though can go anywhere (noting you can hide default unity launcher but you can't get rid of it.
See screen, a quick set up, notice I added the home scope.. 
(- while plank supports desktop actions the right click on 'real' home scope isn't as it's not a desktop.. those right clicks could be added as actions to the plank version of the home scope..

That looks great! I'm going to give it a go. thanks and Happy Holidays!

---

### Post by mc4man on 2020-12-24
> **michael_diemer said:**
> That looks great! I'm going to give it a go. thanks and Happy Holidays!

In case not apparent,
plank doesn't autorun so after install open Dash, search startup, open startup applications and add plank , like in screen will suffice. Then after a log out/in or reboot plank will be running.

To add applet and any options run this command in a terminal or from alt+F2
```
plank --preferences
```

If keeping and desiring a Dash icon , ask, pretty simple to do.

---

### Post by O)9(yo&amp;# on 2020-12-24
Thanks again, mc4man. I have plank up and running. I am having trouble getting the Cairo clock installed, however. I have dowlnloaded the timex and Rauland versions. I also got  AppImage Launcher and Pling Store, and tried to get OCR-URL, but I couldn't download that one. I can't figure out how to get the clock installed. I have never used AppImage or the other two things before, so I'm at a loss at this point. I really appreciate the help!

---

### Post by O)9(yo&amp;# on 2021-01-04
After some unsuccessful attempts to add Cairo clocks, I went with Mc4Man's suggestion of just adding the clock provided by Plank. Kind of small, but it does the job, I can see at a glance what time it is, instead of straining my eyes to find and read the panel clock!

---

