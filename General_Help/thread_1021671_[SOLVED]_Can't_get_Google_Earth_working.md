---
title: "[SOLVED] Can't get Google Earth working"
date: 2008-12-25
forum: General Help
---

### Post by N9TA on 2008-12-25
Man, I'm havin' a blast with Ubuntu....BUT, I can't get Google Earth working and I've tried everything I could find on the forum.

Google Earth installs just fine...no error codes or anything. But when I start the program it brings up the splash screen...then goes into the Google Earth console where everything looks just fine EXCEPT there is no Earth!! Just a field of stars.

I've tried every way of installing Google Earth I could find on the forum....and EVERY one gets the same results. 

Anybody have any ideas what I may have goofed up??

Fred

---

### Post by dcstar on 2008-12-25
> **N9TA said:**
> Man, I'm havin' a blast with Ubuntu....BUT, I can't get Google Earth working and I've tried everything I could find on the forum.

Google Earth installs just fine...no error codes or anything. But when I start the program it brings up the splash screen...then goes into the Google Earth console where everything looks just fine EXCEPT there is no Earth!! Just a field of stars.

I've tried every way of installing Google Earth I could find on the forum....and EVERY one gets the same results. 

Anybody have any ideas what I may have goofed up??

Fred

Does your video hardware have 3D working correctly?

---

### Post by benny bronx on 2008-12-25
Try it with desktop effects disabled and see if it works. My experience, however, is that version 4.3 did not like my computer, so I installed 4.2 from the medibuntu repo, and everything is working with metacity and compiz.

---

### Post by N9TA on 2008-12-25
> **dcstar said:**
> Does your video hardware have 3D working correctly?
I "think" so....I'm pretty new to Linux. I'm using an "NVIDIA Accelerated Graphics Driver (Version 173)". I've got Mythtv working great, I'm running Windows XP_MCE in a virtual machine with "Virtualbox"...and having a BLAST learning all this new stuff. But Google Earth....of all things...is kicking my butt!!

---

### Post by N9TA on 2008-12-25
> **benny bronx said:**
> Try it with desktop effects disabled and see if it works. My experience, however, is that version 4.3 did not like my computer, so I installed 4.2 from the medibuntu repo, and everything is working with metacity and compiz.
If I try this, will my Mythbuntu installation quit working??

And HOW do I disable desktop effects?

---

### Post by N9TA on 2008-12-25
> **benny bronx said:**
> Try it with desktop effects disabled and see if it works. My experience, however, is that version 4.3 did not like my computer, so I installed 4.2 from the medibuntu repo, and everything is working with metacity and compiz.

Okay, I figured out how to disable desktop effects:System/Preferences/Appearance/Visual Effects.
That didn't make any difference. I re-installed Google Earth from the Medibuntu repository....after doing a "sudo apt-get autoremove googleearth" to purge any failed attempts...and still got only the star field.

I'm kinda happy that didn't fix GoogleEarth....because disabling visual effects made my display look kinda "flat".

Any other ideas?

---

### Post by benny bronx on 2008-12-25
Medibuntu has both googleearth 4.2 and 4.3. Which one did you install.  I had trouble with 4.3 and none with 4.2. If neither one works, it may be a hardware problem as dcstar stated.  One painless trick you might try is, after running Googleearth for the first time, go into your home folder and delete the googlearth folder, then restart the application.  I've read that this occasionally solves some problems.

---

### Post by N9TA on 2008-12-26
Got it working!! I brought a terminal and entered  > sudo googleearth  
This brought up Google Earth just fine. This means I didn't have "permission" to run Google Earth from my username. This permission crap is VERY hard for me to get used to....in short...it SUCKS!

I solved it by cd'ing to the directory where Google Earth lives on my system ( /OPT/Google-Earth ) and doing a> sudo chown *username:username[I] **[/I] in the terminal window. Change "*username[I]"*[/I] to whatever YOUR username might be and you're good to go.

---

### Post by Kappity on 2009-01-03
> **N9TA said:**
> Got it working!! I brought a terminal and entered sudo googleearth 
This brought up Google Earth just fine. This means I didn't have "permission" to run Google Earth from my username. This permission crap is VERY hard for me to get used to....in short...it SUCKS!

Hey, that works, thanks.  Google Earth is still kind of slow compared to how it works on my Macs, or on the XP computers at work, but at least it's usable.

> **N9TA said:**
> I solved it by cd'ing to the directory where Google Earth lives on my system ( /OPT/Google-Earth ) and doing a in the terminal window. Change "*username[I]"*[/I] to whatever YOUR username might be and you're good to go.

Okay, here's the part that still is a problem for me.  Wasn't sure exactly what I am running when I type googleearth, so it's hard to figure out what to change the permission for.  There is nothing for Google Earth in my /OPT/ directory.  So I searched the file system for anything with Google in it to find what it is that I'm actually running.  I thought it was a script "googleearth" in the usr/bin directory, so I typed "sudo chown root:myusername googleearth" in that directory.  It apparently took it, but then when I type "googleearth", or select the shortcut in the application menu, I just get the blank starfield.  It's not a big hassle to type sudo googleearth every time, but I'd really like just to be able to click on the shortcut.  What am I missing? :confused:

---

