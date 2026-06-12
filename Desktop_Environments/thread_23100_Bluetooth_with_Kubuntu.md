---
title: "Bluetooth with Kubuntu??"
date: 2005-03-31
forum: Desktop Environments
---

### Post by André on 2005-03-31
Hi,

is there a way to send files to a bluetooth device with Kubuntu?

Is there bluetooth support anyways?

Greetings
André

---

### Post by emuman on 2005-04-02
You need a proper bluetooth configuration and kde bluetooth.
1. install bluez-utils, libbluetooth1, libbluetooth1-dev, bluez-pin and configure you bluetooth device. See [http://www.holtmann.org/linux/bluetooth/](http://www.holtmann.org/linux/bluetooth/) and [http://www.bluez.org/faq.html](http://www.bluez.org/faq.html) for details. Make sure that your that bluez finds your bluetooth device.
2. Install kdebluetooth. There are inofficial debian packages, simply add

# kdebluetooth
deb http://fred.hexbox.de/debian ./

to your /etc/apt/sources.list, apt-get update, apt-get install kdebluetooth

If the packages doesn't work for you, install the current CVS:

export CVSROOT=:pserver:anonymous@anoncvs.kde.org:/home/kde
cvs checkout kdeextragear-3/kdebluetooth
cvs checkout -l kdeextragear-3
cvs checkout kde-common
cd kdeextragear-3
ln -s ../kde-common/admin
make -f Makefile.cvs
./configure --prefix=/usr
cd kdebluetooth
make
make install

---

### Post by apokryphos on 2005-04-02
There are also some kdebluetooth packages provided by Simone Gotti, currently:
[https://www.ubuntulinux.org/wiki/SimoneGotti](https://www.ubuntulinux.org/wiki/SimoneGotti)

---

### Post by tnilsson on 2005-09-10
Kdebluetooth is really great! 
Thank you for the information.
Gnome-bluetooth is also good, but I miss the feature to browse all the files
on your phone.

---

