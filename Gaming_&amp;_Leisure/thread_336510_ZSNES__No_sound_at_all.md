---
title: "ZSNES : No sound at all?"
date: 2007-01-11
forum: Gaming &amp; Leisure
---

### Post by Pobega on 2007-01-11
I've been playing ZSNES for all my SNES needs lately, but I've come across a problem; At first I had crackly sounds, and now I have *no* sounds. Does anyone have any idea why ZSNES wouldn't be giving off any sounds? And yes I've checked, neither my computer volume nor ZSNES volume is muted.

---

### Post by chronusdark on 2007-01-11
try killing esd before launching it

---

### Post by Pobega on 2007-01-11
It seems that it isn't using ALSA for some reason. Is there any way to force ZSNES to use ALSA sound?

---

### Post by Pobega on 2007-01-13
Bump, I still need to force ZSNES to use ALSA.

---

### Post by Pobega on 2007-01-13
Bump for great justice!

---

### Post by MeanFish on 2007-01-20
If you want to force SDL applications (of which ZSNES is one) to use ALSA for audio output, install the following package:

libsdl1.2debian-alsa.

As a warning, however, to get sound working smoothly I had to install libsdl1.2debian-oss from the repository.  It crackled a lot before that.

---

### Post by Pobega on 2007-01-20
> **MeanFish said:**
> If you want to force SDL applications (of which ZSNES is one) to use ALSA for audio output, install the following package:

libsdl1.2debian-alsa.

As a warning, however, to get sound working smoothly I had to install libsdl1.2debian-oss from the repository.  It crackled a lot before that.

Yeah, I noticed that; OSS playback is fine, but ALSA is crackly. I guess I could live with it, though.

---

### Post by fmaste on 2007-02-07
I downloaded the source of zsnes from its page and installed it myself, this was the only think that worked for me.
Look for the source here [http://www.zsnes.com/](http://www.zsnes.com/)

sudo apt-get install libc6-dev g++ gcc libsdl1.2-dev

Extract the files you download and in a terminal go to the src folder

./configure --enable-release --enable-libao
make
make install

Then run it by typing zsnes in a terminal or alt + f2 and type zsnes

---

### Post by Sarteck on 2007-02-20
> **fmaste said:**
> I downloaded the source of zsnes from its page and installed it myself, this was the only think that worked for me.
Look for the source here [http://www.zsnes.com/](http://www.zsnes.com/)

sudo apt-get install libc6-dev g++ gcc libsdl1.2-dev

Extract the files you download and in a terminal go to the src folder

./configure --enable-release --enable-libao
make
make install

Then run it by typing zsnes in a terminal or alt + f2 and type zsnes


I did the same on my opensuse 10.2 install, but I ran zsnes from a terminal with the sound flags:

$**zsnes -ad oss**

This was using the latest SVN of ZSNES that I could find, and I still had the same problem as the OP--good sound with a few cracks, really cracky sound, then no sound, eventually.

I haven't tried ZSNES on my Kubuntu yet, but hopefully it'll not be such a nightmare. ^_^

---

### Post by DaveCradock on 2008-04-30
I write this post while listening to Zelda title music playing in the background :)

With Ubuntu 8.04...
1. Make sure your volume is turned up :)
2. Make sure your amplifier is actually turned on (Whoops, silly mistake by me, I wasted 10 minutes wondering why I was getting no sound!)

Just install ZSnes, run it, set stuff up, exit.
Then goto ~/.zsnes directory and edit the file "zsnes1.cfg"
I found some lines under the sound section of this config that looked like this...
> ; libAO driver to use. Use zsnes --help to see valid list.
; However "auto" (to automatically pick best one), and "sdl" should
; always be available.
libAoDriver="auto"


I changed "auto" to "sdl", which uses whatever your SDL libs installed on your system are compiled to use.

To find out which audio lib SDL is using, (Mine was using alsa) ... load up synaptic and search within the "installed" section for "lib sdl"
This will show all SDL libs installed, there should be displayed either...

