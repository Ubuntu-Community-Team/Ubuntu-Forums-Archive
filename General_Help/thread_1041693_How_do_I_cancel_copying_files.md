---
title: "How do I cancel copying files?"
date: 2009-01-16
forum: General Help
---

### Post by orangecakez on 2009-01-16
I was browing some files in a file browser (the one that comes with Xubuntu), and I accidentally dragged a 1 TB folder into another folder and it started copying the files and now my computer is VERY slow (it took me 5 minutes just to open up the browser and go to this website). How do I cancel this? I don't want to wait days for this to finish copying

---

### Post by dcstar on 2009-01-16
> **orangecakez said:**
> I was browing some files in a file browser (the one that comes with Xubuntu), and I accidentally dragged a 1 TB folder into another folder and it started copying the files and now my computer is VERY slow (it took me 5 minutes just to open up the browser and go to this website). How do I cancel this? I don't want to wait days for this to finish copying

You can manually kill the process, there are various ways to do this (command line, System Monitor etc).

---

### Post by orangecakez on 2009-01-16
> **dcstar said:**
> You can manually kill the process, there are various ways to do this (command line, System Monitor etc).

How do I find the process? I did "ps aux | grep foldername" but it didn't return anything with my folder being copied name in it

---

### Post by taurus on 2009-01-16
The command for copy would be **cp** so you would want to look for that near the end of this output.

```
ps -A
```

---

### Post by ByteJuggler on 2009-01-16
> **taurus said:**
> The command for copy would be **cp** so you would want to look for that near the end of this output.

```
ps -A
```

I'm pretty sure a drag-drop with nautilus does not happen via "cp", so looking for it in the process list it likely not going to work. 

[I]**_!!Edit: The following will only work on *Ubuntu*, as it assumes you're using Gnome/Nautilus.  I'll have to check what the equivalent on Xubuntu is!!_**
[/I]
You might however want to try killing the nautilus file-system explorer that's doing the copying.  Press alt-f2, then enter:

```
killall nautilus
```

This will kill the filesystem any explorer windows running (including any copying tasks), after which it should restart automatically.

---

