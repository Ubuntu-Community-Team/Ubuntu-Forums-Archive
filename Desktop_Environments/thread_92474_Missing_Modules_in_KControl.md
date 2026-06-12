---
title: "Missing Modules in KControl"
date: 2005-11-19
forum: Desktop Environments
---

### Post by C_nemo on 2005-11-19
Hi.
After installing the kubuntu-desktop package i had almost all of the modules in kcontrol and systemsettings dissapear on me. Althoug they were gone with only the bare minimum for kcontrol and amarok installed as well. I figured that the kubuntu-desktop package should pull inn anything missing. I just got myself a new disk and was curious of how KDE had progressed.
I can no longer set my application style, fonts or colors, to name a few. I hav tried reinstalling, deleting the .kde dir to no avail. Deleting the old .kde dir  just left me with unbearable large fonts

"kcmshell --llist" gives the folowing:
```

kcmgtk-xdg      - Control the style and fonts used by GTK applications
ksplashthememgr - Manager for Splash Screen Themes
kwindecoration  - Configure the look and feel of window titles
kwinoptions     - Configure the window behavior
kwinrules       - Configure settings specifically for a window
kcm_kbluetoothd - Manage Bluetooth Services offered to others.
kcmkrfb         - Configure Desktop Sharing
fileshare       - Enable or disable file sharing
kcm_btpaired    - Manage paired Bluetooth devices
kcmsambaconf    - KcmSambaConf - a KControl module for configuring a samba server
kcmwifi         - Set up your wireless LAN
kcmvim          - Configuration of the vim editor component
kamera          - Configure Kamera
obex            - OBEX device configuration tool
printers        - Printing system configuration (printers, jobs, classes, ...)
laptop          - Laptop Battery
kwalletconfig   - KDE Wallet Configuration
kcm_useraccount - User information such as password, name and email
audiocd         - Audiocd IO Slave Configuration
mountconfig     - Disk & Filesystem Configuration
thinkpad        - Configure the KDE Interface to the IBM Thinkpad Special Controls
kvaio           - Configure the KDE Interface to the Sony Programmable Interrupt Controller Driver
serviceconfig   - System Service Configuration
userconfig      - Users & Groups Administration

```

I have no idea whats going on. If i start "kcmshell style" it only gives me a mostly blank window. 
Help! anyone? bueler?


[EDIT]
now I have removed and reinstalled all the kde packages, and I now have lost all the modules in kcontrol

---

### Post by C_nemo on 2005-11-27
Replying to myself, but I found the cause of my problems.

The .local directory created for managing the sytem menus. I had removed a lot of KDE programs from my gnome menu that way. And in an effort to remove som java settings entries unmarked large parts of the "Settings-Module" group. It seems that kcmshell/kcontrol/systemsetting also honours these settings. Net reult: Almost no modules to configure in said programs. 

I dont know if it should count as a bug since invocating "kcmshell style" never gave any errors, but just displayed a empty kcontrol window. However, I have solved my own little mystery and posting this so that anyone with similar problems can find it via search. It was a hard "problem" to track down.

---

### Post by johann_p on 2008-03-08
I have the same problem -- I have no modules in kcontrol. But I don't understand the solution: what has to be done to get them back ? :confused:

---

### Post by robrosenbaum on 2008-05-07
I am having this problem as well, and have been Googling for hours trying to resolve this problem. If anyone knows anything about how kcmshell finds modules or decides they don't exist, could you post it?

---

### Post by caljohnsmith on 2008-05-15
If you have no modules showing up at all in kcontrol (or maybe just the "network" module), then you may have the problem I had. I had to spend alot of time tracking it down too, but for me it boiled down to this: there should be a "kde-essential.menu" file in BOTH /etc/xdg/menus/kde-applications-merged directory and also the /etc/xdg/menus/applications-merged/ directory. For some people the file all ready existed in their applications-merged directory, but for me, it was in my kde-applications-merged directory but not the applications-merged directory. So, bottom line is, to fix the problem, all I had to do was:

sudo ln -s /etc/xdg/menus/kde-applications-merged/kde-essential.menu /etc/xdg/menus/applications-merged/.

Voila! Modules show up in kcontrol now. Hope this helps, but if it doesn't, here's a solution that involves uninstalling/reinstalling some packages:
[https://bugs.launchpad.net/ubuntu/+source/kde-systemsettings/+bug/114286](https://bugs.launchpad.net/ubuntu/+source/kde-systemsettings/+bug/114286)

---

### Post by johann_p on 2008-05-15
> **caljohnsmith said:**
> If you have no modules showing up at all in kcontrol (or maybe just the "network" module), then you may have the problem I had. I had to spend alot of time tracking it down too, but for me it boiled down to this: there should be a "kde-essential.menu" file in BOTH /etc/xdg/menus/kde-applications-merged directory and also the /etc/xdg/menus/applications-merged/ directory. For some people the file all ready existed in their applications-merged directory, but for me, it was in my kde-applications-merged directory but not the applications-merged directory. So, bottom line is, to fix the problem, all I had to do was:

sudo ln -s /etc/xdg/menus/kde-applications-merged/kde-essential.menu /etc/xdg/menus/applications-merged/.

Voila! Modules show up in kcontrol now. Hope this helps, but if it doesn't, here's a solution that involves uninstalling/reinstalling some packages:
[https://bugs.launchpad.net/ubuntu/+source/kde-systemsettings/+bug/114286](https://bugs.launchpad.net/ubuntu/+source/kde-systemsettings/+bug/114286)

Hmm, I do not have a kde-essential.menu file anywhere on my file system ... ?!?!?
Which package is supposed to provide this file?

---

### Post by johann_p on 2008-05-15
On my system, the directory /etc/xdg/menus/applications-merged links to /etc/xdg/menus/kde-applications-merged and contains these files:
system-settings-merge.menu and wine.menu

Complete removal of kde-related packages and reinstalling them did not make the file kde-essential.menu appear anywhere.

So I browsed my old backups of a prior version of Ubuntu and found a file with that name: 

OK, I browsed through my old backups and found a version of kde-essential.menu.

I copied this old file into /etc/xdg/menus/applications-merged and voila! I have my KControl modules back!

Here is the content of my kde-essential.menu file if you want to try this or compare it to your (maybe newer) version:
```

 <!DOCTYPE Menu PUBLIC "-//freedesktop//DTD Menu 1.0//EN"
  "http://www.freedesktop.org/standards/menu-spec/1.0/menu.dtd">

<Menu>
        <!-- The following menus are hidden by default -->
        <Menu>
                <Name>Settings</Name>
                <Directory>kde-settings.directory</Directory>
                <MergeFile>../kde-settings.menu</MergeFile>
        </Menu>
        <Menu>
                <Name>Information</Name>
                <Directory>kde-information.directory</Directory>
                <MergeFile>../kde-information.menu</MergeFile>
        </Menu>
        <Move>
           <Old>Settings/Information</Old><New>Information</New>
        </Move>
        <Menu>
                <Name>System</Name>
                <Menu>
                        <Name>ScreenSavers</Name>
                        <Directory>kde-system-screensavers.directory</Directory>
                        <MergeFile>../kde-screensavers.menu</MergeFile>
                </Menu>
        </Menu>
</Menu>

```

---

