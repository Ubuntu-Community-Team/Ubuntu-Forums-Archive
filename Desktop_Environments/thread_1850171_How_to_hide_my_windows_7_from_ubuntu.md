---
title: "How to hide my windows 7 from ubuntu ?"
date: 2011-09-25
forum: Desktop Environments
---

### Post by rishi_singh on 2011-09-25
I can see and edit my windows 7 partition from inside ubuntu linux 10.04. I want to hide it or make it inaccessible in ubuntu. The sole reason i use linux is to clean pendrive of malware before i use them in windows. So i dont want malware to be able to access the windows 7 or people using ubuntu in my laptop to accidentally put infected files there. I have wasted more than 10 hours on this problem and getting wifi to work on ubuntu. Nothing happened and i am looking for help.


PS :
I dont want to use this silly and needlessly complicated os for anything except that. I dont care what the security experts and the computer scientists say about linux. It is anything but convenient. Is this thing even getting popular or is it the exclusive preserve of people who love typing many commands to sound cool and nerdy ?

---

### Post by Copper Bezel on 2011-09-26
Hmm, for your use case, you probably don't really need a full Ubuntu install, then. Have you considered just using a LiveCD? Otherwise, you're dealing with the grub boot menu and lost disk space for no real benefit. 

As for access to your Windows partition, there's a yes-and-no to this. Windows doesn't use permissions in the filesystem in the same way that Linux filesystems do. However, you can edit the filesystem table to mount that volume read-only - see [_this guide_]("http://ubuntuforums.org/showthread.php?t=283131").

However, I don't know that it's necessary for your use here, and it means dinking around with a text file and using elevated permissions and things, which doesn't sound to be something you're interested in doing. There's little or no risk of malware on the Ubuntu side - none if you use the LiveCD - and the Windows partition won't be mounted until you yourself access it.

Edit: You might also look into using an Ubuntu virtual machine within Windows; no rebooting required and no access between Windows 7 and Ubuntu.

---

### Post by rishi_singh on 2011-09-26
> **Copper Bezel said:**
> Hmm, for your use case, you probably don't really need a full Ubuntu install, then. Have you considered just using a LiveCD? Otherwise, you're dealing with the grub boot menu and lost disk space for no real benefit. 

As for access to your Windows partition, there's a yes-and-no to this. Windows doesn't use permissions in the filesystem in the same way that Linux filesystems do. However, you can edit the filesystem table to mount that volume read-only - see [_this guide_]("http://ubuntuforums.org/showthread.php?t=283131").

However, I don't know that it's necessary for your use here, and it means dinking around with a text file and using elevated permissions and things, which doesn't sound to be something you're interested in doing. There's little or no risk of malware on the Ubuntu side - none if you use the LiveCD - and the Windows partition won't be mounted until you yourself access it.

Edit: You might also look into using an Ubuntu virtual machine within Windows; no rebooting required and no access between Windows 7 and Ubuntu.

Thanks. But the live cd is too slow. I wanted to instal ubuntu and learn about linux. I am learning it because i see so much blah blah about it regularly. Wanted to see if its really that good.
I have tried oracle virtualbox before. But using virtualization seems to be a risk for my purposes. When i put an infected pen drive into, say windows and open it in linux inside a VM, wont my windows get infected ?

Please let me know if there are any simple (gui based programs) ways to keep windows partition invisible inside ubuntu. Other people use my laptop too and I dont want them to accidentally put infected files into the windows 7.

---

### Post by Copper Bezel on 2011-09-26
Oh, good point - using a VM, the flash drive *would* be mounted by Windows first.

It looks like we're in luck - from the same guide, install and run the package pysdm by running these commands in a terminal:

```
sudo apt-get install pysdm

gksu pysdm
```

Since both of these are administrative tasks (thus the "sudo" and "gksu"), it'll ask for your password, but that should be all you need to do in the terminal.

Once you figure out which one is the Windows partition in the left-hand navigation pane, select it, click the "Assistant" button, and uncheck the options to allow any user to access it and to mount it at boot. That should do it - the next time you boot, the Windows partition should be unmounted and unreadable without elevated permissions.

---

### Post by rjbl on 2011-09-26
> **rishi_singh said:**
> I can see and edit my windows 7 partition from inside ubuntu linux 10.04. I want to hide it or make it inaccessible in ubuntu. The sole reason i use linux is to clean pendrive of malware before i use them in windows. So i dont want malware to be able to access the windows 7 or people using ubuntu in my laptop to accidentally put infected files there. I have wasted more than 10 hours on this problem and getting wifi to work on ubuntu. Nothing happened and i am looking for help.


PS :
I dont want to use this silly and needlessly complicated os for anything except that. I dont care what the security experts and the computer scientists say about linux. It is anything but convenient. Is this thing even getting popular or is it the exclusive preserve of people who love typing many commands to sound cool and nerdy ?

*The sole reason i use linux is to clean pendrive of malware before i use them in windows. *Interested to hear just how you actually do this. Do let us know, sometime soon.

rjbl

