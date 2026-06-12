---
title: "Original Breezy Lagoon Wallpaper for Dapper"
date: 2006-08-29
forum: Desktop Environments
---

### Post by ant1060 on 2006-08-29
Hi,
I would like to use again as my wallpaper in Dapper (which I love) the dark, lugubrious 'original' Ubuntu Lagoon available in Breezy.... but I cannot find it anywhere. Can someone tell me where it is? (It's not in ..../share/wallpapers)
Thanks in advance,
Ant

---

### Post by deldredge on 2006-08-29
/usr/share/backgrounds
Also, it should be available just by right clicking the desktop going to change background and selecting it in the list.

---

### Post by ant1060 on 2006-08-29
Thanks but that location (/usr/share/backgrounds) does not contain the version of the lagoon which I would like to have back....it was what I meant when I said /usr/share/wallpapers by mistake.  Right clicking also brings up the same choice which does not contain the lagoon I am looking for..
Can anybody help here please?  I have been looking ever since Dapper came out!
Thanks :)
Ant

---

### Post by Ramses de Norre on 2006-08-29
Maybe in the ubuntu-artwork package from the breezy repo?

---

### Post by ant1060 on 2006-08-29
Thank you (and in Flemish ook dank je wel :)) Ramses....please could you tell me how to access this repo (what commands to use). Am not much good at stuff like that :(

---

### Post by Ramses de Norre on 2006-08-29
Do ```
wget http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-artwork/ubuntu-artwork_0.2.27-1_all.deb
file-roller ubuntu-artwork_0.2.27-1_all.deb

``` Click on "data.tar.gz" (this will open a new window), then on ".", then keep clicking untill you're in "share" and there choose "backgrounds", you will then hopefully see the desired wallpapers, richt click them select extract and choose an appropriate location.

En neig om nog belgen op het forum te zien ;)

---

### Post by ant1060 on 2006-08-30
Thank you very much once again : I will try this as soon as I can, in a few days' time (when back home in Belgium - am at present in Malta).
:)

---

### Post by ant1060 on 2006-09-03
Hi Ramses,
Back now in Belgium :)
Am unable to do the second line of the code you suggested : I am told
"Could not open file-roller ubuntu-artwork_0.2.27-1_all.deb ARCHIVE TYPE NOT SUPPORTED
Could you possibly help me again?
Thanks in advance
Ant

---

### Post by Ramses de Norre on 2006-09-03
That's strange.. it works here.

This will do it too: ```
dpkg-deb --extract ubuntu-artwork_0.2.27-1_all.deb lagoon
cd lagoon/usr/share/backgrounds/
mv warty-final-* ~/
cd
rm -rf lagoon
```
You now have two files in your home dir, warty-final-ubuntu.png and warty-final-ws-ubuntu.png (wide screen version).
I hope these are the wallpapers you were looking for.

---

### Post by ant1060 on 2006-09-05
Hartelijk bedankt nog eens Ramses = Thanks again so much - that's wonderful! At last :)

---

