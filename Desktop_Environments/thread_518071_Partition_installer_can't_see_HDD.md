---
title: "Partition installer can't see HDD"
date: 2007-08-05
forum: Desktop Environments
---

### Post by sp0nge on 2007-08-05
I built a new machine, and have decided to put Dapper on it then to upgrde to feisty. I've got the live CD in and all is working fine, but when I go to install,  the partition manager hangs up as if it can't find the HDD. Anyone have an idea what causes this and how to fix it?

---

### Post by joe.turion64x2 on 2007-08-05
It is a new machine, and most likely a new hard drive.

Within the liveCD you can type in a terminal *sudo gparted* and if it can not see the drive still then perhaps you are gonna want to check its connections or be ready to replace it.

Is it a SATA?

Joe.

---

### Post by sp0nge on 2007-08-05
I ran gparted and found no devices. It is an IDE HDD. Still not detected.

---

### Post by joe.turion64x2 on 2007-08-05
> **sp0nge said:**
> I ran gparted and found no devices. It is an IDE HDD. Still not detected.
Do you have a spare IDE connector & cable. I have had several IDE cables faulty with brand new mobos, perhaps you'll want to try with another one. Just to discard possibilities. What about the BIOS? Is the drive detected there?

Joe.

---

### Post by sp0nge on 2007-08-06
Now that you mention it, I checked the BIOS and the drive doesn't show up. I will be pirating another IDE cable this afternoon. I know the drive works because it has run windows up to this point. I've tried to change the settings in BIOS, but don't seem to be able to get it to recognize the drive. Any help is appreciated, I'm off to the mobo forums to look for more info.

---

### Post by joe.turion64x2 on 2007-08-06
> **sp0nge said:**
> Now that you mention it, I checked the BIOS and the drive doesn't show up. I will be pirating another IDE cable this afternoon. I know the drive works because it has run windows up to this point. I've tried to change the settings in BIOS, but don't seem to be able to get it to recognize the drive. Any help is appreciated, I'm off to the mobo forums to look for more info.
If the drive has been working before then it is most likely a bad IDE cable. I remember my first assembled machine had that problem too.

I don't know if it is your case but several Western Digital drives need to be put in "Cable Select" mode to work. I recall having trouble booting machines in the past and that helped me so far.

Good luck.

Joe.

---

### Post by sp0nge on 2007-08-06
So I replaced the IDE cable and got no change when I fired the machine back up. I poked around the MSI website to see if I could find anything which led me to call Tech Support. The kid on the other end of the line was tellinng me that the IDE connector is a 3rd party hardware which typically requires a driver to be installed under WindowsXP in order to see the drive properly. He mentioned trying another flavor of Linux which I don't want to do until I can get dapper up and running and then upgrade to feisty. The next suggestion was to manually "add the hard drive" which didn't make any sense and the kid obviously couldn't help me much more after that statement. At this point, I'm considering buying an SATA HDD (something I should have done in the first place but was one of several mistakes in building my first machine), but would really like to solve this problem without spending more money. Any ideas how I can manually "add the hard drive" while running the live CD so I can install?

---

### Post by logos34 on 2007-08-06
what model msi board is this?  Make and model of drive? A Bios update might solve the problem.  Is the jumper set correctly on the drive? do you have it on its own ide channel as master or is it slave?

---

### Post by sp0nge on 2007-08-06
The board is P965 Neo. The drive is Seagate Baracuda 7200.10 250GB ATA-100/EIDE. I was sure I configured the jumpers correctly, but I'll be digging the manual out to confirm this once I post this reply. It is on it's own channel and the ribbon cord is only connected to the HDD as the master. Never done a BIOS update before.. any tips for a first timer before I jump into it?

---

### Post by sp0nge on 2007-08-06
I've confirmed the jumper setting is correct. I'm looking over the MIS site for info on upgrading the BIOS, this is kind of nerve wracking, I should probably do this in windows since that tends to be more user friendly? Everything I've done so far has been with the Live Ubuntu disk running..

---

### Post by psusi on 2007-08-06
How are you going to do it in windows if you can't get the hard disk to work?  I'd suggest plugging the drive into another computer again and see if you can get it recognized.  Either the drive is dead, or the cable is bad, or the ide controller on the new motherboard is dead.  

If the drive works in another machine using the same cable, but this board won't see it in the bios, then RMA the new board.

---

### Post by sp0nge on 2007-08-06
Perhaps I confused you. The drive is working. Windows XP is installed, but I hate it. I can run the Live CD on the machine and everything works fine. The problem is only when I try to install Ubuntu, the partition manager can not see the drive.

---

