---
title: "How I got Quake II working in Ubuntu 9.04 &quot;Jaunty&quot;"
date: 2009-06-03
forum: Gaming &amp; Leisure
---

### Post by Staesys on 2009-06-03
I hope this helps someone. I spent a lot of time searching forums and the internet. I couldn't get the loki installer to work because it couldn't find an outdated version of gtk. You could download and compile the correct version of gtk, and glibs and try again... It's a lot of fun satisfying all of the dependencies, let me tell you. This is a lot easier as all you have to do is install a couple of .deb's, copy your data files off the Quake 2 CD and edit the config file. I checked and the quake 2 files are not in Synaptic.

I downloaded and installed the quake2-data_13_all.deb from here:

```
http://packages.ubuntu.com/dapper/all/quake2-data/download
```

and the quake2_0.3-1.1ubuntu1_i386.deb from here:

```
http://gb.archive.ubuntu.com/ubuntu/pool/multiverse/q/quake2/
```

I then inserted my game CD and did the following in a terminal:

```
sudo sulogin

cd /usr/lib/games/quake2/baseq2
cp /media/cdrom/Install/Data/baseq2/pak0.pak .
cp /media/cdrom/Install/Data/baseq2/players/male/* players/male
cp /media/cdrom/Install/Data/baseq2/players/female/* players/female
cp /media/cdrom/Install/Data/baseq2/videos/* videos 
```

Run the game with this line:

```
/usr/lib/games/quake2/./quake2.real
```

If you have no sound (I didn't) and there is an error such as this in the terminal:

```
------- sound initialization -------
loading oss sound output driver, ok
/dev/dsp: Input/output error
SNDDMA_Init: Could not mmap /dev/dsp.
```

To fix this, edit the config.cfg file in the .quake2/baseq2/ folder in your home folder. Find the line:

```
set snddriver "oss"
```

and change it to:

```
set snddriver "sdl"
```

You should now have sound the next time you run the game.

I have been able to run this in SDL OpenGL mode at 1024x768, full screen mode and am getting over 80FPS on my laptop with it's built in nVidia graphics controller.

To make starting the game easier, created a text file called quake2.sh containing:

```
/usr/lib/games/quake2/./quake2.real
```

...and make it executable.

You can then edit your Applications menu and add a launcher pointed to quake2.sh.

---

### Post by Blonddeeni on 2009-06-06
Whoo hooo. Thank you so much for that.
I've been beating my head against a wall for several days now trying to get this game working on my Dell Latitude laptop. 
Admittedly  I'm using Ubuntu 8.10, and the screen that comes up with Quake 2 is quite a small square, but it is at least working somewhat. So I feel I'm getting close.
Now to try and get the sound to work properly. At the moment it is coming through in 1 second bursts.

But I feel that I'm getting somewhere now. Thank you.
Cheers.

---

### Post by Mr.Linc on 2009-06-06
Thank you very much for this guide, works fine for me, although I'm not on Jaunty, I'm on Intrepid.


> **Blonddeeni said:**
> Admittedly  I'm using Ubuntu 8.10, and the screen that comes up with Quake 2 is quite a small square, but it is at least working somewhat. So I feel I'm getting close.
Can't you change the resolution from inside the game menu?

---

### Post by Blonddeeni on 2009-06-07
Cheers. 
Amazing what 24 hours can do for the brain awareness. 
Had a look in the game settings as you suggested, and changed the video part to suit my screen suze.
Now to figure out why the sound is coming out in 1 second bursts.

Tomorrow with a bit of luck.
Thanks heaps for the pointer.:)
B

PS: Been trying variations of sndspeed, bits, channels, not having any effect. Same with snddriver oss, sdl or alsa in the /root/.quake2/baseq/config.cf file.

---

### Post by Blonddeeni on 2009-06-08
Oh yeah, here we gooooooooo...

Changeed the video setting within the game options menu to sdl OpenGl and resolution 1280 x 1024.
Then edited the ~.quake2/baseq/config.cnf file to put in the changes poseted above about changing the set snddriver "sdl".
Now have it working, just a residual echo of scratchyness whenever a sound is played on the game.
I can live with that.
More fiddling later, but thanks to you both for your help.

:D

---

### Post by JarekErvin on 2009-07-26
Hello,
Thanks for your excellent guide, Staesys, which got Quake II running quickly after a long day full of headaches.

However, I can't seem to get sound to come through at all.  There was no config.cfg file to be found, so I created one and added the line you suggested.  This had no effect.

I see that all of the other responders had sound problems, so maybe if any of you guys came across some something that might be useful, I would greatly appreciate your sharing it.

Best,
Jarek

EDIT:
Another obvious thing I forgot to mention was that it occurred to me to check ownership of the folder and subdirectories, but I had already changed ownership so that I could edit everything.

---

### Post by markharding557 on 2009-07-26
just a note quake2 also works perfectly on wine if you prefer the win installer

---

### Post by JarekErvin on 2009-07-26
Well, after a lot of messing around, I came across a site that suggested adding "+set snddriver sdl" to the startup command.  I made a launcher that pointed to quake2.real and added that command, and am now happily gaming with sound.

Cheers,
Jarek

---

### Post by ewg118 on 2009-11-07
Has anyone tried getting Q2 Rocket Arena working in x64?  If you take the arena folder from a working 32bit copy, you can +set game arena and the maps load, but the code isn't executed, presumably because the gamei386.so doesn't work.

---

Actually, after a little more testing, I am able to connect to other Quake 2 Rocket Arena servers perfectly well, but I am having troubles starting the server.  My config files are in ~/.quake2/arena, but it doesn't seem like arena.cfg is executing properly or something.  When I join into the server I start with the native x64 binaries, I end up autospawning into one of the arenas with just a blaster as if it were deathmatch.  No option to join teams.  No weapons settings from the cfg, nothing.

---

### Post by Gato303co on 2012-01-07
Hello, I have Xubuntu 11.10 64bits on al dell Inspiron laptop, and despite I have installed the ia32libs, KVM, to have virtualization, I can't install the quake2 deb package I still got error: "wrong arhictecture: i386"

Anyone may give me some suggestions?  Thanks

---

### Post by VicViper on 2012-01-09
Use a full 64 bit clean client like [http://www.yamagi.org/quake2/]("http://www.yamagi.org/quake2/")

---

### Post by Perfect Storm on 2012-01-09
Necromancing (old thread). Thread close.

---

