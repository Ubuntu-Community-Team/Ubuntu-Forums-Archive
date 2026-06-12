---
title: "vmware not detecting palm on usb (Ubuntu 6.10)"
date: 2006-11-07
forum: Desktop Environments
---

### Post by GorBo on 2006-11-07
Has anyone managed to get USB working on VMware (guest OS WinXP) after the upgrade to Ubuntu 6.10? Previous solution (worked under 6.06) was to:

[LIST=1]
[*]put '[FONT="Courier New"]blacklist visor[/FONT]' in [FONT="Courier New"]/etc/modprobe.d/blacklist-visor[/FONT]
[*]add [FONT="Courier New"]usb.generic.skipSetConfig = "TRUE"[/FONT] to .vmx file of the virtual machine
[/LIST]

After the upgrade to 6.10 I had to (of course) reinstall VMware Server. The settings are all the same, but nothing happens when I press Hotsync (the guest OS doesn't detect the USB device).

Has anyone figured this out? Thanks in advance.

---

### Post by hartungu on 2006-11-09
Try to enter this command in a terminal:

sudo mount -t usbfs none /proc/bus/usb 

Restart your virtual machine. When it us up,  enter the full-screen mode. Then connect your usb-device. You should now have the usb connection.

If this worked for you, add the following line to your /etc/fstab:
usbfs  /proc/bus/usb  usbfs  auto  0  0

---

### Post by GorBo on 2006-11-09
Yes! My Palm now hotsyncs in vmware. Many thanks for this, hartungu. You just made my life in the office a lot easier.

---

### Post by Blixter on 2006-11-14
> Is it possible to install a usb printer (canon PIXMA5200) to?? ](*,)

With vmware 6 Beta works USB 2.0 printers :)

---

### Post by jasnix on 2006-11-21
Hello,
I tried following the instructions here and mounting /proc/bus/usb

However I am not able to get USB working with vmware server. I am using Ubuntu Edgy for the host and running Windows XP as a client.  I mounted /proc/bus/usb then restarted Windows, went into full screen mode and when I plug in my cingular 8125 it can't detect it.  This is the case with any USB device, jump drive, iPod etc..   

Also,
When I go into device manager in windows, I don't see any USB controllers.  In vmware when I go to VM > Settings, there isn't any USB options either.

I'm not sure what to try next.  Not sure if this helps but here is the files in my /proc/bus/usb directory.

$ ls /proc/bus/usb/
001/  002/  003/  devices@

Please help me out.. I really don't want to dual-boot windows for this.

Thanks!!

---

### Post by xkenneth on 2006-11-28
I'm having the same problem, anyone?

As you can see it it's mounted.

usbfs and procbusn, could these be conflicting?

/dev/sdc2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.17-10-386/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sdb5 on /media/sdb5 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sdc2 on /media/sdc2 type ext3 (rw)
/dev/sdc5 on /media/LinuxShare type vfat (rw,umask=0000)
usbfs on /proc/bus/usb type usbfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

I'm not sure what to do here, I really need USB support in VMWare server with UBUNTU as the host OS.

---

### Post by xkenneth on 2006-11-28
Just marking as high priority, which it is. :D

---

### Post by GorBo on 2006-11-29
Maybe the host OS grabs the device before the guest OS has a chance? When you plug in the device, check /var/log/messages to see if there's a log showing that Ubuntu recognised it. Than add that device to the black list (see the start of this discussion). You also have to add one line to the .vmx file of the virtual machine (see the first post). If you did all that, check also if the device shows up of the "VM -> Removable Devices -> USB Devices" list in the VMware menu and enable it.

That's as far as my knowledge on this topic goes, I'm afraid.

---

### Post by hawko on 2006-11-29
Was having a similar problem with my Pocket PC and found this at the VMWare website
> Adding a USB Controller
The USB controller is disabled by default in all virtual machines created with VMware Server.To add a USB controller to the virtual machine’s configuration, complete the following steps with the virtual machine powered off. Use the VMware Server Console to add the device.

Don't know if it helps you, but it sorted my probs.  USB devices appeared (only 2 at a time though).

---

