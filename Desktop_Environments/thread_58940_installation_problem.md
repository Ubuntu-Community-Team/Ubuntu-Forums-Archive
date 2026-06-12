---
title: "installation problem"
date: 2005-08-22
forum: Desktop Environments
---

### Post by cymoril on 2005-08-22
hello everyone, linux newbie here.

i tried to install kubuntu today after burning the .iso i downloaded from [http://releases.ubuntu.com/kubuntu/hoary/kubuntu-5.04-install-i386.iso](http://releases.ubuntu.com/kubuntu/hoary/kubuntu-5.04-install-i386.iso) onto CD.

i have however faced problems with the installation at the "loading additional components" stage.

the installation program said there was a problem reading data from my cd and that i should check the integrity of the CD.  i tried doing this using the menu option and i was given the path of a file which had failed the md5 checksum process.

i thought this might have been caused by errors in the burning procedure but after repeating it twice i found that all the CDs i burnt received this same error upon installation. 

the md5 i generated for the .iso i downloaded matched the one for kubuntu-5.04-install-i386.iso given here: [http://releases.ubuntu.com/kubuntu/hoary/MD5SUMS](http://releases.ubuntu.com/kubuntu/hoary/MD5SUMS)

using wxChecksums to check md5sum.txt on each of the CDs i burnt i found these 3 errors on all of them:

filename: default
path: install\netboot\pxelinux.cfg\  
status: file not found

filename: mozilla-firefox-locale-en-gb_1.0.1lang20050309ubuntu1-0ubuntu3_all.deb  
path: pool\main\m\mozilla-firefox-locale-all\   
status: file not found

filename: pxelinux.0 
path: install\netboot\
status: checksums differ

i mounted the .iso using alcohol too instead of burning it onto CD and when i checked md5sum.txt the errors above were also present.

well i don't even know if it's these errors that are causing my installation to fail.
when i ran the CD integrity test from within the kubuntu installation the path and name of the file was unlike any of the 3 mentioned above.

is there any way i can solve this?

thank you.

---

### Post by heimo on 2005-08-22
You could try to burn it on slower speed, 4x perhaps.

```
 is there any way i can solve this?
``` 

If bandwidth is not a problem, you can always install from Ubuntu install CD and add kubuntu-desktop package later (KDE and K-programs).

---

### Post by cymoril on 2005-08-22
thank you for your reply, heimo.
i did burn one of the Cds at a slow speed.
it had the same errors.

---

### Post by heimo on 2005-08-22
I believe I've seen exactly same error somewhere on these forums, some time ago. I think the solution was to use Ubuntu install CD or some other version of install CD anyway.

---

