---
title: "using live ubuntu to recover files --please help!!!"
date: 2009-02-17
forum: General Help
---

### Post by mwing on 2009-02-17
I'm desperately trying to get to the hundreds of baby pics on my compaq that i hope i haven't lost- windows won't boot - so i'm running ubuntu- and i'm following instructions from the only website i see that helps extract files from the hard drive,([http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/))  but in the instructions it tells me that the details for why the hard drive won't mount should include a choice 2  in the message, which includes the commands to force Ubuntu to use that drive even though there's something wrong.
i have no choice 2.
mine says: "windows is hibernated, refused to mount. Failed to mount '/dev/sda1':Operation not permitted the NTFS partition is hibernated. Please resume and shutdown Windows properly, or mount the volume read-only with the 'ro' mount option, or mount the volume read-write with the 'remove_hyberfile' mount option. For example type on the command line: mount -t ntfs-3g/dev/sda1 /media/disk-1 -o remove_hyberfile" 
When I type that command line in this is what appears on the screen: 
root@ubuntu:~# mount -t ntfs-3g/dev/da1/media/disk-1 -o remove_hiberfile
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
root@ubuntu:~# 

the directions on the website say after the last step i should be able to get into the media files but it still says volume cannot mount.
this might as well all be greek to me. i'm so distraught at losing my photos, and since i'm rather computer illiterate i'm hesitant to try anything that would cause further damage.
If anyone has any ideas, i'd be indebted to you forever!!!!!!

---

### Post by Perryg on 2009-02-17
> **mwing said:**
> I'm desperately trying to get to the hundreds of baby pics on my compaq that i hope i haven't lost- windows won't boot - so i'm running ubuntu- and i'm following instructions from the only website i see that helps extract files from the hard drive,([http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/))  but in the instructions it tells me that the details for why the hard drive won't mount should include a choice 2  in the message, which includes the commands to force Ubuntu to use that drive even though there's something wrong.
i have no choice 2.
mine says: "windows is hibernated, refused to mount. Failed to mount '/dev/sda1':Operation not permitted the NTFS partition is hibernated. Please resume and shutdown Windows properly, or mount the volume read-only with the 'ro' mount option, or mount the volume read-write with the 'remove_hyberfile' mount option. For example type on the command line: mount -t ntfs-3g/dev/sda1 /media/disk-1 -o remove_hyberfile" 
When I type that command line in this is what appears on the screen: 
root@ubuntu:~# mount -t ntfs-3g/dev/da1/media/disk-1 -o remove_hiberfile
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
root@ubuntu:~# 

the directions on the website say after the last step i should be able to get into the media files but it still says volume cannot mount.
this might as well all be greek to me. i'm so distraught at losing my photos, and since i'm rather computer illiterate i'm hesitant to try anything that would cause further damage.
If anyone has any ideas, i'd be indebted to you forever!!!!!!

I see two typos that might be keeping this from happening.  You have dal instead of sda1  and also hiperfile instead of hyberfile.  Try it again and see what happens

---

### Post by Coreigh on 2009-02-17
You may have better luck if you can install the Windows hard disk in a Windows computer - *as a secondary disk* -. Start Windows let it finish booting, DON'T DO ANYTHING, and then shut Windows down NORMALLY. This will set the disk state to closed or properly shut down, and that in turn should allow you to easily mount the disk from a LiveCD and retrieve your files.
Obviously you could retrieve the files while you have it in the other Windows computer but you need to be careful about how you access the disk. You don't want to accidentally partition or format and destroy the files you are trying to save.

---

### Post by mwing on 2009-02-17
perryg- thank you- i'll try that! 
coreigh- do i boot from the windows disk? will it do that w/out using an install or repair option? i'm afraid to even put the disk in- i don't want to accidentally restore to factory settings...
thanks for your speedy replies!!!

---

### Post by caljohnsmith on 2009-02-17
While you are still on the Live CD, how about trying:
```
sudo mount -t ntfs-3g /dev/sda1 /mnt -o remove_hyberfile
```
If it doesn't return an error, then do:
```
nautilus /mnt & 
```
And you should be able to browse your files. Let me know if that works or not.

---

### Post by mwing on 2009-02-17
thank you! i'll be trying these things as soon as my baby isn't sleeping on me..i didn't expect replies to be so fast!

---

