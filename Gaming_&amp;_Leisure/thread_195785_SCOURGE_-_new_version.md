---
title: "SCOURGE - new version"
date: 2006-06-13
forum: Gaming &amp; Leisure
---

### Post by dolny on 2006-06-13
```
trainchaser@acer:~/games/scourge/src$ scourge
Constructing root path:
        using binreloc...
        temp rootDir=/usr/local/share/scourge_data
*** Can't find local version of data dir. You're running a distribution.
ERROR: check for files failed in data dir: /usr/local/share/scourge_data
Either install the data files at the above location, or rebuild with ./configure --with-data-dir=<new location> or run the game from the source distribution's main directory (the one that contains src,data,etc.)
```

After successful compiling :( (got some warnings) Can anybody help?

[http://scourge.sourceforge.net](http://scourge.sourceforge.net)

---

### Post by seth0x2b on 2006-06-13
You could try to run it with "./scourge" instead of "scourge"
The game complains about the data dir missing so you might wanna check that you actually have it.
Are you using svn sources for compilation, or the source package found on the S.C.O.U.R.G.E. project page?!

Cheers

---

### Post by dolny on 2006-06-13
I tried ./scourge - the same problem.
I've used the source provided on the website.

---

### Post by Harleen on 2006-06-13
Have you also installed the scourge-data? It doesn't seem so.
I could compile scourge without any problems, then copied the data to the path it mentioned upon first start (for you it is /usr/local/share/scourge_data) and then it ran - and this game looks realy good!

---

### Post by seth0x2b on 2006-06-13
Well the source is not enough (imagine Luke Skywalker's reaction to this :D ).
You need to download scourge-data-0.14.tar.gz and extract the contents to the folder where the S.C.O.U.R.G.E. executable is located(or just create a new folder, extract the data and copy the compiled executable there).

Cheers

---

### Post by francisco_athens on 2006-10-09
If you d/l the source from the svn repository, it will grab source and data files for SCOURGE.

I've posted instructions for UBUNTU [HERE]("http://herenaforge.org/tiki-index.php?page=building_scourge_from_source_on_nix")! (HerenaForge.org)

---

