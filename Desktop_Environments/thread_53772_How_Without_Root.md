---
title: "How Without Root"
date: 2005-08-02
forum: Desktop Environments
---

### Post by alec on 2005-08-02
Hi,

I want to use qparted to change a usb hd from NTFS to FAT. However I cannot proceed because I need to be in root to do this.

Question: How do I use applications like qtparted without a root account?

Thanks

---

### Post by Lord Illidan on 2005-08-02
You have to use sudo..
like this:

Instead of 

```
synaptic
```

you do:

```
sudo synaptic
```

where it will ask you for your password, which you gave in the installation.

```
sudo qparted
```

and you're off!!!

---

### Post by Feanor on 2005-08-02
If you're using an application under kde I think it's better to use kdesu instead of sudo

---

### Post by alec on 2005-08-02
OK, As usual when you know how it works like a dream.

Many thanks.

---

