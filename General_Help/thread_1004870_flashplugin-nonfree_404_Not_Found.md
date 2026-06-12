---
title: "flashplugin-nonfree 404 Not Found"
date: 2008-12-07
forum: General Help
---

### Post by zygut on 2008-12-07
I'm running Hardy, up-to-date... but I can't install flashplugin-nonfree because the URL seems to have changed:

Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 207617 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.124.0ubuntu2_i386.deb) ...
Setting up flashplugin-nonfree (9.0.124.0ubuntu2) ...
Downloading...
--17:45:58--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 96.6.34.70
Connecting to fpdownload.macromedia.com|96.6.34.70|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
17:45:58 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.

How do I get this?

---

### Post by taurus on 2008-12-07
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by jvanderb on 2008-12-16
Hello!

I seem to be having the same issue as the original poster:

```
:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/18.7kB of archives.
After this operation, 168kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 96968 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.124.0ubuntu2_i386.deb) ...
Setting up flashplugin-nonfree (9.0.124.0ubuntu2) ...
Downloading...
--22:43:21--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 96.6.226.70
Connecting to fpdownload.macromedia.com|96.6.226.70|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
22:43:22 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.
```

Here is my /etc/apt/sources.list:
```

deb http://archive.ubuntu.com/ubuntu hardy main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu hardy-updates restricted main multiverse universe
```

Is the Ubuntu repository being updated for Flash 10, or is there something else I can do?

Thank you!

---

### Post by PocketDog on 2008-12-16
```
sudo apt-get update
``` should do the trick. Quite a lot of repository locations were out of date (error 404) with a fresh Hardy install I did recently

---

### Post by jvanderb on 2008-12-16
that did not seem to work for me...

I did:
```
sudo apt-get remove flashplugin-nonfree
sudo apt-get clean
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install flashplugin-nonfree
```

and end up getting the same 404 error messsage.  Perhaps my repositories need to be changed, but if so, I'm not sure what to change them to.

---

### Post by eraker on 2008-12-16
This url is wrong:
```
http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
```

Going to [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) gives the current one:
```
http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_**10**_linux.tar.gz
```

You can always just do:
```
 wget http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz
```

And then unpack and install it using the ./install script.

---

### Post by jvanderb on 2008-12-16
Thanks for the suggestion, eraker, I've actually already done that.  The main reason I am trying to figure out how to get it to install properly via apt-get is so I don't have to screw around with a bunch of manual installs of packages, particularly when it comes to updating them.  I prefer to install from the Ubuntu repositories when I can.

Your response is appreciated nonetheless.

Thanks!

---

### Post by eraker on 2008-12-16
I know what you mean. I used to install tons of stuff in /opt/ and ever since I've moved to ubuntu I've tried to get out of the habit because it can be tricky to make sure apt knows what's there.

---

### Post by eraker on 2008-12-16
I just the solution on this offered in the other thread, but I don't know if it works generally:

[http://ubuntuforums.org/showthread.php?t=1010340&page=2](http://ubuntuforums.org/showthread.php?t=1010340&page=2)

---

### Post by darkbluedove on 2008-12-24
> **eraker said:**
> I just the solution on this offered in the other thread, but I don't know if it works generally:

[http://ubuntuforums.org/showthread.php?t=1010340&page=2](http://ubuntuforums.org/showthread.php?t=1010340&page=2)

For fellow Googlers who hit this post first and run Hardy x64 (the solution in the link provided did not work for me in that scenario), I posted another solution to that thread:

[http://ubuntuforums.org/showthread.php?p=6432963#post6432963](http://ubuntuforums.org/showthread.php?p=6432963#post6432963)

---

