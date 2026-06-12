---
title: "Where is Opera browser DEB file?"
date: 2006-07-13
forum: Desktop Environments
---

### Post by larryalk on 2006-07-13
I've looked all over for an Opera DEB file without success but notice a few people here have mentioned it.
Apparently it was released for Badger June 30.

Can anyone give me a pointer?

I also tried (from this thread):
Update the package 'app-install-data-commercial' and then choose "Applications->Add/Remove". It's in there.

The best I could find on Opera's web site was: opera-9.0-20060616.6-shared-qt.i386-en.tar.gz
which was labled as a Badger 6.06 file.

Although I know how to install a tar.gz file and installed Opera that way on other Linux distibutions,  I would prefer to install Opera the Debian / Ubuntu way. 

Larry

---

### Post by linuxnewbie946 on 2006-07-13
I looked for it on [http://packages.ubuntulinux.org/]("http://packages.ubuntulinux.org/") bbut didn't find anything so it looks like you will have to install it from the source.

---

### Post by -Phi- on 2006-07-13
You can get it from the Dapper Commercial Repository. There's more information about it here:

[http://ubuntu.wordpress.com/2006/07/08/introducing-the-dapper-commercial-repository/]("http://ubuntu.wordpress.com/2006/07/08/introducing-the-dapper-commercial-repository/")

- Phi

---

### Post by juanjojo73 on 2006-07-13
Hallo, 

try this repository:
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

---

### Post by ZBREAKER on 2006-07-13
Or you could just go with Automatix and get Opera and a whole lot 
more if you'd like:)

---

### Post by aysiu on 2006-07-13
You can use the commercial repository or just download the Ubuntu .deb at the Opera website:
[http://www.opera.com/download/index.dml?opsys=Linux%20i386&lng=en&ver=9.0&platform=Linux%20i386&local=y](http://www.opera.com/download/index.dml?opsys=Linux%20i386&lng=en&ver=9.0&platform=Linux%20i386&local=y)

---

### Post by larryalk on 2006-07-13
Thanks to the pointer to the new commercial repository.  After adding it to Adept, Opera came up in the list!

One slight problem.  I used Adept to load Opera and it did not appear in either the K menu or desktop.  Same after I requested reinstall and applied changes.  Are commerical apps being handled differently?

I used:
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

Where are the downloaded programs (or a list) kept so I can check further?

Larry

---

### Post by larryalk on 2006-07-13
Problem loading Opera solved.

There was no problem - it's just that Adept didn't add an icon to either the desktop or K menu.

So I used 'which opera' to find the executable, made a new 'link to application' on the desktop - and there it was.  

I'm a very happy camper now.
Again my thanks to all.  I've noticed that the Ubuntu people are quite friendly and helpful unlike my experiences in another (unnamed) distro.

Larry

---

