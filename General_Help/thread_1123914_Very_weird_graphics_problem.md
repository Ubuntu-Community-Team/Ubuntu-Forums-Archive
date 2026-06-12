---
title: "Very weird graphics problem"
date: 2009-04-12
forum: General Help
---

### Post by Beezleray on 2009-04-12
Hi,
I just updated my Nvidia drives and restarted my system and now there is this weird glitch. About a half an inch of the left hand of my screen is located on the right side. For instance, right now to scroll down I have to take my cursor off of the screen to the left and it'll apear on the right where the scroll bar is.

Does anyone know how to fix this?

---

### Post by Beezleray on 2009-04-12
Any help at all would be greatly appreacated.

---

### Post by Universal344 on 2009-04-12
With proprietary drivers there is only so much you can do.  I would suggest fiddling with the settings in the nVidia configuration program and seeing if anything works.

---

### Post by Beezleray on 2009-04-13
I messed with the nVidia config file and I get it to work but I have to mess with it every time I start up my computer, its annoying but I guess since its proprietary I'll have to deal.

---

### Post by DenysT on 2009-04-13
> **Beezleray said:**
> I messed with the nVidia config file and I get it to work but I have to mess with it every time I start up my computer, its annoying but I guess since its proprietary I'll have to deal.

Did you just run nvidia-settings off the menu? If so you fell into the same trap I did. Instead open a terminal window and use *gksudo nvidia-settings* to change your settings. Then save settings and all should be fine the next boot up.

Wouldn't it be nice if you could just right click on a system menu and get a "Run with gksudo" similar to "Run as..." in Windows? Just a thought.

---

### Post by Beezleray on 2009-04-14
At first I did it off the menu then I caught on and used gksudo, it still changes every reboot. I wonder if there is a script I can get to start on start-up and change it for me every time.

---