libsdl1.2.debian-alsa
or
libsdl1.2debian-??????

I at first went into the "System/Preferences/Sound" UI and disabled the ESD, but after I got the sound working, I turned that back on, so that setting this seems to make no difference :)

I also double clicked on the little speaker icon on Gnome's panel and went to file/change device ... and checked that I was using ALSA.

So to recap, edit the config file found in /home/yourname/.zsnes/zsnes1.cfg and change the line which reads...
libAoDriver="auto" <-- didn't work for me.
to 
libAoDriver="sdl" <-- worked (As I was using ALSA (double click speaker icon) and the SDL libs which were installed were compiled with ALSA support.

It worked for me... I hope it works for you :)

This is my first post, sorry for my dumbness, I'm new to Linux.. I'm just trying to figure it all out.. I hope my above post makes sense.
Happy computing.

---

### Post by Grishka on 2008-04-30
you don't have to manually edit the configuration file. entering "zsnes --help" would list the available audio drivers. to make zsnes use sdl just enter "zsnes --ad sdl". also, if you still can't get the sound to work, try installing the libsdl1.2debian-all package.

---

### Post by willowhisp on 2008-05-01
Turning up sampling rate eliminates most crackling. (I think it would eliminate all if it could be turned up more)

---

### Post by acoustibop on 2008-05-01
I think one of the problems with trying the solutions that people suggest for problems like this is they're often solutions that worked for the suggester's own system and setup.

It seems to me that, as a general solution, the best way to go is a combination of Grishka's and DaveCradock's solutions above:

First install libsdl1.2debian-all - don't worry that it removes libsdl1.2debian-alsa, because support for the ALSA driver is included in libsdl1.2debian-all.

Then do 'zsnes --help' to find the available drivers, and try each out with 'zsnes --ad <driver choice>' (substitute the driver you want to try for <driver choice>).

When you've found the driver that works best for you, make it permanent (until you decide to change it) by editing ~/.zsnes/zsnesl.cfg so that you replace auto in the libAoDriver="auto" line with your driver of choice.

BTW the driver that most people seem to have found works for them using this method is the sdl one.  But for some people, the best solution may be different.

---

### Post by Grishka on 2008-05-01
again - there is no need to edit the configuration file by hand. starting zsnes with "-ad <driver>" option will set the proper value for good.

---

### Post by acoustibop on 2008-05-01
Why not, Grishka?  It seems much easier to me to set it in configuration than to have to include the switch every time you start the game.  Even if you set it in a launcher, there will still be times you may want to start ZSNES from a terminal, for instance - then you have to remember to include the switch.

It's not as if it's in any way difficult to edit the configuration file.  To me, it's a much simpler, more elegant solution - it sets your configuration once and for all, and you don't have to worry about it any more.

---

### Post by Grishka on 2008-05-01
> **acoustibop said:**
> Why not, Grishka?  It seems much easier to me to set it in configuration than to have to include the switch every time you start the game.  Even if you set it in a launcher, there will still be times you may want to start ZSNES from a terminal, for instance - then you have to remember to include the switch.

It's not as if it's in any way difficult to edit the configuration file.  To me, it's a much simpler, more elegant solution - it sets your configuration once and for all, and you don't have to worry about it any more.

like I said, starting zsnes with "-ad <driver>" option will set it for good - there is no need to manually edit the configuration file afterwards, and no need to include the switch every time one starts zsnes. once is enough, as zsnes will pass the choosen option to zsnesl.cfg by itself.

---

### Post by acoustibop on 2008-05-01
Ah, I see, good point, Grishka!

---

### Post by gaeawalker on 2008-05-15
Here is my clear sound solution for ZSNES on Ubuntu 8 (Hardy Heron):

1). Install the libsdl1.2-dev by opening a terminal and entering:

```
sudo apt-get install libc6-dev g++ gcc libsdl1.2-dev
```

