---
title: "2q's: removing default apps.keyring nagging"
date: 2006-08-22
forum: Desktop Environments
---

### Post by invictus on 2006-08-22
Hi

I have 2 questions I cant figure out.

1)

I want to use AbiWord and Gnumeric instead of openoffice, Epiphany instead of firefox, and just remove a few other applications I dont need that were icluded in the default install. I have installed the extra apps I want, but when I try to remove OpenOffice, Ekiga, etc I get a message saying I need to switch to advanced package manager. Doing that and trying to remove the application says it will also remove ubuntu-desktop. So what should I do to get rid of apps I dont want from default install without removing ubuntu-desktop? I suggest a fix for this issue in the next ubuntu release :)

2)

I have installed network-manager-gnome for wireless+wpa and everything works like a dream. The only problem is a nagging for a keyring everytime I log in to my account. I am not sure if I did anything wrong when installing network-manager-gnome because the passord I have to enter to get rid of the dialog is the WPA passphrase. I would love to NOT get this message, or at least not needing to type the WPA password each time but rather my account password or something. In another thread I found while searching it was suggested that one could do something with gnome-keyring-manager, but I cant find it in the system or in the add/remove software dialog.

Thanks for the help.

---

### Post by mlissner on 2007-02-10
You might do a search for pam keyring. I installed it on two computers. One worked, the other doesn't (yet)...

Not sure why, but I think I wasn't paying as close attention when I installed it on the second one and messed something up. It'll fix the nagging problem I think.

---

### Post by Riverside on 2007-02-10
> **invictus said:**
> I have installed network-manager-gnome for wireless+wpa and everything works like a dream. The only problem is a nagging for a keyring everytime I log in to my account. I am not sure if I did anything wrong when installing network-manager-gnome because the passord I have to enter to get rid of the dialog is the WPA passphrase. I would love to NOT get this message, or at least not needing to type the WPA password each time but rather my account password or something. In another thread I found while searching it was suggested that one could do something with gnome-keyring-manager, but I cant find it in the system or in the add/remove software dialog.You can remove the existing default keyring as follows:

rm .gnome2/keyrings/default.keyring

Next time you log into your account, you will be asked to supply a password for a newly created default keyring, and you can choose the password that you want to use in the future.

You can also I believe (however I am not using my laptop to type this, so this may not be entirely correct) remove nm-applet from Gnome's startup programs so that your wireless network does not automatically start as soon as you login to Gnome (System > Preferences > Sessions > Startup Programs if using the version of Gnome packaged with Dapper).

If you do that, you will then need to run /usr/bin/nm-applet manually each time you want to connect to the wireless network, of course.

---

