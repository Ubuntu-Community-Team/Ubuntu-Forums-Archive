---
title: "Download packages"
date: 2006-04-28
forum: Desktop Environments
---

### Post by adriaanputter on 2006-04-28
Hi

Is it possible to download packages and then go install it on another computer, and how, how do I access the repositories?

Adriaan

---

### Post by ajgreeny on 2006-04-28
All packages you install on your computer are stored in /var/cache/apt/archives as the deb file.  You can burn these to a cd or put them on a usb flash drive or whatever means you have to move files around, and then copy them using sudo to your new computer in the same folder.
Then I think when you go to install from synaptic on the new computer it will pick up the file from cache, and not download it. If that doesn't work you can just copy the files to your home folder and enter
"sudo dpkg -i filename.deb"
and it should install it OK.  You may have some dependency problems with this last way however, so it may not be quite that simple and you may need to get more files across from the older computer.  Look out for any error mesages when installing or running any new progs. and then get hold of any needed files.

---

### Post by az on 2006-04-28
[https://wiki.ubuntu.com/AptMoveHowto/simple](https://wiki.ubuntu.com/AptMoveHowto/simple)


or

[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

---

