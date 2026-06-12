---
title: "administrative privileges"
date: 2009-04-27
forum: General Help
---

### Post by TJLYD on 2009-04-27
ive been trying to use KDE partition but every time i click it, it just tells me i need to have   p, li { white-space: pre-wrap; }  administrative privileges. how do i log in as the administrator?  im new to ubuntu and the only other linux experience is my ps3 with yellow dog 6.1

---

### Post by wolfen69 on 2009-04-27
most people just put their user name and password in.

---

### Post by Jimbley on 2009-04-27
Hi mate,

Ubuntu hides the root user by default as a security precaution. Open up a terminal window and type:

sudo KParted

It'll ask you for your password. You now have root privileges! Why not try GParted given that Ubuntu has GNOME by default.

Cheers

Jim

---

### Post by SentientFluid on 2009-04-27
> **Jimbley said:**
> 

sudo KParted



Fore reference you should use gksudo [when launching graphical apps and sudo for CLI apps]("http://www.psychocats.net/ubuntu/graphicalsudo").

Like so: ```
gksudo KParted
```

---

### Post by Jimbley on 2009-04-27
Quite right. I appreciate the correction. As the author of your link says, most of the time sudo will work OK. However, you will save yourself some trouble if you use gksudo for graphical programs.

Cheers

Jim

---

