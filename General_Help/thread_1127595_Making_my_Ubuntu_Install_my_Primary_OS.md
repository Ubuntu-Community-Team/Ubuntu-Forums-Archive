---
title: "Making my Ubuntu Install my Primary OS"
date: 2009-04-16
forum: General Help
---

### Post by punjabdasher on 2009-04-16
Hello, I have a Windows XP as my main install on my hard drive and I have all my music, movies, etc on that partition. I have been using Ubuntu for a while now on a small 10 GB partition. I was wondering what processes I would have to go through to make Ubuntu my main install and move all of my files to that install.

---

### Post by James_Lochhead on 2009-04-16
Unless you have some free space you will need an intermediate medium such as DVD or external hard disk to put all your files on. If you do have free space I simply recommend shrinking the XP partition and putting all the files on a new ntfs partition. You can then shrink/remove XP and enlarge Ubuntu.

---

### Post by Iowan on 2009-04-16
If by "make Ubuntu my main install" you mean default boot, that can be accomplished by editing */boot/grub/menu.lst* > ## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#


---

