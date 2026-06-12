---
title: "How to &quot;extract&quot; compiz from Live CD"
date: 2008-04-16
forum: Desktop Effects &amp; Customization
---

### Post by smartygoldenfish on 2008-04-16
hi..
i have Kubuntu 7.10 and was just wondering if i could get Compiz for it..as its preinstalled in Ubuntu.
i dont hv a fast net connection so i cant download it from net,
now i have my Kubuntu 7.10 Live Cd and ubuntu 7.10 Live cd

i have added both in adept. 

but when i search COMPIZ there i dont get anything!
how can i tell Kubuntu to install compiz from ubuntu disk

**[COLOR="Red"]plz tell ONLY methods which dont require Internet[/COLOR]**

---

### Post by kiddyfurby on 2008-04-16
compiz should be installed with Ubuntu 7.10
no further downloading is needed.

I have no idea what the official way to turn on compiz is in KDE
you can however try the following command in terminal,  which would lose effect once you logout

compiz --replace

---

### Post by Zorael on 2008-04-16
> **kiddyfurby said:**
> compiz should be installed with Ubuntu 7.10
no further downloading is needed.
Are you sure Compiz is included on the Kubuntu Live CD? It isn't available as Advanced Desktop Effects as it is in Ubuntu.
edit: Nevermind, didn't read that you have already tried with an Ubuntu disc. Just make sure you update from sources after inserting it, then it should theoretically work as long as you've added the CD as a software source.

Alternatively, download the .deb files from the [Ubuntu Packages site](http://packages.ubuntu.com/search?keywords=compiz&searchon=names&suite=gutsy&section=all). I've never done this myself, so it will likely get messy.

You should get the [**compiz**](http://packages.ubuntu.com/gutsy/compiz) package bundle, [**compizconfig-settings-manager**](http://packages.ubuntu.com/gutsy/compizconfig-settings-manager), and the [**emerald** package bundle](http://packages.ubuntu.com/gutsy/emerald), if you want to use Emerald. Might as well get [the Feisty **emerald-themes** package](http://packages.ubuntu.com/feisty/emerald-themes), as well.

---

### Post by erginemr on 2008-04-16
According to:
[https://wiki.kubuntu.org/HardyHeron/Beta/Kubuntu](https://wiki.kubuntu.org/HardyHeron/Beta/Kubuntu)

the upcoming release of Kubuntu will have Compiz bundled. But you will still need a fast internet connection ;)

---

