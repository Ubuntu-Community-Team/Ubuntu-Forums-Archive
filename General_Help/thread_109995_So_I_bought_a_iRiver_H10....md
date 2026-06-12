---
title: "So I bought a iRiver H10..."
date: 2005-12-29
forum: General Help
---

### Post by dpmaxey on 2005-12-29
alright, i bought the iRiver H10 media player 512mb (yes....512mb...) and knew that i was going to be able to uset knowing that my dad uses Windows XP Home so that's a for sure upload option, but i want to use my Linux box, and i don't know why the file i downloaded "EasyH10-1.2" does not compile when i tell it to correctly.

this is the screen that i have in the terminal:
:???:
```


cd /home/david/easyh10-1.2
david@maxey:~/easyh10-1.2$ ./configure
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
david@maxey:~/easyh10-1.2$


``` 
 if anybody can tell me how to update my C compiler...please tell, because i have already tried to update my whole system, and it finds no packages to download... thanx for your help.

:D~KaWiKa~ :p(hawaiian for david)

---

### Post by MetalMusicAddict on 2005-12-29
From a terminal: ** sudo apt-get install gcc gcc3.4**

You might try just **gcc** 1st then try to compile but I just compiled nVidia drivers and needed both. Also when you install pay attention to the "Recommended Packages" also.

I have a H340 and love it but need to find an app like this to build its database on linux. :)

---

### Post by dpmaxey on 2005-12-29
ok...i got that problem solved now....but now i have another error....dang.

```

david@maxey:~$ cd /home/david/easyh10-1.2
david@maxey:~/easyh10-1.2$ sh ./configure
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables

```

it says C comiler cannot create executables...what's up with that:confused:

---

### Post by DaMasta on 2005-12-29
sudo apt-get install build-essential should help.

---

### Post by Clazzy on 2005-12-29
[http://packages.debian.org/unstable/sound/easyh10](http://packages.debian.org/unstable/sound/easyh10)

What about that?

---

### Post by dpmaxey on 2005-12-29
[quote=DaMasta]sudo apt-get install build-essential should help.[/quote]

so what does that do???

:confused::rolleyes:

---

### Post by DaMasta on 2005-12-29
That gets you the tools to build from source (well...some of the tools).

---

### Post by MetalMusicAddict on 2005-12-29
[QUOTE=Clazzy][http://packages.debian.org/unstable/sound/easyh10](http://packages.debian.org/unstable/sound/easyh10)

What about that?[/QUOTE]
This gave a "Model template not found" error but this should work for you. I dont have the player but it installed fine.

---

### Post by dpmaxey on 2005-12-29
my bad everyone... i meant to say i bought a iRiver U10, it's totally different i think. but anyways,does anybody know how to sync up with that model of iRiver MP3 player???  at least on linux i mean.

---

### Post by pek on 2006-01-12
i'm looking for a solution for the same problem here, it looks that gphoto should work...but i'm not able to...

```

~$ gphoto2 -a
Capacit&#224; della fotocamera        :
Supporto alla porta seriale      : no
Supporto USB                     : no
Scelte di cattura                :
                                 : Cattura non gestita dal driver
Supporto per la configurazione   : no
Cancellazione file su fotocamera : no
Supporto per l'anteprima dei file: no
Caricamento file su fotocamera   : no

```

it's in italian, i'll try to translate

```
~$ gphoto2 -a
camera capacity       :
serial port support      : no
USB support                     : no
capture choice                :
                                 : capture not supported by driver
config support   : no
del files on camera : no
file preview support: no
file loading on camera   : no

```

[http://www.gphoto.org/news/](http://www.gphoto.org/news/)

but if you do a quick search in google you can clearly read "17:13 Monday, gphoto, commit by marcusmeissner to libgphoto2: added iRiver U10"

[http://www.google.com/search?q=U10&domains=cia.navi.cx&sitesearch=cia.navi.cx](http://www.google.com/search?q=U10&domains=cia.navi.cx&sitesearch=cia.navi.cx)

---

### Post by pek on 2006-03-04
update :KS 

[http://lists.freedesktop.org/archives/hal/2006-January/004402.html](http://lists.freedesktop.org/archives/hal/2006-January/004402.html)

what is this thing? how to use it? i searched on google but i found no answer i could understand :cry:

---

