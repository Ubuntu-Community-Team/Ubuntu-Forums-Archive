---
title: "VMware + Edgy + No USB"
date: 2006-11-29
forum: Desktop Environments
---

### Post by xkenneth on 2006-11-29
Hi,


    So i'm running edgy, 6.10 and I've installed VMWare Server here and have Windows XP running as the guest OS. Everything is fine and dandy and smooth except for my inability to have VMWare pick up on usb devices. I'm sure that /proc/bus/usb is mounted, and after that I'm not sure what else to do. I can see the devices I plug in by using the lspci command but I can't seem to get the USB Devices menu to populate under VMWare. When I use the Device Manager under the windows guest OS i can't see any USB controllers, nor under the VM setup menus can I modify or add a usb controller. Has anyone else experienced this? I would really like for this to be fixed quickly.

Regards,
Ken

BTW if this is not the proper forum please help me redirect it.

---

### Post by drr422 on 2006-11-29
I ran into the exact same problem, and I was never able to fix it.  This was a few weeks ago, so i just switched back to dapper.  I'm gonna go search to see if anything new came up about how to fix it.

---

### Post by drr422 on 2006-11-29
Just to clarify things, I already had usb support in dapper, but when i installed vmware server in Edgy, there was no usb support, even though the usb controller was enabled.  When a usb drive is connected to the computer, normally there is an option under the tools menu i believe to enable the usb drive for the virtual machine, But in Edgy, this does not appear.  Any help will be appreciated
Thanks again

---

### Post by Mike'sHardLinux on 2006-11-30
I have VMware Server working fine with all my USB stuff in Edgy. It sees my printer, scanner, memory card reader, gamepad, and usb drive, and I can use them all, too.

What version of VMWare Server are you running? I am on 1.0.1 build-29996. As far as I know, it's the latest.

my kernel:
```
rjguerrero@ubuntu1:~$ uname -a
Linux ubuntu1 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux

```

This may seem like a dumb question, but did you install VMware tools in the guest OS? I really don't even think that is necessary, but just considering all the possibilities.

Oh, I did a clean install of Edgy, not an upgrade. I'm not sure where else to look.

---

### Post by LLRNR on 2006-11-30
I also have XP "jailed" in VMware **evil grin**

As a quick note, it's best to install the VMware Tools too, they'll speed up the guest OS. To do this, be **SURE** that your guest OS is running and go to the VM menu -> Install VMware Tools. It should boost up your guest OS...

To enable USB support, you first need to **add** an USB controller to your virtual machine, since it doesn't have it by default. For this:

**a)** be sure your virtual machine is *turned off* 

**b)** go to Edit virtual machine settings -> Hardware tab -> Add... -> USB Controller -> Next -> Finish -> OK

**c)** turn on your virtual machine

**d)** VM menu -> Removable Devices -> select the USB controller in order to have it active.

If everything goes well, the guest OS **should** see whatever you attached to your USB port.

HTH,

LLRNR

---

### Post by drr422 on 2006-12-01
Yes, I'm running the same version that you are, and i have the VMware tools installed as well since they do make it a lot faster. 

 I'll give it another try tonight though, since it has been about two weeks since my last attempt.  I like to keep the xp jailed in vmware as well, cause I don't like nasty things doing things i dont know about on my computer.

  well, im going to go install it, thanks for your help though, and ill let you know how it goes.

---

### Post by drr422 on 2006-12-01
well, i tried it out and it still didn't work, I'll retry it in a few weeks with a fresh edgy install.  Thanks for the help though.

---

### Post by Mike'sHardLinux on 2006-12-01
Is your USB hardware working fine in Edgy? I have to ask because you really didn't say. Can you tell us the specs of your motherboard (at least the make and model #). Maybe there is a bug related to your hardware.

Also, I assume you're running regular Ubuntu (Gnome)? Any special things you've installed other than the norm? special drivers or anything not from the repos....

List all your USB hardware: usb hubs, scanners, printers, whatever.....

One thing to try is to disconnect all but 1 usb device, and see if you can get that working. This includes disconnecting internal usb devices.

---

