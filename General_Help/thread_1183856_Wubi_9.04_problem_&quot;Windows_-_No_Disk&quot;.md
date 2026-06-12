---
title: "Wubi 9.04 problem &quot;Windows - No Disk&quot;"
date: 2009-06-10
forum: General Help
---

### Post by zidler17 on 2009-06-10
When i hit "run" on the wubi.exe, i get an error window saying 
"Windows - No Disk
Exception Processing Message 0xc0000013 Parameters..." It won't go away until i restart the computer forcibly. I've tried this a couple times, as well as redownloading the installer application. Any help would be great.

---

### Post by s.fox on 2009-06-10
Hi and welcome the forums,

Is that the complete windows error message? Only reason I ask is that there is usually a code after parameters.

For example:

```

Windows - no disk Exception Processing Message c0000013 Parameters 75b6bf9c 4 75b6bf9c   
```

-Ash R

---

### Post by ginsumaster on 2009-06-13
I have exactly the same error message.  I've installed Wubi a few times .. on different machines -- no problems.  But this is the first time I've seen it.

Specs: Dell Vostro 220, WinXP SP3, all updates, fresh install, E7400, 3GB RAM, Intel GMA,  DEP off.  Filesystem: FAT32.

Trying to install Wubi v9.04.  ubuntu-9.04-desktop-amd64.iso located in same directory.

Exact error message:


Windows - No Disk

Exception Processing Message c0000013 Parameters 75b6bf7c 4 75b6bf7c 75b6f7c

---

### Post by Tipped OuT on 2009-06-13
> **ginsumaster said:**
> I have exactly the same error message.  I've installed Wubi a few times .. on different machines -- no problems.  But this is the first time I've seen it.

Specs: Dell Vostro 220, WinXP SP3, all updates, fresh install, E7400, 3GB RAM, Intel GMA,  DEP off.  Filesystem: FAT32.

Trying to install Wubi v9.04.  ubuntu-9.04-desktop-amd64.iso located in same directory.

Exact error message:


Windows - No Disk

Exception Processing Message c0000013 Parameters 75b6bf7c 4 75b6bf7c 75b6f7c

Maybe because your filesystem is FAT32? You should be using NTFS. ;)

---

### Post by danq989 on 2009-06-15
Hi, 

I had the same problem with WinXP Pro, 4GB, 3 HDD, trying to install Ubuntu 9.04 via Wubi.

I traced it down to my USB SD/MMC/CF multi-card reader. Since all the card slots were empty but still had drive letters assigned by Windows, they apparently came up in WUBI as "No Disk" and threw the exception.

I got past the exception message by using "Safely Remove Hardware" from the systray to effectively eject the empty drives. Since the drive letters no longer show up in Windows, Wubi does not get confused by them.

Hope this helps!
---DanQ

---

### Post by Mycle on 2009-06-20
> **danq989 said:**
> Hi, 

I had the same problem with WinXP Pro, 4GB, 3 HDD, trying to install Ubuntu 9.04 via Wubi.

I traced it down to my USB SD/MMC/CF multi-card reader. Since all the card slots were empty but still had drive letters assigned by Windows, they apparently came up in WUBI as "No Disk" and threw the exception.

I got past the exception message by using "Safely Remove Hardware" from the systray to effectively eject the empty drives. Since the drive letters no longer show up in Windows, Wubi does not get confused by them.

Hope this helps!
---DanQ

Hi thanks for the tip. "Safely Remove Hardware" certainly let me cancel the error message and move on. But this error occurred for me when installing Ubuntu 9.04 within WinXP. Perhaps coincidentally, Ubuntu froze during it's first normal boot process, after an apparently successful installation of and checking of files on first run. 

I took this further problem to be associated with the "No Disk" error during installation, so I set out to uninstall Ubuntu and received the same error again. 
Using "Safely Remove Hardware" on the card reader entries cleared the error message once again and allowed me to uninstall Ubuntu. 

What do I have to do now to install Ubuntu 9.04 within WinXP?
is it possible to disable the card reader for the duration of Ubuntu use?
Do I have to remove the card reader hardware from the PC?
-- 
Regards,
Mycle

---

### Post by onecent on 2009-08-18
I also had this error when trying to install Wubi. I was able to go into control panel, system, and device manage and disable my card readers. The install went smoothly after this. 

After the install was complete I went back and enabled them and there was no further problems running Ubuntu.

Disabling the card readers was much easier than removing the hardware and reinstalling it.

---

### Post by adycristi on 2009-09-19
Thank you. It works!

---

### Post by DuckTape33 on 2009-10-19
> **danq989 said:**
> Hi, 

I had the same problem with WinXP Pro, 4GB, 3 HDD, trying to install Ubuntu 9.04 via Wubi.

