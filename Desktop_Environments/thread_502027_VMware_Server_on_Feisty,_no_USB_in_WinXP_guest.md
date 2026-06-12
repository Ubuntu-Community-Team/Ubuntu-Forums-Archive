---
title: "VMware Server on Feisty, no USB in WinXP guest"
date: 2007-07-16
forum: Desktop Environments
---

### Post by SirOracle on 2007-07-16
Hi
I'm using Ubuntu Feisty as host OS, with VMware Server 1.0.3. And I have a Windows XP guest OS.

I have a problem using my USB memory stick in the guest OS. It comes up automatically in the host, but the guest don't see it.

VM -> Removable Devices -> USB Devices just says Empty.

I've found some other posts about this problem on earlier versions of Ubuntu:
[http://ubuntuforums.org/showthread.php?t=309020](http://ubuntuforums.org/showthread.php?t=309020)
[http://www.vmware.com/community/thread.jspa?threadID=66096&tstart=0](http://www.vmware.com/community/thread.jspa?threadID=66096&tstart=0)
[http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&externalId=3862823](http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&externalId=3862823)

I've tried the fix in the last link, VMware KB article, I've tried to plug in two USB devices and I've tried to restart the guest while the USB stick is mounted, but nothing :(

Is this a common problem with Feisty and VMware Server 1.0.3 or is it just me?

---

### Post by murderface on 2007-07-17
Did you unmount the device from the host first?

---

### Post by xarmian on 2007-07-17
You have to make sure you add the device to your virtual machine.. With the virtual machine powered down, select the settings for the VM (which shows a Hardware and Options tab) and under hardware select "Add" and then select USB Controller, and follow the menus to add the USB controller..

Then power up your virtual machine and select VM->Removable Devices->USB Devices and your USB device will be listed.. select the USB device to enable it on your VM, and Windows will detect it in the same way it does when you plug it in, and will install the drivers..

-Dave

EDIT: Some added side notes.. Make sure you insert the USB drive then unmount it before powering on your VM guest (you can resume it from a supended state too, it doesn't need to have been completely shut down)

---

### Post by SirOracle on 2007-07-18
Ohh, you have to add an USB controller, I didn't think of that, I thought it was there by default. Thanks for the tip :)

But a tip back, is that if you add this line:
```
usbfs  /proc/bus/usb  usbfs  auto  0  0
```
to your /etc/fstab file, you won't have to restart your guest to make it find the USB device. Just plug it in, and it's there. (from this link: [http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&externalId=3862823](http://kb.vmware.com/selfservice/microsites/search.do?cmd=displayKC&externalId=3862823)).

I only got USB 1.1 ports though, are there really no USB 2.0 support in VMware Server? I use the memory stick to move large files to computers on another network. So if there is only USB 1.1 support I will have to find another way :(

---

### Post by xarmian on 2007-07-18
Thanks for the tip.. Yeah it's true there's only USB 1.1 support in vmware server/player.. They reserved USB 2.0 for the workstation (which still costs cash)..

One way around it would be to mount the USB drive into ubuntu and set it up as a Samba share (easy to do) then Map the drive in the Windows XP VM so you can link it to any drive letter.. I actually set up my Ubuntu home directory that way.. I don't know exactly how fast it is though.. If you're looking for any specific instructions let me know and I'm sure I can make them up..

-Dave

---

### Post by veloce on 2007-07-18
> **xarmian said:**
> Thanks for the tip.. Yeah it's true there's only USB 1.1 support in vmware server/player.. They reserved USB 2.0 for the workstation (which still costs cash)..

One way around it would be to mount the USB drive into ubuntu and set it up as a Samba share (easy to do) then Map the drive in the Windows XP VM so you can link it to any drive letter.. I actually set up my Ubuntu home directory that way.. I don't know exactly how fast it is though.. If you're looking for any specific instructions let me know and I'm sure I can make them up..

-Dave

In answer to how fast using the samba share is, if you are using host only networking between host and vm then it is mimicking gigabit ethernet.  If it's going through bridged networking then it can be incredibly slow.

---

### Post by xarmian on 2007-07-18
> **veloce said:**
> In answer to how fast using the samba share is, if you are using host only networking between host and vm then it is mimicking gigabit ethernet.  If it's going through bridged networking then it can be incredibly slow.

I'm using NAT, which I would think works similarly to host-only.. theoretically.

-Dave

---

### Post by allforcarrie on 2007-08-18
i have hte same problem, i cant acces my usb devices and i cant get to them threw a virtual network either.

---

