---
title: "Ubuntu 24 Desktop via RDP not Detecting GPU"
date: 2024-08-16
forum: Desktop Environments
---

### Post by naxal on 2024-08-16
Hello,

Following are the desktop pc configuration on which I have installed Ubuntu 24 LTS Desktop

HP Z230 SFF Desktop PC
Intel Core i7 4790 // Intel C226 Chipset Motherboard
Nvidia GT 730 GPU (2GB GDDR5) // 16GG DDR3 RAM
256GB SATA SSD

Things are smooth and working fine when I am using physical login. System Settings are showing my GPU. However, whenever I am login into via Remote Desktop, I see my CPU usage pegged at 40-50% with RDP working via software rendering. On remote desktop access, system settings doesn't show the GPU anymore and shows software rendering.

```
root@H1:/home/xxx# 
nvidia-smiFri Aug 16 21:20:03 2024       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 470.256.02   Driver Version: 470.256.02   CUDA Version: 11.4     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. |
|===============================+======================+======================|
|   0  NVIDIA GeForce ...  Off  | 00000000:01:00.0 N/A |                  N/A |
| N/A   62C    P0    N/A /  N/A |    117MiB /  1993MiB |     N/A      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                                  |
|  GPU   GI   CI        PID   Type   Process name                  GPU Memory |
|        ID   ID                                                   Usage      |
|=============================================================================|
|  No running processes found                                                 |
+-----------------------------------------------------------------------------+
root@H1:/home/xxx# 

```

```
root@H1:/home/xxx# lspci
00:00.0 Host bridge: Intel Corporation 4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:16.3 Serial controller: Intel Corporation 8 Series/C220 Series Chipset Family KT Controller (rev 04)
00:19.0 Ethernet controller: Intel Corporation Ethernet Connection I217-LM (rev 05)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation C226 Series Chipset Family Server Advanced SKU LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GK208B [GeForce GT 730] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GK208 HDMI/DP Audio Controller (rev a1)
root@H1:/home/xxx# 

```

```

# System Details Report
---


## Report details
- **Date generated:**                              2024-08-16 21:35:01


## Hardware Information:
- **Hardware Model:**                              Hewlett-Packard HP Z230 SFF Workstation
- **Memory:**                                      16.0 GiB
- **Processor:**                                   Intel® Core™ i7-4790 × 8
- **Graphics:**                                    Software Rendering
- **Disk Capacity:**                               1.4 TB


## Software Information:
- **Firmware Version:**                            L51 v01.52
- **OS Name:**                                     Ubuntu 24.04 LTS
- **OS Build:**                                    (null)
- **OS Type:**                                     64-bit
- **GNOME Version:**                               46
- **Windowing System:**                            Wayland
- **Kernel Version:**                              Linux 6.8.0-40-generic

```

What do I do? How to solve this issue? If possible, please help.

Thanks.

---

### Post by ActionParsnip on 2024-08-16
What are you doing on the remote system that needs the full desktop session? There may be a sleeker solution to what you want to do

---

### Post by TheFu on 2024-08-16
Remote desktops don't use the GPU.  That's life.

If you want more responsible remote desktop access, there are other options, provided you don't use Gnome or KDE.  Interested?

Also, if your client workstation is running Linux and you are on the same LAN, there are more convenient ways to run GUI programs remotely, but have the window displayed on your local desktop of the local workstation.  This is usually fast enough that nearly any programs work great, though video editing wouldn't be something I tried.  Any productivity apps, email, web browser type things, this is how I run daily and have for the last 25 yrs.  I seldom run standard GUI programs on the system I happen to be sitting behind.

BTW, don't run as root. That's a bad idea for many reasons.

---

### Post by naxal on 2024-08-16
Hello,

Thanks for the reply.

I dont have a running display plugged in. So I cant use that desktop sharing function. It is not working without any display. I have this Ubuntu PC in headless mode.

I need that GUI mainly for few reasons, namely,

1. I need to run and manage that QEMU/KVM based VMs
2. I would like to have a GUI for random tasks, file file browsing, system settings and such, which feels much easier over GUI rather trying to spend hours on finding the right commands.

What are my options now?

Thanks.

---

