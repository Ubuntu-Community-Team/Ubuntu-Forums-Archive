---
title: "Free Download Manager in Ubuntu"
date: 2008-12-09
forum: General Help
---

### Post by iampriteshdesai on 2008-12-09
As a windows user I always loved Free Download Manager it is my favorite. How can I run it in Ubuntu?
I tried Wine but wasn't successful.
It can even convert youtube videos
[http://www.freedownloadmanager.org/](http://www.freedownloadmanager.org/)

---

### Post by bogdan.veringioiu on 2008-12-09
Hi.

I don't know I you will be able to run the app under wine.

However, I reccomend a native download manager: gwget. (sudo apt-get install gwget)

Or, you can install DownloadThemAll ([https://addons.mozilla.org/en-US/firefox/addon/201](https://addons.mozilla.org/en-US/firefox/addon/201)) firefox extension (not so powerfull as gwget..)

Cheers.

Bogdan

---

### Post by iampriteshdesai on 2008-12-09
I installed it but it doesn't have much feature at all....

---

### Post by bogdan.veringioiu on 2008-12-09
You might want to check d4x. I used it some time ago, had a lot of features.

sudo apt-get install d4x

Bogdan

---

### Post by habtool on 2008-12-09
Multiget works well for me..

Info here:
[http://multiget.sourceforge.net/](http://multiget.sourceforge.net/)

Deb install file here...
[http://mesh.dl.sourceforge.net/sourceforge/multiget/multiget_1.1.2-0getdeb1_i386.deb](http://mesh.dl.sourceforge.net/sourceforge/multiget/multiget_1.1.2-0getdeb1_i386.deb)

---

### Post by binbash on 2008-12-09
I am using jdownloader.

---

### Post by compat on 2009-03-06
i use fdm lite with wine, i had to copy mfc42.dll from an XP.
folder c:/WINDOWS/system32/ to ~/.wine/drive_c/windows/system32/ in ubuntu
i only use it for big files, "copy link location" and add it to fdm.

---

### Post by hatalar205 on 2009-03-06
Why do you want to use it? Can you say about its some important features, please. Maybe there will be similar linux program

---

### Post by Jozza The Wick on 2009-03-12
Oh man I love Freedownload manager too (FDM). Multiget is the closest I've found to it, but it's not quite there. The thing I was missing is the ability to download from a site that requires a username and password. Although Multiget supports that feature, I have not been able to get it to work. 

Also, Ability to schedule downloads, or fine tunebandwidth - multiple download threads, etc. Start & stop easily. Run downloads outside of a webbrowser in a stand-alone app.

I've been using FDM under Virtualbox. I couldn't get it to work under Wine, but VBox does it fine (of course), though you need to install Windows (virtually) for that of course...

---

