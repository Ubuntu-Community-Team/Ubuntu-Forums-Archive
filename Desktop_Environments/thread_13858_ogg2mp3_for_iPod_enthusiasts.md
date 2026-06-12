---
title: "ogg2mp3 for iPod enthusiasts"
date: 2005-02-03
forum: Desktop Environments
---

### Post by mathjazz on 2005-02-03
We all agree that OGG is a hell of a music format, even better than MP3. However the MP3s are far more popular and most digital music players (like iPod) do not support the OGG encoding technology.

So, I you have a collection of OGG files and you'd like to convet them to MP3s, follow these short steps:

**Installation**
```

$ sudo apt-get install mp32ogg lame
$ wget ftp://ftp.pbone.net/mirror/plf.zarb.org/plf/mandrake/10.1/noarch/ogg2mp3-0.3-3plf.noarch.rpm
$ sudo alien ogg2mp3-0.3-3plf.noarch.rpm
$ sudo dpkg -i ogg2mp3_0.3-4_all.deb

```
**Usage**
Assumed that /ogg is the location of your OGG files and music.ogg is the name of your OGG file:
```

$ ogg2mp3 /ogg
$ ogg2mp3 music.ogg

```
Enjoy!

---

### Post by Rancoras on 2005-02-03
Just be aware that converting a lossy format to another lossy format will result in even more loss of quality compared to the source recording.

---

### Post by karih on 2005-02-03
[QUOTE=mathjazz]We all agree that OGG is a hell of a music format, even better than MP3. However the MP3s are far more popular and most digital music players (like iPod) do not support the OGG encoding technology.

So, I you have a collection of OGG files and you'd like to convet them to MP3s, follow these short steps:

**Installation**
```

$ sudo apt-get install mp32ogg
$ wget ftp://ftp.pbone.net/mirror/plf.zarb.org/plf/mandrake/10.1/noarch/ogg2mp3-0.3-3plf.noarch.rpm
$ sudo alien ogg2mp3-0.3-3plf.noarch.rpm
$ sudo dpkg -i ogg2mp3_0.3-4_all.deb

```
**Usage**
Assumed that /ogg is the location of your OGG files and music.ogg is the name of your OGG file:
```

$ ogg2mp3 /ogg
$ ogg2mp3 music.ogg

```
Enjoy![/QUOTE]
 Ahh, nice, I was just wondering yesterday how I would do this :)
Had to install additionally package named "lame" though, you might want to mention that.

This info should be added on ubuntuguide.org I think.

---

### Post by mathjazz on 2005-02-03
Ooops, I forgot lame, because I installed it before. It's added now.

And I already emailed the Ubuntu Guide maintainer ;)

---

### Post by mathjazz on 2005-02-03
Rancoras: it still good enough for almost everyone. But the quality depends on compression setting, of course.

---

### Post by John McClane on 2005-02-11
Very nice but i must convert ogg 48000 to mp3 48000 and i can't to use this command.
If i convert an .ogg file to .mp3 the audio is not sincronized :(

---

### Post by tom on 2005-03-06
[QUOTE=mathjazz]Ooops, I forgot lame, because I installed it before. It's added now.

And I already emailed the Ubuntu Guide maintainer ;)[/QUOTE]

And don't forget mp32ogg (!) must be installed also.

---

### Post by mirtux on 2005-03-30
Thanks for the hint, this was what i was looking for!

Regards,
MC

---

