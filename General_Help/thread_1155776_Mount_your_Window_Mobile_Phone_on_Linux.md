---
title: "Mount your Window Mobile Phone on Linux"
date: 2009-05-11
forum: General Help
---

### Post by DYFeng on 2009-05-11
[B][B]via [http://www.dyfeng.co.cc/2009/05/11/mount-your-window-mobile-phone-on-linux/](http://www.dyfeng.co.cc/2009/05/11/mount-your-window-mobile-phone-on-linux/)


The First and First[/B][/B]

 I’m **NOT** talking about how to syncing your **contacts**,**calendar **or **tasks** on **Linux**.My aim is to browse the files of my **Window Mobile** Phone on **Linux**.Just browse the files!!
 All I have done is on **Kubuntu 8.04** and my **Window Mobile 5**.
 &#20013;&#25991;&#30340;&#35831;&#30475;:[&#22312;Linux&#19978;&#25346;&#36733;Window Mobile&#35774;&#22791;]("http://www.dyfeng.co.cc/2009/05/2009/05/11/%e5%9c%a8linux%e4%b8%8a%e6%8c%82%e8%bd%bdwindow-mobile%e8%ae%be%e5%a4%87/")
 **[B]Preparation**[/B]

 The first,you need** synCE**.[INDENT]**SynCE** project is to provide a means of communication with a **Windows Mobile** device from a computer running **Linux.**
[/INDENT]More information about **SynCE**,please visit [www.synce.org]("http://www.synce.org/")
 But do not forget,it’s just provide a **communication**.We need another tool to mount your Window Mobile Phone on Linux — **SynCE FS **.
  [INDENT]**Syncefs** is an application allowing to mount pocketPC like          a remote filesystem.
[/INDENT]More information please visit [http://www.lvivier.info/SynceFS](http://www.lvivier.info/SynceFS)
 **[B]Installation**[/B]

 **synCE Installation**
 **Note:**[INDENT]If you’re not a ubuntu user,please visit [http://www.synce.org/moin/SynceInstallation](http://www.synce.org/moin/SynceInstallation) .[URL="http://www.synce.org/moin/SynceInstallation"]
[/URL]
[/INDENT][INDENT]If your phone is legacy devices (Windows Mobile 2003 or earlier),please visit [here]("http://www.synce.org/moin/LegacyDevices/Ubuntu") .
[/INDENT]Add the ppa sources into your apt system.
 ```
sudo kate /etc/apt/sources.list
``` Add the following lines into sources.list
 ```
deb http://ppa.launchpad.net/synce/ubuntu hardy main
deb-src http://ppa.launchpad.net/synce/ubuntu hardy main
``` (Note, in the above please replace **hardy** by** intrepid ** if you are running ubuntu intrepid or by **jaunty** if you are running ubuntu jaunty)
 Install the public key
 ```
sudo apt-key adv –recv-keys –keyserver subkeys.pgp.net 7D2C7A23BF810CD5
``` Install the main SynCE package
 ```
sudo apt-get install synce-hal librra-tools librapi2-tools
```Now you can connect your window mobile device and computer with USB.
 Let’s have a test whether the connection is working.Run the following command:
 ```
synce-pls
``` In case you see a list of files, congratulations!!The connection between your window mobile device and computer is working.If not,please check the steps above,or maybe you need to reboot your computer.
 **synCE FS Installation**
 Download synCE FS from[ http://www.lvivier.info/SynceFS]("http://www.lvivier.info/SynceFS") (The bottom of page)
 The ubuntu user can download the .deb,but I recommend that compile it from sources.
 I copy many things from  [http://www.lvivier.info/SynceFS](http://www.lvivier.info/SynceFS)  [IMG]http://www.dyfeng.co.cc/wordpress/wp-includes/images/smilies/2E0923A7EA5F4B9F3B5B923C74E1074E.gif[/IMG] 
 Create a directory to mount your filesystem
 ```
sudo mkdir /mnt/synce
``` Edit the fstab file
 ```
sudo kate /etc/fstab
``` You should add following lines in /etc/fstab to allow non-root user (owner of dccm) to mount the pocketPC filesystem on /mnt/synce:
 ```
none           /mnt/synce      cefs    rw,user,noauto,codadev=/dev/cfs0       0 0
``` Ask kernel to load CODA
 ```
sudo modprobe coda
``` then, you (as non-root user, owner of dccm) can mount the pocketPC filesystem:
 ```
feng@dyfeng:~$ mount /mnt/synce/
SynCE FS using "/dev/cfs0" (CODA v3)
``` and you can use all files of the pocketPC as they were stored         in a local filesystem:
 ```
feng@dyfeng:~$ find /mnt/synce/
/mnt/synce/
/mnt/synce/Storage Card
/mnt/synce/Windows
…..
``` LOOL,just enjoy it!!! [IMG]http://www.dyfeng.co.cc/wordpress/wp-includes/images/smilies/23533FEF8F33FB5373120EBE86E3A589.gif[/IMG]

---

### Post by DYFeng on 2009-05-11
[B][B]via [http://www.dyfeng.co.cc/2009/05/11/mount-your-window-mobile-phone-on-linux/](http://www.dyfeng.co.cc/2009/05/11/mount-your-window-mobile-phone-on-linux/)

[/B][/B]**[B]The First and First**[/B]

 I’m **NOT** talking about how to syncing your **contacts**,**calendar **or **tasks** on **Linux**.My aim is to browse the files of my **Window Mobile** Phone on **Linux**.Just browse the files!!
 All I have done is on **Kubuntu 8.04** and my **Window Mobile 5**.
 &#20013;&#25991;&#30340;&#35831;&#30475;:[&#22312;Linux&#19978;&#25346;&#36733;Window Mobile&#35774;&#22791;]("http://www.dyfeng.co.cc/2009/05/2009/05/11/%e5%9c%a8linux%e4%b8%8a%e6%8c%82%e8%bd%bdwindow-mobile%e8%ae%be%e5%a4%87/")
 **[B]Preparation**[/B]

 The first,you need** synCE**.[INDENT]**SynCE** project is to provide a means of communication with a **Windows Mobile** device from a computer running **Linux.**
[/INDENT]More information about **SynCE**,please visit [www.synce.org]("http://www.synce.org/")
 But do not forget,it’s just provide a **communication**.We need another tool to mount your Window Mobile Phone on Linux — **SynCE FS **.
  [INDENT]**Syncefs** is an application allowing to mount pocketPC like          a remote filesystem.
[/INDENT]More information please visit [http://www.lvivier.info/SynceFS](http://www.lvivier.info/SynceFS)
 **[B]Installation**[/B]

 **synCE Installation**
 **Note:**[INDENT]If you’re not a ubuntu user,please visit [http://www.synce.org/moin/SynceInstallation](http://www.synce.org/moin/SynceInstallation) .[URL="http://www.synce.org/moin/SynceInstallation"]
[/URL]
[/INDENT][INDENT]If your phone is legacy devices (Windows Mobile 2003 or earlier),please visit [here]("http://www.synce.org/moin/LegacyDevices/Ubuntu") .
[/INDENT]Add the ppa sources into your apt system.
 ```
sudo kate /etc/apt/sources.list
```
 Add the following lines into sources.list
 ```
deb http://ppa.launchpad.net/synce/ubuntu hardy main
deb-src http://ppa.launchpad.net/synce/ubuntu hardy main
```
 (Note, in the above please replace **hardy** by** intrepid ** if you are running ubuntu intrepid or by **jaunty** if you are running ubuntu jaunty)
 Install the public key
 ```
sudo apt-key adv –recv-keys –keyserver subkeys.pgp.net 7D2C7A23BF810CD5
```
 Install the main SynCE package
 ```
sudo apt-get install synce-hal librra-tools librapi2-tools
```
  
Now you can connect your window mobile device and computer with USB.
 Let’s have a test whether the connection is working.Run the following command:
 ```
synce-pls
```
 In case you see a list of files, congratulations!!The connection between your window mobile device and computer is working.If not,please check the steps above,or maybe you need to reboot your computer.
 **synCE FS Installation**
 Download synCE FS from[ http://www.lvivier.info/SynceFS]("http://www.lvivier.info/SynceFS") (The bottom of page)
 The ubuntu user can download the .deb,but I recommend that compile it from sources.
 I copy many things from  [http://www.lvivier.info/SynceFS](http://www.lvivier.info/SynceFS)  [IMG]http://www.dyfeng.co.cc/wordpress/wp-includes/images/smilies/2E0923A7EA5F4B9F3B5B923C74E1074E.gif[/IMG] 
 Create a directory to mount your filesystem
 ```
sudo mkdir /mnt/synce
```
 Edit the fstab file
 ```
sudo kate /etc/fstab
```
 You should add following lines in /etc/fstab to allow non-root user (owner of dccm) to mount the pocketPC filesystem on /mnt/synce:
 ```
none           /mnt/synce      cefs    rw,user,noauto,codadev=/dev/cfs0       0 0
```
 Ask kernel to load CODA
 ```
sudo modprobe coda
```
 then, you (as non-root user, owner of dccm) can mount the pocketPC filesystem:
 ```
feng@dyfeng:~$ mount /mnt/synce/
SynCE FS using "/dev/cfs0" (CODA v3)
```
 and you can use all files of the pocketPC as they were stored         in a local filesystem:
 ```
feng@dyfeng:~$ find /mnt/synce/
/mnt/synce/
/mnt/synce/Storage Card
/mnt/synce/Windows
…..
```
 LOOL,just enjoy it!!! [IMG]http://www.dyfeng.co.cc/wordpress/wp-includes/images/smilies/23533FEF8F33FB5373120EBE86E3A589.gif[/IMG]

---

