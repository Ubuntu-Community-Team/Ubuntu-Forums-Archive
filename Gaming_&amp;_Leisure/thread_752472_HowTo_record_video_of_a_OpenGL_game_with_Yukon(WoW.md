---
title: "HowTo record video of a OpenGL game with Yukon(WoW, etc)"
date: 2008-04-11
forum: Gaming &amp; Leisure
---

### Post by LaLLi on 2008-04-11
I play World of Warcraft and I wanted to record some fun moments. I looked into a few tools, but wasn't sure they would do what I wanted until I found Yukon. Yukon records OpenGL applications using seom video with lossless compression.

I'm using Hardy atm and had a bit of trouble getting Yukon to work with their own Wiki so I desided to make my own how-to for Ubuntu.
yukon Wiki [https://devel.neopsis.com/projects/yukon/wiki/RewriteBranch](https://devel.neopsis.com/projects/yukon/wiki/RewriteBranch)

1.  Install all required files.
```
sudo apt-get install libx11-dev libxv-dev x11proto-xext-dev mesa-common-dev libgl1-mesa-dev libasound2-dev build-essential subversion lame mplayer mencoder
```

2. get yukon.
```
svn co https://devel.neopsis.com/svn/seom/branches/packetized-stream seom
svn co https://devel.neopsis.com/svn/yukon/branches/rewrite yukon

```

3. compile it.
```
cd seom
./configure && make && sudo make install
cd ../yukon
./configure && make && sudo make install
cd ..
```

NOTE: This compiling procedure will make 32bit libs for 32bit systems, 64bit libs for 64bit systems. To record 32bit applications on a 64bit system you will also need to compile the libs for 32bit. See orginal [wiki]("https://devel.neopsis.com/projects/yukon/wiki/RewriteBranch") for details.

4.yukon installs libraries to a folder that Ubuntu doesn't search so we need to add it to Ubuntu library search.
```
echo '/usr/local/lib' | sudo tee -a /etc/ld.so.conf
sudo ldconfig
```

5. Copy configuration files and edit to your liking. Do NOT edit the sysconf file!
```
cp ~/yukon/tools/yukon.conf ~/.yukon/conf
mkdir ~/.yukon/system
cp ~/yukon/sysconf ~/.yukon/system/
nano ~/.yukon/conf

```
6. Verify that all files are where they are supposed to. It's not fool proof but if it fails so will making videos with yukon.
```
sh ~/yukon/tools/post-install-check.sh
```

Yukon works as a wrapper. You use it before the application you want to record. example:
```
yukon glxgears
```
default capture start/stop key is F8.
default capture folder is /tmp.

Raw video recorded with yukon with a resolution of 640*512 takes 10MB every second.

To play a seom video use the yukon filter and mplayer.
```
cd ~/yukon
sh play-stream.sh /directory/of/video.seom

```
To make the videos a LOT smaller you need to convert them to another format. You can use conver-to-avi.sh.
```
cd ~/yukon
nano convert-to-avi.sh
sh convert-to-avi.sh /directory/of/video.seom
```


EDIT: There is a similar software available called GLC. It's easier to get working especially on 64bit. [http://ubuntuforums.org/showthread.php?t=587935&highlight=glc](http://ubuntuforums.org/showthread.php?t=587935&highlight=glc)

---

### Post by boubbin on 2008-05-13
nice, works.
its just drops the framerate of my game... i have pretty old gfx card tho..

---

### Post by LaLLi on 2008-05-14
Good to know it works for some-one else than me. I don't have any notisable fps drop from recording. Dual Core 2,1GHz, 2GB DDR2, GF8600GT and recording to a seperate IDE drive.

---

### Post by zwastik on 2008-05-21
could you do a deb package plis? :)


I am getting this error:

```
make
gcc -shared -o libX11.so.native -Wl,-soname,libX11.so.native
gcc -Iinclude -Wall -std=c99 -O3 -fPIC -shared -o libX11.so src/libs/libX11.c libX11.so.native
rm -f libX11.so.native
gcc -shared -o libGL.so.native -Wl,-soname,libGL.so.native
gcc -Iinclude -Wall -std=c99 -O3 -fPIC -shared -o libGL.so src/libs/libGL.c libGL.so.native
rm -f libGL.so.native
gcc -Iinclude -Wall -std=c99 -O3 -fPIC -c -o src/core/conf.o src/core/conf.c
In file included from include/yukon.h:33,
                 from src/core/conf.c:2:
include/stream.h:17:25: error: seom/stream.h: No existe el fichero o el directorio
In file included from include/yukon.h:33,
                 from src/core/conf.c:2:
include/stream.h:29: error: expected specifier-qualifier-list before ‘seomStream’
make: *** [src/core/conf.o] Error 1

```

---

### Post by LaLLi on 2008-05-22
Hmm..if you followed my guide exactly then I don't know what went wrong. My spanish is a bit rusty(e.g. haven't studied it) so I'm not even sure what error you are getting. "File or directory doesn't exist"?

Sorry I can't make a DEB since I don't remember how I can make one and It would propably suck. :P

---

### Post by birdiewd on 2008-07-05
Hello, I have gotten yukon to work using your guide (thank you so much).

