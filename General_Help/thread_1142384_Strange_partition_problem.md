---
title: "Strange partition problem"
date: 2009-04-29
forum: General Help
---

### Post by Tytanium on 2009-04-29
Hey guys,

Here is my problem which i will try and be as detailed as possible when describing.

I have a 320gb IDE hard drive which i was using for data storage externally via USB enclosure.When i first set it up I partitioned it into a single NTFS logical partition and all was well and i had no issues what so ever.One day my now ex girlfriend needed to have her laptop formatted and have WindowsXP reinstalled but first the data that she wanted to keep needed to be backed up which i offered to do for her.When the time came to perform the backup I plugged my drive into the USB and it accessed like normal so i started copying her data to it and all of a sudden got an I/O error and the drive vanished and would not appear again.Later we went to my house and i tried it on my desktop which is dual boot Ubuntu/WinXP and achieved the same result under both OS's,still would not access correctly directly plugged to IDE or through USB which this of course worried me since i have loads of valueable data on it(all this was a few months ago and i took a break from it until tonight).I started trying partitioning softwares like Partition Magic and Acronis disk director,etc just to see the status of the partition and it is there but with a MBR/BS error so i did some searching and came across testdisk.Using testdisk(under Ubuntu) i used the quick partition search and the partition showed up but as being deleted so i also ran the deeper search and here is what i am trying to wrap my head around, my originally single ntfs partition seems to have been magically split up into multiple partitions of 320gb and testdisk currently tells me the boot sector and all that is ok and matching for the partition on the top of the list plus i can see a few of my files when i press "p" BUT its only about 5% of them if that.As for the other partitions that show up in the list, i can't seem to get any of them to access through testdisk eg. listing my files,etc plus the status says that its bad so i am not quite sure what to do.So as we speak i am using Photorec and backing up whatever files it finds to another harddrive and so far it has found a lot and has copied them and they work BUT i would still like to attempt to restore the partition once Photorec is finished so can save the hassle of renaming and sorting every file and so i can make another backup just to make sure i have EVERYTHING.Am I screwed or is there still a way to get testdisk to work the way that i want it to?. I hope my post makes sense and does not confuse anyone. Thanks in advance :) .

---

### Post by blackmail on 2009-04-29
Your problem is that your mft or mbr is messed up, please try to find a way to edit your mbr, or your mft, later i will come back and tell you what i have found.
I knew a way to edit the mbr, in hex but that is not helpfull, since it has only uses in writing mallicious code.
hope it was at least a minor help
best regards

---

### Post by blackmail on 2009-04-29
oh yes please try photorec, i just remembered that it attempts a non file system bependent recovery it might work, if you installed testdisk just type
```
sudo photorec
```
and it should help you.
if it is of any help the hint was given to me when you said that you had many 320 gb partitions and your files where missing.
maybe your hdd overheated or something happened and when you recived the i/o error things got messed up
best regards

---

### Post by Tytanium on 2009-04-29
Thanks for the reply.

Not to discount that heat could be a factor but in this situation i don't think it was as it happened maybe like 5 mins after turning the external enclosure on.I have been running Photorec for the past couple of hours and it is almost complete but i would still like to figure out how to utilize testdisk properly as i am not sure what else to do.The data is obviously there still since photorec is recovering it so there must be a way to resurrect the partition using testdisk.

---

### Post by caljohnsmith on 2009-04-29
Tytanium, how about first posting the output of:
```
sudo fdisk -lu
```
Also, what version of testdisk are you using? Versions prior to 6.10 do not read the NTFS partitions reliably, so in my experience it is helpful to make sure you are using the latest version of testdisk, which is 6.11. How about downloading the [testdisk-6.11.1.linux26.tar.bz2]("http://www.cgsecurity.org/testdisk-6.11.1.linux26.tar.bz2") package to your desktop, and then do:
```

cd ~/Desktop
tar xvf testdisk-6.11.1.linux26.tar.bz2
sudo testdisk-6.11/linux/testdisk_static
```
After starting testdisk with the above command, choose "No Log", select the correct HDD and then "Proceed", "Intel", "Analyze", "Quick search", "N" to search for Vista partitions, hit enter to continue, select "Deeper Search" so it does a deeper search, which could take a while. Please post the output of the screen that has the deep search results. Also, use your up/down arrow keys to select each partition listed in the deep search results, and press "p" to get a directory listing; please let me know exactly which partitions give you a directory listing, and also which of those partitions seem to be your existing NTFS partition. We can work from there if you want.

---

### Post by Tytanium on 2009-04-29
Here ia the output that sudo fdisk -lu gives me.

Disk /dev/sda: 17.2 GB, 17280442368 bytes
255 heads, 63 sectors/track, 2100 cylinders, total 33750864 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3d233d23

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    33505919    16752928+   7  HPFS/NTFS
/dev/sda2        33511590    33543719       16065    f  W95 Ext'd (LBA)

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe38c7189

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *       16065   625137344   312560640    5  Extended
/dev/sdb5           16128    49464134    24724003+  83  Linux
/dev/sdb6        49464200   625137344   287836572+   7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
240 heads, 63 sectors/track, 41345 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0bdfe3ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1           15120   268425359   134205120    f  W95 Ext'd (LBA)
/dev/sdc5           15183   268425359   134205088+   7  HPFS/NTFS