### Post by az on 2009-02-17
If you have the slightest trouble reading this drive, I strongly suggest you image it before continuing.  Once you have done that, you work on getting the data back from the image.

If the drive has sustained hardware damage, you may damage the filesystem on it if you try to fix it there.

See [http://help.ubuntu.com/community/DataRecovery](http://help.ubuntu.com/community/DataRecovery)

But, in a nutshell, you use Gnu ddrescue to copy the drive from the original drive to the destination drive (or an image file on the destination drive)  So you need to obtain a drive with lots of space on it;  more space than the total size of the original drive to store the image as well as the copy of the data you are saving.

---

### Post by mwing on 2009-02-17
az- would it be safe to try the above suggestions first? could i damage it by trying to get to the files through ubuntu?apparently the hard drive is unreachable because it's stuck in hibernation. 
i checked the link and think i understand what you're saying, but it looks way too over my head.. i was going to hook up an external hard drive and then could try what that link tells me to do.. i'm just not sure i'll be able to follow it w/out knowing more...

---

### Post by alejobar on 2009-02-17
Hi mwing,

I had similar problems with Ubuntu cd when I'm trying to access a a windows drive, and sometimes its because windows didn't close correctly. So in those cases I use Puppy linux live cd, you can find my version here [http://murga-linux.com/puppy/viewtopic.php?t=35753]("http://murga-linux.com/puppy/viewtopic.php?t=35753")

---

### Post by az on 2009-02-17
> **mwing said:**
> az- would it be safe to try the above suggestions first? could i damage it by trying to get to the files through ubuntu?apparently the hard drive is unreachable because it's stuck in hibernation. 
i checked the link and think i understand what you're saying, but it looks way too over my head.. i was going to hook up an external hard drive and then could try what that link tells me to do.. i'm just not sure i'll be able to follow it w/out knowing more...

Mount it read-only as the article you linked suggests.  If you can see your files, but they don't copy - like the transfer hangs and won't progress, image the drive.  

If you try to mount it read only, but it still doesn't work because the filesystem needs fixing, abort!  Do not try to fix the filesystem on a drive that you suspect is damaged physically;  that will cause you to lose lost of data.

So basically proceed as you would have, but give up very easily.  Move on to the less dangerous technique of imaging the drive.

---

### Post by mwing on 2009-02-17
> **alejobar said:**
> Hi mwing,

I had similar problems with Ubuntu cd when I'm trying to access a a windows drive, and sometimes its because windows didn't close correctly. So in those cases I use Puppy linux live cd, you can find my version here [http://murga-linux.com/puppy/viewtopic.php?t=35753]("http://murga-linux.com/puppy/viewtopic.php?t=35753")

your links don't work but i'm assuming i can download from the puppy linux website? why can that get through when ubuntu can't? just curious..

---

### Post by alejobar on 2009-02-17
> **mwing said:**
> your links don't work but i'm assuming i can download from the puppy linux website? why can that get through when ubuntu can't? just curious..

mmm that's weird, I just test the link myself twice and it took me to the page, anyway here's the link to the direct file [http://www.megaupload.com/?d=YBQQX8GF]("http://www.megaupload.com/?d=YBQQX8GF") or just copy and paste this in to your browser:
[http://www.megaupload.com/?d=YBQQX8GF](http://www.megaupload.com/?d=YBQQX8GF)

My guess is that since Puppy uses another window manager its easier to have complete access to discs and files

---

### Post by caljohnsmith on 2009-02-17
> **alejobar said:**
> mmm that's weird, I just test the link myself twice and it took me to the page, anyway here's the link to the direct file [http://www.megaupload.com/?d=YBQQX8GF]("http://www.megaupload.com/?d=YBQQX8GF") or just copy and paste this in to your browser:

[http://www.megaupload.com/?d=YBQQX8GF](http://www.megaupload.com/?d=YBQQX8GF)
I'm curious too, why do you think Puppy Linux is better suited in this case to do file recovery? Puppy Linux comes with far fewer basic system programs/commands/functionality than Ubuntu, so what would be the advantage? Is there something special about your particular variation of Puppy Linux?

---

### Post by Coreigh on 2009-02-17
Excellent advice from az, I have made the mistake many times not having an image of the drive in question.

In essence it may not be too late to do a back-up. ;)

---

### Post by mwing on 2009-02-17
can anyone who is still hanging out tell me if it's safe to try the suggestions made above w/ubuntu?? or should making an image be priority? can i mess up my hard drive trying to get to it through ubuntu? 
and if i put my windows xp cd in can i boot from the cd w/out installing?
and is my husband right that i should've gotten a mac?? lol

---

### Post by mwing on 2009-02-17
> **Coreigh said:**
> Excellent advice from az, I have made the mistake many times not having an image of the drive in question.

In essence it may not be too late to do a back-up. ;)

ok...is backing it up something i could realistically do if my computer knowledge is next to nothing? perhaps i'll wait for my computer expert brother to come home from college....

---

### Post by caljohnsmith on 2009-02-17
It is always safest to do a complete image of the HDD first, but in many cases it is not necessary and of course can take a long time. If you have an extra HDD that you can image the Windows drive to, you could do that first if you want to be as safe as possible. But if that is really inconvenient, I would suggest going ahead and trying to mount the partition and seeing if you can access your files first. If you get some errors that make it obvious there are more serious problems with the Windows file system, then definitely doing a backup image of the drive is a really good idea.

---

### Post by Perryg on 2009-02-17
> **mwing said:**
> can anyone who is still hanging out tell me if it's safe to try the suggestions made above w/ubuntu?? or should making an image be priority? can i mess up my hard drive trying to get to it through ubuntu? 
and if i put my windows xp cd in can i boot from the cd w/out installing?
and is my husband right that i should've gotten a mac?? lol

Well I don't think a MAC, but Ubuntu installed instead of Windows.  Only kidding.  All of these suggestions carry with them their own problems.  My guess is that these pictures are very important to you.  If you do not feel comfortable doing any of the suggested methods I suggest that you take the PC to an expert and have them recover the data that you need.  Other wise go very slowly in the recovery process.  Mistakes like typos can lead to loosing the data you want to save.  Please keep us posted on what is happening.

---

### Post by alejobar on 2009-02-17
> **Perryg said:**
> Well I don't think a MAC, but Ubuntu installed instead of Windows.  Only kidding.  All of these suggestions carry with them their own problems.  My guess is that these pictures are very important to you.  If you do not feel comfortable doing any of the suggested methods I suggest that you take the PC to an expert and have them recover the data that you need.  Other wise go very slowly in the recovery process.  Mistakes like typos can lead to loosing the data you want to save.  Please keep us posted on what is happening.

PerryG is right, you have to do only things you confortable and capable doing. If you feel the command line its complicated just try other simplier method, I know what its having your baby pics in the computer, I had the same problem a few months a go and thanks God I was able to save them!. And like I told you for some reason I was able to access the hard drive using Puppy linux, and before that I tried Ubuntu, Knoppix and Mandriva with no luck at all. I hope your hard drive is ok and it's only a Windows problem.

And as soon you have your pics saved in to another hard drive I would erase everything in the hard drive and install Ubuntu 8.10 in it.

---

### Post by mwing on 2009-02-17
ok-- if a typo could mess w/the pics, i certainly don't want to risk it, as i've obviously already made typos! I was hoping to retreive them myself only because of cost issues.. then again, baby pics are priceless. so thanks everyone- i'll keep you updated once i make up my mind! :)

---

### Post by mwing on 2009-02-17
WHOA..i can't believe this but i turned on my computer to try your suggestions and windows (after a long time and lots of beeping)...booted!!! it's running, but very slowly. I am sending my husband off to get an external hard drive now and hopefully if the computer stays healthy for the next few hours i could be ok!!! i'll let you know, and i'm so grateful for all of the wonderful people on this forum! i think i'll be using ubunto rather than windows from here on out.

---

### Post by Perryg on 2009-02-17
> **mwing said:**
> WHOA..i can't believe this but i turned on my computer to try your suggestions and windows (after a long time and lots of beeping)...booted!!! it's running, but very slowly. I am sending my husband off to get an external hard drive now and hopefully if the computer stays healthy for the next few hours i could be ok!!! i'll let you know, and i'm so grateful for all of the wonderful people on this forum! i think i'll be using ubunto rather than windows from here on out.

GREAT!  :-)  Good luck and get them as soon as you can.  Let us know.  After you are sure that you have everything that you need give Ubuntu a try.  Not a bad OS!

---

### Post by mwing on 2009-02-19
I bought an external hard drive and was able to successfully dump all pictures into it.phew. now i'm going to try your suggestions to see what the problem was. thanks sooooo much for all of your help!

---

