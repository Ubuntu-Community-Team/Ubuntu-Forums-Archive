---
title: "enable password request after hibernation"
date: 2011-09-22
forum: Desktop Environments
---

### Post by doru001 on 2011-09-22
I would like to enable password protection when i exit hibernation in lubuntu. There is also an issue with the mouse not showing after hibernation. 

I have found some information on the issue: 
[http://ubuntuforums.org/showpost.php?p=8368647&postcount=5](http://ubuntuforums.org/showpost.php?p=8368647&postcount=5)
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/42052](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/42052)

but I would like to know if anybody has successfully done this before I try to install kdm over gdm and lxdm.

---

### Post by doru001 on 2011-09-25
On second thought, I will not install kdm over gdm and lxdm, because I understand that it would continue running in the background and slow down the system, defeating the very purpose of lubuntu. 

Plus, nobody answered my post. Bump! 

P.S. Use xscreensaver-command -lock to lock the screen in lubuntu.

---

### Post by Neosano on 2011-10-23
In the power manager you can tick "Lock screen when going for suspend/hibernate" in extended tab.

---

### Post by doru001 on 2011-10-25
> **Neosano said:**
> In the power manager you can tick "Lock screen when going for suspend/hibernate" in extended tab.

I am sorry that I did not mention this clearly in the title, but I am talking about lunbuntu, not about gnome. I have gnome installed in parallel with lubuntu, and everything works well in gnome. In lubuntu, I did not find "Power Manager", but it could be hidden somewhere.

---

### Post by Neosano on 2011-10-25
Yes, I was talking about lubuntu. Lubuntu uses xfce power manager by default.

---

### Post by doru001 on 2011-10-26
> **Neosano said:**
> Yes, I was talking about lubuntu. Lubuntu uses xfce power manager by default.

I installed xfce4-power-manager. It is not running by default. 

I killed gnome-power-manager and started xfce4-power-manager. xfce4-power-manager-settings showed that password is required. I tested and it is not required. 

To make xfce4-power-manager to run by default, I tried to mv /etc/xdg/autostart/gnome-power-manager.desktop but still only gnome-power-manager is started. 

If you have any ideas, shoot.

---

### Post by doru001 on 2011-10-26
Just in case you did not see the edit. :)

---

### Post by SteveDee on 2011-10-26
> **doru001 said:**
> I installed xfce4-power-manager. It is not running by default....

Lubuntu 11.10 uses xfce4-power-manager as the default manager, but Lubuntu 11.04 uses gnome-power-manager.

After installing xfce version, go to Synaptic Package Manager and remove the gnome version. Then go to Desktop Sessions Settings and enable Power Manager which should now reference the xfce version.

Reboot and the battery icon should appear on your panel. Right-click the battery and select preferences

> 
Originally Posted by Neosano View Post
In the power manager you can tick "Lock screen when going for suspend/hibernate" in extended tab.


...it works for me.

---

### Post by doru001 on 2011-10-31
> **SteveDee said:**
> Lubuntu 11.10 uses xfce4-power-manager as the default manager, but Lubuntu 11.04 uses gnome-power-manager.

After installing xfce version, go to Synaptic Package Manager and remove the gnome version. Then go to Desktop Sessions Settings and enable Power Manager which should now reference the xfce version.

Reboot and the battery icon should appear on your panel. Right-click the battery and select preferences



...it works for me.

Thank you for your answer. 

When I try to remove gnome-power-manager it will also remove ubuntu-desktop, which is necessary for gnome and maybe for lubuntu. Since I am not sure what will happen if I remove this package and I would like to be able to use gnome when I need it, I have postponed this action.

---

### Post by mcduck on 2011-10-31
> **doru001 said:**
> Thank you for your answer. 

When I try to remove gnome-power-manager it will also remove ubuntu-desktop, which is necessary for gnome and maybe for lubuntu. Since I am not sure what will happen if I remove this package and I would like to be able to use gnome when I need it, I have postponed this action.

The "ubuntu-desktop"-package is perfectly safe to remove, no desktop and no program depends on it. 

It's an empty metapackage, with all the packages used on default Ubuntu setup marked as it's dependencies. No package has it as their dependency, and as dependencies are one-way mechanic removing ubuntu-desktop won't remove anything else.

The only thing you should pay attention with when dealing metapackages like this is that you should reinstall them before you try to upgrade to next Ubuntu release version, as the metapackage will make sure you get all the new features during the release upgrade.

---

