---
title: "Problems with battery monitor"
date: 2009-09-06
forum: Desktop Environments
---

### Post by pedro3005 on 2009-09-06
I have a laptop with Ubuntu on it (LXDE as a desktop environment) and the battery monitor doesn't work. During boot it says that it'll skip file check since it's on battery power, thus linux is detecting the battery, but when finished booting, the battery monitor says No Battery Found. I tried ibam via the terminal and it always says the battery is completely full, which is impossible. Any help?

---

### Post by earthpigg on 2009-09-06
hi,

probably silly, but

> IBAM is an advanced battery monitor for laptops, which uses statistical and
adaptive linear methods to provide accurate estimations of minutes of
battery left or of the time needed until full recharge. [B][U]It requires APM, ACPI
or PMU.[/U][/B]

ACPID (Advanced Configuration and Power Interface Daemon) is the "standard" one used by Ubuntu. package name is acpid.

do you have it installed?

it's a daemon, so you may need to either start it manually or restart your system to get it up and running.

you can also use gnome-power-manager in lxde, if you like.

after installing it, you need to comment out the "OnlyShowIn" line of it's .desktop file, as shown:
```

chris@mason-netbook:/etc/xdg/autostart$ cat gnome-power-manager.desktop
[Desktop Entry]
Encoding=UTF-8
Name=Power Manager
Comment=Power management daemon
Icon=gnome-power-manager
Exec=gnome-power-manager
Terminal=false
Type=Application
Categories=
_**#OnlyShowIn=GNOME;XFCE;**_
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-power-manager
X-GNOME-Bugzilla-Component=gnome-power-manager
X-GNOME-Bugzilla-Version=2.24.2
X-GNOME-Bugzilla-ExtraInfoScript=gnome-power-bugreport.sh
X-Ubuntu-Gettext-Domain=gnome-power-manager
chris@mason-netbook:/etc/xdg/autostart$ 
```

---

### Post by pedro3005 on 2009-09-06
Ibuclaw helped me on the IRC channel. Basically, what I did was:
Got his edited good DSDT from [http://www29.zippyshare.com/v/28557715/file.html](http://www29.zippyshare.com/v/28557715/file.html) (also attached if the link goes down)
Installed iasl with ```
sudo apt-get install iasl
```Ran ```
iasl -tc acpi_dsdt-fix.asl
```Then ran ```
sudo cp acpi_dsdt.aml /etc/initramfs-tools/DSDT.aml
```Then I backed up my current working initdr with (remember to change names if your is different) ```
sudo cp initrd.img-2.6.28-15-generic initrd.img-2.6.28-15-generic-safeboot
```Edited /boot/grub/menu.lst adding an entry at end pointing to the safeboot initram copied above.
Ran ```
update-initramfs -u all
```Then I rebooted and everything worked! :D

---