### Post by RChickenMan on 2006-12-02
Hey, this thread helped me a lot, thanks.  One thing I wasn't able to test was if this will allow me to use USB devices that don't work in Linux in fake Windows.  I never thought I would call this a "problem", but every USB device I own works flawlessly in Ubuntu so I can't test for myself!

---

### Post by chrisharris0 on 2007-01-04
Thanks allot! mounting /proc/bus/usb worked great for me too.

Running ubuntu 6.10 with windows xp as guest VMware workstation 5.3 and using an ipod nano :) :)

---

### Post by StarkD on 2007-01-25
I runned the > sudo mount -t usbfs none /proc/bus/usb
and now Windows XP recognizes my Palm but I get the following error message:
> The specified device appears to be claimed by another driver (visor) on the host operating system which means that the device may be in use. To continue, the device will first be disconnected from its current driver.
> The existing driver (visor) could not be successfully disconnected. (Operation not permitted)
Unload the driver manually, then try again.
What should I do?

I'm using:
Ubuntu 6.10 Edgy Eft
VMWare Workstation 5.5.3 build-34685
Microsoft Windows XP SP2 as guest

---

### Post by GorBo on 2007-01-25
You have to tell Ubuntu not to try and load modules for this device. Do this by issuing a command:

sudo echo 'blacklist visor' > /etc/modprobe.d/blacklist-visor

If it's still not working, add:

usb.generic.skipSetConfig = "TRUE"

at the end of the .vmx file of the virtual machine.

---

### Post by StarkD on 2007-01-25
running
> sudo echo 'blacklist visor' > /etcmodprobe.d/blacklist-visor
resulted in
> bash: /etcmodprobe.d/blacklist-visor: No such file or directory

and after adding
> usb.generic.skipSetConfig = "TRUE"
at the end of the .vmx file of the virtual machine.
I don't get any error messages but nothing happens. What now?

edit:
after rebooting and running > sudo mount -t usbfs none /proc/bus/usb again I get the same error messages I had from the beginning. Can I uninstall visor or something instead?

---

### Post by StarkD on 2007-02-02
I spotted the misspelling by GorBo and added the "blacklist visor" line using a text editor.

I also added the "usbfs /proc/bus/usb usbfs auto 0 0" in my /etc/fstab

Now my Palm TX is detected:
[IMG]http://www.microansa.com/vmware_palm_dump.png[/IMG]

But nothing happens when I push the sync button...

Now what?

---

### Post by jimyoung1 on 2007-02-10
I am having similar problems with my Palm TX.
I was able to sync my Palm TX with this VM in Kubuntu Dapper and VMware Server as long as I  dumped the visor module with 'modprobe -r visor' and had 

usb.present = "TRUE"
usb.generic.autoconnect = "TRUE"
usb.generic.skipsetconfig = "TRUE"

in the .vmx file. I have been unable to sync since upgrading to Edgy 6.10 

I added "blacklist visor" to "/etc/modprobe.d/blacklist" to avoid having to dump the visor module manually each time. Thanks for the suggestion by the way.

Runing 'mount -t usbfs none /proc/bus/usb' as root worked for me so I added 'usbfs /proc/bus/usb usbfs auto 0 0' to fstab.
Now my Windows XP guest OS will find the palm and display it in "VM -> Removable Devices -> USB Devices" list in the VMware menu. 

The problems now start when I press the hotsync button.
The kernel writes to /var/log/messages:

Feb 10 11:22:40 amd3000 kernel: [17311863.232000] usb 1-4: USB disconnect, address 44
Feb 10 11:22:41 amd3000 kernel: [17311863.656000] ohci_hcd 0000:00:02.0: wakeup
Feb 10 11:22:41 amd3000 kernel: [17311864.040000] usb 1-4: new full speed USB device using ohci_hcd and address 45
Feb 10 11:22:42 amd3000 kernel: [17311864.256000] usb 1-4: configuration #1 chosen from 1 choice

Apparently Kubuntu is seeing the hotsync as a disconnect and with the above changes it is now remounting the Palm TX as a new device in sync mode? I presume it should pass the hotsync button "push" to the guest and not remount the device.

