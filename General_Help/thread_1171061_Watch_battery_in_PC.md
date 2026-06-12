---
title: "Watch battery in PC"
date: 2009-05-27
forum: General Help
---

### Post by cybrsaylr on 2009-05-27
My daugther's PC is acting up. It won't boot, keeps going in an endless loop.
When trying to boot it flashes the Gateway logo F2, F10, then goes to XP start, then reflashes the Gateway logo again then goes to the DOS screen saying there was a recent power failure that shut the PC down and hit enter if you want to start normal, or go into a 'safe mode start', or a 'dos prompt start', or a 'restricted safe mode', with a 25 second timer before it by default starts normal. No matter what you select, it is ignored and just keeps repeating this loop. The only way out is to hit F10 to boot off the install disc which then wants me to format and reinstall XP!

There was a power failure in her house that knocked out the PC causing a hard shutdown.

Looked over the PC and HDD sounds normal trying to boot and the PC just keeps going though this startup loop endlessly.

BTW I saw this 'watch battery' in her PC a [CR2032]("http://www.lowcostbatteries.com/Batteries/B-310_p/b-310.htm") 3 Volt Lithium Coin Battery! Why is that battery in a PC? My desktop has no battery in it. Her Gateway PC is 5 years old. Could this battery be related to the problem? My Gateway desktop has no battery in it.

---

### Post by lisati on 2009-05-27
> **cybrsaylr said:**
> 
BTW I saw this 'watch battery' in her PC a [CR2032]("http://www.lowcostbatteries.com/Batteries/B-310_p/b-310.htm") 3 Volt Lithium Coin Battery! Why is that battery in a PC? My desktop has no battery in it. Her Gateway PC is 5 years old. Could this battery be related to the problem? My Gateway desktop has no battery in it.

Many modern computers have some kind of battery in them, even if you don't see them. They're commonly used to help save the BIOS settings in what's known as a CMOS memory. The practice dates back from the early days of the x86-based computers, most notably the "AT" range and *some* XTs.

---

### Post by cybrsaylr on 2009-05-27
lisati,
What happens when they go dead? Is there any warning?

---

### Post by plucky on 2009-05-27
> **cybrsaylr said:**
> lisati,
What happens when they go dead? Is there any warning?

You will be asked to input the time and date as they would have reset to some default setting.Any cmos setting will reset to factory default.This should not cause the symptoms you are seeing.

Possibly Memory,power supply or motherboard.Boot a Live CD and see if that runs and then test the memory from the Live CD.


Good Luck

---

### Post by cybrsaylr on 2009-05-27
plucky,
Thanks, I'll try running a live CD and test the memory.

---

