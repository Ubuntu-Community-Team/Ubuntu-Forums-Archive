---
title: "Online backup"
date: 2008-12-08
forum: General Help
---

### Post by Kalrog on 2008-12-08
Does anyone use an online backup service? I use SmugMug for my photo site and I know that the SmugVault is available through them, but I don't know that I want to go that route. I was thinking something more inclusive. I want essentially a full backup of my system at a better cost as $0.22/GB/month is cheap for small amounts, but not so inexpensive when you start talking about 100GB+ in backups. Carbonite caught my eye, but they don't have a Linux client (and that is a must). I have found SpiderOak and MemoPal that look like they would meet my needs, but they are not unlimited space like Carbonite is.

Thoughts?  What does everyone here use?

---

### Post by CrusaderAD on 2008-12-08
I use a local Ubuntu backup system. Check out the instructions here:

[http://ubuntuforums.org/showthread.php?t=902366](http://ubuntuforums.org/showthread.php?t=902366)

---

### Post by Kalrog on 2008-12-08
Not a bad idea, but I was wanting off site backup in case of fire (etc.).

---

### Post by CrusaderAD on 2008-12-08
We thought the same thing. So we have two external hard drives. One is hooked up to the machine pulling backups every so often, and the other we keep off site in a lock box. Then once in a while we will switch the drives. It works really well. I would recommend the program Keep if you're using Ubuntu.

sudo apt-get install keep

---

### Post by Kalrog on 2008-12-08
Kubuntu 8.10 actually.

I'll think about the external drive like that, but it really is more hassle than I was hoping for (and more initial cost).

---

### Post by CrusaderAD on 2008-12-09
Keep is actually a KDE program, but works with all variants as far as I know. You could rig any old machine to do this, even a really old one and throw Xubuntu on it, but you will want a reliable machine.

---

