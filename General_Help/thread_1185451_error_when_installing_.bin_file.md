---
title: "error when installing .bin file"
date: 2009-06-12
forum: General Help
---

### Post by kelz101 on 2009-06-12
Hey,
Im trying to install Maple 13 and it gives me this error, and I dont know how to fix it. Im just wondering if anyone out there may be able to help.  I have Ubuntu 8.10 Intrepid Ibex, 64 bit. This is the error i get:

kelsey@kelsey-desktop:~$ ./Maple64.bin
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

/tmp/install.dir.7385/Linux/resource/jre/bin/java: 1: Syntax error: "(" unexpected
kelsey@kelsey-desktop:~$

---

### Post by 3rdalbum on 2009-06-12
I don't know anything about Maple. But it looks like the installer is trying to install its own version of the Java Runtime Environment (JRE). If you haven't already, you should install the version available in the Ubuntu repositories. Once that's installed, I think the Maple installer should recognise it and use it rather than install its own.

The other thing is, you're running the installer as your own user account. This means that it won't be able to write to any system-wide locations; are you sure the installer can install into your own home directory? If it needs to write to a system-wide location (most installers do) then you need to switch your terminal to root with this command:

```
sudo su
```

Then run the installer. After running the installer, either close the terminal or type:

```
exit
```

to get back to your normal user mode.

---

### Post by Soul-Sing on 2009-06-12
offtopic

I would recommend genius math. software which could be installed via synaptic package manager. ( Maybe next to maple? ) :)

---

### Post by kelz101 on 2009-06-12
I installed JRE, and used sudo su, at it gave me the same error, and it still used the jre from archive. Sorry if im being so unhelpful, this is the first time ive tried installing something outside of synaptic.

kelsey@kelsey-desktop:~$ sudo su
[sudo] password for kelsey: 
root@kelsey-desktop:/home/kelsey# ./Maple64.bin
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

/tmp/install.dir.6681/Linux/resource/jre/bin/java: 1: Syntax error: "(" unexpected
root@kelsey-desktop:/home/kelsey#

---

### Post by michy99 on 2009-06-12
I would think that for the amount of money they charge for Maple 13, they would provide customer support.

---

### Post by kamicc on 2010-09-11
Have same problem with  Maple13LinuxX86_64Installer.bin and Ubuntu 10.04 :(


Tried another installer from the web. It worked.

So probably Corrupted Installer.

---

