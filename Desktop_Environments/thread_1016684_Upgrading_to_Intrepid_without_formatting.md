---
title: "Upgrading to Intrepid without formatting"
date: 2008-12-20
forum: Desktop Environments
---

### Post by mister_p_1998 on 2008-12-20
Hi guys,
Ive read that I can upgrade to Intrepid without formatting & losing all my files, Ive done an online update on my test machine - Hardy to Intrepid and it worked flawlessly. What I want to do is upgrade my main work machine, which stills runs Dapper (too much stuff on it so I never updated). I cant see the option to update without a wipe in the menus. Can someone walk me through it?
Cheers
Steve

---

### Post by bapoumba on 2008-12-20
Do you have a separate /home partition or another partition for all your files?
Backup - Backup - Backup

In synaptic, you can ask for the LTS release upgrade, and you should be prompted to upgrade to Hardy.

---

### Post by mister_p_1998 on 2008-12-20
> **bapoumba said:**
> Do you have a separate /home partition or another partition for all your files?
Backup - Backup - Backup

In synaptic, you can ask for the LTS release upgrade, and you should be prompted to upgrade to Hardy.

No, home is on main partition, yes Ive seen the 8.04 option, will it install without wiping though? Ive tried before with Edgy, and it broke the install.

Steve

---

### Post by bapoumba on 2008-12-20
> **mister_p_1998 said:**
> No, home is on main partition, yes Ive seen the 8.04 option, will it install without wiping though? Ive tried before with Edgy, and it broke the install.

Steve
Make sure your system is _up to date_ and that you have enabled the _dapper-update_ repositories. _Backup_ all your home (including hidden configuration files) so that you can retrieve them if need be.
A network upgrade will preserve your /home, a fresh install will not (if you choose to fresh install, you can create a separate partition in the manual partitioning menu). Remove all the third party repos you have been using, you can add them  back later.

[https://help.ubuntu.com/community/HardyUpgrades#Upgrade%20from%206.06%20LTS%20to%208.04%20LTS](https://help.ubuntu.com/community/HardyUpgrades#Upgrade%20from%206.06%20LTS%20to%208.04%20LTS)

Ubuntu recommends network upgrades over fresh installs.
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

Always backup all your important files, even the non-important ones.

---

### Post by mister_p_1998 on 2009-02-10
Didnt work...
Im going to have to do a fresh install.. grr...
Steve

---

