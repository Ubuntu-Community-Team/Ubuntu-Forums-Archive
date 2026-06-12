---
title: "Problem in creating VM"
date: 2009-06-04
forum: General Help
---

### Post by prema on 2009-06-04
Hi 

I have created a  ubuntu image . Using this image to create a VM on xen.
I have create ubuntu image using the source ubuntu8.04 . while creating the image,  mirror path is given as  [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) is used.

The image use the config file 

name = 'one-new246'
memory  = '256'
kernel = '/boot/vmlinuz-xen'
ramdisk = '/boot/initrd-xen'
root = '/dev/sda4 ro'
#extra = 'ro'
#extra='xencons=tty'
disk = [
    'tap:aio:/home/vm-image/ubuntu/disk.img,sda4,w',
]
vif = [
    'ip=10.101.102.245,bridge=eth0',
]
vfb = ['type=vnc,vnclisten=127.0.0.1,vncdisplay=9999']


once the vm is created it shows vm is created immediatley  it disappears . 
and also the partition are as shown below.
so alsocorrect me on the partion sda4 mentioned by me in config file .

l-4000061:/var/log/xen # df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda4             52261452  38396540  11210172  78% /
udev                    456376       216    456160   1% /dev
/dev/sda2               782696     62800    680136   9% /boot
/dev/sda3             10989652   3996716   6434680  39% /var
/dev/sda1             15358108  11810248   3547860  77% /windows/C



The log file says 
[2009-06-04 17:08:47 14342] DEBUG (DevController:151) Waiting for devices ioports.
[2009-06-04 17:08:47 14342] DEBUG (DevController:151) Waiting for devices tap.
[2009-06-04 17:08:47 14342] DEBUG (DevController:156) Waiting for 2052.
[2009-06-04 17:08:47 14342] DEBUG (DevController:620) hotplugStatusCallback /local/domain/0/backend/tap/17/2052/hotplug-sta
[2009-06-04 17:08:47 14342] DEBUG (DevController:634) hotplugStatusCallback 1.
[2009-06-04 17:08:47 14342] DEBUG (DevController:151) Waiting for devices vtpm.
[2009-06-04 17:08:47 14342] INFO (XendDomain:1167) Domain one-new246 (17) unpaused.
[2009-06-04 17:08:51 14342] WARNING (XendDomainInfo:1283)[COLOR=Red] Domain has crashed: name=one-new246 id=17.[/COLOR]
[2009-06-04 17:08:51 14342] DEBUG (XendDomainInfo:1997) XendDomainInfo.destroy: domid=17
[2009-06-04 17:08:51 14342] DEBUG (XendDomainInfo:2014) XendDomainInfo.destroyDomain(17)
[2009-06-04 17:08:51 14342] DEBUG (XendDomainInfo:1580) Destroying device model
[2009-06-04 17:08:51 14342] DEBUG (XendDomainInfo:1587) Releasing devices
[2009-06-04 17:08:51 14342] DEBUG (XendDomainInfo:1593) Removing vif/0
[2009-06-04 17:08:51 14342] DEBUG (XendDomainInfo:590) XendDomainInfo.destroyDevice: deviceClass = vif, device = vif/0
[2009-06-04 17:08:51 14342] DEBUG (XendDomainInfo:1593) Removing vbd/2052
[2009-06-04 17:08:51 14342] DEBUG (XendDomainInfo:590) XendDomainInfo.destroyDevice: deviceClass = vbd, device = vbd/2052
[2009-06-04 17:08:51 14342] DEBUG (XendDomainInfo:1593) Removing console/0
[2009-06-04 17:08:51 14342] DEBUG (XendDomainInfo:590) XendDomainInfo.destroyDevice: deviceClass = console, device = consol
[2009-06-04 17:08:52 14342] DEBUG (XendDomainInfo:1585) No device model
[2009-06-04 17:08:52 14342] DEBUG (XendDomainInfo:1587) Releasing devices


Thanks in advance,
Prema

---

