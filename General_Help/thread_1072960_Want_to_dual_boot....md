---
title: "Want to dual boot..."
date: 2009-02-17
forum: General Help
---

### Post by teamsupreme on 2009-02-17
Hey. I want to dual boot Windows XP on Ubuntu 8.10, but I need some help. How do I install the whole dual boot thing, and I have a Dell Recovery Disc that my nephew gave me...can I use it? Thanks!

---

### Post by handy on 2009-02-17
If windows is already installed, then you can just go through the Ubuntu installation process & it will give you the tools to resize the windows partition & install Ubuntu on the newly made space.

It is a very common procedure & has become quite well polished these days in Ubuntu.

---

### Post by teamsupreme on 2009-02-18
I have Ubuntu isntalled, but no Windows...so what do I do?

---

### Post by handy on 2009-02-18
You will need to boot up the Ubuntu LiveCD & shrink the Ubuntu install to the size that you require, then move it to the right hand side making room for your windows install, so the C: drive is first after the MBR of the disk.

When you install windows onto the drive it will rewrite the MBR & you will loose access to your Ubuntu drive, after which you will have to use the Ubuntu LiveCD to remedy the situation.

The above is the run down as I see it.  Do a search of the forums & you will find a step by step how-to which will make the job a lot easier for you.  The how-to does exist, as I have seen references to it. ;-)

---

### Post by teamsupreme on 2009-02-18
I already have Ubuntu installed...now how do I install Windows?

---

### Post by handy on 2009-02-18
I told you in my above post how it works.

I also mentioned in my previous post that you should search out the existing how-to that answers your question. :-)

Anyway, I did a search for you & found the following how-to; it goes step by step & has pictures.  It won't get any easier than this set of instructions:

*_[http://davestechsupport.com/blog/2008/03/22/how-to-install-windows-after-ubuntu-with-gparted/](http://davestechsupport.com/blog/2008/03/22/how-to-install-windows-after-ubuntu-with-gparted/)_*

---

### Post by teamsupreme on 2009-02-18
Oh...Thanks!

---

