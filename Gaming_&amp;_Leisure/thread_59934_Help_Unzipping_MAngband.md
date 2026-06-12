---
title: "Help Unzipping MAngband"
date: 2005-08-25
forum: Gaming &amp; Leisure
---

### Post by Master Shake on 2005-08-25
I downloaded MAngband, and was trying to unzip it and I got the following error:

cp: cannot stat `/tmp/fr-wWMYoY/mangclient-061.glibc-2.1.linux': No such file or directory

What am I doing wrong?  Do I need to be logged in as root for this?

BTW, I am a linux newb (in case you  couldn't tell)

---

### Post by amohanty on 2005-08-26
What is the file called - the full name?
Where did you download it to?
What command did you use to unzip it?

AM

---

### Post by Master Shake on 2005-08-26
The file is called mangclient-061.glibc-2.1.linux.gz

Stored in a folder called Mangband which resides on the desktop, and I double click it, and it opens with File Roller

---

### Post by amohanty on 2005-08-26
Opena terminal and type in:
cd <path to where file is located>
gunzip mangclient-061.glibc-2.1.linux.gz

This will unzip it in the same location.

HTH
AM

---

