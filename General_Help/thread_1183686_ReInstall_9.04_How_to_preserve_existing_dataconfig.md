---
title: "ReInstall 9.04 How to preserve existing data/config ?"
date: 2009-06-10
forum: General Help
---

### Post by UranUtan on 2009-06-10
Hi,

Currently using Ubuntu 9.04 x64. The 1st install was 8.04. I think I did something wrong since the upgrade to 9.04. There are stranges things that I don't know how to fix. Rhythmbox doesn't recognize the duration of the mp3 and the seekbar is always inactive (have already reported bug to launchpad). Recently I tried several softphone (Ekiga, Zoiper, QuteCom) there might be codec issues or something corrupted, only Ekiga works. Then after reboot, now none of them work, as soon as I dial a number the software exit right away without displaying a msg.

Long intro, just to tell you that I would like to attempt a re-install. The root partition is 10 GB ext3 and /home is separate. There is only 1 user on this machine. What I want to do is:

1. Re-install Ubuntu 9.04 x64 and change the root partition to ext4

2. Preserve all other partitions, 2nd hard drive.

3. Preserve all application settings (especially email)

Question: is it possible and ... how? I can reconfigure the visual or preferences settings, but I would like to avoid loss of data.

I have found a re-install instructions here: [http://ubuntutip.googlepages.com/reinstall](http://ubuntutip.googlepages.com/reinstall)

Can you please review / confirm / additional instructions ?

---

### Post by Therion on 2009-06-10
Okay, so you delete the "Ubuntu partition".  By this I'm assuming the author assumes that both / and /Home are co-existing on a single partition (typical install).  

You, however, have /Home on a separate partition.  

What I'm wondering is, if you perform these steps, won't you need to create a new /Home on the same partition as / (to preserve your existing /Home partition with all your data and configuration files) and then, once the install is complete, go back and delete the new /Home and merge the now free space with / (lest you wind up with unused free space)?

Not a problem, I'm just wondering and am pointing all this out in case you hadn't thought about it.  Because unless I'm missing something (and it's entirely possible I am, it's early here) that's how it's going to have to go down.

---

### Post by tenmilez on 2009-06-10
During the installation process you'll come to a point where you have to pick how you want to utilize your hard drives. Pick manual (I suspect you already know how to do this) and then set your drives like you had before, / to /, /home to /home, etc, and make sure that for the partitions you want to keep, you don't have the "format" flag set. If the format flag is not set then it will just map those partitions to those directories (/etc/fstab file?). Then when you go to create a user you pick the same user name and all that and it will use the existing /home/<user> that is already there and use all the settings within it. Amazed the crap out of me when I did it because I was expecting to have to redo all my settings like I would in Windows. 

Always backup first, just in case :)

And before you try this, try looking for hidden files/folders within your /home/<user> directory that belong to the applications that're being problematc. For instance, Firefox has settings in a file or folder that is called .mozilla. Most well written apps will look for these settings and create these files with default settings if they're not found. So try deleting these files and see what happens. 

Always backup first, just in case :)

---

### Post by UranUtan on 2009-06-10
Hi,

Thanks for your help. At least it is possible and thanks god, with all the playing I have done so far with Ububtu, I am familiar with the manual partioning procedure.

I will backup /home but still stress level is going to be high tonight.

One thing I am not clear yet. Should I use the LiveCD or the Alternate CD? Or may be it doesn't matter for a re-install?

---

### Post by randiroo76073 on 2009-06-10
I use the live-cd myself, but either one will work :) You can even sometimes do a distro version update and get away with that too.

---

### Post by UranUtan on 2009-06-10
> **randiroo76073 said:**
> I use the live-cd myself, but either one will work :) You can even sometimes do a distro version update and get away with that too.

Do you mean **sudo apt-get dist-upgrade**? I believe this is the cause of all my troubles. I have installed Ubuntu 9.04 fresh on two machines and another one with LinuxMint 7. None of them have the weird codec issues I have experienced with the 9.04 upgrade. May be there is some subtle differences for x64 but I don't have time and skills to investigate. I hope that a re-install will fix better.

---

### Post by nowhere@cox.net on 2009-06-10
Question: When you do reuse the /home partition when upgrading, how does the install handle any changes in packages that have config files in your home directory already there and possibly on an older version of the package?

I have always worried that "stuff" just wont work right with all these old version config files laying around so I always have just mirrored my home folder to an external drive, installed then manually pulled config setting as I need them.

Example: cairo dock pushed a major update with 9.04. None of my settings work with the new version and it wouldn't even start...

Could this be the source of UranUtan's instabilities?

---

### Post by michy99 on 2009-06-10
I kept my /home partition frim 8.04 when I did a new install of 9.04. The only program that I had problems with is evolution. Usually the new version of a program will recognize the setting from an older version and make any adjustments. Unfortunately this is not 100%.

---

### Post by nowhere@cox.net on 2009-06-10
OK. When I install 9.04 on my desktop box, I will still do my mirror of /home then I will try to maintain it. We'll see what happens...

Thanks!

---

