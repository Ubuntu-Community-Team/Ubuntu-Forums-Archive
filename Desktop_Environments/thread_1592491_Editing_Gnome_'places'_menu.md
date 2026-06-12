---
title: "Editing Gnome 'places' menu"
date: 2010-10-10
forum: Desktop Environments
---

### Post by Pedricko on 2010-10-10
I am running Ubuntu 10.04 with Gnome as my desktop enviroment.

I used Wubi to install from my laptop's default OS, Vista. I keep most of my media on the Windows partition, mostly for ease of use - such as streaming a movie through my xbox etc

I would like to know if there is a way to edit the Gnome 'places' menu to have Music, Pictures etc direct to my /host/users equivalent.

---

### Post by demosthenese on 2010-10-10
Edit ~/.gtk-bookmarks.

---

### Post by Pedricko on 2010-10-10
> **demosthenese said:**
> Edit ~/.gtk-bookmarks.

Forgive me, I'm quite the noob - could you make that any clearer?

---

### Post by demosthenese on 2010-10-10
Open a terminal and enter:

```
gedit ~/.gtk-bookmarks
```

The file contents will look something like:

```
file:///home/user/Documents Documents
file:///home/user/Download Download
file:///home/user/Music Music
file:///home/user/Pictures Pictures
file:///home/user/Videos Videos
```

Each line is a pair - file location followed by display name.

Change the file path(s) to the location(s) you want.

Possible simpler GUI alternative:
It is a while since I used Nautilus but I think you can just drag file locations on to the bookmark list to add them. You can also remove and rename bookmarks on the right click menu.

---

### Post by heyandy889 on 2010-10-12
Sweet and merciful Jesus. That was so much easier than I thought. At first, I couldn't figure out why right-clicking didn't help. Then, I searched the forums and there was something about editing .desktop files. It sounded very involved. I am glad that the solution is editing a well-organized text file.

---

