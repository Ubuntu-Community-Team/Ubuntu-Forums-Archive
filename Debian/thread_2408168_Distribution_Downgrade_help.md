---
title: "Distribution Downgrade help"
date: 2018-12-14
forum: Debian
---

### Post by le0n564 on 2018-12-14
I used this set of commands to attempt a downgrade from Debian 8 to debian 7.


#revert to SystemV
apt-get install sysvinit sysvinit-core sysvinit-utils
cp /usr/share/sysvinit/inittab /etc/inittab
reboot
apt-get remove --purge --auto-remove systemd


#Set apt-pinning to stick the version at Wheezy
echo -e 'Package: systemdnpin: release o=DebiannPin: release *nPinPriority: -1' > /etc/apt/preferences.d/no-systemd


#set /etc/apt/sources.list to Wheezy only
echo 'deb [http://example.redact/debian](http://example.redact/debian) wheezy main contrib' > /etc/apt/sources.list
echo 'deb [http://example.redact/debian](http://example.redact/debian) wheezy-updates main contrib' >> /etc/apt/sources.list
echo 'deb [http://example.redact/debian-security](http://example.redact/debian-security) wheezy/updates main contrib' >> /etc/apt/sources.list


#add below to /etc/apt/preferences to Apt-pin release level to wheezy
echo 'Package:*' > /etc/apt/preferences
echo 'Pin: release n=wheezy' >> /etc/apt/preferences
echo 'Pin-Priority:1001' >> /etc/apt/preferences


#kill apps
killall -9 bb BBWD.pl rsyslogd




#Run the apt command to pull the Wheezy package and Wheezy Dist
apt-get update
apt-get upgrade
apt-get dist-upgrade
# I had to run apt-get dist-upgrade -f a few times to get it to downgrade
apt-get dist-upgrade -f


#if downgrade fails, they need to be purged
apt-get purge <failing package> 


#reinstall wheezy version after purging
apt-get install <failing package>


I added the failing packages to apt-get purge but every time I got everything added even more dependency issues would crop up. I then decided to zero out /var/lib/dpkg/status with previous settings saved to /var/lib/dpkg/status.old
After this course of action I ran apt-get dist-upgrade and it failed at glibc and then any further input was met with a segmentation fault. Rebooting brought me to kernel panic when Init attempts to start up.
Which unfortunately tells me that the install is borked.


Where did I go wrong? Can I get a run through on the proper downgrade procedure?

---

### Post by howefield on 2018-12-14
Thread moved to the "*Debian*" forum.

---

### Post by Tadaen_Sylvermane on 2018-12-30
The only proper downgrade is a reinstall. Nothing else is supported as far as I know.

---

