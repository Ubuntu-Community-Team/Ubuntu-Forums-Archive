---
title: "Two power managers on Xubuntu 13.10?"
date: 2013-10-19
forum: Desktop Environments
---

### Post by Stormlord on 2013-10-19
Hi,

I noticed that both gnome-power-manager and xfce4-power-manager are installed in the new Xubuntu 13.10.  Why both?  Plus, I can adjust only xfce4-power-manager settings in the Settings area.

Thanks.

---

### Post by Toz on 2013-10-19
Only xfce4-power-manager is installed by default. You must have installed something else that brought in the gnome-power-manager as a dependency.

---

### Post by Stormlord on 2013-10-19
> **Toz said:**
> Only xfce4-power-manager is installed by default. You must have installed something else that brought in the gnome-power-manager as a dependency.

No.  I just installed xubuntu-desktop on an ubuntu mini installation.  What I noticed though is that on another installation on a vm, I just installed XFCE4 and it did install gnome-power-manager automatically without installing xfce4-power-manager at all.  I had to install that manually.  Seems that gnome-power-manager has been included in the XFCE4 meta-package.

That brings up another question.  Do I leave gnome-power-manager installed or do I have to uninstall it to avoid conflicts?

---

### Post by Toz on 2013-10-20
> **Stormlord said:**
> No.  I just installed xubuntu-desktop on an ubuntu mini installation.
Oh, I see. I was referring to the actual Xubuntu 13.10 release. You have a xubuntu-desktop on ubuntu install - there is a small difference (well, actually a little bigger than small if its installing gnome-power-manager). 

> What I noticed though is that on another installation on a vm, I just installed XFCE4 and it did install gnome-power-manager automatically without installing xfce4-power-manager at all.  I had to install that manually.  Seems that gnome-power-manager has been included in the XFCE4 meta-package.
I'm noticing something similar but different. Installing the [Ubuntu mini 32-bit]("https://help.ubuntu.com/community/Installation/MinimalCD") into a VM then installing:
- xubuntu-desktop: It actually installs a number of gnome packages (gnome-screensaver, gnome-settings-daemon, gnome-session, notification-daemon, etc) that it shouldn't be. This would cause conflicts.
- xfce4 - I'm not seeing it installing gnome-power-manger (or any other gnome packages) like xubuntu-desktop does. It does not however install xfce4-power-manager because its listed as suggested (meaning you need to install it manually).

> That brings up another question.  Do I leave gnome-power-manager installed or do I have to uninstall it to avoid conflicts?
If you are looking to run Xfce, I would uninstall gnome-power-manager and let the Xfce power manager do it's job. You may also want to uninstall the other gnome packages so they don't conflict. 

[s]I think it may be best to file a bug report against both the xubuntu-desktop and xfce4 meta-packages regarding this issue. 
-xubuntu-desktop: should not be installing the extra conflicting gnome packages
-xfce4: should be setting xfce4-power-manager as "recommended" so that it installs.[/s]

EDIT: Now that the xubuntu-desktop install on the ubuntu-minimal CD is complete on my VM, I see that although there are many potentially conflicting gnome packages installed, none are running on login and Xfce is running as it should be.

Out of curiosity, if you want to run Xfce, why not just install the official [Xubuntu]("http://xubuntu.org/getxubuntu/") spin?

---

### Post by Stormlord on 2013-10-20
> **Toz said:**
> Out of curiosity, if you want to run Xfce, why not just install the official [Xubuntu]("http://xubuntu.org/getxubuntu/") spin?


The problem with all *ubuntu releases after 12.04 is that they do not offer the ability for the user to manually configure LVM groups and volumes and encrypt them manually like the alternate install did.  If I use the desktop installer, the only way for me to encrypt my hard disk is by selecting to erase it completely and allow the installer to do the job.  My laptop hard disk has a hidden bootable partition that has utilities and apps for configuring the laptop itself and I don't want to delete that partition.  Ubuntu server and Ubuntu mini installers allow me to create the partitions exactly the way I want and encrypt the LVM partition only.  Plus, I can place the grub boot loader on the /dev/sda1 partition instead of changing the master boot record, which might cause problems.

That's why I prefer to use those installers and install any other *-desktop afterwards.  :)

If you happen to know of any other way for me to accomplish the same things by using the official DVD image installer, I'd appreciate it if you could advise me on how to do it.

Thank you!

---

