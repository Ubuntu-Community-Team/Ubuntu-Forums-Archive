---
title: "VirtualPC VM on Ubuntu"
date: 2007-08-03
forum: Desktop Environments
---

### Post by muecker on 2007-08-03
I hate to even ask this question because it seems hypocritical, but I need to ;)  Is it possible to run a Microsoft Virtual PC VM under Linux?  I have been assigned to work with another team and they use Virtual PC for emulation.  They have a VM I need to work with and install stuff on so I will need to run Virtual PC to do it.

Even stranger question.  Will Virtual PC run within a VMWare VM?  I have a Windows 2000 VM I use frequently.

---

### Post by mtbsoft on 2007-08-07
dup.

---

### Post by mtbsoft on 2007-08-07
In a word... Yes!

You will need to install VMPlayer in your Windows environment and open/run the VM at least once using it to perform the conversion - make sure to completely shutdown (not suspend/hibernate) the VPC before you do this.  Once you've run it under the Windows VMPlayer you can then copy all the files to a FAT32 common/shared area and can then use the Linux VMPlayer to open it.

What is more is that you can close the VM down in Linux and reopen it under VPC on Windows, all the changes will be there - neat, huh?  Just remember: going between Linux and Windows copies of VMPlayer you don't always have to completely shutdown the VM but you do when going between VPC and VMWare.  

I've been doing this for a few months now and had no problems.  Any other questions... just ask.

You cannot run an emulator within an emulator, so VMWare within VPC and/or VPC within VMWare is a no-go.

---

