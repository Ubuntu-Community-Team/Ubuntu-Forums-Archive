---
title: "Mounted drives missing in 'Places'-Menu after dist-upgrade"
date: 2005-02-07
forum: Desktop Environments
---

### Post by stef65 on 2005-02-07
Hi all,

I upgraded from Warty to Hoary quite a while ago now and dist-upgrade now  on a regular basis. After the last dist-upgrade I missed my mounted drives on the desktop and in the Ubuntu 'Places' menu. They are still accessible in the computer:/// view in nautilus , but  I really like them to have in 'Places' (where they perfectly belong).
What I've found out is that this has something to do with the Hardware Abstraction Layer (HAL) and the dbus- daemon which seems not to be started with  the right configuration. 
The funny thing is if i reinstall the hal-package my 'media' and 'store' partitions appear again in 'Places' and on the desktop, but only until I reboot. Peeking in the install-script inside the hal-package showed me, that the HAL is restarted by the post-installation script, so I found that

[FONT=Fixedsys]
sudo invoke-rc.d dbus-1 restart
[/FONT]

fixes the issue after being logged in.
But I did not manage to find out how to modify the startup scripts that this happens automatically at startup. I looked into the conf-files in /etc/dbus and init.d but did not get a clue out of it.
Maybe some Warty heritage is messing things up here, anybody knows how to avoid restarting the dbus-daemon again everytime after startup?

Help appreciated,

Stef

---

### Post by Totzo on 2005-02-07
I have the same problem- seems to be an issue as they keep upgrading the hal pakages, I found a really messy fix was to put your command in the- sessions/ start-up programs, this returns a "failed to initialise hal" message but also does the job!

I'm sure there is a simple solution, let me know if you find one,

T

---

