---
title: "cant get lx doom to work."
date: 2007-02-06
forum: Gaming &amp; Leisure
---

### Post by techno-mole on 2007-02-06
Hello.
I have been trying to get lx doom  to run, thats the lx doom that you can install by going through, applications/add/remove, the game appears to be there, but when i click on it nothing happens ? 
ive read various posts and looked at various posts but nothing has helped.
any help will be appreciated.
cheers.

---

### Post by lukew on 2007-03-05
> **techno-mole said:**
> Hello.
I have been trying to get lx doom  to run, thats the lx doom that you can install by going through, applications/add/remove, the game appears to be there, but when i click on it nothing happens ? 
ive read various posts and looked at various posts but nothing has helped.
any help will be appreciated.
cheers.

If you click somewhere and you get no menu item up it means there is a traceback. Try running the application from the terminal and see what error message appears.
```

llxdoom -iwad /usr/share/games/freedoom/doom2.wad
```

---

### Post by lukew on 2007-03-06
I could not get llxdoom to work either. I ended up switching to lxdoom.

Install lxdoom lxdoom-sndserver

Run with lxdoom or lxdoom -sndserv

---

