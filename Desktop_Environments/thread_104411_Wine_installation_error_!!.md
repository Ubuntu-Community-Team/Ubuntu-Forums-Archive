---
title: "Wine installation error !!"
date: 2005-12-16
forum: Desktop Environments
---

### Post by index_0@ya.com on 2005-12-16
Hi thr , 
     i tried to install wine in my system equipped with ubuntu 5.10 ,but only the following error message resulted in and installation aborted ,, ..

prompt> sudo dpkg -i wine_0.9.2-winehq-1_i386.deb
(Reading database ... 57157 files and directories currently installed.)
Unpacking wine (from wine_0.9.2-winehq-1_i386.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing wine_0.9.2-winehq-1_i386.deb (--install):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Errors were encountered while processing:
 wine_0.9.2-winehq-1_i386.deb

pls help
Thx in advance ,

---

### Post by dcstar on 2005-12-16
[QUOTE=index_0@ya.com]Hi thr , 
     i tried to install wine in my system equipped with ubuntu 5.10 ,but only the following error message resulted in and installation aborted ,, ..

prompt> sudo dpkg -i wine_0.9.2-winehq-1_i386.deb
(Reading database ... 57157 files and directories currently installed.)
Unpacking wine (from wine_0.9.2-winehq-1_i386.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing wine_0.9.2-winehq-1_i386.deb (--install):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Errors were encountered while processing:
 wine_0.9.2-winehq-1_i386.deb

pls help
Thx in advance ,[/QUOTE]

Add this repository and use Synaptic to install the latest wine:

[http://wine.sourceforge.net/apt](http://wine.sourceforge.net/apt) breezy/

---

### Post by index_0@ya.com on 2005-12-16
hey .. thx for ur  reply .. but i  dont have net connection to directly use synaptic  . .. i download at off and try to install at home !!.. 
 
any reply for me ??

---

### Post by kosmic on 2005-12-16
Hum download again the wine.deb file it looks like it is corrupted

---

### Post by index_0@ya.com on 2005-12-16
ok ..thx for suggestion .. 
ll do it

---

