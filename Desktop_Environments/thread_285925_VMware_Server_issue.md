---
title: "VMware Server issue"
date: 2006-10-27
forum: Desktop Environments
---

### Post by WoodyMahan on 2006-10-27
Preamble:
Ubuntu 6.06 LTS Dapper
Lin Kernel: 2.6.15-27-386
Downloaded VMware-server-1.0.1-29996.i386.rpm from vmware website
Used alien to convert this to a .deb
I installed from the .deb

I try to open vmware from the applications-system tools menu but it does not start.

I open terminal run vmware and get the following:

woody@ubuntu-laptop:~$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.

So I follow instructions and got through the following:
 
woody@ubuntu-laptop:~$ sudo /usr/bin/vmware-config.pl
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the mime type icons?
[/usr/share/icons]

What directory contains your desktop menu entry files? These files have a
.desktop file extension. [/usr/share/applications]

In which directory do you want to install the application's icon?
[/usr/share/pixmaps]

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Server is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [yes]

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

Does anyone know what I am supposed to answer here to get this configuration working?

Thanks All!!

---

### Post by boban on 2006-10-27
try:

```

sudo aptitude install linux-headers-`uname -r` build-essential xinetd

```

You have to have kernel headers installed before compiling kernel modules...
When you'll have headers installed, then vmware should find correct path ...


(code taken from: [http://www.ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=1671637](http://www.ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=1671637))

---

### Post by The Darkness on 2006-10-27
Typically you can just hit enter here.
It usually knows what is set.
you can also do uname -r to find out the kernel version you are running.
example:
uname -r
2.6.17-10-generic
make sure you have the restricted modules installed:
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
Get htese as well:
sudo apt-get install module-assistant build-essential 
sudo apt-get install fakeroot dh-make debconf libstdc++5 
make sure you have the src and header files installed for your version:
linux-headers-$(uname -r)

then run the install.

---

### Post by dughutch on 2006-10-28
Please see this post... :)

[http://ubuntuforums.org/showthread.php?t=183209&highlight=vmware+server](http://ubuntuforums.org/showthread.php?t=183209&highlight=vmware+server)

---

### Post by WoodyMahan on 2006-10-30
> **boban said:**
> try:

```

sudo aptitude install linux-headers-`uname -r` build-essential xinetd

```

You have to have kernel headers installed before compiling kernel modules...
When you'll have headers installed, then vmware should find correct path ...


(code taken from: [http://www.ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=1671637](http://www.ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=1671637))

This did the trick.  Thanks

---

