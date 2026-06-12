---
title: "[SOLVED] elements of my menu dissapear"
date: 2008-03-13
forum: Desktop Environments
---

### Post by ubuntu_jazzbach on 2008-03-13
Hi !!!

I booted my ubuntu normally and I needed to install a package so, I opened Sistem -> administrator and suprise !!! Synaptics was gone !!!

So I left-clicked over the "system" section in my panel and selected "edit-menus". Under the "Administration" section there was synaptics unchecked, so I checked it but it unchecked it by itself in less than a second. I noticed that the options that "uncheck" themselves were in Italic font.

How can I solve this ??

Thanks in advance.

---

### Post by ubuntu_jazzbach on 2008-03-16
I've solved it !!!

It had to do with adding the user to the corresponding group.

WARNING. Any further change of the following file may corrupt your system.

1.- let's backup the /etc/group file

> sudo cp /etc/group /etc/group.bak

2.- Open the file with your favorite text editor

> sudo nano /etc/group

3.- Search in the file the line that starts with "admin". It sould look something like this:

> admin:x:114:

4.- and add your current username at the end of the line. My username is "jazzbach" so, it should look something like this:

> admin:x:114:jazzbach

5.- Save the file and restart your computer

---

