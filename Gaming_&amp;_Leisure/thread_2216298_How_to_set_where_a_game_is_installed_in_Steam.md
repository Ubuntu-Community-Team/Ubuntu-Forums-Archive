---
title: "How to set where a game is installed in Steam?"
date: 2014-04-11
forum: Gaming &amp; Leisure
---

### Post by slovenskyweb on 2014-04-11
Is it possible in Ubuntu 14.04 to set the destination directory where  the currently installed (via Steam) game is stored? Is this possible in  Windows 8.1? Can I install games on NTFS from Ubuntu 14.04 Steam?

---

### Post by oldrocker99 on 2014-04-11
By default, Steam games either go into /home/username/Steam or /home/username/.Steam (a hidden directory). If you make a Steam directory in a different partition, and start Steam and go to View/Settings, you can define that directory as where Steam games go. I wouldn't have Windows and Linux games in the same Steam directory, but, if you have more than one directory enabled, Steam will ask where to install a game before you download it. Ubuntu has zero problems reading NTFS partitions, by the way.

---

### Post by meistersreign on 2014-04-12
Also when installing a game, for most you can specify where you want it installed. It will give you a list of options on a drop down menu, and you can choose from there or create a new location. Just make sure you have read/write permissions on the folder or partition especially if it's somewhere such as /games .

---

### Post by Ranko Kohime on 2014-04-14
> **oldrocker99 said:**
> By default, Steam games either go into /home/username/Steam or /home/username/.Steam (a hidden directory). If you make a Steam directory in a different partition, and start Steam and go to View/Settings, you can define that directory as where Steam games go. I wouldn't have Windows and Linux games in the same Steam directory, but, if you have more than one directory enabled, Steam will ask where to install a game before you download it. Ubuntu has zero problems reading NTFS partitions, by the way.
The correct default location of the Steam library is ```
~/.local/share/Steam
``` for reference.

---

### Post by oldrocker99 on 2014-04-14
Oops. Right you are, on my laptop. On my desktop, it was ~/Steam, until I moved it to another partition.

---

### Post by dianadavis on 2014-04-15
[COLOR=#000000]Valve and Canonical (the company behind Ubuntu) have worked together to bring the steam client to linux. You can either download Steam via Ubuntu Software Center or go to the Steam homepage and download the .deb file.[/COLOR][!!](http://www.ifgames.net/)[COLOR=#000000]

[/COLOR]

---