---

### Post by rishi_singh on 2011-09-26
> **rjbl said:**
> *The sole reason i use linux is to clean pendrive of malware before i use them in windows. *Interested to hear just how you actually do this. Do let us know, sometime soon.

rjbl

Sometimes there is windows malware in pen drives/usb drives. They cannot be seen inside windows and might infect your system. In fact, a scan by most updated antivirus programs might even show that the pen drives are clean. But when the same pendrive is used inside ubuntu, i see so many suspicious files that should not be there. I simply change the permissions of these otherwise undeletable files. Delete those files and then go and use the pen drive in windows. Takes 3-5 minutes, but much better than getting infected and spending 3-7 days in fixing window$. 

PS : 
Can i say that linux is the best malware removal tool ? Currently, I dont use it for anything else.

---

### Post by SecretCode on 2011-09-26
A thought: if you are prepared to install another OS to protect your Windows, then you are aware of quite a high level of danger from pen drives. You would be better off migrating to a Linux-based OS as your main system - and move your Windows 7 to a virtual machine under linux. (You would need to reactivate windows but otherwise it's OK.)

---

### Post by Copper Bezel on 2011-09-26
Windows 7 would have some performance limitations that way, though, and it's a bit of a hassle.

It's odd - where are these flash drives coming from that they're regularly packing this malware? And do you have any idea what the files might be, specifically?

---

### Post by rjbl on 2011-09-27
> **rishi_singh said:**
> Sometimes there is windows malware in pen drives/usb drives. They cannot be seen inside windows and might infect your system. In fact, a scan by most updated antivirus programs might even show that the pen drives are clean. But when the same pendrive is used inside ubuntu, i see so many suspicious files that should not be there. I simply change the permissions of these otherwise undeletable files. Delete those files and then go and use the pen drive in windows. Takes 3-5 minutes, but much better than getting infected and spending 3-7 days in fixing window$. 

PS : 
Can i say that linux is the best malware removal tool ? Currently, I dont use it for anything else.

This doesn't really make a lot of sense. Either your Windows can see, and read, these phantom files - in which case they may be some kind of malware or not; or Windows cannot see, or read, these phantom files in which case they certainly ain't Windows-malwares.

Here's a tip: set your BIOS so that your box won't boot off a USD device and reformat these suspect flash drives, using Windows, before you use them. 

In this context you really are wasting your time messing around with Linux. Do explore GNU/Linux's capabilities - you will find it well your efforts. Ubuntu is, of course, a very good place to start.

rjbl

---

### Post by Copper Bezel on 2011-09-27
> This doesn't really make a lot of sense. Either your Windows can see, and read, these phantom files - in which case they may be some kind of malware or not; or Windows cannot see, or read, these phantom files in which case they certainly ain't Windows-malwares.

That's the opposite of true. Linux and Windows use different conventions to hide files. Use a flash drive between a Windows machine and a Linux machine, and you'll only see the Windows trash bin from the Linux machine and vice versa. In Linux, hidden files can always be displayed with a quick Ctrl+H, but that's not true of Windows. 

Still, I'm really curious what these mysterious files are, and I'm equally unsure that they're actually malicious. Could be some app's little proprietary thumbnail cache, for all we know at this point.

---

### Post by SecretCode on 2011-09-27
> **Copper Bezel said:**
> Windows 7 would have some performance limitations that way, though, and it's a bit of a hassle.

For sure, but what I'm saying is (not completely seriously), given the threats are this serious, to migrate as many apps as possible to Linux, retaining Windows only for things that don't have Linux alternatives and don't run well in wine.

Or else stop using USB sticks.

---

### Post by rishi_singh on 2011-09-27
> **Copper Bezel said:**
> That's the opposite of true. Linux and Windows use different conventions to hide files. Use a flash drive between a Windows machine and a Linux machine, and you'll only see the Windows trash bin from the Linux machine and vice versa. In Linux, hidden files can always be displayed with a quick Ctrl+H, but that's not true of Windows. 

Still, I'm really curious what these mysterious files are, and I'm equally unsure that they're actually malicious. Could be some app's little proprietary thumbnail cache, for all we know at this point.

I understand that its possible that sometimes files may not be harmful. But I did see the nasty ones in my cleaning sessions before. Unfortunately, I dont have any more malware-infected pen drives. I would gladly show you if I could. Many of the mysterious files i mentioned before were exe files. No thumbnails.

Can you try this (its damage on purpose) ? 
Get an old version of a malware that uses usb drives to spread. Turn off your AV in windows. If the malware doesnt prevent access to the pen drive after infection, then good. You will see regular stuff in your pen drive and nothing else. 
Go into linux and see the pen again. It have some exe files that should not be there.
Or, go to google and search for the name of that .exe you see in linux. It might appear on the malware list of some AV vendor.

---

### Post by rjbl on 2011-09-27
> **Copper Bezel said:**
> That's the opposite of true. Linux and Windows use different conventions to hide files. Use a flash drive between a Windows machine and a Linux machine, and you'll only see the Windows trash bin from the Linux machine and vice versa. In Linux, hidden files can always be displayed with a quick Ctrl+H, but that's not true of Windows. 

Still, I'm really curious what these mysterious files are, and I'm equally unsure that they're actually malicious. Could be some app's little proprietary thumbnail cache, for all we know at this point.

CopperB

Hate to be a bit of a bitch. But I've just this moment written a testfile out of XPsp3 onto one of my USB externals, set the file's attribute to 'hidden' and can seen it plainly visible from 11.04. Pretty sure the external is NTFS as well.

Personally I am highly skeptical about the OP - his earliest postings really smell of troll; glad to see you are kindlier and more patient than I, good example for me to follow.

best wishes

rjbl

---

### Post by Basher101 on 2011-09-27
There is an easy way to keep others from accessing your windows partitions. Simply edit your fstab so only root has access to them, so you wont be able to open them at all UNLESS you start a nautilus window with root rights (this is done with a command and will require a password).

---

### Post by Copper Bezel on 2011-09-27
[QUOTE=rishi_sigh]I understand that its possible that sometimes files may not be harmful. But I did see the nasty ones in my cleaning sessions before. Unfortunately, I dont have any more malware-infected pen drives. I would gladly show you if I could. Many of the mysterious files i mentioned before were exe files. No thumbnails.[/quote]

Huh. Weird. Did you Google search for any of the filenames?

> Can you try this (its damage on purpose) ? 
Get an old version of a malware that uses usb drives to spread. Turn off your AV in windows. If the malware doesnt prevent access to the pen drive after infection, then good. You will see regular stuff in your pen drive and nothing else. 
Go into linux and see the pen again. It have some exe files that should not be there.
Or, go to google and search for the name of that .exe you see in linux. It might appear on the malware list of some AV vendor.

I don't actually have a Windows install handy. Part of why I'm a bit out of touch with Windows security these days, although this does seem to be a somewhat unusual case.

[QUOTE=rjbl]Hate to be a bit of a bitch. But I've just this moment written a testfile out of XPsp3 onto one of my USB externals, set the file's attribute to 'hidden' and can seen it plainly visible from 11.04. Pretty sure the external is NTFS as well.[/QUOTE]

Yes, but that's what I said. = )

[QUOTE=Me]Linux and Windows use different conventions to hide files.[/QUOTE]

You'd originally said that the files rishi couldn't see from Windows couldn't be intended to infect a Windows system. I was saying that they wouldn't use the Windows "Hidden" attribute if they weren't some part of the Windows universe, just as a .*.* file wouldn't be a very good disguise on a Windows machine. = )

