---
title: "How do you end a non-responsive program?"
date: 2005-08-08
forum: Desktop Environments
---

### Post by Curlydave on 2005-08-08
What's the Ubuntu equivolent of ctrl+alt+delete. Xmms is completely frozen, adn right-clicking on it's taskbar icon and hitting close isn't doing the trick.

---

### Post by Sam on 2005-08-08
Open a terminal, run [font=monospace]xkill[/font] and click on the non responsive program.

Or the Gnome applet 'Force Quit' does the same.

Or in a terminal type [font=monospace]kill <app name>[/font].

---

### Post by jasmuz on 2005-08-08
Applications -> System tools ->System Monitor

or 

alt+f2, then type xkill, and click on the program that is being naughty

---

### Post by wellery on 2005-08-08
[QUOTE=Sam]Open a terminal, run [font=monospace]xkill[/font] and click on the non responsive program.

Or the Gnome applet 'Force Quit' does the same.

Or in a terminal type [font=monospace]kill <app name>[/font].[/QUOTE]

I thought kill accepted a process id and killall accepted an app name.

If you wish to use kill then use ps aux to view the processes and type

```
kill processID
```

---

### Post by Curlydave on 2005-08-08
Ahhh, thanks! I just ended up rebooting which did the trick.

New question: How do you get Xmms to continue to the next song after it finishes one? It just kinda stops.

---

