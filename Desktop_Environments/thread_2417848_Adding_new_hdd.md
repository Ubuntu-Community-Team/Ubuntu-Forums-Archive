---
title: "Adding new hdd"
date: 2019-04-28
forum: Desktop Environments
---

### Post by agarwaldvk on 2019-04-28
Hi Everybody


I just bought a 6 tb hdd - WD red. I connected it and partitioned, formatted and mounted  it (at this location : /sharedfiles/media_hindi_v2) it using Gparted. "sharedfiles" is a folder in root directory!

Seems to show the correct details. However, I have a couple of concerns :-
The output of the df -h /sharedfiles/media_hindi_v2

shows 5.5 tb size,used 58M and available 5.2 tb - wondering what happened to the other 500 gb of space!

The output from fdisk -l shows this :-
**Disk /dev/sde: 5.5 TiB, 6001175126016 bytes**, 11721045168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 14280B84-6BAF-489E-A93C-C416F8C99DD1

Device     Start         End     Sectors  Size Type
/dev/sde1   2048 11721043967 11721041920  5.5T Linux filesystem


Further, this drive also appears under "Devices" in the "Places" in Mate terminal whilst no other drive appears there. I have another 3 2 tb physical hdd's on this computer. So why does only this 6 tb drive show under "Devices" and none of the other 3?


As an aside, the O/S is installed on a SSD, the details for the same from fdisk -l shows this :-


Disk /dev/sdc: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x9f6c3ccf

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sdc1  *         2048 218386431 218384384 104.1G 83 Linux
/dev/sdc2       218388478 234440703  16052226   7.7G  5 Extended
/dev/sdc5       218388480 234440703  16052224   7.7G 82 Linux swap / Solaris
[B]
Partition 2 does not start on physical sector boundary.[/B]

Any idea why does it say "Partition 2 does not start..." and what can I do to fix it if at all I need to do anything?

Please let me know if there is anything else I can provide to help you all to help me. My knowledge of Ubuntu systems is quite limited, just about enough to maintain a file server at home.


Best regards


Deepak

---

### Post by oldfred on 2019-04-28
Probably most of you "missing" space is the 5% reserved space. Some is formatting & partitioning.
The 5% was for smaller drives to make sure you had a little room when drive was full to be able to boot & houseclean.
But 5% on new larger drives and on a data drive is not really required. But you still  are responsible for making sure drive does not get too full. Some working room always required.
       Also in Linux the default is to reserve 5% of the diskspace for the superuser (this can be adjusted using tune2fs -m).
sudo tune2fs -l /dev/sdd3 
For details see
man tune2fs

