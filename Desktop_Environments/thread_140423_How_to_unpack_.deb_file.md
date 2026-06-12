---
title: "How to unpack .deb file ?"
date: 2006-03-06
forum: Desktop Environments
---

### Post by stonex on 2006-03-06
When I try with "extract to" , I got message " file type not supported " . I trying to unpack modem driver for Agere .

---

### Post by WackToMack on 2006-03-06
First, place the .deb file into your Home folder.

Then, go to Applications>Accessories>Terminal.  In the Terminal, key in the following text:

```
sudo dpkg -i (filename).deb
```

(Don't include the parenthesis, and replace the (filename) that you see above with the name of your .deb file)

The application should now be installed on your system.  Good luck, and leave a reply to tell me if it worked for you or not. :D

---

### Post by codejunkie on 2006-03-06
[QUOTE=stonex]When I try with "extract to" , I got message " file type not supported " . I trying to unpack modem driver for Agere .[/QUOTE]
try```
sudo dpkg -i nameofpackage.deb
```this should install it.
Edit: two slow

---

### Post by stonex on 2006-03-06
OK .I'v done it but it is not good driver . I need driver sl-modem-modules-2.6.12-9-386 for my Kernel . Where to find it ?

---

