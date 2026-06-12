---
title: "localepurge error in APT"
date: 2006-09-29
forum: Desktop Environments
---

### Post by Anonii on 2006-09-29
Greetings,


I'm having an interesting and annoying problem in APT.
When I'm trying to do any actions I get this:
"Examples of actions and their output"

```
~$ sudo aptitude dist-upgrade
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  python-soappy 
The following NEW packages will be installed:
  python-soappy 
The following packages will be upgraded:
  apport apport-gtk cpio dbus dbus-1-utils deskbar-applet gnome-mag 
  gnome-orca gnome-pilot gnome-utils java-gcj-compat language-selector 
  language-selector-common libbeagle0 libdbus-1-3 libdbus-1-dev 
  libgnome-mag2 libgnome-pilot2 libjaxp1.2-java libnotify1 libssl-dev 
  libssl0.9.8 notification-daemon openssh-client openssl powernowd 
  python-apport-utils python-problem-report ssh-askpass-gnome usplash 
30 packages upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 11.6MB of archives. After unpacking 610kB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Get:1 http://gr.archive.ubuntu.com edgy/main cpio 2.6-17 [96.4kB]
Get:2 http://gr.archive.ubuntu.com edgy/main libssl-dev 0.9.8b-2ubuntu2 [2063kB]
...
**blablablabla**
....
Get:30 http://gr.archive.ubuntu.com edgy/main usplash 0.4-30 [103kB]            
Get:31 http://gr.archive.ubuntu.com edgy/main gnome-pilot 2.0.14-0ubuntu2 [212kB]
Fetched 11.6MB in 2m55s (66.5kB/s)                                              
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 144538 files and directories currently installed.)
Preparing to replace cpio 2.6-16 (using .../archives/cpio_2.6-17_i386.deb) ...
Unpacking replacement cpio ...
Preparing to replace libssl-dev 0.9.8b-2ubuntu1 (using .../libssl-dev_0.9.8b-2ubuntu2_i386.deb) ...
Unpacking replacement libssl-dev ...
Preparing to replace libssl0.9.8 0.9.8b-2ubuntu1 (using .../libssl0.9.8_0.9.8b-2ubuntu2_i386.deb) ...
Unpacking replacement libssl0.9.8 ...
Preparing to replace openssh-client 1:4.3p2-2ubuntu5 (using .../openssh-client_1%3a4.3p2-4ubuntu1_i386.deb) ...
Unpacking replacement openssh-client ...
Preparing to replace python-problem-report 0.22 (using .../python-problem-report_0.24_all.deb) ...
Unpacking replacement python-problem-report ...
Preparing to replace python-apport-utils 0.22 (using .../python-apport-utils_0.24_all.deb) ...
Unpacking replacement python-apport-utils ...
Preparing to replace apport 0.22 (using .../archives/apport_0.24_all.deb) ...
 * Stopping automatic crash report generation: apport                    [ ok ] 
Unpacking replacement apport ...
Preparing to replace apport-gtk 0.22 (using .../apport-gtk_0.24_all.deb) ...
...
**blablablalblalba**
...
Setting up notification-daemon (0.3.5-0ubuntu7) ...

Setting up openssl (0.9.8b-2ubuntu2) ...

Setting up powernowd (0.97-1ubuntu6) ...
Installing new version of config file /etc/init.d/powernowd ...
 * Starting powernowd...                                                        /etc/init.d/powernowd: 156: cannot create /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor: Directory nonexistent
 * CPU frequency scaling not supported
                                                                         [ ok ]

Setting up python-soappy (0.11.3-1.6) ...
Compiling /var/lib/python-support/python2.5/SOAPpy/Client.py ...
  File "/var/lib/python-support/python2.5/SOAPpy/Client.py", line 46
    from __future__ import nested_scopes
SyntaxError: from __future__ imports must occur at the beginning of the file

Compiling /var/lib/python-support/python2.5/SOAPpy/GSIServer.py ...
  File "/var/lib/python-support/python2.5/SOAPpy/GSIServer.py", line 49
    from __future__ import nested_scopes
SyntaxError: from __future__ imports must occur at the beginning of the file

Compiling /var/lib/python-support/python2.5/SOAPpy/Server.py ...
  File "/var/lib/python-support/python2.5/SOAPpy/Server.py", line 46
    from __future__ import nested_scopes
SyntaxError: from __future__ imports must occur at the beginning of the file

Compiling /var/lib/python-support/python2.5/SOAPpy/Types.py ...
  File "/var/lib/python-support/python2.5/SOAPpy/Types.py", line 39
    from __future__ import nested_scopes
SyntaxError: from __future__ imports must occur at the beginning of the file


Setting up ssh-askpass-gnome (4.3p2-4ubuntu1) ...

Setting up usplash (0.4-30) ...
update-initramfs: Generating /boot/initrd.img-2.6.17-8-generic

Setting up gnome-pilot (2.0.14-0ubuntu2) ...

Errors were encountered while processing:
 localepurge
grep: /etc/locale.nopurge: No such file or directory
grep: /etc/locale.nopurge: No such file or directory
grep: /etc/locale.nopurge: No such file or directory
 No /etc/locale.nopurge file present, exiting ...
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up localepurge (0.5.5) ...
cat: /tmp/filevrQr13.locale.gen: No such file or directory
dpkg: error processing localepurge (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 localepurge

```

Also:

```
$ sudo dpkg --configure -a
Setting up localepurge (0.5.5) ...
cat: /tmp/filewPbqAo.locale.gen: No such file or directory
dpkg: error processing localepurge (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 localepurge

```

And:

```
$ sudo dpkg-reconfigure localepurge
/usr/sbin/dpkg-reconfigure: localepurge is broken or not fully installed

```

And:

```
~$ sudo aptitude reinstall localepurge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages will be REINSTALLED:
  localepurge 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up localepurge (0.5.5) ...
cat: /tmp/fileFA0eHx.locale.gen: No such file or directory
dpkg: error processing localepurge (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 localepurge
grep: /etc/locale.nopurge: No such file or directory
grep: /etc/locale.nopurge: No such file or directory
grep: /etc/locale.nopurge: No such file or directory
 No /etc/locale.nopurge file present, exiting ...
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up localepurge (0.5.5) ...
cat: /tmp/file5JyPl0.locale.gen: No such file or directory
dpkg: error processing localepurge (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 localepurge

```


Any ideas? I can do nothing at all!
I tried cleaning APT, I tried reconfiguring, installing and removing localepurge, reconfiguring it. 
What else? :/

---

### Post by Anonii on 2006-10-01
Hump de Bump

This problem is not yet fixed, and it cant stay like this.

---

### Post by carla on 2007-03-11
I hope my responses here might help:
[http://ubuntuforums.org/showthread.php?p=2282809#post2282809](http://ubuntuforums.org/showthread.php?p=2282809#post2282809)

Also, what's the output when you run ```
sudo apt-get -f install
``` to resolve dependency problems?

---

### Post by BLTicklemonster on 2007-04-08
Wonder if it was ever fixed for that poster?


Anyway, I have it installed, but can't get past the chose language section. How do I chose a language? I have it in gnome-terminal, and I can scroll down to en but how do I make it choose that? What button do I push? I push enter, and it doesn't take. What do I do?


*edit: for what it's worth: [http://bluev.wordpress.com/2005/12/27/how-to-use-localepurge/](http://bluev.wordpress.com/2005/12/27/how-to-use-localepurge/)

---

### Post by muggins on 2007-06-21
I had the same problem yesterday, I found that if you right click on your selection with the mouse it would select it.

---

