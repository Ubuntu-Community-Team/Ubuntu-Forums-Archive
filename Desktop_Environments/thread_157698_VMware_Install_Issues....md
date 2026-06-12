---
title: "VMware Install Issues..."
date: 2006-04-09
forum: Desktop Environments
---

### Post by Swiss on 2006-04-09
I am trying to install VMware Server, but after installing (almost) it spits this out... 

```
Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Player is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for
your system (you need to have a C compiler installed on your system)? [no]

For more information on how to troubleshoot module-related problems, please
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

Any way around this?

---

### Post by towsonu2003 on 2006-04-09
just got an idea: 
sudo apt-get update
sudo apt-get install build-essential

than try reinstalling and teling it to build the module for you at that prompt. if that fails, try
sudo apt-get install gcc-3.4
export CC=gcc-3.4

than try installation again + tell it to build module.

---

### Post by briancurtin on 2006-04-09
check out a support forum maybe.

---

### Post by Swiss on 2006-04-09
Okay, it got past the "Text Sceen Of Death" (Thanks) But now this:
```

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

```

I have no idea where they would be! ](*,)

---

### Post by Stormbringer on 2006-04-09
Open a terminal.

Type *uname -r* and write down its output ( i.e.: 2.6.12-10-amd64-k8 )

[QUOTE=Swiss]I have no idea where they would be![/QUOTE]

If you haven't installed anything else than "build-essential" and "gcc-3.4" then you're missing at least the kernel header files.

Type *sudo apt-get install kernel-headers-`uname -r`* to install the required package.

[QUOTE=Swiss]
```

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

```
[/QUOTE]

Answer the question with */lib/modules/<kernelversion>/build/include* - subsitute <kernelversion> with the output of *uname -r*.

Storm.

---

### Post by Swiss on 2006-04-10
```
If you haven't installed anything else than "build-essential" and "gcc-3.4" then you're missing at least the kernel header files.

Type sudo apt-get install kernel-headers-`uname -r` to install the required package.
```

Result:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kernel-headers-2.6.12-10-386


You have been very helpful! :cool:

---

### Post by opus on 2006-04-10
You are missing the kernel header files.  The command to install them however is:
```
sudo apt-get linux-headers-2.6.12-10-386
```
You should also create the symbolic link to make it easier for VMWare to find them:
```
sudo ln -s /usr/src/linux-headers-2.6.12-10-386 /usr/src/linux
```
After this, you should be able to just hit enter when it asks where the headers are (if it still asks).

Aaron

---

### Post by Stormbringer on 2006-04-10
Sorry, my bad.

# sudo apt-get install linux-headers-2.6.12-10

Storm.

---

### Post by Swiss on 2006-04-10
```
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.12-10 /usr/src/linux
The path "/usr/src/linux-headers-2.6.12-10 /usr/src/linux" is not an existing
directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]  /usr/src/linux-headers-2.6.12-10-386 /usr/src/linux

The path "/usr/src/linux-headers-2.6.12-10-386 /usr/src/linux" is not an
existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]
```

](*,)

---

### Post by opus on 2006-04-10
Oops - sorry - I forgot to the mkdir line.  Try:
```
sudo mkdir /usr/src/linux
sudo ln -s /usr/src/linux-headers-2.6.12-10-386 /usr/src/linux

