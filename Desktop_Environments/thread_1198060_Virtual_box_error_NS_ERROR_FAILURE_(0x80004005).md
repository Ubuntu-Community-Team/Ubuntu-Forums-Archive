---
title: "Virtual box error NS_ERROR_FAILURE (0x80004005)"
date: 2009-06-26
forum: Desktop Environments
---

### Post by burntresistor on 2009-06-26
the problem is I can't get into virtual box. I get the same error  I did what the error reccomeneded which i attached below. After I reinstalled dkms I went into etc/init.d  and clicked on the dkms auto installer file which didn't run it terminal wouldn't open same with vboxdrv,there isn't one with actual setup in the title. terminal didn't want to run the file. 



Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Machine
Interface: 
IMachine {13420cbb-175a-4456-85d0-301126dfdec7}


Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Re-setup the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

---

### Post by Locutus_of_Borg on 2009-06-27
Just download the Linux installer from Sun's website

you have mismatched kernel modules, the installer from Sun will recompile the modules for you.

---

### Post by merlinus on 2009-06-27
Same thing happened to me after installing some updates.  I checked and DKMS was already installed.

But running the command prefaced by sudo fixed everything.

```

sudo /etc/init.d/vboxdrv setup

```

---

### Post by theGlitch on 2009-08-15
I just want to bump this with a thank you... I've been banging my head about this one for a week

---

### Post by essius on 2009-10-23
> **merlinus said:**
> Same thing happened to me after installing some updates.  I checked and DKMS was already installed.

But running the command prefaced by sudo fixed everything.

```

sudo /etc/init.d/vboxdrv setup

```


Thanks alot ! :)

---

### Post by thiefy on 2009-11-18
hi, i got that error also. 
 all you have to do (at least for me) was run virtualbox as root.
 
 
 simply gksudo VirtualBox &
 
 
 that's it. 
 it wants to run as root i guess...
 if you start it from the menu - i get that error - saying that the virtual machines are not accessible.
 
 oh, and notice the caps in that command. they are needed...

---

### Post by granade on 2009-12-02
> **merlinus said:**
> Same thing happened to me after installing some updates.  I checked and DKMS was already installed.

But running the command prefaced by sudo fixed everything.

```

sudo /etc/init.d/vboxdrv setup

```


Bump for thanks! ;)

---

### Post by dakaltty on 2009-12-05
while installing the kernel i got this error message..

Makefile:152: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again.  Stop.


How can i resolve it?

---

### Post by Astrals on 2009-12-07
**I am having the same problem.**

i'm using **ubuntu-9.10-alternate-amd64** from fresh install did the system updates, setup the system to my needs, installed **virtualbox-3.1_3.1.0-55467_Ubuntu_karmic_amd64.deb** (latest version) from sun (for extra functionality) and it worked great last night, then turned my system on again about 12 hours later (did not install anything and no updates available) and vbox now coming up with the same error i have tried the above with the same error, also tried complete removal and reinstall also with no luck.


**Error:**
Failed to create the VirtualBox COM object.
The application will now terminate.
Start tag expected, '<' not found.
Location: '/home/xxxx/.VirtualBox/VirtualBox.xml', line 1 (0), column 1.
/home/vbox/vbox-3.1.0/src/VBox/Main/VirtualBoxImpl.cpp[420] (nsresult VirtualBox::init()).


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
VirtualBox
Interface: 
IVirtualBox {2158464a-f706-414b-a8c4-fb589dfc6b62}




"xxxx"=my username
Any help with this will be very much appreciated, hopefully this might help someone out as well.



EDIT:
I found a solution for this.
In your home folder **/home/xxxx/.VirtualBox** the file **VirtualBox.xml** became **corrupted** so delete it (when you restart virtualbox you will have to re-register).
After that go to virtualbox menu for **Virtual Media Manager** and add the xxxx.vmdk image to it.
Next step add a new OS for virtualbox and select the first (for me xp) then select for **Boot Hard Disk** use existing hard disk and select the one you added for media manager.
There your done vbox is now working with your virtual hard disk before the crash and you don't loose anything.

