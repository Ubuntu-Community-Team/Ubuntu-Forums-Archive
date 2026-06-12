---
title: "How install Lexmark Z617?"
date: 2006-01-12
forum: General Help
---

### Post by Alexandre Ortiz on 2006-01-12
Hi all,

I download the driver from Lexmark Z617, but not work (not install too!). This driver is Red Hat...

Somebody can help me to install this printer on Ubuntu? 

* The printer is recognized on System Information on USB

---

### Post by BOMBMASTAH on 2008-03-14
Hi, I have the same problem. I hope that someone help us soon.](*,)

---

### Post by danwood76 on 2008-03-14
According to the open printing database ([http://openprinting.org/printer_list.cgi?make=Lexmark](http://openprinting.org/printer_list.cgi?make=Lexmark)) the Z617 doesnt work with linux, though sometimes this info is out dated.

But if you have redhat drivers (.rpm package) then you could try to alienate the packages (convert to .deb for debian package) and install them that way.

-- edit --

Guide to alienating packages:
[http://www.ubuntu-unleashed.com/2008/03/howto-convert-redhat-and-fedora-rpm.html](http://www.ubuntu-unleashed.com/2008/03/howto-convert-redhat-and-fedora-rpm.html)

---

### Post by Sef on 2008-03-14
If you can't get danwood76's idea to work, then your best bet would be to get another printer.  [OpenPrinting Suggested Printers]("http://www.linux-foundation.org/en/OpenPrinting/Database/SuggestedPrinters") says that either HP or Epson.  If you are a causual user, then HP would be best.

---

### Post by Radioman991 on 2008-03-14
I got danwoods idea to work (actually from another thread, but I don't hav the link handy) for a Z611 I have.  Took a little work,  but it prints.  Took the 2 .deb packages to my father-in-law, who has the same printer, and he prints too!

I was looking at trashing a couple printers until I tried and successfully installed them.

---

### Post by BOMBMASTAH on 2008-04-01
Hallo, again its me. Thanks to everybody hos write about the problem. I find the light in the end of the dark. This is the link : [http://ubuntuforums.org/archive/index.php/t-83456.html](http://ubuntuforums.org/archive/index.php/t-83456.html)

It works on me 100%.:guitar:

---

### Post by ashvee on 2008-04-02
ANY DRIVER FOR A x5470

---

### Post by danwood76 on 2008-04-02
> **ashvee said:**
> ANY DRIVER FOR A x5470

[http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-x5470](http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-x5470)
[http://forums.linux-foundation.org/read.php?29,926](http://forums.linux-foundation.org/read.php?29,926)
Lexmark linux support is poor at best.

If you can find rpm (redhat package) drivers from lexmark have a go at alienating them (guide a previous link in the thread) the guys earlier in the thread seemed to have a great success with that method.

Just had a quick look at lexmark dont even do redhat drivers:
[http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=227:5:0:549:0:0](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=227:5:0:549:0:0)

---

### Post by ashvee on 2008-04-10
thnxs

---

