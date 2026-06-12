---
title: "No display variable set"
date: 2012-06-16
forum: Desktop Environments
---

### Post by sharethl on 2012-06-16
ubuntu 12 with ATI video card, after a update, it can not boot to unity, stays in command line mode. And I type unity in command line, it said no display variable set.
How can I fix this?

Thanks

---

### Post by papibe on 2012-06-16
Hi sharethl.

Did you update Ubuntu from a previous version, or Did you update your graphic cards?

Regards.

---

### Post by N0oki3 on 2012-06-16
Hello there. In command line type 
```
sudo startx 
```

if it won't start
```
sudo rm /etc/X11/xorg.conf
sudo startx

```

Now you should be able to get into the desktop. Go to the terminal Ctrl + alt + t and type 
```
lspci | grep VGA
```

please copy paste the input here

---

### Post by sharethl on 2012-06-16
> Hi sharethl.

Did you update Ubuntu from a previous version, or Did you update your graphic cards?

Regards.
What I installed is ubuntu12, it is a normal update. Not sure what it updated, my ATI driver is 12.3.

---

### Post by sharethl on 2012-06-16
> **N0oki3 said:**
> Hello there. In command line type 
```
sudo startx 
```

if it won't start
```
sudo rm /etc/X11/xorg.conf
sudo startx

```

Now you should be able to get into the desktop. Go to the terminal Ctrl + alt + t and type 
```
lspci | grep VGA
```

please copy paste the input here

I tried startx, then the laptop freezes.......

---

### Post by N0oki3 on 2012-06-17
have you tried editing grub from quiet splash to nomodeset?

---

### Post by sharethl on 2012-06-17
> **N0oki3 said:**
> have you tried editing grub from quiet splash to nomodeset?
followed this instructions to use nomodeset. it still freeze when I startx.

[http://askubuntu.com/questions/109944/highlight-the-first-entry-and-replace-quiet-splash-with-nomodeset-how-do-i-d](http://askubuntu.com/questions/109944/highlight-the-first-entry-and-replace-quiet-splash-with-nomodeset-how-do-i-d)

---

