---
title: "Oolite"
date: 2007-12-11
forum: Game Specific Discussions
---

### Post by compiledkernel on 2007-12-11
Discuss here. All discussions fall under the general rules of the UGA Code.
No swearing, profanity, nudity or other such subversive images or communications.
No Personal Attacks. Spamming of any kind will not be tolerated.

---

### Post by Perkins on 2007-12-26
I like the game.  Multiplayer would be cool...

I am mildly irritated that I can't find where I'm supposed to put expansion modules.  None of the directories listed on the oolite wiki exist, and creating them doesn't seem to work.

---

### Post by Silvain on 2008-01-02
Oolite ,is running very nicely on my system, So I decided to download a few of the OXP files. Checked on the wiki site
[http://wiki.alioth.net/index.php/OXP]("http://wiki.alioth.net/index.php/OXP")
and it says to put the files in the "AddOns" folder.  I have searched my system and none of the AddOns that I have found seem like obvious candidates for places to put OXP files into. Does anyone know where I need to create this folder at?

---

### Post by Perkins on 2008-01-02
:-\" "Listen... to the sound....   of silence...."  :-\"

---

### Post by Silvain on 2008-01-02
Ok I found some information here, [http://aegidian.org/bb/viewtopic.php?t=3683&highlight=ubuntu]("http://aegidian.org/bb/viewtopic.php?t=3683&highlight=ubuntu")
And here :
[http://aegidian.org/bb/viewtopic.php?p=45016#45016]("http://aegidian.org/bb/viewtopic.php?p=45016#45016")

I posted my question on the Oolite board also and you can see it in the fore mentioned link, Still have not figured out exactly what to do yet.

---

### Post by Perkins on 2008-01-25
ok, figured it out.  It is actually ~/.Oolite/AddOns

But, and here's what was messing everything up, all the modules I have downloaded have an extra folder inside them.  If you extract them straight into the AddOns directory, they won't work.  You need to put just the folder that ends in .oxp in there.

---

### Post by Silvain on 2008-01-26
Ok trying that now, had made that folder elsewhere in system. It didn't seem to work tho. Edit, Just saw my first large asteroid. This definitely:) works for me !

---

### Post by statto1977 on 2008-02-23
No matter how low I turn the settings down on this it runs slowly for me. The only way I can get a playable speed is by turning all the settings down as low as they go and playing in a screen about a quarter of my total screen size. I have a dual core HP laptop (1.83Ghz) with 2gig of ram. Are dual processors not supported in this? Even so, I'd have thought the hardware would have coped with it with no problems.

All the other stuff I've tried has been fine (compiz etc) so I'm a bit nonplussed.

---

### Post by veloce on 2008-03-08
I'm having the same trouble.  I'm wondering if it's graphics card related - I'm using intel onboard on my dell laptop.

---

### Post by greyphi on 2008-03-24
It's all OpenGL folks,  So if you have difficulties displaying your OpenGL screensavers, then you will have issues with the rendering of the game.

Once you can find the drivers for your graphic chipset to display the Screensavers correctly, you shouldn't have any more problems.

I'm running a compaq Evo ultra-slim desktop with onboard Intel Extreme Graphics.  The game runs well - as long as I'm not dogfighting while directly facing a planet with multiple background tasks runnings...

Ps.  Whenever you do a fresh install, the OEM disk finds better drivers than the live-cd.

---

### Post by veloce on 2008-03-26
> **greyphi said:**
> It's all OpenGL folks,  So if you have difficulties displaying your OpenGL screensavers, then you will have issues with the rendering of the game.

Once you can find the drivers for your graphic chipset to display the Screensavers correctly, you shouldn't have any more problems.

I'm running a compaq Evo ultra-slim desktop with onboard Intel Extreme Graphics.  The game runs well - as long as I'm not dogfighting while directly facing a planet with multiple background tasks runnings...

Ps.  Whenever you do a fresh install, the OEM disk finds better drivers than the live-cd.

So are you using the "intel" driver or something different?

The screen savers work fine for me, but oolite is unusable.

---

### Post by statto1977 on 2008-03-26
Same here.

---

### Post by Old_Holborn on 2008-04-08
statto1977 and veloce,

plz, read the following post (*Posted: Tue Apr 08, 2008 1:27 pm*):
[[COLOR="RoyalBlue"]_http://aegidian.org/bb/viewtopic.php?p=49655#49655_[/COLOR]](http://aegidian.org/bb/viewtopic.php?p=49655#49655)

Perform the test with the "Freaky Thargoids" OXP, and post your feedback here or in the following related Ubuntu Forums topic:
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showthread.php?t=746323&highlight=oolite_[/COLOR]](http://ubuntuforums.org/showthread.php?t=746323&highlight=oolite)

---

### Post by statto1977 on 2008-04-08
> **Old_Holborn said:**
> statto1977 and veloce,

plz, read the following post (*Posted: Tue Apr 08, 2008 1:27 pm*):
[[COLOR="RoyalBlue"]_http://aegidian.org/bb/viewtopic.php?p=49655#49655_[/COLOR]](http://aegidian.org/bb/viewtopic.php?p=49655#49655)

Perform the test with the "Freaky Thargoids" OXP, and post your feedback here or in the following related Ubuntu Forums topic:
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showthread.php?t=746323&highlight=oolite_[/COLOR]](http://ubuntuforums.org/showthread.php?t=746323&highlight=oolite)

Which addons folder should I unzip it to? I only see:

/var/lib/vim/addons

and

/usr/share/vim/addons

---

### Post by Old_Holborn on 2008-04-08
The fact is that in Oolite-Linux the "AddOns" directory is not created by default. You have to create it manually. It also depends on the way you managed to have Oolite installed. By the way, which version of Oolite do you have installed?
Anyhow, open a terminal window and create the "AddOns" directory as indicated in the code that follows (*the first line is just an empty "cd" command that puts you to homedir*):```
cd
mkdir .Oolite
mkdir .Oolite/AddOns
```
You should copy the "Freaky Thargoid" oxp directory in the newly created "AddOns" directory. My OXP structure for example is the following:```
me@mypc:~/.Oolite/AddOns$ ls -l
total 64
drwxrwxrwx 7 me me 4096 2008-04-02 23:36 Anarchies1.0.oxp
drwxrwxrwx 8 me me 4096 2008-04-02 23:36 AsteroidStorm.oxp
drwxr-xr-x 6 me me 4096 2006-12-26 16:29 behemoth.oxp
drwxrwxrwx 5 me me 4096 2008-04-02 23:35 cobra35.oxp
drwxrwxrwx 5 me me 4096 2008-04-02 23:34 custsounds.oxp
drwxr-xr-x 5 me me 4096 2007-03-22 19:49 **[COLOR="Red"]Freaky Thargoids 3.oxp[/COLOR]**
drwxr-xr-x 6 me me 4096 2008-02-17 21:09 **[COLOR="Red"]griff_shady_station.oxp[/COLOR]**
drwxr-xr-x 4 me me 4096 2008-04-04 13:11 System_Tinux.oxp
drwxrwxrwx 3 me me 4096 2008-04-02 23:38 YOUR_AD_HERE.oxp
drwxrwxrwx 6 me me 4096 2008-04-02 23:38 YOUR_AD_HERE_set_A.oxp
drwxrwxrwx 6 me me 4096 2008-04-02 23:38 YOUR_AD_HERE_set_B.oxp
drwxrwxrwx 6 me me 4096 2008-04-02 23:38 YOUR_AD_HERE_set_C.oxp
drwxrwxrwx 6 me me 4096 2008-04-02 23:38 YOUR_AD_HERE_set_D.oxp
drwxrwxrwx 6 me me 4096 2008-04-02 23:38 YOUR_AD_HERE_set_E.oxp
me@mypc:~/.Oolite/AddOns$ 

```
I have highlighted two OXPs that demonstrate shaders well (*when they are operational, of course*).

---

### Post by veloce on 2008-04-08
> **Old_Holborn said:**
> statto1977 and veloce,

plz, read the following post (*Posted: Tue Apr 08, 2008 1:27 pm*):
[[COLOR="RoyalBlue"]_http://aegidian.org/bb/viewtopic.php?p=49655#49655_[/COLOR]](http://aegidian.org/bb/viewtopic.php?p=49655#49655)

Perform the test with the "Freaky Thargoids" OXP, and post your feedback here or in the following related Ubuntu Forums topic:
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showthread.php?t=746323&highlight=oolite_[/COLOR]](http://ubuntuforums.org/showthread.php?t=746323&highlight=oolite)

Firstly, I'm using version 1.65 as that's what's in the repository and downloadable from the site.  Not sure how you get 1.7+?

I got the addon installed okay but no animations on the freaky thargoids ship.

---

### Post by Old_Holborn on 2008-04-09
The OpenGL shader functionality (and many more "goodies") appeared in later releases. The Ubuntu repositories have the last _stable_ release (i.e. v1.65) as this has been distributed by the Oolite community. I am currently testing a fix on Oolite OpenGL shader effects, and I thought that this could also address your issue, but that's not the case.

You may still use OXP addons (not all OXPs use OpenGL shader effects). My instructions on how to create the AddOns folder do not concern system-wide Oolite installations (i.e. as the one you have). Read the instructions [[COLOR="RoyalBlue"]_here_[/COLOR]]("http://wiki.alioth.net/index.php/OXP#Linux"), on where your AddOns folder should be located. You may just remove the "*.Oolite*" folder (and its contents), you have created in your home directory. The Oolite addons archive is currently located in [[COLOR="RoyalBlue"]_this wiki_[/COLOR]]("http://wiki.alioth.net/index.php/OXP").

You could always try Oolite development release v1.70 by installing this [[COLOR="RoyalBlue"]package[/COLOR]]("ftp://ftp.alioth.net/oolite/oolite-1.70.x86.package"). Take care to uninstall the previous version of Oolite, first. You can reinstall it anytime you want, if v1.70 does not interest you. The development releases, although they are heavily tested and debugged, could have some glitches, since they still are under development. Check if this version helps with your case, however, it seems that you have a driver installation problem. I did not have any performance issues with Oolite v1.65 on an Intel(R) 3000 chipset.

I will start a new thread for those who want to be "*on the bleeding edge*" and build the most recent Oolite version on Ubuntu.

EDIT: Two new threads started on [[COLOR="RoyalBlue"]_how to get Oolite v1.71.2(development release)_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=792813") and [[COLOR="RoyalBlue"]_how to build Oolite from source_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=792781").

---

### Post by Old_Holborn on 2008-05-13
statto1977 and veloce,

please execute
```
lspci -vn | grep VGA | awk '{ print $3 }'
```
and post the results. We may be close to something.

---

### Post by Category on 2008-08-17
I've just installed this, and love it!

Can anybody recommend any good OXP's to expand the game, but still run on a lighter system?

---

### Post by kcallis on 2009-01-25
Is it just me, or did anyone have problems with the keybinding in Oolite 1.65 from the Ubuntu repositories? I seems to have issues with the yaw keys (, and .). I didn't want to make any changes until I was certain it was just on my machine.

---

### Post by veloce on 2009-01-25
> **kcallis said:**
> Is it just me, or did anyone have problems with the keybinding in Oolite 1.65 from the Ubuntu repositories? I seems to have issues with the yaw keys (, and .). I didn't want to make any changes until I was certain it was just on my machine.

Not just you, the yaw keys don't work for me either.

---

### Post by Perkins on 2009-01-25
There are yaw keys?  

I guess that means they're not working on mine either...

---

### Post by yanick.rochon on 2010-08-21
I just installed Oolite right off the repository and it does not work. There does not seem to be any error (??) so I'm not sure why it won't run. My hardware should be way sufficient to run this program as I can play all the most recent games (Windows 7 in dual boot) very fluid.

Hers't the output of the command :

> ~$ oolite 
2010-08-21 01:17:49.954 oolite[3331] initialising SDL
2010-08-21 01:17:50.385 oolite[3331] init: numSticks=0
2010-08-21 01:17:50.386 oolite[3331] CREATING MODE LIST
2010-08-21 01:17:50.386 oolite[3331] Added res 1280 x 720
2010-08-21 01:17:50.386 oolite[3331] Added res 1024 x 768
2010-08-21 01:17:50.386 oolite[3331] Added res 800 x 600
2010-08-21 01:17:50.386 oolite[3331] Added res 720 x 480
2010-08-21 01:17:51.632 oolite[3331] drawRect calling initialiseGLWithSize
2010-08-21 01:17:51.632 oolite[3331] Creating a new surface of 800 x 600
2010-08-21 01:17:51.634 oolite[3331] no universe, clearning surface
2010-08-21 01:17:51.635 oolite[3331] ---> searching paths:
("/usr/lib/GNUstep/System/Applications/oolite.app/Contents/Resources", "/usr/lib/GNUstep/System/Applications/AddOns", "/home/yanick/Library/Application Support/Oolite/AddOns", "/home/yanick/.Oolite/AddOns")
2010-08-21 01:17:51.635 oolite[3331] DEBUG ** no cache exists - yet **
2010-08-21 01:17:51.697 oolite[3331] Vertex Array Range optimisation - not supported
2010-08-21 01:17:51.697 oolite[3331] DEBUG creating octree cache......
2010-08-21 01:17:51.798 oolite[3331] ***** Player 100 does not respond to 
2010-08-21 01:17:51.798 oolite[3331] ***** Player 100 does not respond to 
2010-08-21 01:17:51.798 oolite[3331] ***** Player 100 does not respond to 
2010-08-21 01:17:51.798 oolite[3331] DEBUG ** resetting track for <ShipEntity Player 100> **
Aborted

---

### Post by Perkins on 2010-08-25
My best guess would be that it has something to do with:

2010-08-21 01:17:51.697 oolite[3331] Vertex Array Range optimisation - not supported

---

### Post by movieman on 2010-09-15
> **yanick.rochon said:**
> I just installed Oolite right off the repository and it does not work. There does not seem to be any error (??) so I'm not sure why it won't run.

It's raising some kind of exception and crashing, unfortunately it doesn't bother to tell you what kind of exception is, which might help to figure out how to work around it.

---

### Post by movieman on 2010-09-15
Ah, looks like it won't work with the version of Gnustep that comes with 10.04:

[http://aegidian.org/bb/viewtopic.php?t=7872&postdays=0&postorder=asc&start=15](http://aegidian.org/bb/viewtopic.php?t=7872&postdays=0&postorder=asc&start=15)

---

### Post by yanick.rochon on 2010-09-18
> **Perkins said:**
> My best guess would be that it has something to do with:

2010-08-21 01:17:51.697 oolite[3331] Vertex Array Range optimisation - not supported


Ok.... and what would cause such an error? OpenGL screensavers run just fine, I can play any other accelerated graphic games/apps, etc. I may not have *the* most recent graphics card, but it's still an ATI Mobility Radeon HD 3670.

I did not play in the configuration files; just installed via synaptic and run.

By the way...

```
2010-09-18 20:00:08.949 oolite[8068] no universe, clearning surface

```

... "clearning" ? And what is that :

```
2010-09-18 20:00:09.115 oolite[8068] ***** Player 100 does not respond to 
```

... does not respond to what?

---

### Post by Perkins on 2010-09-19
Well, if you're dual-booting anyway, then try the Windows version:  [http://www.oolite.org/download.shtml](http://www.oolite.org/download.shtml)

If it works, then you've probably got a library issue.  If it doesn't, then it doesn't like your hardware.  :)

---

### Post by hawthornso23 on 2011-04-01
Me too. Installed from repositary. No joy. Running from commandline gives

```

ian@einstein:~$ oolite
2011-04-01 19:14:54.108 oolite[9210] initialising SDL
2011-04-01 19:14:54.199 oolite[9210] init: numSticks=0
2011-04-01 19:14:54.199 oolite[9210] CREATING MODE LIST
2011-04-01 19:14:54.199 oolite[9210] Added res 1680 x 1050
2011-04-01 19:14:54.199 oolite[9210] Added res 1440 x 900
2011-04-01 19:14:54.199 oolite[9210] Added res 1400 x 1050
2011-04-01 19:14:54.199 oolite[9210] Added res 1280 x 1024
2011-04-01 19:14:54.199 oolite[9210] Added res 1152 x 864
2011-04-01 19:14:54.199 oolite[9210] Added res 1024 x 768
2011-04-01 19:14:54.199 oolite[9210] Added res 800 x 600
2011-04-01 19:14:54.199 oolite[9210] Added res 720 x 480
2011-04-01 19:14:54.456 oolite[9210] drawRect calling initialiseGLWithSize
2011-04-01 19:14:54.456 oolite[9210] Creating a new surface of 800 x 600
2011-04-01 19:14:54.468 oolite[9210] no universe, clearning surface
2011-04-01 19:14:54.469 oolite[9210] ---> searching paths:
("/usr/lib/GNUstep/System/Applications/oolite.app/Contents/Resources", "/usr/lib/GNUstep/System/Applications/AddOns", "/home/ian/Library/Application Support/Oolite/AddOns", "/home/ian/.Oolite/AddOns")
2011-04-01 19:14:54.470 oolite[9210] DEBUG ** no cache exists - yet **
2011-04-01 19:14:54.559 oolite[9210] Vertex Array Range optimisation - not supported
2011-04-01 19:14:54.559 oolite[9210] DEBUG creating octree cache......
2011-04-01 19:14:54.711 oolite[9210] ***** Player 100 does not respond to 
2011-04-01 19:14:54.711 oolite[9210] ***** Player 100 does not respond to 
2011-04-01 19:14:54.711 oolite[9210] ***** Player 100 does not respond to 
2011-04-01 19:14:54.711 oolite[9210] DEBUG ** resetting track for <ShipEntity Player 100> **
Aborted


```Same prob as you can see. Was this ever resolved?

 I have an ATI Radeon HD 4650 - proprietary driver.

---

### Post by Keith_Beef on 2012-02-26
I used to play Elite on the BBC Micro, and had it running for a while on my Ubuntu computer.

At some point, I lost it, probably in the upgrade from 10.04 to 11.04, and now that I've installed it again, I get an audio problem.

```
$ oolite
2012-02-26 19:50:43.510 oolite[12659] initialising SDL
2012-02-26 19:50:43.642 oolite[12659] Mix_OpenAudio: No available audio device
Segmentation fault

```

Any ideas how to fix this?

K.

---

### Post by Perkins on 2012-02-27
I no longer have a copy installed, but, if I recall correctly, there were command-line options to adjust sound settings.  You might try playing with those and see if you get any different results.  (If it wasn't available through the command line, I know there was a config file.)

---

### Post by Keith_Beef on 2012-02-27
> **Perkins said:**
> I no longer have a copy installed, but, if I recall correctly, there were command-line options to adjust sound settings.  You might try playing with those and see if you get any different results.  (If it wasn't available through the command line, I know there was a config file.)

Thanks for the idea. I had a quick look at the man page, but didn't see any options for sound like that. Looks like I need to google around a bit more.

---

### Post by Keith_Beef on 2012-02-29
Well, I looked around a lot, and could not find anything about changing sound output options.

Since oolite uses SDL, I tried VDrift (another SDL game) and that gave me no sound, too.
```

ERROR: Error opening audio device, disabling sound.
ERROR: Sound initialization failed
```

I'm beginning to think that this is a problem between SDL and Ubuntu Studio.

---

### Post by Perkins on 2012-02-29
> **Keith_Beef said:**
> Well, I looked around a lot, and could not find anything about changing sound output options.

Since oolite uses SDL, I tried VDrift (another SDL game) and that gave me no sound, too.
```

ERROR: Error opening audio device, disabling sound.
ERROR: Sound initialization failed
```I'm beginning to think that this is a problem between SDL and Ubuntu Studio.


You are most likely correct.  Check your library versions.  It wouldn't be the first time some version of Ubuntu shipped with a broken, beta version of something and was never updated.

---

### Post by Keith_Beef on 2012-03-01
> **Keith_Beef said:**
> Well, I looked around a lot, and could not find anything about changing sound output options.

Since oolite uses SDL, I tried VDrift (another SDL game) and that gave me no sound, too.
```

ERROR: Error opening audio device, disabling sound.
ERROR: Sound initialization failed
```

I'm beginning to think that this is a problem between SDL and Ubuntu Studio.

Success!

I searched a bit further and found [this thread]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/198453") where I picked up a few clues.

I installed libsdl1.2debian-all though I had to remove ubuntu-desktop to do it. After that, vDrift and Oolite both start up with sound, no problem.

I wonder what removing ubuntu-desktop did...

So I decided to install ubuntustudio-desktop, and I&#314;l keep a wary eye out for changes.

---

### Post by Perkins on 2012-03-02
ubuntu-desktop is what they call a "meta package"  It doesn't actually include anything itself, it merely contains the list of what packages to install for the standard system.  You had to remove it to swap out your libraries because what you have installed no longer matches the list in the package.  This doesn't generally cause any problems, but if you decide to upgrade the distro, reinstall the ubuntu-desktop package first since the upgrade process uses that to decide what to replace.

---

