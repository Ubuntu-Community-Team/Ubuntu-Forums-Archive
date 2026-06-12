---
title: "No root login since 5.10 upgrade"
date: 2005-11-08
forum: Desktop Environments
---

### Post by photoworx on 2005-11-08
Since I upgraded to 5.10, I can not log in as root from anywhere. Not even from the main startup screen. The only way I can do anything as root is in a terminal with sudo.
Is this a problem with the upgrade or was this intentional?
I had installed apache and I could not change any configuration files, or add anything to the directories because of this.

Any help would be great.

Thanx

---

### Post by earobinson on 2005-11-08
did you at one point change the root password? if so ubuntu might have reset it. yes this is a featuer if you want your root password back do the following

sudo su
<type sudo password>
passwd
<type password that you want to set for the root password>

NOTE: this will not change your sudo password

---