---

### Post by rjbl on 2011-09-27
> **Copper Bezel said:**
> Huh. Weird. Did you Google search for any of the filenames?



I don't actually have a Windows install handy. Part of why I'm a bit out of touch with Windows security these days, although this does seem to be a somewhat unusual case.



Yes, but that's what I said. = )



You'd originally said that the files rishi couldn't see from Windows couldn't be intended to infect a Windows system. I was saying that they wouldn't use the Windows "Hidden" attribute if they weren't some part of the Windows universe, just as a .*.* file wouldn't be a very good disguise on a Windows machine. = )

Oops, looks like I misunderstood what you wrote. Wazzat about two great nations divided by a common language? Sorry.

rjbl

Still can't make head ner tail of what rishi is actually on about.

---

### Post by rishi_singh on 2011-09-27
> **rjbl said:**
> CopperB
Personally I am highly skeptical about the OP - his earliest postings really smell of troll; 
rjbl

I dont even understand what i am doing when i tinker with ubuntu and my partitions. I ask questions that sound not-so-nerdy, so i am a troll. great. thank you very much.

---

### Post by rishi_singh on 2011-09-27
[SIZE=4][B]update : 
I now use ubuntu 11.04. But the original problem still remains. Please help me to solve it, ie i want to make my win 7 inaccessible from linux. 
[/B][/SIZE]

---

### Post by rishi_singh on 2011-09-27
> **Copper Bezel said:**
> Oh, good point - using a VM, the flash drive *would* be mounted by Windows first.

It looks like we're in luck - from the same guide, install and run the package pysdm by running these commands in a terminal:

```
sudo apt-get install pysdm

gksu pysdm
```Since both of these are administrative tasks (thus the "sudo" and "gksu"), it'll ask for your password, but that should be all you need to do in the terminal.

Once you figure out which one is the Windows partition in the left-hand navigation pane, select it, click the "Assistant" button, and uncheck the options to allow any user to access it and to mount it at boot. That should do it - the next time you boot, the Windows partition should be unmounted and unreadable without elevated permissions.

Using ubuntu 11.04 now. I get an error when i use your commands.

[B]Unable to locate package pysdm.

<edit>

I got pysdm off the net. Installed and run. 
New problem - i only see "sda" in the pysdm windows. All else is deactivated/cant be clicked. Please tell me what to do now.
[/B]

---