My next step was back in my .Virtualbox folder i copied the 3 files (compreg.dat, VirtualBox.xml and xpti.dat) to .xxxx (copy) in the same folder (just in case this happens again).
The last step was to make another virtualbox snapshot.

I hope this helps you out as well.

---

### Post by lilo624 on 2009-12-20
Thank you Astrals, this did the trick for me.  Have been looking for a solution for weeks.  But makes me wonder why the "VirtualBox.xml"  became corrupt in the first place?

Once again, thanks for posting.  Your are a life saver!

---

### Post by Samhain13 on 2010-01-06
I had the same problem just now. What I did was:
```
$ /etc/init.d/virtualbox-ose stop 
```

Then:
```
$ /etc/init.d/virtualbox-ose start
```

It's working fine now. :D

---

### Post by dddanmar on 2010-01-29
+1 Samhain13 thank you, I tried everything else in the thread short of a restart and this saved me from the trip!

---

### Post by aniserg on 2010-02-20
> **Samhain13 said:**
> I had the same problem just now. What I did was:
```
$ /etc/init.d/virtualbox-ose stop 
```Then:
```
$ /etc/init.d/virtualbox-ose start
```It's working fine now. :D

Thx alot!!!!!!!!!!!!

How did u guessed to this?

---

### Post by hariks0 on 2010-02-20
I had received an error saying Licence file was not found in /usr/share/doc/virtualbox3.1. I tried reinstallation - Failed. I tried removal, autoclean, autoremove and reinstallation - Worked. Even the clients I had already installed were there.:popcorn:

---

### Post by Hero of Time on 2010-02-21
As a VB forum mod, it pains me to see such nasty 'solutions' to problems that aren't really problems.

First of all, the problem where it all started with was a simple kernel module. With update-manager updating your system AND kernel without your knowledge, it can happen that the module isn't compiled properly because you don't have the right kernel headers to match your kernel image. So make sure that you have the meta package installed that depends on the latest available kernel packages and are of the same flavour (generic image and server headers don't match).
The solution is noted clearly, run '/etc/init.d/vboxdrv setup' AS ROOT. This means that you need to put 'sudo' before the command.
You also need to be a member of the 'vboxusers' group. This error can come up if you're not a member.

Running VB as root is very bad practise. In fact, running anything MADE for normal user use as root is bad.

Dakalty, your error means that you don't have 'build-essential' installed, thus lacking the kernel headers and tools to build kernel modules.

Finally, if your VirtualBox.xml file gets corrupted in some way, don't remove it but rename it. If you start VB again without a VirtualBox.xml, one will be recreated (no need to register, cancel that 3 times and it won't show up again) and you can use that recreated file to fix your original VirtualBox.xml file. It is possible that this 'corruption' happens when the file is flushed to disk but the action is somehow cancled, leaving out a few close tags in the xml file. Fixing it manually can be done, you only need to have some insight in xml markup. There are plenty of examples on how to fix this on the VirtualBox forums.

In fact, all of these 'issues' are discussed and solved on the official VB forum, using the best method to keep your VMs and system configuration.

---

### Post by moontrains on 2010-02-25
> **Astrals said:**
> **I am having the same problem.**

i'm using **ubuntu-9.10-alternate-amd64** from fresh install did the system updates, setup the system to my needs, installed **virtualbox-3.1_3.1.0-55467_Ubuntu_karmic_amd64.deb** (latest version) from sun (for extra functionality) and it worked great last night, then turned my system on again about 12 hours later (did not install anything and no updates available) and vbox now coming up with the same error i have tried the above with the same error, also tried complete removal and reinstall also with no luck.


**Error:**
Failed to create the VirtualBox COM object.
The application will now terminate.
Start tag expected, '<' not found.
Location: '/home/xxxx/.VirtualBox/VirtualBox.xml', line 1 (0), column 1.
/home/vbox/vbox-3.1.0/src/VBox/Main/VirtualBoxImpl.cpp[420] (nsresult VirtualBox::init()).


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
VirtualBox
Interface: 
IVirtualBox {2158464a-f706-414b-a8c4-fb589dfc6b62}




