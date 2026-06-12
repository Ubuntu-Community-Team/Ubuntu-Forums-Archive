---
title: "Doesnot have a dialer to connect to internet for linux"
date: 2006-03-16
forum: Desktop Environments
---

### Post by naveents on 2006-03-16
Hai, i am relatively new 2 ubuntu.Earlier,i have a time based internet plan that reqiure a dialer to connect to internet. but, now,i would like to connect to net from ubuntu. But,the company donot have a dialer for linux. it only has a windows dialer..what can i do?? i am having a broadband connection using cable modem..now,i am using net from XP...My ISP company is called asianet satellite communication pvt. ltd.,a small company in my place,india. I am having broadband connection,but i also have a download limit. So, the company provides a dialer using which i can connect to internet using the dialer and can keep the dlod limit under control..that is y i have a dialer..but, that dialer works only in xp, i have tried to download it from linux,but i am unable to install it..do i need to configure something to enter internet from linux??plz reply

---

### Post by _bacon_ on 2006-03-16
I guess if your modem is supported and the ISP uses standard dial-up access, all you need is already installed... you can start 
```
$ gksudo network-admin
```
or click on the network icon on the toolbar and then click on the configure button. From there you can configure your dial-up/modem connection if it's in the list.

---

### Post by akiro.yamamoto on 2006-03-17
These are some shots of the network configuration for serial modems.
Click on :
System >> Administration >> Networking.

Personaly I use gnome-ppp for my dial-up needs. These tools will only work
if your modem is supported natively by linux (external serial modem. internal
hardware modem etc.) or if you have drivers that will support your winmodem.

Hope this helps ;)

---

### Post by mrbiscuit on 2006-03-22
I'm too sure on this, but I thought somewhere in the Gnome PPP client it had some sort of "Account time on net restriction" thingey, but that might just be me. If you want to try something, thought it's not guarenteed to work, you could download wine from winehq.com and once installed, download the dialer onto your Linux Box and run the installer with wine in the terminal, however, you may have to install instmsia.exe and DCOM98.exe to get the installer to run.

---

