---
title: "HALO under wine, Crossover, ect?"
date: 2007-04-26
forum: Gaming &amp; Leisure
---

### Post by unixdotseth on 2007-04-26
I have tried to install Halo the pc game under wine, and crossover

they both gave me the same error 

pidgen.dll

is there anyway to install halo inside ubuntu?

---

### Post by justin whitaker on 2007-04-26
It looks like maybe. 

[http://appdb.winehq.org/appview.php?iVersionId=2720](http://appdb.winehq.org/appview.php?iVersionId=2720)

According to the thread there, it's rated as Garbage with Feisty, but supposedly runs on WINE on other versions of Ubuntu and Linux.

Supposedly, it works with Cedega with some command hacks:

[http://cedega.com/forum/viewtopic.php?t=7892&highlight=halo](http://cedega.com/forum/viewtopic.php?t=7892&highlight=halo)

According to the Unofficial Transgaming Wiki, it's a no go.

[http://cedegawiki.sweetleafstudios.com/wiki/Halo](http://cedegawiki.sweetleafstudios.com/wiki/Halo)

That data looks a little old though.

It's not known to run with Crossover.

---

### Post by acracker on 2007-06-10
you need to get a .dll called mfc42.dll and put it in the /home/$USER/.wine/drive_c/windows/system32 folder. You can find this .dll in any standard Windows 2000 or XP system32 folder or you can download it from here:
[http://www.dll-files.com/dllindex/dll-files.shtml?mfc42](http://www.dll-files.com/dllindex/dll-files.shtml?mfc42)

---

### Post by The Noble on 2007-06-10
If you follow the guide on the appdb site you can install it with no problems. It also looks like halo is getting really close due to all of the DX9 fixes from the wine devs. Someone using the CVS version has halo working as gold right now. Either wait for the next release or compile the CVS.

---

