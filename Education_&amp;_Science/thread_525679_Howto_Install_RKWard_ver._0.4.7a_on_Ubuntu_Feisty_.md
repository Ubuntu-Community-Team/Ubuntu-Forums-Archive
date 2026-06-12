---
title: "Howto: Install RKWard ver. 0.4.7a on Ubuntu Feisty (7.04)"
date: 2007-08-14
forum: Education &amp; Science
---

### Post by akniss on 2007-08-14
I've seen some folks having trouble getting RKWard to work on Ubuntu Feisty.  I decided to see if I could get it working on my machine, and was able to get it up and running.  I thought I'd post how I did it in case it might help someone else.

First of all, the RKWard package in the Ubuntu repos is broken, and a simple apt-get install rkward did not give me a functional package.  Here's what I did to get it woking.

[LIST]
[*]Download version 0.4.7a (rkward-0.4.7a.tar.gz) from:
[Sourceforge.net]("http://sourceforge.net/project/showfiles.php?group_id=50231&package_id=43758")
[*]Obtain the required packages for RKWard to compile:
```
sudo apt-get build-dep rkward
```
[*]Extract the .tar.gz and change into the rkward-0.4.7a directory
[*]Enter the following commands:
```
sudo ./configure
sudo make
sudo make install
```
[*]Start RKWard by entering ```
rkward
``` at a terminal, or hitting Alt+F2 and entering rkward.
[/LIST]

---

### Post by carlao2005 on 2007-10-26
Hello,

Your link to sourceforge has "http://" twice.

Best regards
Carlos

---

### Post by akniss on 2007-10-27
> **carlao2005 said:**
> Hello,
Your link to sourceforge has "http://" twice.
Best regards
Carlos

Fixed. Thanks.

---

### Post by Tart on 2007-10-28
Thank you for posting this guide.

---

### Post by cseljatib on 2007-12-24
excellent, it works!!!

change 
sudo make intsall

to 
sudo make install

cheers

---

### Post by akniss on 2007-12-26
> **cseljatib said:**
> 
change sudo make intsall to sudo make install


Fixed.  Thanks!

---

