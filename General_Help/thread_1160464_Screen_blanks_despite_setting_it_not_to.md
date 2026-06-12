---
title: "Screen blanks despite setting it not to"
date: 2009-05-15
forum: General Help
---

### Post by Old *ix Geek on 2009-05-15
I'm obviously missing some setting, somewhere.  I have set EVERY possible option I can find to NOT use power saving, screensavers, ANYTHING that can cause the screen to blank.  For example, I've chosen "do nothing" for "when laptop lid is closed."  I've been through every setting multiple times and I'm just not seeing anything else, but the screen goes blank after X amount of inactivity, and it goes blank when I close the lid.  Where's the setting I'm not seeing? :confused:  Better yet, which config file controls this?

In case you're wondering, I don't want it to blank because when it does it causes random hanging.  I'll attempt to use the laptop and it's totally unresponsive.  NOTHING works.  Not the trackball. Not pressing a key.  Not [ctrl][alt][backspace]. Not [alt][F2].  Not ANYTHING.  And I end up having to hard reboot.

---

### Post by wpshooter on 2009-05-15
You might want to check the setting of the power related parameters in BIOS, BUT, if you are also having random lockups, then I would say you probably have more problems than just some setting that is affecting the screen blanking.

Possibly something related to video card drivers, but then it could also be computer overheating or a multitude of other things.

Good luck.

---

### Post by Old *ix Geek on 2009-05-15
Funny...I do happen to think it's video-related, though I don't know what exactly. After giving up on Jaunty I downgraded back to 8.10, then I installed all updates for KDE (4.2) and I'm using the recommended NVIDIA driver for this laptop.  Yet I'm having some flaky graphics-related issues.  HOWEVER...this same laptop was randomly locking up before, too.  I mean when I was running Intrepid before trying Jaunty.  Every time it locks up it's after the screen blanks itself despite my choosing every possible setting that says not to!

---

### Post by Screwdriver0815 on 2009-05-15
did you also check the screensettings in the single energyprofiles?

For that you need to go to System settings -> advanced -> energy management and on the lefthand side on "profiles". In each profile is close to the bottom something like a tab (but not really a tab) for the screen which you can open. In there you can choose to not switch off the screen.

There is also a second possibility: in system settings -> screen settings. There you should also set up the energy options like you want them to be.

---

### Post by Old *ix Geek on 2009-05-15
> **Screwdriver0815 said:**
> did you also check the screensettings in the single energyprofiles?

For that you need to go to System settings -> advanced -> energy management and on the lefthand side on "profiles". In each profile is close to the bottom something like a tab (but not really a tab) for the screen which you can open. In there you can choose to not switch off the screen.Yep, I already have ALL of the profiles set not to do anything.  The example I mentioned in my OP is that I have "do nothing" selected for "when laptop lid is closed," but it still blanks the screen.
> There is also a second possibility: in system settings -> screen settings. There you should also set up the energy options like you want them to be.I don't have a "Screen settings" choice on my "System settings" screens.  I do,  however, have "Display" and then I can select "Power control."  As with everything else, I already had that set to NOT enable display power management.

This is frustrating. ](*,)

---

### Post by Old *ix Geek on 2009-05-17
bump...

---

