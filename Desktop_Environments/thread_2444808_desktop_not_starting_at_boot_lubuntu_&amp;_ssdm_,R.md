---
title: "desktop not starting at boot :lubuntu &amp; ssdm ,RPi3B SBC"
date: 2020-06-04
forum: Desktop Environments
---

### Post by richard-g8jvm2 on 2020-06-04
recently installed Ubuntu20.04LTS server + Lubuntu-desktop on one of those horrible little raspberyPi SBCs
lubutu-desktop not starting at boot
 

I've played with the DMs
GDM3 puts such a load on the RPI3B that on the CLI you can type a sentence and it takes 1 minute to appear
lightdm forces a gnome desktop which is slow, could be MATE
 after a manual startx
systemctl status display_manager shows
```

ubuntu@ubuntu:~$ systemctl status display-manager
&#9679; sddm.service - Simple Desktop Display Manager
     Loaded: loaded (/lib/systemd/system/sddm.service; enabled; vendor preset: enabled)
     Active: active (running) since Thu 2020-06-04 17:32:11 UTC; 6min ago
       Docs: man:sddm(1)
             man:sddm.conf(5)
    Process: 1488 ExecStartPre=/bin/sh -c [ "$(cat /etc/X11/default-display-manager 2>/dev/null)" = "/usr/bin/sddm" ] (code=exited, status=0/SUCCESS)
   Main PID: 1491 (sddm)
      Tasks: 2 (limit: 966)
     CGroup: /system.slice/sddm.service
             &#9492;&#9472;1491 /usr/bin/sddm


Jun 04 17:32:11 ubuntu systemd[1]: Starting Simple Desktop Display Manager...
Jun 04 17:32:11 ubuntu systemd[1]: Started Simple Desktop Display Manager.
Jun 04 17:32:11 ubuntu sddm[1491]: Initializing...
Jun 04 17:32:11 ubuntu sddm[1491]: Starting...
Jun 04 17:32:11 ubuntu sddm[1491]: Logind interface found



```

It also shows exactly the same after reboot with no display, just CLI
dmesg shows nothing of SSDM starting, nor does syslog or journalctl
I'm only using the desktop as a test bed so its not an ordeal to
ALT F2 , to get a login, login and then type startx
I'd like to get it working as intended , without resorting to putting "startx" in rc.local, if that would still work
any ideas, apart from putting in an oven at high temperature :)
TIA

---

### Post by guiverc on 2020-06-09
Also asked on [https://discourse.lubuntu.me/t/lubuntu-desktop-fail-on-20-04-on-a-horrible-raspberry-pi-3b/](https://discourse.lubuntu.me/t/lubuntu-desktop-fail-on-20-04-on-a-horrible-raspberry-pi-3b/)

(When I get a flash card I'll do some testing of Lubuntu 20.04 (& desktopify) on the pi, but with lockdown I don't know when that will be...)

---

