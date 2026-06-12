---
title: "The latest updates still break the Xserver on Intel !"
date: 2006-08-26
forum: Desktop Environments
---

### Post by abhiomkar on 2006-08-26
The latest updates crashed my Xserver.  
Iam using Intel.
[lspci]("http://paste.ubuntu-nl.org/21704") output > [http://paste.ubuntu-nl.org/21704](http://paste.ubuntu-nl.org/21704)

I have added the fallowing repos & did "sudo apt-get dist-upgrade"

[INDENT]deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper aiglx
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
[/INDENT]

especially, The latest version of the fallowing packages crashed my system, :( 
[INDENT]libpoppler1 0.5.3-0ubuntu1
libpoppler1-glib 0.5.3-0ubuntu1
xserver-xorg-core 1.0.2-0ubuntu10.4
xserver-xorg-driver-ati 6.6.0-0ubuntu1
xserver-xorg-driver-i810 1.6.0-0ubuntu3[/INDENT]

whereas the fallowing versions works fine for me ,  :) 
libpoppler1 0.5.1-0ubuntu7
libpoppler1-glib 0.5.1-0ubuntu7
xserver-xorg-core 1.0.2-0ubuntu10.1
xserver-xorg-driver-ati 6.5.7.3-0ubuntu7
xserver-xorg-driver-i810 1.4.1.3-0ubuntu6

after doing dist-upgrade i rebooted my system...
when i try to login, the black screen appears and it goes back to login screen (gdm) ](*,) 

Any Suggestions ??? :confused: 

Thank you

---

