---
title: "Failed to install package"
date: 2009-03-18
forum: General Help
---

### Post by thornate on 2009-03-18
I'm trying to install some webcam drivers via a .deb file that I downloaded [from here]("https://launchpad.net/~nickel62metal/+archive/ppa"). When I ran the .deb file, I got the following error message:

```
Creating symlink /var/lib/dkms/microdia/2009.01/source ->
                 /usr/src/microdia-2009.01

DKMS: add Completed.
Installing prebuilt kernel module binaries (if any)
Building module...

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.27-11-generic KVER=2.6.27-11-generic src=/var/lib/dkms/microdia/2009.01/build....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.27-11-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/microdia/2009.01/build/ for more information.
0
0
dpkg: error processing microdia-dkms (--install):
 subprocess post-installation script returned error exit status 10
Processing triggers for man-db ...

```

This is the make.log:
```
DKMS make.log for microdia-2009.01 for kernel 2.6.27-11-generic (i686)
Wed Mar 18 22:42:57 EST 2009
make -C /lib/modules/2.6.27-11-generic/build SUBDIRS=/var/lib/dkms/microdia/2009.01/build modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /var/lib/dkms/microdia/2009.01/build/sn9c20x-usb.o
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /var/lib/dkms/microdia/2009.01/build/sn9c20x-usb.c:27:
include/linux/mmzone.h:18:26: error: linux/bounds.h: No such file or directory
include/linux/mmzone.h:197:5: warning: "MAX_NR_ZONES" is not defined
In file included from include/linux/gfp.h:4,
                 from include/linux/kmod.h:22,
                 from include/linux/module.h:13,
                 from /var/lib/dkms/microdia/2009.01/build/sn9c20x-usb.c:27:
include/linux/mmzone.h:218: error: ‘MAX_NR_ZONES’ undeclared here (not in a function)
make[2]: *** [/var/lib/dkms/microdia/2009.01/build/sn9c20x-usb.o] Error 1
make[1]: *** [_module_/var/lib/dkms/microdia/2009.01/build] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [driver] Error 2
```
How do I clear these errors and get the package to install?

---

