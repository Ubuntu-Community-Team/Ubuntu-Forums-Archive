---
title: "sinaptic pakage manager is not working"
date: 2009-04-19
forum: General Help
---

### Post by mubbashar on 2009-04-19
hi 
   i am new to ubunto my sinaptic pakage manager is not working when i open it it show a window like this

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


plese help me...............

---

### Post by Hellstudios on 2009-04-19
open up the terminal and type in:

dpkg --configure -a



that should fix it, I believe.

---

### Post by mubbashar on 2009-04-19
this is not working terminal show me this message 

dpkg: requested operation requires superuser privilege

---

### Post by Hellstudios on 2009-04-19
add "sudo" in front of it.


then when it tells you too, type your password and press enter, dont worry if you cant see it.



Sorry, forgot about sudo. that should fix everything for you.

---

### Post by mubbashar on 2009-04-19
thanks dude its work...
can u tell me where from i can download graphics driver of intel 945 series.and how to install them because i dont know how to install on ubunto in window there is a exe but in ubunto i dont know.....

---

### Post by Hellstudios on 2009-04-19
System >> administration >> hardware drivers


from there it's pretty self explanatory.

---

