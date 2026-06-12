---
title: "LibreOffice 3 &quot;General network error has occurred&quot; while opening Ubuntu One documents"
date: 2011-05-01
forum: Desktop Environments
---

### Post by kaustavdm on 2011-05-01
Hi,

I cannot open documents (.odt, .doc etc) synchronized through Ubuntu One in LibreOffice 3 on my laptop running Ubuntu 11.04 (network upgrade from 10.10). LibreOffice quits by throwing an error message: "General network error has occurred".

However, if I copy the same files outside the Ubuntu One synced directory (e.g. to ~/Desktop), I can open them without any errors.

I just can't open them within the synced directory.

FYI, I have synchronized an existing folder on Ubuntu One after the upgrade and the synchronization has been smooth. The synced folder is a sub-directory of ~/Documents and has local sync enabled.

Any ideas on what's going on? Let me know what more info can I provide?

EDIT: I can open other files like .pdf, .mp3, .php, shared in the same directory. I'm having problem with LibreOffice in particular.

System info:
------------
Ubuntu 11.04
LibreOffice 3

---

### Post by kaustavdm on 2011-05-01
bump

---

### Post by kaustavdm on 2011-05-19
bump again.
I've not yet got this fixed. Still can't open documents using LibreOffice in Ubuntu One shared folders. Can anyone please confirm whether this is the desired behaviour?

---

### Post by srinivasmurty on 2011-07-04
I found this in the reported bugs. When I tried running LibreOffice as root (sudo), it worked. This is not a solution, obviously, but apparently is a known and reported bug. For me, this only happened when running LibreOffice from the Ubuntu Natty 64-bit version, not in the 32-bit.

[URL="https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/792947"]https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/792947
[/URL]

---

