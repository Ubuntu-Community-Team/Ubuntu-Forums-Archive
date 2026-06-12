---
title: "Tried to install awn, but..............."
date: 2008-02-07
forum: Desktop Effects &amp; Customization
---

### Post by Camrygrl on 2008-02-07
Followed this how to for installing awn:
[COLOR="Red"][http://ubuntuforums.org/showthread.php?p=2307772#post2307772](http://ubuntuforums.org/showthread.php?p=2307772#post2307772)
[/COLOR]
Then got this error when trying to get to synaptic:
[I]E: Type 'echo' is not known on line 56 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.[/I]

Can't get into update manager either: 
[I]Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'echo' is not known on line 56 in source list /etc/apt/sources.list, E:The list of sources could not be read.'[/I]

Help please :(

---

### Post by Tenken on 2008-02-07
It sounds like 'echo' somehow got printed to your sources.list. Open your sources list in a terminal:

```
sudo nano /etc/apt/sources.list
```

and check if your new repos have echo written in front of them, they should look like this:

```
deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
```

the run

```
sudo update
```

---

### Post by Camrygrl on 2008-02-08
> **Camrygrl said:**
> 

'E:Type 'echo' is not known on line 56 in source list /etc/apt/sources.list, E:The list of sources could not be read.'[/I]



found that file but how do I edit it?

---

### Post by Tenken on 2008-02-08
If you are comforitable using a terminal editor, you can use nano

```
sudo nano /etc/apt/sources.list
```

after you edit the file hit ctrl+x, then y, enter to save 

Or you can use gedit, hit alt+F2 and type

```
gksu gedit /etc/apt/sources.list
```

---

### Post by Camrygrl on 2008-02-08
we must have been typing at the same time...

it does say echo, how do I get rid of it?

Thank You!

---

### Post by Camrygrl on 2008-02-08
another lesson learned.  don't copy everything.
thank you very very much!

think I'll save this for another day

---

### Post by Tenken on 2008-02-08
EDIT: Too slow

---

