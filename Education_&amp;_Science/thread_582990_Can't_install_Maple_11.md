---
title: "Can't install Maple 11"
date: 2007-10-20
forum: Education &amp; Science
---

### Post by durus on 2007-10-20
Hi I am trying to install Maple 11 on Ubuntu 7.10 but I gets this error msg:
> Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...

gzip: /tmp/install.dir.6964/Linux/resource/vm.tar.Z: not in gzip format

gzip: /tmp/install.dir.6964/Linux/resource/vm.tar.Z: not in gzip format

gzip: /tmp/install.dir.6964/Linux/resource/vm.tar.Z: not in gzip format
The included VM could not be uncompressed (GZIP/UNCOMPRESS). Please try to
download the installer again and make sure that you download using 'binary'
mode.  Please do not attempt to install this currently downloaded copy.

I have donwloaded the iso from my school so the iso should not bee corrupt.
Do you have any idea of how I can fix this ?

---

### Post by parktownprawn on 2007-10-25
Did you edit the installer?

try following these instructions:

[http://ubuntuforums.org/showthread.php?t=283473](http://ubuntuforums.org/showthread.php?t=283473)

---

### Post by Nicolas.Perrault on 2010-02-14
I'm having the same problem with a legal CD-copy. Any help?

---

### Post by Orion8 on 2010-02-15
Hi --

Are you having the Java problem described by durus in 2007?  That is one I have not had, probably because I always install the restricted-extras package and have no trouble with Java after that. 

However, I have had some trouble with Maple, today in fact.  I had a tough time installing my legal copy of Maple 11.  I installed Ubuntu 9.10 64 bit and when I put in the Maple install CD nothing would happen -- no image on the desktop and /media/cdrom was empty.  

I found [this link]("http://www.maplesoft.com/support/faqs/detail.aspx?sid=32620&cid=356") and tried the mount trick.  That did it -- the disk mounted and I could install as su from /media/cdrom.

Again, I don't know what to say about the error described above, but if your disk is not loading try:

```
sudo mount -t iso9660 /dev/cdrom /media/cdrom
cd /media/cdrom
sudo ./installMapleLinux64

```
(or 32 bit).

This worked for me.  

Afterwards, Maple will load to a blank screen which is kind of annoying.  You need to edit the xmaple script -- include the line ```
export AWT_TOOLKIT=MToolkit
```  I also take the time to make symbolic links to these scripts so I can run the CLI version of maple easily, and I alway turn the font aliasing on so the x interface looks decent.

Anyway, can you clarify your problem? I will try to help if I can.

---

