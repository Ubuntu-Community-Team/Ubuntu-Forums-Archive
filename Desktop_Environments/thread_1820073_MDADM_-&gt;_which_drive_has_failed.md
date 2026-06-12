---
title: "MDADM -&gt; which drive has failed?"
date: 2011-08-07
forum: Desktop Environments
---

### Post by Neo_x on 2011-08-07
Hi guys

I know this is probably a very generic linux question, but since i am using ubuntu  - i thought it safer to ask here.


I have jumped into the deep end of linux - and i am afraid that i will be forced to swim sooner rather than later.

Let me start at the beginning -
I am and probably will be a windows fan for a long time :P - let me not list the reasons - or else you guys will probably hang met out to dry :P -
the one thing i have discovered - is that windows sucks in generating a software RAID - especially the RAID 5 that i was looking for
any case- after loosing plenty data via windose - i decided to attempt linux/ ubuntu

I must say - so far so good. I used this excellent guide :
[http://ubuntuforums.org/showthread.php?t=517282](http://ubuntuforums.org/showthread.php?t=517282)

and must say that the raid is performing admirably - i am currently busy adding/growing the 12th 1Tb drive onto the RAID, and no issues so far(some other major WOW advantages i have noticed... like speed writing too and reading from the RAID.. :D)

But.. :(  - that is where my knowledge of linux stops  - so i am sorry for troubling you okes with some possible dumb questions :P)

*i am even ashamed to say that i am not exactly sure which version of ubuntu is running - after the latest upgrade to unity? ubuntu 11 - i just cant make my way around the interface anymore * :(

see below MDstat output[INDENT]***cat proc mdstat***

***Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] ***
***md0 : active raid5 sdl1[11] sdj1[10] sdb1[1] sdm1[6] sdk1[2] sdi1[8] sdh1[0] sdg1[3] sdf1[4] sde1[9] sdd1[5] sdc1[7]***
***      9767599360 blocks super 0.91 level 5, 64k chunk, algorithm 2 [12/12] [UUUUUUUUUUUU]***
***      [==========>..........]  reshape = 50.7% (495864576/976759936) finish=1482.0min speed=5407K/sec***

***unused devices: <none>***
[/INDENT]My questions :


[LIST]
[*]if one drive fails on the array(for example SDK1) - how the heck do i determine which physical hardware device it is that has failed?  (without compromising the other data - yes unfortunately i cant afford to backup 11TB of data - personal server ;) )
[LIST]
[*]Please keep in mind - i don't have space in the box for a mouse - not even talking about a hot spare drive - thus adding the backup drive before removing the faulty drive is rather difficult - but if that's the only option i will have to keep with that
[*]as everybody know RAID5 is only 1 drive backup - so partly i would like to solve the issue as quick as possible -without having to resort to disconnecting one drive at a time to determine which is which.
[LIST]
[*]if the drive assignments ( SDA/SDB/SDC) is constant -i would appreciate a "safe"/quick method to determine which is which - i can probably then mark the cables/drives with the names?
[/LIST]
 
[/LIST]
 
[*]what is the most intuitive/fast way to determine that a faulty drive exist in the array? - ie is there some sort of GUI solution for MDADM that will tell me the moment that a drive has turned faulty? - The box is currently not on the internet -meaning notification via email is not possible
[*]Is there a non-destructible way to convert the RAID-5 to RAID-6? ( i would rather sacrifice 1TB of free space - for peace of mind) - and RAID6 will make troubleshooting a bit easier since 3 drives will have to fail before data-loss
[/LIST]



Thank you for your patience with a complete nooblet :)

Neo_X

---

### Post by SeijiSensei on 2011-08-07
At a prompt, type "cat /proc/mdstat".  You'll see a list of "U"'s like you've shown above.  If a drive fails, the U is replaced with an underscore.  The U's appear in the order of the component partitions listed above it.  If the third U were replaced with "_", it would mean the third component partition has failed, /dev/sdb1 in your case.

You can have mdadm monitor the array and send you an email if something goes awry.  Type "mdadm --monitor --help" at a prompt for details.  The simplest method is to add a line to /etc/rc.local like this:

```
/sbin/mdadm --monitor --mail=you@example.com /dev/md0 &
```

