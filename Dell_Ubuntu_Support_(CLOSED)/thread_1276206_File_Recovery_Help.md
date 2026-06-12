---
title: "File Recovery Help"
date: 2009-09-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by LowTechie on 2009-09-26
Hello, I am currently attempting to recover files from my stop error "blue screen of death" dell desktop. I was following this tutorial, [http://http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/), and have run into an issue.
 
After booting from my ubuntu cd i go to places>computer and double click my harddrive which is displayed as 40.0 GB Media
 
I first get a message which states the following:
 
**UNABLE TO MOUNT LOCATION**
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
 
Which is then followed immediately by
 
**Cannot Mount Volume**
unable to mount the volume
 
Details:
ntfs_attr_pread_i: ntfs_pread failed: Input/output error failed to read ntfs $bitmap:input/output error NTFS is either inconsistent, or there is a hardware fault, or it's a SoftRAID/FakeRAID hardware. In the first case run chdsk /f on Windows then reboot into windows twice. The usage of the /f parameter is very important! if the device is a SoftRAID/FakeRAID then first activate it and mount a different device under the /dev/mapper/ directory, (e.g./dev/mapper/nvidiao_eahaabcc1). Please see the 'dmraid' documentation for more details.
 
keep in mind i cannot boot into windows.
 
Any help is greatly appreciated i really need access to my files _asap_
 
p.s. layman's terms essential :)

---

### Post by aysiu on 2009-09-26
Maybe the disk is corrupt somehow.

That makes the process a bit more difficult, but you'll still get all your files back:
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles](http://www.psychocats.net/ubuntucat/recoverdeletedfiles)

---