### Post by amjjawad on 2011-10-31
> **doru001 said:**
> When I try to remove gnome-power-manager it will also remove ubuntu-desktop, which is necessary for gnome and maybe for lubuntu. Since I am not sure what will happen if I remove this package and I would like to be able to use gnome when I need it, I have postponed this action.

Hi,

You need to be clear and explain in details which you haven't, I'm afraid.
I dislike to make any guess but I have to. Seems to me you have Ubuntu installed then you installed "lubuntu-desktop" package, right? you are not even Dual-Booting, correct?

You need to know that each package installed by default, is there for a reason. Changing it with something else, might work and might not work. Having that said, you need first to understand that installing lubuntu-desktop package is NOT like install Lubuntu. Why? because your desktop will be mixed and you can imagine the packages that you'll have.

Lubuntu 11.10, by default, uses XFCE Power Management while it was using GNOME on 11.04. Not sure about Ubuntu because I don't use it any more and not even sure whether you are using the latest release or not?

I'll stop right here and waiting for you to confirm my guess :)

---

### Post by doru001 on 2011-11-05
> **amjjawad said:**
> Hi,

You need to be clear and explain in details which you haven't, I'm afraid.
I dislike to make any guess but I have to. Seems to me you have Ubuntu installed then you installed "lubuntu-desktop" package, right? you are not even Dual-Booting, correct?

You need to know that each package installed by default, is there for a reason. Changing it with something else, might work and might not work. Having that said, you need first to understand that installing lubuntu-desktop package is NOT like install Lubuntu. Why? because your desktop will be mixed and you can imagine the packages that you'll have.

Lubuntu 11.10, by default, uses XFCE Power Management while it was using GNOME on 11.04. Not sure about Ubuntu because I don't use it any more and not even sure whether you are using the latest release or not?

I'll stop right here and waiting for you to confirm my guess :)

I have installed lubuntu over ubuntu, no dual boot. 
Version: Ubuntu 10.04.3 LTS (upgraded from 8.04 LTS). 

Thank you for the info.

---

### Post by amjjawad on 2011-11-05
> **doru001 said:**
> I have installed lubuntu over ubuntu, no dual boot. 
Version: Ubuntu 10.04.3 LTS. 

Thank you for the info.

Had to go back to page 1 of your thread to read the other suggestions. I see very good suggestions so have you tired these suggestions? please make sure to go back and read your thread from beginning.

Let me know if you need anything!

---

### Post by doru001 on 2011-11-05
> **mcduck said:**
> The "ubuntu-desktop"-package is perfectly safe to remove, no desktop and no program depends on it. 

It's an empty metapackage, with all the packages used on default Ubuntu setup marked as it's dependencies. No package has it as their dependency, and as dependencies are one-way mechanic removing ubuntu-desktop won't remove anything else.

The only thing you should pay attention with when dealing metapackages like this is that you should reinstall them before you try to upgrade to next Ubuntu release version, as the metapackage will make sure you get all the new features during the release upgrade.

I see that ubuntu-desktop does not depend on kernel. So you are sure that ubuntu-desktop only plays a role when Ubuntu release is upgraded, but not when the kernel or an update within a specific release takes place?

---

### Post by doru001 on 2011-11-05
I have installed xfce4-power-manager. 
I have removed gnome-power-manager. 
I have checked Xfce Power Manager (and not Power Manager) in Preferences > Desktop Session Settings. 
I have rebooted. 
I have run xfce4-power-manager-settings for settings. Password after hibernate was checked. 

... and it still didn't work, it didn't ask for password when exiting hibernation. 

Also, the mouse cursor is not visible after I exit hibernation and the Internet connection does not seem available any more. 

Fortunately, I do not need this facility very badly. 

I remind you that this install is old, it is upgraded from 8.04 and lubuntu is installed over. I did keep it clean and secure, though. 

Thank you all for your answers.

---

### Post by amjjawad on 2011-11-05
> **doru001 said:**
> I remind you that this install **is old**, it is **upgraded from 8.04** and **lubuntu is installed over**. I did keep it clean and secure, though.

May I suggest an advice that will never harm you but will help you big time?
Please, backup your files and go for Fresh New Installation of Lubuntu 11.10.

The time you spend in searching and fixing such issues is MUCH MORE than the time you'll spend on installing Lubuntu and tweaking it the way you want :)
This is from experience with more than 50 distributions I have tried and none were so good and last with me all that long except Ubuntu and Lubuntu. However, as it's not a secret, with Unity Thing, I'm much happier with Lubuntu and not going back at all :)

