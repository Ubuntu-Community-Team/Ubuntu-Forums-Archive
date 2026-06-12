---
title: "KDE 3.5 broken after update!!!"
date: 2005-12-13
forum: General Help
---

### Post by martamius on 2005-12-13
I am running kubuntu breezy, with kde 3.5 installed.
Today I just ran my routine update, and adept updateded many of the kde libs from "breezy1" to "breezy2". 
after the update, i started getting access denied errors for my ~/.kde directoy. after a reboot, i was no longer able to log in at all. KDM starts up fine, but when i log in, i get an "could not start kstartupconfig. Check your installation" error. It then kicks me back to KDM.
When I log in under failsafe, I get "cannot save settings" and "Can't setup DCOP communication" errors before getting the console.
I thought perhaps my user directory was corrupted, so I created a new user. login in under this new user didn't help.

I noticed that I can run kicker if i do a sudo kicker while in failsafe mode.

Anybody else experience this after updating?

Is there a fix?

PLEASE HELP!!!!

---

### Post by amd-64 on 2005-12-14
Could it be that the user is no longer owner of some files in .kde

You can check the permissions manually using 
> ls -lR .kde | grep root

Change ownership of all files in .kde to the user of the account

From the parent folder (substitute user name below)
> sudo chown -R <user>:<user> .kde

:)

---

