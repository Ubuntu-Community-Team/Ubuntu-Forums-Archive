---
title: "MS Office 2003"
date: 2006-02-22
forum: Desktop Environments
---

### Post by kelsey23 on 2006-02-22
Ok, so I have MS Office 2003 and CrossOver Office 5. I know it is possible to install MS Office 2003 on CrossOver Office 5, but it fails everytime I do it. I'm sure someone here has Office 2003 on CrossOver Office, could you tell me why it is doing that/what needs to be done for it to function properly? Thanks :)

---

### Post by yanik on 2006-02-22
Well, since you PAID for crossover office 5, you should try to get support from them or their forum, if any.

May I ask what feature you need in ms office 2003 that isn't in OpenOffice.org 2?

---

### Post by kelsey23 on 2006-02-22
I use AbiWord...OO.o sucks..but I wanted to see what MS Office is like more than use it full time. Btw, there is a TRIAL version of Crossover Office 5, as well as for MS Office 2003 <_<

---

### Post by art on 2006-02-22
In case you haven't solved it yet, in terminal
sudo umount /media/cdrom
mount -t iso9660 -r -o unhide /dev/cdrom /media/cdrom

it should work now!

---

### Post by kelsey23 on 2006-02-22
ok thanks, but this is another issue...I downloaded the 60 day Trial from MS, so it comes in an "Office.exe" file.

---

### Post by art on 2006-02-22
Oh, I didn't know... Well, what is it complaining about?

---

### Post by kelsey23 on 2006-02-22
after it extracts a few CABs a small dialog box will pop-up saying "INSTALL_ERROR"

---

### Post by art on 2006-02-22
not very imformative... I have no clue... If you could borrow an installation CD then use the licence code of your trial MS OFFICE that should work I guess.

---

### Post by xhie on 2006-02-23
Wait... Im sort of confused... MS Office will run on linux all by itself? Without wine or anything I mean? Or am I just reading that wrong?

---

### Post by hyper84 on 2006-02-23
[QUOTE=xhie]Wait... Im sort of confused... MS Office will run on linux all by itself? Without wine or anything I mean? Or am I just reading that wrong?[/QUOTE]

They are using Crossover Office, which is sort of like a commercial wine.

---

