---
title: "Nvidia - black screen"
date: 2016-12-01
forum: Desktop Environments
---

### Post by drechsel on 2016-12-01
Hello all,

I'm on a dual monitor, Nvidia 630GT, ubuntu 16.10, Gnome.

After a number of freezes (mainly after resume from hibernate) with the nvidia 375 driver, I tried some older nvidia drivers.
Since than, I get stuck with a black screen when nvidia drivers are running.

Purging nvidia and coming back to nouveau leads to the white "The system is running on low graphics mode" display - none of these controls do anything reasonable. But I can switch to terminal 2, and a "startx" will sucessfully finish the boot process.

I tried several nvidia drivers, purged and reinstalled them several times, reinstalled gdm3 - but no succes.
So I'm a little out of clou now....

Fresh ideas appreciated ;)

Cheers,Wolf

---

### Post by lex4hex on 2016-12-01
Hey, same problem here, I couldn't find a solution yet...

---

### Post by drechsel on 2016-12-01
Maybe I can be of assistance now... :)

I purged the gdm and gdm3 package, this forced lightdm to jump into the gap. Till this moment everything is nice, no problems.
It might be a good idea to make sure that lightdm is installed before trying this.

Let me know whether it works and I achieved the ubuntu guru status now...;)

Good luck!
W

---

### Post by oldfred on 2016-12-01
I see many posts with issues with hibernation. I do not use it.

But with nVidia driver best to only install the correct or current version from Ubuntu repository. 
Repository is generally fairly current, but if a very new card like the new 1050 or other 10x0 versions you may need to add the ppa to get very newest driver version.

And installing a new driver will not remove old driver or settings. And that invariably leads to conflicts.
You must totally purge everything related to the old driver, use nomodeset to boot usually and then install new driver.

I have an older GeForce GT 620 and it just boots with open source driver. I do have nVidia driver in another install to test and could not tell any difference. 

       Updated driver search by nVidia model, do not download, just check correct driver version
[URL="http://www.geforce.com/drivers"]http://www.geforce.com/drivers

[/URL]
 Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
sudo apt-add-repository ppa:graphics-drivers/ppa 


 #What is installed
dpkg -l | grep -i nvidia
dkms status
lsmod | grep nvidia 
   
# Shows standard repository versions, which is the same as 
System Settings, Software & Updates icon, Additional drivers tab

ubuntu-drivers devices 

[URL="http://www.geforce.com/drivers"]
[/URL]

---

