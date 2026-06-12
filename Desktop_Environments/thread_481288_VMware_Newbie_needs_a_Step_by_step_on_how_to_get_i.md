---
title: "VMware? Newbie needs a Step by step on how to get it up and running"
date: 2007-06-22
forum: Desktop Environments
---

### Post by Antonio44 on 2007-06-22
Can someone please give me the most basic simplest way to get xp running on my ubuntu laptop. I heard I can have it running in a window. I know that I use VMware. But the instructions are just so complicated. It would also let me use the basic applications and such that I need from windows. Please help. I mean I need it simple. Screenshots would make someone my hero. Also location of all the files I will need. Please have a heart and help.


Thanks.

A.

---

### Post by jamesrl on 2007-06-22
Vmware isn't the simplest method; VirtualBox is.  The following is from an email I wrote to someone explaining how VirtualBox works.

There is a free program called VirtualBox ([http://www.virtualbox.org/](http://www.virtualbox.org/)) that can run an operating system within an operating system as a Virtual Machine [VM].  It works best with machines that have multiple processors (and plenty of memory as you need to devote ~256Mb to the VM for windows to use) as typically you devote one whole processor to the VM.  The Intel duo-core processors support x86 virtualization (you may have to enable virtualization in the BIOS settings; type F12/F2/Del/Bkspc or what-ever when you boot to go to the BIOS menu and see if there are any options for enabling Virtualization), so both linux and windows will run at full speed at the same time, however multitasking within windows or linux will both act as if they only had one processor.

Download & install VirtualBox from the website.  The easiest way to do that and stay up to date is to add a line to your /etc/apt/sources.list (this adds a repository to your list, so you automatically update VirtualBox when a new edition comes out with bug fixes).
```

sudo nano /etc/apt/sources.list
```
and then at the end add:
```

deb http://www.virtualbox.org/debian feisty non-free
```
(if you are running edgy or dapper replace feisty with edgy or dapper).

Then add the key for the repository (so it is signed) with this command:
```

wget http://www.virtualbox.org/debian/innotek.asc -O - | sudo apt-key add -
```
(the wget downloads the public key from innotek, the apt-key part adds it to your list of keys that apt trusts to download packages from).  

Then run 
```

sudo apt-get update
sudo apt-get install virtualbox
```
and it will be installed (the first line updates your apt-get with your new repository, and the second one installs VBox).

Within VirtualBox you create a new virtual machine, which requires a virtual HD (of about 12Gb) [that is a large file within my linux partition that acts like a hard drive] and then within it use a windows xp cd to install windows (taking the 30minutes or so windows normally takes to install) to that virtual hard drive.  Then whenever you want to run a windows program, just boot up the windows virtual machine (wait the ~30sec it takes for windows to start) and run programs from within it.  I'd also recommend after you install windows that you then install "Virtual Box Guest Additions".  This improves mouse integration (so you don't have to press Right-Ctrl every time you want to switch between OS), and allows you to resize windows easily, go into fullscreen mode, etc.  You can install it easily from the Devices menu from the running virtual machine window.

You don't have to worry about hardware compatibility usually, as the virtual machine will just borrow the internet/audio/etc. from linux (i.e., if linux is connected to a wireless network, the virtual machine is automatically on the internet).  You can also mount a cd or a USB stick to it if you want. 

The only problem I have ever had with VirtualBox is in an older versions when I had my linux hard drive as a network folder within windows, this made the virtual machine a little unstable.  This probably has been fixed (though you could always just email/download the files fine - just transferring from a linux HD as a network folder didn't work). Also whenever linux upgrades the running kernel, you have to run a line to update the vbox driver, though Virtual Box will tell
you what line to run when you get this error:  
```
sudo /etc/init.d/vboxdrv setup
```
Also I do not know if it is possible yet to resize your virtual hard drive within VirtualBox, so think about the amount of space you need for linux/windows.

VMWare is much more a pain to install and less intuitive.

---

### Post by mwhmgt on 2007-06-22
I use VMware on several host OS systems, including Ubuntu.  I find it installs easily (just read the instructions) and is very stable.  I run many guest OS systems, including multiple versions of MS Winders.

I've also used a VM from Parallels.  I don't have as much experience with it as VMware but so far it appears stable.  It certainly costs less.

Just a note that both of these are commercial products.

---

### Post by jamesrl on 2007-06-22
Virtual Box is free (as well as Qemu) though only partially open source (a few parts aren't open source; like USB drivers aren't open source, but free to use for personal use from the binary installation).  All the features most users will ever need are in VBox and it has better benchmarks than VMware (see [http://bbs.archlinux.org/viewtopic.php?pid=258022]("http://bbs.archlinux.org/viewtopic.php?pid=258022") or [http://www.linux-gamers.net/smartsection.item.56/virtualbox-vs-qemu.html]("http://www.linux-gamers.net/smartsection.item.56/virtualbox-vs-qemu.html")).  

However, VMware has the most features, but you have to pay for it.  [Extra features are things like use a dual boot partition as a virtual machine, or be able to resize partitions.  I'm not sure if the free VMware player supports these features; and im not sure how well they work either.  At one point I tried very unsuccessfully to get VMware player to work on my laptop with a dual boot and couldn't get it to work.  It claimed you needed the partitions on different physical hard drives.]

---

### Post by ddo on 2007-06-25
VMWare server is free.  You can download it ( make sure to register to get a serial number from VMWare folks).
Assuming you are using Feisty, here is the thread that you can follow to load VMWare Server on Feisty.
       [http://ubuntuforums.org/showpost.php?p=2384779&postcount=52](http://ubuntuforums.org/showpost.php?p=2384779&postcount=52)
** the correct site to get  the patch vmware-any-any-update109.tar.gz is to cut and paste this
     wget [http://ftp.cvut.cz/vmware/vmware-any-any-update109.tar.gz](http://ftp.cvut.cz/vmware/vmware-any-any-update109.tar.gz)

If your Ubuntu version is earlier than Feisty, then just follow the first first part of the Howto and disregard the steps about patching. Just select default option from the the installation script. also if you are new to VMWare then I suggest using bridge port option for network connection.
Good luck.

---

### Post by fjf on 2007-06-25
Both VMware server and virtualbox are free, easy to install and run.  But VMW lacks an important feature (that you can get if you pay 180$): sharing folders between the virtual machine and the host.  Without this, you'll have a hard time sending folders from one to another, because they don't "see" eachother.  You can set up a virtual network with SAMBA and the VMW machine, but that is not for newbies like me.

---

