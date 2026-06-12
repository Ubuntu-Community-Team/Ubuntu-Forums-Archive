---
title: "No audio in wine at all"
date: 2007-03-28
forum: Gaming &amp; Leisure
---

### Post by nosh on 2007-03-28
When I start a program in wine, I get no audio at all though everything else works perfectly.  I ran winecfg to configure my settings and it came up fine, but when I clicked on the audio tab the window immediately closed out and the following error showed up in my terminal:

ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
Creating link /home/josh/.kde/socket-audra.
can't create mcop directory

The same thing happened when I tried gksudo winecfg

anyone know how to fix this?  I tried reinstalling wine but I just ended up with the exact same problem

---

### Post by zorkerz on 2007-03-29
sorry no idea here i would give [winehq]("http://www.ubuntuforums.org/winehq.com") a try. The forums there should have more knowledgeable people about wine.  Good luck

---

### Post by Hadron Quark on 2007-04-03
same problem.

---

### Post by Masterj15 on 2007-04-03
At  lease you guys are better off than I am. My wine wont do anything,but I might be able to help you out. Try going to debian.org and type in the search engine wine with the option any and pick and the wine than that you see in the unstable verizon. Try xwine, libjackwine and others things like that. That will give you the plugin for wine's sound and other things.

---

