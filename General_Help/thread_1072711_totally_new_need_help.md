---
title: "totally new need help"
date: 2009-02-17
forum: General Help
---

### Post by Wikdstang83 on 2009-02-17
I recently made the jump and installed ubuntu on my laptop. I have it setup as a dual boot system ( vista & ubuntu ) In vista my wireless works fine. How do I set up my wireless in ubuntu? If u can help please explain in dummy terms. I know NOTHING about ubuntu except that I like its layout and am trying to learn how to use it.

---

### Post by Titan8990 on 2009-02-17
What kind of wireless card is it? Go to Applications -> Terminal -> Type:  lspci

copy and paste the results here.

---

### Post by davec64 on 2009-02-17
> **Titan8990 said:**
> What kind of wireless card is it? Go to Applications -> Terminal -> Type:  lspci


And which version of Ubuntu are you using 8.10?

---

### Post by RedSingularity on 2009-02-17
You will probably need to install ndiswrapper.  It allows you to install wireless windows drivers in ubuntu.  Look it up in google, you'll see.

---

### Post by Titan8990 on 2009-02-17
> **Shadow121 said:**
> You will probably need to install ndiswrapper.  It allows you to install wireless windows drivers in ubuntu.  Look it up in google, you'll see.



ndiswrapper should be a LAST possible alternative. There are not many wireless devices out there that do not have an open source solution, so please ignore the above comment for now.

---

### Post by Wikdstang83 on 2009-02-17
how can i do this without having to restart laptop? can I open ubuntu as a "piggyback" so to speak to do this? and its 8.10. to post on here i'm using windows because i can't get anything from linux at all.

---

### Post by RedSingularity on 2009-02-17
Did you install all the latest updates?  Thats what i did on my laptop and it got my wireless working.  Of course to install the updates you need to plug it into your router or modem to get Internet.

---

