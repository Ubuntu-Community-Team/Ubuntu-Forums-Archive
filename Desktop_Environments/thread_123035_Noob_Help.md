---
title: "Noob Help"
date: 2006-01-29
forum: Desktop Environments
---

### Post by BlakcTigers91 on 2006-01-29
OK Guys.  Just installed ubuntu 5.1.  Noobie to Linux.

I have a few things though.

Why does it run SOOO slow, compared to XP?

How do I make it so I can Access my Windows Drives ( IE, get Files Off them)

PARTITION 1 - XP (NTFS)
Partition 3    - XP (NTFS)
partition 5   -   UbunTu (/ext3)
Swap File

ANyone?  Try to keep it simple.  Thanks!

---

### Post by aysiu on 2006-01-29
[QUOTE=BlakcTigers91]OK Guys.  Just installed ubuntu 5.1.  Noobie to Linux.

I have a few things though.

Why does it run SOOO slow, compared to XP?[/quote] Try XFCE instead of Gnome.

0. The terminal is in Applications > Accessories > Terminal
1. These instructions: [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)
2. ```
sudo apt-get update
sudo apt-get install xubuntu-desktop
```
3. Log out.
4. Session > XFCE
5. Log in.

> 
How do I make it so I can Access my Windows Drives ( IE, get Files Off them)

PARTITION 1 - XP (NTFS)
Partition 3    - XP (NTFS)
partition 5   -   UbunTu (/ext3)
Swap File

ANyone?  Try to keep it simple.  Thanks! See the fourth link of my signature.

---

### Post by BlakcTigers91 on 2006-01-29
KK thanks.  How do I do the XFCE thing?

Sorry!

---

### Post by BlakcTigers91 on 2006-01-29
Ugh....When I am in the terminal, it won't let me type in my password...the cursor just flashes.. Why?

---

### Post by aysiu on 2006-01-29
It lets you type in your password--it's just not showing you any indication that it's letting you (no asterisks). Just type it in and press Enter.

---

### Post by andrija1989 on 2006-01-29
Hi, i am new to ubutu linux and i was wondering is there a way i can play
games or programs that i used to play on windows.. on linux ...?

---

### Post by BlakcTigers91 on 2006-01-29
OMG THANK YOU!!!

The XFCE thing mad it SOO much Faster!

I owe ya!

Now I gotta do that mount thing :(

---

### Post by Tiede on 2006-01-29
wine, cedega and crossover come to mind... But some are non free and others can be quite a drag...
The best thing would be to try to find a program on linux that matches or is even better than what you use on windows (which shouldn't be to hard) and to by a gaming console, I think ;)

---

### Post by BlakcTigers91 on 2006-01-29
When I do the Mount thing, my Windows Partitions arent showing up when I edit the Fstab thingy....Why?

---

### Post by aysiu on 2006-01-29
[QUOTE=BlakcTigers91]When I do the Mount thing, my Windows Partitions arent showing up when I edit the Fstab thingy....Why?[/QUOTE] Aren't showing up where? They should be mounted as folders.

By the way, if you run XFCE, it may help to also run ```
nautilus
gnome-volume-manager
``` and then save your session at logout.

---

### Post by andrija1989 on 2006-01-29
where can i download programs for linux... for windows i would usually get torrents or soemthin but fro linux..?:-k

---

### Post by aysiu on 2006-01-29
[QUOTE=andrija1989]where can i download programs for linux... for windows i would usually get torrents or soemthin but fro linux..?:-k[/QUOTE] Read the second link of my signature.

---

### Post by andrija1989 on 2006-01-29
...read your what..?lol

---

### Post by andrija1989 on 2006-01-29
nm :P

---

### Post by andrija1989 on 2006-01-29
ok 1 more thing where do i go so ican type all the codes in such as 
"sudu apt-get..." 
where do i click to type that

---

### Post by BlakcTigers91 on 2006-01-29
Like what I mean is...

When I Look for my drives using:

```
 sudo fdisk -l 
```
The NTFS Partitions are Recgonized.


When I do THIS:
```
 sudo nano /etc/fstab 
```

They Aren't there. 
Is there A reason?
Something I did in Installation?

PLEASE HELP?

---

### Post by BlakcTigers91 on 2006-01-29
OK...So If I reinstalled...what Shoulkd I do Different?

---

