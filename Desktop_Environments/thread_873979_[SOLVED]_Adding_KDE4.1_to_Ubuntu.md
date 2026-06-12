---
title: "[SOLVED] Adding KDE4.1 to Ubuntu"
date: 2008-07-29
forum: Desktop Environments
---

### Post by 34.50 on 2008-07-29
I have Hardy Heron and using Ubuntu. How can I get KDE4.1? 

I saw this on kubuntu's site: > Add deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main to your /etc/apt/sources.list.  So, I guess what I'm asking is how do I do this?

---

### Post by Ryszu on 2008-07-29
Copy the *deb [http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu) hardy main* text, then in a terminal:

```
sudo nano /etc/apt/sources.list
```

Page down to the bottom, CTRL+SHIFT+V to paste (or right click), CTRL+O to save, CTRL+X to exit.

Then:

```
sudo apt-get update && sudo apt-get install kubuntu-kde4-desktop
```

Answer yes to the two questions, then choose whether you want Gnome or KDE to startup by default when asked.

---

### Post by 34.50 on 2008-07-29
Thanks!

---

### Post by stathis21 on 2008-09-19
hi...
i just wanted to know how to remove KDE4.1...
i just have to type
```
sudo apt-get remove kubuntu-kde4-desktop
```
???

---

