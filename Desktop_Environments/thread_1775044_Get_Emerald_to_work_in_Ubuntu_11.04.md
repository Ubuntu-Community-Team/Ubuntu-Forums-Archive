---
title: "Get Emerald to work in Ubuntu 11.04"
date: 2011-06-04
forum: Desktop Environments
---

### Post by juman on 2011-06-04
ok, i just installed ubuntu 11.04. now i want install emerald in my comp but as it is a dead project its not competible but i found a guide on google. to compile the emerlad.
```

[I]sudo apt-get install build-essential libgtk2.0-dev libwnck-dev  libxrender-dev libpango1.0-dev libcairo2-dev compiz-dev  libdecoration0-dev libtool intltool git
cd ~
git clone git://anongit.compiz.org/fusion/decorators/emerald
cd emerald
git checkout -b compiz++ origin/compiz++
./autogen.sh
make
sudo make install[/I]

``` 
so i did that and also installed CompizCOnfig SEtting Manager. i enabled the the window decoration, and in command i wrote 
```
emerald --replace
```
but its not changing, even when i select a theme from the emerald theme manager.
COuld anyBody please help me?

---

### Post by Frogs Hair on 2011-06-04
I tried the PPA  at the link  yesterday and got Emerald working . I hadn't used it since 9.10 , so I thought I would give it a try  . I don't if this will cause a problem because of what you have started already. 
[http://www.webupd8.org/2011/05/get-emerald-to-work-in-ubuntu-1104.html#more](http://www.webupd8.org/2011/05/get-emerald-to-work-in-ubuntu-1104.html#more)

---

### Post by beew on 2011-06-04
> **juman said:**
> ok, i just installed ubuntu 11.04. now i want install emerald in my comp but as it is a dead project its not competible but i found a guide on google. to compile the emerlad.
```

[I]sudo apt-get install build-essential libgtk2.0-dev libwnck-dev  libxrender-dev libpango1.0-dev libcairo2-dev compiz-dev  libdecoration0-dev libtool intltool git
cd ~
git clone git://anongit.compiz.org/fusion/decorators/emerald
cd emerald
git checkout -b compiz++ origin/compiz++
./autogen.sh
make
sudo make install[/I]

```so i did that and also installed CompizCOnfig SEtting Manager. i enabled the the window decoration, and in command i wrote 
```
emerald --replace
```but its not changing, even when i select a theme from the emerald theme manager.
COuld anyBody please help me?

Instead of emerald --replace, you should put /usr/local/bin/emerald in ccsm. emeald --replace, even if it works, means that you start with some other window decorator and then switch to emerald, it is unnecessary (like the command "compiz --replace", so you start with metacity and then replace it with compiz, why not just start with compiz by default?)

I manage to get it to work with a lot of help (thanks to mc4man)
[URL="http://ubuntuforums.org/showthread.php?t=1702253"]
http://ubuntuforums.org/showthread.php?t=1702253[/URL]

---

