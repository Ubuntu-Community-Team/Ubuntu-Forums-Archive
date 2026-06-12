---
title: "Is there a program to edit Windows Registery"
date: 2009-06-16
forum: General Help
---

### Post by skozzy on 2009-06-16
Is there a program available on linux that will allow me to load - edit - save the registry on a windows computer (WinXP in this case).

A friend dropped off her computer that got a trojan/virus that shuts down her normal virus checker and does many odd things, I backed up her files using an ubuntu live cd, then deleted the temp files and system restore stuff, but now I need to access it's registry to remove auto running software and unknown services.

---

### Post by billgoldberg on 2009-06-16
> **skozzy said:**
> Is there a program available on linux that will allow me to load - edit - save the registry on a windows computer (WinXP in this case).

A friend dropped off her computer that got a trojan/virus that shuts down her normal virus checker and does many odd things, I backed up her files using an ubuntu live cd, then deleted the temp files and system restore stuff, but now I need to access it's registry to remove auto running software and unknown services.

I don't know, but wouldn't it be easier to just do a format and clean install?

You already have her files backed up.

---

### Post by SOULRiDER on 2009-06-16
From
[http://en.wikipedia.org/wiki/Windows_Registry](http://en.wikipedia.org/wiki/Windows_Registry)

> It also possible to edit the registry under Linux using the opensource Offline NT Password & Registry Editor to edit the files.[14]
[http://home.eunet.no/pnordahl/ntpasswd/](http://home.eunet.no/pnordahl/ntpasswd/)

I dont know if its exactly what you need though.

---

### Post by skozzy on 2009-06-16
[billgoldberg] Normally a fresh install is what I would do, and most likely will. But it's a good opertunaty to try something new.

I already found the trojans and disabled them, many of the hard to stop trojans follow the same principle of how they get into the system where they reside, so finding them is only a small challange, so I got the system to boot clean and the installed virus checker is grinding away right now, best I can tell it is safe enough to use.

I got the trojans backed up as well and will post them off be added to a few known name virus checker places so they can do what is needed to help save some other poor soles life.

But that offline bootable cd with a registry editor I am downloading now and will try it shortly. Thanks for the link [SOULRiDER]

---

### Post by Taras.M.K on 2009-06-16
Being in similar situation I used to load from linux liveCD and deleted all files from temps and restore, as you did. Then I checked system dirs (windows, system32 and some more in the last one) for new files and moved every new file (withing couple of days) to another location. Then I was able to boot cleanly to that system and clear registery, do a system scan and all. If you can do in a similar way, you will not need any registry editor and "hijackthis" will help you to clean any garbage.

---

### Post by skozzy on 2009-06-16
Yeah exactly what I have done with exception to also looking over the whole system to files with current or most recent dates, led me to two folders in the docs and settings/all users/applictions/ where two folders and the files matched what I later found in the registry to run as the system loads.. 

The linux boot cd to edit the registry works ok, but the registry editor is not easy to use.

Well thanks for you helps guys, I will make this thread as solved.

---

### Post by skozzy on 2009-06-16
well I can't change the title to solved or find a button to click on to do it. Oh well.

---

