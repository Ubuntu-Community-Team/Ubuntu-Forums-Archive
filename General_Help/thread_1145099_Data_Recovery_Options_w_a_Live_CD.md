---
title: "Data Recovery Options w/ a Live CD"
date: 2009-05-01
forum: General Help
---

### Post by DnDer on 2009-05-01
My friend's Windows computer crashed a few hours ago. I managed to drop off a copy of Ubuntu (I think it's Heron, if that makes a difference) before I vanished to work.

I don't have a distro in front of me to explore, or I'd not have to bother you guys (sorry!), but once the live CD is loaded, can my friend take the CD out and put in a DVD (or CD) to burn recovered data onto? Does ubuntu have that kind of support, or will I have to have them try to get an app from somewhere to do this?

TIA for the help, and extra cookies for fast replies. I'm baking a whole batch if people want some.

---

### Post by prem1er on 2009-05-01
No, ubuntu is actually running off of the CD so it cannot be removed.  I know there is an option for knoppix to load the cd to ram so that it can be removed, but I don't think ubuntu has that option.  If there is no external device available to write to, I suggest burning a knoppix cd and loading it to memory and then writing the recovery data to another cd.

---

### Post by DnDer on 2009-05-01
How complicated is an Ubuntu installation? I've only ever had cause to use live CDs before now. And if my friend installs it... what happens to the windows partitions and data contained therein? 

(Don't worry, I'm also going to look at the FAQs, too. I'm just slow at research.)

Knoppix is not an alternative at this point. I wish it were, but windows doesn't boot, so they couldn't download a copy and burn it now. I'm also not sure they have the experience or knowledge base to run/install it. :(

---

### Post by prem1er on 2009-05-01
As long as there is enough space left on the drive, ubuntu will not overwrite any of the windows files.  However, it seems as if the person recovering the data has limited knowledge of Ubuntu, so I definitely DO NOT suggest trying this.  Anything could go wrong and the data would be even harder to recover.

---

### Post by ucjb on 2009-05-01
Create a bootable usb flash and boot to it move the files from the hard drive to the usb drive.

---

### Post by prem1er on 2009-05-01
> **ucjb said:**
> Create a bootable usb flash and boot to it move the files from the hard drive to the usb drive.

If there was a flash drive available he could have just used the live CD and wrote to the flash, but I don't think there is one?

---

### Post by DnDer on 2009-05-01
Found this: [http://www.psychocats.net/ubuntu/dualboot]("http://www.psychocats.net/ubuntu/dualboot")

I can't tell what version of ubuntu he's loading from the screen shots. Kernel 2.6.27 tells me it's not Jackalope (that uses .28, right?), so I should be okay doing this.

They don't know what they're doing, but I've got enough background to be comfortable in walking them through the procedure as long as I know it's the right procedure.

---

### Post by DnDer on 2009-05-01
Sorry, no flash drive. I wish it were that easy. >_<

---

### Post by Sef on 2009-05-01
> How complicated is an Ubuntu installation? I've only ever had cause to use live CDs before now. And if my friend installs it... what happens to the windows partitions and data contained therein?

1) If you tell Ubuntu to use the whole disk, it will overwrite Windows, and the information will be lost.

2) You can dual boot by [manually partitioning]("http://psychocats.net/ubuntu") the hard drive.

---

### Post by prem1er on 2009-05-01
> **DnDer said:**
> Found this: [http://www.psychocats.net/ubuntu/dualboot]("http://www.psychocats.net/ubuntu/dualboot")

I can't tell what version of ubuntu he's loading from the screen shots. Kernel 2.6.27 tells me it's not Jackalope (that uses .28, right?), so I should be okay doing this.

They don't know what they're doing, but I've got enough background to be comfortable in walking them through the procedure as long as I know it's the right procedure.

Yes, this is a how you would do it.  One thing to warn about, since you are not able to boot windows and defrag the hard drive some data might become corrupt when you are repartitioning.  I believe there are tools available for ubuntu that can defrag a ntfs drive, so I suggest you look into that before continuing.  Lastly, make sure the partition is exactly what you want before writing the changes.

---

