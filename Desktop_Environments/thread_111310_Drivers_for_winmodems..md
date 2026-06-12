---
title: "Drivers for winmodems."
date: 2006-01-02
forum: Desktop Environments
---

### Post by rdcastroco on 2006-01-02
Morning, I have one modem pci winmodem amr via, I need drivers for it?
Tk.:p

---

### Post by az on 2006-01-02
If you can get on the net some other way, install the sl-modem-source and gcc3.4 (gcc, gcc-base and cpp) and you will also need to install the linux-headers-2.6.12-9-386 and build-essential.

Then you will compile the kernel drivers for the amr modem.  It will make two packages, the sl-modem-modules and the sl-modem-deamon.  Install them both and you should be able to use your amr modem.

---

### Post by Sef on 2006-01-02
[http://linmodems.org/]("http://linmodems.org/")

See if linmodems can answer your question.

---

