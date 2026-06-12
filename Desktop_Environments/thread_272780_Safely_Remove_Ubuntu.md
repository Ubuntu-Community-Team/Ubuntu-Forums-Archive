---
title: "Safely Remove Ubuntu"
date: 2006-10-07
forum: Desktop Environments
---

### Post by Sethro on 2006-10-07
[FONT="Arial Black"]Hi guys, I just installed ubuntu and to tell you the truth it did not work out for me, iam currently using grub and dual booting windows xp, how can i safely remove ubuntu and grub, and resize my partition and give Windows XP the space..

Thanks[/FONT]

---

### Post by lemonsCC on 2006-10-07
You can use Gparted Live CD [http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")to resize your windows partition to use the whole HD.  Then insert your windows CD, enter recovery console and type ```
fixmbr
```.

---

### Post by Sethro on 2006-10-07
colio thanks should i delete the swap and the ext3, I wont have any problems with mounting my WIndows XP partition right?

---

