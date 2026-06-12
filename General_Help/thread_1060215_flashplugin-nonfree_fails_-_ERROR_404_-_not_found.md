---
title: "flashplugin-nonfree fails - ERROR 404 - not found"
date: 2009-02-04
forum: General Help
---

### Post by Mzwo on 2009-02-04
hi,

when installing flashplugin-nonfree i get the following message:
```

mzwo@Mzwo:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  konqueror-nsplugins libflashsupport ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/18.9kB of archives.
After this operation, 168kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 193261 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2_amd64.deb) ...
Setting up flashplugin-nonfree (10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2) ...
Downloading...
--20:57:37--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 88.221.178.70
Connecting to fpdownload.macromedia.com|88.221.178.70|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
20:57:37 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.

mzwo@Mzwo:~$ 
```


something i'm doing wrong (internet works)? a temporary problem with macromedia? anybody else experiencing this?

thanks,
Mzwo

PS: 8.04 studio 64bit, 2.6.24-23 rt

---

### Post by mickbuntu on 2009-02-04
This is by going to the full Url either someone misspelled the source or Adobe is having  problems (mistyped etc).

[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)


> 

Not Found

The requested URL /get/flashplayer/current/install_flash_player_9_linux.tar.gz was not found on this server.
Apache/2.0.52 (Unix) Server at download.macromedia.com Port 8000





> **Mzwo said:**
> hi,

when installing flashplugin-nonfree i get the following message:
```

mzwo@Mzwo:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  konqueror-nsplugins libflashsupport ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/18.9kB of archives.
After this operation, 168kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 193261 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2_amd64.deb) ...
Setting up flashplugin-nonfree (10.0.1.218+10.0.0.525ubuntu1~hardy1+really9.0.124.0ubuntu2) ...
Downloading...
--20:57:37--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 88.221.178.70
Connecting to fpdownload.macromedia.com|88.221.178.70|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
20:57:37 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.

mzwo@Mzwo:~$ 
```


something i'm doing wrong (internet works)? a temporary problem with macromedia? anybody else experiencing this?

thanks,
Mzwo

PS: 8.04 studio 64bit, 2.6.24-23 rt

---

