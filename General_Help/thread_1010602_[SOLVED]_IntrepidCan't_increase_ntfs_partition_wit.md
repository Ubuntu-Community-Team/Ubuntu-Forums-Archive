---
title: "[SOLVED] Intrepid:Can't increase ntfs partition with gparted"
date: 2008-12-13
forum: General Help
---

### Post by Laysan_A on 2008-12-13
Hi,
I have a 500GB hd with three (now four) partitions (not including the boot partition). The first is a 30GB ntfs windows xp partition, then a (approx) 70GB ntfs partition, then a 1GB swap, then the remainder as ext3 where kubuntu is installed.
I wanted the windows partition to be insignificant, so I left it small, but this is a new system and I am new to linux so I decided a larger partition would be better until I'm better settled-in with kubuntu. 
I downloaded the live cd of gparted and tried to expand the 30GB windows partition but it wouldn't let me. I created a new ntfs partition (the 70GB one) right next to the 30GB ntfs partition by decreasing the size of the linux partition and moving the swap partition, thinking that I could then merge the two into one, but gparted will still not let me resize the 30GB partition.
How can I resize my windows partition to 100GB or so without losing my existing win xp installation?

---

### Post by cdtech on 2008-12-13
Booting from the Live gparted CD, you should have complete access to the drive. Make sure you unmount the device.

---

### Post by 2hot6ft2 on 2008-12-13
Like cdtech said use the livecd you're trying to do it while it's mounted. By the way after you resize it boot into windows since it will want to run a chkdsk on it since it's changed. You wont have to tell it to it will do it before windows starts just let it.

30GB is plenty for xp that's what mine is.

---

### Post by -kg- on 2008-12-13
According to the thumbnail snapshot you supplied, I notice that the second line of the info says that the very next partition is an extended partition.  You then created your second ntfs partition *inside* the extended partition, making it a logical partition instead of a primary.

The reason you couldn't increase the size of your original ntfs partition is that you had no room to do so.  If you want to increase the size of your primary ntfs partition, you are going to have to make room to do so.

First (hopefully, you haven't put any critical information in it) you need to delete your 2nd 70 GB partition.  You then will need to shrink the extended partition, giving you free space that is *not* contained in the extended partition.  Then, you should be able to expand your primary ntfs partition into that free space.

---

### Post by 2hot6ft2 on 2008-12-13
Personally I would leave the xp partition at 30GB but the way to do what you're wanting would be to delete the 70GB partition right next to xp's and then resize the xp partition. You're going to have a problem trying to merge them.

Yeah, what he said... Your pic is too fuzzy for me to make all that out, I'm old, my eyes are too.

---

### Post by -kg- on 2008-12-13
An addendum:

Since I posted my answer, a couple of more people posted as well.

> Booting from the Live gparted CD, you should have complete access to the drive. Make sure you unmount the device.

Yes, and you shouldn't have to unmount the partitions when using the GPartEd LiveCD.  Being set up exactly for the purpose of editing partitions, the Live CD is set up to not mount any partitions.

> By the way after you resize it boot into windows since it will want to run a chkdsk on it since it's changed. You wont have to tell it to it will do it before windows starts just let it.

30GB is plenty for xp that's what mine is.

Yes, always a good idea to run chkdsk when performing a disk operation.  As matter of fact, I would have that partition backed up before I performed it, personally.  I *hate* losing my data and information.

BTW:  30GB is a pretty good size for an XP installation, but if you will look at his snapshot, you will see that his 30 GB ntfs partition is almost full to capacity.  Makes for a helluva time trying to defrag it!

---

### Post by 2hot6ft2 on 2008-12-13
Yeah, I noticed that. Must be a collect all place either that or he never cleans out the garbage.

Edit: If it's a new system then why is xp taking up so much space? Perhaps mp3's, movies or something. I would never trust windows to keep that much stuff safe.

---

### Post by 2hot6ft2 on 2008-12-14
Here's mine with XP Pro Ultimate on the left.

Hmmm, didn't know about that free space I'll have to fix that. One more thing the 30GB xp is on my laptop this is the desktop in case one of you caught that.

---

### Post by -kg- on 2008-12-14
> Yeah, what he said... Your pic is too fuzzy for me to make all that out, I'm old, my eyes are too.

Don't feel bad...I'm no spring chicken myself.  I've used various partition editors for so long (I still have some earlier versions of Partition Magic) that I recognized the extended partition by it being indented from the rest.

> If it's a new system then why is xp taking up so much space? Perhaps mp3's, movies or something. I would never trust windows to keep that much stuff safe.

It would be a simple matter to copy everything over to the ext partitions.  Linux will access that partition; then it's just a matter of copying everything over.

> Hmmm, didn't know about that free space I'll have to fix that.

It seems to be an idiosyncrasy of GPartEd that it will leave a small free memory space like that.  Be careful when you expand it, though; I have had one disaster where *somehow* I managed to overlap partitions.  I had to completely wipe the hard drive and repartition and reinstall everything.

:sad:

---

### Post by 2hot6ft2 on 2008-12-14
Looks like he used a cell phone to take the pic....lol.

Yeah, I would move all the stuff that isn't needed by xp to the ext partition along with anything on the 70GB one. I keep a ntfs partition to keep files on so both OS's can get them and they're not in the same partition with any OS.

Since it's only a little < 8 MB I think I can live without it. I have some old partition magic myself it sure came in handy for windows and the old days. Anymore I don't even bother installing it.

---

### Post by -kg- on 2008-12-14
> I keep a ntfs partition to keep files on so both OS's can get them and they're not in the same partition with any OS.

I always used at least two Windows partitions; one for the OS itself and one for software installs and data.  It makes for much better control of fragmentation/defragmentation and, if the OS install got hosed (and I had that problem from time to time), you could reinstall the OS and not lose data or jump through hoops trying to back up or reinstall it.

Considering that Laysan_A hasn't replied yet, we can't know what's taking so much space in his Windows installation.  If it's data (i.e., mp3s (I have nearly 25 GB of mp3 files alone) or movies (I have even more of those...I have been involved in video editing projects)), then he might want to transfer that to the logical ntfs partition, at least until he completes migration to Linux.  But if it's installed software (which is a little hard to believe, and if he just can't live without anything that he has) then he's going to have to expand that partition to give himself more room.  Otherwise, he could free up space in the partition by uninstalling unneeded software.

