---
title: "creating a virtual machine for gaming"
date: 2011-10-26
forum: Gaming &amp; Leisure
---

### Post by murderd2death on 2011-10-26
im currently dual booting windows and ubuntu. windows is just for gaming. the biggest let down for me is having to leave all my media behind just to get into my sterile windows partition. has anyone ever made a windows 7 virtual machine and install video games from their to play? how well does that work?

---

### Post by ajgreeny on 2011-10-26
Not very well for many games.

They depend on having all the direct-x libraries and good video drivers etc etc, which you will get in a full, partitioned windows installation, but in a VM you will be using the video drivers of Ubuntu;  not so good for many games.

---

### Post by murderd2death on 2011-10-26
can you install the windows drivers on the virtual machine?

---

### Post by ss900 on 2011-10-26
I dont' think that the 3d hardware acceleration implemented in most of the virtual machine software (such as VirtualBox) lets your video card unleash it's power, so I don't think you will get good performance by your Windows games. 

In order to open your media from your Windows "boot" you may try to install the ext2fsd project ([http://www.ext2fsd.com/](http://www.ext2fsd.com/)) on your Windows to Ext2,Ext3 and Ext4 partitions.

---

### Post by a2j on 2011-10-26
its not the drivers, its the hardware. virtual video hardware is not for games.

---

### Post by ubupirate on 2011-10-26
You can play *some* games through virtualbox, but don't expect to be able to play most modern 3D games at all due to the lack of 3D support.

Old games I'm sure it could handle.

---

### Post by CharlesA on 2011-10-26
Works for D2. ;)

But not for much else.

---

### Post by ubupirate on 2011-10-26
> **CharlesA said:**
> Works for D2. ;)

But not for much else.

Yea, but D2 can run on pretty much the lowest spec computer ever. xD

---

### Post by CharlesA on 2011-10-26
> **ubupirate said:**
> Yea, but D2 can run on pretty much the lowest spec computer ever. xD
Lol true.

---

### Post by Paddy Landau on 2011-10-26
> **ss900 said:**
> ... most of the virtual machine hypervisors (such as VirtualBox)
There is a significant difference between a *supervisor* and a *hypervisor*.


[LIST]
[*]*Supervisor:* Running one or more virtual machines (VM) on a host. The guest machines depend on the host; the host takes a hit; and the guest machines do not run to full capacity. If the host crashes, the guests all fail. Example: [VirtualBox]("https://www.virtualbox.org/").
[/LIST]

[LIST]
[*]*Hypervisor:* Also called a virtual machine manager (VMM). Running two or more machines fully independently of each other. No machine depends on another, and no machine takes a hit because of the other. If one machine crashes, the others still continue. Example: [KVM]("http://www.linux-kvm.org/").
[/LIST]

A hypervisor would probably solve your problem, as you can switch quickly between Windows and Ubuntu without having to reboot. You need suitable hardware, however: a 64-bit machine with virtualisation support (you may have to enable it in your BIOS), and sufficient RAM; I suspect 4Gb would suffice.

The default hypervisor for Ubuntu is KVM, but there are others such as [Xen]("http://xen.org/").

Some references:

[LIST]
[*][http://en.wikipedia.org/wiki/Hypervisor](http://en.wikipedia.org/wiki/Hypervisor)
[*][https://help.ubuntu.com/community/Xen](https://help.ubuntu.com/community/Xen) (dated)
[*][http://aethylred.blogspot.com/2011/05/xen-41-and-ubuntu-1104.html](http://aethylred.blogspot.com/2011/05/xen-41-and-ubuntu-1104.html) (dated)
[*][https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)
[/LIST]
    
I understand that installing a hypervisor is quite complicated, so don't do it unless you have a **full backup** and are prepared to do a bit of research.

---

### Post by ss900 on 2011-10-26
> **Paddy Landau said:**
> 
A hypervisor would probably solve your problem, as you can switch quickly between Windows and Ubuntu without having to reboot. You need suitable hardware, however: a 64-bit machine with virtualisation support (you may have to enable it in your BIOS), and sufficient RAM; I suspect 4Gb would suffice.

Thank you for sharing the information about supervisor and hypervisor anyway I don't think that a hypervisor may be a good solution for gaming since I'm not really sure that hypervisors implement full, stable and fast hardware acceleration suitable for Direct3D.

---

