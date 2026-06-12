---
title: "Remastering of Ubuntu 9.04"
date: 2009-06-23
forum: General Help
---

### Post by stenrul on 2009-06-23
Hello, I am looking for a way to remaster Ubuntu 9.04 with cloning the version being used back to disc. e.g. installed Ubuntu 9.04 on hard drive cloned to a Ubuntu remastered live cd. I would like to find a way that is quick and basic gui. Really making a full system backup to a live cd/dvd. I have tried to use Remastersys with Ubuntu 9.04 but it is unable to install.
Could someone please tell me another program like this or how to fix this issue?  
Here is the error when i use Synaptic. 

Remastersys 2.0.12-1 from [www.geekconnection.org](www.geekconnection.org)
Unable to install this package
------------------------
remastersys:
Depends: dialog but is not installable
Depends:discover1 but it is not installable or discover but it is installable
Depends:  xresprobe but it is not installable

Here is the error when i use console apt-get install ...

root@ubuntu:/home/ubuntu# apt-get install remastersys
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
root@ubuntu:/home/ubuntu# apt-get install remastersys
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 remastersys: Depends: dialog but it is not installable
              Depends: discover1 but it is not installable or
                       discover but it is not installable
              Depends: xresprobe but it is not installable
E: Broken packages


Thank you.

---

### Post by stenrul on 2009-06-24
Does any one know?
Please, I would really like to know how to fix the error with Remastersys or some other tool that will do the job. I have look for other tool and not be able to find one that does the job but for Remastersys. PLEASE Help[-o<

Thank you again.

---

### Post by ZLance on 2009-06-24
Did you add the repository for it in your sources list:

deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/

---

### Post by ZLance on 2009-06-24
I just added the repository to sources list, then just went "~$ sudo apt-get install remastersys" and it works fine.

---

### Post by stenrul on 2009-06-24
OK, I just tried again. Here is what i did step by step.
-New Start up of Ubuntu
-click on System, Administration, Software Sources
-click on Third-Party Software, add
-Enter "deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/" in APT Line
-Click on Close

-click on System, Administration, Synaptic Package Manager
-Click on Reload
-Enter in quick search "remastersys"
-Right-click on remastersys package
-Click install 
-"additional required changes" squashfs-tools Click on Mark
-ERORR "could not mark all packages for installation or upgrade" ETC SOME ERROR AS LAST TIME

I all so tried by console, it failed also. This is on ubuntu 9.04. If you are using that version also. Could you please posts the steps you used in console or GUI? Thank you 


> **ZLance said:**
> I just added the repository to sources list, then just went "~$ sudo apt-get install remastersys" and it works fine.

---

### Post by stenrul on 2009-06-24
I have tried on other pc, etc and still no luck. Could someone else try and see if it works for them and if it does work please tell me how you did it. This is on Ubuntu 9.04. Could some one please tell me how to fix this?

Here is the info file about remastersys
---------------------------------------
Package: remastersys
Version: 2.0.11-1
Architecture: all
Maintainer: Tony Brijeski <tb6517@yahoo.com>
Installed-Size: 344
Depends: bash, casper, coreutils, dialog, discover1 | discover, eject, findutils, grub, laptop-detect, libdebian-installer4, mkisofs | genisoimage, mount, os-prober, passwd, rsync, sed, squashfs-tools, syslinux, ubiquity, user-setup, util-linux, xresprobe, xterm
Suggests: kdebase-bin, metacity, zenity
Filename: remastersys/remastersys_2.0.11-1_all.deb
Size: 154340
MD5sum: 87247bfd9544dfe2c1b10457d27982f0
Section: system
Priority: optional
Description: Ubuntu and variant system remaster
 This script creates a livecd of the installed system.
 You can either make a distributable livecd or backup of your system.
 For more information, please visit [http://www.remastersys.klikit-linux.com](http://www.remastersys.klikit-linux.com)
---------------------------------------

---

### Post by stenrul on 2009-06-24
OK, I have found the answer.
If you need Remastersys 2.0.11-1 to work on ubuntu 9.04, please install the following DEB.
[http://ubuntu.secs.oakland.edu/pool/universe/d/dialog/dialog_1.1-20071028-3_i386.deb]("http://ubuntu.secs.oakland.edu/pool/universe/d/dialog/dialog_1.1-20071028-3_i386.deb")
[http://ubuntu.mirrors.tds.net/ubuntu/pool/main/d/discover1/discover1_1.7.22ubuntu1_i386.deb]("http://ubuntu.mirrors.tds.net/ubuntu/pool/main/d/discover1/discover1_1.7.22ubuntu1_i386.deb")
[http://ubuntu.mirrors.tds.net/ubuntu/pool/main/x/xresprobe/xresprobe_0.4.24ubuntu8_i386.deb]("http://ubuntu.mirrors.tds.net/ubuntu/pool/main/x/xresprobe/xresprobe_0.4.24ubuntu8_i386.deb")
[http://ubuntu.secs.oakland.edu/pool/main/d/discover1/libdiscover1_1.7.22ubuntu1_i386.deb]("http://ubuntu.secs.oakland.edu/pool/main/d/discover1/libdiscover1_1.7.22ubuntu1_i386.deb")
[http://www.remastersys.klikit-linux.com/repository/remastersys/remastersys_2.0.11-1_all.deb]("http://www.remastersys.klikit-linux.com/repository/remastersys/remastersys_2.0.11-1_all.deb")

And that all you need to do to start remastering ubuntu 9.04. :)

---

