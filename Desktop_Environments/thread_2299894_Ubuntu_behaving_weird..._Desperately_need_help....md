---
title: "Ubuntu behaving weird... Desperately need help..."
date: 2015-10-22
forum: Desktop Environments
---

### Post by amantripathi4u on 2015-10-22
Hello Community.
I was using Ubuntu 14.04, and decided to install KDE environment on it. After some use I decided to upgrade to 15.04. Upgrade went fine and everything was working normal. Then I mistakenly used ```
apt-get autoremove
```, I thought it would save me some memory(I am new in Linux, a noob). After that there were dependencies related issues started to occur. I somehow fixed them (may be partially). Then I tried to upgrade the Plasma desktop. After the upgrade I found there were lots of issues like: 
[LIST]
[*]Wife Icon from system tray was not there, I couldn't find network manager, hence not able to connect to network. For connecting and disconnecting I needed to log out of system then log in into LXDE > connect to hidden wifi network > logout > login again to Plasma.
[*]Some of important programs like Dolphin, Konsole etc were missing. I needed to install them manually.
[*]Dolphin plugins were not working.
[*]Sometimes system won't let you log-out or shutdown.
[/LIST]
I thought this problem would be solved by removing KDE and then installing it again, so I searched for the right way to install kde completely and found this command on Ask Ubuntu: 

```
[COLOR=#111111][FONT=Consolas]sudo apt-get install aptitude
[/FONT][/COLOR][COLOR=#111111][FONT=Consolas]sudo aptitude remove '?and(?and(?reverse-depends(kubuntu),?not(?reverse-depends(ubuntu-desktop))), ?not(?or(?priority(required), ?priority(important))))' ubuntu-desktop+[/FONT][/COLOR]
```

and Bam... Everything became a nightmare after that. After running this command I rebooted, And It booted directly into shell. I tried to switch to gui with clrl-alt-f7, but it was only a blank screen.
I thought it must be a problem of lightdm, xserver or unity-desktop, so I reinstalled and reconfigured them all. After some efforts I succeeded to get Ubuntu splash screen but it was not entering into login screen. I continued to try, and after a while I decided to boot from previous kernel, rather than 3.19, and to my surprise it got into login screen.
Now another story begins here. When I select Ubuntu default, it gives only blank wallpaper and mouse cursor, after login.
And when I select Plasma, it boots normally but with the same problems ( same issues which I stated above i.e network problem and all).

Kindly tell me how to fix all these problem and make my machine run properly. 
Thanks a ton in advance.

---

### Post by deadpool25 on 2015-10-22
hello friend,

i might suggest full reinstall of ubuntu because i faced the same problem and i have tried all the traditional ways to fix it and it did not work other than reinstalling it

---

### Post by SeijiSensei on 2015-10-22
If you do reinstall from scratch, might I suggest leaving an empty partition of say 10-40 GB on the hard drive.  Then if you want to try another flavor like Kubuntu, you can install it to the empty partition and switch between them at boot.  In this arrangement it often helps to create a separate partition for /home that you can share between the two operating systems.

---

### Post by amantripathi4u on 2015-10-22
Thanks a lot friends for your response... I somehow have solved 90% of the problems, now Kubuntu is running well (except Yakuake is still not installing). Although I am not able to enter into Unity. But think I am content with Kubuntu. By the I am yet to to solve dependency problem. Synaptic is not listing any broken packages yet I am getting "you have held broken packages" error. Will look into it.. Thanks Again Mates.

---

