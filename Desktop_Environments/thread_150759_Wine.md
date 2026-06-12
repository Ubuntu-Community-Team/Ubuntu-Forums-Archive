---
title: "Wine"
date: 2006-03-26
forum: Desktop Environments
---

### Post by ripgut on 2006-03-26
Can someone help me get this installed and working properly so that i may be able to play games? Prefferably, Half life 2

---

### Post by ripgut on 2006-03-26
Can anyone help?

---

### Post by Sutekh on 2006-03-26
- Open a terminal window (from the Menu; Applications -> Accesories -> Terminal), and issue the commands
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup 
sudo nano /etc/apt/sources.list
``` - This will backup your apt-get repository sources list, so you can always change it back, and then allow you to edit the list.

- To install wine you will need the wine repository; add these lines to your sources.list
```

deb http://wine.sourceforge.net/apt/ binary/ 
deb-src http://wine.sourceforge.net/apt/ source/
``` - Then save the file (Ctrl+O) and exit (Ctrl+X).

 - Update the repositories using
```
sudo apt-get update
```

 - Finally you can install wine using
```
sudo apt-get install wine
```

 - Once wine is installed youshould run **winecfg** to setup options such as sound, extra drives, etc.
```
winecfg
```

 - To install a game use wine in the following manner
```
wine /path/of/program.exe
```

 - For example running the setup.exe program on a CD-ROM
```
wine /media/cdrom0/setup.exe
```


 - As for Half Life 2, you should have a read of the [Wine Application Database](http://appdb.winehq.org/) to see how a games runs with wine and any issues that you may encounter.

 - This is the database entry for Half Life 2
[Wine AppDB - Half Life 2](http://appdb.winehq.org/appview.php?versionId=2890)

 - I'm not sure how successful wine will be in running Half Life 2, but you can certainly give it a shot.

 - There are other options too....

    - Native Linux Games

    - [Cedega](http://www.transgaming.com/products_linux.php)

---

