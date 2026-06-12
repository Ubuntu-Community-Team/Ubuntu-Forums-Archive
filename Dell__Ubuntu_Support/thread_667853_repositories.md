---
title: "repositories"
date: 2008-01-14
forum: Dell  Ubuntu Support
---

### Post by gpmartinson on 2008-01-14
Is there a Dell-specific apt-repository?  I have a Inspiron E1505 that I just put Ubuntu on and I thought I had heard that Dell was planning on rolling out something like this for drivers.  Maybe it was the meth...:guitar:

---

### Post by natehall on 2008-01-15
I do believe [this]("http://linux.dell.com/wiki/index.php/Repository/software") answers your question!

---

### Post by earobinson on 2008-01-15
so they have a red hat one but no ubuntu one :(

---

### Post by natehall on 2008-01-15
Take another look,. It has Red Hat , Debian and Suse files ! (As you may already know, Debian is what Ubuntu is built on )

---

### Post by Omnios on 2008-01-15
Hi hi I would like to see the Dell Ubuntu repositories get stickied on the dell support section. Also possibly have a hole bunch of dell links there including the native dell support links and possibly the dell forum,

 Other sections have this and think that this may be helpful for dell users.

---

### Post by gpmartinson on 2008-01-15
Fascinating, but I am not sure I understand what is in there.  I look in the debian folder and there are no deb files.  
Further study finds: 
[http://linux.dell.com/wiki/index.php/Repository/hardware](http://linux.dell.com/wiki/index.php/Repository/hardware)
Of particular note, the following operating systems have problems:

Debian/Ubuntu: not yet. 

Thanks though.  It appears that its pretty much hardware updates and bios things, which will be cool.

---

### Post by natehall on 2008-01-15
> **earobinson said:**
> so they have a red hat one but no ubuntu one :(
I just tried loading the program package listing. I see what you mean.This is what came up:

sudo wget -q -O - [http://linux.dell.com/repo/software/bootstrap.cgi](http://linux.dell.com/repo/software/bootstrap.cgi) | bash

Unable to determine that you are running an OS I know about.
Handled OSs include Red Hat Enterprise Linux and CentOS,
Fedora Core and Novell SuSE Linux Enterprise Server and OpenSUSE

Perhaps somebody familiar with one of those distros can tell us Ubuntu users how to get this repository into our package manager.

---

### Post by gpmartinson on 2008-01-16
I guess this is not ready for prime-time.  Thelinuxactionshow may need to update this.  I think this would be a really great way to do things.

---

