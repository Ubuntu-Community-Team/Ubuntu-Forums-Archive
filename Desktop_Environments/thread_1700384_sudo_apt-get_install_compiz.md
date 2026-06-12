---
title: "sudo apt-get install compiz*"
date: 2011-03-04
forum: Desktop Environments
---

### Post by Dimesh on 2011-03-04
[SIZE="3"]Al salamo aleekom

and hi everyone
----------------

I wanted to install compiz manager so i searched for it online and found pages explain something and it say write that in your terminal 
```
sudo apt-get install compiz*
```
then i accept to download about 600Mb then i found that it was not just compiz or emerald but it was KDE-Desktop environment,  the problem now is it takes about 3Gb from my file-system and i do not like to work with KDE-Desktop although i love it, 
i need a way to remove KDE-Desktop environment without any problem leads me to install ubuntu again, so take care in advice i do not go through an frequency one , i hope you to be sure for recommendation AND thanks for reading.

note if you are trying to say that :
```
sudo apt-get remove --purge kubuntu-desktop
```
that is my result
```
sudo apt-get remove --purge kubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package kubuntu-desktop is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 32 not upgraded.
```
this is an online advice but does not work , why? i do not know although KDE works and see it and use it[/SIZE] :-k

---

### Post by stinkeye on 2011-03-05
kubuntu-desktop is a meta-package which merely lists a whole bunch of packages necessary for the kde desktop environment.
meta-packages are used so that that you don't have to specify all the packages separately, but install all the necessary packages by specifying just the meta-package.
So if you install all the necessary packages to run kde you will indeed have kde even if you didn't install kubuntu-desktop.

Possibly you could install **kubuntu-desktop** and then run **sudo apt-get remove --purge kubuntu-desktop**

I have no idea if this would work.
Personally, I would save my data and reinstall.

Where did you get the **sudo apt-get install compiz*** command from?
Online advice is like any other advice.
It needs to be either official documentation or a trusted source.

---

### Post by ankspo71 on 2011-03-05
Hi,
If you are using the Gnome desktop (Ubuntu) try using the instructions on this link...
Getting Back to a Pure Gnome on Ubuntu:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

They also have instructions for removing KDE from XFCE (Xubuntu) and LXDE (Lubuntu). Those instructions can be found in the menu on the left side.

```
sudo apt-get install compizconfig-settings-manager 
```would have been the best command to install Compiz Configuration Settings Manager.

I think the reason why the compiz* wildcard command installed the KDE desktop is because there are  compiz packages for the KDE desktop (such as compiz-kde and compizconfig-backend-kconfig) and those types of packages require the KDE desktop.

APT doesn't support removing (or autoremoving) the additional packages that come from installing _[metapackages]("https://help.ubuntu.com/community/MetaPackages")_ (like kubuntu-desktop, etc). I'm only guessing now but I think it is set up this way to prevent people from accidentally removing their entire desktop, and to prevent breaking the remaining installed packages.

Hope this helps.

---

### Post by Dimesh on 2011-03-05
[SIZE="3"]do you mean by this page that Ubuntu will return to it original case as i installed at first , no program i installed , no program i setup and no configurations i made , etc...
or what ?
i am afraid from loosing something, do you know before trying the command in this page ?!
[/SIZE]

---

### Post by ankspo71 on 2011-03-05
> **Dimesh said:**
> [SIZE="3"]do you mean by this page that Ubuntu will return to it original case as i installed at first , no program i installed , no program i setup and no configurations i made , etc...
or what ?
i am afraid from loosing something, do you know before trying the command in this page ?!
[/SIZE]

Hi,
Yes I have used the commands on that page before, and many people here at the ubuntuforums still recommend using it. The command will remove Kubuntu and Kubuntu's applications from your computer, then it will reinstall Ubuntu to make sure Ubuntu still works. Your Gnome and Ubuntu applications and settings will still be there. Sometimes this will remove an application that you want to keep, but it can be reinstalled again and it will keep the same settings because the settings are still in your home folder. For example, if you wanted to keep the KDE music player called Amarok, you will have to reinstall that application because it will get removed because it is a part of Kubuntu.

Also, be sure to read this:
> 
It's possible that the commands might remove some other packages you have since added to the default and want to keep. If that's the case, keep track of which packages those are and reinstall them. Your settings should still be there. [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
Hope this helps.

---

### Post by Dimesh on 2011-03-05
Thanks Mr.ankspo71, KDE-Desktop environment has been removed successfully, it also removed some packages i do not take care at revision but no problem i can install them again ...

---

