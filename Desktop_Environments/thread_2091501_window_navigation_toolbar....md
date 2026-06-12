---
title: "window navigation toolbar...??"
date: 2012-12-05
forum: Desktop Environments
---

### Post by adym3333 on 2012-12-05
I am using ubuntu lucid 10.04 .... my window navigation toolbar is disappeared I don't know how and when but I want window navigation toolbar back as I am using 
Alt + tab to open minimized windows ...... ???
I tried to get avant window manager some coding below ...

import2@import2:~$ sudo apt-get install aw
awardeco                   awk                        awn-applets-python-extras
away                       awl-doc                    awn-manager
awesfx                     awn-applets-c-core         awn-settings
awesome                    awn-applets-c-dbg          aws-status
awesome-extra              awn-applets-c-extras       awstats
awffull                    awn-applets-python-core    
import2@import2:~$ sudo apt-get install awn-
awn-applets-c-core         awn-applets-python-core    awn-settings
awn-applets-c-dbg          awn-applets-python-extras  
awn-applets-c-extras       awn-manager                
import2@import2:~$ sudo apt-get install awn-
awn-applets-c-core         awn-applets-python-core    awn-settings
awn-applets-c-dbg          awn-applets-python-extras  
awn-applets-c-extras       awn-manager                
import2@import2:~$ sudo apt-get install awn-manager 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package awn-manager is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package awn-manager has no installation candidate
import2@import2:~$ 
import2@import2:~$

---

### Post by howefield on 2012-12-05
> **adym3333 said:**
> my window navigation toolbar is disappeared I don't know how and when but I want window navigation toolbar back as I am using Alt + tab to open minimized windows ...... ???

Alt + Tab is good ;-)

What operating system and version are you using ?

---

### Post by adym3333 on 2012-12-05
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.3 LTS
Release:	10.04
Codename:	lucid

---

### Post by howefield on 2012-12-05
To reset the panels to default try the following commands in  a terminal.

```
gconftool-2 --shutdown
```
```
rm -rf ~/.gconf/apps/panel
```
```
pkill gnome-panel
```

You may need to log out / back in.

---

### Post by adym3333 on 2012-12-05
not working ..... coding below ....

import2@import2:~$ gconftool-2 --shutdown
import2@import2:~$ tm ~rf ~/.gconf/apps/panel
The program 'tm' is currently not installed.  You can install it by typing:
sudo apt-get install libtm-perl
import2@import2:~$ rm ~rf ~/.gconf/apps/panel
rm: cannot remove `~rf': No such file or directory
rm: cannot remove `/home/import2/.gconf/apps/panel': Is a directory
import2@import2:~$

---

### Post by howefield on 2012-12-05
It may help to apply the commands as requested.

You have mistyped one of them.

---

### Post by rutafid on 2012-12-05
there is an option in CompizConfig settings manager. its under window management-window decoration. make sure its on, if it is, turn it off then on again. should fix your problem


if you dont have CCSM you can easily get it from terminal, i found it on google in less than 2 min

---

### Post by adym3333 on 2012-12-06
> **howefield said:**
> To reset the panels to default try the following commands in  a terminal.

```
gconftool-2 --shutdown
```
```
rm -rf ~/.gconf/apps/panel
```
```
pkill gnome-panel
```

You may need to log out / back in.

Thnkgod I got my navigation bar back.....

THUMBSUP for howefield ...:guitar:

---