2). Double check your volume is unmuted and you're audio device is set to Alsa (you can check by double-clicking on your speaker icon then selecting 'File > Change Device').

3). In a terminal window start ZSNES by entering:

```
zsnes -ad sdl
```

4) Try loading a ROM. If there is crackling; select 'Config > Sound' (inside the ZSNES application) and change the sampling rate to 8000HZ (though another sampling rate may work for you).

5). Enjoy hours of old-school gaming.

Hope this helps...

---

### Post by dfreer on 2008-05-15
[http://board.zsnes.com/phpBB2/viewtopic.php?t=11510](http://board.zsnes.com/phpBB2/viewtopic.php?t=11510)

I'm working on getting a package together, just thought I'd share the news :D

---

### Post by WanderingKnight on 2008-05-15
Hey, I've just tried ZSNES on Kubuntu 8.04 and I've got no sound at all. I tried deleting the zsnes config file but no avail, it's still completely mute. Running it from the command line doesn't tell me anything:

```
Audio Opened.
Driver: OSS audio driver output
Channels: 2
Rate: 44100

```

and neither does changing the -ad option. 

I'm fresh out of ideas. This used to work back in GNOME and 7.10.

EDIT: Okay, solved and proved my idiocy while at it, I hadn't tried the sdl option. I suppose the lack of audio with alsa or oss is due to arts, but then again, I had no sound with arts set as the audio driver either.

---

### Post by dfreer on 2008-05-15
> **WanderingKnight said:**
> Hey, I've just tried ZSNES on Kubuntu 8.04 and I've got no sound at all. I tried deleting the zsnes config file but no avail, it's still completely mute. Running it from the command line doesn't tell me anything:

```
Audio Opened.
Driver: OSS audio driver output
Channels: 2
Rate: 44100

```

and neither does changing the -ad option. 

I'm fresh out of ideas. This used to work back in GNOME and 7.10.

EDIT: Okay, solved and proved my idiocy while at it, I hadn't tried the sdl option. I suppose the lack of audio with alsa or oss is due to arts, but then again, I had no sound with arts set as the audio driver either.

Check the post **directly** above yours. Nach already provided a patch and several binaries that should take care of the sound problem.

---

### Post by golfrguy on 2008-05-21
> **gaeawalker said:**
> Here is my clear sound solution for ZSNES on Ubuntu 8 (Hardy Heron):

1). Install the libsdl1.2-dev by opening a terminal and entering:

```
sudo apt-get install libc6-dev g++ gcc libsdl1.2-dev
```

2). Double check your volume is unmuted and you're audio device is set to Alsa (you can check by double-clicking on your speaker icon then selecting 'File > Change Device').



3). In a terminal window start ZSNES by entering:

```
zsnes -ad sdl
```

4) Try loading a ROM. If there is crackling; select 'Config > Sound' (inside the ZSNES application) and change the sampling rate to 8000HZ (though another sampling rate may work for you).

5). Enjoy hours of old-school gaming.

Hope this helps...

Thanks a ton. This worked great!

---

### Post by CanadianLinux on 2008-06-02
> **DaveCradock said:**
> I write this post while listening to Zelda title music playing in the background :)

With Ubuntu 8.04...
1. Make sure your volume is turned up :)
2. Make sure your amplifier is actually turned on (Whoops, silly mistake by me, I wasted 10 minutes wondering why I was getting no sound!)

Just install ZSnes, run it, set stuff up, exit.
Then goto ~/.zsnes directory and edit the file "zsnes1.cfg"
I found some lines under the sound section of this config that looked like this...


I changed "auto" to "sdl", which uses whatever your SDL libs installed on your system are compiled to use.

To find out which audio lib SDL is using, (Mine was using alsa) ... load up synaptic and search within the "installed" section for "lib sdl"
This will show all SDL libs installed, there should be displayed either...

libsdl1.2.debian-alsa
or
libsdl1.2debian-??????

I at first went into the "System/Preferences/Sound" UI and disabled the ESD, but after I got the sound working, I turned that back on, so that setting this seems to make no difference :)

