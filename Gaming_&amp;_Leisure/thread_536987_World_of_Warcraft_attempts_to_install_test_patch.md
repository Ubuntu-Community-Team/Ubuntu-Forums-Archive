---
title: "World of Warcraft attempts to install test patch"
date: 2007-08-28
forum: Gaming &amp; Leisure
---

### Post by orionsbelt on 2007-08-28
I've been running WoW Burning Crusade under Wine for a couple of weeks now with no problems.  However, last week the program has been hanging on the "downloader" part of the login screen.  The first time, I tried "xkill" and restarted WoW.  This would let me logon to the game, but later on I would get an error message (in a separate window).  However, the actual gameplay at the time of the error message was fine.

At first, I thought I just needed to manually install a patch, which I did by running BackgroundDownloader.exe.  The download went fine, but it hung on the install initially.  Finally my roommate (with basically the same configuration, setup, and issue) manged to get the the patch to download (though not install it seems).  The patch was labeled as "WoW-2.1.3-to-2.2.0-enUS-Win-patch".

This part seems to have similar issues to [http://ubuntuforums.org/showthread.php?t=497654&highlight=world+of+warcraft+dowload%2A]("http://ubuntuforums.org/showthread.php?t=497654&highlight=world+of+warcraft+dowload%2A") 

But here's the weird part - the patch is supposed to be for the test realms.  (In other words, it's not available for public consumption yet.)  I've had to use the same workaround to get the game to work at all.  My roommate has just been running wow, waiting for the "downloading" hang, "xkill"ing it, then rerunning wow (eventually, when the error message my roommate would just close the error window and move on.

I probably need to delete the "new" patch, but the background downloader seems to want to continue downloading regardless.

Any suggestions?  Should I downgrade my version of Wine as suggested in the other post?  Is anyone else having this problem?

---

### Post by orionsbelt on 2007-08-30
Well, now it's working, after about an hour of fiddling.

I noticed that the latest version of wine (0.9.44) was out, so I naively decided that they might have fixed the problem.  (Note: I found out later that the latest version of Wine may have *more* bugs, as it's released after two weeks and not necessarily stable.)  Unfortunately, with the new version WoW crashed on startup.

I then decided to try the remedy suggested in [http://ubuntuforums.org/showthread.php?t=497654&highlight=world+of+warcraft+dowload%2A](http://ubuntuforums.org/showthread.php?t=497654&highlight=world+of+warcraft+dowload%2A).

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

For those of you who don't feel like clicking the link, it involved:

"* There is an issue with Wine 0.9.40 that will not allow the user to run a WoW Patch installation. This is not yet a documented bug on the official Wine AppDB site.
* The workaround is to downgrade to Wine 0.9.39 (or below).
* To downgrade, use your terminal to uninstall your current version of Wine. This will NOT delete any of your files under Wine, just the Wine program itself.
* Install version 0.9.39.
* Restart the Patch installation.
* Play WoW!"

Also, older versions of Wine can be installed here: [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

I tried playing WoW under 0.9.39, but experienced problems with framerate, resizing the window, etc.

Since WoW worked under 0.9.43, I decided just to switch back to that.  ("xkill"-ing the program isn't that much of a problem...)

For some reason, I am no longer getting the downloader error message.  I can now log directly into WoW.  However, my roommate tried downgrading from 0.9.44 directly to 0.9.43 - and still has the error message.

Good luck to anyone working on this issue!  I hope I don't have trouble installing patches in the future, or it's back to 0.9.39 for me...

---

### Post by orionsbelt on 2007-08-30
Sorry for duplicate posts, for some reason I could not find this when I was having the initial problem...try here:

[http://ubuntuforums.org/showthread.php?t=533164&highlight=wine+update](http://ubuntuforums.org/showthread.php?t=533164&highlight=wine+update)

---

