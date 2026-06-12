---
title: "Fight to the death (cannot find ex3 filesystem on hda7)"
date: 2005-06-22
forum: Desktop Environments
---

### Post by Dave_is_sexy on 2005-06-22
FATAL: Cannot find ex3 filesystem on hda7

OK, that would be bad. I've not caused that, but did just start win2k... and it will have. As you may see from my earliest threads win2k has a habbit of finding and destroying ex3 filesystems on my system. I'm not too sure why.

Now for some reason, what should be called hda4 is actually hda7. There are only 5 partitions and they go like this:

 | /boot | empty | win2k | winxp | / | ntfs |     The last 3 are logical


Explore2fs seems to know that is should be hda4. 
Naturally the other boot modes don't work because it lost the whole filesystem.

Also, I have a feeling I'm going to need to know how to get the text from that command line screen into a text file... on the harddrive it can't find  ;-)  or on /boot that'll be fine too there's 60mb free there

---

### Post by uidzer0org on 2005-06-22
try cfdisk and see what the partition shows up as...

---

### Post by az on 2005-06-22
Have you changed your partition table recently, by adding or removing partitions?

---

### Post by Dave_is_sexy on 2005-06-22
No, I actually didn't do anything. I did look at them in partition magic, but didn't do anything. It's more likely to be window's fault.

However, cfdisk says that / is on hda6. Great. It's not been there before. Why would the fourth partition be called 6? the logical  partition is partition 3, so / should be on 5. Ah well i'm sure it'll find its way there by itself somehow  ;-) 

So, we want to do some super advanced terminal stuff - and tell it that they keyboard is dvorak first  :smile: 

Thanks guys!

---

### Post by Dave_is_sexy on 2005-06-22
Ahha. Got my Fstab! 

> /dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda6        /mnt/cache  ntfs    ro,user,auto,umask=0222  0       0
/dev/hda2        /mnt/win2k  ntfs    ro,user,auto,umask=0222  0       0
/dev/hda5        /mnt/winxp  ntfs    ro,user,auto,umask=0222  0       0
/dev/hdb1        /mnt/data  ntfs    ro,user,auto,umask=0222  0       0
/dev/hdc        /media/cdfs   cdfs	ro,user,noauto  0       0

I knew it was on hda7 before! How weird that it would move. cfdisk says it's now on 6... which is cache. so they must've switched places. 

So i need to....?

sudo gedit hda6/etc/fstab ?

Somehow... from CD?

EDIT: or renaming hda6 to hda7 would also be fine

---

### Post by Dave_is_sexy on 2005-06-22
OK I can't run gedit cos it needs X. D'uh i should've thought of that. I'm completely open to alternatives

---

### Post by davahmet on 2005-06-22
[QUOTE=Dave_is_sexy]OK I can't run gedit cos it needs X. D'uh i should've thought of that. I'm completely open to alternatives[/QUOTE]
 When you can't get to your favorite text editor, there's always vi.

---

### Post by Dave_is_sexy on 2005-06-22
But I have no X environment. I just wanna alter a text file by a bit of terminal language. Current plan is to put the fstab i want on an ntfs drive and cp it over the top of the wrong one

but i don't know how to do this from CD (cos it doesn't know where the cp program is on the harddrive), or haw to specify absolute volumes

cp hda1/fstab hda...........

wait a second. if the kernel can't find the filesystem, it's not reading fstab at all. 

Something else needs changing as well. Something I don't know about.

I think i'd just like to rename hda6 to hda7 and vice versa

can that be done? maybe in cfdisk?

EDIT: oh right. vi looks cool, I will learn it's basics shortly  :smile:  ..but not for this

---

### Post by davahmet on 2005-06-22
hmm..also, where is your swap partition?  Not having a swap partition available can lead to all sorts of hard-to-debug, weird behaviors.

---

### Post by Dave_is_sexy on 2005-06-22
Oh. I didn't make one yet, although i did stat a thread about how to add one. The disk was complicated enough as you can see. 

Shortly, when i understand things a bit better, i'll be restructuring the disks.

It seems to be that hd0 and the kernel have formed an alegence to look for / on hda7. must tell them to look on 6, or re-name 7 to 6

EDIT: I'd still like to know why it moved - but not urgently

---

### Post by davahmet on 2005-06-22
[QUOTE=Dave_is_sexy]But I have no X environment. I just wanna alter a text file by a bit of terminal language. [/QUOTE]
Vi doesn't need X, but I must warn you, vi isn't the most intutive text editor.  You will definitely want to look through 'man vi' if you're not familiar with it.

> 
Current plan is to put the fstab i want on an ntfs drive and cp it over the top of the wrong one

Really, really bad idea.  The bootloader expects the fstab to be in a standard, safe location, and on a safe, reliable filesystem.  Putting fstab on ntfs is really dangerous.  The problem is that no amount of software coaxing, tweaking or any other tricks will get aroudn the fact that NTFS is a very poorly designed filesystem.  I say this not from a bias against Microsoft, but from experience engineering filesystems.  Lately I have been working on a project to merge Windows components with Linux on firmware, so I have had way more exposure to Microsoft filesystem problems than I'd ever want.  It really is bad enough that I am currently searching for another job just to escape the self-induced nightmare that comes from mixing the two.

