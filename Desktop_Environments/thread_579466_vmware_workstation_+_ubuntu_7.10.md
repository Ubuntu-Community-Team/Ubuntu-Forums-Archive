---
title: "vmware workstation + ubuntu 7.10"
date: 2007-10-18
forum: Desktop Environments
---

### Post by troelskn on 2007-10-18
I just upgraded to 7.10 and my vmware workstation ceased to function. Running /usr/bin/vmware-config.pl from the console, yields the following output:

```

root@tkn-laptop:/home/tkn# /usr/bin/vmware-config.pl
Making sure services for VMware Workstation are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Blocking file system:                                               done
   Bridged networking on /dev/vmnet0                                   done
   Host network detection                                              done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   Bridged networking on /dev/vmnet2                                   done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

Configuring fallback GTK+ 2.4 libraries.

In which directory do you want to install the theme icons? 
[/usr/share/icons] 

What directory contains your desktop menu entry files? These files have a 
.desktop file extension. [/usr/share/applications] 

In which directory do you want to install the application's icon? 
[/usr/share/pixmaps] 

Trying to find a suitable vmmon module for your running kernel.

None of the pre-built vmmon modules for VMware Workstation is suitable for your
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running
kernel? [/lib/modules/2.6.22-14-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.22-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/hostif.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/comport.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/cpuid.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/hash.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/memtrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/phystrack.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/task.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmciContext.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmciDatagram.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmciDriver.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmciDs.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmciGroup.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmciHashtable.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmciProcess.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmciResource.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmciSharedMem.o
  CC [M]  /tmp/vmware-config1/vmmon-only/common/vmx86.o
  CC [M]  /tmp/vmware-config1/vmmon-only/vmcore/moduleloop.o
  LD [M]  /tmp/vmware-config1/vmmon-only/vmmon.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config1/vmmon-only/vmmon.mod.o
  LD [M]  /tmp/vmware-config1/vmmon-only/vmmon.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
cp -f vmmon.ko ./../vmmon.o
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
The module loads perfectly in the running kernel.

This program previously created the file /dev/vmmon, and was about to remove 
it.  Somebody else apparently did it already.

Extracting the sources of the vmblock module.

Building the vmblock module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmblock-only'
make -C /lib/modules/2.6.22-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /tmp/vmware-config1/vmblock-only/linux/block.o
  CC [M]  /tmp/vmware-config1/vmblock-only/linux/control.o
  CC [M]  /tmp/vmware-config1/vmblock-only/linux/dbllnklst.o
  CC [M]  /tmp/vmware-config1/vmblock-only/linux/dentry.o
  CC [M]  /tmp/vmware-config1/vmblock-only/linux/file.o
  CC [M]  /tmp/vmware-config1/vmblock-only/linux/filesystem.o
  CC [M]  /tmp/vmware-config1/vmblock-only/linux/inode.o
  CC [M]  /tmp/vmware-config1/vmblock-only/linux/module.o
  CC [M]  /tmp/vmware-config1/vmblock-only/linux/stubs.o
  CC [M]  /tmp/vmware-config1/vmblock-only/linux/super.o
  LD [M]  /tmp/vmware-config1/vmblock-only/vmblock.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /tmp/vmware-config1/vmblock-only/vmblock.mod.o
  LD [M]  /tmp/vmware-config1/vmblock-only/vmblock.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
cp -f vmblock.ko ./../vmblock.o
make: Leaving directory `/tmp/vmware-config1/vmblock-only'
The module loads perfectly in the running kernel.

You have already setup networking.

Would you like to skip networking setup and keep your old settings as they are?
(yes/no) [yes] 

Extracting the sources of the vmnet module.

Building the vmnet module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmnet-only'
make -C /lib/modules/2.6.22-14-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /tmp/vmware-config1/vmnet-only/driver.o
  CC [M]  /tmp/vmware-config1/vmnet-only/hub.o
  CC [M]  /tmp/vmware-config1/vmnet-only/userif.o