### Post by Copper Bezel on 2011-09-27
Oh, I didn't think of that - pysdm is in the repositories, but you only have the basic ("Canonical-maintained") repositories enabled. To fix this for later and enable the others, open the Software Center or Synaptic, click Edit, select Software Sources, and check the unchecked boxes.  (Edit: for Synaptic, make that Settings, then Repositories.)

For the present problem, in pysdm itself, there's a triangle next to "sda" that will expand the list of volumes or partitions on that device. The Windows partition is the one where the "Type" is listed as "NTFS" instead of "ext4" or "swap".

---

### Post by rishi_singh on 2011-09-28
> **Copper Bezel said:**
> 
For the present problem, in pysdm itself, there's a triangle next to "sda" that will expand the list of volumes or partitions on that device. The Windows partition is the one where the "Type" is listed as "NTFS" instead of "ext4" or "swap".

Ok, i clicked that triangle. They should reduce the size of it, its too big.
I see sda 1 sda 2 sda 3... all ntfs except for one ext3 which is linux. I see no other info like size and all. So which sda properties are to be altered now ?

---

### Post by Copper Bezel on 2011-09-28
Hmm. It's odd that you're not seeing a swap partition. The two NTFS partitions are probably the main Windows partition and the Windows recovery partition. I'd just lock them both out, honestly. Select them, click the button labeled Assistant, and make sure the first two boxes are both unchecked.

---

### Post by rishi_singh on 2011-09-28
> **Copper Bezel said:**
> Hmm. It's odd that you're not seeing a swap partition. The two NTFS partitions are probably the main Windows partition and the Windows recovery partition. I'd just lock them both out, honestly. Select them, click the button labeled Assistant, and make sure the first two boxes are both unchecked.

Wait, i did see a swap word there. But can we be 100% sure about which one is the partition of win 7 ? I hope that not knowing which is the win 7 one will not affect my system in a wrong way.
I am not an expert at these things.

---

### Post by Copper Bezel on 2011-09-28
If it's NTFS, Windows put it there. As I said, the smaller one (and I know you can't see sizes from pysdm) is likely a recovery partition, which is probably not normally visible from Windows. I don't know how Windows 7 handles it, because I've never had a 7 machine of my own or had to do maintenance on one, but Windows 7 also introduced an equivalent to the Linux swap partition, and I don't know whether or not we might be seeing that, too.

If you want a graphical display of all the partition sizes and layout, install gparted. It's a very useful utility for other reasons, particularly since you're using Ubuntu primarily as a maintenance tool. For right now, it'll also cut down on the guesswork.

I know it sounds a little sloppy and haphazard to cut things out while we don't know what we're looking at, but changing the way Ubuntu recognizes the Windows partitions can't damage your Windows system, because the filesystem table we're editing is completely separate and won't be read by Windows. 

Conversely, a normal dual-boot install of Ubuntu won't (and couldn't, until recently) create any NTFS partitions at all. Ubuntu can read and write from NTFS filesystems, but NTFS doesn't support features that Linux system architecture requires, and your Ubuntu install (at system level) is only dependent on what's in the ext3 partition.

---

### Post by rishi_singh on 2011-09-28
> **Copper Bezel said:**
> 

If you want a graphical display of all the partition sizes and layout, install gparted. It's a very useful utility for other reasons, particularly since you're using Ubuntu primarily as a maintenance tool. For right now, it'll also cut down on the guesswork.


So, are you saying this - use gparted to see information about each partition and its size. See which sda is windows and then change the properties of that sda using pysdm ? BTW, what does sda mean ?

<EDIT>
I am downloading the gparted iso now. How do i install gparted inside ubuntu 11.04 , so that i can use it right away ? 

> **Copper Bezel said:**
> 
I know it sounds a little sloppy and haphazard to cut things out while  we don't know what we're looking at, but changing the way Ubuntu  recognizes the Windows partitions can't damage your Windows system,  because the filesystem table we're editing is completely separate and  won't be read by Windows. 


Can you confirm that there will be no damage to windows ? (I dont know what this filesystem table means, so i am unable to fully appreciate your advice)

> **Copper Bezel said:**
> 
Conversely, a normal dual-boot install of Ubuntu won't (and couldn't,  until recently) create any NTFS partitions at all. Ubuntu can read and  write from NTFS filesystems, but NTFS doesn't support features that  Linux system architecture requires, and your Ubuntu install (at system  level) is only dependent on what's in the ext3 partition.

Sorry, i dont really understand what those words mean. I am hoping that its not critical to doing what we are doing. 

