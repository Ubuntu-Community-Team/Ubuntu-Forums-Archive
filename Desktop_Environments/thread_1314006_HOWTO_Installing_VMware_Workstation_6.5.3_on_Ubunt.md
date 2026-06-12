---
title: "HOWTO: Installing VMware Workstation 6.5.3 on Ubuntu 9.10 Karmic"
date: 2009-11-04
forum: Desktop Environments
---

### Post by schiotz on 2009-11-04
Hi!

I have a license for VMware Workstation 6.X, and I therefore wanted to install version 6.5.3 on my newly installed Ubuntu 9.10 laptop.   It did not work out of the box, but googling helped with a solution, that I post here in case anybody else can use it.  Note that VMware Workstation 7.X reportedly works (but my license is not valid)

A normal installation freezes.  Apparently this is due to a large number of warnings from the compiler causing a deadlock.  The wrapper below removes the options enabling all these warnings and allows the install script to complete.

Instructions:


[LIST=1]
[*]Save the Python script below in the same directory as the downloaded  VMware-Workstation-6.5.3-185404.x86_64.bundle file (or .i386. if 32 bits).  Name it gcc and make it executable.
```
#!/usr/bin/python

import sys
import copy
import os

argv = copy.copy(sys.argv)

i = len(argv)
for i in range(i-1, 0, -1):
    if len(argv[i]) > 4 and argv[i][:2] == "-W" and argv[i][3] != ",":
        del argv[i]

argv[0] = "/usr/bin/gcc"
os.execv(argv[0], argv)
```
[*]Install with the command
```
sudo env PATH=`pwd`:$PATH ./VMware-Workstation-6.5.3-185404.x86_64.bundle
```
[*]Build the kernel modules with the command
```
sudo vmware-modconfig &#8211;console &#8211;install-all
```
[*]Finally, edit the file /etc/vmware/bootstrap and add this line to the bottom
```
VMWARE_USE_SHIPPED_GTK=force
```If you omit this the mouse will behave in a highly erratic way.
[/LIST]
See also [http://aldeby.org/blog/index.php/vmware-workstation-6-5-3-on-ubuntu-karmic-9-10.html/comment-page-1](http://aldeby.org/blog/index.php/vmware-workstation-6-5-3-on-ubuntu-karmic-9-10.html/comment-page-1)

/Jakob

---

### Post by drapsag on 2009-11-16
this guide doesn't work....


the python script has no name, it doesn't seems to be executed in your guide?

---

### Post by schiotz on 2009-11-16
> **drapsag said:**
> this guide doesn't work....


the python script has no name, it doesn't seems to be executed in your guide?

No, it is not a one-click solution. :-)

You have to cut-and-paste the python script to a file, name it gcc, and make it executable, and make sure that it appears on your PATH before the real gcc while you install VMware.  Remember to remove it afterwards. 

If you are new to Linux/Unix or otherwise have problems with it, I strongly suggest using VirtualBox instead, unless you already have a VMWare license or virtual machine.   VirtualBox can be installed with Synaptics Package Manager.  It also looks easier to configure a virtual machine with VirtualBox.  I found it slightly slower, although VMware is quite sluggish too.

/Jakob

---

### Post by schiotz on 2009-11-16
> **drapsag said:**
> this guide doesn't work....

Rereading my post, I see that you are absolutely correct.  I forgot to write that the script should be named gcc.  I guess that was far from obvious ;)

Thanks for catching it!

/Jakob

---

### Post by drapsag on 2009-11-16
well I installed both... I need Vmware, so I had to install it with:

* In one terminal, run: while true; do sudo killall -9 vmware-modconfig-console; sleep 1; done
* In a second terminal, run: sudo ./VMware-Workstation-6.5.3-185404.i386.bundle --ignore-errors
* Kill loop in first terminal.
* Run: sudo vmware-modconfig --console --install-all
* Edit /etc/vmware/bootstrap to add the line: VMWARE_USE_SHIPPED_GTK=force


I didn't test jet if this will run any of my machines.... Vmware is installed correctly btw.

---

### Post by drapsag on 2009-11-16
> **schiotz said:**
> Rereading my post, I see that you are absolutely correct.  I forgot to write that the script should be named gcc.  I guess that was far from obvious ;)

Thanks for catching it!

/Jakob

gcc is an exsting command, so that was why I didn't gues that ;)

---

### Post by koorenne on 2009-12-13
I kept getting the error: "Icon name must be set." So I added the following commandline options for building the kernel modules:

--appname="VMware Workstation" --icon="vmware-workstation

So the commandline becomes:

sudo vmware-modconfig &#8211;console &#8211;install-all --appname="VMware Workstation" --icon="vmware-workstation"

---

### Post by Wabbitoid on 2009-12-13
Thanks very much for posting your icon fix, koorenne. I just ran into the error as I was going through schiotz's steps and luckily Google had just indexed your reply from 1 hr previously, so this (updated) post was my first hit.  I hit the refresh button in my FF tab, and there it was.  :)

---

### Post by borodark on 2010-01-05
Big Thank You! I had this problem too and it's solved now ..

---

