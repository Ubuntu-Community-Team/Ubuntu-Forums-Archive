---
title: "gnome / kde startup slow ubuntu 19.04"
date: 2019-06-30
forum: Desktop Environments
---

### Post by kmismail on 2019-06-30
Hi , i recently upgraded from ubuntu 18.04 to ubuntu 18.10 and then 19.04. Since the upgrade , the login screen and desktop take long time to load. 

I tired some solution given in threads like reinstalling Nvidia drivers , uncomment waylandEnable= false. I tried using both gnome and kde plasma, have issues in both.

System details:
Acer Aspire 5
intel i5-8250U
Nvidia MX150
8 GB ram

Systemd-analyze time:
startup finished in 3.250s (firmware) + 4.113s (loader) + 7.428s (kernel) + 1min 22.574s (userspace) = 1min 37.367s 
graphical.target reached after 1min 21.376s in userspace

systemd-analyze blame:
28.684s mpd.service
         22.116s systemd-journal-flush.service
         19.206s libvirtd.service
         18.450s winbind.service
         18.409s dev-sda2.device
         17.754s firewalld.service
         17.324s NetworkManager-wait-online.service
         14.060s apache2.service
         13.637s networkd-dispatcher.service
         13.118s udisks2.service
         12.865s accounts-daemon.service
         12.365s ModemManager.service
         11.244s dev-loop1.device
          9.609s snapd.service
          8.427s grub-common.service
          7.505s avahi-daemon.service
          7.428s thermald.service
          7.293s gpu-manager.service
          7.272s dev-loop0.device

I am fairly new to linux and ubuntu , if you need log info for Xorg or anything , please let me know. Thanks for your help.

---

### Post by &amp;wP*!) on 2019-07-03
There is a some general problem on your computer which slows down the take-off of all of your services. Maybe you have a hardware which firmware is not recognized by the system? You can check it with /var/log/syslog to find out whether some firmware update is running continuously, which is causing this slow-down? This NVIDIA might be the problem.

Your grub-common.service takes 9 seconds. My takes 129ms (Lubuntu though).

Tell us How big your harddisk(s) are. What filesystems you use.

Have you changed any thing recently? Cron? File system?

Try a fresh install of Lubuntu (very lightweight Ubuntu) to check out if this  works

---

### Post by CatKiller on 2019-07-03
Those times all look very slow, rather than just being one thing holding up the process. I agree with pencuse; that looks like a systemic misconfiguration of some kind.

---