### Post by drr422 on 2006-12-01
My usb hardware works fine in edgy, which include usb drives and a usb mouse.  The usb mouse works fine in VMware as well. The only problem arises when i try to connect a usb drive and try to get it reconginzed in VMware.  In dapper, it worked by me connecting the usb drive, then loading it in the vmware session.  

I don't have anything else connected through VMware though.  I'm running the default Ubuntu with Metacity as my window manager, and i have 'fglrx' loaded and working perfectly.  This is all on a Dell Inspiron 6000 laptop, with 2 GB of ram, 60 GB hard drive, and a ATI x300 with 128 MB of ram, loaded with the fglrx driver which i don't think is the cause of this problem.  

I'm thinking I will do a fresh installation, update, and try again.  For some reason i enjoy reinstalling, cause i cataloged all the necessary changes i need to make, so i just make them.  I'll make a script one day that will automate it all, and that will be fun.

---

### Post by LLRNR on 2006-12-01
> **drr422 said:**
> I'm thinking I will do a fresh installation, update, and try again.  For some reason i enjoy reinstalling, cause i cataloged all the necessary changes i need to make, so i just make them.  I'll make a script one day that will automate it all, and that will be fun.

I'm sorry, I forgot to mention, I'm on a clean Edgy install and it's working ok... don't know if that's the problem though. I _still_ can't figure why certain things tend to work better on clean installs (I guess I'll have to do a couple more to finally get that, LOL). Well if you "enjoy reinstalling" as you say, it's worth a try, anyway... Just my 2 cents :)

LLRNR

---

### Post by peterx14 on 2006-12-08
Well I'm having problems with my USB scanner under a clean Edgy install, but I had hgoped it would work fine under VMWare (Workstation 5.5.3? -- the current version anyway!).

To cut a long one short, added the USB controller to VMware, booted up (Windows 2000), it detected the USB controller fine but when I subsequently plug in the scanner it didn't see it. I had a dig around in Windows device manager and there was nothing there either. So I wondered if my USB flash drive would work; I plugged that in, and *then* my scanner gets detected!

HTH! :)

---

### Post by drr422 on 2006-12-09
yeah, the same kind of thing ended up working for me.  if i want to look at a flashdrive, then i plug in the flashdrive, then plug in something else, usually another flash drive, and then the first flash drive will work.  quite strange, but hey, it works.

---

### Post by nada.cascadia on 2006-12-19
I am running VMWare Server with a Windows XP SP2 Guest OS inside of Edgy.  Within the Windows Guest, my USB devices were also not recognized when plugged in.  

Based on the previous post's suggestion, these are the steps I took:

1.  With the Guest OS running, I plugged in TWO USB devices, and Edgy recognized both. 
2. Then, in the VMWare Server Console, I clicked on the "VM" item on the Menu, and then on "Removable Devices > USB Devices" and clicked my USB key. 
3. Then Windows in the Guest OS recognized the new hardware and I am set!

Thanks for the help.

---

### Post by CrippledCanary on 2006-12-20
I think there is some trouble when vmware detects USB devices after the virtual machine is started.

For example.
If I connect my USB drive to my computer (running edgy) and then starts the guest, then vmware is able to use it. But if I start the guest and THEN connects my USB drive it's not able to use it. Not even seen on "VM->Removeable Devices-> USB Devices"

---

### Post by pdg777 on 2006-12-21
Hi, I can confirm the same issue - usb devices are not seen in the vm guest when they are plugged into the hardware.

I am running edgy with VM Workstation.  When I plug in my blackberry it would not show up in the VM guest, even when the guest settings are ticked to automatically connect usb devices when it has focus.  

Though i did have to add some entries in my vmx file to enable using the Blackbery in the vm guest (see other posts about this) i do not think it contributed to the problem.  

When the Blackberry is plugged in, it is not seen by the Windows xp guest, or even available in vm --> removable devices --> usb.  following the instructions in the above post, I then installed a usb flash key.  It showed up in edgy 1st, so I ejected (dismounted) it, and then the Blackberry was visable in the vm --> removable devices --> usb devices.  

Very strange, maybe a fix for this one day.  till then it looks like a training issue...:-k

