---
title: "How do i install a app from my desktop in ubuntu?"
date: 2006-02-21
forum: Desktop Environments
---

### Post by aten on 2006-02-21
i downloaded the free VMware Server its extention is (.tar.gz) how do i install this? :confused: 
:confused: 
:confused: 
:confused: 
:confused: 
:confused: 
:confused:




-Aten\\:D/

---

### Post by suRoot on 2006-02-21
You first need to install GCC 3.4... you also need to install a few kernel-related packages.  I think build-essentials will do it, but there may well be one other package... I don't remember.

Main Menu -> System -> Administration -> Synaptic Package Manager

Search for gcc & build-essential, then check the box beside 'gcc-3.4' & 'build-essential'... click apply to install it & whatever else it wants to install...

Open a console & type

```
export CC=/usr/bin/gcc-3.4
```

Now you can install vmware... I'm sorry, I don't have the vmware archive in front of me, so I'm making up names - replace them with the appropriate ones for the archive, the directory that's created & the installer script in that directory...

```
tar -zxvf whateverthenameofthearchiveis.tar.gz
```

```
cd vmware-directory-name
```

```
sudo ./vmwareinstallername.pl
```

Answer all the questions & you should be set.

---

### Post by aten on 2006-02-21
I was looking for GCC 3.4 on google and dont know which one, could you plaese help a little more 



sorry

Thanks ;)

---

### Post by suRoot on 2006-02-21
Use synaptic

Click the main menu (start button) on your desktop, go to System -> Administration -> Synaptic Package Manager

When synaptic opens, click the "Search" button on the toolbar & enter gcc in the box.  Scroll down the results until you find gcc-3.4 & then click the box beside it.  Click the "Apply" button on the toolbar.

---

### Post by aten on 2006-02-21
[B]twesh@ubuntu:~$ sudo ./vmwareinstallername.pl
Password:
sudo: ./vmwareinstallername.pl: command not found
twesh@ubuntu:~$
[/B]


That is what i get what happend did i do something wrong ? :confused: :-k

---

### Post by kaamos on 2006-02-21
The name there is just a placeholder. You should navigate to the extracted folder with "cd **name-of-folder**". You can use the command "ls" to list folders and directories. When you are in the right folder use "ls" again to find the name of the installer file (will probably have install in the name) and then type
```
sudo ./**the-name-of-the-install-file**
```

---

### Post by aten on 2006-02-21
im not sure if this help


[B]twesh@ubuntu:~$ sudo: /home/twesh/Desktop/vmware-server-distrib/bin/vmware-unins tall.pl
bash: sudo:: command not found
twesh@ubuntu:~$ /home/twesh/Desktop/vmware-server-distrib/bin/v
bash: /home/twesh/Desktop/vmware-server-distrib/bin/v: No such file or directory
twesh@ubuntu:~$ /home/twesh/Desktop/vmware-server-distrib/bin/
bash: /home/twesh/Desktop/vmware-server-distrib/bin/: is a directory
twesh@ubuntu:~$ ls
automatix_5.4-3_i386.deb    firefox                 kubuntu-packages-jriddell-key.gpg  tall
automatix_5.4-3_i386.deb.1  firefox-1.5.0.1.tar.gz  macmatrix_original.jpg             vmware-server-distrib
automatix.log               Firefox_wallpaper.png   OperaDownloads                     wget-log
Desktop                     Incomplete              Shared
twesh@ubuntu:~$ Desktop ls
bash: Desktop: command not found
twesh@ubuntu:~$ ls desktop
ls: desktop: No such file or directory
twesh@ubuntu:~$ desktop
[/B]


but that wat came up

---

### Post by aten on 2006-02-21
sorry double post

---

### Post by kaamos on 2006-02-21
[QUOTE=aten]twesh@ubuntu:~$ sudo: /home/twesh/Desktop/vmware-server-distrib/bin/vmware-uninstall.pl[/QUOTE]
Should be sudo then a space, dot, slash, filename. "sudo ./blaablaa". That btw looks like an **un**install script to me, are you shure you are trying to run the right file?

Also, remember to follow suRoot instrucions abowe with the gcc version.

---

