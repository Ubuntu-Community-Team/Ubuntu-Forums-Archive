---
title: "How to save/move my entire Ubuntu Partition?"
date: 2009-06-22
forum: General Help
---

### Post by PsychedelicWonders on 2009-06-22
Ok here is the deal, I've changed so much in Ubuntu and finally got it to the point that I just love and it took many many months as you all know.
 
Now the HDD that its on is completely full because its just a 40g sharing with XP Pro.
 
Now I am going to be upgrading to Either Windows 7 or Vista Ultimate 64, here as soon as I can, so I will end up using much more space than XP Pro took up, so Ubuntu is going to have to get moved until I can buy a big enough HDD to keep and run both OS off of successfully.
 
Now I normally dont like putting my OS **** on the same HDD as my media HDD for corruption reasons.
 
But I do have a 500g internal HDD also that is only reserved for media right now, and there is like 430g of free space.
 
So can I just move the entire Ubuntu parition to my 500g HDD temporarliy?  Do I really need to worry about any Ubuntu files corrupting any of my media?
 
thanks.

---

### Post by LoloftheRings on 2009-06-22
What about simply copying all files in the Ubuntu partition to your 500GiB HDD?
You could also use compression, see the 'tar' command :D

---

### Post by PsychedelicWonders on 2009-06-22
> **LoloftheRings said:**
> What about simply copying all files in the Ubuntu partition to your 500GiB HDD?
You could also use compression, see the 'tar' command :D
 
But because I need to pretty much use the entire 40g HDD for my new Windows 64 upgrade and Adobe Master Collection, I need to completely move Ubuntu onto the 500g until I buy a 160g to put all of the OS back on the same HDD.
 
I need it to run like normal, so I dont think I want to compress it do I?
 
Make sense?
 
I'm not worried about the space, there is plenty of that.
 
Its kind of like a permanent, temporary move...
 
Should I be concerened about any corruption issues with mixing my Ubuntu partition to my media drive?

---

### Post by PsychedelicWonders on 2009-06-24
bump

---

### Post by surfed on 2009-06-24
I have done this with other distros before. Boot with liveCD, Resize your media drive to make space for ubuntu, create new partitions (/ swap & home), format them, mount your old partitions in /mnt/old , mount new partitions in /mnt/new, do a: cp -aR /mnt/old /mnt/new, edit /mnt/new/etc/fstab, edit /boot/grub/menu.lst, reinstall grub, pray.
:)

if you need more detailed help let me know.

---

### Post by PsychedelicWonders on 2009-06-25
> **surfed said:**
> I have done this with other distros before. Boot with liveCD, Resize your media drive to make space for ubuntu, create new partitions (/ swap & home), format them, mount your old partitions in /mnt/old , mount new partitions in /mnt/new, do a: cp -aR /mnt/old /mnt/new, edit /mnt/new/etc/fstab, edit /boot/grub/menu.lst, reinstall grub, pray.
:)

if you need more detailed help let me know.

:confused:

I'm not able to just move the entire parition any easier eh?

Can you just go a little deeper with the walk through, I'm not that advanced yet :)

Should I worry about any corruption of my media files by transfering the ubuntu partition?

---

