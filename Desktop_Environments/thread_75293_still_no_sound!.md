---
title: "still no sound!"
date: 2005-10-13
forum: Desktop Environments
---

### Post by Jordan Meeter on 2005-10-13
Well I tried to reply my thread here: [http://ubuntuforums.org/showthread.php?t=70103](http://ubuntuforums.org/showthread.php?t=70103) but apparently it's locked. I tried [FONT="Courier New"]killall esd[/FONT] and I STILL have no sound! What is going on?

---

### Post by Jordan Meeter on 2005-10-13
*bump*

---

### Post by Jordan Meeter on 2005-10-14
*bump*

---

### Post by oldblue on 2005-10-14
Did you read this thread:
[http://www.ubuntuforums.org/showthread.php?t=75581](http://www.ubuntuforums.org/showthread.php?t=75581)
The sound card in question was a ICH6 (built in Intel chipset, I believe).  He fixed it by uninstalling polypaudio and installing esound.  You do this by running Synaptic Package Manager and searching for polypaudio and marking it for removal, then search for esound and mark for installation, then click the apply button.  Reboot the computer afterward.  I didn't go through the entire thread you posted, but did you get flash running?  This might not work for you, but it's a thought.

---

### Post by Jordan Meeter on 2005-10-14
Polypaudio is already disabled. =\

And yes, I got Flash working, thank you. :)

---

### Post by oldblue on 2005-10-14
OK.  Have you tried going into System->Preferences->Multimedia Systems Selector?  If it says ESD, change it to ALSA, and vice versa.  Then try doing things that produce sound sound.  If that doesn't work try setting it back to ESD, install polypaudio and uninstall esound, then reboot.  I'm reaching at straws here, but it's worth a shot, and it can all be changed again later.

---

### Post by oldblue on 2005-10-14
Oh yeah, if you go to System->Preferences->Sound what does it say?  Is sound server startup checked?  What about system sounds?  And what does it say for your soundcard?  Still try what I said earlier, but the info mught help.

---

### Post by Jordan Meeter on 2005-10-14
None of that worked. Damn. I didn't want to do this, but it looks as if I'm going to have to being my laptop to Best Buy. :(

[Edit] "Enable sound server startup" is check, as well as "Sound for events". And then is says what my default sound card is.

---

### Post by Jordan Meeter on 2005-10-14
Help?

---

