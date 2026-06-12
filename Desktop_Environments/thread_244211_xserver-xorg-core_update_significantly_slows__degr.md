---
title: "xserver-xorg-core update significantly slows / degrades performance of VMware Server"
date: 2006-08-26
forum: Desktop Environments
---

### Post by davescafe on 2006-08-26
CORRECTED: 
I posted too soon. I thought I had a good understanding of what was going on, but my testing since then has revealed that I can reproduce the performance degradation of VMware using  multiple versions of xserver-xorg-core, and, I have been able to successfully run VMware without performance degradation using the latest update of xserver-xorg-core. This indicates that xserver-xorg-core is likely not to blame for the dramatic, recent slow-down of VMware Server performance.

I apologize, and I will post more info as to the specific cause of the problem if I can manage to isolate it. I will add this information to the Bug #57790 and close it, if possible.

My original post is below (which I now have concluded is incorrect):



The August 22 update of Xserver (xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb) degrades performance of VMware server 1.0.1. A previously-installed virtual machine of Windows XP takes significantly longer to boot and shut down than prior to the update, and installs of new Windows XP virtual machines are so slow that they cannot reasonably be installed at all. Downgrading xserver-xorg-core to the previous version (xserver-xorg-core_1.0.2-0ubuntu10.1_i386.deb) restores VMware performance.

I managed to download the previous version of xserver-xorg-cor at this path:
[http://archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10.1_i386.deb) 
However, I see that it is not there anymore. I have a copy available, however.

By rolling-back the August 22 update of xserver, VMWare Server performance is restored.

I have logged this defect with Ubuntu: Bug #57790

Here are the details:
Environment:
Ubuntu 6.06 with all updates installed (plus or minus the xserver-xorg-core in question)
VMware Server 1.0.1
Virtual Machine consisting of Windows XP Pro on a 20GB dynamic partition, 2 virtual processors and 512 MB virtual RAM assigned to the VM.
Hardware:
P4 1.3 Ghz
1GB RAM
Plenty of HDD space
Performance metrics:
xserver-xorg-core_1.0.2-0ubuntu10.1_i386.deb (this version works as expected)
VM boot time: 0:50
VM shut down: 0:15
New VM install time: Approx 1 hour incl. Windows OS updates
xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb (this version degrades performance)
VM boot time: 2:12 to 3:09
VM shut down: 0:53 to 0:59
New VM install time: Install is so slow that the software appears hung. If I had the patience, I suppose it could easily take four or more hours to install the OS and updates.
Steps to Reproduce:
1. Install Ubuntu 6.06, but do not upgrade to xserver-xorg-core_1.0.2-0ubuntu10.4
2. Install VMware Server 1.0.1
3. Install a Windows XP Pro virtual machine on VMWare server.
Note performance and response time
4. Upgrade to xserver-xorg-core_1.0.2-0ubuntu10.4
Defect: Note degraded response time. Attempt to install a new Windows XP Pro virtual machine and note degraded response time.

---

### Post by theslut on 2006-08-26
the package you linked to is now missing, which is really annoying as my system is not good since this update.

i found this one 

[http://archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10_i386.deb)

but i can't install it saying a later version is already installed. how do i force it on?

---

### Post by davescafe on 2006-08-26
> **theslut said:**
> the package you linked to is now missing, which is really annoying as my system is not good since this update.

i found this one 

[http://archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.0.2-0ubuntu10_i386.deb)

but i can't install it saying a later version is already installed. how do i force it on?

I'm assuming you were using the graphical interface to install, and it won't let you because a later version is installed. The way to get past this is to use the terminal window.
1. Save any open documents or work, and close any open programs you have on the desktop. The reason for this is that we will need to restart the desktop when we are done.
2. Copy the version of xserver that you want to install to your user's home directory
3. Open a terminal window
4. You should automatically begin at your home directory. If you aren't in the directory you want to be, just use the cd command to change to the proper directory.
5. Run this command:
```
sudo dpkg -i xserver-xorg-core_1.0.2-0ubuntu10.1_i386.deb
```
6. When the previous command is complete, run this command to restart the desktop (or you can just reboot):
```
sudo /etc/init.d/gdm restart
```

Done! You should be rolled-back and VMware server should be working again.

If you cannot find the older version of xserver, you might try looking on your own machine in this directory
> /var/cache/apt/archives
If you do, be aware these file versions:
This is the version that I found to be successful in restoring VMware performance (use this one or an earlier version):
> xserver-xorg-core_1.0.2-0ubuntu10_i386.deb
This version was the bad one that created problems for a lot of people (don't use this one):
> xserver-xorg-core_1.0.2-0ubuntu10.3_i386.deb
And this version is the one that causes problems for VMware server (don't use this one):
> xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb

---

### Post by davescafe on 2006-08-26
I posted too soon. I thought I had a good understanding of what was going on, but my testing since then has revealed that I can reproduce the performance degradation of VMware using  multiple versions of xserver-xorg-core, and, I have been able to successfully run VMware without performance degradation using the latest update of xserver-xorg-core. This indicates that xserver-xorg-core is likely not to blame for the dramatic, recent slow-down of VMware Server performance.

I apologize, and I will post more info as to the specific cause of the problem if I can manage to isolate it. I will add this information to the Bug #57790 and close it, if possible.

---

### Post by davescafe on 2006-08-27
I am posting this follow up for others why may have been in the same situation I was in. If you are using VMware server, and experience a dramatic slow-down in your client operating systems, it may be fixed by reducing your virtual machine from 2 virtual processors to 1. This fixed things for me. I have also read that if you allocate more than 1GB of RAM to your virtual machines, you can experience slow-downs, but I don't have that much RAM so I have not experienced this myself.

---

### Post by lcadman on 2006-08-27
Hi all, I have a general question about the xserver-xorg-core problem.

I was one of the lucky ones to not have gone gung ho when I saw the update in the software update manager.  However, it is still on there:  xserver-xorg-core (1-1.0.2-0-ubuntu10.4).  Is it now safe to update, or best to leave it be?  How can I remove it from  showing up on the list?

Thanks--cheers!

---

### Post by davescafe on 2006-08-28
> **lcadman said:**
> Hi all, I have a general question about the xserver-xorg-core problem.

I was one of the lucky ones to not have gone gung ho when I saw the update in the software update manager.  However, it is still on there:  xserver-xorg-core (1-1.0.2-0-ubuntu10.4).  Is it now safe to update, or best to leave it be?  How can I remove it from  showing up on the list?

Thanks--cheers!

I was one of those who updated almost immediately, and my xserver broke. However, Ubuntu posted a new version approx. 17 hours after they posted the bad version. The bad version was 10.3, and the current, good version is 10.4. You can safely install the 10.4 version. I have, and it works fine on my machine. I originally thought it caused trouble with VMware, but it turned out that I was wrong. So I think you should be fine to just install the update.

---

