---
title: "Wireless questions in Kubuntu"
date: 2005-08-28
forum: Desktop Environments
---

### Post by thieves.honor on 2005-08-28
I have installed Kubuntu without a problem.  Both my nic and wireless card were detected and setup.  The problem is that Kwifi only shows non encrypted networks which is a problem since my network uses wpa.  Any suggestions as to what can be done??

---

### Post by gravestone on 2005-08-29
Open a terminal, and type iwconfig  You may need to type sudo first, depending on how you have modified your system. iwconfig will show you any wireless cards detected, which will show if the card is being picked up. iwlist is another useful tool that shows networks, including cloaked ones. type iwlist --help for options.

If running WEP, it's easy to configure with iwconfig. For WPA, you will need to find the wpa_supplicant wireless stuff and install that.

---

### Post by tonysathre on 2005-08-29
also try dhclient from the terminal

---

### Post by daller on 2005-08-29
Well, is there no way to manage wireless interfaces, without doing commandline?

kwifimanager is great - if it worked!

---

### Post by c0rderr0y on 2005-08-29
try looking into wifi radar theres a howto on here somewhere

---

### Post by thieves.honor on 2005-09-03
To add further to my problem.  I don't have the start on boot box checked on either my nic or wireless card.  when the system comes up, in order to connect my wireless i have to go through kcontrol and enable the connection.  i installed wifi radar, but anytime i try to switch networks it fails to locate ip address and i lose all funcionality of my wireless until i reboot.  any sugestions on how to get the wireless manager to work correctly??

---

### Post by mlomker on 2005-09-03
I know you don't like the command-line, but the easiest tools are from there.

You can look into: wpa_supplicant, ifplugd, and resolvconf.

The combination of those tools, when properly configured, will allow things to 'just work.'  I use kwifimanager just to monitor signal strength in my tray.  The networking applets in Ubuntu are not ready for prime-time and they always get panned for it in distro reviews.

---

