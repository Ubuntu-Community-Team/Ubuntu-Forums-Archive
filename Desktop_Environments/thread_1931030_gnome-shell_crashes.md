---
title: "gnome-shell crashes"
date: 2012-02-24
forum: Desktop Environments
---

### Post by cybergalvez on 2012-02-24
Gnome-shell crashes every time I try to use the search box. I have turned off all the extesions I was using to see if that would help but nothing, It seems to have started this morning, but I really can't be sure because I've not used the computer for much other then email for a few days

OK it seems that it's the nvidia driver, I ahve 295.20 from x-update. Does anyone know how to downgrade to version 290?

---

### Post by Frogs Hair on 2012-02-24
This is happening to others as well. Search for the other threads to find out if anyone has solved the problem . You could check launchpad also.

---

### Post by cybergalvez on 2012-02-24
well I just ended up downgrading to version 280 which is in the repos. Hopefully the next version of the nvidia driver will fix the issue

---

### Post by sc00ter on 2012-03-04
Thanks for the info. 

I too had a very unstable lucid 10.04.4LTS system since the upgrade of the Nvidia drivers to 295.20 from the X-Update PPA.

My issues included:

1. Occasional system hangs, with frozen screen with the mouse movement still responding.

2. GL Screensaver activating = occasional hang

3. Compiz desktop effects + maximizing a window = occasional screen freeze!

4. Full screen video playback (especially with HD content .mkv files) = occasional screen freeze!

5. Clean shutdown stopped. System would shutdown, with blank screen and system fan running. Hard power off (holding power button down) was the only way to turn the laptop off.

I then downgraded my Nvidia drivers to 280.13 (luckily was still in the repos) and "locked" the packages.

Now my system is back to it's usual stable self. No more random screen freezes and more importantly, system now shuts down cleanly (no more holding the power button until full power off).

My system is:

Dell XPS M1530
Ubuntu 10.04.4 LTS (2.6.32-39-generic)

I too am now waiting for a fix, until then I'm staying with the working drivers.

---

### Post by escentrix on 2012-03-06
For the gnome-shell crashes, I posted some information I found here: [http://ubuntuforums.org/showthread.php?t=1931677](http://ubuntuforums.org/showthread.php?t=1931677)
maybe it will help others.

---