/tmp/vmware-config1/vmnet-only/userif.c: In function 'VNetCopyDatagramToUser':
/tmp/vmware-config1/vmnet-only/userif.c:630: error: 'const struct sk_buff' has no member named 'h'
/tmp/vmware-config1/vmnet-only/userif.c:630: error: 'const struct sk_buff' has no member named 'nh'
/tmp/vmware-config1/vmnet-only/userif.c:636: error: 'const struct sk_buff' has no member named 'h'
make[2]: *** [/tmp/vmware-config1/vmnet-only/userif.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmnet-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [vmnet.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmnet-only'
Unable to build the vmnet module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

root@tkn-laptop:/home/tkn# 

```

Help.

---

### Post by unf on 2007-10-18
You need to install kernel patch for vmnet... more info on vmwares forums?

---

### Post by rubinstein on 2007-10-18
You have to install this patch: [http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update114.tar.gz](http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update114.tar.gz)

---

### Post by troelskn on 2007-10-18
It works -- It was that simple.

Thanks a lot.

---

### Post by Shimmy on 2007-10-19
Worked for my vmplayer also. thanks a lot!

---

### Post by jcronkhite on 2007-10-19
NEVERMIND! I was running the patch from its own directory.  I needed to copy the patch contents to the install directory of the vmware setup folder.  Done deal!

----------------

Anyone else doing a fresh install like me?  I get the error on a fresh install downloaded from VMWare (my company purchased Workstation 6 a while ago, so I have a license code) and I get the error.  Running the patch first seems improper since the app is not installed yet.  Any suggestions?

---

### Post by protenniser on 2007-10-19
Thanks for this useful info, nearly saved my head :D

---

### Post by knightluo on 2007-10-19
I am new to both Ubuntu and VMWare
A newbie question, 
How to install the patch I got this message when I run "sudo ./runme.pl" 

Unable to ope the installer database /etc/vmware/locations

any help?:confused:

also, I had my network working in Gusty for about a hour yesterday, but now Gusty won't recognize there is a network, but VMware is set to bridged network as before, I might messed with the setting, 
any suggestion?

Thanks

---

### Post by ArtoN on 2007-10-20
I have succeeded to setup the WMware workstation for Ubuntu 7.10. (I did not install any patches except the one I made and described below.)

1) Check that you are using VMware-workstation-6.0.1-55017.exe or VMware-workstation-6.0.2-59824.exe

2) Be sure you have downloaded the build-essentials. If not, use e.g. the Synaptics Package Manager and download it. (System/Administration/Synaptic Package Manager, search build-essentials and install it.)

3) Get the WMWare Tools into some tmp directory; VMware workstation menu VM/Install VMware Tools...
3.1) When the CD-ROM icon appeard in my screen for the first time and when I clicked it the content was 'rubbish'. I restarted Ubuntu 7.10 and after that the content showed OK.
3.2) I selected the tar file and extracted it into a tmp directory
3.3) Thanks to Frederic Staats ([http://communities.vmware.com/thread/107691;jsessionid=DF9C89ED577B875B1699520A14836CB6?tstart=30](http://communities.vmware.com/thread/107691;jsessionid=DF9C89ED577B875B1699520A14836CB6?tstart=30)) I made one modification; I navigated to the extracted archive vmware-tools-distrib/lib/modules/source/vmhgfs.tar, changed its permissions to read/write, extracted the file vmhgfs-only/compat_slab.h out of the tar, deleted the file from the tar, edited the extracted file and put it back to the tar. The change I made was like Frederic indicated: 
- The VMWare tools vmhgfs-only/compat_slab.h has a bug that prevents the hgfs kernel module from compiling:
/* 
* Destructor is gone since 2.6.23-pre1. 
*/ 
#if LINUX_VERSION_CODE < KERNEL_VERSION(2, 6, 22) || defined(VMW_KMEMCR_HAS_DTOR)

Should be:

/* 
* Destructor is gone since 2.6.23-pre1. 
*/ 
#if LINUX_VERSION_CODE <= KERNEL_VERSION(2, 6, 22) || defined(VMW_KMEMCR_HAS_DTOR)

I.e. instead of having less than it should be less than or equal.

3.4) In the vmware-tools-distrib I executed "sudo ./vmware-install.pl" and accepted all suggested locations & prompts to do something. Everything built correctly.

4) I restarted Ubuntu 7.10. Shared folders (FAT32 partition of the WIndows XP host) and network (bridged) worked fine.

5) However, I got a message that gnome settings daemon did not start correctly. At this very moment I have not solved the problem but I found a workaround; I log out from Ubuntu and then log in again. The daemon is started correctly...

I hope this would solve also you problem.... Have a nice day...

---

### Post by knightluo on 2007-10-21
Thanks ArtoN, for the step by step instruction, my vmware-tool got intall successful,
But I got few questions:
1. I restarted Gusty, but where can I find the shared folder? (I set shared folder on for VMWare already.)
2. My network is down again after install vmware-tools, it shows on for the VMWare, but Gusty just could not get anything but a warning of "Restricted driver", any idea on this?

btw my wireless card is intel4965AGN, don't know if that matters to bridged network....

Thanks in advance

---

### Post by ArtoN on 2007-10-21
VM->Settings->Options->Shared Folders - enable and specify the path (e.g. D:\)

I also got the "restricted..." warning but that's OK.

Shutting down the Ubuntu and the VMWare and restarting them helped in my networking. (Check also that your host OS can connect to the internet.) If nothing else change the network mode to the NAT.

---

### Post by tynen on 2007-10-21
What do you guys run on you're vms?

---

### Post by qbox on 2007-10-21
I tried to install vmwhare workstation 1000 times but i didnt.
Finaly I download and install VirtualBox from [www.virtualbox.org](www.virtualbox.org) and its work perfekt.
Its run much faster than vmware for windows.

---

### Post by knightluo on 2007-10-22
Hey ArtoN, Thanks for your reply,
I reinstalled my Gusty again and after intall the vmware-tools, the bridged network still worked this time. :)
Did not figure out what happened.... but it works now! :KS

> **ArtoN said:**
> VM->Settings->Options->Shared Folders - enable and specify the path (e.g. D:\)


One last question, I do have Shared Foler enabled and have set a path, but where in my linux system can I find this shared folder???

---

### Post by Anicka on 2007-10-26
I cannot reach my shared folders either, but I have an even more mysterious problem, the vmware-tools "cd" refuses to mount. I get an error message saying: Unable to mount the volume 'VMware Tools'. line 9 in /etc/fstab is bad, cannot find /media/cdrom0 or /etc/mtab.

My fstab looks like this: ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1 -- converted during upgrade to edgy
UUID=7d52d6eb-efa0-4d29-aa91-f37a49c32dc9 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=3f1f18f8-615f-4a1b-aafb-79695cad5054 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0# Beginning of the block added by the VMware software
.host:/                 /mnt/hgfs               vmhgfs  defaults,ttl=5     0 0
# End of the block added by the VMware software

```
and the mtab like this: ```
/dev/sda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
none /proc/fs/vmblock/mountPoint vmblock rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0

```
Any ideas?

---

### Post by jbroome on 2007-10-29
> **rubinstein said:**
> You have to install this patch: [http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update114.tar.gz](http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update114.tar.gz)
Worked great, thanks a bunch!

---

### Post by L0cKd0wN on 2007-11-15
Just wanted to share my success.  I was having problems with VMWare Workstation as well under the new ubuntu 7.10 .  I did:

1. sudo apt-get install build-essentials
(I thought I had them but turns out I didn't...)
2. Downloaded the "vmware-any-any-update114" .tar file and unpacked the modules to the original vmware-distrib directory I was working out of.  
3.  I moved the vmblock.tar, vmmon.tar, and vmnet.tar files to /vmware-distrib/lib/modules/source and copied over the files already in there.  I'm not sure if this was supposed to be done or not, but I figured since it was a patch, SOMETHING had to be replaced.
4. I then ran the ./runme.pl command and then afterwards the ./vmware-install.pl command and the kernel modules built like a charm.

I hope this pushes you guys in the right direction.  It's near 5:30 in the AM but I got lucky and conquered this problem!  Good luck!

L0cK

---

### Post by knowledge_6 on 2007-11-15
aight i am very new to this vmware and linux scene .. so i need a little help.

i posted in my own thread about how i get a GNOME desktop error and Ubuntu 7.04 doesn;t finish loading up off the live cd for me to install it.

so

I want to download the 7.10 iso file from Ubuntu.. 

how would i go about installing this onto my vmware server? 

thanks ; >

oh yes my host OS is windows XP .. so how and where would i go about installing this patch?

---

### Post by L0cKd0wN on 2007-11-15
knowledge_6, I think you're straying from the point of this topic which is running vmware workstation under ubuntu 7.10 - not running vmware workstation on Windows.  Regardless, depending on the Installer you use, you shouldn't need to apply a patch.  I had VMWare Workstation ACE running without complication under Windows XP a few months back - no patch required at all.  I think you should refer to the VMWare documentation about loading up an operating system or perhaps: [http://www.howtoforge.com/create-vmware-machines-from-iso-files-without-burning-cds-dvds](http://www.howtoforge.com/create-vmware-machines-from-iso-files-without-burning-cds-dvds)

Hope this pushes you in the right direction.  Let's try to keep this more on topic for people actually USING ubuntu. ;-)

L0cK

---

### Post by haroonie on 2008-01-28
> **L0cKd0wN said:**
> 
1. sudo apt-get install build-essentials
(I thought I had them but turns out I didn't...)
2. Downloaded the "vmware-any-any-update114" .tar file and unpacked the modules to the original vmware-distrib directory I was working out of.  
3.  I moved the vmblock.tar, vmmon.tar, and vmnet.tar files to /vmware-distrib/lib/modules/source and copied over the files already in there.  I'm not sure if this was supposed to be done or not, but I figured since it was a patch, SOMETHING had to be replaced.
4. I then ran the ./runme.pl command and then afterwards the ./vmware-install.pl command and the kernel modules built like a charm.
L0cK

I had the same user error and followed these steps with the "vmware-any-any-update115" available here [http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update115.tar.gz](http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update115.tar.gz) but I just replaced the files per step3, didn't run ./runme.pl and only ran ./vmware-install.pl and it worked great.

thanks.

---

### Post by Superman859 on 2008-03-14
Just posting my experience.

I had the same error as original poster.  

Then I made sure I had correct files first as I saw on another page (before this thread)

# sudo aptitude install linux-headers`uname -r` build-essential
# sudo aptitude install xinetd

Ran the install again, it seemed to make a little more progress but eventually arrived at the same error.

Read through the thread, followed link to the patch.  Gave an error saying it couldn't be found (used wget at first, then just the browser).  Page said a newer version was out (115).  Downloaded it.  Moved the contents of the archive to vmware-distrib folder.

From there, I ran sudo ./runme.pl which configured it.

```
russell@russell-ubuntu:~/installs/vmware/vmware-distrib$ sudo ./runme.pl
Updating /usr/bin/vmware ... No patch needed/available
Updating /usr/bin/vmnet-bridge ... No patch needed/available
Updating /usr/lib/vmware/bin/vmware-vmx ... No patch needed/available
Updating /usr/lib/vmware/bin-debug/vmware-vmx ... No patch needed/available
VMware modules in "/usr/lib/vmware/modules/source" has been updated.

Before running VMware for the first time after update, you need to configure it 
for your running kernel by invoking the following command: 
"/usr/bin/vmware-config.pl". Do you want this script to invoke the command for 
you now? [yes] 
```

It then went ahead and did the configuration questions.  I did not need to run ./vmware-install.pl again.

So basically make sure you have the dependencies first, then follow the instructions for the past as the last couple posters mentioned.  The only thing that differed for me was step 3.  I did not move the .tar files to the other directory - I left them in vmware-distrib and all seems ok.  Perhaps the script moves them if needed.  After running the script, the only thing it said was patched was that sources directory, so it probably does it for you if you haven't manually patched them by copying those files.

I will post if anything else shows up.

---

