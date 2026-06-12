---
title: "wont load... keeps bringing up Grub"
date: 2009-06-11
forum: General Help
---

### Post by bullDAWgs on 2009-06-11
So I run a Dual OS with Vista and Ubuntu, and it used to load everything on it's own when i would click ubuntu... i would simply select it... i would see commands running frantically on my screen, and then i would see the splash, login, and be on my happy way. But all of the sudden it stopped doing that and now brings up grub4dos, i am completely lost and can't get into my system at all. Help. Please.

---

### Post by synapsys on 2009-06-11
Your best bet would probably be to boot from live cd and reinstall grub.

---

### Post by bullDAWgs on 2009-06-11
Um, I am not exactly sure what grub even is, or how to work it. And also, would I still have my files, cause I was doing some major graphics work, and then this happened, now I can't get to any of my work. I really have no clue what I'm doing.

---

### Post by lindsay7 on 2009-06-11
Boot your computer with the Ubuntu live cd and go to the terminal.  Type the following

```
sudo grub
find /boot/grub/stage1
(it will give a (hdx,y)
root (hdx,y)
setup (hdx)
quit
```

---

### Post by synapsys on 2009-06-11
Yes you will still have all of your files. Grub is the name of the 'boot loader' that loads ubuntu (and windows) when you start your computer.

---