### Post by NDLunchbox on 2010-04-13
I just upgraded to 6.5.4 and followed these directions.  It installed, but the mouse is still finicky.  If I try clicking on tabs to switch between VMs, the VM Console grabs the cursor.  I must go to the menu and choose a tab from there.  Same thing happens when I try clicking on anything that borders the console (side-bar options, network settings, etc).  Very annoying.

Any ideas?

---

### Post by knoxg on 2010-04-14
I'm seeing the same er-rat-ic mouse issue (geddit?) with VMware Workstation 6.5.4; instead of

VMWARE_USE_SHIPPED_GTK=force

try 

export VMWARE_USE_SHIPPED_GTK=force

in /etc/vmware/bootstrap, otherwise it doesn't seem to take effect.

---

### Post by a.gnistrup@gmail.com on 2010-05-05
I have just tested ubuntu 10.04 and vmware workstation 7.01.
It installed just fine using the hints above.

---

### Post by schiotz on 2010-05-05
I just tried to install version 6.5.4 after upgrading to Ubuntu 10.04 Lucid.  Unfortunately, the modules could not compile due to undefined symbols, apparently something has changed in the kernel.  :-(

It may mean that VMware workstation 6.5 and Ubuntu 10.04 is a no-go. 

/Jakob

---

### Post by ReetP on 2010-05-05
> **schiotz said:**
> I just tried to install version 6.5.4 after upgrading to Ubuntu 10.04 Lucid.  Unfortunately, the modules could not compile due to undefined symbols, apparently something has changed in the kernel.  :-(

It may mean that VMware workstation 6.5 and Ubuntu 10.04 is a no-go. 

/Jakob


Nope, I have 6.5.4 on 10.04 up & running (AMD64 but I think it will work for other CPUs)

Read the following :

[http://linux.aldeby.org/vmware-workstation-6-5-3-on-ubuntu-karmic-9-10.html](http://linux.aldeby.org/vmware-workstation-6-5-3-on-ubuntu-karmic-9-10.html)

[http://communities.vmware.com/thread/228949](http://communities.vmware.com/thread/228949)

[http://communities.vmware.com/message/1436970#1436970](http://communities.vmware.com/message/1436970#1436970)
[http://communities.vmware.com/message/1401588#1401588](http://communities.vmware.com/message/1401588#1401588) (get the two required patch files from here)



Basically this :


Run this in one terminal :

while true; do sudo killall -9 vmware-modconfig-console; sleep 1; done

Then the installer in another -this gets the files installed

Next put the two patch files you got above into /usr/lib/vmware/modules/source

Run the patch file which will modify the modules and then compile them.

The longest hardest part was finding out the above which took me hours. Actually doing it took minutes.

Just got too sort out the goddam mouse now which doesn't like the whole screen. Sorted it before but forgot how !

---

### Post by ReetP on 2010-05-05
The above solution solves the mouse situation as well I'm pleased too say. All working quite happily.

---

### Post by schiotz on 2010-05-05
Yes!  I also found these pages:

[http://communities.vmware.com/thread/236411](http://communities.vmware.com/thread/236411)
[http://blog.gnu-designs.com/solved-building-vmware-workstation-modules-on-linux-2-6-32](http://blog.gnu-designs.com/solved-building-vmware-workstation-modules-on-linux-2-6-32)

although the scripts in the latter did not work for me (strange).

I did the following:

1) Install VMware workstation 6.5.4 according to my instructions in
the beginning of this thread, i.e. save the Python script in a file
named gcc in the same directory as the VMware*.bundle file, make it
executable, and run it *as root* with

```
env PATH=`pwd`:$PATH ./VMware-Workstation-6.5.4-246459.x86_64.bundle

```I *did not* run the vmware-modconfig script, as it fails.

2) As root, go to /usr/lib/vmware/modules/source, unpack two of the
tar files, and edit a file manually.  First, vmnet:

```
cd /usr/lib/vmware/modules/source
tar xvf vmnet.tar
```Then edit vmnet-only/vnetUserListener.c and add the line

```
#include "compat_sched.h"
```after the other #include lines in the beginning of the file.  Then
pack it again:

```
mv vmnet.tar vmnet.tar.BACKUP
tar cvf vmnet.tar vmnet-only
```Then repeat the same for vmci.tar, this time the file to edit is
vmci-only/linux/include/pgtbl.h and the same #include line should be
added after the other include lines.


Then you can start VMware.  The first time you do it, do it as root,
then the modules are built automatically.  Or you can build them on
the command line as described in this thread.

```
sudo vmware
```Hmm, somewhat tedious, but workable.

Regarding the mouse problem, I start vmware from a script which sets 
VMWARE_USE_SHIPPED_GTK=yes

It also revs up my CPUs, and starts the vmware services (I do not want to have them running permanently, as I don't use vmware that much).

```
#! /bin/bash

export VMWARE_USE_SHIPPED_GTK=yes
sudo /usr/local/bin/performance high

grep vmnet /proc/modules > /dev/null || (sudo /etc/init.d/vmware start; sleep 3)
#ps aux | grep -v grep | grep smbd > /dev/null || (sleep 20; sudo /etc/init.d/samba start) &
/usr/bin/vmware

#sudo /etc/init.d/samba stop
sudo /etc/init.d/vmware stop

sudo /usr/local/bin/performance normal

```

---

