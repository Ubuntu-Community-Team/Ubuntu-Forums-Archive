---
title: "Ubuntulooks Trouble"
date: 2008-12-24
forum: General Help
---

### Post by Wintereich on 2008-12-24
Hello, I just got my computer, and this is my first time using Ubuntu. I downloaded a theme and it said, "This theme will not look as intended because the required GTK+ theme engine 'ubuntulooks' is not installed." :confused:Now, I'm a DIY'er, so I tried to figure it out myself. I downloaded ubuntulooks, but I have no idea how to install it. I also need it for Elements (an add-on for Compiz), can anyone guide me through it?

---

### Post by josephellengar on 2008-12-24
> **Wintereich said:**
> Hello, I just got my computer, and this is my first time using Ubuntu. I downloaded a theme and it said, "This theme will not look as intended because the required GTK+ theme engine 'ubuntulooks' is not installed." :confused:Now, I'm a DIY'er, so I tried to figure it out myself. I downloaded ubuntulooks, but I have no idea how to install it. I also need it for Elements (an add-on for Compiz), can anyone guide me through it?

Go to system-administration-synaptic.  Type in ubuntulooks in the search box and then check it.  Hit install.  You don't need to download it- synaptic will do all of the work.  Once you do that, everything should work.  Hope this helped!

---

### Post by Wintereich on 2008-12-25
Thank you!!! I Have ubuntulooks installed now... but the elements plugin wouldn't work:

phil@phil-desktop:~/Documents$ bash ./elementsinstall.sh
[sudo] password for phil: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz-bcop is already the newest version.
compiz-dev is already the newest version.
libxcomposite-dev is already the newest version.
libpng12-dev is already the newest version.
libsm-dev is already the newest version.
libxrandr-dev is already the newest version.
libxdamage-dev is already the newest version.
libxinerama-dev is already the newest version.
libstartup-notification0-dev is already the newest version.
libgl1-mesa-dev is already the newest version.
libtool is already the newest version.
libxslt1-dev is already the newest version.
xsltproc is already the newest version.
The following packages were automatically installed and are no longer required:
  libflac++6
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mkdir: cannot create directory `/home/phil/.elements': File exists
--2008-12-25 20:15:01--  [http://www.elementsplugin.com/downloads/elements-most-recent.tar.gz](http://www.elementsplugin.com/downloads/elements-most-recent.tar.gz)
Resolving [www.elementsplugin.com](www.elementsplugin.com)... 69.89.31.238
Connecting to [www.elementsplugin.com|69.89.31.238|:80](www.elementsplugin.com|69.89.31.238|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 81464 (80K) [application/x-gzip]
Saving to: `/home/phil/.elements/elements.tar.gz'

100%[======================================>] 81,464      55.7K/s   in 1.4s    

2008-12-25 20:15:03 (55.7 KB/s) - `/home/phil/.elements/elements.tar.gz' saved [81464/81464]

images/
images/stars1.png
images/snow2.png
images/snow1.png
images/plugin-elements.png
images/fireflies2.svg
images/fireflies1.svg
images/bubbles2.png
images/bubbles1.png
images/autumn2.png
images/autumn1.png
elements.c
elements.xml.in
Makefile
plugin.info
install   : /home/phil/.compiz/plugins/libelements.soinstall: cannot create regular file `/home/phil/.compiz/plugins/libelements.so': Permission denied
make: *** [install] Error 1
Checking for Xgl: phil@phil-desktop:~/Documents$ not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Segmentation fault

This makes no sense to me, but maybe you know what it means?

---

### Post by josephellengar on 2008-12-26
> **Wintereich said:**
> 
install   : /home/phil/.compiz/plugins/libelements.soinstall: cannot create regular file `/home/phil/.compiz/plugins/libelements.so': Permission denied
make: *** [install] Error 1
Checking for Xgl: phil@phil-desktop:~/Documents$ not present. 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (8192): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Segmentation fault

This makes no sense to me, but maybe you know what it means?

Do you own your home folder?  Try the command:
chmod 777 ~
or, if you are on a shared system:
first make sure that you own it:
chown [your username] ~
then:
chmod 770 ~
If you don't understand the syntax for these commands, check here (I had to use it to remember what I was doing): 
[http://www.dba-oracle.com/linux/change_user_ownership.htm](http://www.dba-oracle.com/linux/change_user_ownership.htm)
If this doesn't work, your problem is beyond me.  Good luck!

---

### Post by drubin on 2008-12-28
> **idigchess said:**
> Do you own your home folder?  Try the command:
chmod 777 ~
or, if you are on a shared system:
first make sure that you own it:
chown [your username] ~
then:
chmod 770 ~
If you don't understand the syntax for these commands, check here (I had to use it to remember what I was doing): 
[http://www.dba-oracle.com/linux/change_user_ownership.htm](http://www.dba-oracle.com/linux/change_user_ownership.htm)
If this doesn't work, your problem is beyond me.  Good luck!

Your home folder should always be *00 where * is the level you would like per file. (Not all files need execute permissions.)

Giving others read/write/execute access to your home folder is very bad practice. Even if you are a single user on your system you would still *try* to follow best practises.

---

### Post by drubin on 2008-12-28
Please also take a read at this 
[http://www.linuxforums.org/security/file_permissions.html](http://www.linuxforums.org/security/file_permissions.html)
[http://www.tuxfiles.org/linuxhelp/filepermissions.html](http://www.tuxfiles.org/linuxhelp/filepermissions.html)
 to understand what the "odd" numbers mean :)

---

