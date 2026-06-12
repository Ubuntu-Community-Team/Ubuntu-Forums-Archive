---
title: "wine not installing or running utorrent"
date: 2009-06-19
forum: General Help
---

### Post by cyclobs on 2009-06-19
Hey guys,

so you guys know don't bother suggesting an alteritive program other then utorrent, i've tried the others and i don't like them :) thanks.

ok so a while ago i deleted and purged wine cause of all the crap that was installed on it so i decided to wipe it completely and start again, only issue i tho is that now i cannot run or install utorrent at all.

it works fine right until it actually has to copy and install the program. the process will remain in the tables but nothing happens.

can anyone help with this pleaseeee :)

---

### Post by pedro_orange on 2009-06-19
I don't understand what you're asking.

Copy and install what? uTorrent? 

Why don't you just download the setup.exe and do: 

```
wine setup.exe
```

---

### Post by cyclobs on 2009-06-19
ah, yeah it wont install utorrent. i've tried running it off from the terminal but that gave me nothing to why its not working

---

### Post by pedro_orange on 2009-06-24
Can you post the output of what happens when you try to run this please?

---

### Post by geirha on 2009-06-24
Note that purging the wine package will not remove the programs installed with wine. The programs installed with wine are located in the hidden folder ".wine" in your home folder. If you want a fresh start, remove/rename .wine.
```
mv ~/.wine ~/.wine.old
```

---

### Post by wojox on 2009-06-24
I use Bit Torrent for Linux  [http://download.bittorrent.com/dl/](http://download.bittorrent.com/dl/)
Make sure you grab the .gz file.
The .exe is for windows.

---

