---
title: "Double-booting Windows? Consider FAT32"
date: 2007-04-17
forum: Connecticut Team
---

### Post by Razzl on 2007-04-17
What the heck, I may be the new kid on the block but our new Connecticut forum needs some stuff to read, so let me toss out a thought for the big Feisty Feasty this week: 

    if you're double booting with Windows, and you don't have any files you want to save on your previous install, consider doing a fresh install on your old partition and using FAT32 as your file system.  The Official Ubuntu Handbook says this will allow you to read from your Ubuntu partition in Windows (notice you can't even see it in Windows Explorer now?).  You should even be able to copy files to Ubuntu (but it doesn't go both ways; you'll only be able to copy files from Ubuntu to Windows if your Windows is all FAT32 (like those funky Acer laptops) rather than NTFS, which ain't likely.  (If you're going to encrypt your Vista laptop then don't bother, it probably won't help)

   This is the kind of tech tip we should in theory have enough "ubuntu" to share with the mega-forums, but things are a little chaotic and testy out there with all the newbies overwhelming the volunteers, so I'll share it with just us homies for now...:-$

---

### Post by Dragonbite on 2007-04-18
Another alternative if you just want to share your files in a dual-boot system between Windows and Linux is to partition the HD 3 ways (at least)
[INDENT]hda0  :NTFS (Windows)
hda1 : EXT3 (Linux)
had2 : Fat32 (files)
[/INDENT]You can re-direct your **My Documents** folder to go off of the Fat32 partition by right-clicking on **My Documents** and go into **Properties**. You will see a place to put the location of My Documents and you can redirect it to the drive letter.

If you share the computer with multiple people, you may want to set up a sub-folder with each person's login name and set each of their **My Documents** to their specific folder. Of course Thunderbird allows you to redirect where you want to keep your files.

One thing you'll notice is that Windows allows you to set a file or folder to be hidden.. Linux doesn't hid them. Linux instead uses the prefix "." (like .Trash ) to hide the directory of file and you guessed it: Windows shows those.

Also note, this doesn't move over Application settings (like default Mozilla Thunderbird files go in _C:\\Documents and Settings\<<your login>>\Application Date\Thunderbird_ and this is NOT moved to the Fat32 Partition in this example, only the things under the **My Documents** folder.

An alternative of this, though, is to set up the Fat32 partition as an "( S: )" drive.. for "Share". This way you only put those files you want to share between the OSs there and everything else stays in the default location.

On the Linux side, all you need to do is 
[INDENT]Mount the partition (modify the /etc/fstab file, or check the Disk Management tool)
Symlink to the mount point to make it easy to access (middle-click the mounted directory and drag it to where you want it and select "Link"[/INDENT]

The nice thing about that is that for all intents and purposes the link IS the linked directory so all navigation, etc. is as if those files are in the link, not in the actual directory.  I wish Windows Shortcuts would work like this.

**NOTE:**
I do not recommend linking your entire /home/ directory to the Fat32 partition.  Even if it works (which it did for me) it caused me errors, and after seeing a partition table I built using a Live CD get blown away when I booted windows because it didn't understand it (or something), I am hesitant on having crucial information placed where both can access, and so suggest the Shared directory method instead.

Another alternative is using VMWare and setting one up as your host, and the other as a virtual machine and sharing (if that is possible) the desired directories ( or the whole  C: ).

---

### Post by Razzl on 2007-04-18
Thanks for the expansion, Drew.  Since I have nothing critical to lose on my old Ubuntu I'm going to experiment with the fresh install of Feisty with the partition reformatted as FAT32 and see what happens.  I was curious about some other things as well, like whether Windows utilities such as defrag would include Ubuntu space in their routine.  I'll report back on what happens.  I'm supposing at worst it will only be Ubuntu that gets hozed rather than Windows, cross my fingers...

---

### Post by garlik42 on 2007-04-18
I always use an ext2/3 partition for transfer between linux/windoz, since I often have the need to transfer large (4-20gig) files fat32 just doesn't fly (can't have a file larger than 4 gig) so it led me to this.

[http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)

But previously, I was using fat32 for transfer operations only (I like having a transactional file system for safty sake)

Funny, when I first started using linux in the early 90's I used ext2 for everything, now I use ext2 for /boot
reiser for /, /tmp, /var, /home, /usr, xfs for /var/lib and ext3 for my transfer area.

It's nice having the option to use so many different file systems all optimized for different things.

---

### Post by Razzl on 2007-04-18
Garlik, how are ext2 and ext3 different?  I haven't read any general linux books so I don't know much about them.

And about FAT32--I'm now sure I understand how the 4gb limit comes into play--new Acer laptops come formatted as FAT32 on the C: drive, yet they have Windows, which must have some files larger than 4gb?

---

### Post by garlik42 on 2007-04-19
ext3 is actually just ext2 with a transaction log.
It is safe to mount an ext3 file system (that was cleanly unmounted) as an ext2

---

### Post by Razzl on 2007-04-20
I tried to set up my 7.04 primary partition as FAT32 and it wouldn't take--the system said FAT32 wasn't "a recognized Linux file system".  I went back to the book and found that it was suggesting creating an extra  FAT32 partition for swapping data, not using it as the primary Ubuntu partition.  Sorry for any confusion my confusion my have caused!:(

---

### Post by garlik42 on 2007-04-20
> **Razzl said:**
> Garlik, how are ext2 and ext3 different?  I haven't read any general linux books so I don't know much about them.

And about FAT32--I'm now sure I understand how the 4gb limit comes into play--new Acer laptops come formatted as FAT32 on the C: drive, yet they have Windows, which must have some files larger than 4gb?

Not nesessarily. 
The only files that ever get this size during normal windows operation, would be the hiber files, and swap files, but only if you have a shitload of memory.

But like I Said, if you want to use ext2/3 you can download that windows driver to access ext2 from windows, or you can use fat32 if your file size limit is not an issue.

As far as running linux on a fat32, that used to be supported, but I guess it's not any more. Fat32 has no provisions for security or transaction processing, and isn't really a good idea for linux.

---

