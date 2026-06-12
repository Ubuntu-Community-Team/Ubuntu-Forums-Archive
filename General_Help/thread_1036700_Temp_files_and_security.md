---
title: "Temp files and security"
date: 2009-01-11
forum: General Help
---

### Post by ex-para on 2009-01-11
I have Ubuntu 8.04 and I have read Ubuntu deletes temporary and all the unwanted files its self, and then I have read people do it. Regarding security some so not needed others it is, I would like to know which way is it. 
****

---

### Post by jonabyte on 2009-01-11
Sorry I can't shed light on the temp files but click the link here for a good article on Ubuntu desktop security:

[http://www.ibm.com/developerworks/linux/edu/l-dw-linux-harden-desktop-i.html?S_TACT=105AGX03&S_CMP=HP]("http://www.ibm.com/developerworks/linux/edu/l-dw-linux-harden-desktop-i.html?S_TACT=105AGX03&S_CMP=HP")

---

### Post by IllegalCharacter on 2009-01-11
Not sure exactly, but one good way to find out:
[LIST=1]
[*]Put a file in /tmp.
[*]Restart your computer.
[*]See if the file is still there.
[/LIST]
If after this the file is gone, then it looks like Ubuntu removes them!

I think what might be a problem is if your system is staying on all the time, then Ubuntu might not automatically delete temp files.

---

