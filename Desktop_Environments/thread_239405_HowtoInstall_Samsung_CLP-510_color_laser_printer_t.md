---
title: "Howto:Install Samsung CLP-510 color laser printer to Ubunutu dapper i386 &amp; x86_64"
date: 2006-08-19
forum: Desktop Environments
---

### Post by ocake on 2006-08-19
Install Samsung CLP-510 color laser printer to Ubunutu dapper i386 & x86_64
sudo adduser cupsys shadow
Insert in /etc/udev/rules.d/60-symlinks.rules
# Create symlink for usb printer to /dev/usb/lp*
BUS=="usb", KERNEL=="lp[0-9]*",         SYMLINK+="usb/%k"
restart udev:
/etc/init.d/udev restart
/etc/init.d/cupsys restart
download latest Samsung CLP-510 driver from [http://downloadcenter.samsung.com/content/DR/200607/20060719124812000_UnifiedLinuxDriver.tar.gz](http://downloadcenter.samsung.com/content/DR/200607/20060719124812000_UnifiedLinuxDriver.tar.gz)
tar -zxvf 20060719124812000_UnifiedLinuxDriver.tar.gz
The package will create a folder call cdroot
The package offer an automatic setup, but it doen't work for me, I can only print half page, therefore, I uninstalled and create it manually.
cd cdroot\Linux, you'll find 3 folders, i386;noarch&x86_64
/cdroot/Linux$ cp noarch/at_root/etc/sane.d/smfp.conf /etc/sane.d/
/cdroot/Linux$ cp noarch/at_opt/share/ppd/CLP-510splc.ppd /usr/share/ppd/linuxprinting.org-gs-builtin/
now we have to go either i386 or x86_64 depends on your distro
For x86_64 we choose x86_64 folder
/cdroot/Linux$ cp x86_64/at_root/usr/lib64/libmfp.so.1.0.1 /usr/lib64/
/cdroot/Linux$ cp x86_64/at_root/usr/lib64/cups/backend/mfp /usr/lib64/cups/backend/
/cdroot/Linux$ cp x86_64/at_root/usr/lib64/cups/filter/* /usr/lib64/cups/filter/
now use browser [http://localhost:631/admin/](http://localhost:631/admin/) to add printer
when prompt for userid and passwd use root and root password
hope this help](*,)

---

### Post by SimonTheMime on 2006-09-04
Thanks for the guide! Worked for i386 too! :D 

Though I don't think it's the fault of the guide, my printer doesn't print colours right.. sometimes not at all.. they just get smeared on the other side of the page..

---

### Post by benjou on 2006-11-15
Hey Thanks!

Works great on ubuntu edgy with a network xerox phaser 6100dn (samsung's and xerox's are in fact the same hardware...)

My modifications:
.Did not do the usb/udev thing (I have a network printer)
.Did have a 386 so everything has to be copied in /usr/lib/* rather than /usr/lib64/* 
.Did use sudo all over (do not have a root account)
.Did use the gnome-add-printer tool insted of CUPS web admin (since I still do not have a root account...)

---

### Post by agecanonix on 2006-12-11
Hi,

Don't know why, I had a message in cups :
"usb:/dev/usb/lp0 : Too many levels of symbolic links". Maybe because another printer was already installed ?

Anyway, I had just to remove /etc/udev/rules.d/60-symlinks.rules (so, maybe, try first to not install it ;) ). Then, I restarded udev and cups, as described, but it was not enough. It started to work when I restarted the computer.

Now, all works well :D 

Thanks.

---

