---
title: "I need to install something from Synaptic"
date: 2005-03-27
forum: Desktop Environments
---

### Post by Ricapar on 2005-03-27
I don't know how or why, but my CD Rom drive is dead now. I tested it on anohter computer, no worky. Won't even want to boot from it either, so I'm assumming it's fried.

I'll fix the CD Drive later, but right now I'm trying to install something from Synaptic, and it is asking for me to put the Warty CD in the CD drive.

Is there a way I can still install the packages by downloading from somewhere, and not using the CD?

If it matters, I'm trying to install esound.

---

### Post by astoltz on 2005-03-27
Start Synaptic.  

Then under the settings menu, go to Repositories.  This will bring up a dialog with several repositories listed.  

Uncheck the cdrom, and check the one that has Warty (I'm assuming you're using warty) as the Distribution and "main restricted" as the sections (you'll have to click on the different entries to see the details).

Once you have the on-line repository enabled, click OK.

Then from the menu, click Edit then Reload Package List.  It'll take a minute to retrieve all the package info.

Now you should be able to search for esound and it'll install from the on-line repository instead of the cd-rom.

---

### Post by bored2k on 2005-03-27
Read [Q: How to add extra repositories?](http://ubuntuguide.org/#extrarepositories) for a different approach on this ;) .

---

### Post by Ricapar on 2005-03-27
Yay, thanks, it worked!

Now to find myself a new CD drive :(

---

