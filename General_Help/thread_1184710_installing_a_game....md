---
title: "installing a game..."
date: 2009-06-11
forum: General Help
---

### Post by prabhanjan2906 on 2009-06-11
I am new to linux. i have downloaded a game called sauerbraten which  has an extension .tar.bz2. how do i install the game? its about 344mb. pls help me out......!

---

### Post by gradinaruvasile on 2009-06-11
That is an archive. What is inside cannot tell. Might be binaries, might be source code that needs to be compiled. I would advise to stay with the .deb format (standard debian/ubuntu installable package format). 

Some games here : [http://www.playdeb.net/available_games.html]("http://www.playdeb.net/available_games.html")

You also can install games from the application add/remove menu. Just make sure select all available applications and search. Sauerbraten is there too.

---

### Post by andersbk on 2009-06-11
> **prabhanjan2906 said:**
> I am new to linux. i have downloaded a game called sauerbraten which  has an extension .tar.bz2. how do i install the game? its about 344mb. pls help me out......!

You could just install the binaries from the ubuntu repos. Either use synaptic to search for it and install (the gui method), or open a terminal and install with apt-get. i.e.:

> sudo apt-get install sauerbraten


However, if you want to install by source, which I assume is what you DL'd, then...

The file you have is a "bzipped" "tarball". It's compressed with bzip and the tar, "tape archive", contains the files.

Open a terminal and use "tar".

> man tar

to see options.

To uncompress and untar in a single step use the appropriate options.

i.e.:

> tar xvjf sauerbraten.tar.bz2

Once that's done, you have what is most likely the source code. You now have to compile and install manually.

.

---

### Post by Ms_Angel_D on 2009-06-11
You don't need the archive, you can actually just install the game from the repository.

Install option 1)
Go too
System -> Administration -> Synaptic Package Manager 
and search for sauerbraten then mark for install and apply.

Install option 2)
go to 
Applications -> Accessories -> Terminial 
and enter the following command
```
sudo apt-get install sauerbraten
```

Install option 3)
In add/remove programs make sure you have it set to show all available applications and search for sauerbraten check mark then click apply changes

Install option 4)
[CLICK HERE]("apt://sauerbraten") to start the install.

---

