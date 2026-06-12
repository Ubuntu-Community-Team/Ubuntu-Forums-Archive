---
title: "My openoffice is showing following error??"
date: 2010-12-18
forum: Desktop Environments
---

### Post by scott_tiger on 2010-12-18
Plz see the attachment and tell me how to get out of it...
whenever i am opening any WORD DOCUMENT these msg comes to recover and i dont understand what to do???
help me out!!!!!

---

### Post by pfnorris on 2010-12-18
I had a similar problem to this a while back. The problem is that at some point OpenOffice has closed/crashed whilst a file was still open. When this happens it tries to preserve what it can of the file, and then attempts to recover it when it is next opened. You need to either use the recovery dialogue that you are presented with (in your screenshot) to recover the file, and then save it if successful. 

Or, if that does not work you need to find the recovery stub that Open Office is using, and delete it. This is usually found in your home directory or one of it's subdirectories. It usually starts with a ~ symbol and should contain at least part of the original file name.

---

