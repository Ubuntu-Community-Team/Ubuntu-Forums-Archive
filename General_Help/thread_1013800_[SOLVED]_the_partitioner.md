---
title: "[SOLVED] the partitioner"
date: 2008-12-17
forum: General Help
---

### Post by 2handband on 2008-12-17
I just got a new laptop with a 250GB hard drive and would like to partition it as follows:

150GB for my main OS (Hardy)
50GB for Intrepid to play around with
50GB to experiment with other distros

Trouble is I don't really understand partitioning in Ubuntu outside of the guided regions, and the online tutorials are not enlightening. Could someone explain how to get the partitions I want using the manual partitioner? Thanks!

By the way my new machine is an ACER 6930. I haven't put Ubuntu on it yet and probably won't get the chance for a couple of days. If anyone has any experience with these machines and wants to post it I'm all ears...

---

### Post by taurus on 2008-12-17
If you want to resize your harddrive, you must use gparted from Ubuntu LiveCD or GParted LiveCD, [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php).  Don't forget to create a swap partition too.

---

### Post by birddog165 on 2008-12-17
Be sure to have anything important backed up... partitioning isn't a problem if you're careful ;)

---

### Post by caljohnsmith on 2008-12-17
> **2handband said:**
> I just got a new laptop with a 250GB hard drive and would like to partition it as follows:

150GB for my main OS (Hardy)
50GB for Intrepid to play around with
50GB to experiment with other distros

You could use Ubuntu's partition editor "gparted" on the Live CD (System > Admin > Partition Editor) like taurus suggested to do your partition changes. Just keep in mind that as far as partitioning rules go, you can only have a maximum of either 4 primary partitions, or you can have have a max of 3 primary partitions with one extended partition where the extended partition contains as many logical partitions as you want. So if you want more than 4 partitions, you will need to set up an extended partition. Let us know how it goes or if you run into problems. :)

---

### Post by 2handband on 2008-12-17
I just found a tutorial that was at least moderately useful. Let's see if I have this straight:

a "/" partiton is the one that the OS and programs goes into.

a "/home" patition holds the files

What about a swap partition? I understand what it's for, but what kind of file is it and how do I create it?

Something else that occured to me: can I create a big /home partition for files and make it accessable to multiple OSes in seperate "/" partitions?

Thanks for the tips so far!

---

### Post by SuperSonic4 on 2008-12-17
Yes

Yes but it also holds non-critical data such as program settings

Swap is what the system uses when it runs out of ram, you can select "linux-swap" from the formatting options - make it ram+512mb if you have more than 1gb RAM (assuming you want to hibernate). If you have more than 2gb ram you generally won't need a swap but I'd make it ~1gb if you don't want to hibernate/suspend the system especially since your hdd space is not at a premium

Not sure, but it would be easier to make a data partition without anything else, this will then mount in media and can be referred to from anywhere

---

### Post by caljohnsmith on 2008-12-17
I would definitely not recommend using a shared /home partition between your distros, because your home directory contains a lot of hidden .files and .directories that have settings specific to each distro. Like SuperSonic4 mentioned, I think it is better to have a shared data partition. If you create folders like "Music", "Video", etc in your data partition, you can use a symbolic link to link them directly to each of your home directories in your different distros if you want. That works really well for most people.

---

### Post by SuperSonic4 on 2008-12-17
> **caljohnsmith said:**
> I would definitely not recommend using a shared /home partition between your distros, because your home directory contains a lot of hidden .files and .directories that have settings specific to each distro. Like SuperSonic4 mentioned, I think it is better to have a shared data partition. If you create folders like "Music", "Video", etc in your data partition, you can use a symbolic link to link them directly to each of your home directories in your different distros if you want. That works really well for most people.

Yeah, a shared data drive is what I've done to put my media on whereby Music, Video, Pictures and Documents have their own partitions. You'll be best just making one partition and making subfolders I suspect

---

### Post by tarps87 on 2008-12-17
> **2handband said:**
> Something else that occured to me: can I create a big /home partition for files and make it accessable to multiple OSes in seperate "/" partitions?

