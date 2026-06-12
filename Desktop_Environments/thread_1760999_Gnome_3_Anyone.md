---
title: "Gnome 3 Anyone?"
date: 2011-05-17
forum: Desktop Environments
---

### Post by Nerotriple6 on 2011-05-17
So while I await a power splitter for my computer, I get bored by Gnome 2.. I have tried to install Gnome 3 three times but it crashed on start-up (maybe because of language settings I dunno..).

Currently I have no optical drive up and running and I was going to postpone installing Gnome 3 and Shell until I did, but the store is taking an awful long time processing my order and thus I grow impatient....

No fallback.. Little chance of success.. I wanna try again, even though I may have to fiddle with my hard drives to install Ubuntu again...
Does Gnome 3 run with non-English languages (Norwegian)? Will it run okay on my PC if I get it to run at all?

Pentium 4
1024 MB RAM
Radeon HD 4650 (1024MB)

---

### Post by ratcheer on 2011-05-17
I don't know about the language question. But how are you installing Gnome 3?

Make sure 11.04 is fully updated
Add the Gnome3 Team PPA
sudo aptitude update
sudo aptitude dist-upgrade (do this from gnome panel, not Unity)

Make sure gnome-themes-standard is installed.

It should work. I have done this several times without trouble. Unless there is something strange about your system (or, maybe it is the language thing).

Tim

---

### Post by Nerotriple6 on 2011-05-18
The last time I tried it asked me to update my folder names, from Norwegian to English. To which I said no and it crashed.

I removed the accessibility themes all the times I tried. But that's basically how I did it.

Add PPA
sudo apt-get update then upgrade, then dist-upgrade.. or something I don't remember exactly.

Will your way install Gnome Shell as well?

---

### Post by ratcheer on 2011-05-18
> **Nerotriple6 said:**
> The last time I tried it asked me to update my folder names, from Norwegian to English. To which I said no and it crashed.

I removed the accessibility themes all the times I tried. But that's basically how I did it.

Add PPA
sudo apt-get update then upgrade, then dist-upgrade.. or something I don't remember exactly.

Will your way install Gnome Shell as well?

Again, I do not know anything about bugs or problems when using other languages. But, it does seem that it is causing at least some of your problems.

The last couple of times I did the upgrade, gnome-shell was installed. The first time, I think I recall having to install it after the upgrade completed. It seems to me that the PPA is getting better and better at having everything done completely via the dist-upgrade. But, I haven't done it in the past few weeks.

I am getting a new PC in a few days, so I will be doing it again, soon. I can't abide Unity.

Good luck,
Tim

---

### Post by NormanFLinux on 2011-05-18
Every one is waiting til Oneiric Ocelot. Its just too buggy right now.

Downstream distros are sticking with the tried and true GNOME 2.32 until the bugs in GNOME 3 get weeded out and it becomes a functional desktop.

---

### Post by Nerotriple6 on 2011-05-18
Thanks for the input, both of you.

I will wait until I get my power splitter, I probably will reinstall Ubuntu anyway. Maybe I will try out Fedora again. I have been reading and yes, there seem to be a bunch of bugs.

Oneric, still 5 months away. Well least I have an OS that works.

---

### Post by ManualSparrow on 2011-05-18
It's been mentioned that upgrading from Xubuntu 11.04 works better because it has fewer conflicting Gnome dependencies. You could try that.

---

### Post by Nerotriple6 on 2011-05-18
Interesting, thanks. Will have to be when I get my order from multicom.. Still haven't processed it though..
Time to send angry email.:mad:

---

### Post by JohnSS2 on 2011-05-18
just available for Ubuntu 11.04 via PPA :)

---

