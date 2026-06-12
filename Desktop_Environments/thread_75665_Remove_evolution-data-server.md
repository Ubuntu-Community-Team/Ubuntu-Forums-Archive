---
title: "Remove evolution-data-server?"
date: 2005-10-14
forum: Desktop Environments
---

### Post by 12quality on 2005-10-14
I use thunderbird, and evolution has all of the processes that automatically run all of the time.  Under Hoary I was able to remove Evolution completely.  But before I "dist-upgrade" ed, I added evolution so that I could have the ubuntu-desktop metapackage installed for the upgrade.  Now that I am in Breezy, I removed evolution, but I can't remove evolution-data-server. It still has a task list popping up under the calendar when I click on the time applet.  In addition, it uses up RAM.  When I try to remove evolution-data-server, Synaptic tells me it is going to remove about 10 different packages.  I think these may just be meta packages, but isn't it bad to remove all of those, anyway?  What do I do?

---

### Post by Ampersand on 2005-10-14
There's no problem removing meta-packages. They don't contain anything, but just depend on other packages so you won't lose any applications by uninstalling them.

If you list what it wants to remove here, someone should be able to tell you whether it's safe.

---

### Post by Wolki on 2005-10-14
Don't remove evolution-data-server, it's a core gnome component and other parts in gnome depend on it being there. removing it will effectively remove gnome.

It's also not a big memory loss; the little volume applet on the panel takes far more real ram than evolution-data-server.

---

### Post by ubuntu-mike022465 on 2006-02-17
Is there any way of stopping evolution-alarm-notify, evolution-data-server and evolution-exchange-storage from starting up when Gnome does?  That way no one has to try to uninstall the packages, because I'm in the same boat, I use thunderbird as my default email client, and have no wish to use evolution at all.  Any thoughts would be appreciated


M.

---

### Post by pkoufalas on 2006-05-03
I'd also like an answer to this.
The system monitor app tells me that evolution-alarm-notify, evolution-data-server and evolution-exchange-storage together take up ~140MB of memory (49MB, 56MB, 34MB resp.)
This is enough to cause me problems with octave (probably a bug in octave) when working on large data files. I've already shut down other running programs to free up RAM...I only have 512MB of RAM.
I'll be happy enough to stop evolution from running, rather than remove it entirely.
Why does Gnome depend on evolution data server?? (see earlier posts).
Advice appreciated.

---

### Post by Wolki on 2006-05-03
[QUOTE=pkoufalas]The system monitor app tells me that evolution-alarm-notify, evolution-data-server and evolution-exchange-storage together take up ~140MB of memory (49MB, 56MB, 34MB resp.)[/QUOTE]

And it's lying. If you want values that are closer to the real ram they use, look at the RSS size in the system monitor (this is also the only one that will be shown by default in dapper). And even that is thechnically not the correct amount of memory, since it includes memory shared by different processes, but it's difficult to calculate the exact amount.

Eg., on my dapper box, e-a-n, e-d-s and e-e-s are taking 84,8 74,3 and 25,9 MB of virtual RAM, but only 10,3 3,9 and 2,7 real ram. And most of that is shared between processes.

---

### Post by tombeharrell on 2006-08-01
I'm running Dapper, Evolution is set up with an IMAP account, and an Exchange account.

During half a day, the evolution-data-server can eat over 500MB, Evolution 200-300, and there hits a point where it maxes out and the disk thrashes, and the desktop is completely unresponsive with the mouse hardly responding. (I have 1GB RAM) 

I have to keep an eye on my free memory (system monitor panel applet) and restart Evolution every hour or so, this brings it back down to about 275MB (e-d-s) and 180MB Evolution.

Have tried removing the Exchange account and adding the server as another IMAP one but it still happens. This isn't good, it was fine in Breezy. :(

---

