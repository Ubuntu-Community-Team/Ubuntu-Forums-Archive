---
title: "dual boot problems with Windows 2000Pro"
date: 2009-04-12
forum: General Help
---

### Post by norfolkandgood on 2009-04-12
Hello folks! I have just spent about 3 hours searching and reading posts which may have had to do with my problem (the computer one that is!), without finding anything relevant. I see that there are around 3600 pages where it might be found but I think I might die before I find the answer ;)
I recently installed Ubuntu 8.10 as a dual boot alongside W2000Pro from the ComputerActive disk. To my surprise Linux worked apparently OK. I played a couple of rounds of Patience just to try it and then shut the computer down. There are some files in the Windows system that I needed (OpenOffice) so, the next time I started the computer, when the choice of operating systems screen came up, I elected to boot into W2000. At first everything seemed to be OK, Windows began to load, the Windows screen came up with a progress bar at around half way and then disaster - the blue screen of death - a STOP error with a long stream of gibberish following...... The gist of the error seems to be "INACCESSIBLE_BOOT_DEVICE". I have tried downloading supergrubdisk on the other computer on my desk and then burning the file to a CD and booting from that - the supergrub appears to load but then only offers me the chance to burn the disk.
It seems to me that the sensible thing to do is to remove Ubuntu to see if W2000 will then behave itself, transfer the documents to the other computer and then have another try with Ubuntu. Trouble is - how do I remove Ubuntu when it is the only working system - it won't remove itself while it is operating will it?
And here's me, hopefully taking the first steps away from BG's pension fund.
If there is an answer staring me in the face then I apologise, with much grovelling and cringing, that I could'nt find it myself!

---

### Post by statistic on 2009-04-12
You should have a look at: [http://icrontic.com/articles/repair_windows_xp](http://icrontic.com/articles/repair_windows_xp)
EDIT: Don't use that article except for instructions to get into the recovery console.

Windows NT to Windows XP all used the same boot loader, and that should include Windows 2000. So follwoing these instructions with the Windows installation cd should remove grub as your bootloader and put the windows one back on there, and hopefully you will boot back into windows, with no need to remove your linux partition... yet.

---

### Post by statistic on 2009-04-12
Sorry that article is crap. what you want to do in the recovery console, is simply type

"fixboot c:"

---

### Post by khelben1979 on 2009-04-12
My advise to you would be to get another harddrive and do a fresh install of Windows 2000Pro on this one and after this you have Ubuntu and Windows on 2 separate harddrives.

It is possible to run both Windows and Linux on the same harddrive, but it can cause problems, which you now apparently are experiencing.

This would be the most easiest thing, however, it may still be possible to repair your current system, but I doubt whether it's really worth all the hassle and time it may take.

---

### Post by norfolkandgood on 2009-04-12
Thanks statistic for your very prompt reply! I have just melted two icepacks on my brain, unfortunately without success...
The icrontic site gave an "error 404 - not found" and I couldn't find anything relevant so I resorted to trying out my amazing powers to sort it myself......
I couldn't find a recovery console - I take it that the recovery menu during the boot process is not the right one? I tried putting in the "fixboot c:" command but it claimed that it didn't recognise the command.
I then tried applications > Accessories >Terminal and that didn't recognise the command either. So much for my amazing powers!
If there is another recovery option I would be delighted to try it.
Again - THANKS!

---

### Post by norfolkandgood on 2009-04-12
Thanks Khelben1979 for your help - I have a nasty idea that I might have to adopt your solution in the end.

---

### Post by ivanvajar on 2009-04-12
You can access your Win partition from Ubuntu and backup any data you want to save. Find 'recovering Ubuntu after installing windows' with google. It will teach you how to recover GRUB(Ubuntu's boot loader) after Win reistallation and use it to boot into any OS. You don't need another HDD for this.

---

### Post by khelben1979 on 2009-04-12
> **norfolkandgood said:**
> Thanks Khelben1979 for your help - I have a nasty idea that I might have to adopt your solution in the end.

:-)

It will give you less pain in the long run.

---