"xxxx"=my username
Any help with this will be very much appreciated, hopefully this might help someone out as well.



EDIT:
I found a solution for this.
In your home folder **/home/xxxx/.VirtualBox** the file **VirtualBox.xml** became **corrupted** so delete it (when you restart virtualbox you will have to re-register).
After that go to virtualbox menu for **Virtual Media Manager** and add the xxxx.vmdk image to it.
Next step add a new OS for virtualbox and select the first (for me xp) then select for **Boot Hard Disk** use existing hard disk and select the one you added for media manager.
There your done vbox is now working with your virtual hard disk before the crash and you don't loose anything.

My next step was back in my .Virtualbox folder i copied the 3 files (compreg.dat, VirtualBox.xml and xpti.dat) to .xxxx (copy) in the same folder (just in case this happens again).
The last step was to make another virtualbox snapshot.

I hope this helps you out as well.


this worked for me.

thanks!!!

---

### Post by hoopoo on 2010-03-04
my thanks @ :KSAstrals:KS    
I have put way to much time into a fix for my "VM"
never thinking the .xml file could be corrupted.

[B]

[/B]

---

### Post by alwynvanniekerk on 2010-05-03
Likewise here, perfect solution thanks!

> sudo /etc/init.d/vboxdrv setup

---

### Post by gadzoinks on 2010-05-31
i got this error too, for a similar but not quite exact same reason, so i'll post it here just "for the record".. perhaps this is not a "use case" that the VirtualBox designers had thought about or at least prioritized, but here goes.

