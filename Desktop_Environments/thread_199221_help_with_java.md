---
title: "help with java"
date: 2006-06-18
forum: Desktop Environments
---

### Post by itechx on 2006-06-18
ish@ish-desktop:~$ sudo -i
Password:

Sorry, try again.
Password:
root@ish-desktop:~#
root@ish-desktop:~#
root@ish-desktop:~#
root@ish-desktop:~#
root@ish-desktop:~#
root@ish-desktop:~#
root@ish-desktop:~#
root@ish-desktop:~#
root@ish-desktop:~#
root@ish-desktop:~# dpkg --configure -a
Setting up libopenexr2c2a (1.2.2-4ubuntu2) ...

Setting up libqt3-mt (3.3.6-1ubuntu6) ...

Setting up menu-xdg (0.2.2) ...

Setting up libavahi-qt3-1 (0.6.10-0ubuntu3) ...

Setting up libpcre3 (6.4-1.1ubuntu4) ...

Setting up kdelibs-data (3.5.2-0ubuntu1 ...

Setting up libartsc0 (1.5.2-0ubuntu1) ...

Setting up sun-java5-doc (1.5.0-06-1) ...
This package is an installer package, it does not actually contain the
J2SDK documentation. You will need to go download one of the
archives:

jdk-1_5_0-doc.zip jdk-1_5_0-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

[http://java.sun.com/j2se/1.5.0/download.html](http://java.sun.com/j2se/1.5.0/download.html)

now and download. The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]
I copied the file to temporry but thta didn't work
itechx is online now   	Edit/Delete Message

---

### Post by GoogleNinja on 2006-06-18
well, if you just want to get rid of it, do "sudo dpkg -r sun-java5-doc" or if that doesnt work, you could try "sudo dpkg --force-all -r sun-java5-doc".

to actually configure the package, click on the link it gave, then download jdk-1_5_0-doc.zip to /tmp. after that, do "sudo chown root:root /tmp/jdk-1_5_0-doc.zip". now you should be able to do "sudo dpkg --configure -a" without any problems.

---

