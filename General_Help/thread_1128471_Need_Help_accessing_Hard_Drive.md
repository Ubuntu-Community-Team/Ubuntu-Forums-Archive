---
title: "Need Help accessing Hard Drive?"
date: 2009-04-17
forum: General Help
---

### Post by rogeroo on 2009-04-17
I was recently reffered to try and use the Ubuntu live disc to access a hard drive that i am having problems seeing in Windows.I ran the live disc and tried to mount the drive but i get this error message and can't force the drive.Here is the message i am getting :
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

Can anyone help me or is the drive dead?

---

### Post by HermanAB on 2009-04-17
Howdy,

NTFS repair work needs to be done with Windows.  So you need to make a BartPE bootable Windows disk:
[http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

---

### Post by rogeroo on 2009-04-17
Thanks will give it a try.

---

