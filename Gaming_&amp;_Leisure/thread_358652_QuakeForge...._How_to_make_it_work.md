---
title: "QuakeForge.... How to make it work?"
date: 2007-02-11
forum: Gaming &amp; Leisure
---

### Post by Muiske on 2007-02-11
Good day.



After trying to compile it from source (with help of the documents) several times with always an error message making it stop, I learned that there is a synaptic repository for quakeforge. I have now installed the necessary packages and tried running the game. It does run, but I have no idea to set it up properly. These are my issues:

- Where do I put the pak files so I can run the single player version (I don't need quakeworld as I run that in another client)? 

- Where to put the config files?? How can you set them up for autorun?

- Is there anyone out there who has tried to run the original Quake 1 mission packs (Scourge of Armagon and Dissolution of Eternity) run with QuakeForge? I have read it SHOULD be possible, but I guess it's nightmare. 

So, does anyone have some tips?

Thanks.

---

### Post by Muiske on 2007-02-13
Ok, problems solved.... was a piece of cake actually. The pak files are in /usr/share/games/quake/id1, you can put the mission pack paks there as well and then run the game with command line parameters -game hipnotic or -game rogue. 

All in all it took me 30 minutes to find this out. :D

---

### Post by ardya on 2007-04-14
> **Muiske said:**
> Good day.



After trying to compile it from source (with help of the documents) several times with always an error message making it stop, I learned that there is a synaptic repository for quakeforge. I have now installed the necessary packages and tried...
 


Can you give me a URL for this repository? Seems my quakeforge 0.5.5 src compile won't build on edgy.

Compile error:

 gcc -DHAVE_CONFIG_H -I. -I. -I../../../include -I../../../include -g -march=i686 -O2 -frename-registers -finline-limit=32000 -Winline -ffast-math -funroll-loops -fomit-frame-pointer -fexpensive-optimizations -fstrict-aliasing -pipe -Wall -fno-common -MT cd_file.lo -MD -MP -MF .deps/cd_file.Tpo -c cd_file.c  -fPIC -DPIC -o .libs/cd_file.o
cd_file.c:87: error: static declaration of 'bgmvolume' follows non-static declaration
../../../include/QF/sound.h:126: error: previous declaration of 'bgmvolume' was here
make[3]: *** [cd_file.lo] Error 1
make[3]: Leaving directory `/usr/src/quakeforge-0.5.5/libs/audio/cd'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/src/quakeforge-0.5.5/libs/audio'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/src/quakeforge-0.5.5/libs'
make: *** [all-recursive] Error 1

Thanks!

---

### Post by opt1k on 2008-12-09
Ok this is very weird why this is no longer included in any distributions.

but u can get .deb binaries here
[http://www2.informatik.hu-berlin.de/~beier/code/debian/quakeforge/](http://www2.informatik.hu-berlin.de/~beier/code/debian/quakeforge/)
dpkg -i *common*
dpkg -i *qfcc*
dpkg -i *deb

if these files are gone you can always use alien to convert rpms to debs?

For quake 1 cd install heres one way...

Insert original quake cd.
Open with wine ... diece.exe. Install to drive C when prompted.

open terminal

cd ~/.wine/drive_c/QUAKE
wine resource.exe 
cd ID1
mv PAK0.PAK pak0.pak
mv PAK1.PAK pak1.pak
sudo bash
mkdir -pv /usr/share/games/quake/id1
mv *pak /usr/share/games/quake/id1
rm -rf ~/.wine/drive_c/QUAKE
ln -sv /usr/share/games/quake/id1 /usr/share/games/quakeforge/id

this game may or may not need alsa and osscompat?
apt-get install oss-compat alsa-oss

---

### Post by opt1k on 2008-12-09
Attaching quakeforge debs...

---

### Post by opt1k on 2008-12-09
Still attaching...

---

### Post by opt1k on 2008-12-09
...

---

### Post by opt1k on 2008-12-09
Hopefully this helps anyone else looking for the QuakeForge files.

---

### Post by opt1k on 2008-12-10
If sound is choppy remove the alsa-plugin and try
echo "nq-sdl 0 0 direct" >/proc/asound/card0/pcm0p/oss

---

### Post by badclustercleber on 2009-01-03
It returns Missing GFX.WAD.

Can you help?

Thanks

---

### Post by bdamer on 2009-03-07
> **badclustercleber said:**
> It returns Missing GFX.WAD.

Can you help?

Thanks

Make sure that the pak files under /usr/share/games/quake/id1 are all LOWER CASE (i.e. pak0.pak, pak1.pak).

---

### Post by butji on 2009-05-17
ive got it to work.. but when i open quakeforge, all i see is the intro..... none of the keys have any functions.
can anyone help me?

---

