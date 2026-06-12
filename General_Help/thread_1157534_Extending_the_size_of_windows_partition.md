---
title: "Extending the size of windows partition"
date: 2009-05-12
forum: General Help
---

### Post by Mister LinOx on 2009-05-12
Okay. My HP a522n Power Supply is bad(I think I did something to it) and on my grandmothers PC, I resized the Windows partition ready to reinstall a dual boot for XP and ubuntu. Problem is, I didn't notice the size of the HD as I applied this, and it's only 38GB! So now, I need to resize the XP partition for around 35GB and forget about Ubuntu for now. When I try to though, I problem occurs, so I saved the error. Here it is in the attachment with a screenshot.

So please, help me with this. Otherwise, I will end up getting b****ed at and all of that. Thank you.

---

### Post by Mister LinOx on 2009-05-12
Oops. Forgot to add the attachments. XP

---

### Post by Cheesemill on 2009-05-12
It looks like XP didn't shut down cleanly.  You just need to follow the instructions that gparted gives you in the error message:

Boot XP, open a command prompt and type chkdsk /f c: and then reboot your computer into XP **twice**.

After this try gparted from the Live CD again (remembering to shut down XP properly first).

Cheesemill

---

### Post by geraldvillorente on 2009-05-12
You can't perform chkdsk while drive c: is active...you need to insert it as a slave to other PC which is running under windows to perform that task.

---

### Post by Cheesemill on 2009-05-12
> **geraldvillorente said:**
> You can't perform chkdsk while drive c: is active...you need to insert it as a slave to other PC which is running under windows to perform that task.

You don't need another PC to do this, if you try running chkdsk /f on the system drive it will just inform you that it cannot be done now, but will be performed next time the computer is started (before windows fully loads).

Cheesemill

---

### Post by geraldvillorente on 2009-05-12
oops..sorry you're absolutely correct :)

---