Those, of course, are the only options if he is to maintain a healthy Windows installation and/or partitions.  Even Linux could not be healthy for long under such conditions.

---

### Post by Laysan_A on 2008-12-14
Hi everyone, thanks so much for responding!

First, I'm pretty new to Linux, and I'm really not too sophisticated a win user either.

The image (I really apologize for that) is fuzzy because I was struggling to comply with the site's image attachment restrictions. I reduced the size by 2x, reduced it to eight bit, and still it seemed too large. I said to hell with it and uploaded it anyway and somehow the size reported by the forum became significantly smaller than that reported by my image program's properties output. Don't know what that was all about, but it's done now...

As for what's on my hard drive...boy, you guys are nosy, aren't you? :)

I put a couple of dvds on there because I'm still unsure about the Linux alternatives - it'll take a while. I also have a (bad) habit of keeping just about every program installer I get off the web in a folder on my desktop. It's wasteful of disk space, but when I do a backup I get a fresh copy of all my most recent installers in case I need to reinstall Windows.

> According to the thumbnail snapshot you supplied, I notice that the second line of the info says that the very next partition is an extended partition. You then created your second ntfs partition inside the extended partition, making it a logical partition instead of a primary.
 
 The reason you couldn't increase the size of your original ntfs partition is that you had no room to do so. If you want to increase the size of your primary ntfs partition, you are going to have to make room to do so.
 
 First (hopefully, you haven't put any critical information in it) you need to delete your 2nd 70 GB partition. You then will need to shrink the extended partition, giving you free space that is not contained in the extended partition. Then, you should be able to expand your primary ntfs partition into that free space

Yeah, I have no idea what an extended partition is. I assumed it was just a some kind of virtual construct - a way for the software to organize the drive, rather than an actual partition. I'm pretty sure I didn't try to manipulate in any way. The 70GB partition has nothing on it. It was intended as just a transitional partition to create a "more compatible" space next to the ntfs windows partition.

Yeah, I thought 30GB would be a good size too. When I'm more settled-in with kubuntu I'll likely reclaim the space.

I'm afraid I don't know the difference between a primary and logical partition. 

Okay,  I'm going to try removing the 70GB partition it took so long to create and try shrinking the extended partition.

A couple more questions while I'm at it. I have an amd64 system with only 2GB of ram. How big would you recommend I make my swap? I've seen recommendations for making a separate /home partition (I believe there's a selectable attribute for that in gparted?). It seems like a reasonable customization providing it doesn't create more hassles for me. Is it a good idea, and if so, how would you recommend I divy-up my ext3 partition?

Oh, if I lose the data on any of these partitions it's not a huge deal, just a hassle.

Thanks for all your help.

See the (hopefully) improved version of my snapshot below.

---

### Post by -kg- on 2008-12-14
Hi Laysan;

> First, I'm pretty new to Linux, and I'm really not too sophisticated a win user either.

Hey...all of us were in that position at one time or another.  I still have to have help now and again, and I've been into computers (though not Linux) since the early '80s (when things were a lot simpler).

> As for what's on my hard drive...boy, you guys are nosy, aren't you? 

Yep! ;)

Have to be, really.  The more information we have, the better advice we can give.  If your Windows partition was substantially empty, I would have advised you not to worry about it.  That a 30 GB partition was almost full told me that you had a substantial amount of data on it, and if that data was critical, it was incumbent on me to advise you to back it up somewhere before performing disk operations on it.

> I put a couple of dvds on there because I'm still unsure about the Linux alternatives - it'll take a while. I also have a (bad) habit of keeping just about every program installer I get off the web in a folder on my desktop. It's wasteful of disk space, but when I do a backup I get a fresh copy of all my most recent installers in case I need to reinstall Windows.

Oh, I have that bad habit myself, though I do it in a different partition.  With some programs (especially the pay-fors that you download from an emailed link) it's a real good idea to save them somewhere, along with a text-based copy of your email with the registration number and all in case you have to re-install them, as you said.

If you're going to do that, though, you want to have them in another partition...preferably on another physical hard drive, and most preferably on a CD-ROM.  What if something disastrous happened to your installation, like a hard drive crash?  You would no longer have access to *anything* stored on that hard drive and you would lose it all!  It wouldn't matter that you had it all backed up...you couldn't access it and it would do you no good.  Let me tell you...been there; done that...and it ain't fun!

I have 4 separate hard drives; 3 internal to my desktop and 1 external.  I have all my critical files redundantly backed up on my two large (1 TB a piece) hard drives (1 the external, which of course is portable).  If I have a hard drive crash, I at least have backups of all my critical information, and though it would be inconvenient, I can pretty much put it back like it was.

> Yeah, I have no idea what an extended partition is. I assumed it was just a some kind of virtual construct - a way for the software to organize the drive, rather than an actual partition. I'm pretty sure I didn't try to manipulate in any way. The 70GB partition has nothing on it. It was intended as just a transitional partition to create a "more compatible" space next to the ntfs windows partition.

I understand.  Though I'm somewhat of a newbie to Linux, disk drives, partitions and file systems I understand.  I've been dealing with them for years upon years.  OK:

On a physical hard drive, the convention is that you can only have 4 partitions...either 4 primary partitions or 3 primary partitions and an extended partition, which takes up the 4th "space."  In an extended partition you are able to make any number of "sub-partitions," which are called "logical drives."

Under Windows, you can have any number of partitions as long as you have drive letters left to assign to them.  Of course, this will include all partitions on all hard drives you have connected, including removable media.  Under Linux, I'm not sure if there's a limit, but as far as I understand, you are able to have a limitless number due to the disk "naming" conventions (i.e., no "drive letter," but using the "hd(X,X)" or "sd(X,X)" drive naming convention).

Windows (and certain other OSes) will only launch and run in a primary partition.  It used to be that a certain amount of the program had to be within the first few megabytes of the primary hard drive.  I don't know if this is true anymore, but the actual booting system must be (at least the MBR).  Linux (and certain other OSes) will launch and run from a logical partition inside the extended partition, anywhere on any disk or drive that can be made bootable in your BIOS.

If you are to run Windows, you must have at least one primary partition in which to have the Windows OS files.  Windows can access partitions (of the proper format, of course) on a logical drive (which is contained in the extended partition).  You can store files and data there, and you can load software and run it from a logical drive, as well.  Only the OS and files which *must* be installed with the OS in it's partition need to be in that primary partition.

Now on to things more specific to your situation.  I understand that your's is a relatively new system.  Usually, on a new system from the store, the disk drive is formatted into one single primary partition on which Windows is installed.  Your's, however, has been formatted not only with your ext3 and swap partitions, but with an extended partition surrounding the remaining partitions and free space, making them logical.

Now I know that one of the installation selections in the Ubuntu installer is one where the Windows partition is resized so that the required Linux partitions can be created and installed to.  The thing that puzzles me is the extended partition.  Being that I have a good understanding of disks and partitioning, I did my installation using the manual install and creation option, and not all *from* the LiveCD during installation, but part of it from the GPartEd LiveCD (and I shrank the Windows partition with Windows Disk Manager, as I earlier didn't quite trust GPartEd to do this properly).

Somehow, your Windows partition was shrunk (to a very minimal size, and unnecessarily, to "boot" {that's a pun, son! :lol:}) and an extended partition was created, with the Linux partitions created inside it.  I was unaware that the Ubuntu installer would create an extended partition and install itself in logical partitions.  But if not, how otherwise would that extended partition have been created?  That is the question.

How new was the computer when you got it, and exactly how did you install Ubuntu?  Did you use the installer to do it, or did you use the GPartEd LiveCD to initially shrink the Windows partition and/or set up the partitions?  Did you fill the Windows partition to such an extent before or after you installed Ubuntu?

Really, if the Ubuntu installer did all these operations, and if you haven't added significantly to the Windows partition since then, it is my opinion that the partitioning part of the Ubuntu installer needs to be adjusted.  The installer should not shrink the Windows partition to such an extent that there would be so little free space in it, *especially* considering all the room you have on your drive.  Linux *does not need **that*** much space to run, unless you plan on doing multimedia productions or some other disk-intensive activities (I do video editing; hence the massive hard drive space I have).

> Okay, I'm going to try removing the 70GB partition it took so long to create and try shrinking the extended partition.

Of course, it's totally up to you.  My advice would be to boot into Ubuntu and transfer some of the storage files, like the DVD .iso images and installers from your Windows partition to folders on your Linux partition (*Lord knows* you have enough room to do that!).  You could then free up some space in your Windows partition and it might not be necessary to free up space in the Windows partition.

If it was not necessary to expand that partition, then you could leave the logical ntfs partition and, from now on, install software to it and do any other storage in that partition.  As matter of fact, you could do all these operations in Windows, transferring data and files that are not necessary to have on your Windows partition on the logical partition and store them there.

> A couple more questions while I'm at it. I have an amd64 system with only 2GB of ram. How big would you recommend I make my swap?

Convention says that you should make your swap file twice as big as the amount of RAM you have installed.  Sounds good to me, and that's what I've done on my systems.

> I've seen recommendations for making a separate /home partition (I believe there's a selectable attribute for that in gparted?). It seems like a reasonable customization providing it doesn't create more hassles for me. Is it a good idea, and if so, how would you recommend I divy-up my ext3 partition?

Yes, and all the reasons sound right to me.  That way, you can upgrade Linux distributions, and ostensibly install other distributions, without losing your data.  I'm not sure on how to do it though, short of at installation time.  Linux is certainly nothing like Windows, and Windows is what I have the *massive* part of my experience with.

I'm still very much a Linux newbie and am still involved in the learning curve, myself.  There's a wealth of information on the Ubuntu site, the forums, and other sites as well.  Perhaps others will read this and give you information on this question.  Like I said, I know disk drives, partitions, and file systems, but as far as the inner workings of Linux (and how to set up a distribution) I am as much a newbie as you (and possibly more!).

I would not presume to proffer information that I am unsure of myself, only to have that information be wrong.  I'll leave that to others more qualified.

:grin:

Good luck, and if you have any further questions or issues with anything, just post and I'll answer if I can.  I'm sure others will be only too glad to help in their areas of expertise as well.  I've found these forums chock full of helpful information.

Oh, don't forget that you can find a lot of information on this site by using the search function.  Very often you can find what you're looking for in questions that have already been posted.  Go to the search box at the top of the forum pages and type in "separate /home partition" (preferably *with* the quotes) and look down the list.  You may find the answer to those questions in one of the other posts on the site.  If that fails (and I doubt it will), you can also Google it and find information on other sites.

Now, *I* have to go find some information and ask for help.  Seems that somehow the system got configured to mount all my drives, and I don't have the permission necessary to unmount them.  Not particularly a great problem, but I'm an old hacker from way back and too much of a control freak to let something like this pass.

:lolflag:

---