This monitors /dev/md0 and sends an email to [email]you@example.com[/email] if something is wrong.  You need a separate command for each array to be monitored.

---

### Post by Neo_x on 2011-08-07
> **SeijiSensei said:**
> At a prompt, type "cat /proc/mdstat".  You'll see a list of "U"'s like you've shown above.  If a drive fails, the U is replaced with an underscore.  The U's appear in the order of the component partitions listed above it.  If the third U were replaced with "_", it would mean the third component partition has failed, /dev/sdb1 in your case.

You can have mdadm monitor the array and send you an email if something goes awry.  Type "mdadm --monitor --help" at a prompt for details.  The simplest method is to add a line to /etc/rc.local like this:

```
/sbin/mdadm --monitor --mail=you@example.com /dev/md0 &
```This monitors /dev/md0 and sends an email to [EMAIL="you@example.com"]you@example.com[/EMAIL] if something is wrong.  You need a separate command for each array to be monitored.

Hi Sensei

Thx for the details - much appreciated :)

as explained i am rather struck to discover an unobtrusive way to find out which exact drive is SDB1 for example - ie once i determine via MDADM which drive it is faulty - i want to power down the box - remove that exact drive and replace with a working drive. taking out the wrong drive will leave the RAID inoperable (ie taking out a working drive in a RAID-5 already with one failed drive is a disaster.)

unfortunately i don't have internet on the box, so an automated email a bit of an issue.

---

### Post by fjgaude on 2011-08-07
Wow, I must say without a full backup to your data sooner or later you are going to lose all of it. Take it from one who has been around for a long, long time. RAID is not the answer to backups. I use three levels to protect my graphic designs.

Good luck!

---

### Post by Neo_x on 2011-08-08
yup understood backup is better  - :) - but understanding my RAID is a step in the right direction. :)

Any other help please guys?

---

### Post by jupiter14 on 2011-08-08
I dont create any back up never ,.........may be i will teach this lessons , after facing this lesson :p

---

### Post by coffee412 on 2011-08-08
> i am rather struck to discover an unobtrusive way to find out which exact drive is SDB1Drives are listed as they appear on the bus. On your motherboard or controller there is documentation on what SATA port is what. They are numbered basically. The numbering will follow this pattern:

SATA0 is sda
SATA1 is sdb
SATA2 is sdc

sdb1 is your second drive and first partition.

ect...

But it is alot easier to label the drive(s) and keep track of them than have to refer to documentation that might be missing in the future. 

So, I would suggest refer to your documentation on your controller or motherboard and then get a ink pen and some stickers and label your drives. In the future it pays off.

coffee

---

### Post by Neo_x on 2011-08-09
> **coffee412 said:**
> Drives are listed as they appear on the bus. On your motherboard or controller there is documentation on what SATA port is what. They are numbered basically. The numbering will follow this pattern:

SATA0 is sda
SATA1 is sdb
SATA2 is sdc

sdb1 is your second drive and first partition.

ect...

But it is alot easier to label the drive(s) and keep track of them than have to refer to documentation that might be missing in the future. 

So, I would suggest refer to your documentation on your controller or motherboard and then get a ink pen and some stickers and label your drives. In the future it pays off.

coffee


ok thank you :)

