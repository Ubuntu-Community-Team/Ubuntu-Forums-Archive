---
title: "networking problem with Win XP"
date: 2009-04-11
forum: General Help
---

### Post by mickie.kext on 2009-04-11
Hi all!!

I have problem to connect my Ubuntu PC with another Win XP based. I have two Gigabit LAN ports, and using one for internet conection (which works fine) and another for connecting to another PC with crossover cable. When I boot windows Vista (which I use in dualBoot with ubuntu) all works fine, but in Ubuntu I can't get shared files from another PC. 

First when installed Ubuntu, radio button (when clicked on conections) was empty, but when I set IP adresses and subnet mask manually, radio button got full, but still can't se shared files in windows network. I think is it because workgroup, but not sure how to set that in Linux. 

Help please

---

### Post by mickie.kext on 2009-04-11
Please... anyone?

---

### Post by mickie.kext on 2009-04-12
Now every time I restart computer, radio butin goes emptu until I set IP address again. And still no files from other computer!!

I'm runing out of patience, this crap is gone from my hard drive if it wont start working soon.

---

### Post by romuald_geo on 2009-04-12
You can access Windows shared folder by manually specifying it's network name(computer name) or ip adrress.To access a shared folder, open a Nautilus file browser window (Places &#10148; Home), and then click Go &#10148; Location. In the box, type the following:
```
smb://computer name/
```
Alternatively, if you wish to use the IP address, type the following:
```
smb://IP address/  
```

---

### Post by romuald_geo on 2009-04-12
what radio buttons are you talking about?

---

### Post by mickie.kext on 2009-04-12
> **romuald_geo said:**
> You can access Windows shared folder by manually specifying it's network name(computer name) or ip adrress.To access a shared folder, open a Nautilus file browser window (Places &#10148; Home), and then click Go &#10148; Location. In the box, type the following:
```
smb://computer name/
```
Alternatively, if you wish to use the IP address, type the following:
```
smb://IP address/  
```
When I try that ist says:

[B]Error: Failed to retrieve share list from server
Please select another viewer and try again.[/B]

It is the same with every file manager, and it is the same when I click on windows network with my mouse.

---

### Post by mickie.kext on 2009-04-12
> **romuald_geo said:**
> what radio buttons are you talking about?

When click on this icon in upper corner, there are nethernet controlers and radio buton in front ich one. I cant picture actual controler (and butons) because stupid print scren wont work when that computer icon is clicked.

---

### Post by mickie.kext on 2009-04-12
Does anybody have some idea?

---

### Post by romuald_geo on 2009-04-12
To make your computer automataically connect to your network right clik on computers icon and go to "Edit Connections" then setup up to automatically connect to the network you want.Concerning shared files perhaps it's not something proprely configured under Windows. Read this article [http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/](http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/) and here [http://ubuntuforums.org/showthread.php?t=1082148&highlight=Error%3A+Failed+retrieve+share+list+server](http://ubuntuforums.org/showthread.php?t=1082148&highlight=Error%3A+Failed+retrieve+share+list+server)

---

### Post by mickie.kext on 2009-04-12
> **romuald_geo said:**
> To make your computer automataically connect to your network right clik on computers icon and go to "Edit Connections" then setup up to automatically connect to the network you want.Concerning shared files perhaps it's not something proprely configured under Windows.

I alredy tried that, and every time computer is restarted, conection is gone. If it is any conection, since popups says I am conected, but can't see any files...

---

### Post by romuald_geo on 2009-04-12
Sorry but I can't suggest anything else but to search forums with similliar issues

---

### Post by DenysT on 2009-04-13
I was having the same problem and was about to give up but as a last resort I decided that the error was not in either Windows XP or Ubuntu as too many other users were able to do what I was not able to do. Therefore I checked the only place left to check - the router. Lo and behold there was an entry on the LAN setup page that assigned my network name to be the domain name and Ubuntu was scanning the router domain for name resolution and failing. I simply cleared the setting in the router LAN page and everything has worked the way others said it would. Now I have a Belkin router/gateway combo so I can't for sure if your setup could be causing this but it's worth a look see.

---

### Post by mickie.kext on 2009-04-16
I was not entering Ubuntu for couple of days, hoping for the problem to go away, but no :icon_frown:

@romuald_geo
Unfortunately I have not had any luck finding someone with exact problem...

@DenysT
Thanks for reply, but I dont use ruter to conect to local network. Only crossover cable. Ruter is for ADSL only and is conected via separate ethernet port. I have two marvell Yukons integrated in Asus P5Q-E mobo.

Ruter is Huwai HG520s 

I can't find anything in router setup... but jou given me an idea... I will try to connect both computers on ruter, but I am not sure that this ruter supports Gigabit connection.

---

### Post by DenysT on 2009-04-16
> **mickie.kext said:**
> I was not entering Ubuntu for couple of days, hoping for the problem to go away, but no :icon_frown:

@romuald_geo
Unfortunately I have not had any luck finding someone with exact problem...

@DenysT
Thanks for reply, but I dont use ruter to conect to local network. Only crossover cable. Ruter is for ADSL only and is conected via separate ethernet port. I have two marvell Yukons integrated in Asus P5Q-E mobo.

Ruter is Huwai HG520s 

I can't find anything in router setup... but jou given me an idea... I will try to connect both computers on ruter, but I am not sure that this ruter supports Gigabit connection.

You many need to go to Control Panel -> Add Remove/Programs -> Add/Remove Windows Components. Then go to networking services and enable peer-to-peer networking services since you are only using a crossover cable.

---

### Post by mickie.kext on 2009-04-28
I forgot to say, problem is solved with upgrade to 9.04 ! First with Beta, now Final.

Mandriva and PClinuxOS was very close to taking Ubuntu's place, but Jaunty saved the day. :P

---

### Post by Baneblade on 2010-02-19
Think I have the solution.

I cannot "connect to server" either.
Nautilus is unable to browse the "Windows Network"
Nautilus also cannot seem to connect when i specify the IP.

In a fit of desperation i tried using the hostname instead, and lo and behold.. it worked!

That's great and all, now that we have a work around... but really?

---

### Post by Baneblade on 2010-02-24
Ok, it seems that was just a fluke.

The [real fix is here.]("http://ubuntuforums.org/showthread.php?t=1169149&highlight=config+network+wins")

Specifically "Problem 3".

This has fixed all network share issues for me. Anyone else care to confirm?

---

