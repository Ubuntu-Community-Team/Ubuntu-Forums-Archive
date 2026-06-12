---
title: "Tracker does not index MS Office documents?"
date: 2007-10-26
forum: Desktop Environments
---

### Post by jlinho on 2007-10-26
Hi,

on my computer Tracker does not find  words in my MS Office files (.doc,.ppt) . If I convert those files to OpenOffice documents tracker finds the words into the documents ...

Does that happen to you ?

Could I change that ?

Thanks in advance for your help ...

---

### Post by jamiemcc on 2007-10-26
You need to install the wv package and then reindex 

killall -9 trackerd
trackerd --reindex

unfortunately wv is not in main so could not be included by default - we plan on using libgsf to get text from ms office which is in main in the near future

---

### Post by jlinho on 2007-10-27
> **jamiemcc said:**
> You need to install the wv package and then reindex 

killall -9 trackerd
trackerd --reindex

unfortunately wv is not in main so could not be included by default - we plan on using libgsf to get text from ms office which is in main in the near future

Thanks , taht's did it !

---

### Post by faust99 on 2007-10-30
How do I install the wv package?

---

### Post by jlinho on 2007-11-05
> **faust99 said:**
> How do I install the wv package?

Open synaptic package manager, and search for "wv", select the wv package and install. 

Or faster, open a terminal window and type:
```
sudo apt-get install wv
```

or the best:
 try clicking this link (if you use firefox with Ubuntu 7.10 , the firefox "ubufox" plugin should be installed):
[apt:wv]("apt:wv")

---

### Post by faust99 on 2007-11-05
Thank you very much. It was kind of obvious really wasn't it.

---