that makes sense - although the minor issue is that i am using ports on the board as well as on SATA controllers ( if memory serves 6 sata ports on the MB and then another 7 spread over two 4port SATA controllers

is there a way to stop the RAID from trying to initiate ?

ie then i could probably disconnect a drive at a time(probably while the box is powered down?) and mark it as it shows up missing?


anycase- a more critical problem now (and it seams to contradict what you said on top where it being physically related to the SATA ports.)


this morning Murphy decided to join the party


It seems that one of the drives failed(and as per Sensei's help - the underscore seams to be the third drive)

problem is - upon system restart - the order of the drives seems to change every time :(

see the cat /proc/mdstat output with a system restart in between each
[I][B]OUTPUT1
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sda1[3] sdc1[8] sdl1[9] sdm1[4] sdb1[0] sdk1[5] sdj1[7] sdi1[1] sdg1[6] sdf1[11] sdd1[10]
      10744359296 blocks level 5, 64k chunk, algorithm 2 [12/11] [UU_UUUUUUUUU]

*RESTART*

OUTPUT2
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdh1[10] sdc1[7] sdj1[11] sdk1[6] sdm1[4] sdd1[5] sdl1[9] sdg1[8] sdf1[0] sde1[3] sdb1[1]
      10744359296 blocks level 5, 64k chunk, algorithm 2 [12/11] [UU_UUUUUUUUU]
      
unused devices: <none>

*RESTART*
OUTPUT3
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdf1[11] sdd1[10] sdg1[6] sdl1[9] sdm1[4] sdk1[5] sdi1[1] sdj1[7] sdc1[8] sdb1[0] sda1[3]
      10744359296 blocks level 5, 64k chunk, algorithm 2 [12/11] [UU_UUUUUUUUU]

[/B][/I]
This is extremely odd-  furthermore - (verified via gparted ) - even my 500GB system drive seems to change position every time round. (ie if memory serves during output 2 the system drive was SDA1, during output 3 gparted listed it as SDH1)

analyzing output1 / output2/ output 3

even though i have 12 drives in the array(from SDA up to SDM - 12 + 1 system) (as per the ***UU_UUUUUUUUU) ***, the list of partions seems to only contain 11. issue is - each time around another one is missing
output 1 -  SDE1 and SDH1  ( not sure which one was the system partition during that capture :(

output2 - SDA1 (system) and SDI1

output3 -  SDE1 and SDH1(system)


the above results confuses me blind - basically because it cant be that a different drive fails during each restart(the data is still accessible on the RAID -for now:P).
 It rather seems that the drives is labelled differently after each power cycle(especially when tracking the system drive), which means i am stuck between a rock and a hard place - 
how the hell do i determine which drive failed??


any help will be greatly appreciated :)

*after thought* After some coffee ;) -  output 1 and 3 seems to be the same. but still not trusting why output 2 changed.
for the time being - can someone please assist - once located - i think it safe to remove the drive from the array (and shrink it) before finding the physical hardware(
although now that i mention it - gparted shows all the drives active... - meaning whichever drive it is , its not completely dead- is there some thorough testing that can be recommended to determine if a drive is faulty or not?)

*progress*
i added SDE1 again to the array, and the array started rebuilding again - 24hours to wait :O

---

### Post by coffee412 on 2011-08-09
Normally in a situation where a drive has failed in a rather large raid setup there is info about the failed drive that can be displayed to help identify it. The basic idea is to identify the drive and shutdown the system and replace it. Then when the system comes back up you can add the new drive to the array.

Correct me if Im wrong:

In the case of having an extra sata controller card in your box and using both the onboard and extra card for array drives - The first sata device (/dev/sda) will be from which ever controller that you boot from first. So, If you boot from your sata controller card instead of the onboard (in motherboard) then you will see a change in the discriptions of the drives (they change sda,sdb ect..). 

You have a bad drive out of say - 12. Which one is it???

Check your logs (/var/log/messages) for entries about the failing drive. Remember NOT to reboot and if you did reboot you will have to look at an entry for the bad drive after the reboot. When you see the failing drive you can take its discription and use it with hdparm to find the serial number of the failing drive. Then shutdown the system and replace the drive.

Example: My drive /dev/sde is failing! Which drive is it???
> sd 7:0:0:0: [sde] 625142448 512-byte logical blocks: (320 GB/298 GiB)
sd 7:0:0:0: [sde] Write error, I/O error 
sd 7:0:0:0: [sde] Mode Sense: 00 3a 00 00
sd 7:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 sde: sde1
sd 7:0:0:0: [sde] Attached SCSI disk
> hdparm -i /dev/sde
[root@dino coffee]# hdparm -i /dev/sde

/dev/sde:

 **Model=ST3320620AS, FwRev=3.AAD, SerialNo=5QF0GH2R**
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=16384kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=625142448
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: Unspecified:  ATA/ATAPI-1,2,3,4,5,6,7

 * signifies the current active mode
Fine, I know that drive /dev/sde has errors and that its serial number is 5QF0GH2R. I will shutdown now and look for the drive and replace it. Bring the system up again and add the replacement drive back to the array.

done.:D

---

### Post by Neo_x on 2011-08-09
> **coffee412 said:**
> Normally in a situation where a drive has failed in a rather large raid setup there is info about the failed drive that can be displayed to help identify it. The basic idea is to identify the drive and shutdown the system and replace it. Then when the system comes back up you can add the new drive to the array.

Correct me if Im wrong:

In the case of having an extra sata controller card in your box and using both the onboard and extra card for array drives - The first sata device (/dev/sda) will be from which ever controller that you boot from first. So, If you boot from your sata controller card instead of the onboard (in motherboard) then you will see a change in the discriptions of the drives (they change sda,sdb ect..). 

You have a bad drive out of say - 12. Which one is it???

Check your logs (/var/log/messages) for entries about the failing drive. Remember NOT to reboot and if you did reboot you will have to look at an entry for the bad drive after the reboot. When you see the failing drive you can take its discription and use it with hdparm to find the serial number of the failing drive. Then shutdown the system and replace the drive.

Example: My drive /dev/sde is failing! Which drive is it???
Fine, I know that drive /dev/sde has errors and that its serial number is 5QF0GH2R. I will shutdown now and look for the drive and replace it. Bring the system up again and add the replacement drive back to the array.

done.:D

wrt to booting - i have the system drive connected to the motherboard during each boot on the exact same position - not sure why the anomaly of it changing SD assignment. 
*i will have to verify this just to be sure - i normally connect my boot/system drive to the most reliable port - ie motherboard. *

with regards to the serial number -

:D

ten thumbs up for that post :)

very good idea - and a definite way to track the problematic drive. :)


One final question - is at all possible to convert a working RAID5 to a working RAID6?

---

### Post by coffee412 on 2011-08-09
> One final question - is at all possible to convert a working RAID5 to a working RAID6?Yes you can. You will have to have 2 hot spares to perform this. I have not ever had to do this and I would backup the raid before you attempt it. 

The difference between raid5 and 6 is that there is one more parity block on the drives in raid6. 

Here is some good read on it if your going to attempt this. Keep in mind that raid6 will decrease your available storage because of the extra parity block.

[http://blog.serverhorror.com/2011/01/27/migrating-raid-levels-in-linux-with-mdadm/](http://blog.serverhorror.com/2011/01/27/migrating-raid-levels-in-linux-with-mdadm/)

coffee
[U]
Do not forget to change your /etc/mdadm.conf file after the change to raid6
[/U][ ]("http://ubuntuforums.org/newreply.php?do=newreply&p=11134153")

---

### Post by Neo_x on 2011-08-09
> **coffee412 said:**
> Yes you can. You will have to have 2 hot spares to perform this. I have not ever had to do this and I would backup the raid before you attempt it. 

The difference between raid5 and 6 is that there is one more parity block on the drives in raid6. 

Here is some good read on it if your going to attempt this. Keep in mind that raid6 will decrease your available storage because of the extra parity block.

[http://blog.serverhorror.com/2011/01/27/migrating-raid-levels-in-linux-with-mdadm/](http://blog.serverhorror.com/2011/01/27/migrating-raid-levels-in-linux-with-mdadm/)

coffee
[U]
Do not forget to change your /etc/mdadm.conf file after the change to raid6
[/U]

Than you very much! will virtualize it as suggested and test it out - backup is always a good idea :)

I am running a RAID-6 on a dedicated controller on my other machine , so i am aware of losing two partitiions/drives due to parity

will keep you updated if i encounter any other issues - still waiting for the drive to rebuild :P

thx again for the help

---

### Post by tekknoir on 2011-08-09
To see which drive has failed, type this

# mdadm --detail /dev/md0 

to see valid superblocks, type this

# mdadm --examine /dev/sdX1  #where x is the drive letters

or shortcut
# mdadm -E /dev/sd[abcdef]1   # lists sda1 through sdf1

now to figure out where it is on the controller, you can type
# sudo apt-get install smartmontools
# smartctl -d sat -a /dev/sdX # get the serial number, where X is failed SATA drive.

if using a 3ware controller
# smartctl -d 3ware,X -a /dev/twa0  #where X is the port# on the card.

poweroff the server and find the matching drive via the SN#.

---

### Post by rickyrockrat on 2012-09-25
Do this:
ls -l /dev/disk/by-id/|grep sdc

Replace sdc with the filed drive from the array.

The link names should give you the manufacturer and device name.
Or try:
info --query=all --name=/dev/sdc

I know...I'm posting to a year old thread. The above solutions just seem a bit complicated and don't give you full info.

---

