---
title: "i need help with Ubuntu 11.04 XPS 15"
date: 2011-09-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jeggy on 2011-09-16
this is my first Thread on ubuntuforums :D

i have been a ubuntu user for a long time, but i just got an new laptop and i installed ubuntu 11.04 on it. after i installed it on my 'Dell XPS 15 i7' i got this error "it seems that you do not have the hardware required to run unity. Please choose ubuntu classic at the login screen and you will be using the traditional environment"
i like unity and really would like to get it back, i have been googling for a while now and i found that its something with the nvidia driver or something. i found this article [http://linux-hybrid-graphics.blogspot.com/]("http://linux-hybrid-graphics.blogspot.com/") but when i got to the line where i should write "echo OFF > /sys/kernel/debug/vgaswitcheroo/switch" i just get an error "bash: /sys/kernel/debug/vgaswitcheroo/switch: No such file or directory" and i looked the directory ain't there.
anyone that can help me?

---

### Post by Coder68 on 2011-09-20
IIRC, you can turn off the Nvidia card. Something about how it is connected and to what it is connected.

You can checkout a project called bumblebee though. That is designed to work with the Nvidia card. 

I myself am having issues with the Intel graphics, and may have to go to the Nvidia card even though I do not need it.

Good luck,

C68

---

### Post by web-e on 2011-09-21
Please don't install the nvidia proprietary driver at first.It will give you a black screen after reboot.

First uninstall any scripts you are using. Then install Ironhide ([https://github.com/MrMEEE/ironhide](https://github.com/MrMEEE/ironhide)) .Optionally also add xorg edgers ppa ([https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")) and update.It should work fine.

---

### Post by Coder68 on 2011-09-21
Thanks for the heads up on the Nvidia stuff.

---

