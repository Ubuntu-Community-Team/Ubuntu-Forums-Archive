---
title: "AWN and Emerald issuses after upgrade to Intrepid"
date: 2009-02-17
forum: Desktop Environments
---

### Post by Shelbsterina on 2009-02-17
Last night I upgraded from Hardy to Intrepid, and since then, I can't get Emerald window decorations to work, and my AWN won't show up. I have both commands set to run on startup, as I assume they still do, but I just don't see anything. The process for both appear to be running when I open system monitor.
Also, since I can't use AWN to keep track of open applications and switch between them, I added the bottom panel back, but none of the applications will show up there. I can live without this if I can get AWN working, though.

Help? Thanks in advance.

---

### Post by Tim Sharitt on 2009-02-17
You need to make sure the screen in composted. Hit Alt-F2 or open a terminal and enter:
```
compiz --replace
```

---

### Post by Shelbsterina on 2009-02-17
I tried that earlier and it got rid of my window borders completely. I did it again just now and it did nothing and the output in terminal was:

```
shelby@FluffyGonzales:~$ compiz --replace
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2562' found 
aborting and using fallback: /usr/bin/metacity 
/home/shelby/.themes/ish-purple/gtk-2.0/gtkrc:51: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/shelby/.themes/ish-purple/gtk-2.0/gtkrc:52: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/shelby/.themes/ish-purple/gtk-2.0/gtkrc:53: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.

```

---

### Post by Shelbsterina on 2009-02-18
I think something may be incompatible with my graphics card? I looked at my appearance settings, and desktop effects was set to "None". When I tried to set it to normal, I got a notification saying it couldn't be done.

---