Perhaps, i should be reading ubuntu for complete dummies. :(

---

### Post by Copper Bezel on 2011-09-28
Sorry, I'll try to slow down and explain more!

> So, are you saying this - use gparted to see information about each partition and its size. See which sda is windows and then change the properties of that sda using pysdm ?
Yes - gparted is a partition editor that gives you a neat little bar-graph representation of each drive and how its individual volumes are broken down (as well as a number of maintenance and editing features you won't need right now.) But it doesn't edit the filesystem table in the way we need to do, so we have to use pysdm for that.

> BTW, what does sda mean ?
It's a naming convention that Linux uses for mounted volumes within a drive, sort of like Windows' Drive C:, D:, etc. but more descriptive. I actually had to look up what the bits properly stood for myself. = ) For sda1, usually (but not always) equivalent to what Windows would call drive C:

SD refers to SATA drive, which identifies the interface the computer uses at the hardware level for this storage device.

A, B, C, etc. simply identifies which storage device attached to the SATA controller we're talking about. A in this case refers to the physical hard drive in your laptop.

1, 2, 3, etc. identifies the partition on that drive. So, in this case, your Linux system is installed at sda1, while something like sda2 is your swap, sda3 is your Windows partition, etc.

The term *filesystem* refers to the storage method used in a particular partition. Every partition is formatted according to a particular filesystem (and we can actually use the term *filesystem* in the particular to refer to a particular partition, as in the statement, "sda1 contains an ext3 filesytem." Windows and Linux need to know different things about the files that make up the system, so they need different ways of storing them. Different filesystems have other benefits and drawbacks; for instance, ext3 doesn't suffer file fragmentation and slow down over time like NTFS does, but it requires more space on disk for the same data.

NTFS is the filesystem introduced in the Windows NT kernel; ext3 is the third iteration of the Linux extended filesystem. (More information than you need right now, but there are many others, and interestingly, both NTFS and ext3 are on the way out - Linux is shifting to ext4, while Windows 8 uses another fileystem entirely that any earlier Windows and any current Linux can't read.)

> I am downloading the gparted iso now. How do i install gparted inside ubuntu 11.04 , so that i can use it right away ?

Gah, we've got to get you out of the Windows world a bit. The .iso you're downloading is basically its own little Linux distro that includes gparted and boots from a LiveCD. What we want is gparted installed in Ubuntu, as you say. You don't generally download Linux software from a website directly like that.

Linux systems use "repositories" to manage software packages. "Repositories" is what app stores were called before they were cool. = ) Ubuntu's primary interface with its repositories (its "App Store") is called the Ubuntu Software Center. I don't know which desktop shell you're using, but the Software Center is easy to find in the menu - either by finding it under Applications in the old interface or by typing a bit of the name in the Dash in the new interace.

Open up the Software Center and search for gparted - it'll come up as "Gnome Partition Editor" (g-part-ed is an acronymn for this.) Then, click "install." No browser needed.

> Can you confirm that there will be no damage to windows ? (I dont know what this filesystem table means, so i am unable to fully appreciate your advice)
Yes. For instance, if we deleted the filesystem table on your Ubuntu install outright, Ubuntu would no longer be bootable, but Windows wouldn't know the difference. 

And just to explain a bit more - "Filesystems table" is what the acronymn fstab refers to. It's just a text file (located at /etc in your Ubuntu install) that defines for Ubuntu what physical drives exist, what partitions (and thus what filesystems) exist on them, what to do with them at boot, and what users can access them in what ways. This filesystems table is read by Ubuntu at boot. pysdm is just a graphical editor that edits fstab. 

The only thing we could damage within your Ubuntu partition  that could in turn make Windows inaccessible is grub, the menu that you see when you first turn on the computer that allows you to select between Ubuntu and Windows. This is a "bootloader"; although it's installed from the Ubuntu side and located within your Ubuntu install, it's independent of Ubuntu, and it passes off to either Ubuntu or Windows after you make your selection. fstab isn't read until after Ubuntu begins to boot, so it doesn't affect your Windows install.

As I'd said, each system has its own way of identifying the volumes (partitions) that are mounted (recognized by the OS) at any given time. What's sda1 to Ubuntu might be drive E: or something in Windows. We're just indicating to Ubuntu that what it calls sda(whatever) shouldn't be mounted at all under Ubuntu.

---

### Post by rishi_singh on 2011-09-28
> **Copper Bezel said:**
> Sorry, I'll try to slow down and explain more!


Yes - gparted is a partition editor that gives you a neat little bar-graph representation of each drive and how its individual volumes are broken down (as well as a number of maintenance and editing features you won't need right now.) But it doesn't edit the filesystem table in the way we need to do, so we have to use pysdm for that.


It's a naming convention that Linux uses for mounted volumes within a drive, sort of like Windows' Drive C:, D:, etc. but more descriptive. I actually had to look up what the bits properly stood for myself. = ) For sda1, usually (but not always) equivalent to what Windows would call drive C:

SD refers to SATA drive, which identifies the interface the computer uses at the hardware level for this storage device.

A, B, C, etc. simply identifies which storage device attached to the SATA controller we're talking about. A in this case refers to the physical hard drive in your laptop.

1, 2, 3, etc. identifies the partition on that drive. So, in this case, your Linux system is installed at sda1, while something like sda2 is your swap, sda3 is your Windows partition, etc.

The term *filesystem* refers to the storage method used in a particular partition. Every partition is formatted according to a particular filesystem (and we can actually use the term *filesystem* in the particular to refer to a particular partition, as in the statement, "sda1 contains an ext3 filesytem." Windows and Linux need to know different things about the files that make up the system, so they need different ways of storing them. Different filesystems have other benefits and drawbacks; for instance, ext3 doesn't suffer file fragmentation and slow down over time like NTFS does, but it requires more space on disk for the same data.

NTFS is the filesystem introduced in the Windows NT kernel; ext3 is the third iteration of the Linux extended filesystem. (More information than you need right now, but there are many others, and interestingly, both NTFS and ext3 are on the way out - Linux is shifting to ext4, while Windows 8 uses another fileystem entirely that any earlier Windows and any current Linux can't read.)



Gah, we've got to get you out of the Windows world a bit. The .iso you're downloading is basically its own little Linux distro that includes gparted and boots from a LiveCD. What we want is gparted installed in Ubuntu, as you say. You don't generally download Linux software from a website directly like that.

Linux systems use "repositories" to manage software packages. "Repositories" is what app stores were called before they were cool. = ) Ubuntu's primary interface with its repositories (its "App Store") is called the Ubuntu Software Center. I don't know which desktop shell you're using, but the Software Center is easy to find in the menu - either by finding it under Applications in the old interface or by typing a bit of the name in the Dash in the new interace.

Open up the Software Center and search for gparted - it'll come up as "Gnome Partition Editor" (g-part-ed is an acronymn for this.) Then, click "install." No browser needed.


Yes. For instance, if we deleted the filesystem table on your Ubuntu install outright, Ubuntu would no longer be bootable, but Windows wouldn't know the difference. 

And just to explain a bit more - "Filesystems table" is what the acronymn fstab refers to. It's just a text file (located at /etc in your Ubuntu install) that defines for Ubuntu what physical drives exist, what partitions (and thus what filesystems) exist on them, what to do with them at boot, and what users can access them in what ways. This filesystems table is read by Ubuntu at boot. pysdm is just a graphical editor that edits fstab. 

The only thing we could damage within your Ubuntu partition  that could in turn make Windows inaccessible is grub, the menu that you see when you first turn on the computer that allows you to select between Ubuntu and Windows. This is a "bootloader"; although it's installed from the Ubuntu side and located within your Ubuntu install, it's independent of Ubuntu, and it passes off to either Ubuntu or Windows after you make your selection. fstab isn't read until after Ubuntu begins to boot, so it doesn't affect your Windows install.

As I'd said, each system has its own way of identifying the volumes (partitions) that are mounted (recognized by the OS) at any given time. What's sda1 to Ubuntu might be drive E: or something in Windows. We're just indicating to Ubuntu that what it calls sda(whatever) shouldn't be mounted at all under Ubuntu.

Thanks for all that info. I tried to get gparted started, but failed.
Here is what happened :

got gparted in software center. i see "available from the main source" and a button "use this source". I click the button and nothing happens. Now what ?

[SIZE=4]**PS : Did you folks see the movie "Independence  day "  or any such movie which has hackers ? They should not upload viruses.  Just upload linux and the system will become useless.  **[/SIZE][SIZE=3]**Linux is the most sophisticated "hacking toolkit". **[/SIZE]

---

### Post by Copper Bezel on 2011-09-29
> got gparted in software center. i see "available from the main source" and a button "use this source". I click the button and nothing happens. Now what ?
Well, I'm baffled. Once you select a piece of software in the Ubuntu Software Center, the only buttons are "More Info" and "Install" (or "remove" if it's already installed.)

[img]http://dl.dropbox.com/u/17749392/Screenshots/110910/usc.png[/img]

---

### Post by rishi_singh on 2011-09-29
> **Copper Bezel said:**
> Well, I'm baffled. Once you select a piece of software in the Ubuntu Software Center, the only buttons are "More Info" and "Install" (or "remove" if it's already installed.)

[IMG]http://dl.dropbox.com/u/17749392/Screenshots/110910/usc.png[/IMG]

Ok, using the above screen, how i am i supposed to run this program ? Is it by double clicking the name ? (or is it 9999997977777 arcane commands ;) )

