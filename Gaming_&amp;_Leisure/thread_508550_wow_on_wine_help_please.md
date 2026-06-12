---
title: "wow on wine help please"
date: 2007-07-24
forum: Gaming &amp; Leisure
---

### Post by darksidedude on 2007-07-24
I know this is an over used title, but ive tried everything, 

my specs are as follows

Ubutntu 7.04 :guitar:
BFG? Nvidia 6200 PCI : I am using the ubuntu restricted drivers, I can't figure out the number sorry:(
AMD athlon 2000xp 1.67ghz
1 gig of ram

It will start, however i get about 7fps in wine, and crashes every 4-5 mins :(

I cant rember the code, however direct render comes up with a yes, and openGL gives me the nvidia output,

I have followed the Ubuntu wow on wine howto, but it still is very slow, i even did the registry mod, no dice,

thanks for your time

---

### Post by Nkari on 2007-07-24
Probably an overused title because it is the most common thing keeping people on windows at the moment, and the game supposedly works very well under Ubuntu according to people that actually got it to work.

Looks like you got further than I did. 

Just saw another thread about choppy sound and graphics, where someone with the same problem as you tweaked a few things and it is all better now.

---

### Post by chromerium on 2007-07-24
Turn off the power management and cpu throttling stuff I meantioned in another thread ([http://ubuntuforums.org/showthread.php?t=508409](http://ubuntuforums.org/showthread.php?t=508409)) and that might help.

Also, make sure you're running in OpenGL mode, not DirectX mode. WoW is buggy on DirectX WoW.

---

### Post by Nkari on 2007-07-24
I'm sure all my problems would be solved if I could get it to run in GL mode and not spit out a big fat not supported error

---

### Post by darksidedude on 2007-07-24
i will try the cpu throttling part, and i didnt keep windows, i had to fight the cancer at the source, i had to wait for a shinny new nic card before i switched, my usb modem was not suported, so i got a gigabit ethernet card and router =)

---

### Post by darksidedude on 2007-07-24
it works good untill i patch to the latest, witch at this time was 2.1.3  no TBC
it just goes back to the 7fps, well after all this is beta software so there will be bugs, we should all right to blizzard because dollars speaks more then sense (lol)

---

### Post by Lokanna on 2007-07-24
My specs are pretty overmatched for this game, but I've only been using ubuntu for 3-4 days now and wine even less.  However, I followed the instructions at this url and was running on the first attempt with 73fps in shat.  

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

That link tells you how to edit your config.wtf to choose openGL instead of DirectX.  

Now to try and get sound.  I've not tried since I left the game 2 months ago.  I just tried it to see if it would work.

Also, the easiest way to get these thing running (imho) is to fully patch in windows and just copy the entire directory to your linux drive.  If you have to patch while in linux, ensure to open the torrent ports and downloader ports.  Also, once the patch DL's, it will want to install; the only way I could get this to happen was to open system monitor and kill (not shutdown) the wow.exe application.  

Good luck, hope it was a help!

---

### Post by samexner on 2007-07-25
> **Lokanna said:**
> My specs are pretty overmatched for this game, but I've only been using ubuntu for 3-4 days now and wine even less.  However, I followed the instructions at this url and was running on the first attempt with 73fps in shat.  

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

That link tells you how to edit your config.wtf to choose openGL instead of DirectX.  

Now to try and get sound.  I've not tried since I left the game 2 months ago.  I just tried it to see if it would work.

Also, the easiest way to get these thing running (imho) is to fully patch in windows and just copy the entire directory to your linux drive.  If you have to patch while in linux, ensure to open the torrent ports and downloader ports.  Also, once the patch DL's, it will want to install; the only way I could get this to happen was to open system monitor and kill (not shutdown) the wow.exe application.  

Good luck, hope it was a help!

listen to the man/woman he/she speaks the truth!

---

### Post by Lokanna on 2007-07-25
> **samexner said:**
> listen to the man/woman he/she speaks the truth!

...it? 

<--man

:guitar:

---

### Post by Nkari on 2007-07-25
Yes but it just worked in GL mode for them. Forcing GL just gives me an error dialogue, I get further with d3d, almost but not quite able to play

I did notice one thing rereading it that I didn't try before. I already tried the glow setting, it seems to be very problematic, but not the death setting. If that works there will be a big party.

---

### Post by Lokanna on 2007-07-25
> **Nkari said:**
> Yes but it just worked in GL mode for them. Forcing GL just gives me an error dialogue, I get further with d3d, almost but not quite able to play

I did notice one thing rereading it that I didn't try before. I already tried the glow setting, it seems to be very problematic, but not the death setting. If that works there will be a big party.

Have you ensured you have the correct drivers installed?  

An interesting thread popped up when I googled your card: [http://forums.nvidia.com/index.php?showtopic=22336](http://forums.nvidia.com/index.php?showtopic=22336)

It's mainly dealing w/ windows, but there were a decent amount of people saying that newer drivers "broke" their openGL capabilities.  There is a single post saying it didn't affect linux (but the thread is very old, so the linux drivers are more than likely updated since that post). 

Other than that, I don't have a ton of ideas.  Unfortunately, I've extremely new to linux/wine/etc.  You could try nvnews.net, as they have a linux support forum.

---

### Post by Turboaaa2001 on 2007-07-25
Give WineDoors a try. I just installed it and it comes with several popular programs ready for install including WoW. I just installed Steam and now downloading my copy of Half Life 2 to test with (note: I doubt HL2 will work)

Anyway I saw your post and remembered WineDoors

---

### Post by Nkari on 2007-07-25
Yes I have the Nvidia drivers loaded courtesy of Envy script, and according to things like GL Gears, the command line command to check if GL direct rendering works and the Working GL Screensavers it shouldn't be complaining the way it is, because apparently open GL is working and if gears is anything to go by fairly well.

Maybe I'll try winedoors and see if it helps, sick of having to waste time and space with windows.

---

### Post by darksidedude on 2007-07-25
i have been running wow on openGL mode, that might be the problem, I use the ubuntu restricted drivers, and since i dont know how to install the real ones (something about turning X off.....)
i was afraid i would brake something and just left the ubuntu drivers

---

### Post by darksidedude on 2007-07-25
I installed wine doors , looks good on the outside, im installing wow ans DX9 (with a valid license)
maybe it will work out of the box? ill keep you updated

---

### Post by Lysi on 2007-07-25
I highly recommend wowwiki which collects everything from winedatabase and this forum.

[http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine) 

and of course the already mentioned page...

especially: check the very first thing

glxinfo | grep rendering

which is very often the first thing which went wrong.

---

### Post by Turboaaa2001 on 2007-07-25
Update on my end:

HL2 Lost Coast did not work. It was unable to get to the menu screen. I'm now trying just HL2, I read on another thread about a site that has users give ratings to games they ran on Wine.

[http://appdb.winehq.org/](http://appdb.winehq.org/)

Anyway I hope I was of some help.

---

### Post by darksidedude on 2007-07-25
when i ran ```
 glxinfo | grep rendering
```

i got this 

```
 direct rendering: Yes
```

so that is working, and i have been in OpenGL mode so im kinda lost but determend

and Wine-doors hasnt worked for me, but it might work forothers, its a good idea but it has tons of bugs which all beta's have

---

### Post by Nkari on 2007-07-25
Yes that text command tells me the same thing when I run it, but the game refuses to Launch in GL mode none the less.

---

### Post by justin99 on 2007-07-26
I got it working on my system, but it wasn't easy.

If you've tried different settings under the 'graphics' tab from winecfg then it sounds like some setting within wow is causing the poor performance.
Maybe post your WTF/Config.wtf from the wow folder? You may want to XXX out the account name. Some effects can really slow it down.

Once upon a time doing
set gxWindow "1"
would run in windowed mode and yield better performance.

It also couldn't hurt to post your /etc/X11/xorg.conf file too.

Really hope we can help you can get it going, when it works it seems to work pretty well.

---

### Post by darksidedude on 2007-07-26
well i had to format my drive because i messed up the nvidia driver to much:( so ill post the files as soon as im running again, im posting this from the live cd:lolflag:

---

### Post by Lokanna on 2007-07-26
> **darksidedude said:**
> well i had to format my drive because i messed up the nvidia driver to much:( so ill post the files as soon as im running again, im posting this from the live cd:lolflag:

Ugh! I hate reformats.  

I will say one thing though, I had an issue when I was deciding to install Ubuntu for the first time. I ran into the partition option and froze.  All those options were daunting and I really didn't want to hose my system on the FIRST attempt.  The fact that I was able to launch FireFox, come here, search the forums for the correct answer, and make an informed decision was an AMAZING feat!  This is coming from the "Top of the Line OS, Windows XP" which my disc being an original gold (non SP anything), didn't have drivers for newer motherboards, so unless I had drivers, I wasn't even beginning to think about the net, let alone solve an installation issue.  From that point on, I realized this "linux" thing wasn't a fad =) 

:guitar:

Good luck.

---

### Post by darksidedude on 2007-07-27
well i got everything up and running i get about 50fps in side razor hill barracks  ( go horde ! )

here is  copy of my wow config.wtf ( sensitive data removed )

```
     SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET locale "enUS"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET fullAlpha "1"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "24"
SET farclip "500.000000"
SET specular "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET realmList "XXXX"
SET readScanning "-1"
SET readContest "-1"
SET showToolsUI "1"
SET timingTestError "0"
SET patchlist "XXX"
SET realmName "XXX"
SET gameTip "4"
SET lastCharacterIndex "3"
SET pixelShaders "1"
```
hope posting this makes a difference

---

### Post by darksidedude on 2007-07-28
i got upto around 17 fps outside and around 23 inside dont know how, if my config.wtf helps anyone glad to do it

---

