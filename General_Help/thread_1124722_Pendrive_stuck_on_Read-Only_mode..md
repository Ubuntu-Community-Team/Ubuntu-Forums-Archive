---
title: "Pendrive stuck on Read-Only mode."
date: 2009-04-13
forum: General Help
---

### Post by Marlonsm on 2009-04-13
Today I had to take some files to a computer in my school (it uses Windows and is used by students, so it's very likely to have viruses), I used my pendrive and could save the files there.

Later, I got home and needed to put some other files in the pendrive. I've booted Ubuntu, put the pendrive and when I was copying the 25 files, it said "copying 8 files", the transfer had frozen and then Nautilus crashed.
Some of the files I copied were actually transfered, but the names were all messed up.
I deleted them and started copying again, but this time Ubuntu said the pendrive was on read-only mode, and I couldn't even change the permissions for it. I tried everything I could think of, even using the terminal to copy the files as root.

Could a virus on the school computer do it? or is it just coincidence?

This is what I get when I right-click the pendrive folder, go to properties and try to change the permissions:

[IMG]http://img151.imageshack.us/img151/2929/screenshot2i.png[/IMG]

---

### Post by wilbbe01 on 2009-04-13
Did you try pulling it out and sticking it back in?

---

### Post by Marlonsm on 2009-04-13
> **wilbbe01 said:**
> Did you try pulling it out and sticking it back in?

I did, nothing happens.

---

### Post by wilbbe01 on 2009-04-13
What format is the drive in?

---

### Post by Marlonsm on 2009-04-13
I opened Windows and could write to the drive normally.

It's FAT.


I'm now doing Windows' error check in it.

---

### Post by Marlonsm on 2009-04-13
I've reformatted it to FAT32 using Windows.

Now it's working.

Thx, anyway.

BTW, how do I reformat my pendrive in Ubuntu?

---