### Post by starcannon on 2009-06-25
I have never tried this, but I think remastersys can do this:
[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

Clonzilla should be able to do it as well.
[http://clonezilla.org/](http://clonezilla.org/)

Oh and dd can do this as well.
[http://ubuntuforums.org/archive/index.php/t-997443.html](http://ubuntuforums.org/archive/index.php/t-997443.html)

I'd test it out on the new hdd before wiping the old one though.

---

### Post by surfed on 2009-06-25
in any case you need to BACKUP your media.

---

### Post by PsychedelicWonders on 2009-06-27
Does anyone have anything on this for sure?

No offense, but if youre not sure, I'm not using it to mess with my hard drives.

This is becoming an issue now because it is affecting my web browsing because the HDD is full.

So does anyone know how to successfully transfer/move the entire Ubuntu partition?

Both HDD's are mounted in Ubuntu already if that helps...

**Also, should I be concerned with corrupting my media HDD with my Ubuntu partition?**

---

### Post by -kg- on 2009-06-28
A very, very good tutorial on this subject and Partimage/Clonezilla can be found at the following link:

[http://www.dedoimedo.com/computers/free_imaging_software.html]("http://www.dedoimedo.com/computers/free_imaging_software.html")

He shows step-by-step how to use the Clonezilla Live CD to create an image, with a good reference about what imaging is all about at the beginning and links to other resources (written by the author) included.

I should think that you would be able to recreate partitions on your other drive, copy the files from the first to the second, and have it up and running.  After all, what you're doing is cloning from one drive to another (hence the name, *Clone*zilla!).  All you should have to do is re-install GRUB from the new location so that it can find itself. (Right? Somebody?)

---

### Post by surfed on 2009-06-28
How i mentioned ealier, only grub and fstab will need to be reconfigured. He will need to resize his 500g HD ( i am asuming it has one big partition right now).
The above link to [http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html) will give you all the info you need to resize/move/copy partitions. If you post the output of 

sudo fdisk -l

and less /etc/fstab

i can help you more.

---

### Post by PsychedelicWonders on 2009-06-28
> **surfed said:**
> How i mentioned ealier, only grub and fstab will need to be reconfigured. He will need to resize his 500g HD ( i am asuming it has one big partition right now).
The above link to [http://www.dedoimedo.com/computers/free_imaging_software.html](http://www.dedoimedo.com/computers/free_imaging_software.html) will give you all the info you need to resize/move/copy partitions. If you post the output of 

> sudo fdisk -l

```
psychedelicwonders@JohnnyScience:~$ sudo fdisk -l
[sudo] password for psychedelicwonders: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004465a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        4463        9327    39078112+   7  HPFS/NTFS
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda3               1        4462    35840983+  83  Linux
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003c9ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS
psychedelicwonders@JohnnyScience:~$ 

```


> and less /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=0ff885db-ddc9-42a1-a15e-0d9544ceeebf none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1 /media/storage ntfs defaults 0 0
/etc/fstab (END) 

```

So what are my 1st steps?

I want to actually move the entire partition for good, not just make an .iso image of it.

It will need to be moved for good until I can upgrade HDD's, which may be up to a few months.  So I want it to be a permanent, but temporary move.

---

### Post by surfed on 2009-06-28
In order to do what you want you will need to resize /dev/sdb1 and create new partitions on it. Now this is easy but there is a small chance that you will loose data on /dev/sdb1 , specially as it is NTFS. 

BACKUP

If you cant dont go on.

---

### Post by PsychedelicWonders on 2009-06-28
> **surfed said:**
> In order to do what you want you will need to resize /dev/sdb1 and create new partitions on it. Now this is easy but there is a small chance that you will loose data on /dev/sdb1 , specially as it is NTFS. 

BACKUP

If you cant dont go on.

I have a 500g WD Passport.  I didnt like any of the software on it and wanted to use it more as a flash drive, so I formatted it to NTFS, I believe I have copied everything, but let me make sure I can now access it...

If I am just drag N' dropping my media HDD onto the passport icon, how do I make it just grab new files, instead of the ones that I already have?  Basically just doing a "quick update" via drag n drop?

Should I worry about any type of corruption of my media HDD by putting my Ubuntu partition on it?

---

### Post by PsychedelicWonders on 2009-06-28
> **surfed said:**
> In order to do what you want you will need to resize /dev/sdb1 and create new partitions on it. Now this is easy but there is a small chance that you will loose data on /dev/sdb1 , specially as it is NTFS. 

BACKUP

If you cant dont go on.

Ok, everything is backed up.

Now how should I go about resizing the 500g HDD exactly?

Just do it all in Gparted? I've done it before, but it was a while ago.

Should I worry about any type of corruption of my media HDD by putting my Ubuntu partition on it?

---

### Post by ahndoruuu on 2009-06-28
> **PsychedelicWonders said:**
> Should I worry about any type of corruption of my media HDD by putting my Ubuntu partition on it?


The answer, being 100% honest, is no.
The fact that you have formatted it to NTFS presents a _miniscule_ risk as sometimes NTFS partitions do not like to be formatted and decide to lose data every now and again.  However I've done this so many times myself and never lost a single bit of data.  Once Ubuntu is installed, as long as you're using it for "normal" purposes I couldn't see any possibility that your media would get corrupted.

And you said you backed it up right? So no worries, just go for it. ;)

---

### Post by PsychedelicWonders on 2009-06-28
Ok, so what is the next step?

I need to use Gparted to make a new partition on the 500g?

Will it just adjust the current partiton, & keep all of the data and just create a new partition?

Or will it completely format & re-partition the thing from scratch?

---

### Post by Geffers on 2009-06-29
> **PsychedelicWonders said:**
> Does anyone have anything on this for sure?

No offense, but if youre not sure, I'm not using it to mess with my hard drives.

This is becoming an issue now because it is affecting my web browsing because the HDD is full.

So does anyone know how to successfully transfer/move the entire Ubuntu partition?

Both HDD's are mounted in Ubuntu already if that helps...

**Also, should I be concerned with corrupting my media HDD with my Ubuntu partition?**

I think gparted should be able to do it OK, there is a liveCD version.

It can copy and paste partitions.

Geffers

---

### Post by PsychedelicWonders on 2009-06-29
> **Geffers said:**
> I think gparted should be able to do it OK, there is a liveCD version.
 
It can copy and paste partitions.
 
Geffers
 
 
So I should do this with my Ubuntu LiveCd & not in my normal Ubuntu?

---

### Post by surfed on 2009-06-29
As your Ubuntu right now is on a seperate hd, you can use gparted from within your current install. To move the data over you will have to boot with live cd.

---

### Post by PsychedelicWonders on 2009-06-29
> **surfed said:**
> As your Ubuntu right now is on a seperate hd, you can use gparted from within your current install. To move the data over you will have to boot with live cd.
 
Ok, so I will go into Ubuntu and make the partitions in Gparted.  
 
Once I do that and boot up from livecd, how do I then go about move the actual partition?
 
Will this be a true "move" or a copy & delete?

---

### Post by Polaris96 on 2009-06-29
Do it with 'dd'.  it's very VERY simple.

Break off a partition on the media drive.  I would use lvm2 to do it, but you can use parted by itself, as well.  Format the new partition.

from the terminal type:

sudo dd if=/dev/[old partition] of=/dev/[new partition]

THAT'S IT.  go have a cup of coffee.

Just remember you might need to mess with your grub settings so your boot loader knows where ubuntu is, now.

cheers.

---

### Post by surfed on 2009-06-29
He will also have to edit /etc/fstab

---

### Post by Polaris96 on 2009-06-29
good point !

---

### Post by t4thfavor on 2009-06-29
I would use ddrescue, and clone my existing drive to my new drive, then use gparted to resize the partition to fill the extra space on tshe new drive.

Done it many times, moved from 40g to 80g to sata 120 to sata 300 always works.

---

### Post by surfed on 2009-06-29
Lets not confuse him :)

sudo dd if=/dev/[old partition] of=/dev/[new partition] 

from a live cd will work great, 
then reinstall grub, edit /boot/grub/menu/lst and /etc/fstab
and all should be rosy.

---

### Post by PsychedelicWonders on 2009-06-29
> **surfed said:**
> Lets not confuse him :)
 
sudo dd if=/dev/[old partition] of=/dev/[new partition] 
 
from a live cd will work great, 
then reinstall grub, edit /boot/grub/menu/lst and /etc/fstab
and all should be rosy.
 
Ok so where do I find the information needed to fill in the blanks up there of [Old Partition] & [New Partition]?
 
So then I just run that code
 
and then run:
 
```
 edit /boot/grub/menu/lst 
```
 
and then finally 
 
```
/etc/fstab
```
 
And then its all set and done by easily running those 3 codes?
 
That will move the parition & then also make the grub now boot Ubuntu from the 500g media hdd?
 
Will my grub menu still look the same to me?

---

### Post by Polaris96 on 2009-06-29
you can find all of your available partitions like this:

cat /proc/partitions

you will see the partition or you just made if you used gparted

There is a graphical partitioner, but I don't know the package name.  Anyone want to weigh in?  Anyway, gparted isn't too hard to use.

have you made any partitions, yet.  we'll walk you through.  It's easy, just tell us where you're at right now, ok?

---

### Post by PsychedelicWonders on 2009-06-29
Ok I'm in Gparted, I've unmounted the 500g, but its not letting me create a new parition, it only lets me either delete or resize/move.

So what exactly do I do to create a 100g partition and leave the other 400 on its own like it is?

This is the location of my 500g...

/dev/sdb1

Also, I would really like to take my Opera browser with me.

I have all of my links, skins & Speed Dial that I edited and spent a lot of hours on.

How would I go about safe-havening my Opera?

---

### Post by Polaris96 on 2009-06-30
OK, you probably have all 500gb in the existing partition.

Shrink that partition and create a new one from the resulting empty space.  Sorry for not being more specific, but i usually use "regular" parted from the command line.  You're probably just as good as me at figuring out the GUI version.  If you freak, just let me know and I'll give you some code n/p.

If you plan on doing this a lot, let me know because then we need to talk about lvm2 - it makes your life easy when your doing lots of partition stuff.  You don't need it if this will be a rare action on your part.

Install an fs on the newly created partition.  If you like ext3, you can code:

sudo mkfs -t ext3 /dev/[new partition name]
you get the new partition name from gparted when you create the partition.

you could also code:

sudo mkfs.ext3 /dev/[new partition]

it's the same thing.  Let me know or else check the man page if you a different fs than ext3, ok?

I wrote a pretty comprehensive "how to" on copying a system image here:

[http://forums.debian.net/viewtopic.php?f=16&t=38374&start=45](http://forums.debian.net/viewtopic.php?f=16&t=38374&start=45)

it's on p.4 and please pardon the arrogant banter all around it.  Look for the Polaris96 posting with a checklist and print it out. (I only wrote the damned thing because some smarty was beating up a guy for the wrong reasons...)

I can be much more specific on doing things.  Let me know where you need more explaining.

btw, you're doing real good, so far.  Also, don't worry about opera - we'll bring it all over in a complete image.  You'll have everything.

---

### Post by PsychedelicWonders on 2009-06-30
> **Polaris96 said:**
> OK, you probably have all 500gb in the existing partition.
 
Shrink that partition and create a new one from the resulting empty space. Sorry for not being more specific, but i usually use "regular" parted from the command line. You're probably just as good as me at figuring out the GUI version. If you freak, just let me know and I'll give you some code n/p.
 
If you plan on doing this a lot, let me know because then we need to talk about lvm2 - it makes your life easy when your doing lots of partition stuff. You don't need it if this will be a rare action on your part.
 
Install an fs on the newly created partition. If you like ext3, you can code:
 
sudo mkfs -t ext3 /dev/[new partition name]
you get the new partition name from gparted when you create the partition.
 
you could also code:
 
sudo mkfs.ext3 /dev/[new partition]
 
it's the same thing. Let me know or else check the man page if you a different fs than ext3, ok?
 
I wrote a pretty comprehensive "how to" on copying a system image here:
 
[http://forums.debian.net/viewtopic.php?f=16&t=38374&start=45](http://forums.debian.net/viewtopic.php?f=16&t=38374&start=45)
 
it's on p.4 and please pardon the arrogant banter all around it. Look for the Polaris96 posting with a checklist and print it out. (I only wrote the damned thing because some smarty was beating up a guy for the wrong reasons...)
 
I can be much more specific on doing things. Let me know where you need more explaining.
 
btw, you're doing real good, so far. Also, don't worry about opera - we'll bring it all over in a complete image. You'll have everything.
 
 
I dont plan on doing partitions often, so I think Gparted works well for me.  Plus I like the GUI interface.
 
So I will resize the  current parition, it will then allow me to create a new based on the remainder I assume.
 
Do I need to have a swap partition?
 
Thanks I can do Ubuntu fairly well... I just wish I understood the code more, sudo, gsudo etc etc.  I dont know what it all means really.  But I can copy & paste pretty well :D
 
I want to permanentally move the Ubuntu partition... so do I really want to move this as an .iso?

---

### Post by surfed on 2009-06-30
No iso's needed here, and yes you want a swap partition.

Shrink /dev/sdb1 with gparted by lets say 50gb. Create a 49gb primary partition and format it ext3 (from within gparted) and create a 1 gb swap partition.
Now you will have sdb1 ~450gb media, sdb2 49gb / and sdb3 1gb swap.
Then from within a live cd enviroment do a :
sudo su
mkdir /mnt/old
mkdir /mnt/new
mount -t auto /dev/sda3 /mnt/old
mount -t auto /dev/sdb2 /mnt/new
cp -aR /mnt/old/* /mnt/new/

the last command will take a while

now edit /mnt/new/etc/fstab ( gedit /mnt/new/etc/fstab ) and replace

UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82
with
/dev/sdb2

and
UUID=0ff885db-ddc9-42a1-a15e-0d9544ceeebf
with
/dev/sdb3

The only thing left to do is to reinstall grub and edit your /boot/grub/menu.lst
I dont have all the grub commands memorized and no time to look it up, i can add this part later or somebody else might help out...

---

### Post by Polaris96 on 2009-06-30
ed's method is slightly different than what I would've said but it will work equally well for you.  I don't bother working in a live CD environment, and I've never had problems.  It won't hurt you to work from a Live CD boot, though, so you may as well do so.  If you use his method, don't follow the checklist I sent you to on the debian site - you'll get confused. (as a side comment, using cp -aR is what the knucklehead on the other board was crying about.  Don't worry about him - cp works just fine)

.iso is definitely not needed.  We'll be mirroring what you have on your existing drive so there's no need to change anything.  Simplicity is key.  We are NOT moving the partition.  We're copying it.  It's the better way.  After we've confirmed it's good, you can overwrite the old one.

swap partition:  If you want to, you can keep the one you're already using.  If you have big RAM, you can even ditch the swap, but I wouldn't.  Creating another 1gb swap on the new drive, as ed suggested is as good an idea as any.

Do you want to keep grub on your original drive or move it to the new one?  Also, keep letting us know where you're at as you post.  It makes it easier to give you the advice that's most relevant.

---

### Post by PsychedelicWonders on 2009-06-30
> **surfed said:**
> No iso's needed here, and yes you want a swap partition.
 
Shrink /dev/sdb1 with gparted by lets say 50gb. Create a 49gb primary partition and format it ext3 (from within gparted) and create a 1 gb swap partition.
Now you will have sdb1 ~450gb media, sdb2 49gb / and sdb3 1gb swap.
Then from within a live cd enviroment do a :
sudo su
mkdir /mnt/old
mkdir /mnt/new
mount -t auto /dev/sda3 /mnt/old
mount -t auto /dev/sdb2 /mnt/new
cp -aR /mnt/old/* /mnt/new/
 
Ok, I think I got it all... so all 6 of those codes are ready to go, I dont have to edit them any more?  Just run them one after another?
 
> the last command will take a while
 
now edit /mnt/new/etc/fstab ( gedit /mnt/new/etc/fstab ) and replace
 
UUID=911f7a70-3beb-46c4-ab0f-1a9b73a67a82
with
/dev/sdb2
 
and
UUID=0ff885db-ddc9-42a1-a15e-0d9544ceeebf
with
/dev/sdb3
 
The only thing left to do is to reinstall grub and edit your /boot/grub/menu.lst
I dont have all the grub commands memorized and no time to look it up, i can add this part later or somebody else might help out...
 
What are the next steps for changing the grub?  Polaris, you mentioned keeping it on the original drive - I plan on completely formating this drive and adding just Windows 7 to it.
 
But however we work it, I still want the grub to list all of the OS like it does now...
 
Once I get an extra few dollars I am going to buy a 160g and put both OS's back on 1 drive and keep my media drive clean.  But I just have to do all of this right now so I can even get my computer to work at this point.
 
Thanks for the help btw guys.

---

### Post by PsychedelicWonders on 2009-07-01
I didnt do the parition last night, I wanted make sure I had all the steps correct for setting up grub again before I did everything else

---

### Post by surfed on 2009-07-01
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

dont forget to edit menu.lst

---

### Post by PsychedelicWonders on 2009-07-05
> **surfed said:**
> [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

dont forget to edit menu.lst

How and what do I do to menu.lst?

I'm going to give this a go right now...

---

### Post by surfed on 2009-07-05
good luck!

---

