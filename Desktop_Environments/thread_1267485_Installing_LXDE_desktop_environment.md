---
title: "Installing LXDE desktop environment"
date: 2009-09-15
forum: Desktop Environments
---

### Post by Dangger on 2009-09-15
Hi all, so I was inspired by the [Psychocats tutorials]("http://www.psychocats.net/ubuntu/index") and even asked the author if there were any plans on making a tutorial on how to install the LXDE desktop environment and how to remove it and go back to a pure gnome, kde or xfce environment. The short answer was no. 

So I thought that I would attempt to do it. 

[B]
BEWARE: [/B]:evil:

I have been on ubuntu since I created this account, therefore **I am extremely unexperienced**. 

I have tried this method extensively only in a virtual machine.

This should only be the starting point to building a better method if people are willing to try it and give feedback.

[B]
 Getting LXDE in Ubuntu Jaunty (9.04)[/B]

To get the LXDE you must enter the following command on a terminal

```
sudo apt-get install lxde
```It will prompt you for confirmation.

Once finished you can access LXDE by login out and choosing lxde session from the "session type" menu. 

By this point you should be in the lxde environment. 


**Removing LXDE environment:**

Before you remove the lxde desktop you should login in another session (gnome, kde or xfce) and type the corresponding commands in the terminal. **DO NOT remove lxde inside lxde** because you will be unable to click on the logout icon and you will have to reboot from terminal to change session ("sudo reboot" without quotes if it's too late). 

 ```
sudo apt-get remove arj leafpad libbeecrypt6 libjpeg-progs libneon27 libobparser21 libobrender21 librpm4.4 lxappearance lxde lxde-common lxde-core lxde-settings-daemon lxpanel lxrandr lxsession-lite lxterminal obconf openbox openbox-themes p7zip-full pcmanfm rpm xarchiver xscreensaver
```[B]
Final Step[/B]

To make sure you did not remove a common file, run the following commands in the terminal after removing LXDE (thanks to [theZoid]("http://ubuntuforums.org/member.php?u=460170")):

```
sudo apt-get update
sudo apt-get install -f
```Try it as is and give some feedback please :D

---

### Post by kellemes on 2009-09-16
I don't see why you should (re)install the *ubuntu-desktop packages.. these are huge!
Simply remove LXDE and dependencies and you're done.

---

### Post by theZoid on 2009-09-16
> **kellemes said:**
> I don't see why you should (re)install the *ubuntu-desktop packages.. these are huge!
Simply remove LXDE and dependencies and you're done.

Yeah....OP think that one through again....

---

### Post by Dangger on 2009-09-16
> **kellemes said:**
> I don't see why you should (re)install the *ubuntu-desktop packages.. these are huge!
Simply remove LXDE and dependencies and you're done.


Honestly, it's only out of precaution, and you reinstall them again only after removing the lxde package. you could run the command without reinstalling your previous desktop or just hit n when asked.

---

### Post by theZoid on 2009-09-16
> **Dangger said:**
> Honestly, it's only out of precaution, and you reinstall them again only after removing the lxde package. you could run the command without reinstalling your previous desktop or just hit n when asked.

Nothing wrong with what you posted, just pointing out it was really necessary to reinstall the desktop if you know removing LXDE didnt remove a common file or something, but a:

```
sudo apt-get update
sudo apt-get install -f
```

would take care of that though.

---

### Post by Dangger on 2009-09-17
> **theZoid said:**
> Nothing wrong with what you posted, just pointing out it was really necessary to reinstall the desktop if you know removing LXDE didnt remove a common file or something, but a:

```
sudo apt-get update
sudo apt-get install -f
```would take care of that though.


Great, thank you.

---

