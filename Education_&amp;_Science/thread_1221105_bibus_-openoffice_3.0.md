---
title: "bibus -openoffice 3.0"
date: 2009-07-23
forum: Education &amp; Science
---

### Post by paloalto71 on 2009-07-23
Hi all,
I'm trying to use bibus and openoffice writer 3.0
Everything works nice, but when I try to "Finalize" bibus freezes, and I can just kill it.

If you know something about it, it would be great!

---

### Post by Arup on 2009-07-23
Do you have the latest Java installed?

---

### Post by paloalto71 on 2009-07-23
I don't know, I have regular software updates, but maybe Java is not included.
Should I use apt-get to chek it? 
like apt-get update java?
Thanks..

---

### Post by machoo02 on 2009-07-26
Try starting bibus from a terminal rather than from the menu, and see if any errors are shown.

---

### Post by paloalto71 on 2009-07-26
> **machoo02 said:**
> Try starting bibus from a terminal rather than from the menu, and see if any errors are shown.

I got this:

Traceback (most recent call last):
  File "/usr/share/bibus/BibFrame.py", line 1499, in onMenuOOoFinalize
    self.doc.finalize()
  File "/usr/share/bibus/OOo.py", line 96, in finalize
    bibOOoPlus.finalize(self,msg.Update)
  File "/usr/share/bibus/bibOOo/bibOOoPlus.py", line 103, in finalize
    cit_fuse,cit_separator,cit_order,cit_asc = self.bibStyle['citation']['ad']
ValueError: too many values to unpack

---

### Post by machoo02 on 2009-07-31
Which version of bibus are you using?

---

### Post by machoo02 on 2009-07-31
> **Arup said:**
> Do you have the latest Java installed?Java shouldn't have anything to do with this problem: Bibus is all Python.

---

### Post by paloalto71 on 2009-07-31
I am using 1.4

---

### Post by 80aless on 2010-07-15
Here
[http://ubuntuforums.org/showthread.php?t=1227442](http://ubuntuforums.org/showthread.php?t=1227442)
They modify a line (in line 748 of /usr/share/bibus/bibOOo/bibOOoBase.py
replace "private:stream" with "self.model.getLocation()") , but the finalize command freezes anyway with the following error:
```
Traceback (most recent call last):
  File "/usr/share/bibus/BibFrame.py", line 1633, in onMenuOOoFinalize
    self.doc.finalize()
  File "/usr/share/bibus/OOo.py", line 96, in finalize
    bibOOoPlus.finalize(self,msg.Update)
  File "/usr/share/bibus/bibOOo/bibOOoPlus.py", line 105, in finalize
    bibOOoBase.finalize(self,messages = messages, cit_sort=cit_sort,cit_fuse=cit_fuse,cit_range=cit_range,cit_separator=cit_separator,cit_order=cit_order,cit_asc=cit_asc)
  File "/usr/share/bibus/bibOOo/bibOOoBase.py", line 778, in finalize
    if not self.__newDoc():							# we try to open a copy of the current doc.
  File "/usr/share/bibus/bibOOo/bibOOoBase.py", line 748, in __newDoc
    self.model = self.desktop.loadComponentFromURL('self.model.getLocation()', "_default",0,pvDescriptor)	# reload the document from stream. ALE: I replaces "private:stream" with self.model.getLocation()!!
uno.IllegalArgumentException: URL seems to be an unsupported one.
```

---

### Post by jgratero on 2010-11-26
Remove the OpenOffice and Bibus configuration folders from your home directory, and start all over again...

Backup your references, before you do that...

---

