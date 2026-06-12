---
title: "Update Ubuntu to Xubuntu without Install?"
date: 2012-08-12
forum: Desktop Environments
---

### Post by Ichido on 2012-08-12
I have several questions.
Info: I have Ubuntu 10.04, Xubuntu 12.04 and Linux Mint 12 all on the same Dell 1525 Laptop.
I am writing a book in Libre Office (Xubuntu) and Open Office (Ubuntu).
The Book's file size is 1.5MB in Word .DOC and it's only 303KB in .ODT.
When I Edit/Write in O.O. on Ubuntu, I get System Freezes (Gray Screen) and have I have to use the Power Button to Reboot.
Using Xubuntu, I don't have this problem.
Questions:
Can I Update Ubuntu 10.04 to Xubuntu 12.04 without Re-Installing?
Can I just Change the Gnome Desktop of Ubuntu to Xfce?
If I change Open Office on Ubuntu to Libre Office will that help the System Freezes?
Thanks for any advice!

---

### Post by Morderwurst on 2012-08-12
> Info: I have Ubuntu 10.04, Xubuntu 12.04 and Linux Mint 12 all on the same Dell 1525 Laptop.Out of curiosity, why do you use separate partitions for xubuntu and ubuntu? You can install them side by side and just select which desktop environment you want to use at the login screen: [http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

> 
When I Edit/Write in O.O. on Ubuntu, I get System Freezes (Gray Screen) and have I have to use the Power Button to Reboot.So the system becomes completely non-responsive? If this is the case, can you switch between terminals (ctrl+alt+F1, for example)? If that's not the case, then maybe use xkill to stop the program [http://en.wikipedia.org/wiki/Xkill](http://en.wikipedia.org/wiki/Xkill) (alt+F2 and type xkill, then click on the non-responsive program).

> 
Can I Update Ubuntu 10.04 to Xubuntu 12.04 without Re-Installing?It might not go smoothly. You should backup all essential files first. You'll probably want to update to ubuntu 12.04 and then, as above, install xfce alongside... although it seems that you already have an xubuntu 12.04 system on another partition(?)

---

### Post by 2F4U on 2012-08-13
> Out of curiosity, why do you use separate partitions for xubuntu and  ubuntu? You can install them side by side and just select which desktop  environment you want to use at the login screen: [http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

Ubuntu is 10.04 and Xubuntu is 12.04, so what you suggest doesn't work.

> Can I Update Ubuntu 10.04 to Xubuntu 12.04 without Re-Installing?

Why would you want to do that? You have Xubuntu 12.04 already installed and if you want additional desktop environments, these can be added to the existing Xubuntu 12.04 installation.

> Can I Update Ubuntu 10.04 to Xubuntu 12.04 without Re-Installing?

If you attempt to upgrade your 10.04 installation it will become Ubuntu 12.04 with the Unity interface. Of course, you can install the package xubuntu-desktop and then you have both interfaces available.

---

### Post by lads on 2012-08-13
> **Ichido said:**
> 
If I change Open Office on Ubuntu to Libre Office will that help the System Freezes?

Yes, most likely your problem is using an old version of the software. I'd suggest you to uninstall Ubuntu 10.04 and install the Unity DE in Xubuntu; this way you'll get both DE on a single OS.

---

### Post by Morderwurst on 2012-08-13
> **2F4U said:**
> Ubuntu is 10.04 and Xubuntu is 12.04, so what you suggest doesn't work..

I was merely suggesting that it is possible to install the xfce desktop environment (or others) alongside the gnome DE.

---

### Post by jemadux on 2012-08-13
sudo apt-get install xubuntu-desktop

---

### Post by Ichido on 2012-08-13
Wow! Talk about great Support and Help!
Thanks to everyone who replied!
I didn't know I could have different Desktop Environments for the same "home/" OS.
Thanks again.

---

### Post by Ichido on 2012-08-13
[QUOTE=Morderwurst;12168197]Out of curiosity, why do you use separate partitions for xubuntu and ubuntu? You can install them side by side and just select which desktop environment you want to use at the login screen: [http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

There is No Option the Select Desktop!?
It just boots to Ubuntu.
What next?

---

### Post by Buntu Bunny on 2012-08-13
> **Ichido said:**
> 
There is No Option the Select Desktop!?
It just boots to Ubuntu.
What next?

You should be able to click on the Ubuntu symbol to the right of your name on the login screen. That will give you a menu of DE choices. Ubuntu will remember which one you chose the previous session and automatically login to that one the next time, unless you change it.

---

### Post by Buntu Bunny on 2012-08-13
> **Morderwurst said:**
> Out of curiosity, why do you use separate partitions for xubuntu and ubuntu? You can install them side by side and just select which desktop environment you want to use at the login screen: [http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

Morderwurst, thanks! I've been wanting to try Xfce and wasn't sure if I could install it on Ubuntu. I really am not liking Unity and Xfce looks like a good option.

---

### Post by Bucky Ball on 2012-08-13
In the 'Sessions' popup at the login in screen. Choose 'Xubuntu Session' or 'Xfce session'. 

One of the reasons I use Xubuntu is because it's lighter. Thus installing ubuntu-desktop defeats the purpose for me. My desktop hybrid setup, on the other hand, is like the work of a techno Frankenstein! Also, when you install *buntu-desktop anything you are installing all the related apps etc. If you went for Kubuntu-desktop you are going to get a lot of bloat you probably don't need. Your menus will include all apps from any *buntu-desktop installed. Again, much of this you probably don't need. 

Just a thought; if you are installing xubuntu-desktop to the faulty setup, not sure that will change anything for your errors because that doesn't change the base system in anyway. You're not actually 'installing' again. Most of it's already there. All 'buntu family uses same base system. 

Enjoy. There are all sorts of DEs out there. ;)

---

### Post by Morderwurst on 2012-08-13
> **Buntu Bunny said:**
> Morderwurst, thanks! I've been wanting to try Xfce and wasn't sure if I could install it on Ubuntu. I really am not liking Unity and Xfce looks like a good option.

You're welcome! I feel the same way about Unity.... You should know that installing xfce in this way will add some apps such as abiword. You might want to selectively remove them (if you prefer libreoffice, for example). Good luck!

(edit)...and just realized bucky ball said the same thing, basically. :p

---

### Post by Buntu Bunny on 2012-08-14
> **Morderwurst said:**
> You're welcome! I feel the same way about Unity.... You should know that installing xfce in this way will add some apps such as abiword. You might want to selectively remove them (if you prefer libreoffice, for example). Good luck!

Thanks for that tip. I take it I have to remove unwanted apps after installation? There's not an option to choose which to install?

---

### Post by vasa1 on 2012-08-14
> **Morderwurst said:**
> ... installing xfce in this way will add some apps such as abiword. ...
I installed [Xfce 4.10]("https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10") on top of Ubuntu 12.04 so that I can log into either Unity or Xfce depending on my mood.

I don't remember having to uninstall abiword (and I don't have it installed). That's why I feel it isn't part of the package.

---

### Post by Buntu Bunny on 2012-08-14
Installed Xfce without problem and I like it!

It did install abiword as part of the package, oh well. I also have the choice of either a Xfce or Xubuntu session at login. Can't see any difference between them at first glance however.

---

### Post by cmcanulty on 2012-08-14
To get to the option to select a desktop you have to log out or turn off auto login just once.

---

### Post by Morderwurst on 2012-08-14
> **Buntu Bunny said:**
> Installed Xfce without problem and I like it!

It did install abiword as part of the package, oh well. I also have the choice of either a Xfce or Xubuntu session at login. Can't see any difference between them at first glance however.

It is kind of weird that you can select either at login. The difference seems to be pretty minimal:

[http://ubuntuforums.org/showthread.php?t=1895108](http://ubuntuforums.org/showthread.php?t=1895108)

---

### Post by Ichido on 2012-08-14
> **Buntu Bunny said:**
> You should be able to click on the Ubuntu symbol to the right of your name on the login screen. That will give you a menu of DE choices. Ubuntu will remember which one you chose the previous session and automatically login to that one the next time, unless you change it.

There is Nothing to the right of my name.
The Ubuntu Logo is at the Top of the Log In Window.
On the Bottom Task Bar shows "Sessions" Menu. Changing it from Gnome to xterm. Choosing xterm opens a Terminal Window in the Upper Left Quarter of the screen. Now What?
:confused:

---

### Post by Ichido on 2012-08-14
> **cmcanulty said:**
> To get to the option to select a desktop you have to log out or turn off auto login just once.

Several times of both of your suggested options does nothing.
I do not use auto-login.

---

### Post by Ichido on 2012-08-14
> **jemadux said:**
> sudo apt-get install xubuntu-desktop

Thanks, but this does nothing.
No changes or choices of any kind.

---

### Post by Ichido on 2012-08-14
> **Morderwurst said:**
> You'll probably want to update to ubuntu 12.04 and then, as above, install xfce alongside... although it seems that you already have an xubuntu 12.04 system on another partition(?)

How do I Update 10.04 to 12.04?

---

