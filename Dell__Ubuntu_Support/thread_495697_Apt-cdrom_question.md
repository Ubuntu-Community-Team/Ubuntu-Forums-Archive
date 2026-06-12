---
title: "Apt-cdrom question"
date: 2007-07-08
forum: Dell  Ubuntu Support
---

### Post by Protagonistics on 2007-07-08
I reinstalled from Fesity to Dapper because of daily freezes with feisty as Dapper is reportedly more stable. I used apt-cdrom to make a cd of all the packages on my feisty so that I could transfer them to Dapper. I KNOW that this isn't really a great idea as I was mainly downloading from the feisty repos- let's just assume I want to transfer all my stuff and leave the consequences to me.
My problem is that I can't find the repository where apt-cdrom is. Where can I get the package or at least the rpm because the cd won't add packages unless I have it installed.

help.

---

### Post by ridgeland on 2007-08-09
You might try
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)
I tried it but stayed with a simpler method like copy  and paste.
I copied from one installation of 7.04 to another PC with 7.04 with just copy to CD on one PC then copy from CD on the other.
I copied everything from
/var/cache/apt/archive
and pasted to same on the other PC, using sudo (or root) both times.
Then on the second PC as I selected a package (synaptics) it skipped the download and went straight to install.  I think even with aptoncd you will still have to select your packages one by one.  One obvious snag is if the recommended version is not the same as was copied in then it will go to the web again.  Jumping from 7.04 to 6.10 could result in a higher percentage of mismatched package versions.

---