---

### Post by Copper Bezel on 2011-09-29
No, once you have it installed, you can just run it from the menu. Again, I don't know which UI shell you're using, but if you're using Unity, you can just hit the flag key and start typing gp or partition or whatever and it'll come up. If you're using the "classic" interface, it'll be under System > Administration.

No terminal commands required. Although, if you're more comfortable with that, it'd be [font="Courier New"]gksu gparted[/font]. = )

---

### Post by rishi_singh on 2011-09-29
> **Copper Bezel said:**
> No, once you have it installed, you can just run it from the menu. Again, I don't know which UI shell you're using, but if you're using Unity, you can just hit the flag key and start typing gp or partition or whatever and it'll come up. If you're using the "classic" interface, it'll be under System > Administration.

No terminal commands required. Although, if you're more comfortable with that, it'd be [FONT=Courier New]gksu gparted[/FONT]. = )

In the image you gave, once you click gnome partition editor what do you see ? I see only on button to the right which says "use this source" and nothing happens when i click it. 
The terminal doesnt help either. I am asked for my password and nothing happens after that. Immediately after that, my system became sluggish and i could not ever type "terminal" in the software section for a few seconds. But it became normal after that.

---

### Post by Copper Bezel on 2011-09-29
I've never seen that message before, but it looks like you're not the only one who's had that problem with that button. As far as I know, it's new. I guess gparted is in the "Universe" community-maintained repository and you don't have that repository enabled (as it's not enabled by default.) Previously, gparted wouldn't have come up in the search at all without the source being enabled.

