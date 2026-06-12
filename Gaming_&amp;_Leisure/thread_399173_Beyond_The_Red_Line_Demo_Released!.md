---
title: "Beyond The Red Line Demo Released!"
date: 2007-04-02
forum: Gaming &amp; Leisure
---

### Post by hikaricore on 2007-04-02
[B]** I've posted a full HowTo here: [http://ubuntuforums.org/showthread.php?t=399788](http://ubuntuforums.org/showthread.php?t=399788) **
** I'm leaving the following posts here just to show you all that I have too much time on my hands**[/B]

My second game thread of the day.   :)

Sadly this one is only a demo.

Yesterday, BTRLTeam relased the windows demo of [Beyond The Red Line]("http://www.game-warden.com/bsg/index.html").
The game uses the Freespace 2 engine and is Based on the Sci-Fi Remake series Battlestar Galactica.
The linux demo installer wasn't released, but the source was.

Via their forums here is the linux source:
[http://www.freespacefaq.com/Downloads/BtRL/btrl_fs2_open-3.6.9.tar.bz2](http://www.freespacefaq.com/Downloads/BtRL/btrl_fs2_open-3.6.9.tar.bz2)

You will need the download and install the windows version:
(either with WINE or install on a windows machine then copy the data files)
[http://www.game-warden.com/bsg/downloads_public/BtRLDemo-Windows.torrent](http://www.game-warden.com/bsg/downloads_public/BtRLDemo-Windows.torrent)
[http://files.filefront.com/7090920](http://files.filefront.com/7090920)
[http://www.thecylonbase.com/index.php?option=com_frontpage&Itemid=1](http://www.thecylonbase.com/index.php?option=com_frontpage&Itemid=1)
[http://games.internode.on.net/filelist.php?filedetails=6722](http://games.internode.on.net/filelist.php?filedetails=6722)
[http://files.moddb.com/6720/download-bsg-beyond-the-red-line-demo/](http://files.moddb.com/6720/download-bsg-beyond-the-red-line-demo/)

Then you will need to move the linux binaries to the location of the installed windows version.

I'm trying this out as I type, so I'll post any issues I have and any further info.

--

The soundtrack for the demo is also availible:

[http://www.game-warden.com/bsg/downloads_public/BtRLDemo-Soundtrack.torrent](http://www.game-warden.com/bsg/downloads_public/BtRLDemo-Soundtrack.torrent)
[http://files.filefront.com/BeyondTheRedLine_SixsSounkrar/;7071337;/fileinfo.html](http://files.filefront.com/BeyondTheRedLine_SixsSounkrar/;7071337;/fileinfo.html)

Not sure if this is needed or just extra for fans.

--
LINUX (system requirements)

Operating System: Linux x86 compatible
CPU: Pentium® 1 GHz or AMD Athlon 800 MHz processor
Memory: 512 MB RAM, 1 GB recommended
Graphics Card: 64 MB NVIDIA® GeForce 3 or ATI Radeon with closed source drivers, Mesa 6 or better with S3TC extension available for open source drivers
Input Device: Mouse and keyboard
Installation: 650 MB free HD space

--

Official demo release thread: [http://www.game-warden.com/forum/showthread.php?t=3502](http://www.game-warden.com/forum/showthread.php?t=3502)
Screenshots: [http://www.game-warden.com/bsg/gallery.html](http://www.game-warden.com/bsg/gallery.html)

--

**EDIT**  The windows installer may install very slowly under wine.  The extracted files are something like 750mb, so just be aware if the installer seems to lock up.  Took like 20mins for me.  :P

**EDIT**  Guess the linux release was source and not binaries.  Corrected post.

---

### Post by hikaricore on 2007-04-02
after a sucessful **./configure**

**make** dumps at:

> In file included from cutscene/movie.cpp:120:
./cutscene/oggplayer.h:23:27: error: theora/theora.h: No such file or directory
./cutscene/oggplayer.h:41: error: &#8216;theora_info&#8217; does not name a type
./cutscene/oggplayer.h:42: error: &#8216;theora_comment&#8217; does not name a type
./cutscene/oggplayer.h:43: error: &#8216;theora_state&#8217; does not name a type
make[1]: *** [movie.o] Error 1
make[1]: Leaving directory `/media/devistate/btrl_fs2_open-3.6.9/code'
make: *** [all-recursive] Error 1


continuing on with:

```
make -i
```

Which runs the make command ignoring errors.

--

**EDIT**

Realized this may be a dependancy issue, installing libtheora-dev from:

> deb [http://mirror.home-dn.net/debian-multimedia](http://mirror.home-dn.net/debian-multimedia) stable main


Now continuing make operation which seems to be working.  :P

(Aaron needs a life)

---

### Post by hikaricore on 2007-04-02
One last update for tonight, everything went smoothly after I installed libtheora-dev and the engine complied.

Now the problem was that the **configure** script didn't check for dependancies and it just took logic to discover the problem.  Tonight logic was interrupted by Farscape for about an hour.  lol

Anyway once you've finished compiling simply:

```
cp code/fs2_open_r locationofbtrl
```

Where locationofbtrl is where you installed Beyond The Red Line via the windows installer.

cd to that location and run:

./fs2_open_r

You may need to edit some config files at this point after you get an error.  So hit escape to exit the game/get back to your terminal.

```
pico ~/.btrl_demo/fs2_open.ini
```

Find this line:

> VideocardFs2open=OGL -(800x600)x16 bit

I believe it was 800x600 but no matter, it's that line.  Replace it with this:

> VideocardFs2open=OGL -(**1024x768**)x16 bit

ctrl+o to save, then ctrl+x to exit

Launch the game again and happy flying.

Frack some fracking toasters.

I'll probably write up an actual howto tomorrow on all this crap.  :P

---

### Post by Ruthenium on 2007-04-02
Wow Hikaricore, two good news coming from you, first World of padman and now this battlestar galactica simulation, you never stop :) 

Thanks for the link, I'll see if I wait for a proper installer or compile it from source with your howto.

---

### Post by Breepee on 2007-04-02
That's a nice game! Really cool! I wish I could fly with the mouse though, as I suck at the kayboard controls and I don't have a joystick.

---

### Post by hikaricore on 2007-04-03
Wrote up a howto earlier here on the forums and at [UGA]("http://gaming.gwos.org/").

News from the BTRL website is saying that the linux demo installer will be availible later today.

This link may work upon release: [http://www.game-warden.com/bsg/downloads_public/BtRLDemo-Linux.torrent](http://www.game-warden.com/bsg/downloads_public/BtRLDemo-Linux.torrent)

But as of now the tracker is not responding to that torrent info.

I'll be updating my howtos at the point of the release.  :)

---

### Post by Wulfrunner on 2007-04-07
note: The Beyond the Red Line Linux demo requires libGtk-1.2. 

The run script may fail with a dirname error; this can be fixed on line 32 of the btrl_demo file by adding quotation marks around $fullpath:

```
dirname "$fullpath"
```

On Fiesty (beta), the demo will still not run, dropping out with 

```
Couldn't run Beyond the Red Line Demo (btrl_demo.bin). Is FSO_DATA_PATH set?
```
or
```
bash: ./btrl_demo.bin: No such file or directory
```

---

### Post by hikaricore on 2007-04-07
edit btrl_demo as I've quoted (myself) below:

> **hikaricore said:**
> Just a note if you install anywhere but the default directory you may have to edit the "/usr/local/bin/btrl_demo" file.

```
sudo pico /usr/local/bin/btrl_demo
```

I personally added:

FSO_DATA_PATH="/media/devistate/linux.bin/beyondtheredline"

Before the "export" section as shown below:

```
**FSO_DATA_PATH="/media/devistate/linux.bin/beyondtheredline"**

export LD_LIBRARY_PATH
export FSO_DATA_PATH

PL2PATH="${HOME}/.btrl_demo/data/players/single"
```

This may have been an issue I caused myself but incase anyone else comes across it.  :)

This may help.

You'll obviously have to replace this with your path.

---

### Post by Linuturk on 2007-04-09
[http://www.game-warden.com/forum/showthread.php?t=3696&highlight=ubuntu](http://www.game-warden.com/forum/showthread.php?t=3696&highlight=ubuntu)

Following that thread.

First, I'd like to thank you for all of your hard work.

First, my specs.

I have a toshiba R15-S822 laptop with an intergrated intel chipset. This
chipset is using open source drivers, and runs beryl really nice. I have
Beryl turned off for gaming.

I've pulled a glxinfo and looked for the module mentioned in the thread.

~/btrl_demo$ glxinfo | grep GL_EXT_texture
libGL warning: 3D driver claims to not support visual 0x4b
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object,
GL_EXT_texture_rectangle,

Obviously, I need this loaded to play the game. Do you have any advice
or help you can give me?

---

### Post by hikaricore on 2007-04-09
Well BTRL should run on an intel chipset, I have run Freespace 2 (which is the engine behind the battlestar modification) on my integrated intel in this HP.
But it depends on the system.

I'm assuming you have direct rendering enabled on your system:

```
glxinfo | grep rendering
```

And that you're running the newly released binary installer instead of my hodge-podge outdated howto.

I honestly don't know if the game will work on your system as there are many intel chipsets and some work better in linux than others. >.<

---

### Post by FoolsGold on 2007-04-09
Cool!

I had heard this BSG game was released, but I never knew they had it working cross-platform. Now I have something to do while waiting for Season 3. :)

---

### Post by hikaricore on 2007-04-09
> **FoolsGold said:**
> Cool!

I had heard this BSG game was released, but I never knew they had it working cross-platform. Now I have something to do while waiting for Season 3. :)

>.< I hate waiting.

Atleast I can watch the new season of Doctor Who while I wait. ;)

---

### Post by Linuturk on 2007-04-11
I used the installer from the torrent on their site.

It installed fine after I installed the libgtk1.2 package.

I've ran Freespace 2 on this machine before.

Yes, I have direct rendering.

---

### Post by Ender Black on 2007-04-11
It worked lovely for me but my computer kept locking up during the tutorial.  I figured out what my problem was.. my screensaver would try to start and it would lock up the game.  Easy fix but I was frustrated for a bit till I figured that one out.  

Kudo's to developers...that is one slick sim of BSG.  And thanks for bringing back a great game genre!

Alright...enough typing....must go kill some frakking cylons...

---

### Post by Linuturk on 2007-04-14
[http://www.game-warden.com/forum/showthread.php?t=3696](http://www.game-warden.com/forum/showthread.php?t=3696)

I posted on the game warden forums. They said I need the libraries listed in the thread.

[http://homepage.hispeed.ch/rscheidegger/dri_experimental/s3tc_index.html](http://homepage.hispeed.ch/rscheidegger/dri_experimental/s3tc_index.html) << there is the link they gave me.

I have an intel chipset, as specified in my sig.

---

### Post by Linuturk on 2007-04-14
I forgot to ask, how do I enable this?

---

### Post by Cresho on 2007-04-23
I just downloaded the demo, ran it like "sh ./the_name_of_the_installer.run" and then dove into my documents and ran the sh file directly.  since I have tons of games installed, it ran fine.  I then did the nvidia settings and bumped them up on 16 anisotrophic also the other.  man it is so sweet.  Looks like a totally new game and excellent quality.

Going back to start the missions over again.  So awsome.

were are the additional missions?

---

