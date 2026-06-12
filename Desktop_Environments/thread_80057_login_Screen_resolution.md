---
title: "login Screen resolution"
date: 2005-10-21
forum: Desktop Environments
---

### Post by heart_reaver on 2005-10-21
Hi there,

On the time of first install of 5.10 i by mistake selected login resolution to 1200*800

it looks very small and not in proper display i wanna change its resolution to 

1024*768 :rolleyes:

---

### Post by james4e on 2005-10-21
```

sudo gedit /etc/X11/xorg.conf

```

You can find many resolution parameters in the section "Screen". Then you can delete those resolution parameters you don't want to use. 

NOTE: Before you do that, you'd better backup the file.

---

### Post by heart_reaver on 2005-10-21
:D Thanks 

It works

---

### Post by objorkum on 2005-10-21
You can always configure X as in the installation of Ubuntu with:

sudo dpkg-reconfigure xserver-xorg

---

