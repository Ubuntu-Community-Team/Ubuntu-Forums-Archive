---
title: "Were Are ubuntu files stored in Windows?"
date: 2009-04-17
forum: General Help
---

### Post by al3nmikho on 2009-04-17
I know that the windows files are stored in host in ubuntu but were is the Ubuntu files stored in Windows ? :(

---

### Post by al3nmikho on 2009-04-17
Can anyone help me please!

---

### Post by eruptionjoojo on 2009-04-17
One cannot directly access files stored in ubuntu partition via windows due to the difference in file systems ..............
In order to view these files you may try either of the following listed softwares:-

[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by sschnee on 2009-04-17
I'm not sure I understand your question.  To be clear, you have a dual boot system, and have separate partitions for each OS, right?

Are you asking how to access your Ubuntu partition while running Windows?

---

### Post by al3nmikho on 2009-04-17
Correct, but I can't acess ubuntu due to  a weird error so I want to acess the files using windows and save a backup before I format.

---

### Post by DeMus on 2009-04-17
> **al3nmikho said:**
> Correct, but I can't acess ubuntu due to  a weird error so I want to acess the files using windows and save a backup before I format.

It's easier to use the Ubuntu live cd. With that you can boot your pc and access all the files on your hard disks, both Windows and Ubuntu.

---

### Post by mcduck on 2009-04-18
> **al3nmikho said:**
> I know that the windows files are stored in host in ubuntu but were is the Ubuntu files stored in Windows ? :(

Windows isn't able to read any other file systems than it's own (FAT & NTFS). So you need to install some 3rd party driver to add the support for what ever fs you are using on Ubuntu. (Ext3, most likely, so try Ext-IFS: [http://www.fs-driver.org/]("http://www.fs-driver.org/"))

However since you are talking about a "host" I started thinking that you may have installed Ubuntu inside Windows with Wubi? In that case I'm not sure if you can access Ubuntu's files at all from Windows (I don't think any of the Ext drivers is able to do loop mounting of file systems which you'd need to access Ubuntu when it's not on it's own partition).

---

