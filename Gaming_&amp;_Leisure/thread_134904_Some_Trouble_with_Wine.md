---
title: "Some Trouble with Wine"
date: 2006-02-22
forum: Gaming &amp; Leisure
---

### Post by Tabfugnic on 2006-02-22
I was just wondering if someone could explain to me what this code means when I'm trying to install wine.
```
tabfugnic@TabUbuntu:~$ sudo apt-get build-dep wine
Reading package lists... Done
Building dependency tree... Done
E: Unable to find a source package for wine

```

I do indeed have build-essential installed and such with it telling me that it can no longer be updated anymore.

If i need to give more info let me know.

---

### Post by Sutekh on 2006-02-23
Is there are particular reason you are tying to get wine in this way?

Here's how I'd install wine...

 - Open a terminal window (from the Menu; Applications -> Accesories -> Terminal), and issue the commands
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup 
sudo gedit /etc/apt/sources.list
``` - This will backup your apt-get repository sources list, so you can always change it back, and then allow you to edit the list.

- To install wine you will need the wine repository; add these lines to your sources.list
```

deb http://wine.sourceforge.net/apt/ binary/ 
deb-src http://wine.sourceforge.net/apt/ source/
``` - Then save the file and exit.

 - Update the repositories using
```
sudo apt-get update
```

 - Finally you can install wine using
```
sudo apt-get install wine
```

---