New 4K drives need partitions to be aligned. But you have the now 35 year old MBR partitioning and the extended partition is not directly written into. Only the logical partition(s) inside the extended  need to be aligned.
For long term planning you may want to consider converting to gpt partitioning. But best to do when totally reinstalling or new drive. I started converting all new or repartitioned drives in 2010. You have to have gpt for your large drives as MBR only goes to 2TiB. When MBR was designed GiB was not even considered a possibility for PCs, but they allocated extra space just in case and we have even exceeded that.

      
 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr) 
           
 [http://www.rodsbooks.com/gdisk/whatsgpt.html](http://www.rodsbooks.com/gdisk/whatsgpt.html) 
    
Are all your drives internal or external?
Are you labeling partitions?
Are you just automounting with file browser? Do not know details of Mate brower, but with Naulitus drives auto mounted at /media/$USER/{ either UUID or label} and /home/label will show in browser. But mounted at / or other system folders will not be shown.
Post this with drives mounted:
lsblk-f

If internal drives best to mount with fstab. If external be sure to label so mounted with label, not UUID.

---

### Post by agarwaldvk on 2019-04-28
Hi oldfred


Thanks for your response. Greatly appreicated.

The missing space appears to be 10% and not 5%. This seems to be the case with other internal drives too. All of the 2 tb drives show the size as 1.8 tb and the 6 tb as 5.5 tb. That is fine by me as long as it is available and reserved by the system for housekeeping purposes. But I will look in ot "tune2fs" for academic purposes.


Question 1
For the present, with the exception of this new 6 tb drive, since all the other 3 drives are 2 tb, is there any need to do anything as such about the type of partition being MBR?

Question 2
For my SSD on which the OS is installed, do I need to do anything about the comment that comes up about the "Partition 2 not starting at the sector boundary" in the disk -l output (reproduced for your immediate reference)


Disk /dev/sdc: 111.8 GiB, 120034123776 bytes, 234441648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x9f6c3ccf

Device Boot Start End Sectors Size Id Type
/dev/sdc1 * 2048 218386431 218384384 104.1G 83 Linux
/dev/sdc2 218388478 234440703 16052226 7.7G 5 Extended
/dev/sdc5 218388480 234440703 16052224 7.7G 82 Linux swap / Solaris

**Partition 2 does not start on physical sector boundary.**


Answers to your questions :-
1. All my drives viz 1 off 120 gb SSD, 3 off 2 tb hdd and 1 off 6 tb hdd are internal hard disk drives.
2. I normally don't label them but I don't know to be honest. I can check if you can tell me the command that I need to run to be able to see if I have labelled them.
3. All my drives are mounted with fstab. I can show the output of the file later this evening when I get home.
4. I will also show the output of the command "lsblk -f" again later this evening when I get home.


Further, any suggestion about this one :-

My 6 tb drive also appears under "Devices" in Mate terminal whilst no other drive appears there. There are three (3) other 2 tb physical hdd's on this computer. So why does only this 6 tb drive show under "Devices" and none of the other 3?

Mate appears to be similar to "Thunar". I will attach a screenshot of how the file manager appears for me just so you can see what I am talking about. The filesystem entry shows all of the drives and this new drives also appears under the heading "Devices" which tells me that the system would be seeing it differently to all of the other drives. I would like to know what and have I done something wrong with it. At the moment, this drive is blank, so I can do whatever needs to be done to address this issue.


Best regards


Deepak

---

### Post by oldfred on 2019-04-28
You can keep using MBR.
Alignment is only important for new 4K drives which you have, but also only for partitions you write into. So message on extended partition can be ignored.
I normally add label when partitioning with gparted, but often forget and then use Disks (gnome-disks). Not sure if then you have that. If using gparted you may need to use it from live installer. Not sure then if your partition tools have methods to add labels, but bet they do.

Did you run this command as I suggested?
```
fred@Bionic-Z170N:~$ lsblk -f
NAME   FSTYPE LABEL    UUID                                 MOUNTPOINT
sda                                                         
&#9500;&#9472;sda1 vfat   ESP      D966-440A                            /boot/efi
&#9500;&#9472;sda2 ext4   xenial   5c1e1a3f-261f-4da5-a0c2-8f479b3039de 
&#9500;&#9472;sda3 ext4   ISO      ab916e15-8a74-4d6e-a0b1-32718a505dc7 
&#9492;&#9472;sda4 ext4   bionic   c29fc361-ea05-420b-b919-850aeef65dd4 /
sdb                                                         
&#9500;&#9472;sdb1 vfat   ESP_B    F496-1330                            
&#9500;&#9472;sdb2 ext4   bionic_b 06cdd4fd-6a03-4880-9021-7febff21e4b1 
&#9500;&#9472;sdb3 ext4   ISO_b    c395f36d-5e02-4913-a904-e336054b2eff 
&#9500;&#9472;sdb4 ext4   backup_b dd4e4a2e-4785-4441-91b0-28234b98e625 
&#9500;&#9472;sdb5 ext4   cosmic   75f5141c-8bab-4168-8855-4bf000406680 
&#9500;&#9472;sdb6 ext4   data     f9537995-8b44-4abb-b5fb-ec27023f57b2 /mnt/data
&#9500;&#9472;sdb7 swap            3ef43e7c-8a35-4f8b-bc73-c91d6098d4cd [SWAP]
&#9492;&#9472;sdb8 ext4   disco    8402fb15-78ce-440e-8c84-828ba6a20abe 

```

Also post this:
cat /etc/fstab

---

### Post by sisco311 on 2019-04-28
You can use the x-gvfs-hide and x-gvfs-show mount options to tell the file manager which partitions/images should be displayed.

---

### Post by agarwaldvk on 2019-04-28
Hi


No, I haven't run the commands that you suggested only because I am at work at the moment.

As mentioned in my earlier response, I will provide all the details from that command and contents of fstab this evening when I get home!

I don't remember adding the lable to the drive using gparted but I do recall seeing that there was an option to add one at the time which I didn't bother filling it at the time!


Best regards


Deepak

---

### Post by agarwaldvk on 2019-04-29
Hi


Here are the details requested :-

The output from fstab :-

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=725347c6-51f3-4761-8397-fe9a6d8392bd /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c946b6ad-ddb9-47d8-88da-d39fda0af429 none            swap    sw              0       0
/dev/sda1 /sharedfiles/media_others_v1 ext4 defaults 0 0
/dev/sdb1 /sharedfiles/media_hindi_v1 ext4 defaults 0 0
/dev/sdd1 /sharedfiles/backupdata ext4 defaults 0 0
/dev/sde1 /sharedfiles/media_hindi_v2 auto nosuid,nodev,nofail,x-gvfs-show 0 0


```
The last line entry was made by Gparted mounting options interface. All the other entries for sda1, sdb1, sdd1, sde1 were manually made by me.



The output from lsblk -f is shown below :-

```
NAME   FSTYPE LABEL UUID                                 MOUNTPOINT
sda
&#9492;&#9472;sda1 ext4         f9c052d1-7238-4661-950f-0b77efa6f370 /sharedfiles/media_others_v1
sdb
&#9492;&#9472;sdb1 ext4         550ba0a7-0b53-41b8-9645-b8bc1d990187 /sharedfiles/media_hindi_v1
sdc
&#9500;&#9472;sdc1 ext4         725347c6-51f3-4761-8397-fe9a6d8392bd /
&#9492;&#9472;sdc5 swap         c946b6ad-ddb9-47d8-88da-d39fda0af429 [SWAP]
sdd
&#9492;&#9472;sdd1 ext4         44445819-31ad-4b9e-b865-b711d5490f49 /sharedfiles/backupdata
sde
&#9492;&#9472;sde1 ext4         c7aa6e4d-497e-4299-8abc-6ca3e0fd5d93 /sharedfiles/media_hindi_v2

```
Also, please find attached herewith the screenshot of file manager (I use MATE terminal). Don't understand why does the 6 tb only appear under "Devices" and not the other 3 off 2 tb drives or the SSD which has the OS on it.


Best regards


Deepak

---

### Post by oldfred on 2019-04-29
You can attach screen shots with forum's advanced editor and paperclip icon.
Please use code tags on terminal or text output to preserve formatting.

Best to use UUID to mount as they do not change. If UEFI/BIOS brings up drives in different order you will have different drive as sda or sdb etc.
You are mounting on a new folder just off /.  Normally file managers do not show those without having to drill down to / and back up to folders you have added.
Default mount of partitions not in fstab is /media/$USER/ either UUID or label. And that will show in /home. You can manually mount in /home or /media if desired. I actually mount in /mnt (some prefer / like you have done) which also is not shown in /home, but I then add links to all the folders in my /mnt/data into /home so easy to access them. You could also link your folders with your current mount in /sharedfiles.

[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
my mount:
UUID=f9537995-8b44-4abb-b5fb-ec27023f57b2 /mnt/data ext4 relatime 0 2

Your sda1 with UUID &  defaults is ok, relatime is an alternative that includes defaults see man mount for details:
         UUID=f9c052d1-7238-4661-950f-0b77efa6f370 /sharedfiles/media_others_v1 ext4 defaults 0 0

And how I link folders after data partition mounted.
for i in `echo /mnt/data/*`;do ln -s $i; done
If you just have one or two folders, you just do it like this example for my Music folder, but folder cannot exist in /home.
ln -s /mnt/data/Music

---

### Post by agarwaldvk on 2019-05-03
Hi oldfred


Sorry for the delayed response. Got caught up at work!

I am happy with the current setup, no problems. The only worry I have is that this new drive shows up differently on the file manager as compared to the other drives. I am reattaching the screenshot of the MATE file manager just to show what I mean.

I was wondering if I were to change the fstab file entry for sde1 (the new drive) to be exactly as it is for my other hdd's, would it also appear the same way. It is blank at this point, so I cannot loose any data.


Edit :
I tried a couple of things :-

When I have the following entry in my fstab file, the computer does not bootup - there is something that makes that entry invalid
/dev/sde1 /sharedfiles/media_hindi_v2 defaults 0 0

Surprising that all of the other hdd's are mounted in exactly he same manner and it has no issues as can be seen from the following entries in the fstab file


/dev/sda1 /sharedfiles/media_others_v1 ext4 defaults 0 0
/dev/sdb1 /sharedfiles/media_hindi_v1 ext4 defaults 0 0
/dev/sdd1 /sharedfiles/backupdata ext4 defaults 0 0


When I have either of the following ways, it works with and without showing the drive as a separate entry under "Devices" respectively :-

#/dev/sde1 /sharedfiles/media_hindi_v2 auto nosuid,nodev,nofail,x-gvfs-show 0 0         - shows as a separate entry under "Devices"
/dev/sde1 /sharedfiles/media_hindi_v2 auto nosuid,nodev,nofail,x-gvfs-hide 0 0            - does not show as a separate entry under "Devices"

Could someone advise me what is different in the first entry (which the system sees as invalid) and the 2nd/3rd entries both of which are seen as valid and why does that happen?


I would like to know what can I do to make this entry a valid entry (even if it means that I need to physical remove and reattached the hdd and reformat the same).




Best regards


Deepak

---

### Post by oldfred on 2019-05-03
Do not know Mate's file browser.

And no expert on mount options. for details:
man mount

You posted this without the ext4, typo on post or the issue?
/dev/sde1 /sharedfiles/media_hindi_v2 [COLOR=#ff0000]ext4[/COLOR] defaults 0 0
  

Also last field of 0 means no fsck, which would be correct if not ext2, ext3 or ext4 family of formats (like NTFS). Normally 1 is for / and 2 for other mounts.

You also should really use UUIDs or labels. Your drive order mounts depend on when UEFI/BIOS brings up drive. If a drive is slow starting it may then change your mount. Some have posted issues where drive "changed", but it just mounted in different order.

---

### Post by agarwaldvk on 2019-05-04
Hi oldfred


Again sorry for the delayed response. I am going to be guided by what you suggest given that you definitely know a lot lot more than I do. I do want to setup entries in the fstab file using UUID's but I am not confident how to go about it. Can you please look at the following output from the "blkid" command and for one of the drive show me how should the command be written in the fstab file so that it would be mounted using UUID :-
```

/dev/sda1: UUID="f9c052d1-7238-4661-950f-0b77efa6f370" TYPE="ext4" PARTLABEL="MyData" PARTUUID="d0c1f0b4-d8a6-4615-a0d2-4c01022e17a9"
/dev/sdb1: UUID="550ba0a7-0b53-41b8-9645-b8bc1d990187" TYPE="ext4" PARTLABEL="MyMedia" PARTUUID="aa54a073-2a08-4a97-8e10-5f706a749ea2"
/dev/sdc1: UUID="725347c6-51f3-4761-8397-fe9a6d8392bd" TYPE="ext4" PARTUUID="9f6c3ccf-01"
/dev/sdc5: UUID="c946b6ad-ddb9-47d8-88da-d39fda0af429" TYPE="swap" PARTUUID="9f6c3ccf-05"
/dev/sdd1: UUID="44445819-31ad-4b9e-b865-b711d5490f49" TYPE="ext4" PARTLABEL="Data_Backup" PARTUUID="da0fc8ae-694f-44cd-b750-e061ed94d834"
/dev/sde1: UUID="c7aa6e4d-497e-4299-8abc-6ca3e0fd5d93" TYPE="ext4" PARTUUID="84b59233-3d51-4970-b5e9-3b283986f096"
```


Could you please also advise how can I add labels to my drives. I checked the following command and see that I don't have labels for any of my hdd's and would like to add them now that I am changing things for the drives. This obviously cannot be done in the fstab file entry, right? Must be a separate command?


```

sudo lsblk -o NAME,LABEL
NAME   LABEL
sda
&#9492;&#9472;sda1
sdb
&#9492;&#9472;sdb1
sdc
&#9500;&#9472;sdc1
&#9492;&#9472;sdc5
sdd
&#9492;&#9472;sdd1
sde
&#9492;&#9472;sde1
sr0

sudo blkid -o list
device                             fs_type      label         mount point                            UUID
------------------------------------------------------------------------------------------------------------------------------------------
/dev/sda1                          ext4                       /sharedfiles/media_others_v1           f9c052d1-7238-4661-950f-0b77efa6f370
/dev/sdb1                          ext4                       /sharedfiles/media_hindi_v1            550ba0a7-0b53-41b8-9645-b8bc1d990187
/dev/sdc1                          ext4                       /                                      725347c6-51f3-4761-8397-fe9a6d8392bd
/dev/sdc5                          swap                       [SWAP]                                 c946b6ad-ddb9-47d8-88da-d39fda0af429
/dev/sdd1                          ext4                       /sharedfiles/backupdata                44445819-31ad-4b9e-b865-b711d5490f49
/dev/sde1                          ext4                       /sharedfiles/media_hindi_v2            c7aa6e4d-497e-4299-8abc-6ca3e0fd5d93
```



Also, even I noticed that there wasn't the "ext4" bit in the Gparted specified entry in the fstab file which was like this :-

```
dev/sde1 /sharedfiles/media_hindi_v2 auto nosuid,nodev,nofail,x-gvfs-show 0 0
```


Changing the "x-gvfs-show" to "x-gvfs-hide" fixes my concern with the hdd appearing under the "Device" heading.


So I just removed everything after "_v2" and replaced with what I thought needed to be specified, obviously incorrect. Now, for testing purposes, if I were to change the entry like so :

```
/dev/sde1 /sharedfiles/media_hindi_v2 ext4 defaults 0 0
```

it should work, shouldn't it?


Out of interest though, why was that entry made by Gparted without specifying the "ext4" valid?

---

### Post by oldfred on 2019-05-04
I believe auto is valid.
I do not like any of the automatically generated fstab entries.
Like this that suggests using a template & copy your UUID & mount point.
[https://ubuntuforums.org/showthread.php?t=1983336&p=11955166#post11955166](https://ubuntuforums.org/showthread.php?t=1983336&p=11955166#post11955166)


From this you have what you need to edit a typical entry. Your blkid list:
```
/dev/sda1  ext4 /sharedfiles/media_others_v1     f9c052d1-7238-4661-950f-0b77efa6f370
```

I just copied entry from link above and put in your UUID & mount point.
UUID=f9c052d1-7238-4661-950f-0b77efa6f370 /sharedfiles/media_others_v1 ext4 defaults,noatime 0 2

After any edit of fstab always run this. If it just returns, it remounted everything ok. If errors you must fix before rebooting.
sudo mount -a

I try to label with gparted when creating a new partition. Now with gpt there are two labels.
But when I just need labels I often use Disks, to edit both partition label (with gpt) and file system label. Labels are different than mount points. I have confused myself with mount of Data and label of data. I primarily use labels for those partitions I do not normally mount with fstab, so mounted with Nautilus with something I understand rather than a long UUID.

Screen shows pop up screen that you get with clicking on the little gear or star icon.

---

### Post by agarwaldvk on 2019-05-08
Hi oldfred


Sorry about the delayed response. I didn't realize that you had responded. Thanks for it though.

I tried to mount my sde1 drive (the new 6 tb one) using the UUID but I got an error saying "parse error, ignore line 19"

The command use was like this exactly :-

```
UUID=c7aa6e4d-497e-4299-8abc-6ca3e0fd5d93 /sharedfiles/media_hindi_v2 ext4 defaults, noatime 0 2
```

Any idea why? Where am I going wrong?

In the meanwhile I did mount it using the normal /dev/sde1 and it seems to work!

Best regards


Deepak

---

### Post by oldfred on 2019-05-08
No spaces in comma list of parameters. It looks like you have a space.
defaults, noatime

---

### Post by agarwaldvk on 2019-05-08
Hi oldfred


Thank you!

Yes,  normally do tend to like spaces where  think it would do no harm. Obviously it did in this case.

I will try again tonight and let you know how I went.


Best regards


Deepak

---

