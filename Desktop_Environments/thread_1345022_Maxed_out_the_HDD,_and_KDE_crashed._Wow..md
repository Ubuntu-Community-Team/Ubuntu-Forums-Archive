---
title: "Maxed out the HDD, and KDE crashed. Wow."
date: 2009-12-03
forum: Desktop Environments
---

### Post by Roasted on 2009-12-03
So I installed Kubuntu on my laptop, worked great, blah blah. Copying a 2gb file to it and maxed it out in the process. Ooops. So KDE crashes. Okay, sucks, but whatever. So I reboot... KDE doesn't show back up. Okay, this really sucks... I got an old school looking Gnome setup, and an error that some desktop applet crashed.

I need this laptop running, like, uh... 30 minutes ago, so I'm installing Ubuntu since I know it'll be stable and to be quite frank it's the only CD I have with me at work anyway.

So, what happened? Why does maxing out a hard drive result in KDE crashing? I even deleted some files off of the computer (about 8 gig worth) and KDE STILL is no where to be seen.

What the hell, KDE?

---

### Post by lykwydchykyn on 2009-12-03
Was it the home partition or root partition that was maxed?  Or is it all on one partition?

I guess there's no way to troubleshoot now, since you're reinstalling...

---

### Post by Roasted on 2009-12-03
Actually I found out that the FOG service still worked despite it looking like it was running on Gnome from Ubuntu 4.10. So I haven't changed anything on the laptop.

It was all 1 partition. I was writing data to the /images directory which is under the main of the file system... aka in the same location /etc, /usr, /home, etc is located.

I removed over 16gb of data, and still this thing is FUBAR'd.

EDIT - So uh... I just had to select KDE for the session log in. I guess it defaulted to some kind of failsafe to prevent any trouble. *shrug*.

So, I admit, I suck, I messed up. GO KDE. :)

---

