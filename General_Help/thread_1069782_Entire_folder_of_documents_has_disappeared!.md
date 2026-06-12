---
title: "Entire folder of documents has disappeared!"
date: 2009-02-14
forum: General Help
---

### Post by dorkdork777 on 2009-02-14
I have my Documents folder in /home/data, linked to /home/chris/Documents. Inside this folder *was* a folder called "H-W", which contained many files.

For no apparent reason, and with nobody else touching my machine, this folder is now gone. Completely, taking countless hours of work and one important project with it.

I need to know now if there is any way I can try to get anything from this folder back. I have backups, but only dating to the 4th of February and since then I've done a lot of work on the project. (It was saved in default OO.o format, using OO.o Writer 3.0 - if there's an autorecovery feature I'm missing that can restore my project, this would solve my main problem.)

Please help, this is urgent >_<

---

### Post by drs305 on 2009-02-14
Try searching your entire system for the folder with this. It will even check your trash bins:
```
sudo find / -type d -name *H-W*
```

---

### Post by dorkdork777 on 2009-02-14
Thank you, trying that now along with photorec.

EDIT: nothing found. :( any more suggestions?

---

### Post by dorkdork777 on 2009-02-14
Hate to bump so early, but I need this :S

---

### Post by philinux on 2009-02-14
That command should work but try this in the terminal

1.
sudo updatedb
There are no messages from this it just updates the search database.

2.

locate H-W

make sure the case is correct for your directory.

---

### Post by dorkdork777 on 2009-02-14
Thank you. From the second command I got this:
```
chris@chris-desktop:~$ locate H-W
/home/chris/.nautilus/metafiles/file:%2F%2F%2Fhome%2Fchris%2FDocuments%2FH-W%2FJapanese%2520Y7-9%2520book%2520rewrite.xml
/home/chris/.nautilus/metafiles/file:%2F%2F%2Fhome%2Fchris%2FDocuments%2FH-W%2FYear%252010.xml
/home/chris/.nautilus/metafiles/file:%2F%2F%2Fhome%2Fchris%2FDocuments%2FH-W.xml
/home/chris/.nautilus/metafiles/file:%2F%2F%2Fmedia%2FStorage%2FDocuments%2FH-W%2FYear%252010.xml
/home/chris/.nautilus/metafiles/file:%2F%2F%2Fmedia%2FStorage%2FDocuments%2FH-W%2FYear%25209.xml
/home/chris/.nautilus/metafiles/file:%2F%2F%2Fmedia%2FStorage%2FDocuments%2FH-W.xml

```

Looks like some tracks from Nautilus - the folder's gone, but it was definitely there and I wasn't imagining it.  Which would be ridiculous, but you never know... :) (the last 3 lines are probably from when I had them on a different partition, mounted as "Storage" - this was quite a few months ago.)

Anyway, it's not visibly on my /home partition. photorec has crashed on me twice now; is there anything else I could try to recover the deleted files?

---

### Post by philinux on 2009-02-14
The only thing i can think of is testdisk.

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

I would back up any other important stuff before playing and dont write anything else to the disk.

---

