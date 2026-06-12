---
title: "Dual-boot OS w/out Formatting HDD"
date: 2011-04-14
forum: Desktop Environments
---

### Post by qzpac on 2011-04-14
Can i dual-boot OS without **[COLOR=Black]formatting[/COLOR]**:
1. Install a trial windows server 2008 standard 
2. Next install Ubuntu 11.04 

After my trial windows server expired, will use Ubuntu 11.04 as main OS without formatting my entire hard disk. Will this work as i have only 1 sata hard disk?

---

### Post by cscj01 on 2011-04-14
> **qzpac said:**
> Can i dual-boot OS without **[COLOR=Black]formatting[/COLOR]**:
1. Install a trial windows server 2008 standard 
2. Next install Ubuntu 11.04 

After my trial windows server expired, will use Ubuntu 11.04 as main OS without formatting my entire hard disk. Will this work as i have only 1 sata hard disk?

Yes and no.

You will need to partition the drive into one partition for Windows Server and one unassigned partition.  You can then install Windows Server on the first partition and Ubuntu into the second partition.  However, Ubuntu will require a different file system than Windows Server, so the second partition will need to be formatted (ext3 or ext4).

I am assuming the Windows Server partition is already partitioned.

If the Windows Server partition is using the entire drive, you will need to shrink that partition to create the second partition for Ubuntu.  You can do this with a Ubuntu Live CD using gparted or a Gparted Live CD

---

### Post by oldfred on 2011-04-14
The version of windows you install and the version of Ubuntu you install only differs in details. How you partition drive for servers may differ more than for standard desktops.

With Ubuntu you can have the server version that does not have a gui so that can be a big detail, but you can add gui to a server install or server standard packages to a desktop install.

Once windows expires you can reformat partition and make it a data partition for Ubuntu.

Dual Boot Win7 & Ubuntu
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu)
Alternate install example win 10.04:
[http://members.iinet.net.au/~herman546/p2.html]("http://members.iinet.net.au/%7Eherman546/p2.html")

---

### Post by qzpac on 2011-04-18
HI oldfred,
[B][I]
Once windows expires you can reformat partition and make it a data partition for Ubuntu.[/I][/B]

How should i reformat windows partition and make Ubuntu the data partition without formatting my hard disk?  Will these steps format and delete away my entire hard disk data?

---

### Post by XsheepX on 2011-04-18
Not sure if Windows will let you install to a partiiton and not the entire hard drive. If not, why not just install it to a flash drive or something? If it does let you, the MBR would overwrite GRUB, but you could still run a live disc and reinstall GRUB over the MBR, I think.

---

### Post by oldfred on 2011-04-18
I was suggesting just converting the NTFS partition that win7 was in to a /data or if you have not created /home as part of your install you can make it /home. You just reformat the windows partition(s) from NTFS to ext3 or ext4.

You can use gparted or the command line to reformat a partition.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

You create partitions and format partitions not entire drives unless your drive is all one large partition. Old floppy drives, some USB may be formated in floppy mode which does not have partitions.

---

### Post by Leppie on 2011-04-18
why not download vmware player and install windows 2k8 in a virtual machine?

---

