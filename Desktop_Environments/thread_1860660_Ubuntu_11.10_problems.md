---
title: "Ubuntu 11.10 problems"
date: 2011-10-15
forum: Desktop Environments
---

### Post by pandeylavakesh on 2011-10-15
hey there .. 

Yesterday .. I performed a clean installation of Ocelot. After that I installed some of restricted extras and Synaptic Package Manager. But when I installed Oxford Advanced Learner's Dictionary 8th Edition it did not create any desktop shortcut unlike the previous version where I used to get a shortcut. I installed it in /root/oald8 directory. 
Though I have not a shortcut but I can still run it from the /root/oald8 directory. When I launch oald8 it doesn't give any sound and throws following error.

(oald8-bin:7521): GTK warning **: Unable to locate theme engine in module path: "pixmap"
(oald8-bin:7521): GTK warning **: Unable to locate theme engine in module path: "pixmap"
(oald8-bin:7521): GTK warning **: Unable to locate theme engine in module path: "pixmap"

**PS: In case there is no solution to this Oxford installation  problem how can I completely REMOVE it from my system?? **

Second Problem after installing Oneiric Ocelot:
Secondly, I think my Ubuntu Software Center is not working. Whenever I try to install anything from USC , the INSTALL button on the right doesn't appear bold(doesn't get redeemed) kind of like its dead or not working.

---

### Post by garvinrick4 on 2011-10-15
> Second Problem after installing Oneiric Ocelot:
Secondly, I think my Ubuntu Software Center is not working. Whenever I  try to install anything from USC , the INSTALL button on the right  doesn't appear bold(doesn't get redeemed) kind of like its dead or not  working. 	   	  	     		 	       	 		   

```
sudo apt-get install --reinstall software-center
```

---

### Post by pandeylavakesh on 2011-10-15
> **garvinrick4 said:**
> ```
sudo apt-get install --reinstall software-center
```

thanks for the reply. 
But still the same problem. I can't install anything from Software Center.

---

### Post by garvinrick4 on 2011-10-15
Do you get an error when you try to install something from command line.
Maybe, let me know, try to install anything.
```
sudo apt-get install aptitude
```
Does it work or give an error.

---

### Post by pandeylavakesh on 2011-10-15
> **garvinrick4 said:**
> Do you get an error when you try to install something from command line.
Maybe, let me know, try to install anything.
```
sudo apt-get install aptitude
```
Does it work or give an error.

no it does not give any error. By the time they fix it I'm installing everything from command line. e.g GIMP, pinta, vlc, chrome etc.
tell me one thing .. is it a problem for me or everyone is facing the same problem?? 

They promised to give us a new world of computing but I can still face the same problems that were in Natty 11.04. Even there is no exit option for Banshee Media Player. Once started it is always running. The only way to exit Banshee is to Shut Down ur system. Darn !

---

### Post by pandeylavakesh on 2011-10-15
hello friends 
does anyone have the same problem like me i.e. Ubuntu Software Center not working. I am not a[SIZE=1]ble to install anything from Software Center. The install button on right hand side is not visible that is it doesn't become Bold or Clickable when I want to install something from it.[/SIZE]

---

### Post by dcraddock on 2011-10-15
I did the upgrade and everything was workingfine. This morning I have  no Software Center. When I click the icon I get a blank window. I tried a reinstall but it has made no difference. I no longer can access the Software Center.

---

### Post by ckrishna on 2011-10-16
Same problem here too. I cannot install anything from software center, but commandline works fine. Also if I open software center from command line ( gksudo software-center ) , it works fine
> **pandeylavakesh said:**
>  Even there is no exit option for Banshee Media Player. Once started it is always running. The only way to exit Banshee is to Shut Down ur system. Darn !
Pause banshee player and then close it.

---

### Post by CalvinK on 2011-10-16
> **garvinrick4 said:**
> ```
sudo apt-get install --reinstall software-center
```

Same problem : Synaptic doesn't work on my machine, Toshiba Satellite A400. However, Software center is just fine. 
Others problems : the icons appear erratically in the launcher. And there is non icon to shut down except in the menu Applications -> System
Some problem also to install a network printer.
No classical menu ...
I think that I'm going to reinstall the previous version:confused: 
CalvinK

---

### Post by tphuocthai on 2011-10-16
Same problem to me. I ran software-center from terminal then click install button for any software I get this error:

```
2011-10-16 22:47:00,047 - softwarecenter.ui.gtk3.em - INFO - EM's: 15 12 17
2011-10-16 22:47:00,692 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2011-10-16 22:47:00,763 - softwarecenter.ui.gtk3.utils - INFO - Softwarecenter style provider for radiance Gtk theme: /usr/share/software-center/ui/gtk3/css/softwarecenter.css
2011-10-16 22:47:14,042 - softwarecenter.backend - WARNING - _on_trans_error: org.freedesktop.PolicyKit.Error.Failed: ('system-bus-name', {'name':  ':1.101'}): org.debian.apt.install-or-remove-packages

```

---

### Post by mynameissagarbhatt on 2011-10-22
> **ckrishna said:**
> Same problem here too. I cannot install anything from software center, but commandline works fine. Also if I open software center from command line ( gksudo software-center ) , it works fine

Pause banshee player and then close it.


yes it works this way

---

### Post by chuck5463 on 2011-10-22
opened software center with command line and it works fine::)

---

