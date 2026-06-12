---
title: "kubuntu installed, but doesn't appear in sessions, cannot run kubuntu"
date: 2007-02-20
forum: Desktop Environments
---

### Post by dsimpson on 2007-02-20
I installed kubuntu-desktop on my ubuntu system 6.06, and when I logged out and logged back in it only goes to Gnome desktop. I checked sessions and there is listed: **Last   1.Default system session   2.Gnome   3.Failsafe Gnome   4.Failsafe Terminal.**There seems to be no way to log into KDE (kubuntu-desktop) 
Also when I change to try the choices it deletes the DNS settings from my networking settings and I am unable to access the internet until I restore them. 
It does seem to be on the system as I can find kde3 listed under /etc/kde3, and seems to all be included in /etc/bin. 
How can I access and run kubuntu-desktop from terminal, or can it be run using Applications/Systemtools/Konsole? I really would like to try it out to see if I might prefer kubuntu over ubuntu. I have had great experiences with Ubuntu and want to see how Kubuntu compares. 
Oh yeah! I installed using aptitude, and used the suggestions offered by psychocat in other postings. Everything seemed to go alright but I wasn't given the option of choosing the default desktop environment. That was the only variable that I noticed during installation.

---

### Post by rsambuca on 2007-02-21
Try a complete system restart.

---

### Post by dsimpson on 2007-02-21
Several times I have tried by completely shutting down and restarting the system, is this what you are referring to? The same thing happens, and the only way I can keep from losing my DNS setting is to choose the**Last**option for the GDM otherwise I will have to restore that also. Thanks for the reply.

---

### Post by dsimpson on 2007-02-21
My experience with KDE/Kubuntu has so far been terrible. And it seems that although many extol the virtues of Kubuntu there seems to be nobody that know how it works enough to offer a fix, so I am really close to removing it from my system for now until it becomes more stable. 
So far, I thought that I had it installed but when trying to reinstall it gave me the following error messages, and am missing some dependencies. No idea on how to resolve this issue, tried installing just Kubuntu, there was no program by that name alone, but came as desktop,  default. grub. artwork. etc. all with kubuntu as the main name such as kubuntu-desktop. This is what comes up when I try to reinstall:

The following packages have unmet dependencies:
  language-selector-qt: Depends: language-selector-common (= 0.1.20) but 0.1.20.1 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
gwenview [Not Installed]
kipi-plugins [Not Installed]
kubuntu-desktop [Not Installed]
language-selector-qt [Not Installed]

Leave the following dependencies unresolved:
koffice-data recommends openoffice.org-mimelnk
Score is -174

Accept this solution? [Y/n/q/?]  Answered No (n) then;

Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
koffice-data [1:1.5.0-0ubuntu9 (dapper)]

Keep the following packages at their current version:
gwenview [Not Installed]
kipi-plugins [Not Installed]
kubuntu-desktop [Not Installed]
language-selector-qt [Not Installed]

Leave the following dependencies unresolved:
koffice-data recommends openoffice.org-mimelnk
Score is -204

Accept this solution? [Y/n/q/?] This time answered Yes (y) then;

No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] answered Yes (y) then;


Writing extended state information... Done


As you can see, desktop, koffice, qwen and others weren't loaded and when I try to remove (sudo, aptitude, remove, kubuntu-desktop) I am unable to remove because aptitude is looking for kubuntu-desktop and related dependencies, so I have all the KDE files on my system and they don't work and I can't remove them. 

Once again, is there anyone who might have an idea. If there aren't any "experts", then maybe one of you Ubuntu "newbies" coming from another distro of KDE can help with some ideas. Thank you.

---

