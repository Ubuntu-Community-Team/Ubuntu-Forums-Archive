---
title: "No sound from VLC etc."
date: 2006-01-25
forum: Desktop Environments
---

### Post by chris_andrew on 2006-01-25
Hi,

I have recently installed Breezy, but cannot hear any sound, when logged in.  During log-in, Ubuntu plays the log-on sound.  

When I try to play an avi or streaming media, I can't get any sound.  I have checked the volume levels, and alsamixer.  I haven't been able to run alsaconf.  I guess some part of gnome is controlling this function.

When i add a volume control to my desktop, it has a cross by it, and the information box says that the correct gstreamers (or something) aren't available, or the device isn't found.

All I can think is, that this is a permissions problem.  Can anybody help me?

Many thanks,

Chris.

---

### Post by Jimmey on 2006-01-26
When in Gnome, press ALT + F2. In that window, type
> killall esd
Then run the program ( VLC ) you want sound from. If it was already open, stop the media, and then play it again, you should get sound.

---

### Post by chris_andrew on 2006-01-26
Will try this when I finish work.  Will let you know how I get on.

Many thanks,

Chris.

---

### Post by chris_andrew on 2006-01-28
Hmmm,

It said something like "No processes with this name" :-(

Debianhelp had some ideas:

[http://www.debianhelp.org/module-pnForum-viewtopic-topic-10790-start-0.html#pid45889](http://www.debianhelp.org/module-pnForum-viewtopic-topic-10790-start-0.html#pid45889)

But i'm still to solve the problem.

Thanks,

Chris.

---

### Post by Jimmey on 2006-01-28
Do you hear the Ubuntu jingle when you start the computer?

---

### Post by chris_andrew on 2006-01-28
Jimmey,

"During log-in, Ubuntu plays the log-on sound. "

I do hear the sound, but not once logged-on.

Thanks,

Chris.

---

### Post by Jimmey on 2006-01-28
So there's no sound after the logon, even from the menus, and such?

---

### Post by chris_andrew on 2006-01-29
Jimmey,

Not a sausage, mate.  As much as I love Ubuntu, at least my Debian Sarge install has working sound :-(.

My next step could be to remove all sound stuff, *dpkg --purge* said files, and re-install.  I suspect Gnome will have the sound as dependencies, though.

Cheers,

Chris.

---

### Post by Jimmey on 2006-01-29
Try typing 
> esd
From what I gather, esd's what controlls the little menu sounds, and stuff. When I start XMMS, it complains that something's blocking my soundcard, and so "killall esd" seems to fix it...But strips the sound from the menus, and Gaim, etc.

It doesn't sound like a driver (Hardware) problem, because it plays the opening jingle thing. It sounds more like some part of the software used to play sound has messed up - Is there anything you've done that could have caused this, or did the sound just not work, from the start?

---

### Post by Jimmey on 2006-01-29
Aha. I think I found, a possible fix.

Under "System >> Administration"  click "Synaptic Package Manager".
Click on the "Search" icon in the top right, and type
> gstreamer
There's quite alot with the word "gstreamer" in the name. You'll have to check the descriptions of each, and try and tick the right ones for installation. The other option being to install them all...

---

