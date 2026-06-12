---
title: "Return of the dreaded Grub Error 21. (dual boot gone horribly wrong.)"
date: 2008-04-25
forum: Desktop Environments
---

### Post by Mugsy323 on 2008-04-25
Once again, ubu's installer has fried my MBR so I can't access either Windows nor Ubuntu. :(

**I thought I was done with this nightmare with 7.10**, and complained in _[another thread]("http://ubuntuforums.org/showthread.php?t=740886")_ last month, but I just tried installing 8.04, and not only did it take out the Master Boot Record of my Windows C: drive, running "FIXMBR" from the Windows XP Recovery console, which worked before, now doesn't.

Here's the long version: I have two 500GB SATA drives RAID-0'd together with Windows XP on it. I also have two IDE drives, the first being storage, and the second, dedicated for Ubuntu. I had the system set to boot **XP** by default, but if I inserted the Ubu CD and selected "Boot from Hard disk", it would load Ubu-7.10. This saved me from having to mess with "boot loaders" and other nonsense.

I was using the 32bit Ubu, but wanted to try the 64bit Ubu-8.04. You can't upgrade 32bit 7.10 to 64bit 8.04, so I had to install it from scratch. It formatted the proper drive, installed the files and told me to reboot. I did (removing the CD when prompted). On reboot... hoping to see it still load Windows as before... instead, I got:

Grub loading...
Error-21.

I inserted my WinXP CD and booted into the Recovery Console. A quick check showed all my Windows files present and intact (being a SATA drive, the designation was D**:**). My first IDE came up as C**:** (as it should), also intact.

As I did the last time this happened, I ran "FIXMBR", it claimed to work, but a reboot produced the same "Error-21". Rebooting with the Ubu CD, it reported it could not find the installation it just finished installing.

I've gone back into the Windows Recovery Console and tried everything: "FIXBOOT", "CHKDSK /R", and "FIXMBR" a couple more times (and who knows what else). Windows will not boot.

Nor will Ubuntu. I'm having to use the CD right now to have any Net access at all!

Beside my raging anger at Ubuntu STILL modifying the boot sector of any drive other than the one it is being installed to, **how do I get Windows back?** A reinstall doesn't find it and wants to format my drive. And I can't copy/backup my Windows drive to another drive using the WRC because it's telling me I "don't have permission" to access certain folders. What a pain!

HELP!

---

### Post by gobbledigook on 2008-04-28
i had a very similar problem which ened up with me losing all data on the drive and the MBR being completely screwed!!

the full details are here:[http://ubuntuforums.org/showthread.php?t=770492](http://ubuntuforums.org/showthread.php?t=770492)

---

### Post by Mugsy323 on 2008-04-28
> **gobbledigook said:**
> i had a very similar problem which ened up with me losing all data on the drive and the MBR being completely screwed!!

the full details are here:[http://ubuntuforums.org/showthread.php?t=770492](http://ubuntuforums.org/showthread.php?t=770492)

The authors of Ubuntu REALLY need to address this issue. It's not a "bug" that requires tracking down. It's a deliberate function that needs changing: modifying the MBR of a drive other than the one Ubu is installed on.

The fix is easy, either prompt the user before writing with a warning as to what is about to be done, or check the MBR to see if it already calls another drive (typically SATA) and account for it in GRUB.

[COLOR="Red"]OVERWRITTING THE MBR OF ANY DRIVE WITHOUT REGARD FOR WHAT'S ON IT FIRST IS... ESPECIALLY WHEN YOU KNOW THIS WILL RENDER AN SATA BOOT DRIVE INACCESSIBLE... IN UNFORGIVABLE![/COLOR]

Fortunately, I was able to recover from this disaster. It was an absolute nightmare and took me a day and a half to repair, but it boils down to the fact that after this happened to me (last July), I was smart enough to backup the MBR of the drive in question.

The long version was that I foolishly saved the MBR file to my SATA RAID-0 NTFS drive and nowhere else. As a tech of 20+ years, I just happened to have a program on floppy that can read an NTFS drive from DOS. I then copied the MBR file to a floppy. Then I tried writing the MBR back from Linux using the Ubuntu Live CD, but it refused. Since I was reinstalling Linux anyway, I opened up my PC and changed the jumpers of the drive I had Ubu on to make it my C: drive, unplugged the SATA cables to my RAID, reformatted and put Windows on it instead. Once I had a copy of WinXP running, I copied the MBR back to my boot drive. But before putting everything back, I unplugged the drive I just fixed so that I had only the one HD connected, reformatted the drive yet again and installed Ubu 8.04 on it (now safe from modifying any other drive). I now have my old system back, plus Ubuntu64-8.04 installed on its own drive.

I should also mention in all this, I had to use my Partition Magic rescue floppies to format the drive for Linux each time I tried installing Ubuntu because its formatter creates errors that prevent it from installing.

What a nightmare. The only "solution" right now to prevent this from happening again in the future is to **unplug** every other drive in my system before each upgrade.

:(

---

### Post by Xiong Chiamiov on 2008-04-29
Is there any particular reason why you don't want to use GRUB?  It's not very hard to get set up, and it's very powerful.

---

### Post by Mugsy323 on 2008-04-29
> **Xiong Chiamiov said:**
> Is there any particular reason why you don't want to use GRUB?  It's not very hard to get set up, and it's very powerful.
Quite simply, it doesn't work.

The first time I installed Linux on my system, it was Red Hat's "Fedora", which also installed GRUB. When I updated Fedora with a new installation, I found that my MBR had somehow been altered so that GRUB no longer ran. Reformatting the drive did not correct the MBR (yes, I checked my BIOS settings).

Now, no matter what I install, the MBR of that drive remains unaffected and Grub will not run.

With my latest installation, I unplugged all other drives and Grub installed on the new drive. However, it is not my boot drive, so even though it runs, it isn't being used.

---

