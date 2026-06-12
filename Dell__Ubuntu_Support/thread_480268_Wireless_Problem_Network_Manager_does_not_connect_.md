---
title: "Wireless Problem: Network Manager does not connect consistently"
date: 2007-06-21
forum: Dell  Ubuntu Support
---

### Post by cyanide on 2007-06-21
Hi,
      I have a Dell E1505 laptop,with Broadcom 1390 Wireless card.
     
      My problem is that when I am at home, network manager works perfectly when connecting to both unsecured and secured wireless networks,but when I go to my university network manager refuses to connect to the university wireless. The weird thing is that when I try to connect through wifi radar the wireless connection goes through perfectly and I can access the internet. 
     
       I was wondering if anyone could work with me to find why network manager does not connect to the university wireless and help me solve the problem.

Any help is appreciated.

---

### Post by kgr132 on 2007-06-21
I had a similar problem running Feisty on my Latitude D600 when I'm on the road staying in a lot of different hotels. I finally ditched network-manager in favor of wicd and my connectivity problems went completely away. You can uninstall network-manager via the Synaptic Package Manager. Wicd comes as a .deb file you can easily install. There's no separate version for Feisty so I installed the Edgy version. Pay attention to the notes, as you have to add the tray app. to your session startup manually if you want the tray app. to be there every time you boot up. It seems to offer far more flexibility with per connection settings, connects to access points faster and there's no annoying prompt for the keyring password when I'm at home using WPA. If you want to try it, you can find more about wicd here.
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)
Good Luck.
-K-

PS Don't miss reading the FAQ before you start:  [http://wicd.sourceforge.net/wiki/doku.php?id=faq](http://wicd.sourceforge.net/wiki/doku.php?id=faq)

---

