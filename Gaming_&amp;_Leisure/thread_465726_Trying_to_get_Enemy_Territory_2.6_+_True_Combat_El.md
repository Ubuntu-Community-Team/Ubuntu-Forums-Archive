---
title: "Trying to get Enemy Territory 2.6 + True Combat: Elite"
date: 2007-06-06
forum: Gaming &amp; Leisure
---

### Post by Yellowbelly on 2007-06-06
K, basically what the title says: this is my goal

Here's the situation and I have a few ways of reaching my goal. I went to the TCE website and it said I need ET2.55 plus the 2.6 update plus tce. I wanted to get 2.6 but they didn't have it on linux until I discovered Loki installer. I d/led 2.55 but couldn't install it and got angry because I thought I was going to have to use a command line to do a simple task but I figured a way around it. It was a .run file that opened as text or something. Went in the properties and found the check box that ran it as an installer so I did and it worked. 2.55 is installed fine. 

I then try to install 2.60b which looked like an installer of some sort. Hiccup. I double click and it doesn't want to go. It doesn't do anything at all. I checked settings and didn't find anything good. By this time I see two options: 1) uninstall et 2.55 that I just installed and get a loki 2.6 installer and get tce on top of that. But that's a problem since I don't know the first step into removing a program other than sudo rm remove something... 2) fix 2.60b somehow and continue with that install and put tce on top.

Please help me. I can deal with command lines as long as someone gives me code but I like GUI's. Thanks in advance.

---

### Post by Rafty on 2007-06-06
check this: [http://tce.helpz0r.net/instlin1.html](http://tce.helpz0r.net/instlin1.html)
i'm still working at it, but it should help a bit ;)

---

### Post by Yellowbelly on 2007-06-06
Thanks a lot. That should be easy. Now just to cleanly uninstall what I have...

---

### Post by Rafty on 2007-06-06
btw: for tce you don't need to install the 2.60b patch. this patch causes probs in some cases. to close that security leak, disable ftp/http downloads.

---

### Post by Yellowbelly on 2007-06-06
it says that I need 2.6 to play though. Is this not correct?

---

### Post by Rafty on 2007-06-06
what you need is "ET Full 2.55/2.60" (it's in one file for linux) and "TC:E Full 0.49b". nothing else and enough to do at first ;)

---

### Post by MikeDK on 2008-05-24
seems like libgtk-1.2 is the problem here, dont know what to do here

Kind regards MikeDK

---

### Post by Perfect Storm on 2008-05-25
> **MikeDK said:**
> seems like libgtk-1.2 is the problem here, dont know what to do here

Kind regards MikeDK

```
sudo apt-get install libgtk1.2
```

or you could search synaptic package manager for libgtk1.2

---

