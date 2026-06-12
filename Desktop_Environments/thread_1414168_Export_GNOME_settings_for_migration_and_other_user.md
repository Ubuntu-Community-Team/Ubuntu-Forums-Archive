---
title: "Export GNOME settings for migration and other users"
date: 2010-02-23
forum: Desktop Environments
---

### Post by megamaced on 2010-02-23
This has probably been asked before, but I'd like to "export" my GNOME desktop i.e. panels, panel gadgets and settings, desktop settings, nautilus settings etc and be able to import them on a target PC, be it my user account on another machine or for a new user.

Is this possible?

Thanks

---

### Post by dracuella on 2010-02-26
Yes this has been asked before a number of times but there were never any answers given. Can it really be true that nobody has ever attempted and succeeded at this? 

I started reading the GNOME Desktop System Administration Guide but tbh haven't gotten very far as it is quite long (and not how I'd like to spend my afternoon) and none of its topics indicate "READ THIS CHAPTER FOR INFORMATION ON HOW TO EXPORT SETTINGS". Not even the slightest.

I'd like to do a how-to, I really would, but I only recently switched from Windows and still feel very new and green. I've been using it more as a platform for work rather than exploring it's capabilities, I'm afraid.

-drac

---

### Post by Kakers on 2010-02-26
Not sure about exporting, but if you want to create/import a theme of some kind.. at my workplace when we are building a desktop/laptop for a new user we create an administrator account and the run the following:

```

#!/bin/sh

# Download patch
cd /tmp
wget http://www.webaddress/repo/desktoptheme.tar.gz
tar zxvf desktoptheme.tar.gz

# Upgrade and install packages
apt-get update
apt-get install -y --force-yes tango-icon-theme tango-icon-theme-common tango-icon-theme-extras openoffice.org-style-tango smbfs msttcorefonts openssh-server flashplugin-nonfree java-common sun-java6-bin sun-java6-jdk openoffice.org libstdc++5 sun-java6-plugin
apt-get dselect-upgrade -y --force-yes
apt-get autoremove -y --force-yes 

# Setup default desktop preferences
mv /tmp/background.jpg /usr/share/backgrounds/
mv -f /usr/share/icons/Human/scalable/places/start-here.svg /usr/share/icons/Human/scalable/places/start-here.svg.bak
mv -f /usr/share/gnome-background-properties/ubuntu-wallpapers.xml /usr/share/gnome-background-properties/ubuntu-wallpapers.xml.bak
mv -f /tmp/ubuntu-wallpapers.xml /usr/share/gnome-background-properties/
mv -f /tmp/start-here.* /usr/share/icons/Human/scalable/places
mv -f /usr/share/icons/Tango/scalable/places/start-here.svg /usr/share/icons/Tango/scalable/places/start-here.svg.bak
cp /usr/share/icons/Human/scalable/places/start-here.svg /usr/share/icons/Tango/scalable/places/
rm -fR /etc/skel
mv -f /tmp/skel /etc/

# Setup GDM
mv /tmp/custom_login /usr/share/gdm/themes
mv /tmp/gdm.conf-custom /etc/gdm/
chown root:root /etc/gdm/gdm.conf-custom

# Secure GRUB
mv /boot/grub/menu.lst /boot/grub/menu.lst.bak
sed -e "s/#      password --md5 \$1\$gLhU0\/\$aW78kHK1QfV3P2b2znUoe\//       password --md5 \$1\$KCpUs\$sloY1K7CknUpTstI3udPb\//g" -e "s/# lockalternative=false/# lockalternative=true/g" /boot/grub/menu.lst.bak > /boot/grub/menu.lst
update-grub

# Remove All Patches
cd ~/tmp
rm -f desktoptheme.tar.gz

reboot

```The script is for new builds thats why there is updates and download etc, but you have see that it moves files into the share folders. This won't change much for the Administrator account (the user it is run on) but when you create a new account after... and it had to be after this is run, it will have the theme you've set.

This probably doesn't help you much though... :???:

---

### Post by megamaced on 2010-03-01
The only program I have found is Sabayon which launches a virtual desktop which you can customise, and then export to other user accounts. But that doesn't help me as I already have set my GNOME desktop preferences outside of the Sabayon program.

So the worst case scenario is that I just need to "re-do" my desktop settings in Sabayon and use its tool to move those settings back to my user account #-o

You can find more info about Sabayon here:

[http://live.gnome.org/Sabayon/](http://live.gnome.org/Sabayon/)

---

### Post by michalsmid on 2011-09-01
Well, I think it is pretty easy. Just copy the 
.gconf
.gconfd
directories (from the old to the new one installation) in your home directory. I am not sure if they both are necessary, but it works for me.

But be sure to backup the old ones for the case of any trouble.

---

### Post by Francewhoa on 2012-02-21
Same here. There is no easy way to do that yet without manually copying files and directory. A discussion is in progress for a new feature. There is a brainstorm entry for this. You can discuss or vote for your favorite solution at [http://brainstorm.ubuntu.com/idea/105/](http://brainstorm.ubuntu.com/idea/105/)

---

