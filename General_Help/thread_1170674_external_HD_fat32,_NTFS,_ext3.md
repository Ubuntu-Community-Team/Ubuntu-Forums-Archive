---
title: "external HD: fat32, NTFS, ext3"
date: 2009-05-26
forum: General Help
---

### Post by punkbohemian on 2009-05-26
Recently, I bought this hard drive:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16822136321](http://www.newegg.com/Product/Product.aspx?Item=N82E16822136321)

and it came formatted as FAT32. I'm trying to figure out if/how I should format it to something else. I'll only be using it for extra storage and backup for my Ubuntu only laptop with an already full HD. I was thinking of going to ext3, but I've read other threads by people who have done that and now the external HD isn't being recognized by the machine. OTOH, I've read that NTFS is pretty fussy with unmounting volumes, and if one doesn't unmount cleanly, the whole HD could crash. Finally, I've heard that the only real shortcoming to FAT32 is the file size limit. I'm not sure if that's a problem for me. I don't do anything pertaining to DVD isos, but I'm not sure what else might have as large or larger file sizes.

Also, I got GParted, but it's not giving me the option to delete the partition. I don't know if this means anything, but next to the partition name, there is a key icon (as in it's locked?).

Anyway, I'd appreciate any help on the matter. Thanks.

---

### Post by Minsky on 2009-05-26
I think the problem is that ownership of the drive is assigned to another user (probably Root) which is why you're unable to make any changes to it. To change ownership to yourself, try the following command, it works with files and I assume it also works with devices.

```
sudo chown _R *username*:*username* /path/to/external/drive
```

You and your group should now have ownership of the drive and you'll be able to reformat it. Hope this helps

---

### Post by coffeecat on 2009-05-26
> **punkbohemian said:**
> Also, I got GParted, but it's not giving me the option to delete the partition. I don't know if this means anything, but next to the partition name, there is a key icon (as in it's locked?).

The key/lock icon in Gparted means that the partition is mounted. You can't delete or reformat a mounted partition. Right-click on the partition entry in Gparted and choose unmount.

However, if you are not going to use files of >4GB, why not leave the drive formatted as is? Also - I don't know where you've read that about NTFS drives. **All** filesystems are fussy about being unmounted cleanly. If you just pull the plug on a mounted drive while it is being written to, you will get filesystem corruption. In fact NTFS, being journalled, is more robust than FAT32, but if you do get a corrupted filesystem, you really need Windows to repair it. But you really need Windows to repair FAT32 as well, because that is also a MS filesystem.

> **Minsky said:**
> I think the problem is that ownership of the drive is assigned to another user (probably Root) which is why you're unable to make any changes to it. To change ownership to yourself, try the following command, it works with files and I assume it also works with devices.

```
sudo chown _R *username*:*username* /path/to/external/drive
```You and your group should now have ownership of the drive and you'll be able to reformat it.

Sorry, no. FAT32 is a Microsoft filesystem and doesn't support Linux/Unix permissions, so chown and chmod have no effect on files and folders in a FAT32 partition. You can change the permissions for the mountpoint, but that won't help the OP in this situation.

---

### Post by punkbohemian on 2009-05-27
> The key/lock icon in Gparted means that the partition is mounted. You can't delete or reformat a mounted partition. Right-click on the partition entry in Gparted and choose unmount.

That solved that problem. Thanks.

> However, if you are not going to use files of >4GB, why not leave the drive formatted as is? ...but if you do get a corrupted filesystem, you really need Windows to repair it.

Well, it sounds like I should convert to ext3, as then if I get a corrupted file system, I wouldn't need Windows (which I won't have pretty soon) to repair it. Are there any complications with converting an external HD to ext3 that I should know about?

Thanks again.

---

### Post by coffeecat on 2009-05-27
> **punkbohemian said:**
> Well, it sounds like I should convert to ext3, as then if I get a corrupted file system, I wouldn't need Windows (which I won't have pretty soon) to repair it. Are there any complications with converting an external HD to ext3 that I should know about?

Windows is needed for the chkdsk utility. There may be bootable disc images out there with chkdsk on them, but offhand I don't know of one, but if you're going for a Linux only setup then it does make sense to use ext3. There are no problems in converting the partition to ext3 in Gparted, but there is one minor complication in day-to-day use.

When you plug in the drive and it gets automounted, it's mounted with root-only priviliges for the root of the filesystem. That means you won't be able to create folders, or drag and drop things over, in the normal way. Not at first, that is. One way round this is to change the ownership of the mountpoint to yourself with chown. But you have to do this every time the drive is mounted, because the mountpoint for an external drive is created and removed dynamically. The second way is to create some special udev rules, but I've never gone down that route. I prefer not to give myself a headache. :p

Being a simple sort of soul, I do the following. Assuming the mountpoint for the drive is /media/disk, first create a folder for all your stuff:

```
sudo mkdir /media/disk/my_stuff
```Call the folder what you will. Now change ownership to yourself:

```
sudo chown yourusername: /media/disk/my_stuff
```Note the use of the colon with *yourusername*. That means that ownership is given to your default group - *yourgroupname* in Ubuntu, but sometimes 'users' in other distros.

Now, when you first mount the drive, simply navigate to *my_stuff* and create folders and drag and drop things to your heart's content because everything in my_stuff will be owned read/write by you. And if anyone knows a more elegant way of dealing with permissions with an external drive, I'll be glad to learn of it.

You have to go through this rigmarole because ext3 supports Linux/Unix permissions - which is one reason why I use NTFS (which doesn't) for most of my external drives, but I do have Windows available. There's also one other gotcha with ext3. If your account in Ubuntu is the first created, then your UID will be 1000. That's true for many Linux distros, but some use a UID of 500: Fedora, Mandriva and PCLinuxOS if my memory is correct. Which means that if you try out another distro, you may find yourself denied access to your own files on the external drive and having to invoke root privileges to get to them.

**Edit:** an alternative to creating one folder, my_stuff, and putting all your Music, etc folders in that, is to create Music, Videos, Documents, Whatever folders from the terminal with sudo, and then sudo chown each one to your ownership. A bit more elegant, but you still won't be able to write to the root of the filesystem without invoking root priviliges.

---

### Post by armageddon08 on 2009-05-27
Right click on the external drive icon and click on unmount. Again Right Click on the drive in gparted and click on Format to and select ext3. That should do it.

---

### Post by punkbohemian on 2009-05-27
> There are no problems in converting the partition to ext3 in Gparted, but there is one minor complication in day-to-day use.

so, just so I'm clear, I only have to run that command line to change ownership of the folder once and after that I can read/write/delete within "my_stuff" whenever I mount the drive? In other words, I don't have to run the command line every time?

> There's also one other gotcha with ext3. If your account in Ubuntu is the first created, then your UID will be 1000

I don't see myself switching to another distro any time soon, but if I do, couldn't I just permanently change the permissions on the "my_stuff" folder like I would be doing in Ubuntu?

> All filesystems are fussy about being unmounted cleanly. If you just pull the plug on a mounted drive while it is being written to, you will get filesystem corruption.

I'm actually concerned about this. Not that I ever intentionally dismount a drive uncleanly, but this particular external requires a power supply, and the plug has a slight tendency to just slip out, subsequently unmounting the drive. Hence, I want to go with a format with the greatest ease of recovery.

---

### Post by Legace on 2009-05-27
> **punkbohemian said:**
> so, just so I'm clear, I only have to run that command line to change ownership of the folder once and after that I can read/write/delete within "my_stuff" whenever I mount the drive? In other words, I don't have to run the command line every time?


The change is permanent (unless you change the permissions again), so no, you won't have to run the command line every time :)

---

### Post by punkbohemian on 2009-05-27
ok, (possibly) last question :)

I'm about to start the reformat. Gparted seems pretty straight forward in that all I have to do is right click on the drive, select "format to">*filesystem*. However, I remember reading in another thread that it's better to just delete the entire partition and create a new one in the new format. Is this true? If so, why is it better? Thanks again.

---

### Post by Legace on 2009-05-27
> **punkbohemian said:**
> I'm about to start the reformat. Gparted seems pretty straight forward in that all I have to do is right click on the drive, select "format to">*filesystem*. However, I remember reading in another thread that it's better to just delete the entire partition and create a new one in the new format. Is this true? If so, why is it better? Thanks again.

I don't know if its true, but I've always deleted old partitions and created new ones :) And I've never had a problem, so I think I'll stick with the way I'm using ;)

---

### Post by coffeecat on 2009-05-27
> **punkbohemian said:**
> I don't see myself switching to another distro any time soon, but if I do, couldn't I just permanently change the permissions on the "my_stuff" folder like I would be doing in Ubuntu?

No problem with that.

> **punkbohemian said:**
> However, I remember reading in another thread that it's better to just delete the entire partition and create a new one in the new format. Is this true? If so, why is it better? Thanks again.

You don't want to believe everything and everyone you read in this forum - including me! :wink:

Seriously, I can't think of a good reason to do that, unless there was corruption of the actual partition table, in which case you'd want to create a new partition table anyway, which would have the effect of wiping out everything on the disc. Or perhaps there was something more complicated going on - making one partition out of two or something like that. Simply do the right-click > 'Format to' method that's already been posted and you should be fine. I should imagine there's simply one big partition covering the whole drive anyway.

By the way, a useful tip. While you're reformatting the partition, set a label as well. Set the label after you've reformatted. The label option is further down that right-click menu. The advantage is that when you plug the drive in and it's mounted, you get the label under the drive icon. Useful if you plug more than one device in.

---

### Post by punkbohemian on 2009-05-29
Thanks for all the advice. Everything seems to be working well. :)

---

