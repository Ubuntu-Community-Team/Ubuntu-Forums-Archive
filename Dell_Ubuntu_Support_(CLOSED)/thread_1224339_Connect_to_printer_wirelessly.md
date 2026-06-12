---
title: "Connect to printer wirelessly"
date: 2009-07-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Nathan Cunningham on 2009-07-27
I am on my computer upstairs, with Ubuntu, trying to connect to my downstairs computer, with Windows. I've been able to do that fine, but I'm trying to connect to the printer connected to my downstairs computer. When I connect to the computer, there is a folder named, "print$" but I don't know how to then print a document from there. How to install the printer on my computer or anything like that. Help, please!

---

### Post by epicoder on 2009-07-27
System -> Admin -> Printing

Click new. If your printer isn't found, make sure you have samba installed (sudo apt-get install samba), then click Network -> Windows printer via SAMBA, then browse. you should be able to find it by hostname.

---

### Post by Nathan Cunningham on 2009-07-29
There seems to be a problem. What you said helped me, but there was "an error during the CUPS operation: 'client-error-document-format-not-supported'" any ideas?

---