I was wondering if you had (or knew of) a way to show any kind of on screen display or overlay to show that you are recording. I play WoW at full screen and it would be nice to know at a glance if I'm recording something or not.

Thank you again for the wonderful guide.

---

### Post by LaLLi on 2008-07-06
Good to hear that it works for you. I doesn't work for me anymore..propably cos I use 64bit Ubuntu. :P

No sorry I don't know how to overlay "Recording" or anything like that. If you do the research and find a way to do it please post it here, thanks :)

---

### Post by sblanzio on 2008-07-23
Hi!
I haven't tried that yet, but i was curious: is it possible to start/stop the recording after the game is started?

EDIT: sorry, i didn't read well -- solved --

---

### Post by Ferrat on 2008-08-12
Also if you want to record 32Bit apps on a 64bit system you should use the install scripts (added. originally from a ticket response on yukon page), I also added the GLC build scripts, it's a similar program works a little different but good, but the reason I added it here is for the elfshacks that make it possible to capture 32bit and 64 bit apps just the same, yukon makes the swtich but needs the help of the elshacks (at least mine did) :)

Will maybe look in to doing a combined script for seom, yukon and glc with menus etc. but for now unless you want to install the elfshacks yourself then I recommend the script.

EDIT:
Links to original script sites
[http://dbservice.com/projects/yukon/ticket/28](http://dbservice.com/projects/yukon/ticket/28)   <<<--- SEOM and YUKON script

[http://nullkey.ath.cx/projects/glc/wiki/HowtoInstall](http://nullkey.ath.cx/projects/glc/wiki/HowtoInstall)  <<<--- GLC

---

### Post by airtonix on 2008-08-14
i play wow on wine, with a core duo e6550 2gb-800mhzram and a nvidia8800gt.

gtk-recordmydesktop works fine.

---

### Post by cristo-father on 2008-08-14
[http://www.getdeb.net/app/RecordMyDesktop](http://www.getdeb.net/app/RecordMyDesktop)

---

### Post by kielanmatt on 2008-10-04
one more question where do the converter AVI end up??

---

### Post by LaLLi on 2008-10-05
You can determine the folder for the recordings. IIRC the default folder is /tmp.

---

### Post by 569874123 on 2009-08-10
Does this still work?

---

### Post by LaLLi on 2009-08-11
Actually I haven't tried it on the latest Ubuntu.
I don't see why it would not.

Have you tried [http://www.getdeb.net/app/RecordMyDesktop](http://www.getdeb.net/app/RecordMyDesktop) ?

---

### Post by 569874123 on 2009-08-11
> **LaLLi said:**
> Actually I haven't tried it on the latest Ubuntu.
I don't see why it would not.

Have you tried [http://www.getdeb.net/app/RecordMyDesktop](http://www.getdeb.net/app/RecordMyDesktop) ?
I tried it like a year ago. Good to see u r still active in here :D.
Will try it again.

---

### Post by 569874123 on 2009-08-11
Tried recordmydesktop and istanbul. Record cannot record any game i tried...only desktop was recorded...with istanbul i get 1 fps(i was getting 200 fps before trying istanbul).
As for yukon i get errors while installing it.
Any help is much appreatied :D

---

### Post by LaLLi on 2009-08-11
can you paste the install errors?

---

### Post by 569874123 on 2009-08-11
svn: Can't connect to host 'dbservice.com': Connection timed out

---

### Post by cerda on 2009-08-11
Hello guys, im too running WoW on my kubuntu 9.04 (quad 6600, 4gb ram and geforce 260 gtx), performance looks fine but when i get too much people on screen (like dalaran, BG or any raid) it drops considerably (i mean a lot from 100fps to 12fps).

I'm running -opengl and have disabled desktop effects.
I just saw some WoW+linux video on youtube and the guy aparently didn't have this problem (similar performance out world and dalaran).

So any tips on this? thank you :)

---

### Post by LaLLi on 2009-08-12
I'm sorry I don't want to be rude, but your problem really isn't related to the subject of this thread.

Please start a new thread.

P.S. My FPS improved with unofficial Nvidia beta drivers.

---

### Post by LaLLi on 2009-08-12
> **569874123 said:**
> svn: Can't connect to host 'dbservice.com': Connection timed out
Ok so the svn database is unavailable. You can't download via svn. I prob should test wether I can make it work and fix the guide.

You could try GLC recording.
[http://ubuntuforums.org/showthread.php?t=587935](http://ubuntuforums.org/showthread.php?t=587935)

---

### Post by 569874123 on 2009-08-12
Tried it and liked it, but i still want yukon :D.
Thanx for probably testing and fixing the guide :P.

---

### Post by Joseph Schwenker on 2010-05-30
Can anyone help me get this working?  I am completely confused with it.  I ran all of the commands up to step five, where I couldn't to operation 3 because there was no "sysconf" in Yukon.  Can anyone help me?  I tried using the script to check the files, and it says to move some file to "$PATH/bin" or something like that.

---

### Post by LaLLi on 2010-06-06
Sry dont know how to help you. I haven't tested this guide in a while so im not sure what's wrong. I'm kind of hard pressed for free time atm but I might be able to test this in the summer during slow business hours.

I still suggest you try to find an alternative prog like GLC.

---

### Post by Joseph Schwenker on 2010-06-06
I tried using GLC, but I couldn't figure it out either.

---

