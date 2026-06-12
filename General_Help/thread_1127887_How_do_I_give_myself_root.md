---
title: "How do I give myself root?"
date: 2009-04-17
forum: General Help
---

### Post by Epidemic_HardyBoy on 2009-04-17
I am trying to extract a tar to my usr/share/themes folder, but it says I don't have the permission to do so.. Can anyone help me?!

---

### Post by HOLOGRAPHICpizza on 2009-04-17
Use sudo.
For example
```
sudo tar xf foo.tar /usr/share/themes/
```
in the terminal.

---

### Post by Epidemic_HardyBoy on 2009-04-17
I tryed that, but it says I cannot get it to work.. :(

---

### Post by James_Lochhead on 2009-04-17
OK, if you know to paths type the following in the terminal:

```

sudo tar xzvf /path/to/tar/file
sudo mv /path/to/extracted/directory /usr/share/themes/

```

If it is tar.bz2 you should use tar xjvf. If it is not compressed (i.e. just tar) then you use tar xvf.

---

### Post by HOLOGRAPHICpizza on 2009-04-17
You could try a full root shell with ```
sudo -i
```

---

### Post by Epidemic_HardyBoy on 2009-04-17
how would i get to the desktop? (What are the paths..?)

(im only asking because I know something can happen if you screw up on linux lol)

---

### Post by dtoronto on 2009-04-17
if you're using the GUI you may want to use gksudo

---

### Post by James_Lochhead on 2009-04-17
HOLO's way is better. Make sure you have the write command though from my post. It is different if it is bz2, gz or just normal tar.

---

### Post by James_Lochhead on 2009-04-17
Yea that is an idea. Press alt+f2 and type gksudo nautilus. Enter your password and do it graphically.

---

### Post by HOLOGRAPHICpizza on 2009-04-17
> **James_Lochhead said:**
> HOLO's way is better. Make sure you have the write command though from my post. It is different if it is bz2, gz or just normal tar.

In newer versions of tar it can detect compression automatically, you only need xvf for all files.

---

### Post by James_Lochhead on 2009-04-17
> **HOLOGRAPHICpizza said:**
> In newer versions of tar it can detect compression automatically, you only need xvf for all files.

Oo nice. Learn something new every day.

---

### Post by Epidemic_HardyBoy on 2009-04-17
That didnt work. :(
This sucks, im confused

---

### Post by Epidemic_HardyBoy on 2009-04-17
nvm, got it, i was dumb.. my badddd

---