This is possible. For this I would suggest something like this

30GB hard
30GB intrepid
30GB other os

swap depends on ram
home the rest

In Ubuntu (which ever one you install first) create a partition for the OS ( / ) (30GB is enough for me but you can change it) format it to ext3, create the other to OS partitions (this can be done after but you will have to work out the size of your home partition by hand :)) both ext3. Now create the swap partition as swap and select the remaining space as /home ext3.
Format all these partitions.
When installing the next to OS's you can use the same swap partition if you only hibernate one OS at once. Select the /home partition to use as their home partitions but remember to unselected format, you don't want to format this partition again.

This is how I would do it, but it is not the only way. If you don't understand anything post back and I will try to help.

You may find using separate /home partitions and using a share partition more reliable. I have run Ubuntu and Kubuntu from the same /home partition and as they are different desktops they have interfered.

---

### Post by 2handband on 2008-12-17
> **caljohnsmith said:**
> I would definitely not recommend using a shared /home partition between your distros, because your home directory contains a lot of hidden .files and .directories that have settings specific to each distro. Like SuperSonic4 mentioned, I think it is better to have a shared data partition. If you create folders like "Music", "Video", etc in your data partition, you can use a symbolic link to link them directly to each of your home directories in your different distros if you want. That works really well for most people.

That sounds like exactly what I'm looking for. So how do I go about setting this up? What's a good size for all these partitions? Once again I have a 250GB HD, 4GB of RAM, and will be running three Linux OSes. There will be no Windows.

---

### Post by SuperSonic4 on 2008-12-17
Do you intend to use hibernation?

If Yes:
/ = 30gb ext3 (hardy)
/ = 30gb ext3 (intrepid)
/home = 60gb ext3 (ubuntu home)
/ = 30gb ext3 (other OS)
/home = 30gb ext3 (other OS)
swap = 4608mb = 4.5gb (linux swap)
data = whatever's left

If no
/ = 30gb ext3 (hardy)
/ = 30gb ext3 (intrepid)
/home = 60gb ext3 (ubuntu home)
/ = 30gb ext3 (other OS)
/home = 30gb ext3 (other OS)
swap = 0 or 512, it's unecessary (linux swap)
data = whatever's left

---

### Post by caljohnsmith on 2008-12-17
> **2handband said:**
> That sounds like exactly what I'm looking for. So how do I go about setting this up? What's a good size for all these partitions? Once again I have a 250GB HD, 4GB of RAM, and will be running three Linux OSes. There will be no Windows.
You could give each distro maybe between 20-30 GB for their root partitions and that should be enough for most people. I would use 4 GB of swap space, and then with the rest of the space, make one or more data partitions. It would be good to have the data partition mounted automatically on start up by adding it to the /etc/fstab in each distro, and then once you create your personal directories in the data partition, you can link those directories to your /home folder by doing something as simple as:
```
ln -s /media/sda5/[COLOR="Blue"]Music[/COLOR] ~/.
ln -s /media/sda5/[COLOR="Blue"]Videos[/COLOR] ~/.
ln -s /media/sda5/[COLOR="Blue"]Pictures[/COLOR] ~/.
...etc.
```
So "sda5" in the above example is the mounted data partition in /media, so you would change that if you decide to mount your data partition elsewhere.

---

### Post by 2handband on 2008-12-17
Thanks everybody! I'll hopefully have time to do the install tomorrow afternoon.

---

### Post by 2handband on 2008-12-17
Okay, what mount point should I use for the data partition? Will /home do or should I use something else? What mount point should I use for the swap partition? What's the diff between a primary and logical partition, and which should I use for what? I've got the Ibex partitioner in front of me right now if that makes any difference.

---

### Post by 2handband on 2008-12-17
Another problem also came up... it won't let me use the same mounting point for more than one partition. So what do I create the other two OSs' under?

---

