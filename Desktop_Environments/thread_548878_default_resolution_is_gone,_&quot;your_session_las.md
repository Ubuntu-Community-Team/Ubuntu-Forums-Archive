---
title: "default resolution is gone, &quot;your session lasted less than 10 seconds&quot;"
date: 2007-09-11
forum: Desktop Environments
---

### Post by akiratheoni on 2007-09-11
So for some reason lately, I've been getting a "your $HOME/.dmrc is being ignored" whenever I log in... then today, I got that error, then it logged in, then logged out and gave me a "Your session lasted less than 10 seconds" error message. I think it said something about checking the disk space and logging into the failsafe GNOME. I checked my diskspace, freed up about 1.5 GB and logged into the failsafe GNOME (which I'm posting on now).

The thing is, the first time I logged on, my computer was at its normal 1680x1050 resolution, but it wasn't... correct. Everything was big and only part of the desktop actually fit on the screen. I don't know how else to describe it. But now that I've logged out and logged back in, the choice for a 1680x1050 is gone, even though in the xorg.conf file the 1680x1050 is still present. How can I fix this?

BTW I still get the /.dmrc ignore error, even though I renamed it because I heard somewhere that deleting it should solve the problem (but I just renamed it just in case).

---

### Post by reckless2k2 on 2007-09-11
check your permissions on your home directory:

ls -al


it should all be youruser:youruser

i've seen errors like this with .files getting messed up from using sudo on graphical apps rather than gksudo

---

### Post by akiratheoni on 2007-09-11
Hm, there are two folders that are user:root, should I change the permissions of it? It's my .compiz and .automatix folder, if it matters.

---

### Post by reckless2k2 on 2007-09-11
make it happen captain. what's the worse that will happen...you can't log in. hahaha.

hhmmm...using automatix though could be a root of an issue.

---

### Post by akiratheoni on 2007-09-11
Thing is, I've had automatix (I know it can cause problems) since pretty much day 1 and it's never given me issues, so I don't think that could be it. But anyway I changed the permissions so I'll see if that fixes it.

BTW any suggestion for my resolution problem? Even though 1680 x 1050 is selected in the xorg reconfigure and in my xorg.conf, it doesn't appear at all under System -> Preferences -> Screen Resolution.

---

### Post by reckless2k2 on 2007-09-11
well automatix can haunt you if you use that initially then later update a package via synaptic or apt. that's the issue. 

let me know if you can get in. slap a SOLVED on that bad boy if so.

now as far as xorg.conf.......i missed it...are you getting the resolution you want or are you sitll at something different? 

i missed that part. 

let me know your chipset too......i'm betting intel which you will need 915 resolution.

---

### Post by akiratheoni on 2007-09-11
My resolution WAS 1680 x 1050, but now it's set at 1200 x 768. For some reason, after getting that 'Your session lasted less than 10 seconds' error, it kept the 1680x1050 BUT was really big, imagine using something like a 640 x 480... and only a portion of the desktop fit on my monitor (I didn't have access to the bottom panel, and i could only see part of my top panel). I changed it and it's usable at the resolution I'm using. But... I don't particular like it, and when I went to go change it back through the System -> Preferences -> Screen Resolution, there was no option for the 1680 x 1050, even though my xorg.conf has the entry "1680x1050". Does that make sense?

---

### Post by reckless2k2 on 2007-09-11
ok can you get in regular though or are you still in the failsafe? you'll need to reboot? don't bother restarting x...just reboot. 

after that, let me know if you're back in. i need a xorg.conf post as well for the other gimmick. if you can't get in either...have you tried editing xorg.conf and changing driver?

---

### Post by akiratheoni on 2007-09-12
Okay I'm in the regular session right now so that works. Still getting the .drmc error but that's not a big deal for now I guess, I just want to fix the resolution. 

xorg.conf file:

[http://www.zantherus.com/files/xorg.txt](http://www.zantherus.com/files/xorg.txt)

---

### Post by reckless2k2 on 2007-09-12
i think the driver is intel (i810). query the forums on 915 resolution and that should fix it. i think the error you are getting is because it drops to default res or "best" res because the gimmick isn't in there. 915 resolution.

---

