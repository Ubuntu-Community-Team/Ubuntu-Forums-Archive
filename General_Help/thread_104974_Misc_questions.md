---
title: "Misc questions"
date: 2005-12-17
forum: General Help
---

### Post by Basu on 2005-12-17
I've been using Ubuntu for about 6 months and yesterday I installed KDE 3.5 (just the base and some select apps). In a word, I'm happy. But there are a few things I need. Could you guys help?

1. Something to convert mp3 and vorbis files to cda format so I can run them on an old fashioned CD walkman.
2. A good CD burning tool, with all the power of Nero in Win. Is k3B good?
3. Is there a way to add my windows partitions to the default system menu? If yes, how? Or else can I create a menu linking to important places and put it on the panel?
4. I have both XFCE and Gnome and I want to remove some things I'll never use. I want to remove abiword, but synaptic wants to get rid of xubuntu-desktop as well. Will that take out my XFCE install?

Thanks all.

---

### Post by jeremy on 2005-12-17
1. K3B
2. Yes, very good (see 1)
3 & 4. I don't know.

---

### Post by TeraDyne on 2005-12-17
I'm not sure on #3, but #4 is easy. The "xubuntu-desktop" is a dummy package that depends on all of the needed items for XFCE. If you remove any of the *-desktop packages, it won't uninstall the actual DE, just the dummy package.

---

### Post by aysiu on 2005-12-17
[QUOTE=Basu]
3. Is there a way to add my windows partitions to the default system menu? If yes, how? Or else can I create a menu linking to important places and put it on the panel?[/QUOTE] If you bookmark the partition's mounted folder, it should appear in the Places menu.

**Edit**: Whoops! You're using Kubuntu (not Ubuntu). You can add it as a menu item (right-click the menu and select "menu editor") with the command ```
konqueror /windows
``` (This assumes, of course, the Windows partition is mounted at the folder /windows)

---

### Post by Basu on 2005-12-18
Thank you all. Everything works perfectly now and I am so happy. BTW, do you guys know about a program which can convert .doc files to .odt en masse? opening & saving in OOo individually can be a pain.
Thanks again

---

### Post by odrop on 2005-12-18
KOffice includes a command line program to convert files to other formats.  After a quick search you can apparently do:

```
koconverter file.doc file.odt
```

Though KOffice is somewhat limited in its skills with .doc files.  

> Please note that the KOffice .doc filter is somewhat limited. In particular 
pictures are not converted. But as long as you have simple text-only word 
documents you will be fine with it.   

Raphael Langerhorst
[http://raphael.g-system.at/blog](http://raphael.g-system.at/blog)

[http://lists.oasis-open.org/archives/opendocument-users/200511/msg00032.html]("http://lists.oasis-open.org/archives/opendocument-users/200511/msg00032.html")

---

### Post by Basu on 2005-12-19
that is very helpful. i don't think I have important picture documents, so I'll give it a try. Thanks.

---

