---
title: "VirtualBox USB problems"
date: 2007-01-19
forum: Desktop Environments
---

### Post by ramjet_1953 on 2007-01-19
Hi, Guys!

I have installed Innotek's VirtualBox and almost evrything went well, except there is a problem with USB devices.

I installed a Windows XP desktop and it doesn't see either my HP psc1350 all-in-one printer, or my Logitech QuickCam for Notebooks Pro webcam.

However, it saw my USB mouse straight-up.

I think it may be a permissions thing.

I have gone into System>Administration>Users & Groups and checked both myself and root in vboxusers.

I also created a group called usb and included both myself and root in that group.

I went through the usual thing in windows and loaded-up the software and drivers for the hardware and then, when prompted, plugged the devices in, but to no avail.

Any suggestions?

Regards,
Roger 8)

---

### Post by ramjet_1953 on 2007-01-19
Whoop! Got it!

It took a bit of digging, but I finally cracked it!

1. Create a group usbusers and put yourself in it. (System>Administration>Users & Groups>Manage Groups>Add Groups)

2. In a terminal, type in lsub and note down the vendor and id numbers for the USB devices that you want to enable. In my case, for the HP printer, it was 03f0:3611 and for the Logitech QuickCam, it was 046d:0861.

3. In VirtuaBox's USB section add both of these devices, making sure you have the vendor and id numbers correct.

4. As a super user, edit the properties of the file  /etc/udev, so that you can read and write to the file.

5. To be sure, re-boot and enjoy!

This software rocks!

Regards,
Roger 8)

---

### Post by kaede on 2007-01-25
can you access your harddrive file? i mean since we're installing our OS in virtual drive. is it possible?

---

### Post by kilou on 2007-01-25
what do you mean by vendor id and number id??? When I type lsusb I get different columns (Bus, Device, ID and a denomination). Which one is vendor and which one is number ID???

When I enter the ID in the product ID box, I get an error message...

Thanks

---

### Post by dannyboy79 on 2007-01-25
Vendor (Could be Device I think) for example is Hp Printer and the ID is 03f0:3611. Now do you get it?

---

### Post by kilou on 2007-01-25
When I do lsusb for my USB harddrive I get:

[COLOR="Red"]Bus 005 Device 005: ID 0930:6534 Toshiba Corp. [/COLOR]

So I enter 0930:6534 as product ID and Toshiba Corp. as vendor ID and I get:

[COLOR="Red"]Vendor ID filter string 'Toshiba Corp.' is not valid (error at position 5).
[/COLOR]

If I enter Toshiba Corp. as manufacturer I get:
[COLOR="Red"]
Product ID filter string '0930:6534' is not valid (error at position 5).[/COLOR]

Anyone knows what's going on?

---

### Post by neco on 2007-01-25
use

$ VBoxManage list usbhost

instead  

$ lsusb

and add the numbers inside the brackets

I still have the problem to give permissions to Virtualbox for my bluetooth device , that i fixed launching virtualbox as root

Saluts
Neco

---

### Post by kilou on 2007-01-26
Thanks :D

---