I traced it down to my USB SD/MMC/CF multi-card reader. Since all the card slots were empty but still had drive letters assigned by Windows, they apparently came up in WUBI as "No Disk" and threw the exception.

I got past the exception message by using "Safely Remove Hardware" from the systray to effectively eject the empty drives. Since the drive letters no longer show up in Windows, Wubi does not get confused by them.

Hope this helps!
---DanQ
Thanks, you the best! Made an account only to say thanks, lol. Sad I know but the stupid error was really bugging me, thanks for solution. BTW thanks for the tip!

---

### Post by enobrev on 2009-10-31
Just chiming in.  I had the same problem, and because of this thread, I ejected my ipod and unplugged my Android phone and then Wubi started just fine.

---

### Post by karatedog on 2010-05-02
danq989 +1 :)
You saved me 'bout 10 priceless minutes, because first I was getting past this error by clicking Cancel about 40-50 times.

---

### Post by jonester on 2010-05-05
I had the same issue. Follow these steps and it works:


[LIST=1]
[*]Remove all memory cards/USB devices (except your keyboard, mouse, etc :-))
[*]*Head to: *
_Device Manager_ > _Drives_ > Find your USB flash drive > _Properties_
_Policies_ Tab > _Select Optimize For Performance_ > OK
[*]*Next:*
_My Computer_ > Find your drive > _Format_
Select _NTFS_ (it should be in FAT32) > OK
[/LIST]
DONE!
 
This will erase all data to reformat, just save your data on the Desktop or what not.

Your devices must be in NTFS to use Wubi.

Here is the guide I followed, it's a little bit confusing in the beginning, so use mine if you wish:

[http://www.ntfs.com/quest22.htm](http://www.ntfs.com/quest22.htm)


Enjoy,
- Jonester

---

### Post by donicaben on 2011-02-12
I know this thread is old, but THANK YOU!  It's the first tech problem I've Googled in the past few days that gave me a solution that worked!  :-D

---

### Post by Lukeup on 2011-04-13
Thanks for the tips.  The sooner I can find applications to replace the apps I use in XP, I will rid my self of MS.

---

### Post by SullaQ on 2011-05-16
@danq989: Thanks for posting the solution, I was experiencing the same problem and once I unplugged the Kingston-18-in-1 multi-cards reader it is now installing on my laptop. First time using the Wubi option so I've got my fingers crossed.

---

### Post by vicpol on 2011-09-09
> **danq989 said:**
> Hi, 

I had the same problem with WinXP Pro, 4GB, 3 HDD, trying to install Ubuntu 9.04 via Wubi.

I traced it down to my USB SD/MMC/CF multi-card reader. Since all the card slots were empty but still had drive letters assigned by Windows, they apparently came up in WUBI as "No Disk" and threw the exception.

I got past the exception message by using "Safely Remove Hardware" from the systray to effectively eject the empty drives. Since the drive letters no longer show up in Windows, Wubi does not get confused by them.

Hope this helps!
---DanQ

That was easy! Thanks a lot!

---

### Post by atul3047 on 2011-12-01
[SIZE=2]Heyy.. Some one Please give me a solution to this error.....
I am also having exactly the same problem while installing Ubuntu 11.10 from WUBI.
[SIZE=1]"[/SIZE][/SIZE][SIZE=2][SIZE=1][I]pyrun.exe - No Disk
There is no disk in the drive. Please insert a disk into drive \Device\Harddisk1\DR5.

   Cancel      TryAgain      Continue[/I]"[/SIZE]
I also tried removing all external USB connection except my wireless TataPhoton internet device.
please post a proper solution to this problem...!!![/SIZE]

---

### Post by kewlzero on 2013-04-18
> **atul3047 said:**
> [SIZE=2]Heyy.. Some one Please give me a solution to this error.....
I am also having exactly the same problem while installing Ubuntu 11.10 from WUBI.
[SIZE=1]"[/SIZE][/SIZE][SIZE=2][SIZE=1][I]pyrun.exe - No Disk
There is no disk in the drive. Please insert a disk into drive \Device\Harddisk1\DR5.

   Cancel      TryAgain      Continue[/I]"[/SIZE]
I also tried removing all external USB connection except my wireless TataPhoton internet device.
please post a proper solution to this problem...!!![/SIZE]


**I had the same problem.  Not sure if works for everyone but i tested this on 3 computers and 2 laptops and it worked for me.  -- The trick is to wait about 10 minutes, then continuously click the Try Again, it will eventually load the "Are you sure you want to uninstall ubuntu?"  I clicked on it about 20 times till it worked. **

---

### Post by wildmanne39 on 2013-04-18
Thread closed. Please do not post in old threads.

---

