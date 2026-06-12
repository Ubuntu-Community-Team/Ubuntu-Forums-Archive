---
title: "How to update Flash plugin..??"
date: 2009-05-31
forum: General Help
---

### Post by Thanh-BKK on 2009-05-31
Hello.

I tuned up my computer during the weekend (MoBo, CPU, RAM, DVD burners) and now i seem to have run into a small-ish problem that is annoying.

Firefox is as dog slow as before (!) despite having gone from Athlon XP 3000+ to Athlon 64 X2 5600+. Opera, Netscape and Konqueror FLY compared with Firefox. Still i love Firefox the most :)

However now, when watching a YouTube video, it causes a rather high CPU load of exceeding 40% on both cores. As a comparism i can watch FOUR .avi videos SIMULTANEOUSLY (in different players) and have below 5% on either core!

Now i figured out it must have something to do with the Flash plugin which is version 9.0 r159. Oh, and Opera can't play YouTube videos at all, it says Flash is not installed or outdated (yes, Javascript is enabled). Neither does Netscape. Konqueror plays them fine but with similarly high CPU loads. 

So i got me the latest and greatest in terms of Flash from Adobe, installed it - but Firefox doesn't care, it's version is still the same?!?

So please, van anyone teach me how to hammer the Flash 10.x into my system in such a way that all browsers can and will actually use it..? I would highly appreciate it :)

Many thanks in advance.....

Thanh

PS forgot to mention: Ubuntu Hardy 8.04.2, kernel 2.6.24.24 generic. Nvidia graphics with restricted driver, Compiz enabled.

---

### Post by Yellow Pasque on 2009-05-31
Did you remove the one you had installed before installing a new one?

---

### Post by pogztimz on 2009-05-31
hi. try this at your terminal... 

```
sudo apt-get autoremove flashplugin-nonfree
```
```
sudo apt-get update
```
```
sudo apt-get install flasplugin-nonfree
```

---

### Post by Thanh-BKK on 2009-05-31
Hi :)

@Temujin
No i didn't remove it first, i didn't know that was required - AND i didn't know how to do that :)

@pgztimz
Removing did work, update did work - however installing did NOT. Here's what i get:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package flasplugin-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package flasplugin-nonfree has no installation candidate

I then tried it via Synaptic but that offers only the same old version that i already had (9.x). I then proceeded to re-install the one that i previously downloaded from Adobe and THAT works now, in Firefox at least - it shows (finally!) 10.0 r22. 

However i still can't watch YouTube in Opera and Netscape with both complaining that no Flash is installed.

Oh, and Firefox's CPU loads are now down to about 20% on each core when watching a YouTube video - half of what it was before but still way high compared to watching normal videos.... weird. 

Kind regards.....

Thanh

---

### Post by Thanh-BKK on 2009-05-31
Argh!

Yeah, i know... shouldn't copy-paste stuff into a terminal :) The last command is missing an "h" so no wonder it can't be found.... "flasplugin" vs. "flas**h**plugin" :)

STILL doesn't work:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  libflashsupport ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 18.7kB of archives.
After this operation, 168kB of additional disk space will be used.
Get:1 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hardy/multiverse flashplugin-nonfree 9.0.124.0ubuntu2 [18.7kB]
Fetched 18.7kB in 1s (11.1kB/s)            
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 271600 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.124.0ubuntu2_i386.deb) ...
Setting up flashplugin-nonfree (9.0.124.0ubuntu2) ...
Downloading...
--10:31:58--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 125.252.242.70
Connecting to fpdownload.macromedia.com|125.252.242.70|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
10:31:59 ERROR 404: Not Found.

download failed
The Flash plugin is NOT installed.

Anyway, that would be the old version, too./ So i am rather glad it did NOT work, i'll stay with the currently working (10.0) version that i installed manually (was a .deb package anyway). 

Now, any idea how to hammer that into Netscape/Opera..? I've read somewhere to copy it from Firefox's "plugins" folder into a similar such folder for Opera, but where the heck are those hiding..? Google is my friend but in this case my friend doesn't know the answer :..(

Kind regards......

Thanh

---

### Post by Yellow Pasque on 2009-06-01
/usr/lib/opera/plugins

```
sudo apt-get install konqueror-nsplugins
```

---

### Post by Thanh-BKK on 2009-06-01
Hi :)

Thank you very much for that. In Konqueror it worked from the beginning and in Netscape i got it to work by installing a separate plugin (i let Netscape handle that by itself). Remains Opera, i will look into that tomorrow morning... .just got home and need to go to sleep now :)

Kind regards......

Thanh

---