### Post by carlosqueso on 2006-02-21
Okay....enter these two commands into a terminal ```
cd Desktop/vmware-server-distrib/bin
ls
``` remember to capitalize Desktop--linux is CaSe SeNsItIve!   Then it'll give you a bunch of files, one of which should say something like install so, assuming it's install you'd type ```
sudo ./install
```  not that there is no colon after sudo.  Hope this helps.

---

### Post by aten on 2006-02-21
[QUOTE=carlosqueso]Okay....enter these two commands into a terminal ```
cd Desktop/vmware-server-distrib/bin
ls
``` remember to capitalize Desktop--linux is CaSe SeNsItIve!   Then it'll give you a bunch of files, one of which should say something like install so, assuming it's install you'd type ```
sudo ./install
```  not that there is no colon after sudo.  Hope this helps.[/QUOTE]


> twesh@ubuntu:~/Desktop/vmware-server-distrib/bin$ ls
vmnet-bridge   vmnet-sniffer       vmware-cmd        vmware-ping
vmnet-dhcpd    vm-support          vmware-config.pl  vmware-uninstall.pl
vmnet-natd     vmware              vmware-loop       vmware-vdiskmanager
vmnet-netifup  vmware-authtrusted  vmware-mount.pl




dont know which one

---

### Post by kaamos on 2006-02-21
What is the output of
```
ls ~/Desktop/vmware-server-distrib/
```
?

---

### Post by aten on 2006-02-21
[B]
twesh@ubuntu:~$ ls ~/Desktop/vmware-server-distrib/
bin  doc  etc  FILES  installer  lib  man  sbin  vmware-install.pl
twesh@ubuntu:~$ sudo ./installer
sudo: ./installer: command not found
twesh@ubuntu:~$ ls ~/Desktop/vmware-server-distrib/
bin  doc  etc  FILES  installer  lib  man  sbin  vmware-install.pl
twesh@ubuntu:~$ cd ~/Desktop/vmware-server-distrib/
twesh@ubuntu:~/Desktop/vmware-server-distrib$ sudo ./installer
sudo: ./installer: command not found
twesh@ubuntu:~/Desktop/vmware-server-distrib$ sudo ./installerinstaller
sudo: ./installerinstaller: command not found
twesh@ubuntu:~/Desktop/vmware-server-distrib$

[/B]

---

### Post by kaamos on 2006-02-21
~/Desktop/vmware-server-distrib/vmware-install.pl

Thats the file you are looking for.

---

### Post by aten on 2006-02-21
so what do i do with it?

---

### Post by aten on 2006-02-21
im sorry that im such a "n00b" but what do i do here ??

[B]twesh@ubuntu:~/Desktop/vmware-server-distrib$ sudo ./vmware-install.pl
Creating a new installer database using the tar3 format.

Installing the content of the package.

In which directory do you want to install the binary files?
[/usr/bin]
[/B]

---

### Post by kaamos on 2006-02-21
The installer asks you for a huge amount of questinons, hitting enter should be ok probably for all of them. And, before you think of it, no, installing programs is not normally this hard. :)

---

### Post by engla on 2006-02-21
The default values are specified in brackets [like this]... you should probably just hit enter to accept the defaults.

[And yes, normally applications are installed with the menu choice Applications > Add applications, or the more advanced System > Administration > Synaptic package manager. Both those methods are much easier, but doesn't provide all the possible software you can download. So some things like vmware will have to be done like this.

When you get hang of it though ./configure && make ; sudo checkinstall is easy and great too.. ]

---

### Post by aten on 2006-02-21
[B]Creating a new installer database using the tar3 format.

Installing the content of the package.

In which directory do you want to install the binary files?
[/usr/bin]

What is the directory that contains the init directories (rc0.d/ to rc6.d/)?
[/etc]

What is the directory that contains the init scripts?
[/etc/init.d]

In which directory do you want to install the daemon files?
[/usr/sbin]

In which directory do you want to install the library files?
[/usr/lib/vmware]

The path "/usr/lib/vmware" does not exist currently. This program is goi[/B]

i just hit enter for every thing ;)

---

### Post by carlosqueso on 2006-02-21
What was the rest of that last thing?  If it was okay with creating it, then cool...if not....you may need to add it yourself with ```
sudo mkdir /usr/lib/vmware
```

---

### Post by aten on 2006-02-21
UH OH :( !!!!

[B][I][U]The module bld-2.6.12-9-i386up-Ubuntu5.10 loads perfectly in the running kernel.

Setup is unable to find the "make" program on your machine.  Please make sure itis installed.  Do you want to specify the location of this program by hand?
[yes]
[/U][/I][/B]






help!!!!!

What happend???

SO Close!

---

### Post by aten on 2006-02-21
[QUOTE=carlosqueso]What was the rest of that last thing?  If it was okay with creating it, then cool...if not....you may need to add it yourself with ```
sudo mkdir /usr/lib/vmware
```[/QUOTE]
The path "/usr/lib/vmware" does not exist currently. This program is going to
create it, including needed parent directories. Is this what you want? [yes]

---

### Post by kaamos on 2006-02-21
[QUOTE=aten]UH OH :( !!!!

[B][I][U]The module bld-2.6.12-9-i386up-Ubuntu5.10 loads perfectly in the running kernel.

Setup is unable to find the "make" program on your machine.  Please make sure itis installed.  Do you want to specify the location of this program by hand?
[yes]
[/U][/I][/B]






help!!!!!

What happend???

SO Close![/QUOTE]
Run this command in a terminal
```
sudo apt-get install build-essential linux-headers-$(uname -r)
```

---

### Post by carlosqueso on 2006-02-21
> The path "/usr/lib/vmware" does not exist currently. This program is going to
create it, including needed parent directories. Is this what you want? [yes] yeah...just keep hitting enter....thought it died at that point.

EDIT: as for the other thing...I'm just too slow.......;)

---

### Post by aten on 2006-02-21
...
....
.....
......
.......
........
.........[B]
Setting up linux-headers-2.6.12-9-386 (2.6.12-9.23) ...
Setting up libstdc++6-4.0-dev (4.0.1-4ubuntu9) ...
Setting up g++-4.0 (4.0.1-4ubuntu9) ...
Setting up g++ (4.0.1-3) ...

Setting up build-essential (11.1) ...
twesh@ubuntu:~$
[/B]


Now what do i do?

---

### Post by kaamos on 2006-02-21
Just in case do this as well:
```
sudo apt-get install gcc-3.4
```

Then run the vmwares install script again. (Also remember the gcc export thing from the first page of the thread)

---

### Post by aten on 2006-02-21
[B][I][U]
Unable to find any instance of the super-server "inetd" or "xinetd".  It is
possible that you do not have one of these packages installed on this machine.
Please install "inetd" or "xinetd".

If you do have "inetd" or "xinetd" installed, make sure that /etc/inetd.conf or
/etc/xinetd.d exists.
The configuration will continue, but you should re-run /usr/bin/vmware-config.plafter you fix the super-server.[/U][/I][/B]



Now
 what?

---

### Post by aten on 2006-02-21
[B][I][U]Unable to find any instance of the super-server "inetd" or "xinetd".  It is
possible that you do not have one of these packages installed on this machine.
Please install "inetd" or "xinetd".

If you do have "inetd" or "xinetd" installed, make sure that /etc/inetd.conf or
/etc/xinetd.d exists.
The configuration will continue, but you should re-run /usr/bin/vmware-config.plafter you fix the super-server.
[/U][/I][/B]







:(

?

---

### Post by yootje on 2006-02-21
Well, do you have inetd or xinetd installed?

---

### Post by aten on 2006-02-22
[QUOTE=yootje]Well, do you have inetd or xinetd installed?[/QUOTE]


No i dont where do i get it?

---

### Post by kaamos on 2006-02-22
Just search synaptic for xinetd.

[https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto)

---

### Post by Dr. Cox on 2006-05-06
hi there, may i join in with another two problems? for me everything worked more or less fine and i even get vmware icon in my system tray. i'm even able to run it. however, i had two error messages during installation. thus, i am wondering if they'll cause me any trouble in the future. would you please have a quick look at them:

> inetd: Kein Prozess beendet
Unable to make the Internet super-server (inetd) re-read its configuration
file.  Please restart inetd by hand:
killall -v -HUP inetd


> The VMware VmPerl Scripting API was not installed.  Errors encountered during
compilation and installation of the module can be found here:
/tmp/vmware-config0

You will not be able to use the "vmware-cmd" program


any help is appreciated.

---