In the short viewpoint, Windows is great for what it was meant to do, as is Linux.  Do not mix the two and although you can share data between the two, be extremely careful about twidding with hybrid filesystems.

---

### Post by Dave_is_sexy on 2005-06-22
No, no. i was just going to write a new fstab in notepad then save it. (on ntfs cos i can't get to the ex3)

then copy it to where it should be via terminal

but that wont work. i need to re-name the disk back to hda7 somehow

---

### Post by Dave_is_sexy on 2005-06-22
I'm just gonna make a new partition, it'll increase all the numbers by 1  and then i'll edit the windows boot.ini manually

That'll work (prepares for it to go wrong)

---

### Post by Dave_is_sexy on 2005-06-22
OK that didn't work

---

### Post by Dave_is_sexy on 2005-06-23
Maybe I'd be better making a fresh install then copying my existing one over the top of it somehow? The rational thing to do for that would be a live CD, but the damn things don't let you do anything cos of file permissions

---

### Post by Dave_is_sexy on 2005-06-23
Perhaps re-installing /boot (it's seperate) and leaving / where it is would work, but specifying that it is already there. Any thoughts on that one?

---

### Post by sbassett on 2005-06-23
Dave;
  Have you given anymore thought to Davahmet's suggestion of using VI to edit /etc/fstab and /boot/grub/menu.lst? For the limited editing that you will have to do, there are only a few commands/keys you will have to know. The arrows will manuever you around the document, pressing INSERT will enter you into editing mode (pressing insert while already in editing mode will toggle between insert and replace), pressing ESCAPE will remove you from editing mode.
The following commands can then be used, while out of editing mode only:

:q  -  quits
:q! - quits forefully
:wq - quits and saves
:wq! - quits and saves forcefully

and that should be it. :q! helps if you make a small mistake a don't remember what was on that line you just erased.

---

### Post by Dave_is_sexy on 2005-06-23
yeah but fstab is on hda7. and it doesnt know where hda7 is. does it? is that what's wrong?

---

### Post by Dave_is_sexy on 2005-06-23
I can't print the output cos knoppix has a habbit of preventing me saving antything anywhere, and telling cfdisk to save to a file

> /boot/table

doesn't work. nor does

> hda1/boot/table.

I'm not sure why.

But anyway i read the table and it said:

> hda1 - ex3 [/boot]

hda2 - ntfs (win2k)
hda5 - ntfs (winxp)
hda6 - ex3 [/]
hda7 - ntfs [] (cache)

I'm not sure why hda7 has an empty mount point. i put windows names in () for matching up to fstab. and it doesn't mach at all.

fstab says:

> /dev/hda7 / ext3 defaults,errors=remount-ro 0 1
/dev/hda1 /boot ext3 defaults 0 2
/dev/hda6 /mnt/cache ntfs ro,user,auto,umask=0222 0 0
/dev/hda2 /mnt/win2k ntfs ro,user,auto,umask=0222 0 0
/dev/hda5 /mnt/winxp ntfs ro,user,auto,umask=0222 0 0
/dev/hdb1 /mnt/data ntfs ro,user,auto,umask=0222 0 0

with cds and stuff deleted to make it easier to read. hda6 & 7 are the wrong way round. i'd like to just cp a new fstab over the old one, but don't know if that will work, or how.

Thanks
Dave

---

### Post by Dave_is_sexy on 2005-06-23
la lal a...

why doesn't this work?

```
cp /dev/hda2 /fstab /dev/hda6 /etc/fstab
```

That should copy a good fstab file from C:\ to where it should be.

---

### Post by Dave_is_sexy on 2005-06-23
OK For reference:

I copied the new fstab over the old.. and same error. 

So, looks like i was right initially in that it's something more than fstab. 

Yep

Why would that be? Kernel? Hope not. Maybe grub's just geting it wrong to start with?

Yep. Edit grub's menu list file to point to hda6 intead of 7 in combi with fstab changes, and all s good.

Now that's learning

---

### Post by davahmet on 2005-06-23
[QUOTE=Dave_is_sexy]OK For reference:

I copied the new fstab over the old.. and same error. 

So, looks like i was right initially in that it's something more than fstab. 

Yep

Why would that be? Kernel? Hope not. Maybe grub's just geting it wrong to start with?

Yep. Edit grub's menu list file to point to hda6 intead of 7 in combi with fstab changes, and all s good.

Now that's learning[/QUOTE]
 Congratulations, Dave.
You learned it the same way most of the Linux Masters did, by breaking things, asking lots of questions, experimentation, and then finally solving it.  Not a very fun way to learn your way around Linux, I'll admit, but you'll be guiding others around Ubuntu in no time at all. :)

---