### Post by logos34 on 2007-08-06
well there doesn't appear to be a bios update, so that's out of the way (not that would have necessaruly made a diff, but it's always good to flash with the latest one first off when you have a new board).  And you say you double-checked the jumpers, so that's not it.  Could be faulty board.
> 
The drive is working. Windows XP is installed, but I hate it. I can run the Live CD on the machine and everything works fine. The problem is only when I try to install Ubuntu, the partition manager can not see the drive.

I'm confused.  I thought you just said above that the bios isn't recognizing the drive?  You mean windows is installed and works in another pc, just not when you plug it into the MSI board, in which case it doesn;t register in the bios, is that right?

Could be an issue related to the JMicron controller--although yours uses the JMB361 and all the problems seem related to the JMB363 controller.
See this link:
**[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57502](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57502)**

(scroll to bottom--rebrid242 has same board)

Edit: I agree that getting an ide hard drive was not the best idea--the board has only one ide controller.  But you could always use your ide as a  backup drive in slave position to the cd/dvd drive master--that would would work just fine with no bottleneck issues.

---

### Post by sp0nge on 2007-08-06
At least now I see that you're getting to be as confused as I am. Here's the long of it.. 

I built the machine in January, a Christmas present from the parents. P965 Neo mobo, 2x OCZ 1GB RAM, Intel Core 2 Duo 2.66, GF 7600GS graphics, and a generic sound card from CompUSA. I put the thing together and it fired right up, but the drive is not recognised in POST. A second screen runs showing my drive (the guy from tech support said the JMicron chipset that manages the IDE doesn't allow the drive to be seen directly which I thought was odd) and tells me to "press any key to continue" then fires right up to the windows startup. I can run just fine under windows with exception that it's an old pirated version that I can't update or it crashes my system. So I run the Dapper Live CD and all is beautiful in the world of Linux until I try to install the OS~~ then it just hangs up when the partition manager looks for the drive.

---

### Post by sp0nge on 2007-08-06
If I'm reading this right, there is a possibility of this issue being abated if I just install feisty directly? Any leads on a good how to? I managed to burn the ISO for Dapper but that was hellish and my attempts at mounting feisty have simply given me a Nero image of the ISO. I Was hoping that I could take the easy way out and upgrade from the Dapper install :(

---

### Post by logos34 on 2007-08-06
Ok, I see.

> JMicron chipset that manages the IDE doesn't allow the drive to be seen directly which I thought was odd

yeah, pretty odd.

All I can suggest is you read through some of the forums because I just did a quick search and there's no shortage of posts on jmicron and p965.  That's more likely the issue because there's not much else it could be.  Look for those relating to your msi neo board--hopefully there's a workaround to get the ubuntu installer to recognize the drive.

---

### Post by logos34 on 2007-08-06
> **sp0nge said:**
> If I'm reading this right, there is a possibility of this issue being abated if I just install feisty directly? Any leads on a good how to? I managed to burn the ISO for Dapper but that was hellish and my attempts at mounting feisty have simply given me a Nero image of the ISO. I Was hoping that I could take the easy way out and upgrade from the Dapper install :(

upgrading wouldn't be easier--you can only upgrade one release at a time. (you'd have to go dapper-->edgy-->feisty).

I don't know what exactly the problem is you're having burning the iso, but Feisty would be you're best bet if you can manage it.  You burned the feisty iso to CD as an image but you can't boot from it??

---

### Post by joe.turion64x2 on 2007-08-06
> **logos34 said:**
> upgrading wouldn't be easier--you can only upgrade one release at a time. (you'd have to go dapper-->edgy-->feisty).

I don't know what exactly the problem is you're having burning the iso, but Feisty would be you're best bet if you can manage it.  You burned the feisty iso to CD as an image but you can't boot from it??
Perhaps he burnt only a big file named Ubuntu.iso in the main folder, that or either the cd or the image is corrupt.

The conclusive test from my point of view is if you can plug any other IDE hard drive (one that is known to work fine) and see if it gets recognized.

Joe.

---

### Post by sp0nge on 2007-08-06
When burning the feisty ISO, I used nero. It took the file that was downloaded (ubuntu-7.04-desktop-i386.iso) and ended up saving a Nero Image file in My Documents which I burned to the CD. When the system boots to the CD, it hangs a moment then just boots up from the HDD into Windows XP. 

Back to the issue at hand, is it possible to "find" this hard drive manually to install?

---

### Post by merlinus on 2007-08-06
The image file needs to burned as such, not as a data disk. There should be an option to burn as a disk image in nero.

If you look at the contents of the cd in windows, what do you see?  If files and folders, then it is burned correctly,  If one file, then it is not.

Also, burning at 4x or less speed is best.

InfraRecorder is an open-source free cd burning software for windows:

[http://infrarecorder.sourceforge.net/](http://infrarecorder.sourceforge.net/)

-merlin

---

### Post by sp0nge on 2007-08-06
When I look at the CD it shows the one image file. My next plan is:

I'm downloading the alternate cd image now. Once complete, I will take a nother stab at burning both images to CD and try a direct install to feisty. I'm new with nero, but every time I try to burn an image, it forces me to save the image to disk somewhere. and no matter where, it saves one big file.

---

### Post by merlinus on 2007-08-06
Download and install InfraRecorder for windows.  I use it all the time for burning disk images from .iso files.

There is an option in the menu for doing this.  You have been burning data disks, not disk images.  They will never work as intended.

-merlin

---

### Post by sp0nge on 2007-08-06
Well, for a moment I was praising the recomendation, merlinus. I installed Infrarecorder and burned the image. It seemed to work, loading the kernel and opening to an Ubuntu start up page, just as the Dapper CD does. Then it hangs. The loading bar keeps running and it just hangs there.

In looking at the CD from windows now, there are several files and folders as opposed to the single image as before. 

Any more ideas?

---

### Post by merlinus on 2007-08-06
Probably video problems.  Post specs.

-merlin

---

### Post by sp0nge on 2007-08-06
Sorry, I spoke too soon! 

The frustration of 2 days of this BS has me a bit short on patience. I've gotten the feisty CD to begin the install and alas the hard drive was in fact detected. It's installing now at about 46%. 

I'll post again once complete.

---

### Post by merlinus on 2007-08-06
Yeah, patience is a great teacher, for those who have it.

:)

Also, is it not amazing how much better open-source software works compared with most of the commercial variety....

Tell yer friends!

-merlin

---

### Post by sp0nge on 2007-08-06
I am not patient by nature but have been working on that!

so I believe I've overcome this issue, and on to the next. Please see my post:

[http://ubuntuforums.org/showthread.php?t=519296](http://ubuntuforums.org/showthread.php?t=519296)

I'll look forward to your help, much appreciated for the recommendation and support this far!

---

