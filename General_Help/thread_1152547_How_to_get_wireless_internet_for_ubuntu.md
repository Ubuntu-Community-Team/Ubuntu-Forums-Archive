---
title: "How to get wireless internet for ubuntu"
date: 2009-05-07
forum: General Help
---

### Post by xxterry1xx on 2009-05-07
How do i get wireless internet for Ubuntu i tried installing ndiswrapper but its complicating.Is there any installer for ndiswrapper that's easy to install?


o and i have other questions how do i install wine?


Thanks 

(Im used to windows cause im a geek with it i don't mind getting to know ubuntu a little better :))

---

### Post by rainwalker on 2009-05-07
For Wine: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

For your wireless, what card/chipset/etc to you have? Ubuntu should automatically install or suggest drivers for it

---

### Post by drcdebaca on 2009-05-07
You shoud be able to go:

System > Administration > Hardware Drivers

and that should run a plug and play of sorts to scan your system and install the necessary drivers.  You may have to go to:

System > Administration > Software Sources

and allow third party or propriatary drivers to be used.

Hope this helps.

Cheers!

---

### Post by xxterry1xx on 2009-05-08
> **rainwalker said:**
> For Wine: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

For your wireless, what card/chipset/etc to you have? Ubuntu should automatically install or suggest drivers for it

I have WMP54GS and its linksys. what do you mean by chipset do you mean the mother boards chipset if so the that is nvidia nforce

---

### Post by xxterry1xx on 2009-05-08
> **drcdebaca said:**
> You shoud be able to go:

System > Administration > Hardware Drivers

and that should run a plug and play of sorts to scan your system and install the necessary drivers.  You may have to go to:

System > Administration > Software Sources

and allow third party or propriatary drivers to be used.

Hope this helps.

Cheers!

I restarted and i went to hardware drivers it says something about boardcom wireless driver but i dont have boardcom and when i go to install it it downloads it but i cant cause i dont have the wireless working yet

---

### Post by 3rdalbum on 2009-05-08
> **xxterry1xx said:**
> I restarted and i went to hardware drivers it says something about boardcom wireless driver but i dont have boardcom

[Yes, you do]("http://www.linuxforums.org/forum/suse-linux-help/24813-linksys-wireless-g-wmp54gs-drivers.html")*. The companies that make wireless cards actually use chips from Broadcom, Atheros, Intel, Realtek, Marvell etc. That's what matters. Your card has a Broadcom chipset in it - less than ideal for Linux.

> and when i go to install it it downloads it but i cant cause i dont have the wireless working yet

Why don't you plug your computer straight into the router using an Ethernet cable?

It's much better to use a native Linux driver, like the one that Hardware Drivers is suggesting to you, than try and emulate a Windows one.

*Don't worry about the thread where it says "there's no Linux driver". It was written in 2005 - ancient history in Linux terms.

---

### Post by golusweet on 2009-05-08
If you wireless driver is activated, Click Network connection icon on panel, and see if it sees any wireless network SSID.

---

### Post by xxterry1xx on 2009-05-08
> **3rdalbum said:**
> [Yes, you do]("http://www.linuxforums.org/forum/suse-linux-help/24813-linksys-wireless-g-wmp54gs-drivers.html")*. The companies that make wireless cards actually use chips from Broadcom, Atheros, Intel, Realtek, Marvell etc. That's what matters. Your card has a Broadcom chipset in it - less than ideal for Linux.



Why don't you plug your computer straight into the router using an Ethernet cable?

It's much better to use a native Linux driver, like the one that Hardware Drivers is suggesting to you, than try and emulate a Windows one.

*Don't worry about the thread where it says "there's no Linux driver". It was written in 2005 - ancient history in Linux terms.

Well i have a ethernet cable but my router is in the basement so i cant reach lol but all i need is that driver and im set lol so do you know where to download it?

---

### Post by rainwalker on 2009-05-08
If you can find out the name of the package you should be able to download it from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by xxterry1xx on 2009-05-08
> **rainwalker said:**
> If you can find out the name of the package you should be able to download it from [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Thanks so much :P but i installed the 
**ndiswrapper-utils-1.9**

AND
**ndiswrapper-common**


now what do i do??? i tryed connecting to my wireless network but it said disconnected every time? please help

---

### Post by rainwalker on 2009-05-08
> **xxterry1xx said:**
> Thanks so much :P but i installed the 
**ndiswrapper-utils-1.9**

AND
**ndiswrapper-common**


now what do i do??? i tryed connecting to my wireless network but it said disconnected every time? please help

I belive the correct thing to install would be the "b43-fwcutter" package; try that and see if it works

---

### Post by xxterry1xx on 2009-05-10
> **rainwalker said:**
> I belive the correct thing to install would be the &quot;b43-fwcutter&quot; package; try that and see if it works

Ok thanks i installed the thing but now what do i do? i really need help.

---

### Post by xxterry1xx on 2009-05-10
> **rainwalker said:**
> I belive the correct thing to install would be the &quot;b43-fwcutter&quot; package; try that and see if it works

ok i got the internet to work installed the ubuntu updates and got my nvidia driver next thing you know i restart then the internet wont work.... this is bs.... any help? lol

---

### Post by 11cerealkiller26 on 2009-05-26
> **xxterry1xx said:**
> How do i get wireless internet for Ubuntu i tried installing ndiswrapper but its complicating.Is there any installer for ndiswrapper that's easy to install?
 
 
o and i have other questions how do i install wine?
 
 
Thanks 
 
(Im used to windows cause im a geek with it i don't mind getting to know ubuntu a little better :))
 
 
TO INSTALL WINE = update your repository first"
 
open your terminal then type the following:
 
sudo apt-get update
sudo apt-get install wine
 
that's it...

---

### Post by hjacker on 2009-05-26
I have such problems in KDE with its sick plasma network manager. While in Ubuntu everything is sleek and smooth. What distro do you use BTW?

---

