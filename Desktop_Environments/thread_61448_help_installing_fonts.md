---
title: "help installing fonts"
date: 2005-08-31
forum: Desktop Environments
---

### Post by arcanistherogue on 2005-08-31
Hey.  I have a bunch of fonts i have downloaded over a period of time that I keep with me whenever I backup my computer,  a bunch of custom ones.  I had the file named .fonts before I knew that that is where the actual fonts are installed, so when I tried to install them from that  archive it said they all already existed, but I hit overwrite.

When I rebooted, none of my new fonts were installed, and when i try to install them via thie font installer, it says "only fonts may be installed".   The files are all .ttf, I don't know what is wrong?  

What are some things that could be   wrong, and how do I fix them?

---

### Post by xmastree on 2005-09-01
open a terminal, type:
```
cd .fonts
ls 
``` What do you see?

Here's the result for mine.
```
chris@ubuntu:~$ cd .fonts
chris@ubuntu:~/.fonts$ ls
roosthea.ttf  ubuntu-title.ttf
chris@ubuntu:~/.fonts$
```Only a couple in there, but they are available.
If yours is a mess, you could clear out the folder and start over.

You can also view it using the file browser. go to your home directory, and in the top line, where it says home/yourname type /.fonts <enter> after it ( so that it reads /home/yourname/.fonts ) and it will open up your fonts directory.

(in case you didn't know, the dot before the folder name makes it hidden)

---

