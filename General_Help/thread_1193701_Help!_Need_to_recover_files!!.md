---
title: "Help! Need to recover files!!"
date: 2009-06-21
forum: General Help
---

### Post by kssworld93 on 2009-06-21
Please help! I accidentally typed in the command:

```
sudo rm -r ~/.*
```I did this using a tty, while gdm was not running.

This deleted all my config files, and I'm too scared to log in to gnome.
I need serious help to recover all these file.
How do I do it?

---

### Post by michy99 on 2009-06-21
I have had success using ext3grep. The first thing to do is turn off the computer, boot from a Live CD, and do not mount the partition with the deleted files.

---

### Post by kssworld93 on 2009-06-21
So what do I do step by step?

---

### Post by michy99 on 2009-06-21
First thing is to install ext3grep.```
sudo apt-get install ext3grep
```Then you need to have a drive or partition to recover the files to which has enough space for them.

---

### Post by Johnny B on 2009-06-21
[HOWTO recover deleted files on an ext3 file system]("http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html")

---

### Post by HermanAB on 2009-06-21
It looks to me that you deleted all user accounts - not just the config files:
r = recursive
~ = your /home/username dir
. is the present dir
* expands to . also and ~/.. is the previous directory, which is /home

---

### Post by michy99 on 2009-06-21
> **Johnny B said:**
> [HOWTO recover deleted files on an ext3 file system]("http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html")

Actually, that page is a bit out of date. The command you need to run is```
ext3grep --restore-all --after=1245542400 /dev/sda1
```BUT you need to change /dev/sda1 to whatever partition the deleted files are on and you need to run it from a partition that has enough space for the recovered files.

The --after=1245542400 part tells it only to recover files deleted since last midnight. If you need an earlier time use this converter:

[http://www.onlineconversion.com/unix_time.htm](http://www.onlineconversion.com/unix_time.htm)

---

