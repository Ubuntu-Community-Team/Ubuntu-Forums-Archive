---
title: "wine and dcom98"
date: 2005-12-10
forum: Desktop Environments
---

### Post by Sander50 on 2005-12-10
Hey,

i installed wine as in [http://ubuntuforums.org/showthread.php?t=29996](http://ubuntuforums.org/showthread.php?t=29996) . The installation was succesful, and i created a "fake windows drive" with winetools.  But when i try to install DCOM98, i got the error "It seems the installation has failed". I got the following in the terminal:
```

Choice is Base setup
Choice is DCOM98 with checked=F
dcom98.exe
wine: error while loading shared libraries: libwine.so.1: cannot open shared object file: No such file or directory
grep: /home/sander/.wine/installed.reg: Onbekend bestand of map
grep: /home/sander/.wine/installed.reg: Onbekend bestand of map
rm: cannot remove `/home/sander/.wine/installed.reg': Onbekend bestand of map
software installation verified by /home/sander/.wine/winetools.log
1229056
WINEDLLOVERRIDES="ole32=n" wine ./dcom98.exe
wine: error while loading shared libraries: libwine.so.1: cannot open shared object file: No such file or directory
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
Failed: 127
check installation by return value...
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
wine: error while loading shared libraries: libwine.so.1: cannot open shared object file: No such file or directory
Failed: 127
```

Can someone help me?

Sander

---

### Post by Rackerz on 2005-12-10
I think your missing some required libraries.

---

### Post by Sander50 on 2005-12-10
yeah, that worked, i got dcom98 installed now.

but when i try to install Internet Explorer 6, the installer starts, but it "can't download the required data" or something. and the installation fails...

Sander

---

### Post by manicka on 2005-12-10
It's much easier just to install the latest version of wine using the repo at winehq. 

Instructions for install  here
[http://doc.gwos.org/index.php/Wine](http://doc.gwos.org/index.php/Wine)

Once installed the latest version of winetools is here
[http://www.von-thadden.de/Joachim/WineTools/index.html#download](http://www.von-thadden.de/Joachim/WineTools/index.html#download)

---

### Post by Rackerz on 2005-12-10
[QUOTE=manicka]It's much easier just to install the latest version of wine using the repo at winehq. 

Instructions for install  here
[http://doc.gwos.org/index.php/Wine](http://doc.gwos.org/index.php/Wine)

Once installed the latest version of winetools is here
[http://www.von-thadden.de/Joachim/WineTools/index.html#download](http://www.von-thadden.de/Joachim/WineTools/index.html#download)[/QUOTE]

I definately recommend using these. Espcially winetools after you've got Wine installed. It configures everything so it works properly. (Presumabley)

---

### Post by YokoZar on 2005-12-10
[QUOTE=manicka]It's much easier just to install the latest version of wine using the repo at winehq. 

Once installed the latest version of winetools is here
[http://www.von-thadden.de/Joachim/WineTools/index.html#download](http://www.von-thadden.de/Joachim/WineTools/index.html#download)[/QUOTE]
I make a winetools package at the repo at winehq as well, that you can much more easily than by following the instructions there.

---

### Post by Sander50 on 2005-12-11
yeah that worked. thnx all!

Sander

---

