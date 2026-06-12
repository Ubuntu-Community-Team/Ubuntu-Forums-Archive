---
title: "OpenOffice.org 2.0 Base Wizards Do Not Load"
date: 2006-01-05
forum: Desktop Environments
---

### Post by apollo2011 on 2006-01-05
OK, I have a pretty fresh OOo2.0 installation, and whenever I create a new database (or open an old one), none of the Wizards (Table Wizard, Form Wizard, Report Wizard etc.) open, I click on them, and the program sometimes seems to freeze for a little bit, but always continues as if nothing happened.  Does anyone know why I can't get the wizards to open?

---

### Post by Sef on 2006-01-09
What version of OO2 are you running?  2.01 or 1.92?

---

### Post by semaj on 2006-01-29
I have the same problem.  The database wizards worked when I first installed 'breezy' about 1 month ago (my first introduction to the world of linux).  Now they don't.  Also just had to fix a problem with libhsqldb2.so as per another thread.  Has an automatic update cause this perhaps?:confused:

---

### Post by semaj on 2006-01-29
Oh - its version 1.9.129.  Is there a later version with bugs fixed?

---

### Post by william_nbg on 2006-01-29
I've got the newest version, but have the same problem. I read on the OO forum it may be that there are old files left somewhere from the older version and they should be all cleaned out but I'm not sure how to do that. 

Any ideas??

---

### Post by paulbarbee on 2006-02-11
I am using the newest version (.2.0.1)and people.ubuntu.com/~doko/OOo2/ is my repository. In Base the table wizard works, but the form wizard and the report wizard won't. The form wizard doesn't do anything when I click it. The report wizard opens a new Writer document, puts the date, a bar across the bottom gets part way through and then nothing. This works in Windows and it worked last time I used it in Fedora several months ago. What's wrong??? Any ideas? I'd really like to use Kubuntu for OO.o Will somebody please help.

---

### Post by william_nbg on 2006-02-11
I had the same problem with the wizards. 

Fixed it by:

1. Uninstalled everything from openoffice 2 using Synaptic.

2. Blocked the openoffice 2 repository in my sources.list file.

3. Downloaded the deb's from this link:

[http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/](http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/)

 and installed them. (used the rc5, but if your into the bleeding edge stuff take the snapshot)

Everything works great now.

---

### Post by paulbarbee on 2006-02-11
Yes, that solution works very well. Thank you very much!:-D

---

### Post by penguin007 on 2006-12-20
Just for clarity sake: installing OpenOffice .deb packages (or any other .deb package for that matter) is done with:

sudo dpkg -i *.deb

in the directory where you have extracted the .deb's to.

---

### Post by dennis1200 on 2007-06-05
A nice [summarized guide]("http://www.linuxmint.com/forum/viewtopic.php?highlight=openoffice&t=1190") can be found at the Linux Mint forums. I assume the debs on the .cz mirror listed above were made this way, since most OOffice mirrors only carry a tarred collection of RPMs.

I just did it and it works wonderfully now, form wizards and all. Unfortunately, I've lost GNOME integration - something I have to look at. But it's bedtime, so that will be for another day...

---

