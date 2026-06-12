---
title: "FirstClass client problems"
date: 2008-10-29
forum: Education &amp; Science
---

### Post by Riffer on 2008-10-29
I have small but persistent problems with my FirstClass client.  If you click on link it will not come up in the browser (firefox), even if you right click and select "open in browser" it won't work.  Sometimes it takes multiple tries to start FirstClass.

Any thoughts?

Sorry I think this is in the wrong forum, I'll repost in general help.

---

### Post by ddrichardson on 2008-10-30
Yes its really irritating but it happens in the Fedora package too (only the links - the multiple start thing doesn't happen in Fedora but does in Ubuntu I've noticed). Sadly, FirstClass development for Linux is restricted to the 8.x series and is not planned for 9.x series, that's Windows/Mac only.

It does use qt however and I suspect that its something to do with how that handles link requests but haven't got to the bottom of it yet.

---

### Post by ravenon on 2008-11-01
A FC client version 9.108 is available. It is beta but I have been using it on 64 bit with no problems. Here is the link
[http://fcis.vdu.lt/VDU%20FC%20Naujienos/F0000D188/FOV1-0001D9CB/I030341EA](http://fcis.vdu.lt/VDU%20FC%20Naujienos/F0000D188/FOV1-0001D9CB/I030341EA)

---

### Post by ddrichardson on 2008-11-01
Thats interesting, so they are supporting us for 9.x - I stand corrected. Do the links work and does it login every time?

---

### Post by ddrichardson on 2008-11-01
Checked out the 32 bit version and it starts first time but still, no links.

---

### Post by ravenon on 2008-11-01
I use Gnome and it seems that First Class defaults to KDE apps for opening links and such. If you edit the file ~/firstclass/fcapps, e.g. replacing konqueror with firefox, the links will work.

---

### Post by ddrichardson on 2008-11-02
Cheers, I hadn't noticed the folder never mind the config file!

---