### Post by SuperSonic4 on 2008-12-17
If you install ibex as normal giving / 30gb and /home 30gb both ext3 and swap as swap. The data one will just be a generic ext3 not mounted anywhere.

The other two OSes can be installed using their live CDs and putting that into empty spaces. Linux can boot from logical partitions so that's ok. 

Just bear in mind whichever distro you put on last will configure grub

---

### Post by 2handband on 2008-12-19
Okay, I've got Intrepid running on a 30GB partition and have created an unmounted data partition, with the remainder set aside for the additional OSes. How do I go about setting the data partition to mount on start-up?

---

### Post by caljohnsmith on 2008-12-19
> **2handband said:**
> Okay, I've got Intrepid running on a 30GB partition and have created an unmounted data partition, with the remainder set aside for the additional OSes. How do I go about setting the data partition to mount on start-up?
How about posting the output of:
```
sudo fdisk -lu
sudo blkid
```
And please identify which is your new data partition.

---

### Post by 2handband on 2008-12-19
"gene@gene-laptop:~$ sudo fdisk -lu
[sudo] password for gene: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x87c675e4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    58589054    29294496   83  Linux
/dev/sda2        58589055   371085434   156248190   83  Linux
gene@gene-laptop:~$ sudo blkid
/dev/sda1: UUID="3538b7d3-8970-4e8b-91a7-64cc39de4dca" TYPE="ext3" 
/dev/sda2: UUID="ed245138-5562-4c88-abad-a4bc1f254d6d" SEC_TYPE="ext2" TYPE="ext3" 
gene@gene-laptop:~$ "


sda2 is the data partition

---

### Post by caljohnsmith on 2008-12-19
OK, how about doing the following:
```

sudo mkdir /media/Data
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
```
And add the following lines:
```
# /dev/sda2 Data partition:
UUID=ed245138-5562-4c88-abad-a4bc1f254d6d   /media/Data   ext3 relatime,errors=remount-ro 0 0

```
Save the file, and then do:
```
sudo mount -a
```
And if all goes well your new data partition should be mounted on /media/Data. Let me know how it goes or if you run into problems.

---

### Post by 2handband on 2008-12-19
when i entered the last command i got the following reply:

"[mntent]: line 10 in /etc/fstab is bad"

---

### Post by caljohnsmith on 2008-12-19
OK, please post:
```
ls -l /media
cat /etc/fstab
```

---

### Post by 2handband on 2008-12-19
"gene@gene-laptop:~$ ls -l /media
total 5
lrwxrwxrwx 1 root root    6 2008-12-18 19:51 cdrom -> cdrom0
dr-xr-xr-x 1 root root  564 2004-08-04 07:00 cdrom0
drwxr-xr-x 2 root root 4096 2008-12-19 14:56 Data"

---

### Post by 2handband on 2008-12-19
"# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3538b7d3-8970-4e8b-91a7-64cc39de4dca /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
none /proc/bus/usb usbfs devgid=126,devmode=664 0 0
# /dev/sda2 Data partition:
UUID=ed245138-5562-4c88-abad-a4bc1f254d6d a /media/Data	 ext3 relatime,errors=remount-ro 0 0"

sorry, missed this bit

---

### Post by caljohnsmith on 2008-12-19
I'm sorry, I found a small typo in my post #20 and corrected it. How about doing:
```
gksudo gedit /etc/fstab
```
And copy/paste the lines from post #20 again, save the file and do:
```
sudo mount -a
```
And let me know if your data partition is mounted on /media/Data.

---

### Post by 2handband on 2008-12-19
Success! Unfortuately I don't entirely understand what I just did, but it does work. Thanks!

---

### Post by 2handband on 2008-12-19
Okay... maybe I spoke too soon. 160 GB media is now in "places" but it won't let me do anything in there. DO I have to assign myself permissions of some kind in order to acces it's contents?

---

### Post by caljohnsmith on 2008-12-19
OK, how about doing:
```
sudo chown `whoami`:`whoami` /media/Data
```
And then see if you can read/write to the partition.

---

### Post by bodhi.zazen on 2008-12-19
What file system is on the partition ?