```
THEN re-run the configuration (or installer) script.  Just push enter when it asks where the header files are.

Aaron

---

### Post by Swiss on 2006-04-10
> jack@GNUgeneration:~$ sudo mkdir /usr/src/linux
Password:
mkdir: cannot create directory `/usr/src/linux': File exists
jack@GNUgeneration:~$ sudo ln -s /usr/src/linux-headers-2.6.12-10-386 /usr/src/linux
ln: `/usr/src/linux': File exists
jack@GNUgeneration:~$


After having pressed enter:
> 
What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]



:-?

---

### Post by DeShark on 2006-04-10
The directory that I think it's after is /usr/src/linux-headers-2.6.12-10-386/include.. not just /usr/src/linux-headers-2.6.12-10-386. (note the include). Try that and cross your fingers.

---

### Post by Swiss on 2006-04-10
> What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]  /usr/src/linux-headers-2.6.12-10-386/include

The path "/usr/src/linux-headers-2.6.12-10-386/include" is not an existing
directory.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]



I am honored your first bean was spent upon one of my problems! :-D

---

### Post by opus on 2006-04-10
Using the full path will work too.  I think what happened is the link was created but pointed to the wrong place.  so a sudo rm /usr/src/linux, sudo ln -s /usr/src/linux-headers-2.6.12-10-386 /usr/src/linux would then create the proper link, allowing you to accept the default location of /usr/src/linux/include.

Aaron

---

### Post by Swiss on 2006-04-10
Nothing is working! :confused:  

Maybe you (Aaron) could fix it over remote Control? (VNC)

---

### Post by Swiss on 2006-04-10
This: 
> 
/usr/src/linux-headers-2.6.12-10

Is the correct command, however: 

> The path "/usr/src/linux-headers-2.6.12-10" is an existing directory, but it
does not contain a "linux" subdirectory as expected.


Progress!

---

### Post by opus on 2006-04-10
Let's try this first (even if you have already tried them :)):
```
sudo rm /usr/src/linux
sudo ln -s /usr/src/linux-headers-2.6.12-10-386 /usr/src/linux
sudo ls /usr/src -l
```
Then post the output of the ls command (or any errors you get) back here.

---

### Post by Swiss on 2006-04-10
Command sudo ls /usr/src -l:


> jack@GNUgeneration:~$ sudo ls /usr/src -l
total 12
drwxr-sr-x   3 root src  4096 2006-03-14 11:08 hamachi
lrwxrwxrwx   1 root src    36 2006-04-10 11:56 linux -> /usr/src/linux-headers-2.6.12-10-386
drwxr-xr-x  18 root root 4096 2006-04-10 10:04 linux-headers-2.6.12-10
drwxr-xr-x   7 root root 4096 2006-04-09 09:03 rpm
jack@GNUgeneration:~$


---

### Post by opus on 2006-04-10
Cool - I see what the problem is now. We are linking to a folder that doesn't exist (the 386 part).  Try:
```
sudo rm /usr/src/linux
sudo ln -s /usr/src/linux-headers-2.6.12-10 /usr/src/linux
sudo ls /usr/src -l
```
Then try the config again.  If it still doesn't work, post the output of the ls command again.

---

### Post by Swiss on 2006-04-10
> What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The directory of kernel headers (version 2.6.12-10) does not match your running
kernel (version 2.6.12-10-386).  Even if the module were to compile
successfully, it would not load into the running kernel.


jack@GNUgeneration:~$ sudo ls /usr/src -l
total 12
drwxr-sr-x   3 root src  4096 2006-03-14 11:08 hamachi
lrwxrwxrwx   1 root src    32 2006-04-10 12:06 linux -> /usr/src/linux-headers-2.6.12-10
drwxr-xr-x  18 root root 4096 2006-04-10 10:04 linux-headers-2.6.12-10
drwxr-xr-x   7 root root 4096 2006-04-09 09:03 rpm
jack@GNUgeneration:~$

---

### Post by opus on 2006-04-10
At least we are still making progress.  :)  I think we got the wrong linux headers.  We need the ones with the -386 after them.  They match your kernel version.  Run these:
```
sudo rm /usr/src/linux
sudo apt-get remove linux-headers-2.6.12-10
sudo apt-get install linux-headers-2.6.12-10-386
sudo ln -s /usr/src/linux-headers-2.6.12-10-386 /usr/src/linux

```
And try try again.  :)

---

### Post by Swiss on 2006-04-10
Okay... :)

---

### Post by opus on 2006-04-10
So that worked?

---

### Post by Swiss on 2006-04-10
I'm checking, I had to eat my lunch... :D

---

### Post by Swiss on 2006-04-10
Yes! It worked!




```
What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.12-10-386/build/include]

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.12-10-386/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-config0/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config0/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST
  CC      /tmp/vmware-config0/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config0/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
The module loads perfectly in the running kernel.

Do you want networking for your virtual machines? (yes/no/help) [yes]

Configuring a bridged network for vmnet0.

Your computer has multiple ethernet network interfaces available: eth0, eth1.
Which one do you want to bridge to vmnet0? [eth0]

The following bridged networks have been defined:

. vmnet0 is bridged to eth0

Do you wish to configure another bridged network? (yes/no) [no]

Do you want to be able to use NAT networking in your virtual machines? (yes/no)
[yes]

Configuring a NAT network for vmnet8.

Do you want this program to probe for an unused private subnet? (yes/no/help)
[yes]

Probing for an unused private subnet (this can take some time)...

