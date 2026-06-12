---
title: "Wireless Networking settings?"
date: 2006-01-04
forum: General Help
---

### Post by fancyydk on 2006-01-04
Hi, I'm a newb Linux user. I'm fairly new to Linux, but have used Red Hat, SuSE, gentoo, and Ubuntu. I have been using 64-bit Ubuntu Breezy for about three weeks now. I got my wireless networking configured and all, but there is a minor problem that I'm experiencing. The problem is, my wireless network is not automatically configured and I always have to go to terminal and type

sudo iwconfig wlan0 key open ***************** where *************** is my WEP key. 

If I do this using the GUI network configurer, I can never get the network configured. My guess is, when I type in the WEP key in the GUI application, somehow it's incorrect. And I'm not even sure whether the key is hex or ASCII. I had this problem in SuSE too, but I solved it by choosing hex instead of ASCII and inserting dashes ('-') between every four characters like this ****-****-****-****-****-**. That doesn't seem to work in Ubuntu. Any idea as to what I should do to make this automatically work? Thanks in advance.

---

### Post by KingBahamut on 2006-01-04
[http://doc.gwos.org/index.php/Networkwifi](http://doc.gwos.org/index.php/Networkwifi)

Try this.

---

### Post by armcurl on 2006-01-05
[QUOTE=KingBahamut][http://doc.gwos.org/index.php/Networkwifi](http://doc.gwos.org/index.php/Networkwifi)[/QUOTE]

Links through to [https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

---

### Post by fancyydk on 2006-01-06
Thank you for your replies. I went to the links you guys suggested, but they seem to have solutions pertaining to fundamental problems like how to set up your network cards or right drivers or configuring the network. In my case, I have succeeded in configuring my network. It's just that I have to do it in a terminal like this

fancyydk@ubuntu:~$ sudo iwconfig wlan0 key open **************************

I have to do this everytime I log in. I would like to have the computer automatically configure its network environment. So (in gnome) I go to System->Administration->Networking. There, after selecting Wireless connection, I go to Properties. Then a window pops up and I can enter the network information that I can do likewise in a terminal. But, in a terminal, I can specify the WEP options like open, instead of shared, and I have no options such as Hexadecimal or Plain(ASCII). That's what I am confused about. Any further suggestions or ideas? Thanks in advance.

---

### Post by zahidism on 2006-01-07
what ver of ndiswrapper and what card and what driver are you using

---

### Post by fancyydk on 2006-01-07
[QUOTE=zahidism]what ver of ndiswrapper and what card and what driver are you using[/QUOTE]
I'm using ndiswrapper 1.1. It came with Ubuntu 5.10. I tried to download 1.7 and compile it, but failed. And I'm using the 64-bit version of the broadcom driver on Acer's website. But there's nothing wrong with either ndiswrapper or the driver. I can connect to the Internet fine. It's just that I have to manually type in commands like this:
fancyydk@ubuntu:~$ sudo iwconfig wlan0 key open **************************

When I try to configure the settings using the GUI application, that's where the problem arises. I can't connect to the Internet when I use the GUI network configurer. And what confuses me is, whether I should choose Plain(ASCII) or Hexadecimal, and whether I should include dashes('-') between every four characters or not. Because I had this problem in SuSE also, and I solved it by  selecting Hexadecimal and inserting dashes. But that doesn't seem to work.

---

