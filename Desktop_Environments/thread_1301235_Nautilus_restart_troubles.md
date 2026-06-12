---
title: "Nautilus restart troubles"
date: 2009-10-25
forum: Desktop Environments
---

### Post by Standing Stone on 2009-10-25
Hi Everybody

First time poster here, and also probably still to be counted among absolute beginners when it comes to matters linux ;)

Well, here's my problem. I am running Jaunty 64bit, actually everything works fine so far, but i have been noticing that Nautilus tends to eat up a lot of RAM if it's used to browse folders with tons of pics. So, i looked for a way to free up the RAM by flushing the cache w/o having to restart the system. I found the commands "nautilus -q" or "killall nautilus", which work fine where the flushing of the cache is concerned - the process is killed, the RAM freed. Now, restarting nautilus properly is another matter.

After killing nautilus, I still can access everything through the desktop bar (places). According to System Monitor, this calls up nautilus for as long as a given folder is open. If all folders are closed, no nautilus process is active. This is actually a good thing since it is easy on resources, but if nautilus does not run then the desktop is not drawn, leaving me with no icons and inactive right-click on the desktop area... not exactly what i want.

Restarting nautilus with "gksudo nautilus" presents me with a new desktop (default background - why not with my prefs? is this normal?)

Restarting nautilus with "nautilus" gives an error mentioning something along the lines of "cannot create monitor", but will open root folder and a nautilus process that will stay active as long as root folder is open.

Since i am not really proficient at using CLI (I stumbled over above commands in forums and just tried them out - what's to lose^^), I would be grateful for some hints of how to make nautilus perform the same way it does upon boot, meaning a restart with ALL the functionality restored. By the way, is it normal that if a program is called up in a Terminal, that said program will always die when the Terminal is exited? Can't they exist independently?

Thanks in advance for any help regarding these points :)

Cheers!

---

### Post by Standing Stone on 2009-10-30
*bump* 

no-one got an idea?

---

