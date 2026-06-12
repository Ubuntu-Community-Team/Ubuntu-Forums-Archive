---
title: "Ext Security and Windows EXT driver"
date: 2006-03-20
forum: Desktop Environments
---

### Post by pwrstick on 2006-03-20
Hello! I searched around but couldn't find much.  Beeing a nub I'd like to hear people comments about using the EXT driver in Windows to compromise a linux box, via lack of access rights:

*The current version of the Ext2 file system driver does not maintain access rights. All users can access all the Ext2 volumes that a drive letter is created for. **For example, if a drive letter has been created for an Ext2 volume, which is the root volume of a Linux installation, you can simply read and modify files such as /etc/passwd and /etc/shadow. User names are readable and passwords of these users can be quite easily cracked and modified!***

Seeing as it's possible to boot Windows off a flash drive (tho I haven't done it myself) I'm wondering if this is potentially a security hazard.  Of course they say if someone is able to physically access your machine housing important secure data, you have bigger problems (i.e. lock important boxes away).

Afterall, a lot can be done to a Windows box if you can get physical access to it...  Anyway just wondering what you guys think.

Cheers!

---

### Post by GTvulse on 2006-03-20
It is much easier to boot off a live cd or linux on a flash drive. Once you have physical access to a computer, there is nothing you cannot do to obtain the data stored in it. If you really want to secure a system, you encrypt the file systems, unhook it off the internet, keep it in a locked vault and protect it with an army with orders to shot anyone who gets closer to a hundred meters of the site.

A more valid question would be if the ext-fs driver causes data corruption of not. I can talk about unspeakable amounts of file fragmentation...

---

### Post by pwrstick on 2006-03-20
Yeah... I'm working on that Army budget.

---

