---
title: "Major slow down that leads to crash."
date: 2006-01-03
forum: Desktop Environments
---

### Post by nxn on 2006-01-03
I'm starting to get clueless, every day I randomly get a slow down that almost completely stops the clock (sometimes it even goes back a second in time) that will last until the system halts from me trying to find the problem. It's so bad it takes at least 3 to 5 minutes just to start the terminal and around two minutes to start 'top'.

I don't think it's an issue with X since when the slow down happens I can still move the windows smoothly and type in gaim windows without any problems. I can even send messages and the person I'm talking to will get them and can reply (the time shown next to them increases 3 seconds every 5 or so minutes). Shutting down X does not help and the system is still slow. For example it still takes the same amount of time to start 'top'. I swearched the forumes last night and saw that killing gam_server might helpt, I tried that today and no it didn't help me.

I have no clue what it could be, especially since the cpu usage doesn't go up at all, it just stays at around 0-3% as if it's idle. I thought it was an issue with the hd and dma mode but I set all that up today and yet the slow down still happened. System logs do not show anything that's not normal.

The only way I know to get out of it is holding down the power button until it dies.

Any ideas?

---

### Post by nxn on 2006-01-04
Anyone know what 'hpiod' is and how to get rid of it? I think it might be causing the problem somehow.

---

### Post by GrumpyBob on 2006-01-04
[QUOTE=nxn]Anyone know what 'hpiod' is and how to get rid of it? I think it might be causing the problem somehow.[/QUOTE]

It might be an HP printer driver - I did a quick google search which brought up hpiod bug reports.  Mind you, I'm none the wiser - perhaps you've installed an HP printer driver?

Robert

---

### Post by nxn on 2006-01-04
[QUOTE=GrumpyBob]It might be an HP printer driver - I did a quick google search which brought up hpiod bug reports.  Mind you, I'm none the wiser - perhaps you've installed an HP printer driver?

Robert[/QUOTE]
No, didn't install any printer drivers, I don't have a printer, and this install is only like two weeks old so I think it's something that must have been there from the start.

---

### Post by nxn on 2006-01-05
Allright, and that didn't help it. Can someone give suggestions where to look for the cause, because I'm all out of ideas and this needs to be fixed before I move.

---

### Post by winlux on 2006-01-05
I do suspect the hpiod is in fact the hp print drivers. I fyou shut down ububtu you can actually see it displays the hp print server shutting down. It is automatically installed with ubuntu. I had a problem where my system slowed down as well. I found that if I disable the text under the buttons in nautilus the system does not slow down anymore... I am not sure this is what your problem is but it sure worked for me. Give it a try and let me know.

Click System -> prefs -> menus & toolbars then change  Toolbar button labels to icons only. I have not played around with the rest of these options to see if they have any effect. Good luck

---

