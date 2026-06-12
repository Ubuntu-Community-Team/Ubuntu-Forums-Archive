---
title: "Resizing VMWare virtual machines??"
date: 2006-05-01
forum: Desktop Environments
---

### Post by Goonie on 2006-05-01
Hi

I'm running Breezy and VMWare Player with a Windows XP virtual machine. When I created the virtual machine I set it for 4GB but now I find that isn't big enough for good old bloated Windows. Is there a way to allow for more space without having to create a whole new virtual machine?

Thx

Goonie

---

### Post by mannheim on 2006-05-03
Probably the vmware forums might help more. 

"VMware Workstation" comes with a tool called **vmware-diskmanager** which can (amongst other things) expand the size of virtual disks. 

I don't know if that is available in "Player". If you can get hold of a virtual disk (extension .vmdk) you can add it to your virtual machine at ide0:1 (for example) by editing the .vmx file. Add a couple of lines at the end like

```
ide0:1.present = "TRUE"
ide0:1.fileName = "Another-virtual-disk.vmdk"

```

(I've never tried this, so proceed at your own risk.)

---

### Post by rcarring on 2006-05-04
Ubuntu Breezy Badger under VMWARE is a 10GB virtual scsi disk. I am surprised you got it to work at all under an emulated Windows installation. It may be your Ubuntu disk is getting too big. Move it to an external hard drive and repoint your vmware player to look at the hard file externally. If you have Office 2003 installed under Windows, you may want to uninstall it and use Open office instead to create some more room.

---

### Post by Goonie on 2006-05-06
Sorry for the late reply, been away for a while. 

> "VMware Workstation" comes with a tool called vmware-diskmanager which can (amongst other things) expand the size of virtual disks.

I don't know if that is available in "Player". If you can get hold of a virtual disk (extension .vmdk) you can add it to your virtual machine at ide0:1 (for example) by editing the .vmx file. Add a couple of lines at the end like

As far as I know the diskmanager tool is not available for the Player. As for adding a partition to my virtual machine for added storage space (that's how I understood your suggestion at least), I don't think that will solve anything because my problem isn't that I've run out of space for new files. It's just that after installing Windows and Office on a 4GB virtual drive I have 160MB left on the drive and Windows doesn't run well. That wouldn't change if I added more storage on a different drive. I guess I could add a "second drive" and install Office there but I think this is not really worth the effort. I only need 1GB more to make room for a handful of files and a reasonably sized "swap drive" for windows to run on. If I could get my PPTP VPN connection to work in Ubuntu I wouldnt really need Windows in WMVare. I would just install Office via Crossover Office. But Since I can't get VPN any other way, this will have to be the way to go for now.

As for utilizing different hard drives, this is not an option because I'm running on a laptop and can't add more drives.

Thx
Goonie

---

### Post by mannheim on 2006-05-08
> As far as I know the diskmanager tool is not available for the Player. 

I believe there are 30-day trial versions of things like VMware Workstation (and maybe a free beta version of VMware Server ?) available. One possibility might be to download one of those, and use the diskmanager tool.

---

### Post by _Chris_ on 2006-05-09
From my experience with creating virtual machines in VMware Server Beta, once you choose the partition size, you can not change it.  I highly recommend downloading the VMware Server Admin Manual.pdf, and the Server Virtual Machine Manual.pdf from VMware.com.  One of the installation notes states that you can not change the initial size you created.
In regards to disk capacity, it states that "This virtual disk can never be larger than the maximum capacity that you set here" Pg 49 of VMware Server Virtual Machine Guide.  
-Good luck

---

### Post by mannheim on 2006-05-09
Well, I've never done it myself, but the Help files for VMware Workstation seem to say you can enlarge disks created by Workstation:

> **Using VMware Virtual Disk Manager**

VMware Virtual Disk Manager is a utility in VMware Workstation that allows you to create, manage and modify virtual disk files from the command line or within scripts.

One key feature is the ability to enlarge a virtual disk so its maximum capacity is larger than it was when you created it. This way, if you find you need more disk space in a given virtual machine, but you do not want to add another virtual disk or use ghosting software to transfer the data on a virtual disk to a larger virtual disk, you can instead change the maximum size of the virtual disk. This is something you cannot do with physical hard drives. 

---

### Post by Goonie on 2006-05-09
I'll probably end up buying the workstation and start over as soon as I fix my new problem... ghosting my system onto a larger hard drive without rendering grub useless beyond repair.

Thx guys

Goonie

---

