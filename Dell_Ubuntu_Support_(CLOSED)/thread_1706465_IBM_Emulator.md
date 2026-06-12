---
title: "IBM Emulator"
date: 2011-03-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jimmyozuna on 2011-03-13
I do not know where to post this but perhaps this will be a good start.  I want to replace my Windows OS with Ubuntu but have a concern before I do.  I currently use my laptop for work and I use a program called Blue Zone in order to connect to the mainframe and do my work.  Unfortunately this Blue Zone software requires a Windows OS so I cannot do the changeover just yet.  My question is: Does anyone know of a program that I can download that would allow me to do the same as Blue Zone but in Ubuntu?

---

### Post by islamada on 2011-12-15
Hi, 
Did you find a solution yet, I am having the same dilemma. 
Thanks

---

### Post by gbrainin on 2011-12-16
It depends on what the software is doing.  It's not quite clear to me from the website what this package is.

Ubuntu has several remote access capabilities preinstalled (and countless more available for download), but you'll need to find out what protocol your server is using in order to know which one is best to use.  Hopefully, "Blue Zone" uses a standard protocol, and you can simply run a Linux package that uses the same one.  If it uses something proprietary, you might have a problem . . . but that problem might be solvable by running their software under WINE.

---

### Post by Lars Noodén on 2011-12-16
> **islamada said:**
> Hi, 
Did you find a solution yet, I am having the same dilemma. 
Thanks

Do you mean by chance a TN3270 emulator?  If so there are several choices in the repository: x3270, s3270, c3270 and maybe others.

---

