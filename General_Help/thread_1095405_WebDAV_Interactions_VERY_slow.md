---
title: "WebDAV Interactions VERY slow"
date: 2009-03-13
forum: General Help
---

### Post by swegner on 2009-03-13
Hello all,

I have some webspace for my university account (UIUC netfiles), which I can connect to via WebDAV.  However, it is almost unusable because of how slow the interactions are.

I have tried mounting the dav server in two different ways: using GVFS via the Places > Connect To.. menu, as well as manually mounting with davfs2.  In both situations, programs will hang for ~5 seconds on any interaction-- browsing from folder-to-folder, opening a file, editing a file, and saving it.  davfs2 has some extra caching options that I played with a little, but it didn't seem to make much of a difference.  The data stored on my dav space is relatively small, approx. 15 HTML webpages across about 5 subdirectories.  As it stands, the WebDAV mount is functionally unusable.

There was a program on Windows that I previously used called WebDrive, which is also recommended by my university.  It has much quick interactions by keeping a local cache of the entire dav share, and pushes files asynchronously to the server whenever they are updated.  Is there any way to achieve this sort of functionality on Ubuntu?  

I wouldn't mind a solution that required configuring / connecting via the command-line, but should have integration with the filesystem such that I could browse files in Nautilus and easily open files in a text editor.  Does such a program exist?

---

### Post by degtukas on 2009-03-20
Hi, check out Konqueror. I use it for secure webdavs, since neither nautilus nor davfs work properly for me.

---

### Post by Reklov on 2009-03-27
Nautilus seems to be really buggy when it comes to WebDAV. I have never tried Konqueror. An alternative could be 'cadaver', which is an FTP like comandline WebDAV client. It works well enough but does not provide the comfort of a mounted drive.

I don't know why that many WebDAV clients and servers are so unbelievably buggy. It's not really difficult to implement such software. Maybe it's because they want you to pay for good implementations? I even think about fixing Nautilus WebDAV implementation. I really need it ;) But I hardly ever have the time. Well ,,,

---

