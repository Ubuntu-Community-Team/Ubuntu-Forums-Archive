---
title: "want to install Elegant Gnome theme ...."
date: 2010-08-29
forum: Desktop Environments
---

### Post by tusharkoshti on 2010-08-29
Hi friends..... I m a newcomer for Ubuntu.  I m using Ubuntu 10.04 
I want to install Elegant Gnome theme.  I m following link for that . The link is : 
[http://www.omgubuntu.co.uk/2010/07/give-your-desktop-dramatic-overhaul.html?utm_source=feedburner&utm_medium=twitter&utm_campaign=Feed%3A+d0od+%28Omg!+Ubuntu!%29&utm_content=Twitter](http://www.omgubuntu.co.uk/2010/07/give-your-desktop-dramatic-overhaul.html?utm_source=feedburner&utm_medium=twitter&utm_campaign=Feed%3A+d0od+%28Omg!+Ubuntu!%29&utm_content=Twitter)

I installed  [Nautilus-elementary]("http://www.omgubuntu.co.uk/2010/04/nautilus-elementary-230-for-lucid-gets.html") and  [Droid Sans Font]("apt:ttf-droid")   but couldn't install [Murrine and Equinox GTK engines]("https://launchpad.net/%7Eelementaryart/+archive/ppa") 
I couldn't get what is PPA and how to find path of PPA to tell Ubuntu where it is ??? Can anyone tell me how to install it ??? And I searched it is not trusted .... if it is not trusted....so if I install that...what will happen ???  
In this link    [http://gnome-look.org/content/show.php/Elegant+Gnome+Pack?content=127826&PHPSESSID=73a596a51bb9a2ab39a27239b37e903f](http://gnome-look.org/content/show.php/Elegant+Gnome+Pack?content=127826&PHPSESSID=73a596a51bb9a2ab39a27239b37e903f)  

how to install that theme ?? There they have written that download archive and extract it. How to do that ??? 
And if it is not safe to use PPA , then can anyone suggest another theme .... ??? 
Thanx in advance.

---

### Post by @robase on 2010-08-29
1. To install the Murrine Engine from Git:
```
sudo add-apt-repository ppa:murrine-daily/ppa
sudo apt-get update && sudo apt-get install gtk2-engines-murrine
```2. Then install  the Elegant GNOME theme:
```
sudo add-apt-repository ppa:elegant-gnome/ppa
sudo apt-get update && sudo apt-get install elegant-gnome

```3. Go to Applications -> Accessories ->  Elegant GNOME and choose "install the pack".

P.S. You **DON'T** need the Equinox engine anymore, this is a mistake of the article's author.

---

### Post by tusharkoshti on 2010-09-02
Thanx friend... theme successfully installed !!!! 
But now I m following 1 problem....my net is not working....and this is happening after installing this theme.... this issue is really related to this theme ?? 
Actually my net always used to give me problem. When I try to choose DSL connection ...it used to ask me Keyring password.....after giving that pass....he used to ask me DSL Authentication ....and I will have to enter my net password for that...after entering 2-3 times that password ...he used to accept it. Then I used to click on DSL connection but it never used to select easily....he always used to give Auto eth0. And after struggling 10-15 min....I used to select DSL connection. And once it was selected ...my net used to work smoothly. 
              1 more thing...when I installed Ubuntu...that time I could see Network Manager. But after when I logeed in 2nd time...I can't see NM..... then I used to this solution...
sudo gedit /etc/network/interfaces
 
then check that the file has only this 2 lines:
 
auto lo
iface lo inet loopback
 
Delete all the others then reboot...
Is it related to my current problem ??

---

### Post by @robase on 2010-09-03
> my net is not working....and this is happening after installing this theme.... this issue is really related to this theme ?? :) No, this is not related to the theme.

---

