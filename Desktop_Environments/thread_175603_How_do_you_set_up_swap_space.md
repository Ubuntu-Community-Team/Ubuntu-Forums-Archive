---
title: "How do you set up swap space?"
date: 2006-05-13
forum: Desktop Environments
---

### Post by wieserxx on 2006-05-13
During installation it said entering low memmory mode, set up swap space ASAP.

---

### Post by tonyr on 2006-05-13
Usually it is done by creating a **swap** partition, but it can also be
done using a file.  Read the man page for **mkswap**.  If It's too
complicated, or you don't recognize things that it's talking about,
we'll try to walk through it.

---

### Post by tonyr on 2006-05-13
Maybe I jumped the gun, here.  Please describe your situation a little bit more:
machine, operating system, disks, existing partitions, your level of Linux/Ubuntu
experience.

---

### Post by wieserxx on 2006-05-13
I am a newbie. The computer is a 166 pentium , SYS RAM-640KB, NEC DESKTOP. It had two partitions, but i deleted both of them, in hopes of useing linux as the sole OS. It is still installing.

---

### Post by wieserxx on 2006-05-13
Now it went to the second stage of installation. There is now a command prompt on the screen that says "grub>". What do i do?

---

### Post by tonyr on 2006-05-13
Your machine may be too small to support Ubuntu. You should look at the
web page [URL="http://ftp.ubuntulinux.org/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/ch03s04.html"]
http://ftp.ubuntulinux.org/ubuntu/dists/breezy/main/installer-i386/current/doc/manual/en/ch03s04.html[/URL]

I assume you have internet access, since you are using this forum.  You
really should read an installation guide.  Which version of Ubuntu are you
installing?  Breezy (5.10)?  Dapper (6.06)?  Here is a link to a guide for
installing the Dapper version:
[URL="http://www.krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide"]
http://www.krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide[/URL]

and here is one for Breezy:
[URL="https://wiki.ubuntu.com/Installation/I386"]
https://wiki.ubuntu.com/Installation/I386[/URL]

During the installation process you should have come to a **Partitioning**
section.  What did you do at that point?  You should have selected something
like **Auto-Partition**.

---

### Post by wieserxx on 2006-05-13
I chose use the largest free space.

---

### Post by wieserxx on 2006-05-13
And it is 5.10.

---

### Post by tonyr on 2006-05-13
[QUOTE=wieserxx]Now it went to the second stage of installation. There is now a command prompt on the screen that says "grub>". What do i do?[/QUOTE]

The Breezy manual that I suggested says to hit the Enter key, which will cause 
your machine to reboot and continue with the installation.

---

### Post by wieserxx on 2006-05-13
If i hit enter it will just move down a space. It's waiting for a command.

---

### Post by tonyr on 2006-05-13
Well, I'm out of my league now.  The manual says it should reboot into the
second stage.  If that's not happening, something else is wrong.

I strongly suggest that you read the Minimum Requirements document
and the Installation Manual.  You might have to redo the installation and
select Auto-Partition.  I've never used that option, but from what I have read,
it should make one Linux partition and one swap partition.

---

