---
title: "Regnum Install Problem (complete Noob)"
date: 2009-08-02
forum: Gaming &amp; Leisure
---

### Post by Hellbreather on 2009-08-02
Hi all,

Sorry I had a scan but I can't seem to find anything to solve it.

I downloaded the Torrent from the Regnum website called "RegnumOnlineInstall_32"
 
It says its an executable file. But when I click it it tells me:

"No suitable application for automatic installation is available for handling this kind of file"

What program am I missing in order to use this program.

I have Chmod -x it. As well as trying to Sudo run it etc.

So I presume I am missing an application but I am a complete noob at Linux so I don't know what it is. (Btw I updated my system yesterday)

Many Thanks.
Hellbreather

---

### Post by K.L. on 2009-08-02
Hi,

Try this:

Right click on the file, select properties and click on permissions tab. Mark it as executable. Now you should be able to run it normally (double click it).

EDIT: It is a .SH file right? If no, open up terminal, CD to a directory where installation file is and type this:

```
./RegnumOnlineInstall_32
```

---

