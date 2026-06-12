---
title: "Best practice for installing second hard drive?"
date: 2008-12-31
forum: General Help
---

### Post by jessebean on 2008-12-31
I've heard too many scary stories this season about failing drives.  I want to install a secondary drive for the /home partition.

Questions
[LIST=1]
[*]Can I easily install another drive beside an existing system?
[*]Can I easily repartition the current /home onto the new drive?
[/LIST]

Thanks and Happy New Year

---

### Post by albandy on 2008-12-31
Yes.
First backup your /home directory

for example:
sudo tar zcvf /root/home.tgz /home
then install your new drive
make a partition and format it
then edit your /etc/fstab and add the new mount point for /home
reboot your computer
restore the /root/home.tgz to your new /home

---

### Post by drs305 on 2008-12-31
> **jessebean said:**
> 
Can I easily repartition the current /home onto the new drive?


I think you mean 'move' the current /home onto the new drive. Here is a guide to moving your /home:
[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by chrestomanci on 2008-12-31
> **albandy said:**
> Yes.
First backup your /home directory
...
While I don't want to disorage people from making backups, this step is not realy necessary, and could be a problem if the user has hundreds of Gigabytes of multimeda files and no where to keep them.

An alternative strategy, that will be quicker, but slightly risky is to use a live CD.

[LIST=1]
[*]Shut down the system.
[*]Install the new hard drive in the system.
[*]Boot the system with a Live CD such as Knoppix
[*]Using Knoppix, format the new hard drive, copy all the files, and edit the partion table.
[*]Reboot the system. It should now work with /home on the new hard drive
[/LIST]

To explain step 4 in more detail, When the system is booted using a live CD, none of the standard drives need to be in use, so you can move their contents without causing problems. You can use any live CD system you are familiar with, so long as it supports partioning, formating a copying files. More or less all will include those functions.

When you partion and format the new drive you should be extra careful that it is the new one you are working on, not the old. To be doubly sure, you could disconnect the old drive, or use a gui tool such a [GParted](http://gparted.sourceforge.net/) (Which is also available as a live CD).

Once you have setup your new drive, you need to copy your files, and edit the /etc/fstab so that the new drive is mounted as /home.

I suggest you first create a mount point for the new drive in /etc/fstab. Open as root it with your preferred editor using something like:
```
sudo gedit /etc/fstab[/url]

Then add or edit a line for the new location of /home. You need something like:
[code]UUID=c5aac04e-6743-448c-aa0d-677fbdd100ae /home ext3 relatime 0 2 
```
Where the UUID is the correct one for the new partion you have created. You can look it up by looking where the links point to in /dev/disk/by-uuid/ (Run ls -ld /dev/disk/by-uuid/).

If you already had /home in a separate partion, then you should change the mount point to something like /home_old. If not you should just rename the directory. In any case you will need to create an empty directory /home in your root directory so the mount will work when you reboot.

You can now copy all the files. You need to make sure that the file ownerships and permissions are preserved when you copy. Your copy command should be something like:
```
cp --archive --recursive --verbose /mount/sdz1/home/* /mount/sdx1/
```
Where the archive option will preserve all the ownerships, permissions and modification times, recursive so that everything is copied, and verbose so you can follow progress. The from and to directories are where your old and new drives are mounted **when running the live CD**. You should check what they are and fill in the correct paths.

If you have a lot to copy it could take several hours, so just leave it and go for coffee, lunch, or a nights sleep depending on how much you have. Once everything is coppied you should be able to reboot your system and have the new drive in use. Your old home directory will still be preserved if you have a problem, though I suggest that if it is all OK, you delete it after a week or so to save the space.

---

