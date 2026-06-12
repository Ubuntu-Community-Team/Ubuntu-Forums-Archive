---
title: "Themes not working as root"
date: 2007-03-29
forum: Desktop Effects &amp; Customization
---

### Post by fearpi on 2007-03-29
I've noticed that when I use sudo to run programs, certain themes do not work. The most recent one I've had this issue with is "ubuntulooks-bluecurve". The program will default to a very drab looking skin that reminds me of Windows 95. Why would this be?

---

### Post by josephus on 2007-03-29
if the themes are stored in your home directory then when you run using sudo they won't be used.

---

### Post by jordanmthomas on 2007-03-29
Try this:
```
sudo ln -s /root/.themes ~/.themes
sudo ln -s /root/.icons ~/.icons
```
Then, whenever you install a theme under your name, root can use it as well.

Alternatively, copy everything in your ~/.themes into /usr/share/themes

---

### Post by fearpi on 2007-03-29
Ah, thanks, both of you. I love symbolic links.

---

