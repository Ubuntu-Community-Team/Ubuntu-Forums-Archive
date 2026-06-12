---
title: "upgrade question only, no problem"
date: 2006-01-16
forum: Desktop Environments
---

### Post by bikeman on 2006-01-16
I am relatively new to Ubuntu, and really like it.  Following many of the tips in these forums, I have done a lot of customization -  boot splash screens, custom log-in screen, themes, setting up Pocket PC sync (what a pain, and not entirely complete!), etc.

When Dapper Drake is released, will Breezy automatically be upgraded when I use apt-get update and apt-get upgrade?  If so, what exactly happens to all of my customization?  Please don't tell me it will all be replaced and that I will have to start from scratch.  Thanks.

---

### Post by socrazy143 on 2006-01-16
It isn't quite as easy as apt-get update/upgrade.

You have to make a few changes in the /etc/apt/sources.list file first.  

If you open the file either from command line with gedit /etc/apt/sources.list or from gedit.  Replace everything breezy with dapper.

or

You can open the Synaptic Package Manager and click on Settings -> Repositories and highlight each repository, click edit and change the distribution from breezy to dapper.

After you have done either of these then run apt-get update and apt-get upgrade.

I would highly suggest waiting for the stable release before upgrading if you are new to Ubuntu or Linux in general.

---

### Post by bikeman on 2006-01-16
Actually, I was hoping that apt-get upgrade would *not* upgrade to Dapper!  I would definitely want to wait until it is a final release, and then probably a little after that so that others could write all the How-To's.  :D 

My concern, since I am new at this, is that all of my customization would be lost.  Any ideas if that would be the case?  If so, I might have to actually keep the instructions and any files (themes, screens, images, etc., not application packages) installed.  Thanks.

---

### Post by RAOF on 2006-01-16
[QUOTE=bikeman]Actually, I was hoping that apt-get upgrade would *not* upgrade to Dapper!  I would definitely want to wait until it is a final release, and then probably a little after that so that others could write all the How-To's.  :D 

My concern, since I am new at this, is that all of my customization would be lost.  Any ideas if that would be the case?  If so, I might have to actually keep the instructions and any files (themes, screens, images, etc., not application packages) installed.  Thanks.[/QUOTE]
Upgrading will (generally) keep all of your customisation.  If it's local to your user (ie in /home/username), it shouldn't be touched by an upgrade.  If it's system-wide (ie: in /etc), then the upgrade **may** have a replacement config file in it.  If it does, the upgrade will ask whether you want to replace your modified file with the new one.

---