In any case, we'll work around it. Click "Edit" in the menu bar and select "Software Sources," and make sure that all the boxes on the window that comes up are checked.

---

### Post by rishi_singh on 2011-09-29
> **Copper Bezel said:**
> I've never seen that message before, but it looks like you're not the only one who's had that problem with that button. As far as I know, it's new. I guess gparted is in the "Universe" community-maintained repository and you don't have that repository enabled (as it's not enabled by default.) Previously, gparted wouldn't have come up in the search at all without the source being enabled.

In any case, we'll work around it. Click "Edit" in the menu bar and select "Software Sources," and make sure that all the boxes on the window that comes up are checked.

There is no edit option there. After doing something with that synaptic stuff, i see that gparted is not mentioned. I also see a red exclamation mark.

Do i have to download the source code and compile it myself to use it ?


PS : Linux is so easy. All you have to do is type a few simple commands, compile code or develop it yourself. How difficult can that be ? !!! I am happy that microsoft is dominating the market for desktop. I dont care about the flaws, at least its easy to use. Can anyone beat that ? **I would like to inflict the same torture on the creators of every distro of linux - if they wanna learn how to drive a car, i will first force them to learn mechanics, automobile engineering, then electronics engineering before i allow them to go places with the car. **

---

### Post by Copper Bezel on 2011-09-29
> There is no edit option there.
Then you're not in the Software Center, which is where we left off.

> After doing something with that synaptic stuff, i see that gparted is not mentioned. I also see a red exclamation mark.
And subsequently, this means nothing if I don't know what application you *are* using. 

If the exclamation point is an icon in the system tray, that icon is from the update manager, which is notifying you of available software updates (after a check triggered by Synaptic or the Software Center, both of which have to check the package lists to work.)

