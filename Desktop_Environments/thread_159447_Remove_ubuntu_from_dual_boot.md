---
title: "Remove ubuntu from dual boot"
date: 2006-04-12
forum: Desktop Environments
---

### Post by Flow_Source on 2006-04-12
I convinced a friend to let me install Ubuntu on his new hard drive along side Windows XP (NTFS). After several weeks of using it he decided he dosen't want to use Linux. As much as it pains me, I am going to remove Ubuntu from his drive. I was just wondering if I can reformat this space or do I have to uninstall grub?

---

### Post by evilgold on 2006-04-12
[QUOTE=Flow_Source]I convinced a friend to let me install Ubuntu on his new hard drive along side Windows XP (NTFS). After several weeks of using it he decided he dosen't want to use Linux. As much as it pains me, I am going to remove Ubuntu from his drive. I was just wondering if I can reformat this space or do I have to uninstall grub?[/QUOTE]


grub loads from the /boot partition, so if you had a seprate /boot then you can just reformat your main linux partition and leave /boot. If everything was installed on one partition, your going to have to install another bootloader. I think you can load the winXP install disc and use "fixmbr" or somthing like that from the recovery console, to install the windows bootloader.

---

### Post by dermotti on 2006-04-12
Yea you can use fixmbr to put the windows bootloader back on. Once back into windows you should be able to delete the linux partition and create a windows one in its place.

Only weird thing is you will have 2 windows partitions that will each have a differnt drive letter.

---

### Post by walterius on 2006-04-13
Although this does not fit OP's situation, I include it here in case it can help someone.
-------------------------------
My attempts to uninstall Linux (I don’t remember the distro, but it wasn’t Ubuntu and it used the LILO boot loader) eventually led to the loss of everything, including the ability to boot the system.

Recovery attempts that failed after I removed LILO:
•	Windows FORMAT command
•	Recovery Console
•	Windows 2000 CD (repair, reinstall, etc.)—didn’t work because CPU couldn’t reboot.
•	FDISK—couldn’t delete the Linux partitions
•	ScanDisk—found nothing
•	FIXBOOT—said it fixed it but it didn’t
•	FIXMBR—said it fixed it but it didn’t
•	Windows ME boot diskette—no FORMAT command
•	Partition Magic (Windows version)—said it fixed it but it didn’t

I finally began the recovery process by deleting the two Linux (Linux + swap) partitions with the Partition Magic Rescue Diskettes, and then reformatting the C: drive with a Win98 SE boot diskette. After that I reinstalled Windows ME, and then Windows 2000 main system (Office XP), and then the auxiliary Windows 2000 systems (Office 2000 and Office 97). This restored my usual Windows ME and three Windows 2000 systems.

Walterius Oldfartus

---

### Post by walterius on 2006-04-13
For this I need a Windows-Ubuntu guru, if such be found.

Now, since the directions from other posters above are confusing to me (I am a certified Linux idiot), can anyone give me *tested, idiot-proof, step-by-step* directions for removing Ubuntu 5.10 from my computer and restoring my normal Windows multiboot system bootloader?

Note: I have Partition Magic 8 and a ton of Windows tools such as Win 9X boot disks.

*Please* don't guess. I don't want to repeat the process I described in my previous post above.

Many thanks,
Walterius Oldfartus :confused:

---

### Post by dave9191 on 2006-04-13
The way I have done it in the past. Pop the windows xp cd in the drive, restart computer, boot from the cd. 

Go to the recover console and run "fixmbr". That will get rid of grub from the master boot record and restore the windows boot loader. 

Restart the computer without the windows cd and your computer will boot into windows. 

Then right click on the my computer and click "Manage". 

Go to the disks section and you can see your partions. Delete the ones that linux was using and create a new one and format that so that windows will have the space. 

If you don't want to have an extra drive and want to append the sapce to an existing partion, you could try using Partion Magic to resize the exisiting windows partion to use that space, but that risks messing up the windows partion. 

And windows sucks :)

--
Dave

---

### Post by walterius on 2006-04-13
| And windows sucks :mrgreen: 

Agreed. That's why I am learning Linux. Btw, if I uninstall Ubuntu, it will only be temporarily. I am slowly learning Linux and I will keep on keeping on until I do.

I eventually want to have Linux as a *fully viable* alternative to Windoze.

I will try your tip--which looks good to me--and post back.

Walterius Oldfartus

---

### Post by walterius on 2006-04-13
| Go to the recover console and run "fixmbr". That will get rid of grub from the master boot record and restore the windows boot loader.

It didn't get rid of GRUB. In fact, I am writing this in Ubuntu, which survived my assination attempt.

I have a multiboot system consisting of Windows ME (C:), and three versions of Windows 2000 (D:, F:, G:).

To get to the Recovery Console, I had to pick one of the WINNT partitions. I chose the smallest: "FIXMBR G:". But no joy. Fortunately, no pain either. It left both Ubuntu and the variois Win 2K systems intact.

Any further ideas, anyone? Or is the only way out of a WinME-Win2K-Ubuntu system to start over by formatting c:? :confused: 