### Post by Stemp on 2007-01-26
Not working for me :(

> 4. As a super user, edit the properties of the file /etc/udev, so that you can read and write to the file.

What do you mean exactly by that ? Set the group usbusers to acces files ?

---

### Post by lcohen999 on 2007-01-29
yup, I am also stuck on step 4...

---

### Post by domino on 2007-01-30
The good folks on IRC pointed me to this section of the usr manual. thought some will find it useful.

Create group named "usbfs" and add yourself to the group.

> **9.4.6. USB not working**

If USB is not working on your Linux host, make sure that the current user has permission to access the USB filesystem (usbfs), which VirtualBox relies on to retrieve valid information about your host's USB devices.

The permissions for usbfs can be changed by editing the /etc/fstab file.

For example, most Linux distributions have a user group called usb or similar, of which the current user must be a member. To give all users of that group access to usbfs, make sure the following line is present:

# 85 is the USB group
none /proc/bus/usb usbfs devgid=85,devmode=664 0 0

Replace 85 with the group ID that matches your system (search /etc/group for "usb" or similar).

Alternatively, if you don't mind the security hole, give all users access to USB by changing "664" to "666".

cheers!

---

### Post by Stemp on 2007-01-30
Thanks a lot. USB is now working fine.

---

### Post by Moulton on 2007-01-31
Regarding the process of adding groups, or adding oneself as a member of a group...

In the good old days, one could just edit /etc/group by hand and that was good enough.

Now, there is an /etc/gshadow file, with group passwords.  Be sure you use kosher system tools for creating groups and adding members, so that the entries are updated in both /etc/group and /etc/gshadow.

Finally, logging into a group is not automatic.  You might have to log out and log back in before the system will recognize that you are now a member of a new group.  You can try using the 'newgrp' command to see if you can successfully gain authorization for a group other than your default group.

Worst comes to worst, rebooting the system is a sure-fire way to get newly defined components (like new kernel modules and new group IDs) fully recognized and activated.

If you really know what you are doing, you can do all this stuff w/o rebooting, but a simple reboot is often the easiest way to go.

---

### Post by nicnocquee on 2007-02-07
thanks a lot. it works finally. fiuuuh, :)

---

### Post by Nikos.Alexandris on 2007-02-08
Hi!

I run Ubuntu Edgy and I installed Windows XP Pro (Greek Version) SP2 within VirtualBox. I still didn't manage to get my usb devices to work(!).

1. I created a group named usbfs and added myself in it.

2. With "VBoxManage list usbhost" I got Vendor and Product IDs.

3. In VirtualBox Settings (USB section) I added the device filters (Vendor ID, Product ID and I tried with & without Revision numbers).

4. Then, based on the user manual, I added the following lines in /etc/fstab:
# usbfs is the USB group
none /proc/bus/usb usbfs devgid=usbfs,devmode=664 0 0
(and I tried also with devmode=666)

5. Reboot to be sure...

No USB devices under Virtual-Windows(!).

Any ideas? :confused: 

Thanks...

---

### Post by Medieval_Creations on 2007-02-08
Make sure the USB device is plugged in, but not mounted in Ubuntu.  I did that a couple of times, forget to umount the drive and VBox couldn't find it.

Also I don't know if "devgid=usbfs" will work or not.  I used the Group ID "1001" *in my case*.

Those are the only 2 things I can think of to double check if you've tried eveything else.

---

### Post by Nikos.Alexandris on 2007-02-10
Yep!

It worked...

My mistake was using the group **name** instead of group **[COLOR="Red"]ID[/COLOR]** !

Thanx a lot,

Nikos.

P.S. I think there is no more need for dual boot!

---

### Post by xxzeenoxx on 2007-02-23
Hey guys, all of you have been very helpful, and i'm up and running on XP and seeing my external HD.  I usually write myself short text files with step that work for my installs, so i hope this helps other people...

-Install XP or other OS

-Create a group called "usbfs" and add yourself to it.

-In terminal issue the following command:

	sudo gedit /etc/fstab

-In this file paste the following lines, and change the group ID according to the group ID that is shown for the group "usbfs".


# 1001 is the USB group ID
none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0


-Save and close file.


-In terminal, issue the following command:

	VBoxManage list usbhost

-Use the output of this command to set up the filters for USB devices under VirtualBox.

-Reboot


*USB DEVICES HAVE TO BE UNMOUNTED BEFORE VIRTUAL MACHINE CAN RECOGNIZE THEM*


...I hope this helps.


UPDATE: I've noticed that if you don't unmount or eject the external drive before booting the virtual machine, the virtual machine will take precedence over it, and eject it from ubuntu.  So, when the virtual machine is running i've had to just unplug the usb cord and plug it back in, and the virtual machine picks it up.

---

