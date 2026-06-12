---
title: "Transmission-Daemon &amp; Permission denied"
date: 2011-07-01
forum: Desktop Environments
---

### Post by Zitan on 2011-07-01
My settings.json looks like this:

```

{
    "alt-speed-down": 300, 
    "alt-speed-enabled": true, 
    "alt-speed-time-begin": 435, 
    "alt-speed-time-day": 62, 
    "alt-speed-time-enabled": true, 
    "alt-speed-time-end": 915, 
    "alt-speed-up": 1, 
    "bind-address-ipv4": "0.0.0.0", 
    "bind-address-ipv6": "::", 
    "blocklist-date": 1254838899, 
    "blocklist-enabled": false, 
    "blocklist-updates-enabled": 1, 
    "dht-enabled": true, 
    "download-dir": "/var/lib/transmission-daemon/info/Downloads", 
    "download-limit": 100, 
    "download-limit-enabled": 0, 
    "encryption": 2, 
    "incomplete-dir": "/var/lib/transmission-daemon/info/Downloads", 
    "incomplete-dir-enabled": false, 
    "inhibit-desktop-hibernation": 0, 
    "lazy-bitfield-enabled": true, 
    "lpd-enabled": false, 
    "main-window-height": 500, 
    "main-window-layout-order": "menu,toolbar,filter,list,statusbar", 
    "main-window-width": 447, 
    "main-window-x": 221, 
    "main-window-y": 138, 
    "message-level": 2, 
    "minimal-view": 0, 
    "open-dialog-dir": "/home/torrent/seeding", 
    "open-file-limit": 32, 
    "peer-limit-global": 240, 
    "peer-limit-per-torrent": 60, 
    "peer-port": 51413, 
    "peer-port-random-enabled": 0, 
    "peer-port-random-high": 65535, 
    "peer-port-random-low": 1024, 
    "peer-port-random-on-start": false, 
    "peer-socket-tos": 0, 
    "pex-enabled": true, 
    "port-forwarding-enabled": true, 
    "preallocation": 1, 
    "prompt-before-exit": 1, 
    "proxy": "", 
    "proxy-auth-enabled": false, 
    "proxy-auth-password": "", 
    "proxy-auth-username": "", 
    "proxy-enabled": false, 
    "proxy-port": 80, 
    "proxy-type": 0, 
    "ratio-limit": 2.0000, 
    "ratio-limit-enabled": false, 
    "recent-announce-url-0-announce": "http://9.rarbg.com:2710/announce", 
    "recent-announce-url-0-tier": 0, 
    "recent-announce-url-1-announce": "", 
    "recent-announce-url-1-tier": 0, 
    "recent-announce-url-2-announce": "", 
    "recent-announce-url-2-tier": 0, 
    "recent-announce-url-count": 1, 
    "recent-download-dir-1": "/root/torrent", 
    "rename-partial-files": true, 
    "rpc-authentication-required": false, 
    "rpc-bind-address": "0.0.0.0", 
    "rpc-enabled": true, 
    "rpc-password": "{3497e6f97be37b610e4ad7d4c6901e84a202a0edAxCpHJkd", 
    "rpc-port": 9091, 
    "rpc-username": "root", 
    "rpc-whitelist": "127.0.0.*,192.168.16.5,192.168.16.12", 
    "rpc-whitelist-enabled": false, 
    "sched-begin": 1380, 
    "sched-download-limit": 200, 
    "sched-end": 420, 
    "sched-limit-enabled": 0, 
    "sched-upload-limit": 100, 
    "script-torrent-done-enabled": false, 
    "script-torrent-done-filename": "", 
    "show-desktop-notification": 1, 
    "show-filterbar": 1, 
    "show-notification-area-icon": 0, 
    "show-options-window": 1, 
    "show-statusbar": 1, 
    "show-toolbar": 1, 
    "sort-mode": "sort-by-name", 
    "sort-reversed": 0, 
    "speed-limit-down": 100, 
    "speed-limit-down-enabled": false, 
    "speed-limit-up": 100, 
    "speed-limit-up-enabled": false, 
    "start-added-torrents": true, 
    "statusbar-stats": "total-ratio", 
    "trash-original-torrent-files": false, 
    "umask": 0, 
    "upload-limit": 100, 
    "upload-limit-enabled": 0, 
    "upload-slots-per-torrent": 14, 
    "watch-dir": "/root/Desktop", 
    "watch-dir-enabled": 0
}

```

I added the root user to the group debian-transmission

```
usermod -a -G debian-transmission root
```

Then I changed the permissions for the directory

```

chown -R debian-transmission:debian-transmission /var/lib/transmission-daemon/info/Downloads/
chmod 770 -R /var/lib/transmission-daemon/info/Downloads/

```

I can't save files in "download-dear"... why?

---

### Post by oguhhhacker on 2012-01-13
> I encountered difficulties with file permissions when I had Transmission save downloads within the /var/lib/transmission-daemon/. Therefore, I changed Transmissions setting to download to a folder within my home directory. To ensure that both I and the debian-transmission user had read/write permissions, I added my account to the debian-transmission group (which is created when you install transmission), and I changed the group ownership of my torrent download directory to debian-transmission. Doing so grants the debian-transmission group read/write access to that folder, preserves read/write/execute access for my account, and prevents access to all others.

$ sudo usermod -a -G debian-transmission mjdescy
$ chgrp debian-transmission ~/dl/torrent
$ chmod 770 ~/dl/torrent

I also changed the “umask” setting from the default of 18 to 2. That means transmission-daemon will create files with read/write permissions set at both the user and group level.

- [http://1000umbrellas.com/2010/04/21/transmission-install-on-ubuntu-10-04-server-lucid](http://1000umbrellas.com/2010/04/21/transmission-install-on-ubuntu-10-04-server-lucid)

---