I also double clicked on the little speaker icon on Gnome's panel and went to file/change device ... and checked that I was using ALSA.

So to recap, edit the config file found in /home/yourname/.zsnes/zsnes1.cfg and change the line which reads...
libAoDriver="auto" <-- didn't work for me.
to 
libAoDriver="sdl" <-- worked (As I was using ALSA (double click speaker icon) and the SDL libs which were installed were compiled with ALSA support.

It worked for me... I hope it works for you :)

This is my first post, sorry for my dumbness, I'm new to Linux.. I'm just trying to figure it all out.. I hope my above post makes sense.
Happy computing.


I can confirm it worked for me.. Nice job, nice find.

---

### Post by inchaos on 2008-06-07
I'm running hardy and had no sound from ZSNES about two minutes ago.

I use ALSA to begin with, installed the libsdl1.2debian-all, ran ZSNES with '-ad sdl' flags which gave me crackly sound, then changed the sampling rate to 11025 hz.  Problem solved!

---

### Post by Heggerud on 2008-06-08
you also could my guide for libao zsnes
[http://ubuntuforums.org/showthread.php?p=5136009#post5136009](http://ubuntuforums.org/showthread.php?p=5136009#post5136009)

---

### Post by jukingeo on 2008-06-12
> **Heggerud said:**
> you also could my guide for libao zsnes
[http://ubuntuforums.org/showthread.php?p=5136009#post5136009](http://ubuntuforums.org/showthread.php?p=5136009#post5136009)

Hello,

I been having LOTS of sound problems with Ubuntu. I guess for reason being is that I do not have a standard supported sound card.  I have the Sound Blaster X-Fi.  I was told that ALSA will NOT work with this card and was instructed to use OSS instead.  That did work and I got sound from the internet as well as my Totem Movie Player (which also handles my sound files).

I decided to go on a gaming kick and I have several emulators loaded on board right now:

Stella, Gens, GFEC (I think, NES Emulator), ZSNES, and DosBox.

None of these had sound.  Not even native Linux games had sound.  I followed another instruction guide to install Pulse on my system and now I DO have sound but to varying degrees.  These are the results:

Native Linux games:  Work great.

STELLA: plays, but plays fast (higher pitch).  I was able to somewhat play with the audio settings within Stella to correct this.  Audio is fairly clear, but not stupendous, but changing the pitch down does clear things up.

The NES Emulator:  Works great.

GENS:  Works, but it is extremely choppy.  Fiddling with GENS' sound settings doesn't seem to help

DosBox:  The sound is choppy, but it isn't as bad as with GENS. The choppiness tends to come and go more than be continuous.

and last, but not least

ZSNES:  Still no sound.

I am not sure if your guide will work for OSS, but I will let you be the judge of that.  The only thing that I do know is that ALSA will NOT work with my X-Fi card and as of now I think OSS is the only thing that will work with the card.  Pulse is working fine through OSS with the exceptions mentioned above.  However, all these mods did knock out my internet video/sound to where it is so slow and choppy, I cannot view streaming files from the internet anymore.  However, I was able to do so prior to attempting to fix the sound problems with the games.

Any advice would be appreciated.

Thanx,

Geo

---

### Post by acoustibop on 2008-06-12
Looking at the [Creative Open Source site]("http://opensource.creative.com/soundcard.html"), jukingeo, the release notes for the X-Fi driver include this:
> This download is intended for the following audio devices only:

    * Creative Sound Blaster X-Fi Elite Pro 
    * Creative Sound Blaster X-Fi Platinum
    * Creative Sound Blaster X-Fi Fatal1ty®
    * Creative Sound Blaster X-Fi XtremeGamer
    * Creative Sound Blaster X-Fi XtremeMusic

Current release features:

    * ALSA PCM Playback
    * ALSA Record
    * ALSA Mixer

Added Features or Enhancements:

    * Supports GCC version 4
    * Supports Linux 64-bit and 32-bit OS
Looks like your card should support ALSA

---

### Post by Neobuntu on 2008-06-12
> Then goto ~/.zsnes directory and edit the file "zsnes1.cfg"
I found some lines under the sound section of this config that looked like this...
Quote:
; libAO driver to use. Use zsnes --help to see valid list.
; However "auto" (to automatically pick best one), and "sdl" should
; always be available.
libAoDriver="auto"
I changed "auto" to "sdl", which uses whatever your SDL libs installed on your system are compiled to use.

Worked for me! (on a new Hardy install.) 

I guess the non-clean managed dist-upgrage that I did on another box, keep the right configuration.

---

### Post by jukingeo on 2008-06-12
> **acoustibop said:**
> Looking at the [Creative Open Source site]("http://opensource.creative.com/soundcard.html"), jukingeo, the release notes for the X-Fi driver include this:

Looks like your card should support ALSA

It should, but supposedly those drivers are "buggy" and they cause lots of problems.  It is also VERY difficult to set up properly. I WAS going down that route but was told to use OSS instead.

Edit:  I tried to work through some of the steps above.  However, looking for the zsnesl.cfg file to check out the settings, I can't find the file.  In fact I can't even find the .zsnes directory.  Where dose Ubuntu put it?

Thanx,

Geo

---

### Post by acoustibop on 2008-06-12
Same place as most configuration files, jukingeo - in your home folder.  It's hidden (that's what the . before the name does) so you'll need to do View -> Show Hidden Files to see it.

---

### Post by jukingeo on 2008-06-12
> **acoustibop said:**
> Same place as most configuration files, jukingeo - in your home folder.  It's hidden (that's what the . before the name does) so you'll need to do View -> Show Hidden Files to see it.

