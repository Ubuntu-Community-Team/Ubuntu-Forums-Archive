---
title: "Trouble all over the place... Please help!!!!"
date: 2009-03-14
forum: General Help
---

### Post by bleedisaster on 2009-03-14
Hi, 

   I'm fairly new to Ubuntu. I was watching some videos on youtube and I saw the possibilities that beryl offers a user. I installed ubuntu and have compiz, and emerald. I am having sevral issues though.

Firstly my machine is an HP DV6000. My Atheros (ar5007) isn't working. I've been up for 3 days straight browsing the forums trying all kinds of different things. I downloaded the back kernel and now its displaying a message "enabled but not in use". 

Also I tried setting the matrix screen saver as my desktop now I can't right click and use icons on the desktop though it still appears as a file in "places".

I have the screenlet manager but can't figure that out for the life of me. 

If anyone could help me understand how to enable tar.gz themes that would be awesome. 

Finlay I installed Ubuntu onto my friends gateway because she wants to utilize compiz as-well. There is a Nvidia issue the hardware is enabled but it is not recognized. 

We are both using Ubuntu version 8.10

Help would  be GREATLY appreciated.

Thanks,
charlie

---

### Post by ugm6hr on 2009-03-14
**For wifi**

Install [ath5k]("apt:linux-backports-modules-intrepid-generic") driver

Then (in Terminal):
```
echo ath5k | sudo tee -a /etc/modules
gksudo gedit /etc/modprobe.d/blacklist
```
Add the following to the bottom of this file and save:
```
blacklist ath_hal
blacklist ath_pci 
```

Reboot, and it should hopefully work.

Ref: [http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default](http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default)
Ref: [http://ubuntuforums.org/showthread.php?p=6861397#post6861397](http://ubuntuforums.org/showthread.php?p=6861397#post6861397)

---

### Post by sgosnell on 2009-03-14
tar.gz or .bz is an archive format, similar to .zip in Windows.  You have to extract the files from the archive in order to do anything with them.  Archive Manager will do that for you.

---

### Post by bleedisaster on 2009-03-22
I have since come across more trouble... Aparently Ubuntu fried out my hard drive! Whats up with that? So now my machine is in the shop getting worked on and I'm hesitant to put Ubuntu back on, its a shame I LOVE the OS.

---

### Post by ugm6hr on 2009-03-22
Perhaps this issue: [http://ubuntuforums.org/showthread.php?t=805570](http://ubuntuforums.org/showthread.php?t=805570)

Yes, this may be a problem.  It has been recognised.

However, it was apparently fixed in Intrepid 8.10:
[http://ubuntuforums.org/showthread.php?t=941864](http://ubuntuforums.org/showthread.php?t=941864)

But then it appeared it had only been partly fixed (see multiple comments):
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/59695)

To be honest, I'm not really certain what its status is now.

---

### Post by calvinps on 2009-04-05
> **ugm6hr said:**
> **For wifi**

Install [ath5k]("apt:linux-backports-modules-intrepid-generic") driver

Then (in Terminal):
```
echo ath5k | sudo tee -a /etc/modules
gksudo gedit /etc/modprobe.d/blacklist
```Add the following to the bottom of this file and save:
```
blacklist ath_hal
blacklist ath_pci 
```Reboot, and it should hopefully work.

Ref: [http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default](http://www.ubuntu.com/getubuntu/releasenotes/810#Atheros%20ath5k%20wireless%20driver%20not%20enabled%20by%20default)
Ref: [http://ubuntuforums.org/showthread.php?p=6861397#post6861397](http://ubuntuforums.org/showthread.php?p=6861397#post6861397)

The link is broken; whenever I click on it, an error box pops up saying that the package can't be found. :S

---

### Post by ugm6hr on 2009-04-06
> **calvinps said:**
> The link is broken; whenever I click on it, an error box pops up saying that the package can't be found. :S

Make sure you have updated your system, and Ubuntu is already online.

Also, it only works with Intrepid.

The manual download link: [http://packages.ubuntu.com/intrepid-updates/linux-backports-modules-intrepid-generic](http://packages.ubuntu.com/intrepid-updates/linux-backports-modules-intrepid-generic)

---

### Post by bleedisaster on 2009-04-26
So I got my computer back... And I was very hesitant to reinstall Ubuntu due to my hard drive frying out problem... I am still quite weary of using Ubuntu but damn do I hate windows! Anyway the wifi solution worked and I thank calvinps for the help. Hmm I installed flash and Second Life no problem and pretty much got a handle on the theme business. Though suggestions on how to apply the background, icons and buttons (from tar.gz file) would be appreciated. Also oppinions on weather or not it was Ubuntu that crashed my computer previously. I will give detailed system specs if required. TY all for your help!

---

