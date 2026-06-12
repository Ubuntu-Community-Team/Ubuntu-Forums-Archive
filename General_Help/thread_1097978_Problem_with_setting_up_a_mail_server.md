---
title: "Problem with setting up a mail server"
date: 2009-03-16
forum: General Help
---

### Post by onehitxzibit on 2009-03-16
I tried to set up a mail server using [this](https://help.ubuntu.com/8.10/serverguide/C/postfix.html) guide and everything went fine, but when I tried to do "telnet localhost 25" (I've set it up on localhost for the test) it wouldn't connect -
> Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
Connection closed by foreign host.

I opened port 25 but the problem remains. OS is Ubuntu Server Edition 8.10 i386.

---

### Post by LegendofTom on 2009-03-16
What do you mean opened the port?  I would just try restarting the box.

---

### Post by jonobr on 2009-03-16
I have not tried this myself, but did you try maybe from a different machine if you have one?
Telnet for port 25 on the localhost may be prohibited.

---

### Post by onehitxzibit on 2009-03-16
Thank you for the suggestions. I will test tomorrow, because I need to get some sleep now. :D

---

### Post by onehitxzibit on 2009-03-17
Both restarting the PC and trying to connect from another PC failed. Maybe I messed up the addresses somewhere?

---

