---
title: "Unplugged Freezing"
date: 2012-08-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Chisale on 2012-08-29
Hi all,

I'm currently running ubuntu 12.04 lts on a dell vostro 3700 machine. My problem is that the moment the machine is unplugged, the system just freezes. How can I fix this??

Please help

---

### Post by grc01 on 2012-09-07
try this, it work for on Vostro and Inspiron
  	 	 	 	 	 	   Open up Synaptic Package Manager
 
[LIST=1]
[*]Settings > Repositories > 	Other Software, then add the following:
[*]deb 	[http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid main
[*]“Reload” the package list
[*]Find “pm-utils” then go to 	Package > Force Version.. and select 1.3.x
[*]Install the downgraded package
[*]Find “pm-utils” again, go to Package > Lock Version
[/LIST]

---

### Post by Chisale on 2012-09-14
Thanks a lot grc01.

Now the system can work unplugged.
Much appreciated.

---