It's my personal experience and point of view. You are FREE to take it as an advice or suggestion and you are FREE to ignore it. Your call :)
I'm here to offer all what I can to help but at the end, it's you who will decide.

If you need ANYTHING regarding Lubuntu, I guess you know where and what to do ;)

---

### Post by doru001 on 2011-11-07
> **amjjawad said:**
> May I suggest an advice that will never harm you but will help you big time?
Please, backup your files and go for Fresh New Installation of Lubuntu 11.10.

The time you spend in searching and fixing such issues is MUCH MORE than the time you'll spend on installing Lubuntu and tweaking it the way you want :)
This is from experience with more than 50 distributions I have tried and none were so good and last with me all that long except Ubuntu and Lubuntu. However, as it's not a secret, with Unity Thing, I'm much happier with Lubuntu and not going back at all :)

It's my personal experience and point of view. You are FREE to take it as an advice or suggestion and you are FREE to ignore it. Your call :)
I'm here to offer all what I can to help but at the end, it's you who will decide.

If you need ANYTHING regarding Lubuntu, I guess you know where and what to do ;)

Thanks, I believe that you're right and I'll do just that after I finish some current jobs. The lubuntu install cd is also a fully functional live cd and it would recognize a TV tuner board just as Ubuntu 8.04 and 10.04 did? 

I am glad to hear that I picked the right distribution ;)

---

### Post by mcduck on 2011-11-07
> **doru001 said:**
> I see that ubuntu-desktop does not depend on kernel. So you are sure that ubuntu-desktop only plays a role when Ubuntu release is upgraded, but not when the kernel or an update within a specific release takes place?

Yes, I'm sure. the kernel has a metapackage of it's own for updates (*linux-generic* or similar, depending on which kernel you use), and no other package needs such feature (as new packages are never added to Ubuntu release afterwards, normal updates are just a question of taking an existing package and replacing it with a new version).

Anyway, it doesn't even make any difference what packages ubuntu-desktop depends on. It's a question of what packages depend on ubuntu-desktop (for which the answer is "none" ;)).

---

### Post by giannig on 2011-11-07
make a script that contains this command first, and then the pm-hibernate call
su UserName -c 'gnome-screensaver-command --lock'

---

### Post by amjjawad on 2011-11-07
> **doru001 said:**
> Thanks, I believe that you're right and I'll do just that after I finish some current jobs. 
You welcome. Please let me know if you need any thing and I'll be more than glad to help :)

> The lubuntu install cd is also a fully functional live cd
Just like any other Live-CD except it's Lubuntu :)
My thread cover an issue with Live-CDs that sometimes happens: [B]Lubuntu One Stop Thread > Post #2 > #1  
[/B]
> it would recognize a TV tuner board just as Ubuntu 8.04 and 10.04 did? 
If the driver is there then Yes.

> I am glad to hear that I picked the right distribution ;)
You sure did so be proud of that :D

---

### Post by amjjawad on 2011-11-07
> **mcduck said:**
> Yes, I'm sure. the kernel has a metapackage of it's own for updates (*linux-generic* or similar, depending on which kernel you use), and no other package needs such feature (as new packages are never added to Ubuntu release afterwards, normal updates are just a question of taking an existing package and replacing it with a new version).

Anyway, it doesn't even make any difference what packages ubuntu-desktop depends on. It's a question of what packages depend on ubuntu-desktop (for which the answer is "none" ;)).

Very nice information and great explanation, mcduck :)

---

### Post by doru001 on 2012-03-29
Thank you, giannig! I am using this script to protect lubuntu with a password and put it in hibernation: 
```
env SUDO_ASKPASS=/usr/bin/ssh-askpass sudo -Av
xscreensaver-command -lock
sudo -A pm-hibernate

```

Because lubuntu is installed on top of gnome, I also renamed: 
```
sudo mv /etc/init/gdm.conf /etc/init/gdm.conf.nostart
```
such that now I am using: 
```
/etc/init/lxdm.conf
```

I also did Disable Notifications for the network icon next to the clock in the lower right because it prevented lubuntu to enter hibernation. 

Because sometimes the screen is not locked before lubuntu enters hibernation it is not safe to use this script from a ssh connection when you are also logged in to GUI locally and your screen is not already locked. Still, you can do this by issuing the following commands: 
```
sudo -v
run the script given above, you have to make it executable first. 

```
Sometimes the script would not put lubuntu in hibernation. In this case, try to close down open applications. For example, a manual opened in a terminal could prevent lubuntu from entering hibernation.

---

