---
title: "Compiled conky but can not remove compiled version of conky"
date: 2016-10-08
forum: Desktop Environments
---

### Post by dansang on 2016-10-08
Hi i have installed conky 1.10.4 that i have downloaded from github and it does not work as i want it to. it has no cairo or lua binding. how can i uninstall it? There is no way to uninstall using cmake uninstall or anything.  would anyone know a way to uninstall or remove all configuration files for it? even if i   ```
sudo apt-get install conky-all
```   ```
conky -v
```    ```
 conky 1.10.4_pre compiled Sat Oct  8 18:15:40 BST 2016 for Linux 3.16.0-4-686-pae i686  Compiled in features:  System config file: /etc/conky/conky.conf Package library path: /usr/local/lib/conky    General:   * math   * hddtemp   * portmon   * IPv6   * support for IBM/Lenovo notebooks   * builtin default configuration   * old configuration syntax   * apcupsd   * iostats   * ncurses   * Internationalization support  X11:   * Xdamage extension   * Xinerama extension (virtual display)   * Xft   * ARGB visual   * Own window   Music detection:   * MPD   * MOC   Default values:   * Netdevice: eth0   * Local configfile: $HOME/.conkyrc   * Localedir: /usr/local/share/locale   * Maximum netdevices: 64   * Maximum text size: 16384   * Size text buffer: 256 
``` The reason i compiled from source was to install a really flashy conky which i thought would run with the latest conky. The fool i am!! Now i cannot even run a different conky in conky 1.10.0 which comes as standard.  Any help would be greatly appreciated!!

---

### Post by dansang on 2016-10-08
A solution i found as there is no way to 'make uninstall' after the makefile has been created is to uninstall conky-std or conky-all or conky, all of them if you have any one of them installed.  then locate the conky that is installed with  ```
 which conky
```  then delete the conky file at that path, mine being at /usr/local/bin/conky  after that you can reinstall conky and the version that came with your release will be used again.

---

### Post by CantankRus on 2016-10-10
Backports of the latest stable version of conky are available from [**_[COLOR="#B22222"]Vincent Cheng's ppa[/COLOR]_**]("https://launchpad.net/~vincent-c/+archive/ubuntu/conky")
```
**[COLOR="#006400"]glen@Xenial:~$[/COLOR] conky --version**
conky 1.10.5 compiled Wed Oct  5 05:03:17 UTC 2016 for Linux 3.13.0-96-generic x86_64

Compiled in features:

System config file: /etc/conky/conky.conf
Package library path: /usr/lib/conky


 General:
  * math
  * hddtemp
  * portmon
  * IPv6
  * Curl
  * RSS
  * Weather (METAR)
  * Weather (XOAP)
  * wireless
  * support for IBM/Lenovo notebooks
  * nvidia
  * eve-online
  * builtin default configuration
  * old configuration syntax
  * Imlib2
  * apcupsd
  * iostats
  * ncurses
  * Internationalization support

 Lua bindings:
  * Cairo
  * Imlib2
  * RSVG
 X11:
  * Xdamage extension
  * Xinerama extension (virtual display)
  * XDBE (double buffer extension)
  * Xft
  * ARGB visual
  * Own window

 Music detection:
  * Audacious
  * MPD
  * MOC
  * XMMS2

 Default values:
  * Netdevice: eth0
  * Local configfile: $HOME/.conkyrc
  * Localedir: /usr/share/locale
  * Maximum netdevices: 64
  * Maximum text size: 16384
  * Size text buffer: 256
```

To install...
```
sudo add-apt-repository ppa:vincent-c/conky
sudo apt update
sudo apt install conky-all

```

PS: Have a look at [**_[COLOR="#B22222"]checkinstall[/COLOR]_**]("https://help.ubuntu.com/community/CheckInstall") as an alternative to "make install" to easily remove.

---

