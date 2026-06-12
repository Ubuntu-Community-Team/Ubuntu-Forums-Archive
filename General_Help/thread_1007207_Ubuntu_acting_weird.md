---
title: "Ubuntu acting weird"
date: 2008-12-10
forum: General Help
---

### Post by Bokorugro on 2008-12-10
I have various problems came out at the same time:

1, My Mozilla bookmarks disappeared, but the line containing them is still there ( so it wasn't me who disabled it )
2. Mozilla search does not work. The built-in search does not respond to anything.
3, All my saved passwords were forgotten by Mozilla.
4, Not all problems are Firefox-related: If I click the userswitcher-logout menu ( the running green lad ), all the shell ( i don't know if Linux users say shell ), or to say the menus, and everything except the background and the icons disappears, and I can't get it back, so I can't logout, or shut down my PC, just with the on-off hardware switch.
5, Updating crashed a few days ago.

The symptoms must be connected to each other, but I have no clue, for I am a new born baby in Linux-based OS-es.

Anyway, It worked fine for about 2 months, and I didn't do anything radical. I use 8.04, and have all updates installed.

Thanks

---

### Post by ajgreeny on 2008-12-10
I suspect you are using compiz desktop effects and that this is causing the loss of some of the items you mention.  I lost my FF bookmarks, and all my extensions as well to start with when I tried 8.10, but fiddling with compiz plugins got them back.  Open a terminal and type ```
metacity --replace
``` which will give you the old-fashioned no effects desktop, but may make all your desktop items reappear.  You may need to logout and back in again first, but it would not normally be needed.  You can then try to set the compiz plugins using compizconfig-settings-manager, which you can get from the repos using synaptic.

In future if it happens again, for what ever reason, instead of using the power button to shutdown, use the terminal and enter ```
sudo shutdown -h now
``` for a stop or ```
sudo shutdown -r now
``` for a reboot.  If necessary use Ctrl+Alt+F1 to get to a console and login for the same shutdown procedure.

---

### Post by tommy.sean on 2008-12-16
I am having similar problems.

"1, My Mozilla bookmarks disappeared, but the line containing them is still there ( so it wasn't me who disabled it )
2. Mozilla search does not work. The built-in search does not respond to anything."

Same here. Plus Firefox doesn't seem to be keeping track of my history. More importantly its simply closes (or crahes) randomly, specificly every time I visit youtube.

I have tried the "metacity --replace" command with no result. I have even tried removing compizfusion and reinstalling firefox. No luck.

Any ideas?

---