sdc is the drive with the partition i would like to restore. Fdisk shows the heads as being 240 , while testdisk reports them to be 255

TestDisk 6.11.2, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sdc - 320 GB / 298 GiB - CHS 38913 255 63
Analyse cylinder 31881/38912: 81%


  HPFS - NTFS              0 241  1 16708 179 63  268410177 [STORAGE 2]

This is the output for deeper search

TestDisk 6.11.2, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sdc - 320 GB / 298 GiB - CHS 38913 255 63
     Partition               Start        End    Size in sectors
D HPFS - NTFS              0 241  1 16708 254 63  268414902 [STORAGE 2]
D HPFS - NTFS              1   1  1 38912 254 63  625121217
D HPFS - NTFS              1  61  1 16708 254 63  268410177

The only partition in that list that will actually list any files when i press "p" is [STORAGE 2] and it shows only a few files. When i try the "p" command on the others i end up with

TestDisk 6.11.2, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

     HPFS - NTFS              1   1  1 38912 254 63  625121217



Can't open filesystem. Filesystem seems damaged.


and


TestDisk 6.11.2, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

     HPFS - NTFS              1  61  1 16708 254 63  268410177



Can't open filesystem. Filesystem seems damaged.

I also recieve this after the scan completes

TestDisk 6.11.2, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Disk /dev/sdc - 320 GB / 298 GiB - CHS 38913 255 63

Warning: the current number of heads per cylinder is 255
but the correct value may be 240.
You can use the Geometry menu to change this value.
It's something to try if
- some partitions are not found by TestDisk
- or the partition table can not be written because partitions overlaps.

I am not sure of what i need to do and if i am screwed or not.
Hopefully i have posted enough output information.

---

### Post by caljohnsmith on 2009-04-29
Before proceeding with testdisk, have you tried mounting the existing partition on your USB drive to see what happens? It's probably a long shot, but how about trying:
```
sudo mount -t ntfs-3g -o force /dev/sdc5 /mnt && ls -l /mnt
```
Does that give you a directory listing, or does it return an error? 

John

---

### Post by Tytanium on 2009-04-29
> **caljohnsmith said:**
> Before proceeding with testdisk, have you tried mounting the existing partition on your USB drive to see what happens? It's probably a long shot, but how about trying:
```
sudo mount -t ntfs-3g -o force /dev/sdc5 /mnt && ls -l /mnt
```Does that give you a directory listing, or does it return an error? 

John

I currently have it connected directly to my IDE channel but i will try it anyways and post my results.

*EDIT*

Tried to mount it and still seeing the same files that testdisk was showing me which isn't even close to what was originally there.

---

### Post by caljohnsmith on 2009-04-30
Based on the results you've shared, unfortunately it doesn't sound like testdisk will be able to help you completely recover the partition, so your best bet is probably software that can directly dig the files off the HDD such as "photorec" like blackmail all ready recommended. Best of luck with your file recovery efforts with photorec, and keep us posted about how that goes. 

John

---

### Post by Tytanium on 2009-04-30
I have already used photorec and recovered all that i could BUT there are a few specific file types that i would like to recover. mainly .rfl (reason refill). There is a strange thing happening though. Windows is able to access the drive and i have access to some data but it isn't the whole partition its maybe about 127gb and not all of that is used up so its like a huge percentage of the partition is missing in action since the total size of the original partition is 320gb. I am almost positive that there is still a probability that i can get the rest back because i tried some other software under windows called active partition recovery and was able to find the partition. except it found like 10 instances of the same partition but i was able to see ALL of my data but it would not let me do anything because it said there are overlapping partitions and that i need to delete the overlapping partitions in order to proceed with restoring the partition.But i am not 100% sure how i should proceed so i have not made any attempts yet.

thanks :)

*EDIT*

Also i am wondering if the drive geometry is wrong possibly.

---

### Post by blackmail on 2009-04-30
You could try to recover the data from a windows program, i think you could have mucs more success because ntfs used by linux is not the same as the one for windows, i am not musc of a hard drive guru, but you should run an extensive test on your had drive...
I don't know the specs, but what i would do is to go to the site of the hdd manufacturer, and download a testing tool made by them, usually those are mabe for the windows platform, and to see some reviews about your hard drive because data recovery is one, but you will also have to prevent this from happening again.
For data recovery try Hiren's boot cdm google it you can download and you should have active undelete or get data back from ntfs partition, these programs where used by ohe of my friends for data recovery from a server.
best regards

---

### Post by blackmail on 2009-08-14
just wondering has any of our suggestions helped you in your crusade? Have you recovered the data? I am assuning that the mft (master file table) got messed up, my girlfriend's dad also tought he is a  computer mecanic and installed windows, and he actually "hacked" the mft, so nothing worked, photorec did some good work, the data was partially usable, but since it did a non filesystem dependent recoveri, the filenames where long hex codes, actually i think the start address of the file, and the fragmented ones where recovered in fragments. that is why i suggested a windows prog, or hiren's boot cd.

---

### Post by Tytanium on 2009-08-17
I did recover some data but hardly any of it is even usable, I used photorec and I already had tried hiren's boot cd and never had success.I think i might have to start over which sucks lol. Thanks to everyone for the advice though, i might try hiren again just incase .

---

