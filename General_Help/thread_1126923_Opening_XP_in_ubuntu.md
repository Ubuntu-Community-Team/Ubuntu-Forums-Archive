---
title: "Opening XP in ubuntu"
date: 2009-04-15
forum: General Help
---

### Post by Boinz on 2009-04-15
Hey everybody, linux n00b, I'm learning how to use linux/ubuntu for the first time, I'm ok with windows xp but i needed an excuse to learn how to use linux.

the problem i'm having is that i had installed windows xp SP3 on my computer and have using it since last year. Now i have installed and updated ubuntu and so far im having a blast learning. However, what i am interested in doing is opening my windows desktop in a separate window so i can run my apps and games without wine. I read about VMware, but every tutorial or demo shows you have to reinstall windows xp from scratch, i already have a partition, and i know how to access my windows files thru the /host folder. however, i would like to open my windows OS in a separate window WITHOUT reinstalling windows. especially since i have all my media and files and updates just the way i like them.


Is there any hope? or am i doomed to have to reinstall a brand new windows partition?

---

### Post by 3Miro on 2009-04-15
There was a tutorial that shows how to boot an existing windows installation from within Virtual Box (actually is may even be in their manual). I don't know about VMware.

There is a problem wit the games, Virtual Box cannot play 3D games. VMware might, but double check for sure. Graphics under virtual machines is somewhat iffy.

---

### Post by hikaricore on 2009-04-15
> **3Miro said:**
> Virtual Box cannot play 3D games.

**Yes it can.**  But as with vmware, hardware rendering in the vm environment is still in its infancy.

To the OP, if you are expecting to be able to play games on your XP install through a VM you might just wanna dual boot, you may have little to no luck...

---

### Post by Boinz on 2009-04-15
can anyone direct me to a tutorial to show me this, cause every single one i find with google tells me to reinstall windows.

---

### Post by gyaneshwar on 2009-04-15
I am using VirtualBox as it is open and has easy sharing for files on your hard drive.

For installation 
first type
sudo apt-get install virtualbox

This will offer virtual box versions so you choose one
(eg. virtualbox-2.2) and than
sudo apt-get install virtualbox-2.2

Then from Applications menu - System Tools-Sun xVM Virtualbox you start a program and create a Win Xp drive. (Just read options -it's really simple).

Since Virtual Machines are emulating (or whatever) hardware if the game is newer or heavy (3D) probably will not work (properly).

For that you need to make dual boot.

Problem with a dual boot is that you have to restart a machine :D to enter Win/Ubuntu.

On the serious note if you have only ubuntu without windows and you want to put windows it would require some workout - resizing partitions, saving (restoring) boot record after windows installation.
Not too much work but still work.
More details are available on:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Wish you luck whatever you decide! (Or just do both for fun :p)!

---

### Post by Merk42 on 2009-04-15
Well I Googled "boot from existing partition in virtualbox" and found this [http://ubuntuforums.org/showthread.php?t=769883](http://ubuntuforums.org/showthread.php?t=769883) which I believe I tried back in the day.  Keep in mind of course that even if this does work, you may not be able to play your games depending on their requirements.

If you specifically want to use VMWare, you should be able to do all the same steps aside from slightly changing step 5.

---

