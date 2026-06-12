---
title: "HowTo: Fix Compiz Problems In Gutsy"
date: 2007-10-22
forum: Desktop Environments
---

### Post by overlord.gaurav on 2007-10-22
This thread aims at compiling all the fixes for the problems faced in Compiz on Gutsy.
If I have missed a fix, kindly notify me to add it.

**1. Missing titlebar.**

Make sure that you have emerald installed on your computer. If not, then do this:
```
sudo apt-get install emerald emerald-themes
```

Now run this in a terminal:
```
emerald --replace & disown & exit
```

If it works then add this command to the startup:
```
emerald --replace
```

Still not working?
A suggested fix by a user: *only for **nVidia** users*
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```


**2. Unable to get Compiz to work on an Intel graphic card.**

Due to | [bug 111257]("https://bugs.launchpad.net/xorg-server/+bug/111257"), compiz is disabled on the Intel i965 based video cards. To fix it, download [this file]("http://www.fileden.com/files/2007/9/28/1467484/compizubuntuintel.zip"), unzip it, and follow the instructions in "description and README." 

[COLOR="Red"]Note: If you enable Compiz on an Intel card there will be issues with viewing media files, please see the bug report above for details[/COLOR] 


**3.How to get Desktop effects on ATI x1400**
[http://ubuntuforums.org/showthread.php?t=574302](http://ubuntuforums.org/showthread.php?t=574302)
This guide is simple and clear to follow! :)


**4.Compiz-fusion doesn't initiate**

Launch the Synaptic Package Manger.
Package -> Force version -> select the Gutsy version instead of trevinho's repo version.
This should fix it. Now you can try running CCSM.


**5.No Compizconfig-settings-manager [CCSM]**
Inspite Gusty provides you with compiz, it wouldn't provide you with the settings manager, you'll have to install it manually through the synaptic package manager OR the terminal. In short, do this to install it:
```
sudo apt-get install compizconfig-settings-manager
```


**6.Compiz on Kubuntu**
System -> Preferences -> Appearence
That's all!


**7.Compizconfig-settings-manger on KDE**

First, open a console.

Now we make sure that CCSM is removed from the computer.
```
sudo apt-get remove compiz compiz-kde compizconfig-settings-manager emerald
```

Now we install the latest version of CCSM:

```
sudo apt-get install compiz compiz-kde compizconfig-settings-manager emerald
```

That should install everything you need. 

Next, to get it running:

```
/usr/bin/compiz.real
```

Now it should be running. In the K-menu, you should find a Settings sub-menu with the Settings-program. That's all I needed to do anyway, apart from activating the restricted graphics driver.


PS: If you find any other problem with a fix, do inform me, I've already used about two hours in compling this.

---

