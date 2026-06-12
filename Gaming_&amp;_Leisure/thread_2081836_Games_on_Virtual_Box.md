---
title: "Games on Virtual Box"
date: 2012-11-07
forum: Gaming &amp; Leisure
---

### Post by 3dmatrix on 2012-11-07
I wish to install Ubuntu 12.1 on another partition and use it just for gaming. I tried installing Lubuntu > VirtualBox > Xp > Need For Speed / Blazing Angles but non of them worked. Getting several errors like Registery error. Or some write protect / can not write error. Where i might be going wrong ?

---

### Post by doorknob60 on 2012-11-08
Virtualbox uses emulated graphics drivers, the performance will be fairly bad no matter what. I don't recommend it unless it's a very old game.

---

### Post by 3dmatrix on 2012-11-08
> **doorknob60 said:**
> Virtualbox uses emulated graphics drivers, the performance will be fairly bad no matter what. I don't recommend it unless it's a very old game.

So what is the solution ? Here the problem is not bad performance. The problem is its not running at all after installation.

---

### Post by cwsnyder on 2012-11-08
The other problem with a Virtual environment is that the memory map is different than you will see in a standard Windows XP install.  *Especially* in games written for performance, they make use of undocumented system calls and strange areas of memory which can be broken if used virtually.

---

### Post by 3dmatrix on 2012-11-08
> **cwsnyder said:**
> The other problem with a Virtual environment is that the memory map is different than you will see in a standard Windows XP install.  *Especially* in games written for performance, they make use of undocumented system calls and strange areas of memory which can be broken if used virtually.

But what is the solution ? So many people are playing games on Linux. Many claim most of the games can be played. So what is going wrong in my case ?

---

### Post by Sealbhach on 2012-11-08
Some Windows games can be installed and played on a Linux distro using Wine. 

Wine is not an emulator, it's a compatibility layer. Try it out, some games work perfectly, other's don't work well or even install at all.

.

---

### Post by 3dmatrix on 2012-11-08
> **Sealbhach said:**
> Some Windows games can be installed and played on a Linux distro using Wine. 

Wine is not an emulator, it's a compatibility layer. Try it out, some games work perfectly, other's don't work well or even install at all.

.

Well, Blazing Angles did not work in both Virtual Box and Wine but NFS Hot persuit did not work in Virtual Box but worked in wine.

.

---

### Post by Famicommander on 2012-11-09
Virtualbox is usually a dead end for any game that requires 3D acceleration. You're much better off with a combination of Steam for Linux (still in closed beta but you can get in if you check the stickied threads), the Humble Indie Bundles, WINE, and PlayOnLinux.

---

### Post by mastablasta on 2012-11-09
for windows games windows is best. so in this case dual boot would do fine for games that do not run in linux. else oyu need to use wine. they have application database. and sometime you need to tweak or install some addons to make them work. just dont' expect everything to work. games with rating Gold and above are what you are looking for.

---

### Post by Kodeine on 2012-11-09
I hear that VMware has vastly superior graphics performance over virtualbox and would be a much better choice for playing games on. Only problem is that it's not free and open source like Vbox. Something I do if I have to run windows software is boot windows eight via USB. I got the beta before they took it down.

If I were you though I'd be saving my money for Valve's and other publishers games when their available for the penguin via steam. Beta's already out, not far off now.

---

### Post by mzrk7 on 2012-11-09
Virtual box is not very good for gaming. Maybe the best choice is to dual boot with windows.

---

### Post by 3dmatrix on 2012-11-09
Well dual boot is always a possibility but I hate to use windows. If i really have to keep somthing seperate for gaming, then why not a gaming console ? But i would still like to have some sugession about running windows games in linux.

---