in my case, i wanted to share the VirtualBox between two *nix accounts on my ubuntu machine.  (by the way, i'm running ubuntu 10.04 LTS amd64 2.6.32-22-generic kernel, and VirtualBox 3.1.6_OSE r59338).

so to make this work, i first made a '[FONT="Courier New"]users[/FONT]' group and added both users to that group as members (menu: *[FONT="Lucida Sans Unicode"]System->Administration->Users and Groups[/FONT]*).

then (as root) i made a [FONT="Courier New"]/shared/vbox/.VirtualBox[/FONT] directory tree, and in each user's account, i sym-linked each user's [FONT="Courier New"].VirtualBox[/FONT] directory to point to it. i also set the [setgid bit]("http://en.wikipedia.org/wiki/Setuid#setgid_on_directories") on the directory (chmod 2775..) so that future files and directories created within would be owned by the correct group:


[FONT="Courier New"]$ sudo su -
# mkdir /shared
# chgrp users /shared
# chmod 2775 /shared
# mkdir -p /shared/vbox/.VirtualBox
# ln -sf /shared/vbox/.VirtualBox /home/user1/.VirtualBox
# ln -sf /shared/vbox/.VirtualBox /home/user2/.VirtualBox[/FONT]


this worked well for the first user.  but when the 1st user shut down the virtualbox, and the 2nd user tried to start it up, they would get the above mentioned [FONT="Courier New"]NS_ERROR_FAILURE (0x80004005)[/FONT].

it turns out that the missing piece is that the umask is set by default in ubuntu to 0022, which means that the files created by VirtualBox only have 640 or 644 ([FONT="Courier New"]rw-r-----[/FONT] or [FONT="Courier New"]rw-r--r--[/FONT]) permissions, when they should have 660 or 664 ([FONT="Courier New"]rw-rw----[/FONT] or [FONT="Courier New"]rw-rw-r--[/FONT]).  so when one user is done using the virtual box the next user cannot access it **because the group does not have write permission** to various files.

my solution was to change this line from

   [FONT="Courier New"]umask 022[/FONT]

to 

   [FONT="Courier New"]umask 002[/FONT]

in [FONT="Courier New"]/etc/profile[/FONT] (for all users)

OR

to uncomment and change this line:

   [FONT="Courier New"]#umask 022[/FONT]

to

   [FONT="Courier New"]umask 002[/FONT]

in each user's [FONT="Courier New"]/home/user*/.profile[/FONT] file.

oh yes, of course, i had to retro-actively go back in and change the permissions ([FONT="Courier New"]chmod 664[/FONT] or [FONT="Courier New"]chmod 660[/FONT]) on all the previously-created files in the [FONT="Courier New"]/shared/vbox/.VirtualBox[/FONT] directory and its subdirectories.

now both users read/write to these files correctly (albeit at different times of course), so that when one user shuts down the vbox, it can be started up from the other account without error.

---

### Post by VaiPhile on 2010-06-11
I have been having a very similar error message. I have been seeking help on the VirtualBox Forums as well, here:

[http://forums.virtualbox.org/viewtopic.php?f=7&t=31130](http://forums.virtualbox.org/viewtopic.php?f=7&t=31130)

but nothing has helped so far.  It seems likely that I have mismatched kernel headers after updating to 3.2, but I have completely reinstalled VB 2x as well as having run the setup script as root. Any other suggestions or requests for more information would be really really appreciated.  I need to get this fixed.

Oh, 2 more weird things.  It doesn't give me any error details, and it doesn't even make it to the VB splash screen (Gentoo guest works fine though...)  Thanks!

---

### Post by bogdanmata on 2010-07-20
> **merlinus said:**
> Same thing happened to me after installing some updates.  I checked and DKMS was already installed.

But running the command prefaced by sudo fixed everything.

```

sudo /etc/init.d/vboxdrv setup

```

Thank you

---

### Post by Rascayus on 2010-08-28
> **Astrals said:**
> **I am having the same problem.**


**Error:**
Failed to create the VirtualBox COM object.
The application will now terminate.
Start tag expected, '<' not found.
Location: '/home/xxxx/.VirtualBox/VirtualBox.xml', line 1 (0), column 1.
/home/vbox/vbox-3.1.0/src/VBox/Main/VirtualBoxImpl.cpp[420] (nsresult VirtualBox::init()).


Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
VirtualBox
Interface: 
IVirtualBox {2158464a-f706-414b-a8c4-fb589dfc6b62}




"xxxx"=my username
Any help with this will be very much appreciated, hopefully this might help someone out as well.


There is a very simple solution. In the .virtualbox folder is a backup of the VirtualBox.xml called VirtualBox.xml-prev, just rename to VirtualBox.xml and the problem is solved

---

### Post by Astrals on 2010-08-28
> **Rascayus said:**
> There is a very simple solution. In the .virtualbox folder is a backup of the VirtualBox.xml called VirtualBox.xml-prev, just rename to VirtualBox.xml and the problem is solved

  I suggest you do your homework thoroughly instead of being mis-informed!  Anyone with half a brain cell would first look for any backup file.  You obviously don't use virtualbox at all, you are only paraphrasing.  Do us all a favor and get eduacated, stop TROLLING.

---

### Post by andydbzee on 2010-09-01
i got the same error and tried:

sudo modprobe vboxdrv 

like it said in the error message. this worked for me.

---

### Post by Francewhoa on 2010-09-08
**Confirming this error with Virtualbox 3.2. And Ubuntu 8.0.4 LTS**

I tried all above solutions but nothing worked. Find attached error screenshot.

It works if I run VB with sudo. But for security reason I don't want to use sudo to run program. 

This issue seems to be related to file location and permissions. In my case I installed VB using the TERMINAL command line and sudo. But try to run it as another Ubuntu user. It seems that other users don't have access to some files located under root folder and this create the error.

---

### Post by Francewhoa on 2010-09-08
**The following worked for me for VirtualBox (VB) 3.2**

[LIST=1]
[*]**Follow instructions at** [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)
[*]                                   If not already done type in the following command in TERMINAL to **install requirements**
```
sudo apt-get install dkms                            
```
[*]                                  Before you are able to use VB you will need to **add yourself to the required group. **This facilitates access to the vboxdrv system device. Type in the following command in TERMINAL
```
sudo gpasswd -a <username> vboxusers
```
[*]Once you have applied this change **you will need to logout and log back in. **This is required for the group-access change to take effect.
[*]Then if you start VM it will return an error. To fix this navigate to your home folder **/home/xxxx/.VirtualBox** the file **VirtualBox.xml** became **corrupted** so delete it. Thanks to Astrals in comment #9 for this tip :)
[*]Restart VB. You will have to re-register. Type in the following command in TERMINAL to start VM
```
VirtualBox
```
[/LIST]

---

### Post by clockworkpc on 2010-10-04
Have encountered this problem on Ubuntu Lucid 10.04 completely update as of 2010-10-05.

Seems to have solved the problem for me too.

:)

---

### Post by FizzBuzz on 2010-10-25
I am having this same error in Ubuntu 10.10. I am running a Core i5 (dual core, each core hyperthreaded).  When I change the "system" setting for a guest OS to use more than one processor, I get the error.  Everything runs fine with one processor.

I have run /etc/init.d/vboxdrv setup and the problem persists.  I've even tried creating a new VirtualBox.xml file, same results.

Any ideas?

--edit--
Virtualization features for my CPU were turned off at the BIOS.  Whoops!




.

---

### Post by Thyagaraj on 2010-11-23
How about the virtualbox snapshots?. It's not taking the snapshots, having specified the path.

---

### Post by karma167 on 2010-12-26
thank you all i did was search in the ubuntu app thing and type in dkms and download the first thing on the list and then ran

sudo /etc/init.d/vboxdrv setup
thats it then started it up but i think im going to change from linux to windows cuz i cant keep playing at the OS to get it working i have school on this thing.

---

### Post by harishsasikumar on 2011-01-19
I had the following reason

I tried to install the OS (fixed medium storage unit) in a different harddisk partition which was NTFS.
Solution:
I Formated the partition and made it ext4. (:DDon't forget to unmount the partition before formating)

---

### Post by Merka73 on 2011-01-20
I am having the same error when I try to restore a snapshot.
I updated VB to *4.0.2 r69518* and run *sudo /etc/init.d/vboxdrv setup* but the problem persist.
Below the details of my issue posted, probably, in an incorect forum section.
[http://ubuntuforums.org/showthread.php?t=1670812](http://ubuntuforums.org/showthread.php?t=1670812)

Thanks

---

### Post by Merka73 on 2011-01-20
I am having the same error when I try to restore a snapshot.
I updated VB to *4.0.2 r69518* and run *sudo /etc/init.d/vboxdrv setup* but the problem persist.
Below the details of my issue posted, probably, in an incorect forum section.
[http://ubuntuforums.org/showthread.php?t=1670812](http://ubuntuforums.org/showthread.php?t=1670812)

Thanks

---

### Post by fred.warren on 2011-02-12
I am running Ubuntu Maverick with VirutalBox 4.0.2 and I did all of the above things to resolve the error. 

I removed all prior kernels, I installed dkms and the kernel headers for my current kernel.

```

sudo aptitude purge linux-headers-2.6.35-24 linux-headers-2.6.35-24-generic  linux-image-2.6.35-24-generic
cd /var/lib/dkms/vboxhost
sudo rm -rf 3.2.10
sudo /etc/init.d/vboxsvr setup

```

and still no go.

What did work, was this
```
sudo chown root:root /usr
sudo chown root:root /usr/lib
```

/usr/lib must be owned by root.

---

### Post by secros on 2011-12-18
fyi, i got this error after running 

```
sudo virtualbox
```

so that i could get proper usb permissions for my iphone inside my xp.vdi.  when i tried to go back to a non-root virtualbox, my xp vb was 'inaccessible.' the solutions here don't work for me, so for now, i have to just run virtualbox sudo'd.  i'd like to go back to not having to do that and having usb iphone access, but right i can't find a solution.  

thought someone else may be in my situation, too.

---

### Post by dubnutu on 2011-12-21
Deleting the file did the trick.

> rm ~/.VirtualBox/VirtualBox.xml

```
https://forums.virtualbox.org/viewtopic.php?f=1&t=38637#p201685
```

---

### Post by mafi127 on 2012-04-08
After the last update 

cant do nothing. tryed pruge virtualbox and then reinstall it aigan but still got error. cant even instal extension pack.

got this error when installing extension pack
[PHP]  p, li { white-space: pre-wrap; }  Failed to install the Extension Pack /home/tamps/Desktop/Oracle_VM_VirtualBox_Extension_Pack-4.1.12-77245.vbox-extpack.
 The installer failed with exit code 1: VBoxExtPackHelperApp: error: World writable: '/usr'.
  p, li { white-space: pre-wrap; }  
   Result Code: 
  NS_ERROR_FAILURE (0x80004005)
   Component: 
  ExtPackManager
   Interface: 
  IExtPackManager {3295e6ce-b051-47b2-9514-2c588bfe7554}
[/PHP]

Tryed allso:
sudo chown root:root /usr sudo chown root:root /usr/lib
but dident work eather

When trying to run ubuntu ins vb then I got this error
[PHP]  p, li { white-space: pre-wrap; }  Failed to open a session for the virtual machine linux.
 Failed to load VMMR0.r0 (VERR_SUPLIB_WORLD_WRITABLE).
  p, li { white-space: pre-wrap; }  
   Result Code: 
  NS_ERROR_FAILURE (0x80004005)
   Component: 
  Console
   Interface: 
  IConsole {1968b7d3-e3bf-4ceb-99e0-cb7c913317bb}
[/PHP]

can some1 help me to fix this plz?

---

### Post by mafi127 on 2012-04-11
Got fixed the proble. What did the trick was

[PHP]sudo chmod o-w /usr[/PHP]

---

### Post by Tyrr on 2012-05-09
Hello

I know hardly anything about fixing problems and after reading this thread, everything I learned was this:

```
 The character device /dev/vboxdrv does not exist.
	 Please install the virtualbox-ose-dkms package and the appropriate
	 headers, most likely linux-headers-generic.

	 You will not be able to start VMs until this problem is fixed.
Error opening file for reading: Toegang geweigerd (Access denied in Dutch)

```

anyone who knows how to fix this? I used the software centre to install VB but that does not do the trick for me.
used to work fine in 11.10 but on ubuntu 12.04 it no longer works.

edit: sudo Virtualbox doesn't help

---

### Post by dodo_ur on 2012-06-16
thank you Astrals it works for me :)

---

### Post by Neill_R on 2012-08-14
I am getting this error when I try to install the extension pack 

virtualbox 4.1.12_ubuntu r77245
oracle _VM_VirtualBox_Extention_pack-4.1.12-77245.vbox-extpack 

I accept license agreement 

Asks for Administrative password Black screen centered gray box 



[COLOR=Red]None of my password work here[/COLOR]

installer failed error code 255

 p, li { white-space: pre-wrap; }     Result Code: 
  NS_ERROR_FAILURE (0x80004005)
   Component: 
  ExtPackManager
   Interface: 
  IExtPackManager {3295e6ce-b051-47b2-9514-2c588bfe7554}

---

### Post by tijs14tijs on 2012-08-21
Be carefull, I would not recommend you to run virtualisation platforms as root. 
The reason that you need to run it as root is because Virtualbox needs to load a kernel driver. I would advice you to do that manually:
```
sudo modprobe vboxdrv
```
Thats better than giving virtualbox super user rights.

---

### Post by pleurastic on 2012-10-24
I had this error and virtualbox would fail immediately without opening the Machine Manager.  The .xml file had an error.  Luckily I found
/home/<Me>/.VirtualBox/VirtualBox.xml-prev
and copied it to /home/<Me>/.VirtualBox/VirtualBox.xml for the fix.
Good Luck.

---