### Post by GAW-Snow on 2005-07-11
root@Arachnopuppy:/home/hector # sudo alien ogg2mp3-0.3-3plf.noarch.rpm
File "ogg2mp3-0.3-3plf.noarch.rpm" not found.
root@Arachnopuppy:/home/hector # wget [ftp://ftp.pbone.net/mirror/plf.zarb.org/plf/mandrake/10.1/noarch/ogg2mp3-0.3-3plf.noarch.rpm](ftp://ftp.pbone.net/mirror/plf.zarb.org/plf/mandrake/10.1/noarch/ogg2mp3-0.3-3plf.noarch.rpm)
--11:39:37--  [ftp://ftp.pbone.net/mirror/plf.zarb.org/plf/mandrake/10.1/noarch/ogg2mp3-0.3-3plf.noarch.rpm](ftp://ftp.pbone.net/mirror/plf.zarb.org/plf/mandrake/10.1/noarch/ogg2mp3-0.3-3plf.noarch.rpm)
           => `ogg2mp3-0.3-3plf.noarch.rpm'
Resolving ftp.pbone.net... 193.25.186.51
Connecting to ftp.pbone.net[193.25.186.51]:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /mirror/plf.zarb.org/plf/mandrake/10.1/noarch ...
**No such directory `mirror/plf.zarb.org/plf/mandrake/10.1/noarch'.**

root@Arachnopuppy:/home/hector #

---

### Post by tigerstripedcat on 2005-08-01
[QUOTE=GAW-Snow]root@Arachnopuppy:/home/hector # sudo alien ogg2mp3-0.3-3plf.noarch.rpm
File "ogg2mp3-0.3-3plf.noarch.rpm" not found.
root@Arachnopuppy:/home/hector # wget [ftp://ftp.pbone.net/mirror/plf.zarb.org/plf/mandrake/10.1/noarch/ogg2mp3-0.3-3plf.noarch.rpm](ftp://ftp.pbone.net/mirror/plf.zarb.org/plf/mandrake/10.1/noarch/ogg2mp3-0.3-3plf.noarch.rpm)
--11:39:37--  [ftp://ftp.pbone.net/mirror/plf.zarb.org/plf/mandrake/10.1/noarch/ogg2mp3-0.3-3plf.noarch.rpm](ftp://ftp.pbone.net/mirror/plf.zarb.org/plf/mandrake/10.1/noarch/ogg2mp3-0.3-3plf.noarch.rpm)
           => `ogg2mp3-0.3-3plf.noarch.rpm'
Resolving ftp.pbone.net... 193.25.186.51
Connecting to ftp.pbone.net[193.25.186.51]:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /mirror/plf.zarb.org/plf/mandrake/10.1/noarch ...
**No such directory `mirror/plf.zarb.org/plf/mandrake/10.1/noarch'.**

root@Arachnopuppy:/home/hector #[/QUOTE]
 Replace the relevant line above to point to a valid location:

wget  [ftp://ftp.pbone.net/mirror/plf.zarb.org/plf/mandrake/free/2005/noarch/ogg2mp3-0.3-3plf.noarch.rpm](ftp://ftp.pbone.net/mirror/plf.zarb.org/plf/mandrake/free/2005/noarch/ogg2mp3-0.3-3plf.noarch.rpm)

---

### Post by ajslater on 2005-12-02
[ftp://ftp.pbone.net/mirror/plf.zarb.org/plf/mandrake/free/cooker/noarch/](ftp://ftp.pbone.net/mirror/plf.zarb.org/plf/mandrake/free/cooker/noarch/)

---

### Post by zero0w on 2006-03-26
The last update version of the ogg2mp3 script is 0.5, you can find it here:

[http://sourceforge.net/project/showfiles.php?group_id=13488](http://sourceforge.net/project/showfiles.php?group_id=13488) (look for ogg2mp3 in the bottom of the package list)

Author's website
[http://amor.rz.hu-berlin.de/~h0444y2j/linux.html](http://amor.rz.hu-berlin.de/~h0444y2j/linux.html)

I am surprised this package does not go into Debian or Ubuntu universe given it is licensed under GPL v2.

---

### Post by lanort2 on 2008-06-25
Try [[COLOR="DarkOrange"]_Soundconverter via apt-get_[/COLOR]]("apt://soundconverter") or [[COLOR="DarkOrange"]_download Soundconverter_[/COLOR]]("http://soundconverter.berlios.de/")

---