Passing strange, though - what did you do in Synaptic, exactly? I know I suggested yesterday that you *could* use it to enable the Universe repository, but you didn't do that, or I wouldn't be explaining how to do so from the Software Center (which was the first choice I'd recommended - [_post #20_](http://ubuntuforums.org/showthread.php?t=1850171&page=2#20).) 

In any case, this has been fun, but we're done now. = )

---

### Post by rishi_singh on 2011-09-29
> **Copper Bezel said:**
> Then you're not in the Software Center, which is where we left off.


I swear i was there. The software center. But i dont see the edit option. How do you take screenshots in linux ?  I will do it and show you.

---

### Post by Copper Bezel on 2011-09-29
The printscreen key should actually work as it is, or you can launch "Take Screenshot" from the Dash. Anyway, assuming that you're using the default Unity interface, you should be seeing something like this - it occurs to me that you might not have found the menu, which appears in the bar when you hover it. (A fairly silly design feature, to my eye.)

[[img]http://dl.dropbox.com/u/17749392/Screenshots/USC%20question/Screenshott.png[/img]](http://dl.dropbox.com/u/17749392/Screenshots/USC%20question/Screenshot.png)

And once you select "Software Sources," this window will come up, and the boxes for the "Universe" and "Multiverse" repos probably won't be selected.
[[img]http://dl.dropbox.com/u/17749392/Screenshots/USC%20question/Screenshot-1t.png[/img]](http://dl.dropbox.com/u/17749392/Screenshots/USC%20question/Screenshot-1.png)

Once you have them enabled, installing software from them is the same process as getting a track on iTunes (but, you know, free.)

---

### Post by rishi_singh on 2011-09-29
Both options are already enabled. There is a ubuntu cd option too. i checked that. the software center says that no gparted is found. btw my wifi is working now.

---

### Post by Copper Bezel on 2011-09-29
Weird. If you ran the updates, the WiFi thing makes some sense (admitting some *very* lucky timing, so that's quite cool) but I don't get the other bit. Are you seeing anything else in the Software Center? The status bar at the bottom should say something like "2368 items available."

Now remind me, do you get any error messages if you close out the Software Center and open a terminal (sigh, I know) and run this?

```
sudo apt-get update; sudo apt-get install gparted
``` 

If you do, copy and paste the output here.

---

### Post by rishi_singh on 2011-09-29
> **Copper Bezel said:**
> Weird. If you ran the updates, the WiFi thing makes some sense (admitting some *very* lucky timing, so that's quite cool) but I don't get the other bit. Are you seeing anything else in the Software Center? The status bar at the bottom should say something like "2368 items available."

Now remind me, do you get any error messages if you close out the Software Center and open a terminal (sigh, I know) and run this?

```
sudo apt-get update; sudo apt-get install gparted
```If you do, copy and paste the output here.

I see a lot of stuff being installed, as of now. Its not completed yet. Will update soon. BTW, what do those commands mean ? Is  it download updates from internet and then instal gparted ?

---

### Post by rishi_singh on 2011-09-29
Results of Gparted (runs) : 
sda 1 to 6. 1 = nfts , sda 2 = win7,  3 = extended , 4 = swap, 5 = ext 3, 6 = swap and unallocated space.

in syspdm, i click the apply button and nothing happens. Please help.

Unchecked the "allow mount at boot time". Only two options remain checked -
1- mount file system in read only mode.
2- unmask for file permissions in octal.

What about the options under the "special files" tab ?
Stuff like allow execution of binaries. If i understand correctly, this would allow exe files to be executed in win should i decide to mount it in the future - not a good thing.

---

### Post by Copper Bezel on 2011-09-29
Sounds good - I'll break it down. As I've said, [FONT="Courier New"]sudo[/font] just elevates you to administration privileges. [FONT="Courier New"]apt-get[/font] is a command-line utility for package management. [FONT="Courier New"]update[/FONT] and [FONT="Courier New"]install[/FONT] are options that we modify the command apt-get with to tell it what to do.

The [FONT="Courier New"]update[/FONT] option just checks the repositories to update the list of available packages - that's all that scrolling text you're seeing. That it's working is a good sign. With any luck, we'll see in a bit what is broken - any error messages that come afterward.

The [FONT="Courier New"]install[/FONT] option installs the package we specify - in this case, gparted.

The ; just separates commands such that the next command will run as soon as the current one closes.

So, tl:dr version, we're not actually updating packages this way, just the package list. Just so you know, if you did want to install available updates this way, the commands would be [FONT="Courier New"]sudo apt-get update[/font] to update the list and [FONT="Courier New"]sudo apt-get upgrade[/font] to upgrade packages where available. But of course, the update manager provides a neat little GUI for this.

---

### Post by Copper Bezel on 2011-09-29
> Results of Gparted (runs) : 
sda 1 to 6. 1 = nfts , sda 2 = win7, 3 = extended , 4 = swap, 5 = ext 3, 6 = swap.
Great! Now you can take that back to pysdm and disable non-root access to sda2. We're very nearly finished. = )

Edit: I need to watch the jargon. By "root" above, I mean admin privileges - they're used pretty interchangeably. Just to clarify.

---

### Post by rishi_singh on 2011-09-29
> **Copper Bezel said:**
> Great! Now you can take that back to pysdm and disable non-root access to sda2. We're very nearly finished. = )

Edit: I need to watch the jargon. By "root" above, I mean admin privileges - they're used pretty interchangeably. Just to clarify.

I am at a loss of words for how to thank you. I appreciate your help and patience, especially with all the noise i added to my posts. Thank you very much. :)

Now i get a box which shows an error when i try to enter the win 7 - thats good. I was wondering if we could make the icons vanish altogether. Dont let the other users know that there is anything else except linux.

---

### Post by Copper Bezel on 2011-09-29
Excellent! And I do understand that this stuff can be frustrating. I had a few of those moments with my first Ubuntu install. (For me it was a WiFi driver issue. Yucky stuff.)

I'm sorry we couldn't hide it completely, but at least this keeps friends and malware out of your Win7 drive. If this will work for you, just mark the thread as solved in Thread Tools at the upper right. = )

---

### Post by rishi_singh on 2011-09-29
> **Copper Bezel said:**
> 
I'm sorry we couldn't hide it completely, but at least this keeps friends and malware out of your Win7 drive. 

It is fine. My system is not pentagon or something like that. :P That is enough.

---

### Post by gringo loco on 2011-10-02
While I have a serious intellectual predicament understanding why someone with such apparently high level of computer skills (ability to fix windough$!!)choosing Ubuntu for this purpose only, I do see the practicality of rishi_singh's solution to some infected flash drive problems. 
I have several computers running Ubuntu that groups of volunteer teachers use and one still running Windough$ for people who seem to really need it,which, I recently had to completely reformat in order to remove a "Trojan" that very few W based scanners could find and none of the ones I could access were able to remove. However, all of my Ubuntu computers could easily and instantly find and remove both the folder and autorun file it left in any flash drive that was plugged in to it.

---

### Post by rishi_singh on 2011-10-04
> **gringo loco said:**
> While I have a serious intellectual predicament understanding why someone with such apparently high level of computer skills (ability to fix windough$!!)choosing Ubuntu for this purpose only, I do see the practicality of rishi_singh's solution to some infected flash drive problems. 
I have several computers running Ubuntu that groups of volunteer teachers use and one still running Windough$ for people who seem to really need it,which, I recently had to completely reformat in order to remove a "Trojan" that very few W based scanners could find and none of the ones I could access were able to remove. However, all of my Ubuntu computers could easily and instantly find and remove both the folder and autorun file it left in any flash drive that was plugged in to it.

Thats what i do too.

---

