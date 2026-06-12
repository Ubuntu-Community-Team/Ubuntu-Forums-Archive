---
title: "VMware not finding ubuntu"
date: 2006-09-09
forum: Desktop Environments
---

### Post by markcaetano@gmail.com on 2006-09-09
hi folks

i love ubuntu but cant use it because im not allowed to wipe my hdd and use ubuntu
so i have downloaded vmware instead ive used it on other computers and it is a top-notch product

however what do i have to do to get it to find the file to install ubuntu ino my virtual hdd im using the pressed cd from shipit and have all the files dragged onto the same directory folder as the virtual hdd
my setup file looks like this:

#!/usr/bin/vmware
displayName = "Ubuntu Linux 6.04 Dapper Drake"
guestOS = "ubuntu"

memsize = "128"
scsi0:0.fileName = "20G.vmdk"
ide1:0.fileName = "initrd"

i need any help you people have,

using xp home fully patched with SP2

---

### Post by jISh on 2006-09-09
Err, you don't need to copy the files from the CD to your VMWare folder, if thats what you've done. 

Just put the CD in your drive and power on a blank virtual machine, it'll find the CD and boot into the install.

---

### Post by Jose Catre-Vandis on 2006-09-09
You don't say which type of vmware you are using. If its vmware player, then you need to eidt the .vmx file to point the CDROM at either an iso image or the drive, so that the vmx file looks for the "CD" on boot (try [www.vmx.com](www.vmx.com))

If its vmware server, then make sure the CDROM (setup by default) is either pointing to the physical drive or to the iso image

---

### Post by markcaetano@gmail.com on 2006-09-09
im using vmware player - the free one

---

### Post by markcaetano@gmail.com on 2006-09-09
also [www.vmx.com](www.vmx.com) and [www.easyvmx.com](www.easyvmx.com) dont work

---

### Post by markcaetano@gmail.com on 2006-09-09
helooo 
what is this? microsoft

---

### Post by CaveRat on 2006-09-09
> **markcaetano@gmail.com said:**
> also [www.vmx.com](www.vmx.com) and [www.easyvmx.com](www.easyvmx.com) dont work

easyvmx.com works fine. I clicked on the link in your last post and it took me there right away.

---

### Post by markcaetano@gmail.com on 2006-09-09
yes i know but after you have entered the options it gives a zip file link. when i click it a page comes up saying it dosent exist

---

### Post by Jose Catre-Vandis on 2006-09-13
> **markcaetano@gmail.com said:**
> im using vmware player - the free one


Suggest you go to [www.vmware.com](www.vmware.com) and download the vmware server. it is also free, you just need to register to get a key.

Uninstall vmware player completely (check forums for how to)before trying to install vmware server.

Then you can set up virtual machines using your install media no problems, without having to fiddle about with vmx file configurations

---

### Post by Jose Catre-Vandis on 2006-09-13
> **markcaetano@gmail.com said:**
> yes i know but after you have entered the options it gives a zip file link. when i click it a page comes up saying it dosent exist

Try right click and save as on the link, works fine for me here :-)

---