Looking at the "VM -> Removable Devices -> USB Devices" in the VMware console the Palm TX is displayed "Palm, Inc Palm Handheld (Port 1)". With the hotsync button push the Palm TX disappears from the "USB Devices" menu and is found and displayed once again when the Palm is remounted by Kubuntu.

Where do I go from here?

I'm using:
Kubuntu 6.10 Edgy Eft, kernel 2.6.17-10-386 as Host
VMware Server 1.0.1 build-29996
Microsoft Windows XP SP2 as guest

---

### Post by Robor on 2007-02-14
> **GorBo said:**
> Has anyone managed to get USB working on VMware (guest OS WinXP) after the upgrade to Ubuntu 6.10? Previous solution (worked under 6.06) was to:

add **usb.generic.skipSetConfig = "TRUE"** to .vmx file of the virtual machine.

Thank you!!!  I've been trying to get my USB thumbdrive recognized by my WinXP Pro virtual machine in VMWare Server 1.01.  That solved it.

---

### Post by kljsdfuiowerm,help on 2007-02-18
Didn't help me at all.

I got the Vmware server running and have the Usb enable and I still can not get my ipod to work any suggestions? Thanks, bye for now.

---

### Post by hua on 2007-11-21
Hey Guys,

Not sure whether you have solved your palm sync problem. Here is my experience.

vmware server 1.04
Host OS: Ubuntu 7.10
Guest OS: Windows XP
Palm desktop: 4.14
my device: Palm M500
my problem: Palm doesn't sync(intermittent)
root cause: vmware doesn't seem recognize Palm device quick enough

Here is my solution
1. mount usbfs properly (there is plenty of guide on this)
2. make sure visor module unloaded
3. add usb.generic.skipsetconfig = "TRUE" to your .vmx file
4. connect Palm to usb port, my M500 is connected via USB cradle
5. before start hotsync, plugin any usb device, e.g. memory stick, usb mouse, etc
6. start hotsync by either press the button on cradle or click hotsync icon
7. now quickly unplug the usb device in step5
8. quickly go to menu vm->removable devices->usb devices, and tick your palm device
9. repeat step4-step8, whenever you want to sync your palm.

The idea above is to trigger vmware refresh its usb device list by physical unplug a usb device. It works pretty well for me.

---

### Post by sanitycheck on 2008-01-11
SYSTEM: 
AMD64 box running 32-bit Gutsy Kubuntu and VMWare Workstation 6.02.

SOLUTION:
I also had problems with a Palm Z22 connecting to a WinXP Home VM.  I did the blacklist trick to suppress the Visor driver message.  That worked to suppress the message, but didn't help find the Palm or a flash drive more reliably.

I've made a lot of changes recently, but one of them was to upgrade from Workstation 5 to Workstation 6.  Workstation 6 has support for USB2, which was turned on by default for this VM (this XP Home VM was created on this system and on Workstation 6).  Turning USB2 support OFF in the VM manager seems to be the magic fix.

Gutsy is not officially supported on Workstation 6, although everything else seemed to work fine until I ran into this problem.  Workstation 6 and the USB2 support is relatively new, so it looks like VMWare still has some issues to sort out.

This probably isn't a solution for VMWare Server, as I think the 1.x versions of Server only support Workstation 5 level VMs.  This means they won't have USB2 support to turn off.

---

### Post by djbon2112 on 2008-03-11
> **hartungu said:**
> Try to enter this command in a terminal:

sudo mount -t usbfs none /proc/bus/usb 

Restart your virtual machine. When it us up,  enter the full-screen mode. Then connect your usb-device. You should now have the usb connection.

If this worked for you, add the following line to your /etc/fstab:
usbfs  /proc/bus/usb  usbfs  auto  0  0

Hey guys, sorry for the bump. I've got a Moto Q connected via USB, running VMWare Workstation 6 (Windows XP) on Gutsy Gibbon (7.10). Before, I'd go to connect the Q through the VM -> Removable Devices menu, and it would connect for a second then disappear until I rebooted my computer. After searching, I found this and tried it. Now, instead of connecting and disappearing, it continuously connects and disconnects in quick succession until I disable or disconnect the Q (It's also disappearing and reappearing in the VM -> Removable Devices menu). Anyone have any suggestions?

---

