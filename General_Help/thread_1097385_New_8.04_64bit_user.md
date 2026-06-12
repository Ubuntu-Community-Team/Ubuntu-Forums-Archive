---
title: "New 8.04 64bit user"
date: 2009-03-15
forum: General Help
---

### Post by overwingexit on 2009-03-15
Hi guys, I just switched over from windows. Im running on a 64 Athlon 3200 with a NVIDIA 8800GTS graphics card and 2 gigs of ram. I have been unsuccessful at downloading flash, java and even getting my sound to work right. I will hopefully be using X Plane once I get everything working. First, what are some good newbie help guides with unloading files etc. Secondly, should I switch to 32 bit so i could use i386 architecture? I would appreciate any help that you guys could give me.
Thanks

---

### Post by mb_webguy on 2009-03-15
I'm running 64-bit Ubuntu 8.10 on a computer with an nVidia card with no problems.  64-bit Linux used to have fairly poor support in terms of drivers and software, but that's no longer the case.  There are very few reasons not to use a 64-bit version of Linux if you have a 64-bit architecture.

First, for your video card.  Install the envyng-gtk package using your choice of either Synaptic or apt-get in the terminal.  Run the command "envyng -t" in the terminal.  This will identify your video card, suggest the best driver, and (if you want) install it for you.

I don't know why you should have any problems with Java.  Install the ubuntu-restricted-extras package, and it will install Java (and a few other niceties as well).

For Flash, uninstall the flashplugin-nonfree package (and any other Flash plugins you might have installed, such as gnash), then download the [Adobe plugin]("http://labs.adobe.com/downloads/flashplayer10.html") and drop it in your /usr/lib/mozilla/plugins/ or ~/.mozilla/plugins/ directory.

---

### Post by miegiel on 2009-03-16
> **overwingexit said:**
> ... I have been unsuccessful at downloading flash, java and even getting my sound to work right...

Flash and java are in the _[restricted]("https://help.ubuntu.com/community/Repositories/Ubuntu")_ or _[medibuntu]("https://help.ubuntu.com/community/Medibuntu")_ repositories. I'm not sure which :twisted:

There's a good sound guide at [http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by oldos2er on 2009-03-16
You might want to read the stickies in the 64-bit subforum regarding Java and Flash.

 64-bit Ubuntu is capable of running 32-bit software.

---

### Post by overwingexit on 2009-03-16
I got everything on my list completed:) except for the sound. I just cant seem find a way for it to work. I have searched threads about the realtek card. Is there a sound guide? I just cant designate which drive goes where

-NVIDIA CK804 Alsa Mixer
-Microsoft LifeChat LX-3000 Alsa Mixer ( i want this to be my mic. and headphones (speakers) )
-Realtek ALC850 rev 0 OSS Mixer

---

### Post by miegiel on 2009-03-16
> **miegiel said:**
> There's a good sound guide at [http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

:twisted:

---