Thanx!  I was able to get into the file that way and edit it and changed "auto" to "sdl"

Worked like a charm, now I have audio for SNES.

So now that leaves the problem with GENS and getting my internet back in order.

---

### Post by ShadowMKII on 2008-06-13
I am using an Nvidia ALSA mixer for my audio and I have tried both adding the libsdl1.2debian-oss and the libsdl1.2debian-all. I have also changed my zsnesl.cfg (mine says zsnesl.cfg, not zsnes1.cfg for some reason) and that has not seemed to work. I have my sampling rate at the default 32000hz and the default buffer (gaussian) as stated in the .cfg file. I have not allowed my Ubuntu to restart, however.

My Zsnes was running on "oss" for the sound configuration before, but I have changed it to sdl. I do not know what was wrong, as sound was find prior or around the time of the Hardy install.

Is there anyone out there who can assist me?

---

### Post by acoustibop on 2008-06-13
> ... I have tried both adding the libsdl1.2debian-oss and the libsdl1.2debian-all...
So which do you have installed now, ShadowMKII?  Whichever of these two you install will remove the other; however, since libsdl1.2debian-all includes the other drivers, I'd recommend using that.

---

### Post by Heggerud on 2008-06-14
try my sound fix, i have not had anyone say i did not work, unless your sound prob has todo with not having the volume up, lol

[http://ubuntuforums.org/showthread.php?p=5183727#post5183727](http://ubuntuforums.org/showthread.php?p=5183727#post5183727)

---

### Post by ShadowMKII on 2008-06-14
Right now I have the libsdl1.2debian-all, and I have the libao configured to "sdl".

---

### Post by abaqueiro on 2008-08-09
That worked for me too:

Installing zsnes, running, exit.

Edit ~/.zsnes/zsnesl.cfg

put this configurations in the apropiate lines:
libAoDriver="sdl"

The last solve the no sound problem.

StereoSound=1
SoundQuality=6

The last solve the cracky sound.

---

### Post by thrasher6900 on 2008-08-11
I did all of the above and it still doesn't work:(

---

### Post by amr2205 on 2008-10-16
> **DaveCradock said:**
> I write this post while listening to Zelda title music playing in the background :)

