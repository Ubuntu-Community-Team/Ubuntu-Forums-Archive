---
title: "Edubuntu Classroom Control"
date: 2007-04-16
forum: Education &amp; Science
---

### Post by hungrysam on 2007-04-16
I have installed Edubuntu on 10 computers in my elementary computer lab.  They are all connected to the Internet and can all discover the local Windows network, but they cannot find each other.  What do I have to do to set up an edubuntu network?  Also, is there any good network control software that anyone is aware of?  Control Aula looked perfect, but I can't get it installed.  Any help?

---

### Post by rally4life on 2008-03-06
I would also like to install edubuntu 7.10 in my computer lab in an elementary school.  The only thing holding me back from completely switching from XP is that with windows I use a program called LanSchool that allows me to view and control all the computers in my lab (i have 26 computers).  I was wondering if there was an alternative supervision type program for linux.  If anyone has any experience with this type of situation please let me know what you have done.  Thanks.

---

### Post by kesomir on 2008-03-06
try italc

[http://italc.sourceforge.net/](http://italc.sourceforge.net/)

---

### Post by rally4life on 2008-03-07
Thanks, that looks like exactly what I need.  My other problem is getting ubuntu on all the computers in the lab. Like i said, I have 26 PCs and I would like to dual boot with XP and Edubuntu.  I tried using Symantec Chostcast 7.5 (I've used it before to do just Windows images) but when I broadcast the image from the Ghostcast server it gets about half way through and then gives me an error.  Is there another way to do this? I really want to get Edubuntu on these computers.

---

### Post by caveman56 on 2008-03-10
You should try clonezilla, you can setup a DRBL server to multicast or just use a boot cd and use it to create a clone image on a ftp, ssh, nfs, samba, etc server then boot each workstation and pull the image accross the network.  I can do all 23 of my workstations in about an hour using just a boot disc and moving from machine to machine.

---

### Post by kesomir on 2008-03-17
or you could set up a netinstall - boot the system via pxe and automate installations that way.

Then you power on the clients and go grab a coffee.

That said, it's not that simple doing the prep-work... wirth looking into as an option though.

---

### Post by lunkermike on 2008-03-17
I have a lab with 2 LTSP Servers running Edubuntu on 32 machines.  I need to setup LDAP so I can create logins and passwords for my students.  I do not know where to begin........any suggestions

Thanks,

---

### Post by marioquark on 2008-03-19
hey guys! Edubuntu offers us the "Thin Client Manager" under System -> Administration, nothing better...
:)

---

### Post by cmbcne on 2008-03-20
> **hungrysam said:**
> I have installed Edubuntu on 10 computers in my elementary computer lab.  They are all connected to the Internet and can all discover the local Windows network, but they cannot find each other.  What do I have to do to set up an edubuntu network?  Also, is there any good network control software that anyone is aware of?  Control Aula looked perfect, but I can't get it installed.  Any help?

Hi.  I'm looking to help a friend set up some laptops for use by kids in the Dominican Republic.  While researching to find the best distro, I came across gnuLinex, which was created by the regional government of Extremadura, in Spain.  The URL for the ControlAula program looks like it's on their site ([www.linex.org](www.linex.org)), so there may be something in that distro that it needs in order to install correctly.  I don't know if they have an English version but, if they do, it could be an alternative to Edubuntu and work with ControlAula.  Just a thought.

---