If it is a linux native system, use chown and chmod

```
sudo chown root.users /media/Data
sudo chmod 770 /media/Data
```

Now anyone in the users group has full access.

If you are sharing across distros, because they use different groups, just 

sudo chmod 770 /media/Data

---

### Post by 2handband on 2008-12-19
I still can't. There were no error messages when I entered the code, however.

---

### Post by caljohnsmith on 2008-12-19
OK, please post:
```
ls -l /media/Data
```

---

### Post by 2handband on 2008-12-19
"ls: cannot open directory /media/Data: Permission denied"

---

### Post by caljohnsmith on 2008-12-19
My mistake again (sorry about that), it would be better to do:
```
ls -l /media
```

---

### Post by 2handband on 2008-12-19
"total 8
lrwxrwxrwx 1 root root     6 2008-12-18 19:51 cdrom -> cdrom0
drwxr-xr-x 2 root root  4096 2008-12-18 19:51 cdrom0
drwxrwx--- 3 root users 4096 2008-12-18 19:24 Data"

---

### Post by caljohnsmith on 2008-12-19
OK, how about:
```
sudo chown `whoami`:`whoami` /media/Data
sudo chmod 755 /media/Data
```
And then you should be able to read/write to it if all goes well.

---

### Post by 2handband on 2008-12-19
Still no joy.

---

### Post by caljohnsmith on 2008-12-19
OK, please post:
```
ls -l /media
touch /media/Data/testfile
ls -l /media/Data
```

---

### Post by 2handband on 2008-12-19
gene@gene-laptop:~$ ls -l /media
total 8
lrwxrwxrwx 1 root root    6 2008-12-18 19:51 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2008-12-18 19:51 cdrom0
drwxr-xr-x 3 gene gene 4096 2008-12-19 16:12 Data
gene@gene-laptop:~$ touch /media/Data/testfile
gene@gene-laptop:~$ touch /media/Data/testfile
gene@gene-laptop:~$ ls -l /media/Data
total 16
drwx------ 2 root root 16384 2008-12-18 19:24 lost+found
-rw-r--r-- 1 gene gene     0 2008-12-19 16:13 testfile

---

### Post by caljohnsmith on 2008-12-19
That output you just posted shows it worked just fine; you (Gene) are now the owner of that partition, and you successfully wrote a "testfile" to it. What did you previously try when you said no joy? Try opening up a text editor and saving a file to that partition, or open up a file browser (nautilus) and create a folder in it. You should be able to do that without any problems according to the ownership/permissions on your Data partition, and also as we just demonstrated with the commands you posted.

---

### Post by 2handband on 2008-12-19
I tried creating a folder, which it still won't let me do. I just tried saving to it and it will let me do that.

---

### Post by caljohnsmith on 2008-12-19
So are you sure you are trying to create a folder in /media/Data? How about doing:
```
nautilus /media/Data &
```
And then when the browser comes up, try creating a folder in the /media/Data directory, which is where the browser should be. Let me know if that works.

---

### Post by 2handband on 2008-12-19
the create folder button is still greyed out.

---

### Post by caljohnsmith on 2008-12-19
I think I must brain dead today, because I must admit that I'm not understanding what the problem is. :) I just now tested the exact same procedure with a partition on my own computer and it worked just fine. Did you go under File > Create Folder to make the folder in nautilus? Or you should be able to right-click the nautilus screen and select "create folder". Does that not work? If you right-click the screen and choose "properties", does it show the location as /media with a name of "Data"? And if you click the permissions tab, what does that show you (Gene) as the owner?

---

### Post by 2handband on 2008-12-19
I just restarted the computer and now it works. Thanks... you've been tremendously patient and helpful.

---

### Post by caljohnsmith on 2008-12-19
> **2handband said:**
> I just restarted the computer and now it works. Thanks... you've been tremendously patient and helpful.
You're welcome, I'm glad it's finally working. Cheers and hope you have smoother sailing with your Ubuntu install now. :)

---

