---
title: "KDE installed but not getting any option to boot into KDE desktop"
date: 2011-07-31
forum: Desktop Environments
---

### Post by the_chink_between on 2011-07-31
Hi, I'm a new Ubuntu user (2-3 months) and I'm experiencing a two or  three problems with (I think) the Unity desk top.  I'm not sure they're  related so I'll post them as separate threads.  Here's the third.

I recently installed KDE desktop in order to try a different desktop environment.  I installed the application using the Synaptic package manager by selecting the KDE Plasma Desktop package and, subsequently, accepting the installation of the related packages.  The total installation size was a little over 600Mb.

After installation, the Grub menu showed Kubuntu blue instead Ubuntu mauve and the boot up screen showed the Kubuntu logo but each time the boot up completed I was still at the Ubuntu desktop.  As far as I can see I was never presented with an option to select the KDE desktop.

It may be worth noting that (a) I'm dual booting with Windows XP and (b) my original Ubuntu installation appears to be set to boot straight to the desktop screen, in other words it doesn't go through a "login screen".

As the KDE desktop installation didn't appear to work I've tried uninstalling it and that appears to have been successful except that the Grub is still the Kubuntu Grub.

I'd still like to give the KDE desktop a try but otherwise I'd like to get back to a clean installation of Ubuntu.  Can anyone help (with either)?

Regards and thanks.

---

### Post by Winelord on 2011-07-31
Hi, you need to change your Ubuntu login settings so that you are asked for a password. It's the login screen where you get to select which desktop environment you want.

---

### Post by jerrrys on 2011-07-31
KDE Plasma Desktop is a 330M download on my box.  so sounds like something went wrong.  may just want to remove it and try again.  this may do the job

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

also

[https://help.ubuntu.com/community/InstallingKDE](https://help.ubuntu.com/community/InstallingKDE)

---

### Post by Brad55 on 2011-07-31
Well you have a few options here.

1. Once logged in log out and you will have a loin screen once in the login screen click on options at the bottom and pick KDE. NOTE: the next time you reboot your computer you will automatically login to KDE if you don't have the login screen coming up.

To turn on the login screen go to system>Administration>login screen and change it so you don't auto login. Once this is done you can login to either desktop you want from the login screen.

2. You can boot a live CD of KDE and play with it.

3. You can install Kbuntu into a VirtualBox.

---

### Post by the_chink_between on 2011-07-31
Thanks everyone for the very helpful AND rapid advice.  I'll reinstall KDE and give your pointers a try.

Regards.

---

### Post by jerrrys on 2011-07-31
if your reinstalling do a 
[FONT=monospace]
[/FONT]sudo apt-get autoremove
afterwards

---