---

### Post by dashnak on 2006-12-24
Yep, having the exact same problem. Tremendously annoying, can't print, or use my gamepad , hell, even my flash drives....

---

### Post by drr422 on 2006-12-24
yeah, i think i will drop vmware all together and just keep a windows partition on the side.  I was able to shrink down my windows with all the necessary programs i need sometimes down to 2.2 gb, so i have it in a 3 gb partition.

---

### Post by srafx on 2006-12-30
I'm having a similar problem:

[http://www.vmware.com/community/thread.jspa?threadID=66096&tstart=0](http://www.vmware.com/community/thread.jspa?threadID=66096&tstart=0)

Take a look at this post, I would much rather you post you thoughts in this forum then theirs, just because this seems more to be a linux problem and second, we are nicer people :)

---

### Post by glabouni on 2007-01-27
> **peterx14 said:**
> Well I'm having problems with my USB scanner under a clean Edgy install, but I had hgoped it would work fine under VMWare (Workstation 5.5.3? -- the current version anyway!).

To cut a long one short, added the USB controller to VMware, booted up (Windows 2000), it detected the USB controller fine but when I subsequently plug in the scanner it didn't see it. I had a dig around in Windows device manager and there was nothing there either. So I wondered if my USB flash drive would work; I plugged that in, and *then* my scanner gets detected!

HTH! :)

+1

I got the same problem. wondering if it is ubuntu related or vmware related.

Though when i plug the flash drive while focus in on vmware windows machine, the scanner shows up in vmware windows but the flash drive shows up in ubuntu.

---

### Post by drr422 on 2007-01-27
I think it is ubuntu related since vmware worked fine in dapper

---

### Post by d4rthpimp on 2007-03-02
I have a vmware server, host OS Ubuntu 6.10-server, with various guests including a Kubuntu 6.10 guest.  I can confirm that the usb controller option is not available unless the guest is restarted while the host has it mounted (/dev/sdb1 --> /media/usbflash).  Another confirmation for this forum is the plugging in of an additional usb device, like another flash drive, to the host brings the usb controller back to life and the Kubuntu guest sees the original flash drive that wasn't working properly in the first place!  So very wacky.  I am wondering if there is some kind of hardware foolery going on here?  I am using an Dell Optiplex GX 620 with the dual usb ports on the front of the toaster-like chassis.  Maybe it has to do with the non-virtual usb controller on my mobo?  Note the second usb flash drive is connected through a usb hub...

Host, LaCie flash drive and SanDisk connected through generic usb hub:
root@lucifer:~# lsusb
Bus 005 Device 008: ID 0781:5150 SanDisk Corp. SDCZ2 Cruzer Mini Flash Drive (thin)
Bus 005 Device 007: ID 05e3:0606 Genesys Logic, Inc.
Bus 005 Device 006: ID 04b4:6830 Cypress Semiconductor Corp. USB-2.0 IDE Adapter
Bus 005 Device 002: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 005 Device 003: ID 06f2:0011 Emine Technology Co.
Bus 005 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000

Guest, LaCie flash drive shows up, where is the SanDisk?:
root@fatboy:~# lsusb
Bus 001 Device 018: ID 04b4:6830 Cypress Semiconductor Corp. USB-2.0 IDE Adapter
Bus 005 Device 001: ID 0000:0000

Regards,
-d4rthpimp

---

### Post by drr422 on 2007-03-02
Yeah the same thing happened to me, i wonder if there is a command that we can run to refresh the usb controller for Vmware server so it can see it.  This is the only drawback that i can see about Edgy.  I wonder what changed from Dapper to Edgy to cause this problem with vmware?

---

### Post by valmarmoritz on 2007-03-08
I suggest You read this on VMNT (it worked for me, anyhow!):

[USB Devices Are Not Available on Some Linux hosts, the VM > Removable Devices > USB Devices Menu Is Empty]("http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=3862823&sliceId=SAL_Public&dialogID=12453375&stateId=0%200%2012449527&doctag=Author,%20KB%20Article")

In short, the problem was Ubuntu not mounting USBFS to /proc/bus/usb.

