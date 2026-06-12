---
title: "Is there a way to copy an NTFS/Vista in Ubuntu?"
date: 2009-05-10
forum: General Help
---

### Post by Toshibawarrior on 2009-05-10
Hi all,  I'm wondering if there's a way to copy a whole Vista (NTFS) partition as it is to a new hard drive and making it bootable again. I really don't like Vista, but I need it for work...so my hands are tied here.

Anyway, I tried using GParted LiveCD and it says that there are errors on the partition and won't let me copy it. I read about PartImage, and I'm not quite sure of it's capabilities. I also heard about Hiren's BootDisk and again, I really don't know if it'll work.

Anyway, I need something to copy that partition from inside Ubuntu or from a LiveCD, since that partition is inside a hard drive that I just took out of my laptop, and I don't intend to put it back in. I can make it external though, which I'll do if I find a good program/LiveCD/app to copy that partition from one drive to another.

If you need more info to provide me with some help, please ask. I really need that stinking Windoze back on my laptop and I won't reinstall it from scratch... :-(

Thanks in advance!

---

### Post by logos34 on 2009-05-11
Partimage support for ntfs is "experimental" only...When I used it I had trouble getting windows to boot afterward.

Gparted would be the way to go using the [COPY]("http://gparted.sourceforge.net/larry/move/move.htm") function, but you say it's showing errors.  Maybe try booting into vista and run error-checking w/repair (CHKDSK) + defrag

[Clonezilla Live ]("http://clonezilla.org/clonezilla-live/")or the dd command would be your other alternatives.  Either way, you;ll still need to write the windows bootloader to the MBR of the target disk

> DD Command
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

Examples: duplicate one hard disk partition to another hard disk:

[QUOTE]**dd if=/dev/sda2 of=/dev/sdb2 bs=4096 conv=notrunc,noerror**

sda2 and sdb2 are partitions. You want to duplicate sda2 to sdb2. If sdb2 doesn't exist, dd will start at the beginning of the disk, and create it. Be careful with order of if and of. You can write a blank disk to a good disk if you get confused. If you duplicate a smaller partition to a larger one the larger one, using dd, the larger one will now be formatted the same as the smaller one, and there won't be any space left on the drive.[/QUOTE]

---

### Post by Toshibawarrior on 2009-05-11
Considering I'm already running Ubuntu and Kubuntu on the new drive, doesn't copying the old MBR overwrite GRUB?...I like my GRUB like it is...it's the first time I can get a fully functional and updated (as in changing the menu.lst itself in/for both distros) GRUB and I wish there was an easier way. :-(

Thanks for the reply!

Edit: GParted shows an orange triangle beside the partition type, in this case NTFS. It says something about reading "Save Details" and when I do there are tons of errors and warnings...If I manage to clean to errors with the method you mentioned, will I be able to copy it with GParted and make it bootable on the target drive?...

I know these questions might sound stupid, but I HAVE NEVER done anything like this. 

Thanks again!

Edit:2 after some more reading of the link you sent me, DD is down for the count. It can't copy Vista OEM partitions. 

I think my best shot is GParted after fixing (or trying to fix) the errors...but my questions stand...How do I copy the bootloader, or whole old MBR...Again, sorry if these questions sound stupid.

Thanks yet again! ;-)

As soon as I get home from work today I'll try to put the Vista drive back in my laptop and try to clean it's errors...I'll report back then. ;-)

---

### Post by logos34 on 2009-05-11
> **Toshibawarrior said:**
> Considering I'm already running Ubuntu and Kubuntu on the new drive, doesn't copying the old MBR overwrite GRUB?...

oh, I thought maybe windows would have the whole disk to itself.  But if you;ve also got linux on it, by all means continue to use grub, just edit windows entry in menu.lst.

> Edit: GParted shows an orange triangle beside the partition type, in this case NTFS. It says something about reading "Save Details" and when I do there are tons of errors and warnings...If I manage to clean to errors with the method you mentioned, will I be able to copy it with GParted and make it bootable on the target drive?...


Try it...can't promise.  The only other thing I can think of that may be causing the error is maybe an 'unclean shutdown' or the like.  But chkdsk would normally fix that.

---

### Post by Toshibawarrior on 2009-05-11
> **logos34 said:**
> oh, I thought maybe windows would have the whole disk to itself.  But if you;ve also got linux on it, by all means continue to use grub, just edit windows entry in menu.lst.

Heh, I thought so...GRUB FTW! ;-)! Correct me if I'm wrong, but everything needed to boot Vista it's inside it's partition isn't it? There's nothing left behind on the MBR?


> 
Try it...can't promise.  The only other thing I can think of that may be causing the error is maybe an 'unclean shutdown' or the like.  But chkdsk would normally fix that.

I will and I'll report back if any problems arise. And yeah, I had to shutdown violently, but it was like a week ago...Don't know if it matters.

Anyway, this will be my afternoon adventure for today :-)! Thanks for the prompt and useful replies ;-)!

---

### Post by logos34 on 2009-05-11
oh, and you'll need to edit vista boot files to point to it's new partition #/location on the new disk (3rd position after ubuntu and kubuntu?).  I know how to do it in XP (-->boot.ini), but not vista.  Maybe EasyBCD can help

---

### Post by Toshibawarrior on 2009-05-11
Ok, I don't know how to do it either :p! I'll read around and if I can find anything. :popcorn:

---

### Post by logos34 on 2009-05-11
> **Toshibawarrior said:**
> Heh, I thought so...GRUB FTW! ;-)! Correct me if I'm wrong, but everything needed to boot Vista it's inside it's partition isn't it? There's nothing left behind on the MBR?

what gets left behind is only the windows bootloader, the actual boot files are on the vista partition...grub chainloads it

---

### Post by Toshibawarrior on 2009-05-11
Thanks a whole lot logos34!! I did it! I told Windoze to correct the errors on the hard drive and it did! I copied my partition peacefully to the new drive...Now I just need to find a way to add it to menu.lst (gotta find out which list is being used: Kubuntu's or Ubuntu's) and find a way to make it bootable.

But thanks a whole lot for the tip!:)

---

### Post by Toshibawarrior on 2009-05-11
HUM HALLELUJAH!!!...

I did it! 

I saw that the GRUB list in use is the one inside Kubuntu because it was the last to be installed, so it took over the Ubuntu one and added Vista to it following the directions on another post (which I really can't remember now) and successfully added it to the GRUB menu list.

Then...whenever I tried to boot Vista it got stuck on: "Starting Up..." and nothing happened.

So I used the Vista Restore DVD that came with my laptop and let the Recovery agent take care of some discrepancies on the Boot option/configuration of Vista and then I used Testdisk from inside Ubuntu and fixed the Boot Sector (of Vista).

And now I have a fully function Triple-Boot with Ubuntu, Kubuntu,and Vista...and most probably openSUSE...but I'm still worried about it's Atheros Wi-Fi support...but OH WELL!! I got it working!!!

Thanks again to logos34 for the help! Without you I'd still be hitting my head against the desk trying to figure out how to copy the partition!

I guess this thread can be marked as "solved"...but that function disappeared from the forum :(!

---

