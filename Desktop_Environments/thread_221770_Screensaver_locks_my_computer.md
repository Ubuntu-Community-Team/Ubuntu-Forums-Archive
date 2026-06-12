---
title: "Screensaver locks my computer"
date: 2006-07-24
forum: Desktop Environments
---

### Post by patrickthebold on 2006-07-24
The Matrixview screen-saver locks my computer up.  The log messages were:

Jul 24 00:46:51 localhost kernel: [  472.896574] [drm:r128_cce_depth] *ERROR* r128_cce_depth called without lock held
Jul 24 00:46:51 localhost kernel: [  472.897111] [drm:r128_cce_idle] *ERROR* r128_cce_idle called without lock held

So it seems like it has something to do with my video driver.  I'm mainly posting this if someone else has the same issues.  

Also, how do I uninstall this particular screensaver?

---

### Post by ahaslam on 2006-07-24
Hi,

The 'Antspotlight' screensaver completely locks my system. I'm sure that it's to do with my Via Unichrome graphics. Which log file is that from? - I'll induce a crash and compare my log in the hope that someone can help us.

Cheers,

Tony.

---

### Post by mcduck on 2006-07-24
If you haven't got 3D acceleration working all OpenGL-based screensavers can be very heavy on your CPU and might cause crashing too. So either enable 3D-acceleration or make sure that you aren't using any OpenGl screensavers (or random screensaver, as Gnome screensaver doesn't allow you to select wich ones are active..)

---

### Post by ahaslam on 2006-07-24
If you type **glxinfo** in a terminal do you get *direct rendering: Yes* a few lines down? If not it's probably down to not having hardware acceleration  as mentioned above.
Unfortunately I do have hardware acceleration & no entry is made in the xorg or kernel log files after a crash. :(

Tony.

---

### Post by patrickthebold on 2006-07-25
the log was syslog and kernel log.  I have the "direct rendering: Yes" line from glxinfo.  And the other openGL screensavers work.  I dont think its just being cpu intensive; the instant I click on Matrixview it locks up.

---

### Post by ahaslam on 2006-07-26
It sounds as though we're in a similar situation. My laptop only crashes with the antspotlight screensaver and at random points within 3D games.

Out of interest, what graphics card do you have? I am using a Via Unichrome Pro IGP. The problem is normal for my chipset due to buggy 3D support, which doesn't seem to be under development.

Tony.

---

### Post by patrickthebold on 2006-07-27
Its a ATI Rage128.  Its pretty old, and some the the other open GL one look really bad, but they don't instantly crash the computer, nor do they throw the aforementioned error.  I think it's a bug in the driver that this particular screensaver seems to setoff.

---

