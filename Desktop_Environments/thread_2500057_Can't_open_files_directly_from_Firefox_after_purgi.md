---
title: "Can't open files directly from Firefox after purging Xfce"
date: 2024-08-20
forum: Desktop Environments
---

### Post by TuxIsAwesome on 2024-08-20
A few days ago I installed Xfce and ended up not liking it.

I completely purged XFCE but upon doing so I have a weird issue with Firefox.

When prompted to open/save any file type if I click open, even though there is a correct program associated I will then get the following message following it

[https://ibb.co/FgvM2Z3](https://ibb.co/FgvM2Z3)

I am completely unsure how to fix this. It has persisted even after a reinstall of Ubuntu 

I am running Ubuntu 24.04 and Gnome 46. My /home is on a seperate partition.

---

### Post by &amp;KyT$0P# on 2024-08-20
> **TuxIsAwesome said:**
> I completely purged XFCE b

Could you please post the full entry from [FONT=monospace]/var/log/apt/history.log[/FONT] of the problematic purge?

> When prompted to open/save any file type if I click open, even though there is a correct program associated

To be clear, where is the correct program association set?  Firefox has its own associations for file types, which you can view/edit in [FONT=monospace][noparse]about:preferences[/noparse][/FONT] > General, "Files and Applications".

---

### Post by TheFu on 2024-08-20
Uh .... firefox has been installed by default as a snap program.  While the snap is setup to work with the default programs for the DE installed, I wouldn't be surprised if other programs don't work at all.

There are a number of solutions. The easiest is probably to remove the snap version of firefox and install a non-snap version - probably Firefox-ESR is the easiest from the Mozilla PPA.  You probably want to setup the PPA before purging the FF snap.

---

