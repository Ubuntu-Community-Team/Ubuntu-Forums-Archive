---
title: "cd fix?"
date: 2006-09-21
forum: Desktop Environments
---

### Post by DougieFresh4U on 2006-09-21
can I repair my edgy upgrade w/cd that I burned? Having problems w/openoffice core.

---

### Post by Tomosaur on 2006-09-21
Surely just reinstalling openOffice would fix the problem?

---

### Post by DougieFresh4U on 2006-09-21
dougie@DougiesToyBox:~$ sudo apt-get install -f
Password:
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  openoffice.org-core
The following NEW packages will be installed:
  openoffice.org-core
0 upgraded, 1 newly installed, 0 to remove and 48 not upgraded.
13 not fully installed or removed.
Need to get 0B/29.5MB of archives.
After unpacking 83.2MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 91981 files and directories currently installed.)
Unpacking openoffice.org-core (from .../openoffice.org-core_2.0.3-4ubuntu2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/openoffice.org-core_2.0.3-4ubuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/openoffice/program/ooqstart', which is also in package openoffice.org-gtk
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-core_2.0.3-4ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
dougie@DougiesToyBox:~                    dougie@DougiesToyBox:~$ sudo /usr/lib/openoffice/program/ooqstart
Password:

** ERROR **: Missing default argument in OOO_EXTRA_ARG
aborting...
Aborted (core dumped)
dougie@DougiesToyBox:~$ sudo /var/cache/apt/archives/openoffice.org-core_2.0.3-4ubuntu2_i386.deb
sudo: /var/cache/apt/archives/openoffice.org-core_2.0.3-4ubuntu2_i386.deb: command not found
dougie@DougiesToyBox:~$ sudo dpkg -i --force openoffice.org-core_2.0.3-4ubuntu2_i386.de
dpkg: unknown force/refuse option `openoffice.org-core_2.0.3-4ubuntu2_i386.de'

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
dougie@DougiesToyBox:~$ sudo synaptic
dougie@DougiesToyBox:~$

---

### Post by Tomosaur on 2006-09-21
Try:

sudo aptitude purge openoffice.org-core

then reinstall

---

### Post by croak77 on 2006-09-21
If that doesn't work, try removing openoffice.org-gtk then install openoffice.org-core and openoffice.org-gtk.

---

### Post by DougieFresh4U on 2006-09-21
some thing failed?                          dougie@DougiesToyBox:~$ sudo aptitude purge openoffice.org-core
Password:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  openoffice.org openoffice.org-base openoffice.org-calc 
  openoffice.org-common openoffice.org-draw openoffice.org-evolution 
  openoffice.org-gtk openoffice.org-impress openoffice.org-math 
  openoffice.org-writer python-uno 
The following packages have been kept back:
  amarok amarok-xine apt apt-utils console-setup evolution 
  evolution-plugins gdm hpijs initscripts libgnomevfs2-0 libgnomevfs2-bin 
  libgnomevfs2-common libgnomevfs2-extra libmagick9 lsb-base lsb-release 
  python-adns python-clientcookie python-crypto python-gadfly 
  python-htmlgen python-htmltmpl python-imaging python-imaging-sane 
  python-jabber python-kjbuckets python-ldap python-mysqldb python-pam 
  python-pexpect python-pgsql python-pylibacl python-pyopenssl 
  python-pyxattr python-reportlab python-simpletal python-soappy 
  python-sqlite python-syck python-xmpp readahead synaptic sysv-rc 
  sysvutils usplash xserver-xorg-core 
The following packages will be REMOVED:
  openoffice.org-core{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 48 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  openoffice.org-writer: Depends: openoffice.org-core (> 2.0.3) but it is not installable
  openoffice.org-impress: Depends: openoffice.org-core (> 2.0.3) but it is not installable
  openoffice.org-draw: Depends: openoffice.org-core (> 2.0.3) but it is not installable
  openoffice.org-gtk: Depends: openoffice.org-core (> 2.0.2) but it is not installable
  openoffice.org-evolution: Depends: openoffice.org-core (> 2.0.3) but it is not installable
  openoffice.org-math: Depends: openoffice.org-core (> 2.0.3) but it is not installable
  openoffice.org-common: Depends: openoffice.org-core (> 2.0.3) but it is not installable or
                                  openoffice.org-core-experimental (> 2.0.3) which is a virtual package.
  python-uno: Depends: openoffice.org-core (> 2.0.3) but it is not installable
  openoffice.org: Depends: openoffice.org-core (> 2.0.3) but it is not installable
  openoffice.org-base: Depends: openoffice.org-core (> 2.0.3) but it is not installable
  openoffice.org-calc: Depends: openoffice.org-core (> 2.0.3) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
openoffice.org-core [2.0.3-4ubuntu2 (edgy)]

Score is -19

Accept this solution? [Y/n/q/?] y
The following NEW packages will be automatically installed:
  openoffice.org-core 
The following packages have been kept back:
  amarok amarok-xine apt apt-utils console-setup evolution evolution-plugins gdm hpijs initscripts libgnomevfs2-0 
  libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libmagick9 lsb-base lsb-release openoffice.org-gtk python-adns 
  python-clientcookie python-crypto python-gadfly python-htmlgen python-htmltmpl python-imaging python-imaging-sane 
  python-jabber python-kjbuckets python-ldap python-mysqldb python-pam python-pexpect python-pgsql python-pylibacl 
  python-pyopenssl python-pyxattr python-reportlab python-simpletal python-soappy python-sqlite python-syck python-xmpp 
  readahead synaptic sysv-rc sysvutils usplash xserver-xorg-core 
The following NEW packages will be installed:
  openoffice.org-core 
0 packages upgraded, 1 newly installed, 0 to remove and 48 not upgraded.
Need to get 0B/29.5MB of archives. After unpacking 83.2MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 91981 files and directories currently installed.)
Unpacking openoffice.org-core (from .../openoffice.org-core_2.0.3-4ubuntu2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/openoffice.org-core_2.0.3-4ubuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/lib/openoffice/program/ooqstart', which is also in package openoffice.org-gtk
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-core_2.0.3-4ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of openoffice.org:
 openoffice.org depends on openoffice.org-core (>> 2.0.3); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-evolution:
 openoffice.org-evolution depends on openoffice.org-core (>> 2.0.3); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-impress:
 openoffice.org-impress depends on openoffice.org-core (>> 2.0.3); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-base:
 openoffice.org-base depends on openoffice.org-core (>> 2.0.3); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-math:
 openoffice.org-math depends on openoffice.org-core (>> 2.0.3); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-draw:
 openoffice.org-draw depends on openoffice.org-core (>> 2.0.3); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-draw (--configure):
 dependency problems - leaving unconfigured
Setting up acpid (1.0.4-5ubuntu4) ...
 * Loading ACPI modules...                                                                                             [ ok ] 
 * Starting ACPI services...                                                                                                  invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of openoffice.org-calc:
 openoffice.org-calc depends on openoffice.org-core (>> 2.0.3); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-calc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-common:
 openoffice.org-common depends on openoffice.org-core (>> 2.0.3) | openoffice.org-core-experimental (>> 2.0.3); however:
  Package openoffice.org-core is not installed.
  Package openoffice.org-core-experimental is not installed.
dpkg: error processing openoffice.org-common (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-writer:
 openoffice.org-writer depends on openoffice.org-core (>> 2.0.3); however:
  Package openoffice.org-core is not installed.
dpkg: error processing openoffice.org-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-uno:
 python-uno depends on openoffice.org-core (>> 2.0.3); however:
  Package openoffice.org-core is not installed.
dpkg: error processing python-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org-java-common:
 openoffice.org-java-common depends on openoffice.org-common (>> 2.0.3); however:
  Package openoffice.org-common is not configured yet.
dpkg: error processing openoffice.org-java-common (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openoffice.org
 openoffice.org-evolution
 openoffice.org-impress
 openoffice.org-base
 openoffice.org-math
 openoffice.org-draw
 acpid
 openoffice.org-calc
 acpi-support
 openoffice.org-common
 openoffice.org-writer
 python-uno
 openoffice.org-java-common
dougie@DougiesToyBox:~$

---

### Post by Tomosaur on 2006-09-21
Alright, try:

'sudo dpkg-reconfigure openoffice.org-core'

then try starting up openoffice

---

### Post by DougieFresh4U on 2006-09-21
dougie@DougiesToyBox:~$ sudo dpkg-reconfigure openoffice.org-core
Password:
/usr/sbin/dpkg-reconfigure: openoffice.org-core is broken or not fully installed
dougie@DougiesToyBox:~$

---

### Post by Tomosaur on 2006-09-21
Very strange. Try just a simple reinstall:

sudo aptitude reinstall openoffice.org-core

---

### Post by DougieFresh4U on 2006-09-21
I'm getting tjis synaptic package manager message-libdbus-1-2(>=0.62) but 0.60.6ubuntu8 is to be instaled

---

### Post by mssever on 2006-09-21
> **DougieFresh4U said:**
> some thing failed?                          dougie@DougiesToyBox:~$ sudo aptitude purge openoffice.org-core
<snip>
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
openoffice.org-core [2.0.3-4ubuntu2 (edgy)]

Score is -19

Accept this solution? [Y/n/q/?] y
Try answering no there. When you answered yes, it didn't purge openoffice.org-core. Wait for it to give you an option to purge OOo.

If it gives you too much trouble, try ```
sudo dpkg --purge openoffice.org-core
``` I often have problems with aptitude.

---

### Post by DougieFresh4U on 2006-09-21
you have helped me in the past & I appreciate that. Thanks! Yes this is strange and that why I was wondering if I can use cd that I burned to repair although I used upgrade and not cd to install

---

### Post by DougieFresh4U on 2006-09-21
So far no luck in finding solution

---

### Post by mlind on 2006-09-21
Try
```

sudo dpkg -P --force-depends openoffice.org-core
sudo aptitude update
sudo aptitude dist-upgrade

```

---

