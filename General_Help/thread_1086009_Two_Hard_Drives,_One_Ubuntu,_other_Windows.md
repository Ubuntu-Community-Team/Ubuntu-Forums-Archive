---
title: "Two Hard Drives, One Ubuntu, other Windows"
date: 2009-03-03
forum: General Help
---

### Post by mikej6 on 2009-03-03
How do I transfer all my data from my Windows hard drive into Ubuntu? I am new to Ubuntu, so please explain in detail.

---

### Post by LegendofTom on 2009-03-03
Easiest way would be once you have Ubuntu installed, to mount the Windows hard drive, and just drag and drop.  Ubuntu will probably mount the Windows hard drive for you, but if it doesn't, it is pretty simple to mount it manually.

---

### Post by jARLAXL on 2009-03-03
I assume you havent set a mounting point for windows. So if you go in "places" there should appear something like "data(20Gb)".
You should be able to recognize that disk from the disk size.
Then click on it and the file manager nautilus will open showing you the contents of your windows hard drive. 
Navigate into the foler where you have the data you want to copy, select them, copy them and paste them into a folder inside your home folder in ubuntu disk.

Thats it.

---

### Post by emarkay on 2009-03-03
Just remember - you can get to all of your Windows data in Ubuntu, but you can't get ANY of your Ubuntu data in Windows.

I have a reserved FAT 32 area on a volume where I send any Linux data I need to be able to access when I (once in a blue moon) boot into in Windows.  (FAT32 because FWIW, I still have an old Win98 machine around somewhere...)

---

### Post by EzyRyder on 2009-03-03
So if I transferred music from a windows hard drive to an ubuntu hard drive, I wouldnt be able to play it when im in windows?

(Apologies to mikej6 for the hijack, didnt see any point in posting a new thread when this one was exactly what I was looking for :D)

---

### Post by jARLAXL on 2009-03-03
> **EzyRyder said:**
> So if I transferred music from a windows hard drive to an ubuntu hard drive, I wouldnt be able to play it when im in windows?
No, there are programs that you can install on windows so that windows can see the linux drives. for example [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by mikej6 on 2009-03-03
When I do that it says, lost+found

---

### Post by mikej6 on 2009-03-04
Help??

---

### Post by jARLAXL on 2009-03-05
> **mikej6 said:**
> When I do that it says, lost+found

Can you be more specific and give some info such as what you do where it says lost+found etc?

---

### Post by SuperSonic4 on 2009-03-05
> **jARLAXL said:**
> No, there are programs that you can install on windows so that windows can see the linux drives. for example [http://www.fs-driver.org/](http://www.fs-driver.org/)

That doesn't work on my windows :(

What I would do is partition your ubuntu drive keeping some as data (NTFS since windows hates everything good) so that both ubuntu and windows can access it and then use the rest of the drive space for ubuntu (depending on the size obviously).

For copying I'd use the command line, If windows is mounted at 320GB Media and your destination was your home folder in ubuntu

```
cd && mkdir ~/Windows_Data
sudo cp -Rfv '320GB\ Media/' ~/Windows_Data
```

cd && mkdir ~/Windows_Data will create a folder called Windows_Data in your home directory.


If it is in a partition mounted at /media/data:

```
sudo cp -Rfv '320GB\ Media/' /media/Data
```

You need sudo because it's likely root will own the windows disk and so the user can't copy them

-R = recursive, copy folders, subfolders and their contents
-v = verbose, show what is going on (useful for seeing how far you've got)
-f = force, do not ask for confirmation (asking about 100s of files gets annoying)

---

### Post by mikej6 on 2009-03-05
When I click on the 243.8 GB Media, which I assume is my second hardrive, the contents of that drive is a single folder that says "lost+found"

---

### Post by Ptero-4 on 2009-03-05
> **mikej6 said:**
> When I click on the 243.8 GB Media, which I assume is my second hardrive, the contents of that drive is a single folder that says "lost+found"
That means that your filesystem (the one in that HD) got badly trashed. You need to see what you can recover from that "lost+found" folder move whatever you recovered to another HD and reformat the affected HD.

---

### Post by Somiac on 2009-03-05
When I installed Ubuntu, it automatically saw my C Drive which was obviously the hard drive my windows was on...just browsed through it to get my files I needed and that was it...you should be able to see it in ubuntu.Maybe :x Because ever since I got rid of my Error.21 it doesn't see it anymore lol all well..

---

### Post by jARLAXL on 2009-03-05
> **mikej6 said:**
> When I click on the 243.8 GB Media, which I assume is my second hardrive, the contents of that drive is a single folder that says "lost+found"

Are you sure that your windows are in this disk 243.8Gb? Isn't there another disk?
If you can boot windows it means that the file system is not trashed.
Paste the output of this command:
```
sudo fdisk -l
```
This command will list all the hard drives and partitions in your system

---

### Post by mikej6 on 2009-03-06
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0ccb0cca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       29646   238131463+  83  Linux
/dev/sda2           29647       30401     6064537+   5  Extended
/dev/sda5           29647       30401     6064506   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004fbad

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29646   238131463+  83  Linux
/dev/sdb2           29647       30401     6064537+   5  Extended
/dev/sdb5           29647       30401     6064506   82  Linux swap / Solaris

---

### Post by ponyexpress on 2009-03-06
You no longer have a windows drive.

---

### Post by mikej6 on 2009-03-06
Are you serious? All of my data is now gone?

---

### Post by ponyexpress on 2009-03-06
> **mikej6 said:**
> Are you serious? All of my data is now gone?

Most likely. You no longer have a windows partition on either hard drive.
If the new partitions were formated with ext3 file system, everything is gone. If it wasn't formatted you may be able to change the partition back to ntfs and recover your data, I wouldn't get my hopes to high though.

---

### Post by ponyexpress on 2009-03-06
As I think about it, since you have been able to mount the drive and you have a lost+found folder, the drive has already been formatted. To the best of my knowledge, all your windows data are gone.

---

### Post by mikej6 on 2009-03-06
How would I do so? That is, reformat it into NTFS?

---

### Post by ponyexpress on 2009-03-07
> **mikej6 said:**
> How would I do so? That is, reformat it into NTFS?

You won't be able to reformat it and recover your files. You may be able to change the partition type to ntfs and salvage something, but I dobt it. Do you have any idea which drive had your windows on it? Do you know if there were any other patitions on that drive?

---

### Post by jARLAXL on 2009-03-07
Apparently it seems you have 2 hard  drives(sda and sdb 2x250Gb) of exactly the same size, and what is most interesting and strange, they are formatted the exact same way with a 6Gb swap partitions on each and same name of partitions.
Is the above correct? 
Do you know the size of your harddisks?
When you start your computer do you get any options while booting (eg. which operating system to choose?) and what are they if any?
Are you able to boot into windows?

---

