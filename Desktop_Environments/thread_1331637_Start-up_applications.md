---
title: "Start-up applications"
date: 2009-11-19
forum: Desktop Environments
---

### Post by Kognit on 2009-11-19
Hi

I want on start-up to run the following command: ```
sudo modprobe -r psmouse
```.
How can i run this command in start-up applications?

---

### Post by karlson on 2009-11-19
> **Kognit said:**
> Hi

I want on start-up to run the following command: ```
sudo modprobe -r psmouse
```.
How can i run this command in start-up applications?

Why not just blacklist it?

---

### Post by Kognit on 2009-11-19
What is the blacklist?

---

### Post by karlson on 2009-11-19
> **Kognit said:**
> What is the blacklist?

/etc/modprobe.d has a file called blacklist in Intrepid or blacklist.conf on Jaunty.

If you put the module psmouse in it it will not be loaded.

---

### Post by Kognit on 2009-11-19
No, i want to load it, because with this command i will disable my touchpad (i have karmic coala and have some problems with the touchpad - but that solution works for me and now i want to run in on start up).

---

