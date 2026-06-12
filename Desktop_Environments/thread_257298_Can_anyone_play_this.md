---
title: "Can anyone play this?"
date: 2006-09-14
forum: Desktop Environments
---

### Post by SmokingGun on 2006-09-14
[http://www.nintendo.co.jp/wii/topics/wii_preview/movie/lineup.html](http://www.nintendo.co.jp/wii/topics/wii_preview/movie/lineup.html)

Or is it just me?  I have Sun Java and plugin installed along with flashplayer.

---

### Post by oedipuss on 2006-09-14
Can't play it either. It requires flash player version 8, which we unfortunately don't have (yet). 
I think a beta of the new flash player for linux (v.9) is pretty much ready, it should be released soon-ish.

---

### Post by SmokingGun on 2006-09-14
Ah.  I thought that might be the problem.  Cheers.

---

### Post by Ramses de Norre on 2006-09-14
Works here, if the flash version is the problem then you can circumvent it like this:
```
sudo gedit .mozilla/firefox/pluginreg.dat
```

And search for this lines:
```
1154529293000:1:7:$
Shockwave Flash 7.0 r63:$
Shockwave Flash:$
```

then change it to this:
```
1154529293000:1:7:$
Shockwave Flash **9.0** r63:$
Shockwave Flash:$
```

---

### Post by reclusivemonkey on 2006-09-14
> **SmokingGun said:**
> [http://www.nintendo.co.jp/wii/topics/wii_preview/movie/lineup.html](http://www.nintendo.co.jp/wii/topics/wii_preview/movie/lineup.html)

Or is it just me?  I have Sun Java and plugin installed along with flashplayer.

You can install IE and Flash Player 9 using ies4Linux. Install wine and cabextract with apt-get;

```

sudo apt-get install wine cabextract

```

then run the script from here;

[http://www.tatanka.com.br/ies4linux/index-en.html](http://www.tatanka.com.br/ies4linux/index-en.html)

You should now be able to see any Flash 9 clips that won't work in Firefox. At least until they release Flash 9 for Linux.

BTW The clip is AWESOME! I can't wait to get a Wii :-D

---

### Post by SmokingGun on 2006-09-14
> **Ramses de Norre said:**
> Works here, if the flash version is the problem then you can circumvent it like this:
```
sudo gedit .mozilla/firefox/pluginreg.dat
```

And search for this lines:
```
1154529293000:1:7:$
Shockwave Flash 7.0 r63:$
Shockwave Flash:$
```

then change it to this:
```
1154529293000:1:7:$
Shockwave Flash **9.0** r63:$
Shockwave Flash:$
```

I tried what you said.  It played but all i got was sound and a grey screen?  This is on Epiphany btw.

---

