---
title: "Webradio in Listen Music Player 0.5 is broken"
date: 2009-03-28
forum: General Help
---

### Post by MWrigs on 2009-03-28
Hi 

The webradio in Listen Music player 0.5 is broken. I went to the Listen web site and they have fix the problem in listen-0.6rc2.tar.gz. How do I upgrade Listen 0.5 to Listen 0.6. Thanks.

---

### Post by zvacet on 2009-03-29
You have to compile it if you want latest version.Unpack tar.gz package with right click on it and you will get folder.Go to the terminal and if you downloaded package to Desktop then 

```
cd Desktop
```

and then 

```
cd listen-0.6rc2
```

and then 

```
make clean
make
make install
```

---

### Post by MWrigs on 2009-03-29
Hi zvacet

I did as you said in a terminal and this is what I received.

mark@mark-desktop:~/listen-0.6rc2$ make clean
rm -rf data/*.h
rm -rf misc/*.h
rm -rf po/*.mo
rm -rf build
rm -f tags
rm -f misc/listen.1 listen.1.gz listen.desktop
rm -rf dists/
rm -f listen org.gnome.Listen.service
find . -type f -name '*.pyc'  -print | xargs rm -rf
find . -type f -name '*.pyo'  -print | xargs rm -rf
rm -f src/*.so
make -C mmkeys clean
make[1]: Entering directory `/home/mark/listen-0.6rc2/mmkeys'
rm -f mmkeys.so *.o mmkeyspy.c
rm -rf build dist
make[1]: Leaving directory `/home/mark/listen-0.6rc2/mmkeys'
mark@mark-desktop:~/listen-0.6rc2$ make
Checking for Python... /usr/bin/python
Checking Python version: 2.5
Checking for PyGTK >= 2.6: found
Checking for pyGTK-devel >= 2.6:
not found
Listen requires pyGTK-devel
make: *** [check] Error 1
mark@mark-desktop:~/listen-0.6rc2$ 
mark@mark-desktop:~/listen-0.6rc2$ 

It is looking for pyGTK-devel and it is not in the repository, when I went to look for it with synaptic.
Thanks.

---

### Post by mjm1231 on 2009-04-07
What do you mean webradio is broken? I play webradio stations all the time in Listen 0.5. Occasionally, the stream becomes choppy or fails and has to be restarted, but this is rare, and to be fair I am running it on an old PC (P3-933). 

Are you referring to the inability to open .pls files and shoutcasts directly? There are a half dozen posts at least asking about that problem specifically, each without any answer.
 
I've found as a workaround that I can just create a new webradio station from the menu (or CTRL-I) and enter the information (note to Listen dev team: it might be nice to label the fields in that dialog window; note to those attempting this: the first field is for the name, the second for the url) and it will play. The url can be found by opening the .pls file in a text editor. I have found no other method of loading a .pls file in Listen (including setting it as the default app for that file type). 

Anyway, I'm curious to know exactly what is fixed in 0.6 regarding webradio so I can decide whether to wait for the official release.

---

### Post by v1nsai on 2009-08-13
I love the stuff they tried to do in listen music player, but 0.5 was pretty choppy for me too (I just got the latest version compiled not long ago) and I had a hell of a time finding pygtk-devel.  Do this

```
sudo apt-get install build-essential python-gnome2-extras-dev intltools
```

and I'm pretty sure that's all you will need.  If this doesn't answer your questions, maybe your not ready to compile for yourself, it can be a very difficult process if you can't read through compiler output to find errors.

Listen has a LOT of potential, I plan to stick with it and hope they can work out these bugs.

---