### Post by bob-aptllc on 2007-02-26
Thanks everybody for your posts! I am running Edgy with Win 2000 as a guest. At first, my USB flash drive was not recognized by the guest, but after going through the steps summarized in xxzeenoxx's post (Thank's for the great step-by-step!) the drive is now displayed in My Computer. 

Because other posts said that VirtualBox won't recognize my USB device if it is still mounted by Ubuntu, I right click on the device and "Eject" it before starting the guest, although it is still physically in the slot. When I start the guest, it displays the icon, but when I click on the icon, the perpetual hourglass appears and the guest is hung. If I start the guest, then plug the device into the slot, the device's light comes on, I click on the icon in "My Computer", then the device's light goes out and the hourglass appears until I close the app. Please help! :confused:

---

### Post by bob-aptllc on 2007-02-26
I just read that there is a difference between ejecting and dismounting the flash drive. So I used terminal to dismount the flash drive (it's light stayed on), but when I started my W2K guest VirtualBox still hung! Any helpful thoughts?

---

### Post by xxzeenoxx on 2007-02-26
> **bob-aptllc said:**
> I just read that there is a difference between ejecting and dismounting the flash drive. So I used terminal to dismount the flash drive (it's light stayed on), but when I started my W2K guest VirtualBox still hung! Any helpful thoughts?

I'd like to know if theres a different as well...i actually have been right clicking on the drive and ejecting it.

---

### Post by junwah on 2007-03-06
> **xxzeenoxx said:**
> Hey guys, all of you have been very helpful, and i'm up and running on XP and seeing my external HD.  I usually write myself short text files with step that work for my installs, so i hope this helps other people...

-Install XP or other OS

-Create a group called "usbfs" and add yourself to it.

-In terminal issue the following command:

	sudo gedit /etc/fstab

-In this file paste the following lines, and change the group ID according to the group ID that is shown for the group "usbfs".


# 1001 is the USB group ID
none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0


-Save and close file.


-In terminal, issue the following command:

	VBoxManage list usbhost

-Use the output of this command to set up the filters for USB devices under VirtualBox.

-Reboot


*USB DEVICES HAVE TO BE UNMOUNTED BEFORE VIRTUAL MACHINE CAN RECOGNIZE THEM*


...I hope this helps.


UPDATE: I've noticed that if you don't unmount or eject the external drive before booting the virtual machine, the virtual machine will take precedence over it, and eject it from ubuntu.  So, when the virtual machine is running i've had to just unplug the usb cord and plug it back in, and the virtual machine picks it up.


thanks for all of ur guidiance... i hv set it up step by step.. but still can't use usb pendrive.  in the virtualbox usb device setting, does we need to type the "port" number? and wat is remote?  choose no, yes, or any???
urgent///:confused:

---

### Post by nilium on 2007-03-13
This will do it for step 4:

```
sudo chmod -R 777 /etc/udev/
```

---

### Post by marx2k on 2007-03-16
I dont know folks, I've followed everything in this thread and VBox is still telling me that I need to check my usbfs options :(

---

### Post by marx2k on 2007-03-16
Scratch that, got it working... didnt have the correct GID in fstab - changed it to 1001 and it works now :D

---

### Post by bob-aptllc on 2007-03-20
Hi and please help.

I have followed the outline by xxzeenoxx earlier in this thread, but are still having problems. I have Edgy as the host and W2K as the guest. The guest recognizes my flash drive and printer, so I see the flash drive displayed as an icon/drive in My Computer, and the printer prints a test page. However, at that point the VM locks up! All I can do is shut it down. If you know how this might be fixed, please help me. Thanks!

---

### Post by bob-aptllc on 2007-03-26
Here is a good workaround for VirtualBox not recognizing USB drives and peripherals:  [http://www.virtualbox.org/discussion/1/449#-1](http://www.virtualbox.org/discussion/1/449#-1). This approach is to not use VirtualBox's filters to mount the USB in the guest, but to use SMB (Samba) in Linux to communicate the already mounted USB device to the (Windows) guest. I was very surprised at how easy it is to set up Samba in Ubuntu! Just right-click to share the folder and not much more. Please see the link for more. :)

---

### Post by WidowmakerPT on 2007-06-01
try this....
in terminal edit the following:
/etc/udev/rules.d/40-permissions.rules
and change the line for usb devices from 0664 into 0666

hope it helped

---

### Post by adam_r on 2007-07-19
i've tried EVERYTHING for 2 hours just to get my webcam working, unacceptable for a virtual machine, i'm back to vmware, get's them right away

---

### Post by Vadi on 2007-08-22
> **xxzeenoxx said:**
> Hey guys, all of you have been very helpful, and i'm up and running on XP and seeing my external HD.  I usually write myself short text files with step that work for my installs, so i hope this helps other people...

-Install XP or other OS

-Create a group called "usbfs" and add yourself to it.

-In terminal issue the following command:

	sudo gedit /etc/fstab

-In this file paste the following lines, and change the group ID according to the group ID that is shown for the group "usbfs".


# 1001 is the USB group ID
none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0


-Save and close file.


-In terminal, issue the following command:

	VBoxManage list usbhost

-Use the output of this command to set up the filters for USB devices under VirtualBox.

-Reboot


*USB DEVICES HAVE TO BE UNMOUNTED BEFORE VIRTUAL MACHINE CAN RECOGNIZE THEM*


...I hope this helps.


UPDATE: I've noticed that if you don't unmount or eject the external drive before booting the virtual machine, the virtual machine will take precedence over it, and eject it from ubuntu.  So, when the virtual machine is running i've had to just unplug the usb cord and plug it back in, and the virtual machine picks it up.

Woo, this works. Except I have to unmount the drive from ubuntu first, then go to devices - usb devices and check my usb disk, and then the virtual winxp detects it. Thanks a ton for this guide!

---

### Post by MarshallClan on 2007-09-02
Massive Thanks! 
 Huge thanks to all who posted hints! 
I got my Creative Vision M drive running under XP Guest and Ubuntu Studio Host. I think it is really great when a community comes together to help their peers!

---

### Post by mrf76 on 2007-09-05
Hi there!

Is there anybody with working U3 USB disk under Virtualbox? I have problem with Cruzer Sandisk U3 under the Virtualbox v1.5 with Windows XP SP2 as quest. "Normal" USB disk are working just fine. Here is  output from VBoxManage list usbhost:

UUID:               a1b127a3-a827-4c64-3f84-5d3c5ac1a43e
VendorId:           0x0781 (0781)
ProductId:          0x5406 (5406)
Revision:           0.16 (0016)
Manufacturer:       SanDisk Corporation
Product:            U3 Cruzer Micro
SerialNumber:       00000########
Address:            /proc/bus/usb/005/006
Current State:       Captured

After capture device with Virtualbox I see problem under Windows guest in Device Manager ->USB Mass Storage Device:

This device cannot start. (Code 10)


Thanks for advice.

PS: I'm not sure, maybe it's not problem with Ubuntu but Virtualbox and Windows.

---

### Post by Vadi on 2007-09-05
Is the usb drive mounted in Ubuntu? It shouldn't be.

---

### Post by ecmn on 2007-09-07
> **xxzeenoxx said:**
> Hey guys, all of you have been very helpful, and i'm up and running on XP and seeing my external HD.  I usually write myself short text files with step that work for my installs, so i hope this helps other people...

-Install XP or other OS

-Create a group called "usbfs" and add yourself to it.

-In terminal issue the following command:

	sudo gedit /etc/fstab

-In this file paste the following lines, and change the group ID according to the group ID that is shown for the group "usbfs".


# 1001 is the USB group ID
none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0


-Save and close file.


-In terminal, issue the following command:

	VBoxManage list usbhost

-Use the output of this command to set up the filters for USB devices under VirtualBox.

-Reboot


*USB DEVICES HAVE TO BE UNMOUNTED BEFORE VIRTUAL MACHINE CAN RECOGNIZE THEM*


...I hope this helps.


UPDATE: I've noticed that if you don't unmount or eject the external drive before booting the virtual machine, the virtual machine will take precedence over it, and eject it from ubuntu.  So, when the virtual machine is running i've had to just unplug the usb cord and plug it back in, and the virtual machine picks it up.

Thank you for this. IT WORKS!!! - Just follow.

---

### Post by CPImmanuel on 2007-09-12
I have not been successful with this yet. The question that I have on the procedure, is the following:

With reference to: 
VBoxManage list usbhost

-Use the output of this command to set up the filters for USB devices under VirtualBox.

The output of the command does not tell me what port to use. I used the same port 0100 that I chose and used when i set up my group, but that does not work. 
Also, do I have to use the latest version (1.5 of VirtualBox). If so, how do I install it ...when I try to install that package I get a screen about the PUEL but I have no way of typing or selecting OK....the screen appears to be frozen. Should I be downloading a different package? I downloaded the Virtual Box 1.5 for Ubuntu Fiesty which is what I am running..... 

The virtual box that I have installed and is working perfectly except for lack of USB is the version that I could get under add and remove programs....

Any help in these matters will be appreciated. 
Thanks.
Paul

---

### Post by Vadi on 2007-09-12
If you're installing virtualbox via the package editor thingy, you need to use the tab key a whole bunch to select it.

I installed it via the terminal, was somewhat easier.

Also, don't worry about setting the filter right. You can have it to match any usb device connected; I think you can just leave it all blank.

---

### Post by CPImmanuel on 2007-09-13
Thanks. 
That got me past the installing of the new version. 
Now however, my symptoms have changed. I cannot get the VirtualBox to see it --- at least not enough to make it selectable in the "USB Drives" drop down. The drive is shown, but it is grayed out. I was thinking that perhaps it was because the Host still had it mounted. So I tried to unmount the drive on the host, and it says that the device cannot be unmounted. Any ideas? 

I have checked "USers and Groups" and  I have the USBfs group and I have permission, 1001 is the group ID and I have the line "none /proc/bus/usb  usbfs devgid=1001, devmode=664 0 0 "

Any help will be appreciated. This and the inability of Ubuntu to print in color on the Konica Laser  Color printer are the only two reasons left for me not to migrate everything to a Ubuntu system. 

Regards, 

Paul Immanuel

---

### Post by CPImmanuel on 2007-09-13
Never mind... Please ignore the last post... I just found my problem... Clumsy me, I had devgid in the fstab file misspelled...I had spelled it as devguid. 
Now I can get the USB to work at least with an standard IDE attachment... Windows did not recognize my SATA drive for some reason, but that is a Windows problem...

Thanks.
Paul

---

### Post by Vadi on 2007-09-13
Glad you got it working.

Is the SATA recognized in Ubuntu? If yes, you could set up a shared folder for the whole sata drive.

Read the end-user documentation from the virtualbox site on how to set up a shared folder - they did an excellent job in a documentation.

---

### Post by hellibombelli on 2007-09-22
Thanx for all the hints in this thread, usb is now working in VirtualBox. :)

I want to improve the posted solution a little bit:
Dont make a new group called usbfs, simply use the group "plugdev", becaue of:
- this group exists by default and is the right group for access on plugable devices
- the first user is a member by default

So all I had to do was add the right line in /etc/fstab:
```
none  /proc/bus/usb  usbfs  devgid=46,devmode=664  0  0
```

46 is number of the group plugdev on my system. 
It was tested on gutsy with VB 1.5.0, but it also should work for feisty too IMHO.

Cheers,
hellibombelli

PS. Changing the udev permissions hadn't worked for me.

---

### Post by unholy1 on 2007-10-02
Hmm I'm running Fiesty and VirtualBox 1.5 and I still can't get my (4th gen) iPod to work in WinXP.

I've edited /etc/fstab and /etc/udev/rules.d/40-permissions.rules to no avail.

The iPod is recognised in Windows as a "Mass Storage Device", however it cannot start the device ("This device cannot start. (Code 10)"). :(

Anyone have any other ideas?

EDIT: I can't get my N95 connected via USB either. I get a message saying "PC Suite does not recognise the connected phone. The connection between the PC and the phone failed, error code 0x80044403"

Bah :(

---

### Post by Vadi on 2007-10-02
Try the virtualbox forums, the people there are quite helpful.

---

### Post by idkwot on 2007-10-02
hmm, i am having the same problem now :-X

---

### Post by unholy1 on 2007-10-07
Hmm.... I just noticed something.

I've added the following to /etc/fstab:

none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0


But I've noticed the following output from "mount -l":

```
unholy1@nixbox:/$ mount -l
/dev/sda1 on / type ext3 (rw,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
none on /proc/bus/usb type usbfs (rw,noexec,nosuid,nodev,devgid=1003,devmode=664)
```
How come /proc/bus/usb is mounted twice? It only appears once in the fstab file...

---

### Post by progman32 on 2007-10-11
Anyone have any update? I'm having the same problem...

---

### Post by jsully1 on 2007-10-22
Try setting devmode to 666 instead of 664 - this is my exact fstab entry:

#Entry for /dev/bus/usb
none    /proc/bus/usb   usbfs   devgid=1001,devmode=666 0 0

---

### Post by fabiomb on 2007-10-24
i used this solution:

[http://ubuntuforums.org/showthread.php?p=3625464#post3625464](http://ubuntuforums.org/showthread.php?p=3625464#post3625464)

and it worked fine:

Edit (as root) /etc/udev/rules.d/40-permissions.rules (I use vim, you can use nano, getid, or whatever)

Change this line :

SUBSYSTEM=="usb_device", MODE="0664"

To :

SUBSYSTEM=="usb_device", MODE="0666"

then:

sudo /etc/init.d/mountdevsubfs.sh stop

sudo /etc/init.d/mountdevsubfs.sh start

---

### Post by phil54601 on 2007-12-11
Hello;
Thanks,  The "$ VBoxManage list usbhost" proceedure worked for my second Memorex USB traveldrive.
THANK YOU

---

### Post by mikeyfbi on 2008-01-02
I think I've followed the instructions right from this thread, but when I start the virtualbox it 'steals' all of the usb's. I'm running ubuntu as the host, and xp as the virtual.

ie - as soon as the virtualbox loads it unmounts the external, stops the keyboard and mouse from working 

then it still doesn't recognize them in the virtual?

any ideas?

---

### Post by eidauk on 2008-01-21
After following this thread I still had a problem. Windows XP detected my USB Cruzer drive but would show that no files were on it and XP wouldn't let me interact (i.e. create folders) with the drive. I fixed it by unchecking the "Enable USB EHCI Controller" under the USB options in VBox. I'm now in VBox heaven!

---

### Post by ArtInvent on 2008-01-29
I have struggled with this for many hours. I just can't get my USB mp3 player or Cruzer or SD card reader to be usable in the XP guest. Devices show up as being captured in the VM but they just won't appear as an actual drive. Tear your hair out.  I now believe it's simply not possible due to a bug that hasn't been addressed, a conflict between Ubuntu and VirtualBox. Here is a ticket from from their website that's not that new but sure doesn't seem to have been resolved. 

**[http://www.virtualbox.org/ticket/574]("http://www.virtualbox.org/ticket/574")**

Wish I'd found a link to this about 8 hours ago. Sheesh. I was actually pretty impressed with VirtualBox until now. This just sucks.

---

### Post by seiffs on 2008-03-04
ok - i had the same problem - devices that cant be plugged by virtual box into the operating system somehow.
solution: 
# VBoxManage list usbhost

very important line at the device:
Current State:      Available
Current State:      Busy

if busy, than unload all modules that could cause the busy state

and the most important step for it:
every device has its 
Address:            /proc/bus/usb/003/003

so as root chmod 777 it.

# chmod 777 /proc/bus/usb/003/003
and start the virtual machine.

good luck

---

### Post by blue_bullet on 2008-03-17
Just thought I would add something here that may be obvious to everyone else.  I have tried everything to get VB to recognize my Seagate 750GB Ext HD.  My HD was formatted all ext3.  XP could not recognize it.  I used Gparted to format some of it, 98GB, FAT32.  Now XP sees the 98GB HD partition under VB.  Make certain some of your HD is formatted in a windoz approved format.  Thank you Billy.  I thought XP could read ext3- just could not write to it.  Everything else here worked for me.  And thanks for all the posts.  BTW Gparted option to format NTFS was greyed out so I just went with FAT32.  I have nfs-common and nfs-kernel-server installed but not nfsboot, nfsbooted, nor nfs-user-server.  Running Ubuntu 7.10, VB  1.5.6.  All I need now is to figure out how to get some sound working.  Great help on this forum.

---

### Post by rbrown3rd on 2008-04-04
I am running "Gutsy" and Vbox 1.56.  I have a WinXP guest machine and have been trying to get my Garmin USB Nuvi GPS to connect to the guest machine.  I followed all of the instructions here and have succeeded, sort of.  I am hoping someone can help me progress beyond the modest success I achieved.  

To connect I have to plug in my GPS prior to starting Vbox. When I connect a USB icon appears on my Kubuntu desktop. Then I start Vbox and the WinXP guest machine and after I open my account in WinXP the Kubuntu icon disappears indicating to me that my filter has worked.  I then have to click on Devices at the top of the Vbox guest XP window.  I select the GPS by checking the box next to the proper id for the device.  I then have to go to add new hardware in XP and when I do I find the device listed.  After selecting it I have access to the GPS with lGarmin software and Google Maps.  

Is there a way to automate this process?  Am I doing something wrong?  Thanks for any advice.

---

### Post by h4mx0r on 2008-04-07
There are drivers so windows can read and write to ext3, it isn't closed format like ntfs so its quite easy.

---

### Post by baya_agaa on 2008-04-28
I'm the another guy with usb problems. My PC is Iqon.I've istalled  Innotek VirtualBox on Hardy Heron.and my VB doesn't recognize my usb Webcam PCline 300k.Please help me and sorry for my English.I tried to change 664 to 666 on fstab but i got message permission denied you don't have sufficient privilegies etc.actually i'm the owner and user!Unknown device 093A:262A [0100] i guess this is my webcam.

 1-gedit /etc/udev/rules.d/40-permissions.rules

# USB serial converters
SUBSYSTEM=="usb_device", GOTO="usb_serial_start"
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", GOTO="usb_serial_start"
GOTO="usb_serial_end"
LABEL="usb_serial_start"
ATTRS{idVendor}=="0403", ATTRS{idProduct}=="6001
", \
					MODE="0666", GROUP="dialout"
LABEL="usb_serial_end"

2-sudo gedit /etc/init.d/mountdevsubfs.sh

#
	# Magic to make /proc/bus/usb work
	#
	mkdir -p /dev/bus/usb/.usbfs
	domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
	ln -s .usbfs/devices /dev/bus/usb/devices
	
         mount --rbind /dev/bus/usb /proc/bus/usb

---

### Post by crisnoh on 2008-05-16
Ok, this seems to be working fine until I enter  'VBoxManage list usbhost' which give me an output of <none>.  Any thoughts?

---

### Post by fang0654 on 2008-07-23
Fix for the Windows Mobile devices (Error Code 10):

Edit /etc/modprobe.d/blacklist and add the following:

rndis_host

This keeps Ubuntu from loading the networking driver when you plug in the device.  Tested on Hardy.

---