### Post by piratebill on 2009-05-27
It sounds like a hard drive problem to me.  Spinrite will take care of that for you, but the program is not free :(

---

### Post by cybrsaylr on 2009-05-27
piratebill,
Took the side off and listened closely while PC tried to boot and the HDD sounded normal.....no funny or unusual noises.

---

### Post by PaulReaver on 2009-05-27
I had a similar problem. 

I managed to fudge my nvidia drivers,  
windows would boot as normal, 
then just after my desktop icons would would appear, 
it would restart, and take me to the windows did not shut down correctly screen.

To fix it I had to boot to safe mode and uninstall the nvidia drivers.
then windows would boot properly, and then I could reinstall the nvidia drivers.


dont know if it'll help.  but it should'nt hurt.

---

### Post by PaulReaver on 2009-05-27
sorry misread the post.

first thing to do would be boot a linux live cd, if it does'nt crash/restart then its not the motherboard.

if it only crashes when you boot from the hard disk, its either the filesystem or the mechanical parts of the hard disk. hopefully its the filesystem.

do you know if the XP C:\ partition is ntfs or fat32.
fat32 does'nt like power failures.

you could get any important files (photo/documents/music) using a linux live cd and an external hard disk. reinstall XP and copy back your important stuff from the external hdd.

---

### Post by RD1 on 2009-05-27
> There was a power failure in her house that knocked out the PC causing a hard shutdown.

Best case scenario: Corrupted files due to power failure. Reboot with XP cd and use Repair Console to run chkdsk. Possibly do repair install of Windows or, if that fails, a new clean install.

More likely scenario: You need a new hard drive.

---

### Post by cybrsaylr on 2009-05-27
Here's the latest.
JJ Live CD booted up and ran fine with no issues.

Started a JJ install to see what the HDD looked like and the partitioner  said 'there is no operating system'! Just an empty drive!
Went to manual install for a different look and it showed the same 'no OS on the hard drive! I don't have any idea what caused this, or if a power failure could even do that. My daughter then told me she was getting 'funny XP error' messages the last month and a half that XP was having problems and was trying to correct it. She would just re-start the PC and it ran OK, till the next error, ignoring these warnings. Then they got the 'blue screen of death' and it wouldn't boot at all. I didn't know these errors were happening to her PC. 

Since the PC showed the drive 'empty', I assumed all was lost and then installed JJ. Install took 14 minutes, then put in the 76 updates and all looks A-OK. The HDD (a 6 year old Maxtor.......eeekkk!) sounded normal the whole time. She got this PC in 2003. Played around with JJ awhile showing her hubbie a few things on linux. During that hour or two JJ operated flawlessly along with their 6 yr old Gateway.

Just did an XP reinstall for my sister. It took 2 days to get it fully done and up to date with all her programs and apps!
So I figured I wasn't going to take a chance doing that over again if the HDD is going! So I just installed Jaunty to test the HDD and PC which took about 30 minutes total time for install and updates......in case the drive goes.

---

### Post by cybrsaylr on 2009-05-28
I have a question.

Because the Maxtor HDD is 6 yrs old I told them to get a new HDD.
They like Ubuntu but miss XP because they are just learning linux. Can I just put XP on the new HDD, make it primary drive, them move the Maxtor drive with Ubuntu to slave drive? Will this run without problems and allow them to pick the OS they want to run on bootup? I never did it this way before.

---

### Post by plucky on 2009-05-29
> **cybrsaylr said:**
> I have a question.

Because the Maxtor HDD is 6 yrs old I told them to get a new HDD.
They like Ubuntu but miss XP because they are just learning linux. Can I just put XP on the new HDD, make it primary drive, them move the Maxtor drive with Ubuntu to slave drive? Will this run without problems and allow them to pick the OS they want to run on bootup? I never did it this way before.


If you install XP to the master drive and then Ubuntu to the slave drive,Ubuntu will do all the work for you and install the grub boot manager to the MBR of the master drive.This will give you the choice of which operating system to boot.

The default will be Ubuntu,but this can be altered in the menu.lst file to boot XP as the default.

Good Luck

---

### Post by cybrsaylr on 2009-05-29
> **plucky said:**
> If you install XP to the master drive and then Ubuntu to the slave drive,Ubuntu will do all the work for you and install the grub boot manager to the MBR of the master drive.This will give you the choice of which operating system to boot.

The default will be Ubuntu,but this can be altered in the menu.lst file to boot XP as the default.
plucky,
Thanks.
How do you do this?
Is there an app for this in Synaptic manager, or do you have to do it all in terminal?

I assume all is left as is with the master drive right now running 9.04 and you just pull it and switch the jumper making it slave, then reinstall the new drive as master, then connect the two.
Is this correct?

---

### Post by plucky on 2009-05-29
> How do you do this?
Is there an app for this in Synaptic manager, or do you have to do it all in terminal?

When you install the new drive as master and install XP,it will write the XP boot loader to the MBR of the new drive.Then when you re-install Ubuntu to the slave drive,it will install grub to the MBR of the new drive,overwriting the XP bootloader.

Then you have to edit the menu.lst file and specify the default boot by searching in menu.lst for ```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

``` and changing the default from 0 to count down the list of boot options to point to the XP boot entry.This number will vary depending on the number of kernel entries in the menu.lst file.

There are a number of Howto's in the Tutorials and Tips section on this Forum.


Good Luck

---

### Post by cybrsaylr on 2009-05-29
plucky,
Thanks for the help. 
Wasn't really sure how to do that. Wasn't sure if you have to re-install Ubuntu again or not in the slave drive. Guess it looks like I will will have to install it again in the slave drive.

---