### Post by fieroboom on 2009-03-18
This is one of those little reasons that I <3 apt... ;)
All you need to do in order to get apt to chase dependencies for you is:
```
sudo apt-get install -f
```
A lot of 3rd party debs, such as webmin, will fail due to unmet dependencies, and the -f switch is short for --fix-broken. That will automatically install the dependencies and then finish your deb install.
[Apt-get man page](http://linux.die.net/man/8/apt-get). Under "Options", it's the second one.
:D
-Paul

---

### Post by skymera on 2009-03-18
The repos are listed on that link you provided. 
You don't need to download the .deb

```
 sudo gedit /etc/apt/sources.list 
```

Add this to the end: (Change intepid to whatever release you run)
```
deb http://ppa.launchpad.net/nickel62metal/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/nickel62metal/ppa/ubuntu intrepid main 
```

```
sudo apt-get update
sudo apt-get install *name* 
```

Here's a guide from the page you linked:
[https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories](https://help.launchpad.net/Packaging/PPA#Adding%20a%20PPA%20to%20your%20Ubuntu%20repositories)

---

### Post by thornate on 2009-03-18
I had already tried that. I get the following error message when I try to update:

> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 31CCA643CC60BA1F

---

### Post by drs305 on 2009-03-18
Edited: Per post #11, fieroboom is correct that sudo is not used to import the keys.

Launchpad has added keys to increase security so you have to import the keys. Here is one way to do it:
```
 
gpg --keyserver keyserver.ubuntu.com --recv 31CCA643CC60BA1F  
gpg --export --armor 31CCA643CC60BA1F   | sudo apt-key add -
sudo apt-get update
		
```

---

### Post by thornate on 2009-03-18
Running the first line gives the following error:
> gpg: WARNING: unsafe ownership on configuration file `/home/nathan/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error


---

### Post by drs305 on 2009-03-18
> **thornate said:**
> Running the first line gives the following error:

When you get the error you cited it is usually due to improper permissions - they are probably currently set to allow others to modify or access the file.

Change them with the following command and try the commands above again:
```

chmod 750 ~/.gnupg/gpg.conf

```

---

### Post by thornate on 2009-03-18
I'm afraid that I still get that error. 

I also tried changing the permissions and ownership to being the same as the other files in that directory (being **-rw------- 1 root   root**) but this didn't make a difference. Have changed the ownership back to me again.

---

### Post by drs305 on 2009-03-18
The .gnupg folder should be in your $HOME folder and the contents should all be owned by you and not root. It seems you are saying you have files therein owned by root. 

Hopefully someone else will verify all the files in that folder are and should be owned by the user and not root. At least that is the way I have gnupg installed on my machine.

Added: Back to solving the problem, here is a YouTube video on adding Launchpad keys that may solve things for you:
[http://www.youtube.com/watch?v=UUZOQsNo_ws]("http://www.youtube.com/watch?v=UUZOQsNo_ws")

---

### Post by thornate on 2009-03-18
I tried changing the ownership of the other two files to me but it didn't make a difference.

---

### Post by fieroboom on 2009-03-18
> **thornate said:**
> I tried changing the ownership of the other two files to me but it didn't make a difference.

**No! Think of sudo as a huge elephant gun. ONLY fire it when you need to. And for the love of green grass, chmod & chown should NOT be your first line of defense for permission denied type errors! There is a reason you're getting an error, and chown/chmod is not the way to troubleshoot it!**

These first two commands need to be run without sudo at the beginning, like this:
```
 
gpg --keyserver keyserver.ubuntu.com --recv 31CCA643CC60BA1F  
gpg --export --armor 31CCA643CC60BA1F   | sudo apt-key add -
sudo apt-get update
```

I just covered this in [this thread](http://ubuntuforums.org/showthread.php?t=1099084&highlight=fieroboom), see post #5.
On a side note, you'll notice that if you try to run wine as sudo, you'll get the same type of error, warning that /home/user/.wine is not owned by you.
:D
-Paul

EDIT:
If you absolutely insist on running those commands with sudo, then the correct way to do it is with the --no-permission-warning switch, as [outlined here](http://ubuntuforums.org/showthread.php?t=620462), post 6.

---

### Post by thornate on 2009-03-19
I'm afraid that removing the sudo didn't work either, because the other files in that directory were owned by root. But... uhh... ignoring your advice, I changed the ownership to me and ran it again without the sudo and it worked fine to import the keys.

But apt-get still didn't work; I got the same error as when I tried to install from the .deb file (see original post).

---

### Post by fieroboom on 2009-03-19
> **thornate said:**
> I'm afraid that removing the sudo didn't work either, because the other files in that directory were owned by root. But... uhh... ignoring your advice, I changed the ownership to me and ran it again without the sudo and it worked fine to import the keys.

But apt-get still didn't work; I got the same error as when I tried to install from the .deb file (see original post).

The reason you need not use sudo OR chown is because anything in your home directory should be owned by you... That's why it's *your* home directory.

Regarding apt still failing, did you ever run the command from my first reponse (post #2)?
In case you didn't, or somehow missed it, here's the command that will install the dependencies and your program for you:
```
sudo apt-get install -f
```
In my first post, I failed to put sudo in front of the command... I corrected that.
:D
-Paul

---

### Post by fieroboom on 2009-03-19
Here's a good example of that command in operation:
```
root@pallen:~# dpkg -i /save/downloads/webmin_1.410_all.deb
Selecting previously deselected package webmin.
(Reading database ... 126687 files and directories currently installed.)
Unpacking webmin (from .../downloads/webmin_1.410_all.deb) ...
dpkg: dependency problems prevent configuration of webmin:
 webmin depends on libnet-ssleay-perl; however:
  Package libnet-ssleay-perl is not installed.
 webmin depends on libauthen-pam-perl; however:
  Package libauthen-pam-perl is not installed.
 webmin depends on libio-pty-perl; however:
  Package libio-pty-perl is not installed.
 webmin depends on libmd5-perl; however:
  Package libmd5-perl is not installed.
dpkg: error processing webmin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 webmin
```

Note that webmin fails due to dependencies. Now I just make apt chase them down and install them for me:

```
root@pallen:~# apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libauthen-pam-perl libio-pty-perl libmd5-perl libnet-ssleay-perl
The following NEW packages will be installed:
  libauthen-pam-perl libio-pty-perl libmd5-perl libnet-ssleay-perl
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 285kB of archives.
After this operation, 1380kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com intrepid/main libnet-ssleay-perl 1.35-1ubuntu1 [205kB]
Get:2 http://us.archive.ubuntu.com intrepid/universe libauthen-pam-perl 0.16-1.1 [33.0kB]
Get:3 http://us.archive.ubuntu.com intrepid/universe libio-pty-perl 1:1.07-1build1 [40.9kB]
Get:4 http://us.archive.ubuntu.com intrepid/universe libmd5-perl 2.03-1 [5680B]
Fetched 285kB in 3s (85.6kB/s)
Selecting previously deselected package libnet-ssleay-perl.
(Reading database ... 141802 files and directories currently installed.)
Unpacking libnet-ssleay-perl (from .../libnet-ssleay-perl_1.35-1ubuntu1_i386.deb) ...
Selecting previously deselected package libauthen-pam-perl.
Unpacking libauthen-pam-perl (from .../libauthen-pam-perl_0.16-1.1_i386.deb) ...
Selecting previously deselected package libio-pty-perl.
Unpacking libio-pty-perl (from .../libio-pty-perl_1%3a1.07-1build1_i386.deb) ...
Selecting previously deselected package libmd5-perl.
Unpacking libmd5-perl (from .../libmd5-perl_2.03-1_all.deb) ...
Processing triggers for man-db ...
Setting up libnet-ssleay-perl (1.35-1ubuntu1) ...
Setting up libauthen-pam-perl (0.16-1.1) ...
Setting up libio-pty-perl (1:1.07-1build1) ...
Setting up libmd5-perl (2.03-1) ...
Setting up webmin (1.410) ...
Webmin install complete. You can now login to https://pallen:10000/
as root with your root password, or as any user who can use sudo
to run commands as root.
```

:D
-Paul

---

### Post by thornate on 2009-03-19
I'm afraid that that still has given me the same error.

---

