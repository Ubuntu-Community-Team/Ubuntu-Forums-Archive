---
title: "Update Problem on Dell Inspiron 1525"
date: 2010-05-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Xsteel200 on 2010-05-31
Hey guys, new here. Just a problem with the updates on Ubuntu 8.04 LTS. I've been running along side windows 7 on a Dell Inspiron 1525. I keep getting the :"System Restart Required" message,and  even if i do restart the system,the message persists. As such I am unable to get any new updates. Any idea's on how to get out of this mess? 

Thanks! 

P.S: On an completely unrelated problem, the track pad it seems keeps auto clicking, so it becomes kind of a hassle when your typing as the cursor will suddenly move somewhere else. 

Thanks Again!

---

### Post by Xsteel200 on 2010-05-31
UPDATE: ok, so i typed sudo update-manager -d into the terminal and i got the option to upgrade to the 10.04 LTS release which is what i had been planning to do. So im thinking of going ahead with the upgrade. Should I ? Or might the flaw with the system restart messege corrupt the upgrade?

---

### Post by DeXeS on 2010-05-31
The first problem I have no answer but the second I can maybe help you with.

with the trackpad auto clicking.. do you mean that you touch it slightly with your palm?
If that is it and you have a Synaptics touchpad set PalmDetect to 1 in xorg.conf (you probably have a Synaptics touchpad since I have it to on my Dell Studio 1555)

see [http://ubuntu-tutorials.com/2006/12/10/tweaking-your-synaptics-touchpad-laptops-ubuntu-6061-610/]("http://ubuntu-tutorials.com/2006/12/10/tweaking-your-synaptics-touchpad-laptops-ubuntu-6061-610/")how to do that.

---

### Post by Xsteel200 on 2010-05-31
thanks for the help! Also i upgraded to 10.04 LTS however, there was an error with the Adobe flash plugin, Now when use the Package Manager to install the flash package, since it didn't properly install with the initial upgrade, i get this message:

 E: flashplugin-nonfree: Package is in a very bad inconsistent state - you should  reinstall it before attempting a removal.

Any clues as to how one should fix this corruption?

EDIT: Just found out that I cant install any program unless this is fixed,and it also means no youtube videos and other flash-based web applications. XD :/

---

