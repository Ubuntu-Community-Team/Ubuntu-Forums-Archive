---
title: "error while installing java"
date: 2005-03-02
forum: Desktop Environments
---

### Post by joplass on 2005-03-02
I am very new to Ubuntu and any distro Debian based.  I got this error while installing java.  Can someone please tell me what to do from here?

thanks

Do you agree to the above license terms? [yes or no]
yes
Unpacking...
Checksumming...
0
0
Extracting...
UnZipSFX 5.42 of 14 January 2001, by Info-ZIP (Zip-Bugs@lists.wku.edu).
  inflating: jre-1_5_0_01-linux-i586.rpm
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - No such file or directory (2)
error: cannot open Packages database in /var/lib/rpm

Done.
root@ubuntu:/home/job #

---

### Post by lordofkhemenu on 2005-03-02
[QUOTE=joplass]I am very new to Ubuntu and any distro Debian based. I got this error while installing java. Can someone please tell me what to do from here?

thanks

Do you agree to the above license terms? [yes or no]
yes
Unpacking...
Checksumming...
0
0
Extracting...
UnZipSFX 5.42 of 14 January 2001, by Info-ZIP (Zip-Bugs@lists.wku.edu).
  inflating: jre-1_5_0_01-linux-i586.rpm
rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - No such file or directory (2)
error: cannot open Packages database in /var/lib/rpm

Done.
root@ubuntu:/home/job #[/QUOTE]
You need to down the other self extracting archive (not the one that contains the RPM).

---

### Post by ubuntu UsER on 2005-03-02
[QUOTE=joplass]jre-1_5_0_01-linux-i586.rpm[/QUOTE]

Ubuntu as Debian they both use .deb packages not .rpm packages. You can use java with .bin at the end as well.

---

### Post by joplass on 2005-03-03
Ok guys,
Thank you!  I am clearly in the Ubuntu school now.  I am afraid I will have a lot of questions   :confused:  :confused:  :confused:

---

### Post by bored2k on 2005-03-03
[QUOTE=joplass]Ok guys,
Thank you!  I am clearly in the Ubuntu school now.  I am afraid I will have a lot of questions   :confused:  :confused:  :confused:[/QUOTE]

In synaptic , add this repositories to ur list



> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse


deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) warty java


deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) warty-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) warty-extras main universe multiverse restricted

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main 


after this , in Synaptic (Computer>SyS Config> Synaptic) search for sun-j2re1.5debian right click >install . tHat's it , no more compiling.


U would then probably want m$ video playback, so install w32codecs , xine-ui and mozilla-mplayer [video streaming.

---

