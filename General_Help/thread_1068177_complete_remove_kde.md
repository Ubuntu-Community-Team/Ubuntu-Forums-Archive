---
title: "complete remove kde?"
date: 2009-02-12
forum: General Help
---

### Post by firsttimeuser on 2009-02-12
I started my ubuntu journey few months ago with kubuntu 8.0.4, and then upgraded to kubuntu 8.10, last week I tried to install gnome desktop and immediately love it.

Now I want to complete remove all the kde stuff, so is it okay i just fire up a apt-get command as below? (please remember I installed gnome later after the initial kubuntu 8.10) I am not sure if this will be safe.

sudo apt-get remove kde kde-core

---

### Post by Iwanthelp on 2009-02-12
Well you could always just install normal Ubuntu. Just uninstall Kubuntu and you'd be fine. Although you probably wouldn't want to do that... But, hey, reinstall is the easy option on every problem.

---

### Post by perlluver on 2009-02-12
Follow these instructions for a pure Gnome: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by firsttimeuser on 2009-02-12
hehe, the thing is I already installed tons of stuff and fresh installation is really not a good option for me.

> **Iwanthelp said:**
> Well you could always just install normal Ubuntu. Just uninstall Kubuntu and you'd be fine. Although you probably wouldn't want to do that... But, hey, reinstall is the easy option on every problem.

---

### Post by firsttimeuser on 2009-02-12
> **perlluver said:**
> Follow these instructions for a pure Gnome: [http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

"These removal commands were created based on what Kubuntu or Xubuntu packages were added to a default Ubuntu installation."

sounds like I am not suppose to follow the steps since I installed kubuntu first, not ubuntu.....

---

### Post by perlluver on 2009-02-12
It is fine to follow them, make sure you have GDM installed, and that will take you to a Pure Gnome experience.  Since you installed the ubuntu-desktop package, it will keep Ubuntu installed and get rid of KDE.

---

### Post by firsttimeuser on 2009-02-12
man, i think i am screwed!

I was in Gnome and was following the link and bang! i lost my dispaly and my screen goes to console mode (window without gui), from the console messages, it seems that the system is starting a bunch of services such as networkmanager, bluetooth, and there is an error message saying:

"not starting gnome display manager(gdm); it is not the default display manager"

now the screen just stuck at the prompt "setting advanced power management level to 0xfe"

I am afraid to press the power button....

sweating now.....

---

### Post by perlluver on 2009-02-12
You most likely deleted KDM, give it a reboot, and GDM will come up, then you will be able to log back into Gnome.

---

### Post by firsttimeuser on 2009-02-12
ah, after I rebooted the box, the gnome came back....:)

But somehow the network config applet at the upper right of the screen can not detect any network device now, it just shows: no network devices available"


> **perlluver said:**
> You most likely deleted KDM, give it a reboot, and GDM will come up, then you will be able to log back into Gnome.

---

### Post by perlluver on 2009-02-12
Are you able to connect to the internet?  If so than that is the KDE network device.  Is it a green Globe, or two computers?

---

### Post by firsttimeuser on 2009-02-12
i am in gnome now and that icon looks like two round circle.

Anyway I think somehow it lost the configuration and I just reconfiged it, it works now.

One more thing, I still see kubuntu showing up when the system loads

---

### Post by perlluver on 2009-02-12
> **firsttimeuser said:**
> i am in gnome now and that icon looks like two round circle.

Anyway I think somehow it lost the configuration and I just reconfiged it, it works now.

One more thing, I still see kubuntu showing up when the system loads

I believe when you killed KDM, it stopped un-installing the KDE apps, open up a terminal, Applications>Accessories>Terminal, then run ```
sudo apt-get autoremove
``` that should get rid of the rest of the KDE items, and then open up synaptic, System>Administration>Synaptic Package Manager, and make sure the usplash-theme-ubuntu is installed.

---

### Post by firsttimeuser on 2009-02-12
thanks for your help, greatly appreciated!

Doing so now, on the other hand, it seems that that network connection applet does now work correctly, even after I manualy entered the network configuration, the next it reboot it still shows "no network devices available"

---

### Post by perlluver on 2009-02-12
Did you grab all the packages when you installed ubuntu-desktop?  And if the internet is working in Gnome, the two monitors, will let you know you are connected, if it is a globe, then that is the KDE network manager.  Go to System>Preferences>Sessions, and make sure the the KDE network manger is removed so it won't start up on boot.

---

### Post by firsttimeuser on 2009-02-12
holy cow, the evil kde netowkr manager still shows up in the sessions list. What should I do next?

and i still see the kubuntu graphic when I reboot the laptop, scratching my head now...

> **perlluver said:**
> Did you grab all the packages when you installed ubuntu-desktop?  And if the internet is working in Gnome, the two monitors, will let you know you are connected, if it is a globe, then that is the KDE network manager.  Go to System>Preferences>Sessions, and make sure the the KDE network manger is removed so it won't start up on boot.

---

### Post by perlluver on 2009-02-12
Just delete it from the sessions list, as for the Kubuntu logo, that thing is tough to get rid of sometimes.  Type in the terminal, ```
sudo apt-get install ubuntu-desktop
``` and see if it installs anything else.

---

### Post by firsttimeuser on 2009-02-12
nope, nothing new to be installed. 

@noname:~$ sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by perlluver on 2009-02-12
I am kinda at a loss for changing the usplash, you could install start-up manager, it can be found in Synaptic, and then change it to the Ubuntu usplash.

---

### Post by firsttimeuser on 2009-02-12
big thanks man, I will figure these out later. a matter of time.

Seems this forum disabled the "thanks" option. 

thanks again.

---

### Post by perlluver on 2009-02-12
No problem man, enjoy Gnome.

---