### Post by TheFu on 2024-08-16
kvm/qemu can be remotely managed using **virt-manager** from any client system.  This is how I do it.  But I only use virt-manager to install and destroy VMs.  For day to day running, I use remote X/Windows through ssh to run specific programs ... or get a GUI terminal on the other system and run anything from there.  [https://virt-manager.org/](https://virt-manager.org/)

If I need a full remote desktop and I'm on the same LAN, I'll use **virt-viewer**. [https://manpages.ubuntu.com/manpages/jammy/man1/virt-viewer.1.html](https://manpages.ubuntu.com/manpages/jammy/man1/virt-viewer.1.html)
If I need a full remote desktop and I'm outside the LAN - anywhere in the world, then I use **x2go**.  I've used x2go to access my desktop at home from 4 different continents.  Running a lite GUI for this connection is important.   [https://wiki.x2go.org/doku.php](https://wiki.x2go.org/doku.php)

For using a file manager on a remote system, there are lots of methods that don't need a full remote desktop.  Full remote desktops are wasteful.

Remote desktop is something that MS-Windows needs due to limitations in that OS, but not Unix.  What's the program you want to use for the file manager?  

Because my systems support seamless **sftp**, I use any local file manager (almost any of them can be used) and connect into the other systems, then browse the directories and files that way, if I'm desperate for a GUI.  

If you like, you can use a local file manager and **sshfs** to access the files on the remote system. No need for a remote GUI at all.  Or NFS would work too. Because sshfs or NFS is outside the file manager, no specialized support inside the program is needed. They all work once sshfs or NFS is setup.  NFS should be faster.  Remote storage feels like local storage and on the local system, both just appear to be directories with lots of subdirectories that happen to be stored on other systems.  It is easy to forget that remote storage is being accessed. It really is.

I'm old-time Unix guy and 99% of the time, I'd use an **ssh** connection with a shell to the remote system to do file management.  Most linux people these days use a GUI file manager. They don't know the power of the shell (the dark force) for file management.

Always remember, RDP is a foreign protocol that a non-Unix company created. It isn't anywhere where optimized for Linux systems.  For remote access to MS-Windows computers, RDP is the hammer, seeking a nail.  With non-MSFT OSes, we have other, non-nail, options.

---

### Post by naxal on 2024-08-17
Hello,

Thanks again for the reply.

> kvm/qemu can be remotely managed using virt-manager from any client system.

My other computers are Windows based and I am unable to find anything to manage VMs from Windows. Any pointer?

> If I need a full remote desktop and I'm on the same LAN, I'll use virt-viewer.

I dont need GUI for any VM. I can manage them on SSH.

> If I need a full remote desktop and I'm outside the LAN

Apache Guacamole works good for me but never tried that for Linux GUI. But I guess problem will be same here too, since RDP is the issue.

> I'm old-time Unix guy and 99% of the time, I'd use an ssh connection with a shell to the remote system to do file management. Most linux people these days use a GUI file manager. They don't know the power of the shell (the dark force) for file management.

SSH is good, I agree, it is faster but only if I can remember all the commands :( often, the time I spend is searching for the right command

> Always remember, RDP is a foreign protocol that a non-Unix company created.

I dont have to use RDP. Remote GUI of this Desktop Ubuntu PC is what I needed and RDP happen to be there working out of the box. So please point me to something else, which can give me a smoother remote GUI of this desktop ubuntu pc.

Thanks.

---

### Post by TheFu on 2024-08-17
I used to use MS-Windows, but found it too limiting.  Initially, I'd run a tiny VM with X11 to be able to work with Linux ... ssh and GUI tools.


> I dont need GUI for any VM. I can manage them on SSH.
Then you don't need virt-manager.  Use **virt-viewer** from MS-Windows.  With QXL video, which was the default BEFORE newer virtio became available, performance is quite excellent for everything except video editing or FPS games.

Why are you trying to remember ssh commands?  Create the scripts you need, once.  Just use a descriptive name and be done with it.  You do know about the ~/.ssh/config file, right?  Also, use ssh-agent.

> So please point me to something else, which can give me a smoother remote GUI of this desktop ubuntu pc.
I already did, above.  Read again.  I used x2go from MS-Windows for years and from Linux systems when traveling for decades now.

I'm not a fan of guacamole.  Webapps are constantly being hacked.  At least with NX, the network connection is secured using standard protocols that are well-understood and constantly under security testing and updates.

---

### Post by ActionParsnip on 2024-08-20
You can mount the remote file system using SSHFS and manage your files that way. Dead simple, especially from Mac/Linux. What settings do you change?

---

### Post by naxal on 2024-08-20
Hello,

Thank you for your reply.

> **ActionParsnip said:**
> What settings do you change?

I dont change settings always but like in day to day operation, if I need something. 

Like for example, while trying to deploy a QEMU VM, I get to learn that it needs Bridge Mode networking in Host OS for same subnet. Creating a bridge mode is like 3/4 clicks on GUI while a lot of searching and reading to edit network via CLI. 

Stuff like that. Random things. Which feels really intuitive and easy with having access to GUI.

Thanks.

---

### Post by TheFu on 2024-08-20
> **naxal said:**
> Like for example, while trying to deploy a QEMU VM, I get to learn that it needs Bridge Mode networking in Host OS for same subnet. Creating a bridge mode is like 3/4 clicks on GUI while a lot of searching and reading to edit network via CLI. 

Bridge mode is on the hostOS, not each client.  Set up once, give it a name, br0 is common, then when you create the network however you create a new VM, use that name, br0, as the network device.  Done and done.  The VM guest OS doesn't know anything about that.

There are lots of netplan examples that actually work on netplan.io.  Also, these forums have netplan examples with bridges too.

I've found AI tools to be useful, but not definitive.  About 50% of the time, even with specific questions written like code requirements, AI tools seem to fail about 50% of the time.  Most of the answers seem "reasonable", but if you don't actually validate them, that's where they tend to fail.  There's a huge difference in providing book-learned advice and getting advice from someone with hands on experience.  Just sayin'.

---

### Post by currentshaft on 2024-08-20
free

---