With Ubuntu 8.04...
1. Make sure your volume is turned up :)
2. Make sure your amplifier is actually turned on (Whoops, silly mistake by me, I wasted 10 minutes wondering why I was getting no sound!)

Just install ZSnes, run it, set stuff up, exit.
Then goto ~/.zsnes directory and edit the file "zsnes1.cfg"
I found some lines under the sound section of this config that looked like this...


I changed "auto" to "sdl", which uses whatever your SDL libs installed on your system are compiled to use.

To find out which audio lib SDL is using, (Mine was using alsa) ... load up synaptic and search within the "installed" section for "lib sdl"
This will show all SDL libs installed, there should be displayed either...

libsdl1.2.debian-alsa
or
libsdl1.2debian-??????

I at first went into the "System/Preferences/Sound" UI and disabled the ESD, but after I got the sound working, I turned that back on, so that setting this seems to make no difference :)

I also double clicked on the little speaker icon on Gnome's panel and went to file/change device ... and checked that I was using ALSA.

So to recap, edit the config file found in /home/yourname/.zsnes/zsnes1.cfg and change the line which reads...
libAoDriver="auto" <-- didn't work for me.
to 
libAoDriver="sdl" <-- worked (As I was using ALSA (double click speaker icon) and the SDL libs which were installed were compiled with ALSA support.

It worked for me... I hope it works for you :)

This is my first post, sorry for my dumbness, I'm new to Linux.. I'm just trying to figure it all out.. I hope my above post makes sense.
Happy computing.

Thanks, it worked for me!

---

### Post by newgalois on 2008-11-13
I've just download zsnes from 
[http://board.zsnes.com/phpBB2/viewtopic.php?t=11513](http://board.zsnes.com/phpBB2/viewtopic.php?t=11513)
(this version works in intrepid).

The trick to get the sound to work is: remove .zsnes sounds and run again. :D

---

### Post by Drevan on 2008-11-22
> **DaveCradock said:**
> I write this post while listening to Zelda title music playing in the background :)

With Ubuntu 8.04...
1. Make sure your volume is turned up :)
2. Make sure your amplifier is actually turned on (Whoops, silly mistake by me, I wasted 10 minutes wondering why I was getting no sound!)

Just install ZSnes, run it, set stuff up, exit.
Then goto ~/.zsnes directory and edit the file "zsnes1.cfg"
I found some lines under the sound section of this config that looked like this...


I changed "auto" to "sdl", which uses whatever your SDL libs installed on your system are compiled to use.

To find out which audio lib SDL is using, (Mine was using alsa) ... load up synaptic and search within the "installed" section for "lib sdl"
This will show all SDL libs installed, there should be displayed either...

libsdl1.2.debian-alsa
or
libsdl1.2debian-??????

I at first went into the "System/Preferences/Sound" UI and disabled the ESD, but after I got the sound working, I turned that back on, so that setting this seems to make no difference :)

I also double clicked on the little speaker icon on Gnome's panel and went to file/change device ... and checked that I was using ALSA.

So to recap, edit the config file found in /home/yourname/.zsnes/zsnes1.cfg and change the line which reads...
libAoDriver="auto" <-- didn't work for me.
to 
libAoDriver="sdl" <-- worked (As I was using ALSA (double click speaker icon) and the SDL libs which were installed were compiled with ALSA support.

It worked for me... I hope it works for you :)

This is my first post, sorry for my dumbness, I'm new to Linux.. I'm just trying to figure it all out.. I hope my above post makes sense.
Happy computing.

dude you rule

---

### Post by eltoozero on 2008-11-25
My sound was working, but was not today after I came out from suspend.

I poked around and found a solution in this thread:

[http://ubuntuforums.org/showthread.php?t=103465]("http://ubuntuforums.org/showthread.php?t=103465")

"in the sound config of zsnes, i set sampling rate to 44100khz and enabled sound buffering. Restarted Zsnes, and now it sounds crystal clear."

Solution by 0okami, hope it works for you too.

---

