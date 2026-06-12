---
title: "Strange Nvidia error"
date: 2009-04-23
forum: General Help
---

### Post by Sedatcom4 on 2009-04-23
I just installed ubuntu 8.10 today and did a package update before anything. After the update I tried to simply go to the hardware driver app and when I clicked on the recommended driver for my card (version 180), it gave me this message:

SystemError: E:Unable to correct problems, you have held broken packages.


I don't know what broken packages I have or anything. I am at a loss for what to do. Please help. My card is Nvidia 7600 GT if that helps at all.

:confused:

---

### Post by Elfy on 2009-04-23
Open synaptic - System Admin menu. On the left panel - Custom filters - there is a broken filter there

---

### Post by Sedatcom4 on 2009-04-23
> **forestpixie said:**
> Open synaptic - System Admin menu. On the left panel - Custom filters - there is a broken filter there


I used that filter and no packages show up.

---

### Post by Elfy on 2009-04-23
Try 

```
sudo apt-get install -f
```

Post error messages here please

---

### Post by Sedatcom4 on 2009-04-23
Nothing...

---

