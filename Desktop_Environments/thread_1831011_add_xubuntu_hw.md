---
title: "add xubuntu hw?"
date: 2011-08-22
forum: Desktop Environments
---

### Post by ottosykora on 2011-08-22
I have running ubuntu 11.04. As I am not able to find a way how to use this unity, I am using ubuntu classic so far.

Now I wanted to add xubuntu desktop to my system, could then have choice at start up.

However when I try to install xubuntu-desktop from synaptic, it also tells me that it needs to remove ubuntu-desktop. This is not what I want, I would like to have it in addition, like on some of my other system wher I have ubuntu and xubuntu choice.

How to proceed?

---

### Post by ottosykora on 2011-08-23
can I add xubuntu desktop without ubuntu being removed? Hw?

---

### Post by raja.genupula on 2011-08-23
i have installed ubuntu-desktop in ubuntu 11.10 with "sudo apt-get install ubuntu-desktop" . at booting i am gonna choose what session i want . its not removed xubuntu desktop . both are going good . my curiosity allowed me make a try for 11.04 and now i am getting the same thing you are facing . but do one thing , give response as yes . if it is uninstalling let it go . but **dont** run any autoremove or clean . if you're not prompting for ubuntu desktop  session while log in . boot with xubuntu and install ubuntu-desktop . the installed files not cleaned so no need to downloading and its a matter of loading . so no loss to you (but desktop settings ). give a try

---

### Post by oldos2er on 2011-08-23
It's safe to remove the package ubuntu-desktop. [https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)

---

### Post by ottosykora on 2011-08-23
ok this looks like big job for the weekend.

Yes, I also have an original xubuntu on one old system and have installed later ubuntu-desktop to it and this did not remove anything from the original xubuntu.

All I wanted now do was just prepare the xubuntu desktop for near future when gnome2 will not be available any more, so I can at least *use* the system when left with the unity thing later.

Just wonder, why they included this remove thing into the xubuntu-desktop installer.

---

### Post by ottosykora on 2011-08-23
> **oldos2er said:**
> It's safe to remove the package ubuntu-desktop. [https://help.ubuntu.com/community/MetaPackages](https://help.ubuntu.com/community/MetaPackages)

but this is exactly what I *do not want to do*

I want keep all the current ubuntu 11.04, with all its negative parts and have xubuntu in addition, so I can select it on boot the same way as I do on other system (ubuntu/xubuntu 10.04)

---

### Post by raja.genupula on 2011-08-23
> **ottosykora said:**
> ok this looks like big job for the weekend.

Yes, I also have an original xubuntu on one old system and have installed later ubuntu-desktop to it and this did not remove anything from the original xubuntu.

All I wanted now do was just prepare the xubuntu desktop for near future when gnome2 will not be available any more, so I can at least *use* the system when left with the unity thing later.

Just wonder, why they included this remove thing into the xubuntu-desktop installer.

hmmm i dunno . give a try .

---

### Post by oldos2er on 2011-08-23
> **ottosykora said:**
> but this is exactly what I *do not want to do*

I want keep all the current ubuntu 11.04, with all its negative parts and have xubuntu in addition, so I can select it on boot the same way as I do on other system (ubuntu/xubuntu 10.04)

If you read the link, you'll see that removing ubuntu-desktop does not actually uninstall any package from your system. You'll have the choice of DE at login.

If when 11.10 is released and you wish to upgrade to it, you will need to install ubuntu-desktop again.

---

### Post by ottosykora on 2011-08-24
well I read it , but this is rather weird.

Also I can not find any info on that site which tells me why does it remove the ubuntu desktop when it installs xubuntu.

If I have to install it then again why does it unistall it first . Clear as with any other packages most of the things are left around, if I am supposed to have selection of DE then what does it remove and what do I have to reinstall after?

Why all this works the opposite way (add ubuntu to xubuntu) and this way?

---

### Post by Pirate Zoro on 2011-08-24
ubuntu-desktop is just a metapackage. If you remove the package, you WILL still have the Ubuntu desktop to choose at login.

---

### Post by ottosykora on 2011-08-24
but so why does it say it will remove ubuntu desktop when trying to install xubuntu?
And why I have to install ubuntu then again when I want upgrade? If this is not needed otherwise, why do I have it at all.

Sorry but this not easy to understand.

Because when I did install ubuntu desktop in addition to xubuntu, nothing was removed that time.

---

### Post by oldos2er on 2011-08-24
Perhaps only one *buntu-desktop can be installed at a time? I really don't know. You'd need to ask the devs why they package things this way.

---