```

> 
The configuration of VMware Player 1.0.1 build-19317 for Linux for this running
kernel completed successfully.


Thanks! You were very helpful & kind... :D
I am running Kubuntu in VMware Player at the moment. (While using Gnome)

---

### Post by n00blar on 2006-04-12
This is a very nice walkthrough thread. I just installed the latest version of VMWare following this post. Someone needs to 'sticky' this or something.
Great work guys!! :)

---

### Post by opus on 2006-04-12
I'm actually in the process of creating a howto for installing VMWare server.  Look for it in the next couple of days in the howto forum.  :)

Aaron

---

### Post by engineering.concepts on 2006-04-16
Is there any way around this?
It can not find the linking files?

maximus@Maximus:~$ sudo apt-get install linux-headers-2.6.12-10-686
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  linux-headers-2.6.12-10
The following NEW packages will be installed:
  linux-headers-2.6.12-10 linux-headers-2.6.12-10-686
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 6725kB of archives.
After unpacking 70.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main linux-headers-2.6.12-10 2.6.12-10.28
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main linux-headers-2.6.12-10-686 2.6.12-10.28
  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.12/linux-headers-2.6.12-10_2.6.12-10.28_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.12/linux-headers-2.6.12-10_2.6.12-10.28_i386.deb)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.12/linux-headers-2.6.12-10-686_2.6.12-10.28_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.12/linux-headers-2.6.12-10-686_2.6.12-10.28_i386.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
maximus@Maximus:~$

---

### Post by engineering.concepts on 2006-04-16
[QUOTE=engineering.concepts]Is there any way around this?
It can not find the linking files?

maximus@Maximus:~$ sudo apt-get install linux-headers-2.6.12-10-686
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  linux-headers-2.6.12-10
The following NEW packages will be installed:
  linux-headers-2.6.12-10 linux-headers-2.6.12-10-686
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 6725kB of archives.
After unpacking 70.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main linux-headers-2.6.12-10 2.6.12-10.28
  404 Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main linux-headers-2.6.12-10-686 2.6.12-10.28
  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.12/linux-headers-2.6.12-10_2.6.12-10.28_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.12/linux-headers-2.6.12-10_2.6.12-10.28_i386.deb)  404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.12/linux-headers-2.6.12-10-686_2.6.12-10.28_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.12/linux-headers-2.6.12-10-686_2.6.12-10.28_i386.deb)  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
maximus@Maximus:~$[/QUOTE]




even though this command shows

maximus@Maximus:~$ uname -r
2.6.12-10-686
maximus@Maximus:~

It turns out from searching google that 2.6.12-9-686 is available.
Will this still work ok?

---

### Post by engineering.concepts on 2006-04-16
I was able to install  2.6.12-9-686, but now my error is 

The directory of kernel headers (version 2.6.12-9) does not match your running
kernel (version 2.6.12-10-686).  Even if the module were to compile
successfully, it would not load into the running kernel.

---

### Post by engineering.concepts on 2006-04-16
It looks like if I do an

 sudo apt-get update

the download works, but i still get an kernel error
The directory of kernel headers (version 2.6.12-10) does not match your running
kernel (version 2.6.12-10-686).  Even if the module were to compile
successfully, it would not load into the running kernel.

---

### Post by Swiss on 2006-04-16
```
sudo rm /usr/src/linux
sudo apt-get remove linux-headers-2.6.12-10
sudo apt-get install linux-headers-2.6.12-10-686
sudo ln -s /usr/src/linux-headers-2.6.12-10-686 /usr/src/linux
```


Try that...

---

### Post by engineering.concepts on 2006-04-16
[QUOTE=opus]At least we are still making progress.  :)  I think we got the wrong linux headers.  We need the ones with the -386 after them.  They match your kernel version.  Run these:
```
sudo rm /usr/src/linux
sudo apt-get remove linux-headers-2.6.12-10
sudo apt-get install linux-headers-2.6.12-10-386
sudo ln -s /usr/src/linux-headers-2.6.12-10-386 /usr/src/linux

```
And try try again.  :)[/QUOTE]


:-D :-D :-D
I just changed the 386 to 686 after doing an update and It finally worked!!!!
:-D :-D :-D

---

### Post by Swiss on 2006-04-16
Did you see my last post? :D  ;)

---

### Post by hotani on 2006-04-17
- deleted - 

figured it out just as I clicked "post reply"... :)

---

### Post by engineering.concepts on 2006-04-17
Sorry, I did not see your last post Swiss, BUT THANKS FOR YOUR HELP!!!!
IT IS VERY APPRECIATED!!!:-D :-D :-D

---

### Post by engineering.concepts on 2006-04-17
VMware will crash on me when it looks for my network (when WinXP tells me approx 34 minutes left) I am tryind to install WinXP with SP2. Is there any particular version I should get? Does Win2000 install better? Would WinXP without SP1 or SP2 not give me this issue?

---

### Post by Robor on 2007-10-17
> **DeShark said:**
> The directory that I think it's after is /usr/src/linux-headers-2.6.12-10-386/include.. not just /usr/src/linux-headers-2.6.12-10-386. (note the include). Try that and cross your fingers.

I know this post is old and I hate to bump old stuff but this solution just worked for me with getting VMWare Server installed in Gutsy.  Of course with the newer kernel the command was a little different.  My fix was 'sudo apt-get install linux-headers-2.6.22-14-386'.  During the VMWare Server install I had to point the VMWare script to /usr/src/linux-headers-2.6.22-14-386/include and that worked.  Thanks for the help and hope that helps someone else.  :)

---

### Post by GabrielDunn on 2007-10-21
Hey...I have been working on this since last night and I've read a dozen threads..still no luck. 

 > The directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match 
your running kernel (version 2.6.22-14-generic).  Even if the module were to 
compile successfully, it would not load into the running kernel.

What is the location of the directory of C header files that match your running 
kernel? [/usr/src/linux/include] 


I cant seem to get around this...Im still a linux noob, but I can follow orders well enough...any ideas?  It seems the problem is the whole 'generic' thing, but I dont know how to get the 386 headers into my kernel...and I dont know how to recompile...I just downloaded the gutsy iso and greated the vmware in workstation 5.5.  Did you all make your own VMware? or download one premade?  Someone should share one with the vmtools installed.  :)

So how could I proceed?

---

