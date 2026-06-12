---
title: "Steam won't open 14.04"
date: 2015-10-23
forum: Gaming &amp; Leisure
---

### Post by robert1132 on 2015-10-23
when I try to start steam nothing happens. 
This is what comes up when I type "steam" into the terminal:
> _@_-System-Product-Name:~$ steamRunning Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME is enabled automatically
/home/_/.local/share/Steam/steam.sh: line 756:  3602 Illegal instruction     (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$STEAMEXEPATH" "$@"
_@_-System-Product-Name:~$ 

---

### Post by jules-overtoom on 2015-10-23
same here, 
steam won't start after the latest steam update. 
> Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME is enabled automatically
/home/ /.local/share/Steam/steam.sh: line 756:  2800 Illegal instruction     (core dumped) $STEAM_DEBUGGER "$STEAMROOT/$STEAMEXEPATH" "$@"


---

### Post by efflandt on 2015-10-23
I posted that on the Linux Steam forum Oct 20 with a link to the github report about that and solution: [http://steamcommunity.com/app/221410/discussions/0/490123832541719729/](http://steamcommunity.com/app/221410/discussions/0/490123832541719729/)

There apparently was a steam beta release that inadvertently had an instruction that was only on newer cpus. The steam beta seems to be fixed now, or at least current steam beta works on my older i5.

So you might just try doing (note space between steam and --reset):```
steam --reset
```

---

### Post by jules-overtoom on 2015-10-24
thanks, that worked for me!

---

### Post by robert1132 on 2015-10-24
That cleared my library of downloaded games, is there a way I can restore them?

---

### Post by R33D3M33R on 2015-10-24
Settings > Downloads > Steam Library Folders > Add Library Folder > Browse to the folder where your games were installed

---

