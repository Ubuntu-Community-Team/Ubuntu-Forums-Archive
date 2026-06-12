---
title: "Openoffice suddenly quit working"
date: 2010-05-19
forum: Desktop Environments
---

### Post by cfgauss on 2010-05-19
I assume this was the result of an automatic upgrade. I've deleted *.openoffice.org* and reinstalled *openoffice.org* several times using the Ubuntu Jaunty Jackalope packages. When I execute *oocalc* at the command line it hangs. When I do this as root it returns immediately but in both cases nothing boots. I am completely puzzled.

Any debugging hints would be welcomed.

---

### Post by SlidingHorn on 2010-05-19
If you're running it from the command line, it should show you any errors that occurred.  What does the terminal return?

---

### Post by cfgauss on 2010-05-19
> **SlidingHorn said:**
> If you're running it from the command line, it should show you any errors that occurred.  What does the terminal return?
When I execute *oocalc* as a normal user, nothing is printed at the terminal. It just hangs and I need to *Ctrl-C* to get back the bash prompt. If I *sudo oocalc*, it boots! (I didn't know this until right now.) If I *oocalc* as root, the prompt comes back immediately. Since when I *sudo oocalc* and save a file, it saves it as my normal user ID, this work-around is enough for me. Thanks.

---

