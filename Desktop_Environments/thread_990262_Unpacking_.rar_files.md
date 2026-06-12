---
title: "Unpacking .rar files"
date: 2008-11-22
forum: Desktop Environments
---

### Post by yonyz on 2008-11-22
Hi,

I'm using Ubuntu 8.10.

I have an .iso file that is packed into 5 .rar files - part1.rar, part2.rar, etc..

I've downloaded the RAR 3.80 Trial for Linux from [www.rarlab.com](www.rarlab.com).

That software I've downloaded is packed into a .tar.gz file - how do I install it?

Thanks in advance.

---

### Post by keithld on 2008-11-22
Right click on the file and let "Archive Manager" open it...

Archive Manager should also open your other file....

---

### Post by taurus on 2008-11-22
Assuming you are in the directory where those rar files are, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install unrar
unrar x par1.rar
```

---

### Post by yonyz on 2008-11-22
OK, I used Archive Manager to extract the content of the RAR 3.80 software .tar.gz archive.
Now I got a folder called "rar" with the following files:

default.sfx
file_id.diz
license.txt
Makefile
order.htm
rar
rar.txt
rarfiles.lst
rar_static
readme.txt
technote.txt
unrar
whatsnew.txt

How do I run and use this software to unpack the .rar files?
I tried opening the .rar files with Archive Manager, but I get a "Archive type not supported" error.

Note that my Linux PC is not connected to the internet, so I can download anything from Terminal.
Instead, I download everything from a laptop with Win XP, and copy the files to the Linux PC with a USB MP3 player.

---

### Post by taurus on 2008-11-22
You can move that unrar to /usr/bin so it's on your path.

```
sudo cp unrar /usr/bin
source ~/.bashrc
unrar x part1.rar
```
Again, assuming you are in the directory where the unrar is and part1.rar is.  Otherwise, you need to include the whole path.

---

### Post by yonyz on 2008-11-22
I get a "Permission denied" error when trying to move the file "unrar" to the folder "/usr/bin".

---

### Post by taurus on 2008-11-22
Sounds like you are using nautilus.  Run nautilus from a terminal with a root privilege.

```
gksudo nautilus
```

---

### Post by yonyz on 2008-11-22
OK, I got to the root folder. 
Now what?

---

### Post by taurus on 2008-11-22
Just navigate to where you have unpacked the rar.tar.gz and move the unrar to /usr/bin.

---

### Post by yonyz on 2008-11-22
OK, I successfully moved the file "unrar" to the folder "/usr/bin".
I don't understand what to write in the terminal.

It's my first day using Linux, so please try to explain to me what I should write exactly.

---

### Post by yonyz on 2008-11-22
So after I moved "unrar" to "usr/bin", Archive Manager now opens .rar files.

Thank you all.

---

### Post by pietjanjaap on 2008-11-22
Try peazip, has a nice gui.

---

### Post by tcavazos on 2009-03-12
thanks man, worked perfect for me.

---

