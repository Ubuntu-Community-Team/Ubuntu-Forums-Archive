---
title: "Install error!!!"
date: 2009-02-05
forum: General Help
---

### Post by Bozmeister on 2009-02-05
Hi

Ok I have searched the forum & FAQ with little success so I've kinda done my bit. ;)  I have installed VirtualBox on Windows Vista premium. Everything ok. Dloaded Ubuntu and burnt image to CD ok. I installed Ubuntu but I get and error message:

Boot from (hd0,0) ext3 680c35ed-f6d7-47a4-9bcc-d63d281d388f
Starting up ...
This kernel requires the following features not present on the CPU:
pae
Unable to boot - please use a kernel appropriate for your CPU. 

I found this nugget of wisdom but being new to Linux I was unsure what to do:

[http://systembash.com/content/installing-virtualbox-pae-kernel-centos/](http://systembash.com/content/installing-virtualbox-pae-kernel-centos/)

Do I need to run this code?
$ yum install kernel-PAE-devel

I am trying to use the Apache server running on the Virtual OS to develop PHP & Mysql

Hope you can help.

---

### Post by beno1990 on 2009-02-05
What's happening is you're trying to boot into a kernel which has PAE enabled, when the virtual machine can't see the PAE feature.

In the VirtualBox settings for that virtual machine (right click the VM on the list and choose settings), go to advanced and tick the box saying "Enable PAE/NX".

---

### Post by redilyn on 2009-02-05
Did you make sure to select Linux & Ubuntu 8.10 when you created your virtual machine?

Maybe this link will help
[http://moxiefoxtrot.com/2009/01/05/installing-ubuntu-810-in-virtualbox/](http://moxiefoxtrot.com/2009/01/05/installing-ubuntu-810-in-virtualbox/)

---

### Post by Bozmeister on 2009-02-05
It seems to work now after i checked the pae kernel thingy. Thanks for the help.:p

---