Walterius Oldfartus

---

### Post by walterius on 2006-04-13
| Go to the recover console and run "fixmbr". That will get rid of grub from the master boot record and restore the windows boot loader.

It didn't get rid of GRUB. In fact, I am writing this in Ubuntu, which survived my assination attempt.

I have a multiboot system consisting of Windows ME (C:), and three versions of Windows 2000 (D:, F:, G:).

To get to the Recovery Console, I had to pick one of the WINNT partitions. I chose the smallest: "FIXMBR G:". But no joy. Fortunately, no pain either. It left both Ubuntu and the variois Win 2K systems intact.

Any further ideas, anyone? Or is the only way out of a WinME-Win2K-Ubuntu system to start over by formatting c:? :confused: 

Walterius Oldfartus

---

### Post by dave9191 on 2006-04-13
[QUOTE=walterius]
To get to the Recovery Console, I had to pick one of the WINNT partitions. I chose the smallest: "FIXMBR G:". But no joy. Fortunately, no pain either. It left both Ubuntu and the variois Win 2K systems intact.
[/QUOTE]

ahh, having so many OS's might cause a bit of a problem. You need to run fixmbr on the drive that grub is installed on. So that would be the primary drive, probably the drive C:. I don't know how win me will take it. Make sure you have a good backup of all your files ;)

Alternativly, you can leave you /boot partion intact (hopefully thats on its own partion), leave grub and just get rid of the other linux partions. You can use grub to pick what OS to boot into and get rid of linux. 

--
Dave

---

### Post by Herman on 2006-04-13
[My two cents worth]("http://www.users.bigpond.net.au/hermanzone/p18.htm") (by Herman):D

---

### Post by walterius on 2006-04-14
Thanks, Dave. I'm thinking pretty much the same.

If I run fixmbr on C:, Windows ME will always boot; none of the WINNT systems will be known.

If I just boot to the Grub bootloader, I can get along (I do that now), but my goal is to get rid of Grub, and eliminate that extra step. (Presently I have to tell Grub to take me to my Winnt boot dialogue, and only then can I choose a Windows system.)

Idea: I might run fixmbr on win me after creating an extra partition for a dummy win 2k. I could then install the dummy win2k (bare bones) in the spare partition. That in theory would get me access to the win 2k systems. I could then remove the linux and dummy windows partitions.

Walterius

---

### Post by dave9191 on 2006-04-14
You should be able to configure grub to boot you stirght into the OS, not take you to a menu to pick your Windows OS. 

Or you can try your idea. 

--
Dave

---

### Post by walterius on 2006-04-16
After struggling for some days, I agree with Dave9191: I have too many Windows systems in my multiboot setup. Ubuntu is happy if it only has to coexist with *one* Windows system, but more than one (I was *already* using a multiboot system) seems to have overwhelmed it.

I do know how to remove Ubuntu, but that would require rebuilding two to four Windows (ME and 2K) systems, and that is no longer necessary, thanks to my finally starting to understand Ubuntu.

OT: The Ubuntu terminal command language, even to its text editors, bears an uncanny resemblance to my beloved DEC VAX/VMS OS (I loved those VAX's) of the 1960's, which, as I recall, was based on early Unix.

Thanks again,
Walterius

---

### Post by elamericano on 2006-04-16
I would have used Partition Magic to remove your Linux partitions and resized the Windows partition to take up the empty space (someone said that was dangerous? not in my experience.)

Then use recovery console to "fixmbr" and "fixboot". Fixboot rebuilds your boot list when you have multiple bootable Windows partitions. That should get you back to the original state.

Oh, and there is definitely a way to change your default grub selection and set the select time to zero, but no reason to keep it around if you're only booting Winblows. BTW, I've been known to multiboot 98, ME, 2000, and XP, but why 3 versions of 2000?

---

### Post by Mr Egg on 2006-04-16
When I uninstalled Ubuntu from dual-boot, I just deleted the Ubuntu and swap partition with the Windows XP install disc, then I rebooted back into the Windows XP install disc again and went into recovery console and did
```
fixmbr
```
And everything went back to the way it was before Ubuntu.

---

### Post by dave9191 on 2006-04-16
[QUOTE=walterius]Ubuntu is happy if it only has to coexist with *one* Windows system, but more than one (I was *already* using a multiboot system) seems to have overwhelmed it.[/QUOTE]

Ubuntu is happy to coesist with as many OS's as you want. As long as the boot loaders have been properly set up. If I had to run that many OS's, i wld just use grub to let me boot into all of them. Rather then having another boot menu after grub. 

OT: they are all based on UNIX, so thats why they are so similar :)

--
Dave

---

### Post by mabby on 2008-02-21
Thank you **dave9191**,

I did what what you said in your post and it works. Thank you so much.
I have no choice but to remove my ubuntu because someone will use my PC.
Anyway i have my new laptop and i installed Ubuntu there.

I'm still a newbie in this platform and i find it very interesting.

thanks again:KS:KS:KS:KS:KS

---

