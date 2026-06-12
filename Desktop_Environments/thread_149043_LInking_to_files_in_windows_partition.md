---
title: "LInking to files in windows partition"
date: 2006-03-23
forum: Desktop Environments
---

### Post by Dov on 2006-03-23
Ubuntu seems to refuse to make links to files in my windows partion. Have tried several times, both in the terminal and in Nautilus while logged in as the owner of the windows partition. Just want to put links on my Desktop.

Any ideas where I may have gone wrong??

Many thanks in advance,

Dov

---

### Post by dcstar on 2006-03-23
[QUOTE=Dov]Ubuntu seems to refuse to make links to files in my windows partion. Have tried several times, both in the terminal and in Nautilus while logged in as the owner of the windows partition. Just want to put links on my Desktop.

Any ideas where I may have gone wrong??

Many thanks in advance,

Dov[/QUOTE]
ln -s <full windows file path in linux> <link target name>

---

### Post by aysiu on 2006-03-23
By what method are you trying to make links?

---

### Post by Dov on 2006-03-30
[QUOTE=dcstar]ln -s <full windows file path in linux> <link target name>[/QUOTE]

I'm sorry, I don't understand the context or usage of this info. Couyld you please explain a bit more? I'm pretty new to Linux.

Many Thanks

Mark

---

### Post by Ramses de Norre on 2006-03-30
You need to type that in a terminal (applications > accesoires > terminal), so for example: ```
ln -s /media/hda3/Documents\ and\ Settings /home/ramses/Desktop/windocs
```
Would create a link on my desktop called windocs and linking to my Documents and Settings directory in windows.
You need to change the path's to the ones you need.
The windows path needs to start from / and go through the mountpoint (/media/hda3/ in my example).

---

### Post by steve.horsley on 2006-03-30
Or alternatively, open two file manager (nautilus) windows, and drag the file from the windows drive to your home folder using the middle mouse button.

---

### Post by Dov on 2006-04-01
Awesome! Thanks heaps! Just strange how I couldn't make the link by using right-click or using the cp -l command in Terminal...

God Bless All who answered my query!

Dov

---

