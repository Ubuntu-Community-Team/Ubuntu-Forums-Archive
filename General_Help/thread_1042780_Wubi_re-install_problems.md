---
title: "Wubi re-install problems"
date: 2009-01-17
forum: General Help
---

### Post by CrutchyT on 2009-01-17
***I didn't notice Wubi forums and initially posted this in Absolute Beginners. I took the liberty of re-posting it here. Sorry for any inconvenience.***
	

So I installed Wubi/Ubunto 8.10 and long story short, after a modest and confusing amount of tinkering, I lost track of what I had done. I didn't do anything disastrous, I don't think, but I just felt like I would better off uninstalling and starting over again from scratch-I'm sure I wouldn't be the first Linux user to do so.

So I uninstalled it, but it was still on the start up menu.I forged on with the second install, nevertheless. I got the opening Ubuntu load screen, but then got busybox warnings about usplash, mounting, infa-something or other.

Thinking the start up menu might be the culprit, I downloaded EasyBCD and removed it the line entry for from the boot up menu. Still no dice. (Windows works fine BTW)

I then uninstalled a second time, after using CCleaner and Advanced Sytem Care free,Smart Defrag, and tried a third intsallation (which went suspiciously fast compared to the fist two) Still no luck; I got the same busy box warnings.

So far I've uninstalled two versions, and still have the third.

Is there something else that still needs to be removed before I can properly re-install again? I was told during the subsequent downloads that Ubuntu.exe was still there, but could be replaced, which I did.

Also, I don't know if the following is important, but:

In EasyBCD, in the "Add/Remove entries" section, there are five categories at the bottom-Windows, Linux, Mac and NeoGrub and WinPE.

When I click on Linux, I get the following entries under "type": Grub, LILO/eLILO, FreeBSD, Wubi. Grub is presently selected.

Below that in the "name" window it says "NeoSmart Linux"

Underneath is another section, "drive" which says Drive 0, Partition O (HPFS/NTFS-287GB), Partition 1 (HPFS/NTFS 11GB)
It also says that GRUB isn't installed in the boot sector. I have no idea what any of that means. No drive is presently selected.

I'm not only an Ubuntu noob, I'm a noob, period, with only two months serious computer experience.

Any help would be greatly appreciated. I don'y want to miss out on the Ubuntu experience and I really like this virtual partition idea.


HP dv-7
Vista 64 Premium

Thanks!

---

### Post by brandon88tube on 2009-01-18
How did you uninstall?

---

### Post by CrutchyT on 2009-01-18
The typical control panel uninstall.

---

### Post by CrutchyT on 2009-01-18
Bump.

---

### Post by Gen. Lee poor on 2009-01-19
This seems similar to my problem from last week. Although I managed to remove ubuntu from the boot menu using EasyBCD, it's unable to reinstall because it still keeps looking for the old root.disk file

[http://ubuntuforums.org/showthread.php?t=1037118](http://ubuntuforums.org/showthread.php?t=1037118)

I never got it fixed either.

---

### Post by brandon88tube on 2009-01-20
Sorry for the late reply, I think you should try to use the unistall-ubuntu.exe that gets placed in the ubuntu folder next time you want to uninstall. Maybe by doing an add/remove on it, it screwed it up.

---

### Post by CrutchyT on 2009-01-21
No problem, and thank you.

I tried that both under regular user and administrative privilege, and the Ubuntu folder and it's contents were still all there, even after restarting. 

I'd prefer to avoid it, but at last resort, would reverting to a restore point prior to installation work?

---

### Post by Gen. Lee poor on 2009-01-21
Interestingly enough, my pc is a HP dv7 too. 

My suspicion is that EasyBCD is not cleaning up properly the boot manager but it could also be a 64 bit Vista issue.. 
I think I may try a full install instead actually. I just need to get round to backing everything up and then seeing if the "shrink" option in Vista works as well as hoped.

---

### Post by CrutchyT on 2009-01-21
So I noticed. Mine's a dv7-1175nr, specifically.

Who knows, maybe that's no coincidence. I know there's been issues with 64 bit architecture, Vista & Ubuntu, but possibly HP, too? At this point, the culprit could be Colonel Mustard in the Grub folder with the candlestick, for all I know.

If you do the decide on the full install, good luck and I hope you'll report back to say how it went. I'm not ready to do anything as involved as that myself, but would be interested in hearing about it, and what it might say about Wubi, nonetheless.

---

### Post by brandon88tube on 2009-01-22
Sorry, I don't know what to tell you because I do not use Vista. If you were using XP it might be a different story.

---

### Post by CrutchyT on 2009-01-22
Would reverting to a restore point previous to installation work?

---

### Post by Yashiro on 2009-01-22
Delete the folders C:\ubuntu C:\ubuntu-backup and also C:\wubildr, C:\wubildr.mbr

I don't see how you can have issues after this as grub doesnt even get installed to the mbr.

To install. Make a folder. Put the iso in it. Extract the wubi.exe from the iso, or download it, into this folder. Run the exe.

---

### Post by CrutchyT on 2009-01-22
Alright, I deleted everything using the uninstall option in the control panel. I checked the folder wubi was installed in, there's no trace of it except the wubi.exe, which I deleted. I've downloaded wubi again and it didn't mention replacing the pre-existing on wubi.exe. According to EasyBCD, there's no line entry for Ubunto

And so, here goes. Let's hope 4th time is a charm.

---

### Post by CrutchyT on 2009-01-23
...and I'm posting this from Ubuntu!

FINALLY.

I think it was deleting the wubi.exe file which does not get deleted when Ubuntu uninstalls that did it. That's the only thing i can think of that I did differently this time around.

However, just for the record, in my own humble opinion, this thing isn't ready for prime time, and for reasons that go beyond the trouble i've had reinstalling. I won't go into details, you all know why, and besides, it's a subject for a different thread.

Anyway, thank you all very much for your help.

---

### Post by Yashiro on 2009-01-23
Conversely, my old wubi install gave me zero problems. ;)

---

### Post by Gen. Lee poor on 2009-01-23
Wow.. This seems promising. 
I'll give it a go later.

---

### Post by CrutchyT on 2009-01-23
> **Yashiro said:**
> Conversely, my old wubi install gave me zero problems. ;)


Did you ever try to reinstall it?

---

### Post by CrutchyT on 2009-01-23
General, 

To be precise, 

I did the manual uninstall which didn't seem to work

I then did the control panel uninstall, only to find that it wasn't there.

I deleted what's either the wubi.exe or ubuntu.exe file that get's left over. I found it by accessing the contents of the folder I downloaded Ubuntu into. Everything in there was in alphabetical order, the wubi/ubunto file was at the bottom.

I used different log in name, password than i did on previous attempts.

Good Luck!

---

