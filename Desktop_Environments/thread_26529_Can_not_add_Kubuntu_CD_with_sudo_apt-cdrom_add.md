---
title: "Can not add Kubuntu CD with sudo apt-cdrom add"
date: 2005-04-13
forum: Desktop Environments
---

### Post by ChaKy on 2005-04-13
Please, help me with this. I have Ubuntu 5.04 installed with Gnome, and I want now to install KDE from Kubuntu CD. But I can not add CD to sources.list:

chaky@ubuntu:~ $ sudo apt-cdrom add
Password:
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter
Mounting CD-ROM...
Identifying.. [96e0570eb362af6d901aa7492ab3a5bb-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes and 1 signatures
Found label 'Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)'
This disc is called:
'Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)'
Copying package lists...gpgv: Signature made &#268;et 07 Tra 2005 08:18:12 CEST using DSA key ID FBB75451
gpgv: Can't check signature: public key not found
E: Sub-process gpgv returned an error code (2)
W: Signature verification failed for: /cdrom/dists/hoary/Release.gpg


Where I can find Public PGP key?

Thanks.

---

### Post by ChaKy on 2005-04-13
OK, I have managed to import PGP key from PGP server and to verify Kubuntu CD. After that, I have installed KDE Desktop, with apt-get install kubuntu-desktop.

But now I have another problem with KDE. When I log into my KDE, and after KDE desktop is up, I got this messages:

Error - KDE Panel: Could not start process Unable to create io-slave: klauncher said: Unknown protocol 'system'

Sorry - KDE Panel: Could not find mime type application/octet-stream
klauncher said: Unknown protocol 'trash'
klauncher said: Unknown protocol 'file'

Error - KDE Panel: No mime types installed

And also I do not have any applications icons in K menu.


But this is also strange because, on the same computer, on my sister's account, KDE is working fine, great, without any error messages, and I have all application icons in K  menu on my sister's account. But on my account, I got those error messages.

Help me here. Thanks.

---

### Post by compoundctc on 2006-02-27
how did you import the pgp-key - I am trying to add cd-rom and get the same error as you.  Any help would be greatly appreciated.  My system is hosed after dapper upgrade and networking is not working - trying to add cd so I can fix the problem

---

