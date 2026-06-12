---
title: "How to stop Nautilus to associate .dat files as MPEG video? (Re-post)"
date: 2006-08-18
forum: Desktop Environments
---

### Post by Markus Valkeapaa on 2006-08-18
Hi all!
(This a re-post, previously had the thread name in wrong language, sorry about that)

Nautilus keeps associating ASCII text files with extension .dat to MPEG video files. I have tried to change this with 'right mouse button - Properties - Open with' function. I wonder if there is a "lower level" way to assign file extensions to certain applications?

-Markus

---

### Post by Markus Valkeapaa on 2006-08-22
Solution:  The file extension 'dat' was connected to mpeg videos in the file [COLOR="DarkGreen"]/usr/share/mime/packages/freedesktop.xml[/COLOR] 
The problem is solved by:
1. Commenting out the relevant line in a texteditor(e.g. with sudo gedit filename): [COLOR="Blue"]<!-- <glob pattern="*.dat"/--!>[ /COLOR]
2. Updating mime database: [COLOR="Blue"]sudo update-mime-database /usr/share/mime/[/COLOR]
3. Logging out and loggin in again.

Credit and many thanks go to "tn" in Ubuntu Finland forum. Apologies about the cross-posting for those who read both forums.

-Markus

---

