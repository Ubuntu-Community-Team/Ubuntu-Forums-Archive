---
title: "Problems with new motherboard and graphics card"
date: 2011-11-23
forum: Desktop Environments
---

### Post by HasanYavuzOZDERYA on 2011-11-23
Recently I have changed my system except harddisks (which is motherboard, graphics card, ram, cpu changed). Win7 installation successfully handled the situation and after driver installations everthing just working fine. But things didn't go so well with ubuntu. 

when first i booted into ubuntu GUI didn't came up. So i started recovery console and run the command "startx". It complained about "fglrx" module. But when I tried to install it i recognized that network is not working (!). So I selected "dpkg" from recovery console which solved my network problem. then I have installed fglrx package.

After that login screen came up, but I just couldn't login. When I type my password screen goes a while then comes back to the login screen. I tried to do somethings via console but oops connection gone again! And this time dpkg just doesn't solve my problem :s

Now I can't login and can't install any packages since connection not working.. What do you suggest me to do??

One more thing, I have an installation on my usb hdd , ubuntu 11.04 gnome shell running. It runs without problems except networking :s

---

### Post by typhoon_tip on 2011-11-23
Do you have an ATI graphic card or NVIDIA ?

---

### Post by HasanYavuzOZDERYA on 2011-11-23
It's ATI, ASUS EAH6850.

---

### Post by oldrocker99 on 2011-11-23
Hmmm...three years ago I had to replace a motherboard, and, yes, I did have to reinstall the nVidia graphics driver. I don't think it's your graphics card, but some weird "feature" of Ubuntu.

---

### Post by HasanYavuzOZDERYA on 2011-11-23
This page helped me to solve my login problem.
[http://www.upubuntu.com/2011/10/how-to-fix-login-issues-on-ubuntu-1110.html](http://www.upubuntu.com/2011/10/how-to-fix-login-issues-on-ubuntu-1110.html)

I run```
ls -Shla | grep “Xauthority”
sudo mv .Xauthority Xauthority.old
sudo shutdown -r now

```

Now i can login, but my gnome-shell's top bar is showing really weird colors. I think it's a problem with GPU acceleration. When it comes to my network connection, I actually have one. I can navigate to my modem page via 192.168.1.1 but can't navigate to web ???

---

### Post by HasanYavuzOZDERYA on 2011-11-23
Oh, I have just typed DNS adresses manually via Network Settings dialogue. Now i can navigate to web. But i wonder what might be the problem?? :S

---

### Post by HasanYavuzOZDERYA on 2011-11-25
After 6 hours of working I finally solved my problems (for now everthing is okay).

First I made a clean installation of ubuntu 11.10. I didn't have problems with display this time. 

But it took a while to make network working. I found out that, system was using r8169 driver which is not working properly with 8111/8168 adapters. So I installed 8168 module. But that wasn't enough. At that moment I was able to navigate through web  only by typing IP adresses. DNS was not working. I have edited /etc/nsswitch.conf file according to this page [https://bugs.launchpad.net/ubuntu/+source/nss-mdns/+bug/140663](https://bugs.launchpad.net/ubuntu/+source/nss-mdns/+bug/140663) . After a restart DNS was working and Iwas able to navigate through web.

---

