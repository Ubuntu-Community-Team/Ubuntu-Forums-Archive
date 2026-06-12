---
title: "XP in Virtual Machine, file sharing"
date: 2009-05-19
forum: General Help
---

### Post by berdux on 2009-05-19
Hello! sorry if this has already been answered but i am searching the forums for about an hour and have not found anything :)

I installed today Virtual Machine and windows XP. How can i share files and folders with it?

it has a feature to add hardware, i try to add for example IDE hard drive and select sdb and sdb1 but it does not accept it, when i restart it, it doesnot boot..

---

### Post by kestrel1 on 2009-05-19
Is this Virtual Machine (VMWare) or Virtual Box (Sun)?

---

### Post by Egi_Power on 2009-05-19
> **berdux said:**
> Hello! sorry if this has already been answered but i am searching the forums for about an hour and have not found anything :)

I installed today Virtual Machine and windows XP. How can i share files and folders with it?

it has a feature to add hardware, i try to add for example IDE hard drive and select sdb and sdb1 but it does not accept it, when i restart it, it doesnot boot..
```
VBoxManage sharedfolder add **virtualmachinename** -name "sharename" -hostpath "/home/**username**/**foldertoshare**"
```

where
**virtualmachinename** is the name virtual machine you created.
**username** is your ubuntu home directory name. It's usually /home/your user name.
**foldertoshare** is the name of the folder you want to share.

On the Windows command line, use the following:
```
net use **x**: \\vboxsvr\**sharename**
```
Replace "**x**:" with the drive letter that you want to use for the share, and **sharename** with the share name specified with VBoxManage.

BTW, you could look in Help -> Contents (***F1***) in VirtualBox.
It is explained there in details.

[I]EDIT:
My apologies:
I misunderstood, I thought it was VirtualBox.
END OF EDIT[/I]

Egi_Power

---

### Post by 3rdalbum on 2009-05-19
Create a share on the host operating system and the guest will be able to access it as long as it has network access (which should happen by default).

---

### Post by berdux on 2009-05-19
It is Virtual Machine (VMWare), it is installed on my 1st PC (Ubuntu1)

Ubuntu1 is able to see my shared drives from my 2nd pc (Ubuntu2).
The 2nd pc (Ubuntu2) is able to see the 1st's drives

the virtual machine cannot see anything from my network.

i made the drive shared inside the virtual machine but Ubuntu1+2 cannot see that.

virtual machine has internet. 

Ubuntu1 cannot ping the ip of virtual machine (10.0.2.15)
Virtual Machine cannot ping anything except the default gateway (10.0.2.2) (not either any internet server like google.com, though it resolves the hostname)

so i'm stuck here...


(my network has IPs: 192.168.2.x)

---

### Post by berdux on 2009-05-20
still haven't found anything...

for now i can throw files inside the virtual machine throuhg the dvd drive (i make an iso file and load it on the virtual machine)

---

### Post by berdux on 2009-05-23
i swiched to virtual box and everything worked fine :)

---

### Post by kestrel1 on 2009-05-23
I have always found VirtualBox to be very good for virtualization. I tend to use it for trying out other OSes & it is free.

---

### Post by stefangr1 on 2009-05-23
In VMWARE, I always use a shared folder on the windows xp virtual machine. Ubuntu can access that (but only while the VM is on).

---

