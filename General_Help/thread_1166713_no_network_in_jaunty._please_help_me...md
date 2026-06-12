---
title: "no network in jaunty. please help me.."
date: 2009-05-22
forum: General Help
---

### Post by valex on 2009-05-22
I'm using ubuntu 9.04 jaunty. now i can't connect to network and no network icon in notification area. 

there is a icon on panel. I clicked it and do nothing. but i right clicked and go properties i got a error message call "Could not launch nework configuration tool"  

i can't use "apt-get" becouse internet connection is not working.
I tried to download and install "network-manager" and "network-manager-gnome" manually but it depend on other packages. it tried to download dependencies.

please help me.

---

### Post by anezch on 2009-05-22
Are you sure your Ubuntu installed correctly without any error? And what's your network card/interface, model, and brand? Maybe you have problem with your hardware or the driver.

---

### Post by valex on 2009-05-22
yes I installed ubuntu correctly and it worked well. I connected via DSL router (D-Link dir-300). network is working properly. I checked it on my another os call windows 7. 

how do i fix it?

---

### Post by chamithmalinda on 2009-06-03
I have the **_same problem_**..... 
link :[COLOR=Teal]**[http://ubuntuforums.org/showthread.php?t=1164948](http://ubuntuforums.org/showthread.php?t=1164948)**[/COLOR]
and **many people** are suffering from this problem.
**[COLOR=Red]still there is no answer for this prob.....[/COLOR]**

---

### Post by chamithmalinda on 2009-06-03
Finally I found a way to connect to the Internet Sorry for Valex (Installing Mandriva).

Simple way but this is not the answer that i want(Still there is no network icon on the panel)

GO TO >> [COLOR=Red]**System > Preferences > Network Connections >**[/COLOR]
         
            and double click on your net connection(Properties) then put a tick mark on
            _**connect automatically**_.
            Then every time You boot Ubuntu connection will **automatically established**.

---

### Post by valex on 2009-06-03
> **chamithmalinda said:**
> 

GO TO >> [COLOR=Red]**System > Preferences > Network Connections >**[/COLOR]
         


There is no such place. my network manager is losed.!! :(
any other idea?

---

### Post by Teutorix on 2009-06-03
it seems that you need to reinstall, the network manager should ALWAYS install with ubuntu.

---

### Post by valex on 2009-06-03
> **valex said:**
> i can't use "apt-get" becouse internet connection is not working.
I tried to download and install "network-manager" and "network-manager-gnome" manually but it depend on other packages. it tried to download dependencies.



how do i install it?

---

### Post by Yellow Pasque on 2009-06-03
Technically, you don't need NetworkManager to connect to a network (I don't use it).

Another way to install the needed dependencies would be to boot into Windoze,  download them from packages.ubuntu.com and put them on a USB key.

---

### Post by ddrichardson on 2009-06-03
Is this a wired or wireless connection?

---

### Post by valex on 2009-06-03
> Another way to install the needed dependencies would be to boot into Windoze, download them from packages.ubuntu.com and put them on a USB key.

I tried to install network-manager.deb but it depend on "network-manager-gnome" then I tried to install network-manager-gnome.deb but it depend on "network-manager" . how is this happend? 

This is wired connection.

---

### Post by Teutorix on 2009-06-03
> **valex said:**
> I tried to install **network-manager**.deb but it depend on "**network-manager-gnome**" then I tried to install **network-manager-gnome**.deb but it depend on "**network-manager**" . how is this happend? 

This is wired connection.
WTF? cyclic paradox much? im surprised the computer didnt experience some kind of meltdown.:lolflag:

---

### Post by MimziM on 2009-06-03
does ubuntu recognize your ntwork card

lspci | grep (manufacturer of nettttttwork card)

what does that put out?

---

### Post by Yellow Pasque on 2009-06-03
Install them at the same time:
```
sudo dpkg -i network-manager.deb network-manager-gnome.deb
```

---

### Post by valex on 2009-06-03
> **Temüjin said:**
> Install them at the same time:
```
sudo dpkg -i network-manager.deb network-manager-gnome.deb
```

**it's working.!!! thank you all for helping me.** :)

---

