---
title: "Ubuntu freezes on update"
date: 2012-03-17
forum: Desktop Environments
---

### Post by CJ_Hudson on 2012-03-17
Hi,
Since I installed  new CPU Windows doesn't work at all (PFN List Corrupt) and Ubuntu freezes whilst trying to download and install updates.
I have flashed my bios again (to 1003, recommended with this CPU by my motherboard manufacturer Asus).
Please advise/help.

---

### Post by raja.genupula on 2012-03-17
at what kind of update the system getting freeze . GUI or terminal .try the opposite for doing successful update .

---

### Post by 2F4U on 2012-03-17
Are updates the only occasion where your computer freezes?

---

### Post by CJ_Hudson on 2012-03-19
2F4U, yes.
 raja.genupula, at GUI. The GUI is notorious for bugs on my system, N.B. when you right clicked on the icon and go "install all updates" it either froze or you had to do it twice.
Will try terminal, please could you post relevant commands?

---

### Post by CJ_Hudson on 2012-03-22
Well! I can't boot into Ubuntu at all now, and none of the backup OSs (previous version in the boot table)work either. Nor do the diagnostic startups in my current version (3.0.0.16) or any of the previous version. First trouble I've ever had with Ubuntu installation. The Unbuntu logo flashes up briefly but then the screen goes blank. Odd because after the boot repair I had to do after repair-installing W7 it did work, once.
Any help please?

---

### Post by enterdavertex on 2012-03-22
Press CTRL+T, that open up the terminal;
type in : "sudo apt-get update", should you popo to enter your password;
after it is type in let him do his job; 

if there is an error code please let us know it,it may be a dpkg error;

---

### Post by CJ_Hudson on 2012-03-22
This is bad, I urgently need to access my files in Ubuntu and It doesn't work. I've never had problems with Ubuntu before, I've been using it since 2005.
As I say, symptoms are, whilst booting up:
Ubuntu boot/splash screen logo flashes on the screen then it goes blank.
Could I try the boot repair disc again? The table of available OSs is there,the other ones (XP and W7) work fine, it's just when I select Ubuntu it refuses to boot.
Please, can anyone advise me how to rescue an installation that won't boot and/or how to recover my files? (The system is backed up online with Deja Dup by the way asuming I can remember my password!. Using 11.10 Oneiric Osselot.)

---

### Post by CJ_Hudson on 2012-03-26
Bump

---

### Post by CJ_Hudson on 2012-03-27
Please, I had to repair/install Windows 7 on my other partition, repaired the boot menu with boot repair, Ubuntu booted successfully once but now won't boot, the Unbuntu logo flashes up for half a second then the screen goes blank.
Please can anyone advise me apart from suggesting reinstalling Ubuntu?

---

### Post by dannyboy79 on 2012-03-27
i am guessing it's just a graphics card/driver issue if the screen is going black. after you see the ubuntu logo flash have you tried to hit ftrl-alt-F1, which should take you a GUI-less login screen. Let me know

---

### Post by blueshead on 2012-03-27
I'm having problems as of today.. When I start my comp.. I get a quick flash.. "hit esc for other options" then a blue screen..

How ever if I unplug all USB I can boot in.. (I'm on a laptop)

Then I get a partial upgrade message.. and the upgrade just stalls..

When I do a sudu get upgrade.. I get 

"E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

So what's going on?.. Any Ideas?

Everything was working perfectly this morning  Ubuntu 11.10 (fallback to gnome 2)

I simply shut off my comp and went to work..Came home.. Now all this..

---

### Post by bogan on 2012-03-28
Hi! **MogBug,**

You do not say what Video card you have, their drivers are usually the cause of this sort of Blank Screen, when the grub menu is displayed.

Check out MAFoElffen's magnum opus in the Blank Screen Sticky on the Installations & Upgrade Forum:
[http://ubuntuforums.org/showthread.php?t=1743535&page=98](http://ubuntuforums.org/showthread.php?t=1743535&page=98)

There is an index in Post #2, and a step by step Troubleshoot tutorial in Post #1.

Good Luck.

Chao!, **bogan**.

---

### Post by CJ_Hudson on 2012-04-02
Hi Dannyboy79, thanks, I will try that and will let you know.

Dannyboy79, nope that didn't work. I think you are probably correct that it is a graphics issue, despite my earlier problems with the updater.

Please, can I do anything else that will get me into a graphic-less interface apart from physically removing the graphics card which will then force the computer to revert to the onboard Intel graphics?

---

### Post by CJ_Hudson on 2012-04-02
Blueshead, I think the 'unable to lock' message means the computer can't mount the Ubuntu partition on the hard drive, and threfore can't perform any operations on it. I noticed something similar on another website when I was trying to get chkdsk working to sort my problem out (see also this thread: [http://ubuntuforums.org/showthread.php?t=1948019](http://ubuntuforums.org/showthread.php?t=1948019) )
In fact I strongly suggest you run a program to physically check the hard disk, and, if possible, repair and restore bad disc sectors, e.g. something like 'check disk' (chkdsk command in Windows console.)
I assume there is a similar command in bash, if you don't have Windows installed?

EDIT:
Ah yes, it is fsck, available in the 'rescue/restore' Ubuntu menu in the boot screen. Or if you don't have grub installed you probably press a key to start it when you first boot.

---

### Post by CJ_Hudson on 2012-04-02
Bogan it is an Nvidia Ge Force 8400, which worked "out the box" in Ubuntu until recently, no need to install additional drivers etc.

---

### Post by RJARRRPCGP on 2012-04-02
> **MogBug said:**
> 
(PFN List Corrupt) 

99 percent unstable RAM! Usually RAM overclocked too much. 

It's usually a problem with the RAM that's installed.

Other symptoms I saw before:

With GNU/Linux, watch for file-not-found errors, especially KDE under Arch Linux displaying "file not found" and terminating even when KDE appeared to be installed correctly. (After installing KDE with pacman)

You need to go back into the motherboard setup and make sure the DRAM frequency is correct! It's likely too high!

---

### Post by CJ_Hudson on 2012-04-03
Thanks RJARRRPCGP, I have sorted the RAM issue out already thanks, it was merely a question of inserting the modules sequentially in slots A2 to B2, n.b. it did not like my leaving the B2 slot unoccupied. (4 slots, LGA775 mobo, 3 sticks).

However it was odd the Ubuntu worked fine with the sticks in the old position, yet Windows 7 wouldn't boot at all. Now Windows boots fine and it is Ubuntu with the issue!

---

### Post by BruceHayter on 2012-04-24
OK so this problem is appearing in multiple threads and on different forums. Bootrepair seems to make the problem worse. Does anyone have a solution other than reverting to Ubuntu 10.10?

---

