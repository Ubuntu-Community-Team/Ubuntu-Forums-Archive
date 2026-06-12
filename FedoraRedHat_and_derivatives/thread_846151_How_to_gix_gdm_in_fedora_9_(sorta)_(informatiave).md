---
title: "How to gix gdm in fedora 9 (sorta) (informatiave)"
date: 2008-07-01
forum: Fedora/RedHat and derivatives
---

### Post by shawnansasio on 2008-07-01
Are you a new fedora9 user and you want gdm themes.
Well you're in luck!!
here's how to do it:

step 1. Download these rpms: [ftp://rpmfind.net/linux/fedora/updates/8/i386/gdm-2.20.5-3.fc8.i386.rpm](ftp://rpmfind.net/linux/fedora/updates/8/i386/gdm-2.20.5-3.fc8.i386.rpm) , [http://shawnrocks.2d.googlepages.com/fedorainfinity-gdm-theme-8.0.1-1.fc8.rpm](http://shawnrocks.2d.googlepages.com/fedorainfinity-gdm-theme-8.0.1-1.fc8.rpm)

step 2. type sudo yum remove gdm


step 3.go to the folder where the files are (/home/myusername/Download by default) in Terminal.
Now listen carefully YOU CAN NOT CLICK ON THEM.
type: rpm -ivh --nodeps  fedorainfinity-gdm-theme-8.0.1-1.fc8.rpm
Then : rpm -ivh gdm-2.20.5-3.fc8.i386.rpm
(As root or sudo)


Now reboot.

you will boot in to gdm!!

to get themes to work type:
sudo gdmsetup!!

Have fun installing Themes.

_______________________

I am a 9 year old linux MASTER!!!

---

### Post by RebounD11 on 2008-07-04
> **shawnansasio said:**
> Are you a new fedora9 user and you want gdm themes.
Well you're in luck!!
here's how to do it:

step 1. Download these rpms: [ftp://rpmfind.net/linux/fedora/updates/8/i386/gdm-2.20.5-3.fc8.i386.rpm](ftp://rpmfind.net/linux/fedora/updates/8/i386/gdm-2.20.5-3.fc8.i386.rpm) , [http://shawnrocks.2d.googlepages.com/fedorainfinity-gdm-theme-8.0.1-1.fc8.rpm](http://shawnrocks.2d.googlepages.com/fedorainfinity-gdm-theme-8.0.1-1.fc8.rpm)

step 2. type sudo yum remove gdm


step 3.go to the folder where the files are (/home/myusername/Download by default) in Terminal.
Now listen carefully YOU CAN NOT CLICK ON THEM.
type: rpm -ivh --nodeps  fedorainfinity-gdm-theme-8.0.1-1.fc8.rpm
Then : rpm -ivh gdm-2.20.5-3.fc8.i386.rpm
(As root or sudo)


Now reboot.

you will boot in to gdm!!

to get themes to work type:
sudo gdmsetup!!

Have fun installing Themes.

_______________________

I am a 9 year old linux MASTER!!!

That's the same kind of workaround  that had to be done before the NVidia drivers supported F9's Xserver: downgrade to F8' version of it (it = Xorg + Xserver). 

You need to point out that this is not recommended and can be dangerous. Besides if you don't lock those version after the first reboot they will be updated back to Fedora 9's GDM (version 2.22 I think not the 2.20 you just installed) so unless you don't plan to fully update your system or if you don't restart X after you've ran the update there's no problem (also no point to it). But if you don't lock the version after downgrading it will be changed back after update + X restart.

---