Solution:
sudo mount -t usbfs none /proc/bus/usb

and add the following line in the /etc/fstab file:
usbfs  /proc/bus/usb  usbfs  auto  0  0

V

---

### Post by woodgdo1 on 2007-03-12
Awesome!! I was waiting for this solution for a while...

---

### Post by Jose Catre-Vandis on 2007-03-27
This is fine, and provides a connection, but generates an unsafe device removal message. in dapper vmware seems happy to do the switch without causing this. Any way round upsetting edgy?

---

### Post by Psyklops on 2007-09-06
> **valmarmoritz said:**
> I suggest You read this on VMNT (it worked for me, anyhow!):

[USB Devices Are Not Available on Some Linux hosts, the VM > Removable Devices > USB Devices Menu Is Empty]("http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=3862823&sliceId=SAL_Public&dialogID=12453375&stateId=0%200%2012449527&doctag=Author,%20KB%20Article")

In short, the problem was Ubuntu not mounting USBFS to /proc/bus/usb.

Solution:
sudo mount -t usbfs none /proc/bus/usb

and add the following line in the /etc/fstab file:
usbfs  /proc/bus/usb  usbfs  auto  0  0

V

quick thanks to say that this worked perfectly for me too :)

---

### Post by smiki on 2007-10-18
ubuntu 7.10 gutsy has the same problem with the usb detection in vmware server 1.0.4

and the solution above works for gutsy too

---

### Post by d_xtremw on 2007-10-19
yeah im running into the same problem with feisty and vmware server 1.0.4, i got the sound working but the usb is still giving me trouble. im trying to hook up a webcam and its not working. does the device u use have to be supported by the host OS or can it be for the guest OS only?

---

### Post by d_xtremw on 2007-10-19
ok scratch that... using the 2 usb device installation method (lol i might have jus coined a new phrase) i  managed to work it work. it was a bit tricky and it means im always going to need a 2nd usb device but.. i guess if it works.... i cant really object

thanks everyone for this solution

---

### Post by strakarpickup on 2007-10-25
Hi!

I'm using kubuntu 7.10 as host and winxp as guest.
I had the same problem but now with the mount command I can see the devices in VMware (thanks for that solution). But I still can't connect my blackberry. Windows starts the driver installation and says complete. But right after that I receive an error on VMware saying " File not found" and on windows " USB Device Not recognized ".

Anyone having the same problem or have any idea why?

Regards

---

### Post by strakarpickup on 2007-10-25
I also get this on vmware log :
Oct 25 17:56:55: app| VM suddenly changed state: poweredOn.
Oct 25 17:56:55: app| cleanup: cleaned up 2 objects
Oct 25 17:57:03: app| VM suddenly changed state: poweredOn.


help!!!!!!!!!

---

### Post by aatiis on 2007-12-11
> **valmarmoritz said:**
> I suggest You read this on VMNT (it worked for me, anyhow!):

[USB Devices Are Not Available on Some Linux hosts, the VM > Removable Devices > USB Devices Menu Is Empty]("http://kb.vmware.com/vmtnkb/search.do?cmd=displayKC&docType=kc&externalId=3862823&sliceId=SAL_Public&dialogID=12453375&stateId=0%200%2012449527&doctag=Author,%20KB%20Article")

In short, the problem was Ubuntu not mounting USBFS to /proc/bus/usb.

Solution:
sudo mount -t usbfs none /proc/bus/usb

and add the following line in the /etc/fstab file:
usbfs  /proc/bus/usb  usbfs  auto  0  0

V
I can't tell you how thankful I am. It's 06:06, I spent a whole night looking for this line.

---

### Post by davidshere on 2008-04-29
> **valmarmoritz said:**
> 
Solution:
sudo mount -t usbfs none /proc/bus/usb
and add the following line in the /etc/fstab file:
usbfs  /proc/bus/usb  usbfs  auto  0  0
This solution worked for me, but I had to reset the guest machine also.  I'm trying to connect a UPS.

EDIT: UPS connection successful.  I have an APC 350 and the control software only runs on windows... and as I suspected, I need a new battery.

---

