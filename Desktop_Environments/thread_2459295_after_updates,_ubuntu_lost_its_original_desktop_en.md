---
title: "after updates, ubuntu lost its original desktop environment"
date: 2021-03-15
forum: Desktop Environments
---

### Post by dave219 on 2021-03-15
hello team:

after today's updates, my display resolution only has 640x480(4:3) (no other options anymore). also second monitor is not recognizable any more. are there ways to fix this? is it a bad driver? i am using my old lenovo T420 for this.

```
user@home:~$ lspci -nnk | grep VGA -A1
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF119M [Quadro NVS 4200M] [10de:1057] (rev a1)
    Subsystem: Lenovo GF119M [Quadro NVS 4200M] [17aa:21ce]

```
```
user@home:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.2 LTS
Release:            20.04
Codename:    focal
```

```
user@home:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-5.8.0-45-generic linux-hwe-5.8-headers-5.8.0-45 linux-image-5.8.0-45-generic linux-modules-5.8.0-45-generic linux-modules-extra-5.8.0-45-generic
  linux-modules-nvidia-390-5.8.0-45-generic
The following packages will be upgraded:
  libglib2.0-0 libglib2.0-bin libglib2.0-data linux-generic-hwe-20.04 linux-headers-generic-hwe-20.04 linux-image-generic-hwe-20.04 linux-modules-nvidia-390-generic-hwe-20.04
7 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 89.5 MB of archives.
After this operation, 416 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 linux-modules-5.8.0-45-generic amd64 5.8.0-45.51~20.04.1 [15.4 MB]
Get:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 libglib2.0-data all 2.64.6-1~ubuntu20.04.3 [5,988 B]
Get:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 libglib2.0-bin amd64 2.64.6-1~ubuntu20.04.3 [73.0 kB]
Get:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 libglib2.0-0 amd64 2.64.6-1~ubuntu20.04.3 [1,285 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 linux-image-5.8.0-45-generic amd64 5.8.0-45.51~20.04.1+1 [9,565 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 linux-modules-extra-5.8.0-45-generic amd64 5.8.0-45.51~20.04.1 [41.0 MB]
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 linux-generic-hwe-20.04 amd64 5.8.0.45.51~20.04.31 [1,932 B]                                                                         
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 linux-image-generic-hwe-20.04 amd64 5.8.0.45.51~20.04.31 [2,688 B]                                                                   
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 linux-hwe-5.8-headers-5.8.0-45 all 5.8.0-45.51~20.04.1 [11.4 MB]                                                                     
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 linux-headers-5.8.0-45-generic amd64 5.8.0-45.51~20.04.1 [1,438 kB]                                                                 
Get:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 linux-headers-generic-hwe-20.04 amd64 5.8.0.45.51~20.04.31 [2,576 B]                                                                
Get:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/restricted amd64 linux-modules-nvidia-390-5.8.0-45-generic amd64 5.8.0-45.51~20.04.1 [9,294 kB]                                                
Get:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/restricted amd64 linux-modules-nvidia-390-generic-hwe-20.04 amd64 5.8.0-45.51~20.04.1 [5,508 B]                                                
Fetched 89.5 MB in 9s (9,478 kB/s)                                                                                                                                                    
<snip>
```


thanks

_dave

---

### Post by ActionParsnip on 2021-03-16
What is the output of:
```

sudo lshw -C display

```
Thanks

---

### Post by dave219 on 2021-03-16
>  [COLOR=#000000][FONT=&quot]sudo lshw -C display [/FONT][/COLOR]

```
user@home:~$ sudo lshw -C display
[sudo] password for user: 
  *-display UNCLAIMED       
       description: VGA compatible controller
       product: GF119M [Quadro NVS 4200M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:f2000000-f2ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:5000(size=128) memory:c0000-dffff
```

---

### Post by CelticWarrior on 2021-03-16
UNCLAIMED is the problem. Please check:

1 - Whether or not the Nvidia drivers are installed.
2 - Whether or not Secure Boot is disabled.

---

### Post by dave219 on 2021-03-16
> **CelticWarrior said:**
> UNCLAIMED is the problem. Please check:

1 - Whether or not the Nvidia drivers are installed.
2 - Whether or not Secure Boot is disabled.

this workstation has been in operation for over 3 months until this upgrade (not a VM). that is why i suspect the new nvidia driver has problem.

i don't remember i installed secure boot. how could i check this?

---

### Post by zpraven on 2021-03-16
The same problem occured.
I'm using KDE Neon (Ubuntu 20.04 based).
Cause of failure - package
linux-modules-nvidia-390-5.8.0-45-generic
The package does not install correctly.


Installation errors:
[https://pastebin.com/fpQTW0XY](https://pastebin.com/fpQTW0XY)


Solved by rolling back to old kernel 5.8.0-44.

You can check error with yourself by trying to reinstall this package linux-modules-nvidia-390-5.8.0-45-generic.

---

### Post by CelticWarrior on 2021-03-16
Secure Boot is a UEFI ("BIOS") feature. If enabled it prevents unsigned drivers such as Nvidia's from loading and typically result in a similar "unclaimed" status, hence my question.

Regardind drivers, a [COLOR=#000000][FONT=&quot]Quadro NVS 4200M can run *only* with the latest long term support branch, 390. For how long this drivers will be supported is anyone's guess. Once the 390 branch no longer can be installed with newer kernels, support from Nvidia is over. It may or may not (probably not) be supported by the open-source alternative *nouveau*&#8203; driver.[/FONT][/COLOR]

---

### Post by CelticWarrior on 2021-03-16
> **zpraven said:**
> The same problem occured.
I'm using KDE Neon (Ubuntu 20.04 based).
Cause of failure - package
linux-modules-nvidia-390-5.8.0-45-generic
The package does not install correctly.


Installation errors:
[https://pastebin.com/fpQTW0XY](https://pastebin.com/fpQTW0XY)


Solved by rolling back to old kernel 5.8.0-44.

You can check error with yourself by trying to reinstall this package linux-modules-nvidia-390-5.8.0-45-generic.

Great find!
Hopefully the next kernel update will work correctly.

---

### Post by zpraven on 2021-03-17
Package update released
5.8.0-45.51~20.04.1+1
Everything worked :)

---

### Post by dave219 on 2021-03-18
> **zpraven said:**
> Package update released
5.8.0-45.51~20.04.1+1
Everything worked :)


confirmed! thanks.

---

