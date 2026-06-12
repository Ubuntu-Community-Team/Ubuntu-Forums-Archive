---
title: "Triple boot problem"
date: 2008-12-10
forum: General Help
---

### Post by disk11 on 2008-12-10
I am trying to triple boot XP, Vista, and Ubuntu using one boot loader, hopefully GRUB.

I saw a few guides telling me to install XP, hide the XP partition using gparted, and then install Vista so that the Vista boot loader doesn't get rid of the XP loader.  However, Vista can still see the XP partition.  I am using the latest live CD from the gparted page.

Is there a way to use grub or will I have to use the Vista loader?

---

### Post by doctorbighands on 2008-12-10
In my experience, the answer is "both." Let me explain...

I used to have exactly that setup. What worked for me is installing XP first, then Vista (because you actually want Vista's bootloader to see XP), then Ubuntu. That way, when you first boot, you get a GRUB menu asking you to select between either Ubuntu or Vista. If you select Vista, it kicks you into Vista's bootloader, where you can select either Vista or XP (which, I believe, it lists as "older version of Windows" or something like that). It's not as tedious as it sounds, I promise!

---

### Post by disk11 on 2008-12-10
I've done it before, and if at all possible I'd like to use just one.  It's not incredibly annoying, and if its the only feasible way I'll accept it, or just dual boot.

---

### Post by TeXtonyx on 2008-12-10
From XP you can boot Ubuntu with Vista on the Ubuntu boot menu.
From Vista you can boot all three.
And from Grub you can boot all three.

You do have to hide and then unhide, the XP and Vista partitions
or you will boot XP and Vista from Vista because Windows tends to
copy all the boot files onto just one partition. You want them apart.

caljohnsmith (mostly) and I had interesting discussion on how
to do this on a recent thread. He even convinced me, and I had
never heard of it before, that you could install Windows on a
logical partition and boot it through grub. 

[http://ubuntuforums.org/showthread.php?t=1005062&highlight=pr1mal](http://ubuntuforums.org/showthread.php?t=1005062&highlight=pr1mal)
Mostly it is pages 2 and 3 that talk about how to do this.
If you run into trouble post here again, and likely caljohnsmith
will respond, but if he doesn't then I will.

Update: This didn't work for pr1ma1 because he was gone for several
days and I don't think he used the grub hide/unhide trick. To boot
XP and Vista separately, the boot files for XP must be on XP and the
boot files for Vista must be on Vista, then with two separate menu.lst
entries. You have to watch out for all the boot files congregating on
just one Windows partition. If they do, you have to copy them back
so each has just its own. This is by MS design by the way. 

After you get the files copied to each its own, then you can unhide
the partitions and then XP can see Vista and vice versa. I think it
should go Vista, XP and then Ubuntu. Because XP will copy its boot
files to Vista and there are only 3 to copy back to XP, but Vista
has more files to move back to its partition. Then Ubuntu's grub
will see both of them when it is installed.

[http://ubuntuforums.org/showthread.php?t=932727](http://ubuntuforums.org/showthread.php?t=932727)

This was a problem with triple boot thread that caljohnsmith solved
and did so in a clear manner. Maybe this one is better to read first
and go back to the first mentioned pr1ma1 thread for details.

---

### Post by disk11 on 2008-12-14
Just a quick note, I had the dual-bootloader (GRUB then Vista loader to get to Windows) triple boot for a while, and for some reason I can't recall I reloaded XP.  And to my surprise, XP ended up on a logical partition according to gparted.  This occured again during my various attempts to rebuild the triple boot in the last week.  I dunno how or why this happened, or if gparted is reading something funny.

I've been sick then working a bunch the last few days, so no new progress to report, though a question has come up.  With XP installed by itself, shouldn't the boot files (NTLDR, etc.) show up in my C: partition where XP is?  I can't see them when I did show hidden files option.  I ask because I activated XP and would like to avoid calling in to re-activate, and I'll have to locate the Vista files that will be put in my XP partition.

---

### Post by TeXtonyx on 2008-12-14
"You do have to hide and then unhide, the XP and Vista partitions 
or you will boot XP and Vista from Vista because Windows tends to
copy all the boot files onto just one partition. You want them apart."

"I've been sick then working a bunch the last few days, so no 
new progress to report, though a question has come up. With XP 
installed by itself, shouldn't the boot files (NTLDR, etc.) show 
up in my C: partition where XP is? I can't see them when I did 
show hidden files option. I ask because I activated XP and would 
like to avoid calling in to re-activate, and I'll have to locate 
the Vista files that will be put in my XP partition." 

If you don't see the XP boot files on the XP partition, then
look to see if they are on the Vista partition. It works both
ways. The good news is that there are only 3 files to copy
back from Vista to XP (if they are on Vista). 

You have to be careful of the boot.ini file. Because it might
to the wrong partition, so check it. Here is my boot.ini

-----------------------

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"

----------------------

This says boot XP from the first drive, first partition. The 
partition numbers are decided by Windows counting installed on 
primary partitions first, then logical partitions. 

Vista is on a primary, so XP will be at least partition(2)
sudo fdisk -l may help you figure this out more precisely.
If you have the wrong partition number, the Windows error
will most likely be a missing hal.dll error. But that means
the grub menu.lst is working. Your grub menu.lst will need
to have an entry for Vista and an entry for XP. I'm not so
sure that grub and boot.ini make the same distinctions. And
they don't notationally, (hd0,0) is first drive first partition,
(hd0,1) is first drive second partition (re: grub menu.lst).
You might include a report of sudo fdisk -l (little L) next time.
gksudo gedit /boot/grub/menu.lst 
what does it say about Vista (and XP?) under other OS systems?

"And to my surprise, XP ended up on a logical partition according to 
gparted."

Maybe Grub will boot XP I think if its not marked as bootable *, but
I'm not sure that Vista will boot XP from a logical partition, non-*, 
so grub seems like the best/only? solution. If Vista and XP are on the 
same drive then XP overwrites Vista's System Restores. You can prevent 
that with a registry fix (see pr1ma1 thread last page) but then you can
just see XP from Vista, but not Vista from XP.

---

