---
title: "Can't update Ubuntu! = ("
date: 2009-01-16
forum: General Help
---

### Post by JakeWatkins on 2009-01-16
I can't update Ubuntu because of ```
Failed to fetch http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/source/Sources.gz  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```

I edited a file a while ago... I think I was trying to get a program.. but I don't remember the file I edited.. now I can't update.

---

### Post by damis648 on 2009-01-16
What version of Ubuntu are you using?

---

### Post by orlox on 2009-01-16
That shouldnt affect your update, the thing that happens is that you enabled some repositories that cant be found.

If you erase the corresponding lines in /etc/apt/sources.list (does with tuxfamily that claim error) everything should be nice and pretty again!

---

### Post by JakeWatkins on 2009-01-16
I'm using 8.10 = ]

> **orlox said:**
> That shouldnt affect your update, the thing that happens is that you enabled some repositories that cant be found.

If you erase the corresponding lines in /etc/apt/sources.list (does with tuxfamily that claim error) everything should be nice and pretty again!

Apparently... ```
bash: /etc/apt/sources.list: Permission denied
```

---

### Post by damis648 on 2009-01-16
Okay, head over to System>Administration>Software Sources
and go to the third party tab and remove the two offending repositories you posted earlier.

---

### Post by orlox on 2009-01-16
sources.list need to be edited with root permission:

```
gksudo gedit /etc/apt/sources.list
```

That should open a text editor with the file open

---

### Post by 2hot6ft2 on 2009-01-16
> **JakeWatkins said:**
> I can't update Ubuntu because of ```
Failed to fetch http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://download.tuxfamily.org/syzygy42/dists/feisty/avant-window-navigator/source/Sources.gz  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
```

I edited a file a while ago... I think I was trying to get a program.. but I don't remember the file I edited.. now I can't update.
Looks like you edited your sources.list file. Easy way to find out is to open a terminal like you did in the first place to edit it.
Applications>Accessories>Terminal
And just use the up arrow key to go back thru the commands you entered to the one that with sudo gedit the other option is to just edit the file and remove those lines from it.
```
gksudo gedit /etc/apt/sources.list
```
and remove the lines that start with
[http://download.tuxfamily.org/](http://download.tuxfamily.org/)
from the list.

---

### Post by orlox on 2009-01-16
Also, im guessing you were trying to install the avant-window-manager

If you want to do this, its pretty simple:
-Open the synaptic package manager under System->administration->Synaptic package manager
-Under configuration->repositories mark all the tickets that appear on the window that opens and press ok
-search for avant-window-manager and install it
-Now avant is listed under applications->accesories

If you want to make it open at startup, go to system->preferences->sessions and press add to add a new startup progam, you just need to put avant-window-manager under commands.

---

### Post by JakeWatkins on 2009-01-16
> **damis648 said:**
> Okay, head over to System>Administration>Software Sources
and go to the third party tab and remove the two offending repositories you posted earlier.


That fixed it. = ]]

Thanks a bunch!!

---

