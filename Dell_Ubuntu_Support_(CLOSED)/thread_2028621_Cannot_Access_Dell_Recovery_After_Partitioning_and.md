---
title: "Cannot Access Dell Recovery After Partitioning and installing Ubuntu"
date: 2012-07-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sherpa1d on 2012-07-18
Dell Studio 1558 Windows 7
 
(sorry for spelling and grammer, typing on a cell phone) So I got my laptop and thought in the future I would migrate to Linux. I re-paretioned the laptop leaving the dell utilities and dell recovery partions in place. Reallocated space from pirmary (windows) and created 2 new partions, loaded Ubuntu on one of those. During install Ubuntu took over as boot manager (GRUB). Created the 2nd new partion as general storage so I could access from Windows or Ubuntu.
 
Time has gone by and realised I cannot us Linux for my graphics needs and I did not allocate enough room to Windows so that partion is getting full. I decided to just restore back to factory image and start over. When I try F8 at boot I get nothing, it will not start any recoovery options. I decided I would try Datasafe and create restore DVD/s When I run it and it asks to incert my DVD it then says the harddrive (not DVD) does not have enough room to complete the operation, I checked and have 5-gig avalible on my windows partion. I searched and have seen a few people say they have gotten this same error and some have attributed this to not haveing the recovery partion any more.
 
I openned Disk Manager in Windows and can see all of the partions avalible including the Dell Utilites and Dell Recovery (so they do exist). I loaded Ubuntu and went into it's version of Disk Manger and can Mount the recovery partion and it hase all of the necessary files. I search net for other options and saw to create a Windows PE disk with Imagex and use it to start the Dell image from the Recovery Partion. I created the CD and booted it up. The instructions say to verify you are working with the correct drives so I did a DIR of each drive and do not see the Recovery Partions. I tried every drive letter from A to I and never found the recovery partion so I can't load the image that way. 
 
In my searching of the net I stubbled accross a page at work and cannot find it now that said something about if you repartion a dell laptop it will keep the computer from working with the recovery partion but I can't find this page again. So I looked to see how to unistall linux and found this page [http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/](http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/) I skipped the delete the linux partions (maybe this was a mistake) and ran the repair cd and did the bootrec /fixmbr and bootrec /fixboot steps. The fixmbr said ran fine but fixboot came back with an error. So, upon rebooting laptop it would only load now into the Dell Utilites partion and runs the diagnostic tools. I can't couldn't even get the linux boot loader up (GRUB). So I booted up with a Linux DVD and openned it's DiskUtilites and saw that the Dell Utilites drive was marked as active boot drive. I unchecked it as a boot drive and tried marking the recovery as a boot drive, just figgured what the hell. The computer just kept thinking so I rebooted and it came up to message "Cannot find Operationg System" I am sure this is do to no partion being marked as a boot drive. At that point I had to quit and go to bed.
 
Does anyone have any ideas? I think setting the Linux partion as the boot drive may at leaset get me back into the computer, I don't know. I really need to get to the recovery partion, I know it is there. I'm really affraid to delete the Linux partion as it says in the link, but I don't know. Is it because I have all of the partions that the computer won't see the recovery partion so that is why F8 doesn't work? Can I make recovery disks from Linux while booted with a Linux CD?

---

### Post by dave61430 on 2012-07-21
You've included so much stuff it's hard to follow. I ran into a problem trying to remove the recovery partition.
Terabyteunlimited have a partition, multi-boot and imaging program called bootitbm. You can use a trial to look at the system. 
They also have a knowledge base that covers a lot of material regarding installation of linux, problems with grub etc. Log on to their site and read some of the relative articles including fixing BCD etc.

---

