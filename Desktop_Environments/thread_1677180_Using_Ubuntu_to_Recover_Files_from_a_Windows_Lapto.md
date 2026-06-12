---
title: "Using Ubuntu to Recover Files from a Windows Laptop"
date: 2011-01-28
forum: Desktop Environments
---

### Post by RaptorThreeSix on 2011-01-28
All,

I'm trying to work around this without my normal techie available to help, and I'm a complete noob when it comes to this sort of thing--I probably know just enough to get myself in trouble, but here goes:

First off, I'm working on an HP Pavilion dv7 that's had some serious boot issues with Windows Vista64.  I never partitioned any of the drives, I didn't back up (for shame!) and now I'm trying to recover what I can from that data set.  This has happened to me before on other computers, and with one a friend of mine managed to use Ubuntu to at least allow me access to some of the files on my hard drive before he reformatted it.  I'm running Ubuntu 10.10 off of the LiveCD.

Anyways, I've got a liveCD, it's finally working (I was having some sort of error with the "Unclean File System", it eventually allowed me to boot anyways).  So, I'd say that I'm about halfway there.  My question is what is needed for the rest of the process?  Do I need to fully install Ubuntu (currently I'm just rolling off the LiveCD)?  Will I need to partition off files and such in order to gain access to what is saved on my laptop?  How would I go about doing that?

Again, sorry for the relative noob-ness, and thanks to any help in advance.

Respectfully,
Raptor

---

### Post by Rubi1200 on 2011-01-28
Hi and welcome to the forums :-)

If the goal is to just save data from Windows, then no you do not have to install Ubuntu.

Use the Nautilus file browser to find what you need and save to an external medium (HDD, USB stick etc.)

Try first under Places to locate the Windows partition. You may also have to go to Computer > and then look from there.

---

### Post by RaptorThreeSix on 2011-01-28
OK, there seems to be an issue, as I don't know what Nautilus is.  Where would I find that?  I looked in the Applications section, and I didn't see it there....

When I go to "Places", and then go to "Computer" all I'm seeing is my External and "File System".  Clicking "File System" gets me a pile of files (bin, boot, cdrom, dev, etc, home, lib, media, mnt, opt, proc, rofs, root, sbin, selinux, srv, sys, tmp, usr, var), none of which seem to be linked in any way to my main computer (the cd is spinning in the drive when I click on any of it).  Nothing from my computer.  Does this mean that it's not seeing my main hard disk?

---

### Post by sydbat on 2011-01-28
> **RaptorThreeSix said:**
> OK, there seems to be an issue, as I don't know what Nautilus is.  Where would I find that?  I looked in the Applications section, and I didn't see it there....Nautilus is the file browser. When you open "Computer" or "Home Folder", etc, the ensuing window is Nautilus.

> When I go to "Places", and then go to "Computer" all I'm seeing is my External and "File System".  Clicking "File System" gets me a pile of files (bin, boot, cdrom, dev, etc, home, lib, media, mnt, opt, proc, rofs, root, sbin, selinux, srv, sys, tmp, usr, var), none of which seem to be linked in any way to my main computer (the cd is spinning in the drive when I click on any of it).  Nothing from my computer.  Does this mean that it's not seeing my main hard disk?"File System" is the file system on the LiveCD.

"External" should be your Windows drive. 

So, from 'Places', the drop down menu will have a bunch of items (Home Folder, Desktop, etc), then 'Computer' and any other drives connected. The other drives should look similar to this - "80 GB Filesystem".

---

### Post by oldfred on 2011-01-28
If your NTFS partition is unclean or needs chkdsk run Ubuntu will not normally mount it as it may damage it where chkdsk would not fix it.

I would first try repairing with chkdsk. There are ways to force mount but it is better to try to repair first.

Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links:
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not auto repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by RaptorThreeSix on 2011-01-28
@sydbat: Ok, I'm not seeing anything in there aside from my external hd, which sends me to...

@oldfred: thanks for the recommendation, I'm doing that now.  Will it matter what sort of system I'm burning the disc from?  I ask only because my current usable laptop is a Mac.

---

### Post by Swagman on 2011-01-28
If you/someone did a "dirty shutdown" of windows.. ie: pulled the plug then windows wouldn't have been able to "unset" the hard drive in use flag so Linux will report it as "unclean"

Simply reboot into windows and do a proper shutdown to cure this.

Looking at my screengrabs should prove self explanatory 


[img]http://localhostr.com/file/TqrD4aj/Ubuntu148.jpeg[/img] [img]http://localhostr.com/file/xUnRMGY/Ubuntu149.jpeg[/img]

---

### Post by RaptorThreeSix on 2011-01-28
I don't even know what you're talking about... if it's concerning the original "Unclean Drive", that issue has been fixed.  Now I'm trying to get the files on the HP's main HD, onto my external.  The only HD that's showing up is the external HD, however.  Right now I'm working on what Oldfred suggested... I'm hoping that it doesn't completely reformat all of my stuff off of it.

---

### Post by oldfred on 2011-01-28
chkdsk should not cause any further corruption. If you get errors you may have to run it more than once as it does not fix everything on one pass. You have to run until there are no errors.

---

