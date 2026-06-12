---
title: "upgrading to firefox 3.x.x"
date: 2009-01-31
forum: Desktop Environments
---

### Post by prezbedard on 2009-01-31
I'm running 7.10 with the latest updates.

in a terminal I ran 

```
sudo aptitude install firefox-3.0
```

```
sudo aptitude install firefox-3.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  xulrunner-1.9 
The following NEW packages will be installed:
  firefox-3.0 xulrunner-1.9 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 11.0MB of archives. After unpacking 32.0MB will be used.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
Get:1 http://archive.ubuntu.com gutsy/universe xulrunner-1.9 1.9~a8-0ubuntu2 [9846kB]
Get:2 http://archive.ubuntu.com gutsy/universe firefox-3.0 3.0~alpha8+nobinonly-0ubuntu1 [1158kB]
Fetched 11.0MB in 1m31s (120kB/s)                                               
Selecting previously deselected package xulrunner-1.9.
(Reading database ... 139587 files and directories currently installed.)
Unpacking xulrunner-1.9 (from .../xulrunner-1.9_1.9~a8-0ubuntu2_i386.deb) ...
Selecting previously deselected package firefox-3.0.
Unpacking firefox-3.0 (from .../firefox-3.0_3.0~alpha8+nobinonly-0ubuntu1_i386.deb) ...
Setting up xulrunner-1.9 (1.9~a8-0ubuntu2) ...

Setting up firefox-3.0 (3.0~alpha8+nobinonly-0ubuntu1) ...
Please restart all running instances of Firefox-3.0, or you will experience problems.

Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             

```

everything seems to of completed without issue however firefox is still launching as version 2.0.0.19

---

### Post by prezbedard on 2009-01-31
ok I just noticed the info icon up where the update manager displays info stating that a firefox upgrade took place and to restart all instances of firefox. I did that and still nothing even tried a reboot.

---

### Post by vegetarianshrimp on 2009-01-31
Maybe try this?:

right click on the main menu, click Edit Menus. Go to the Internet tab. There might be (I'm guessing here) two Firefox Web Browser icons. Uncheck the one that is checked and check the one the isn't

Hope that helps! Again, I have never installed firefox 3 on Ubuntu 7.10, so I don't know. Complete guess.

---

### Post by prezbedard on 2009-01-31
nope there is only one firefox icon and it lauches to the same firefox as the icon in the top horizontal menu. I'll check where the program is actually install if I can find it still not 100% sure on the wy linix does these things...

Thanks though...

---

### Post by prezbedard on 2009-01-31
ok found

```
/etc/firefox-3.0
```

under it though there are folders titled  profile,pref, and a file called firefoxrc but no executable. No hidden files/folders either.

---

### Post by prezbedard on 2009-01-31
ok now found 

```
/usr/lib/firefox-3.0
```

seems to have all required files etc. I tried opening the executable but for some reason its trying to open in gedit. I then ran a file called run-mozilla.sh then tried the firefox executable again. It opened what appears to be firefox 3 but is calling it "Gran Paradiso 3.0a8" which I guess is the code name and alpha version of firefox 3 for Ubuntu?

---

### Post by prezbedard on 2009-01-31
ok so just decided to do it like I would on windoze. I went to getfirefox.com, downloaded the archive, and extracted it. It extracted all files to a folder called firefox on the desktop. I ran a scropt file in the dir called firefox and bingo got firefox 3.0.5. All shortcuts open 3. Now can I move this firefox from my desktop to a more appropreate program dir and have it still work properly? Where hsould I move it? I'm guessing 

```
/usr/lib
```

which seems to contain most of the programs executable of programs installed in Ubuntu.

---

### Post by prezbedard on 2009-01-31
correction the shortcuts only open 3.0.5 if firefox 3.0.5 is already running. They otherwise still launch the old version. What can I do to correct this without screwing things up?

Thanks!

---

