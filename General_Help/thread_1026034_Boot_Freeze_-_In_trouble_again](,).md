---
title: "Boot Freeze - In trouble again](*,)"
date: 2008-12-30
forum: General Help
---

### Post by MopMonkee on 2008-12-30
*hits head against brick wall* 

**Scenario:**
Been using Ubuntu (8.04) since August. Had some issues in the past. Haven't been able to update in a couple months. But this never bothered my day-to-day activities so I just ignored updating. *hits head against brick wall* 

Whenever my computer decides to do disk scan from boot up as routine it would always fail. I learned that skipping it and doing a manual (***sudo fsck -fv /dev/sdb1***) fixed some problems and made this issue go away for a month or so.

This particular incident occurred again and I busted out the manual scan. This time I encountered this message: ***WARNING!!!  Running e2fsck on a mounted filesystem may cause SEVERE filesystem damage.***

Ignoring this I scanned again. *hits head against brick wall* 
When I went to reboot my loading bar freezes and computer sits.

Running in safe mode under both kernels at my disposal I encounter a pile of unreadable material ending with this: 
[I][B]Begin: Running/scripts/init-bottom...
Done.
Run-int: /sbin/int:no such file or directory
[ 22.890184]Kernel Panic - not syncing:Attempted to kill init![/B][/I]


**What I have attempted:**
Reading through the forums I find this is a common error related to many different types of problems.

What seems to bother people most is faulty ram or HD. I have taken each piece of ram out in turn to see if this is the case and no luck. (still freezing on loading bar).

Run ubuntu from live cd and again try to do a manual fsck scan. This does not seem to help.

I try downloading and installing updates while on the live cd. I am able to download updates but run into issues installing (see error1.txt)

**My Suspicions:** 
I am encountering 2 problems?
An update issue which stems from a voodo curse?
As for the boot freezing I suspect there is some sort of mounting problem or linking issue to my kernel. Although I am a ultra-noob I am completely comfortable with being wrong.  

**Hardware:**
2 Hard-drives(IDE)
250gig - holds Ubuntu and programs
300gig - holds long term data (music, pictures ect.)
Hard Drives work separately from each other and have had no issues there.

Radion x800 graphics card
2gigs of ram 

**Plea for help:**
Is there anyone out there who can help me get my pc running again:confused:

---

