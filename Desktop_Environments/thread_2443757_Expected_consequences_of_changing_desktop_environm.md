---
title: "Expected consequences of changing desktop environment (Ubuntu 18.04 GNOME)"
date: 2020-05-19
forum: Desktop Environments
---

### Post by keijo-kukka on 2020-05-19
Hi!
I consider myself as a rookie in Linux and have started using Ubuntu 18.04 GNOME as my default OS only few months ago. So far I've hardened my system, configured and customized it a bit and installed over 40 applications. Most of them are well-known FOSS and many are security oriented. IMO none of the installed applications are in any way heavily "graphic hungry" (e.g. no heavy games).

I'm not satisfied with my current default GNOME desktop environment and would  like to change it to KDE Plasma. My question is that, is changing desktop environments "business as usual" in Linux world and if I install KDE  Plasma and switch it as my default desktop environment, then should I expect  any problems with the new desktop environment or should everything go smoothly? Should I expect e.g. any conflicts with installed  applications? How about any configurations I've done? Should I expect any critical errors, e.g related to booting etc.? I'm going to backup my configurations and system files with Timeshift and I don't have any personal files stored (e.g. videos, photos etc.).

My configurations include:

Enabling default disk encryption during installation
Configuring IPvanish VPN
Firefox customization
Enabling Night Light feature
Installing Curl
Tweaking with Gnome Tweaks and Unity Tweak Tool
Installing exFAT support
Setting static IP
Installing Kali VM in Virtualbox
Configuring Wazuh HIDS
Forwarding syslogs to my NSM
Enabling GNOME "minimize" icons feature
Enabling backups with Timeshift

My installed apps are following:

pCloud
KeePass
Veracrypt
Timeshift
GUFW
GParted
GVM (OpenVAS)
Wireshark
Authy
Signal
Brave
Tor browser
Nmap
ClamTk
Lynis
VirtualBox
Testdisk
gWakeOnLan
Pinta
Etcher
Viber
Gnome Tweaks
Unity Tweak Tool
Fast
VokoscreenNG
VLC
Kdenlive
Steam
Avidemux
Stacer
Shutter
Audio Recorder
youtube-dl
Caffeine
my-weather-indicator
TeamViewer
Synaptic
Gdebi (for installing .deb packages and to see their dependencies)
Flatpak
PlayOnLinux

Thanks a lot guys!!

---

### Post by CatKiller on 2020-05-19
> **keijo-kukka said:**
> I'm not satisfied with my current default GNOME desktop environment and would  like to change it to KDE Plasma. My question is that, is changing desktop environments "business as usual" in Linux world and if I install KDE  Plasma and switch it as my default desktop environment, then should I expect  any problems with the new desktop environment or should everything go smoothly?

Gnome and KDE (and Xfce and Cinnamon and...) come with a bunch of applications: display manager, file browser, text editor, media player, PDF reader, and so on. That's pretty much what distinguishes a desktop environment from just a window manager. If you have a desktop environment and then you install a second desktop environment then you'll have two display managers, two file browsers, two text editors, two media players, and so on. Some people find that really annoying, others don't - you can go through each application and say that it shouldn't be shown in one desktop environment or the other to declutter your menus. Other than that, functionally you just pick whichever desktop environment session you'd like to log into from the login screen.

---

### Post by crip720 on 2020-05-19
You will need to wait till someone who did it, can give better info.  Some desktops play very nice together(gnome and unity), others will add extra.  It is usually best if no info to test it out either in a VM or a Live Ubuntu USB stick.  You have VirtualBox so you can even match what you have now and see if everything  works, most programs should but some tweaks might not.

---

### Post by DuckHook on 2020-05-19
Trying to get multiple DEs to coexist is a risky exercise. I can tell you from a long history of personal experience that the results are too often breakages or wonkiness so subtle that they are infuriating. I have found that the time I've wasted trying to track down strange behaviour due to mixed DEs was among the most frustrating of the issues I've dealt with, in part because they are so unnecessary.

The problem is configuration files. All DEs install their own settings and configurations that they assume will not change. The installation of a second DE then monkeys with those settings. If those changes were more obvious, then one could at least pinpoint what the problem is. But many such changes are very obscure and don't bite until you are doing something important.

My standard advice is to keep your base install absolutely dead simple. As close to its default state as possible. Experimenting with fundamental system configurations is best done within a VM, where mistakes can easily be corrected with snapshot rollbacks. 

If looking for more detail on this, please click the link in my sig: "The Best 'buntu Flavour".

---

### Post by grahammechanical on 2020-05-20
What will happen when you decide to remove the additional desktop? From my own experience I would suggest be prepared to reinstall as the least complicated way of putting things right. But you have installed a long list of applications. That was a lot of work. It will have to be down all over again with a reinstall. Run the full flavour in a VM or dual/triple boot. Keep your main install the way you like it. Is my suggestion.

Regards.

---

### Post by DuckHook on 2020-05-20
> **grahammechanical said:**
> …or dual/triple boot. Keep your main install the way you like it. Is my suggestion…
&#8593;+1

---

### Post by keijo-kukka on 2020-05-21
Thank you guys very much for your advises!! O:)O:)  I truly appreciate your opinions and will also try to contribute when I  have something to share. Based on your know-how and long experiences,  I've decided not to change my DE as it seems to be generally speaking  bad idea. Possibly installing Kubuntu in the future might be a better long term option.

---

