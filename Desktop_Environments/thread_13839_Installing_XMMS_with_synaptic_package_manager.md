---
title: "Installing XMMS with synaptic package manager"
date: 2005-02-03
forum: Desktop Environments
---

### Post by kyle on 2005-02-03
For some reason i can not get synaptic to install XMMS.  the file of have is XMMS-1.2.10.tar.gz.  I know that i am missing something really obvious but i can't sem to figure it out, so i am hoping that someone can point me in the righ direction.  Thanks

---

### Post by mpie on 2005-02-03
you have downloaded a source package you would need to unpack this (right click on it and select extract)
now open a terminal change directory to where you unpacked it cd /home/Desktop/yourname/xmms1.2.10
./configure --prefix=/usr

you will see loads of configure text when its done
type make
again you will see text
when its done
sudo make install
will install it globally for you


alternatively delete it amend your apt reposities and grab the .deb version alot easier  =P~

---

### Post by kyle on 2005-02-03
thanks.....but i get an error when i do ./configure
it reads: no acceptable C compiler found in $PATH

---

### Post by mpie on 2005-02-03
ok open synaptic and add gcc++ and try again or take the easier option
click on settings then repositories uncheck the other boxes
click refresh then grab the xmms1.2.10-i386.deb

no need to compile then :)

---

### Post by kyle on 2005-02-03
I got it!! yay.  Anyway....here is the thread i used to install it.  [http://ubuntuforums.org/showthread.php?t=10017&highlight=error%3A+acceptable+compiler+found+%24PATH](http://ubuntuforums.org/showthread.php?t=10017&highlight=error%3A+acceptable+compiler+found+%24PATH)

---

