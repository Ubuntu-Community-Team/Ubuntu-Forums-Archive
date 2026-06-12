---
title: "Gnome vs Kde?"
date: 2005-09-07
forum: Desktop Environments
---

### Post by earobinson on 2005-09-07
Not sure where to put this, but i heard that kde was less of a resource hog than gnome is this true? where can i find a good comparision of kde gnome and others?

---

### Post by mcmuffy on 2005-09-07
To be honest I have never seen a Gnome vs KDE comparison that does not turn into a flame war. I think your best bet is to try them both and go with the one you prefer.

---

### Post by Lord Illidan on 2005-09-07
This was in the recent linux format..

Konqueror using 10 mb, versus Nautilus using 17 mb..

so I think KDE is less resource hungry seeing that a simple GTK app like Nautilus takes up 7 mb more than Konqueror which is a browser too..

---

### Post by dbott67 on 2005-09-07
A few months ago, I installed a number of different WMs (KDE, XFCE, fluxbox/blackbox, IceWM and enlightenment).  I did a very crude memory test (free -m -t -o) while running Firefox and one terminal window.  Here's what I found:

**_Gnome 2.10 - Firefox (1 tab open) and 1 Terminal Window_**
```
dbott@tecra8000:~$ free -m -t -o

             total       used       free     shared    buffers     cached

Mem:           250        245          5          0         13         56

Swap:          352         64        288

Total:         603        310        293
```

**_Gnome 2.10 - No Apps running_**
```
dbott@tecra8000:~$ free -m -t -o

             total       used       free     shared    buffers     cached

Mem:           250        245          5          0         12        124

Swap:          352         21        331

Total:         603        266        337
```

**_KDE 3.4 - Firefox (1 tab open) and 1 Terminal Window_**
```
dbott@tecra8000:~$ free -m -t -o

             total       used       free     shared    buffers     cached

Mem:           250        246          4          0         18        116

Swap:          352         21        331

Total:         603        267        335
```

**_KDE 3.4 - No Apps running_**
```
dbott@tecra8000:~$ free -m -t -o

             total       used       free     shared    buffers     cached

Mem:           250        213         37          0         20        118

Swap:          352         21        331

Total:         603        234        368
```

**_XFCE4 - Firefox (1 tab open) and 1 Terminal Window_**
```
dbott@tecra8000:~$ free -m -t -o

             total       used       free     shared    buffers     cached

Mem:           250        206         44          0         18         86

Swap:          352         21        331

Total:         603        227        375
```

**_XFCE4 - No Apps running_**
```
dbott@tecra8000:~$ free -m -t -o

             total       used       free     shared    buffers     cached

Mem:           250        172         77          0         18         86

Swap:          352         21        331

Total:         603        194        409
```

Anyhow, in my opinion, both KDE and Gnome perform about the same on my P2-300 w/256 MB RAM, as soon as you open any application.   XFCE is nice & lightweight, however, I still prefer Gnome (it seems much more intuitive to me than KDE and the others).  Blackbox, fluxbox and enlightenment are all very fast, but as soon as I run something fairly memory-hungry (like Firefox), my computer slows down.

I have recently installed Opera, and it vastly out-performs Firefox.  My computer runs much faster with Gnome & Opera than it ever did with Firefox (under similar circumstances).


-Dave

---

