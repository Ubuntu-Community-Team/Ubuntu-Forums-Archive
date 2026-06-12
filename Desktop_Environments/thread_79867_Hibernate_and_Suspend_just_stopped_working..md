---
title: "Hibernate and Suspend just stopped working."
date: 2005-10-21
forum: Desktop Environments
---

### Post by robfindlay on 2005-10-21
When i select hibernate or suspend all that happens is the screen goes blank, i get some vertical lines and then it goes to to the screensaver. 

This is on a Dell 6000 laptop, anyone had this experience before? 



Rob Findlay

---

### Post by department27 on 2005-10-21
I had the same problem with my d600, but have got it working thanks to some help.

I'm using the ati video driver, and both hibernate and suspend work. Have you installed any other drivers..???

What was suggested to me was this.

Try the following as root.

echo -n mem >/sys/power/state

you should get a black screen with some output.

originally I got the following error:

stopping tasks failed (1 task remaining)

kshfd/modem not stopping....

This was the problem the linuxant softmodem driver would not stop hence hte machine would not hibernate or suspend. Once I removed that driver it worked.

---

### Post by albertobob on 2006-02-14
How do you remove the driver

---

