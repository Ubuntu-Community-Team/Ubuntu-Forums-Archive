---
title: "wine config ?"
date: 2006-07-16
forum: Desktop Environments
---

### Post by mcman42 on 2006-07-16
Hi. I am trying to get photoshop 7 to run under wine. I read at appdb.winehq.org that I have to correct some lines in my config file. Man, I feal myself really stupid but i can not find the file ~/.wine/config that as the [guide]("http://bugs.winehq.org/show_bug.cgi?id=2017") says will probably help me. I am using wine version that was installed by automatix.
Help please.

---

### Post by Ramses de Norre on 2006-07-16
I think there's a package winecfg, maybe you need that. I can't check now so I'm not sure.

---

### Post by mcman42 on 2006-07-16
Nope. As long as I understood I have to add the lines to the config file, and the winecfg thing is just some kind of a gui. It is impossible to add something to it, only choose the given options.

---

### Post by Ramses de Norre on 2006-07-16
Have you tried just creating the file?

---

### Post by mcman42 on 2006-07-16
Well I will :) but it just seems that it has to be somewhere by default.

---

### Post by mcman42 on 2006-07-16
> ;; This config file is for base installation.


Seems that this is the root of the prblem. Because wine that goes with automatix seems to be allready preconfigured or something like that.

---

### Post by Ramses de Norre on 2006-07-16
I've never liked automatix in fact.. maybe you can try to purge the automatix version (sudo aptitude purge wine) and install the repo version then.
This is the most up to date repo:```
## wine
deb http://wine.budgetdedicated.com/apt dapper main
deb-src http://wine.budgetdedicated.com/apt dapper main
```

---

### Post by mcman42 on 2006-07-16
the automatix version works well with other apps so I would remove it only if  there are no other options available. Do you know if it is possible to have like to different versions of wine with them not interferring with each other?

---

### Post by Thund3rstruck on 2006-07-16
Winecfg is not a gui for wine at all, really if you want to use anything beyond standalone exe's in Wine you have to run through winecfg which will install the shared libs base and all the other countles dependencies from windows (fonts and such) that are required for just about every windows app nowadays. 

Search this site for the wine howto and they will walk you step-by-step. It works great. I haven't used photoshop but it worked for all my other windows apps (uTorrent, mp3tag, etc)

---

### Post by rem on 2006-07-16
> **mcman42 said:**
> Hi. I am trying to get photoshop 7 to run under wine. I read at appdb.winehq.org that I have to correct some lines in my config file. Man, I feal myself really stupid but i can not find the file ~/.wine/config that as the [guide]("http://bugs.winehq.org/show_bug.cgi?id=2017") says will probably help me. I am using wine version that was installed by automatix.
Help please.

I also had problems with Photoshop running under Wine (since ImageReady always worked ok) ... had this error message:

```
fixme:actctx:QueryActCtxW stub!
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  147 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  37
  Current serial number in output stream:  37
```

Found out that the proper Photoshop initialisation should be done in Terminal like this:
```

WINEDLLOVERRIDES="wintab32=n" wine "c:\Program Files\adobe\Photoshop 7.0\Photoshop.exe"
```

Tried it and it works... maybe it'll work for you too. I used Wine Tools and installed all the base applications. Besides the well know issue with Photoshop side windows still sticking on the screen after minimalization everything is ok :)

---

### Post by mcman42 on 2006-07-17
```

WINEDLLOVERRIDES="wintab32=n" wine "c:\Program Files\adobe\Photoshop 7.0\Photoshop.exe"
```
Yup. It really does work. Thanks for the help.

---

