---
title: "HowTo: Install ETQW Full on Gutsy"
date: 2007-10-20
forum: Gaming &amp; Leisure
---

### Post by mb108 on 2007-10-20
Optional steps are (in parentheses).

**0.** Make sure you have the latest OpenGL-capable drivers installed for your graphics card. If you're not sure, open a terminal or use your deskbar applet to run "glxgears". If you see some nice 3D gears churning away, you're good to go.

**(0b.)** If you are running Gutsy 64-bit, you'll have to install 32-bit compatibility libraries:
```

sudo apt-get install ia32-libs

```

**1.** Buy the game (there is no Linux box, just get the Windows one), and then download the Linux client [_here_]("http://zerowing.idsoftware.com/linux/etqw/") (scroll down a bit to the "Files" section).

**2.** Go to the directory where you downloaded the installer, and run it.
```

chmod +x ETQW-client-1.4-full.x86.run
./ETQW-client-1.4-full.x86.run

```

*Note:* if you have problems running the the installer, make sure you are either running 32-bit Gutsy, or have done step 0b.

The installer will prompt you to accept a license, do so if you'd like to proceed.

**3.** Enter a path you would like to install to, ie. "/home/path/to/ETQW/". It will have to be in your home directory, as it's not recommended that you run a downloaded binary as root. Later you can use sudo to relocate wherever you'd like.

**4.** Choose whether to install PunkBuster and whether to copy from DVD. Punkbuster is an anti-cheat program. If you choose to install, it will ask you to accept the PB license. If you choose not to install it, you will be unable to play on many servers, and the servers you can play on will not have this anti-cheat protection.

If you choose to copy from DVD, you will need to insert your DVD before continuing.

**(4b.)** If you have an existing installation (say, on your windows partition), de-toggle the "Copy files from DVD" option. After the install is finished, copy the necessary files over from your existing installation:
```

cp -v /path/to/installed/files/base/pak* /usr/local/games/etqw/base/
cp -R /path/to/installed/files/base/megatextures /usr/local/games/etqw/base/

```

**5.** Play!
```

/path/to/ETQW/etqw

```
If you're feeling overwhelmed by this game, don't be frustrated! This is a very complex tactical shooter, and takes a while to learn. Check out [_this guide_]("http://4newbies.planetwolfenstein.gamespy.com/ETQW/") for some tips.

**(5b.)** If you are running Desktop Effects/Compiz (enabled by default in Gutsy)

Open a terminal and do:
```

sudo apt-get install compizconfig-settings-manager

```
Now go to System->Preferences->Advanced Desktop Effects Settings. Click on "General Options", and un-check "Unredirect Fullscreen Windows". This will fix some bugs with input and snapping to windowed mode. You may have better performance if you disable any GL desktop effects (Compiz) entirely.

**(6.)** To create a launcher

Right-click on your desktop and select "Create Launcher...", and enter in the following:

Type: Application
Name: ETQW
Command: /path/to/ETQW/etqw
Comment: pwn some nubs (or whatever)

Click on the "No Icon" button, and enter
/path/to/ETQW/etqw_icon.png

The icon provided is kind of big, so feel free to choose/create your own. This launcher can be dragged onto your Gnome panel if you'd like.


Hope this helps some people... figures my first Ubuntu HowTo would be for a game. :)
My ETQW tag is "Madnis".

---

### Post by cogadh on 2007-10-20
One problem, Gutsy shouldn't be using the gnome-compiz-manager package, it should use the compizconfig-settings-manager package. The gnome-compiz-manager app is for old Compiz, not Compiz Fusion.

---

### Post by mb108 on 2007-10-20
Edited that section out for now. I wonder why gnome-compiz-manager is in the Gutsy repos?

Is there a better way in Gutsy to get compiz-tray-icon functionality (or similar)?

---

### Post by Naegling23 on 2007-10-20
I just wanted to leave a note for those that want to automatically toggle compiz off when launching the game.  I have this set up for all my games, not just quake wars.  Create a file, call it something like QuakeWars.sh.  Make it executable and all that stuff.  Inside the file, paste the following (note, im using kde, so I use kwin, for those using gnome, use metacity:

#! /bin/bash

kwin --replace &
# launches kwin to replace beryl
sleep 2
# obvious pause to allow kwin a few seconds
./etqw &&
# application params and location here will hold script until exit
sleep 2
# another obvious pause so beryl isn't launching the exact second you close the game
compiz --replace & 
# launch bery to replace kwin after game exit

Save the file in the same directory as etqw.  Now, point your launcher to the file you just created.  No more manually toggling compiz!

---

### Post by JG53_Jaguar on 2007-10-20
Thank You mb108 for posting this HOWTO! I have Ubuntu 7.10 64bit version and I couldn't get the Linux version of ETQW to install no matter what I tried earlier today, until I red your post. The key problem  was for me: **sudo apt-get install ia32-libs**; I didn't know I needed that. ETQW  works great now, thanks!

---

### Post by cogadh on 2007-10-20
> **mb108 said:**
> Edited that section out for now. I wonder why gnome-compiz-manager is in the Gutsy repos?

Is there a better way in Gutsy to get compiz-tray-icon functionality (or similar)?
The package is still in the repos because you can remove Compiz Fusion and go back to regular old Compiz if you choose to (but why would you?). I don't think CF has the same type of tray icon functionality (not really sure though), but you can easily turn off CF by going into System > Preferences > Appearance, choose the Visual Effects tab and set it to "None". Using something like Naegling23's launch script is probably a little bit easier.

---

### Post by mb108 on 2007-10-20
Thanks for the reply cogadh. Backwards compatibility ftw, I guess. :D

Nice script Naegling. I knew there was some way to script it but wasn't sure how to make it "hold" like that. For some reason I had to replace

./etqw && 

with 

/usr/local/games/ETQW/etqw &&

Even though the script is in that same ETQW directory.

---

### Post by Curlydave on 2007-10-21
O hay that looks familiar are you Madnis?

---

### Post by mb108 on 2007-10-22
Hey Curly, yeah cross-posting ftw. :)

---

### Post by crane on 2007-10-23
OK, this may be a strange request but I will have to be satisfied with playing the demo for now. Is there any way someone could send me the ETQW icon? The linux demo does not have an icon and I would like to add a launcher to my desktop.

---

### Post by ezak on 2007-10-23
[IMG]http://xs120.xs.to/xs120/07433/etqw_icon.png[/IMG]

Enjoy.

I wanted it from the beta release as well when it first came out ;)

---

### Post by crane on 2007-10-24
Thanks!
 I have very little money and there is a whole lot being released so ET|QW may not be the first one I get. There are a couple for the PS3 that I am being pushed to get (Guitar Hero 3).
 I played with the ET|QW demo last night and it ran quite smoothly. I was not expecting it to as I heard the game was pretty much built with a Dual Core CPU in mind.
 Now, I just need practice....lots of practice.

---

### Post by christopherZA on 2007-10-27
Hi

Bought and installed my Quake Wars today and must say the installation went without any glitches - thanks.

If anybody is still fence siting on buying this game - Just do it. Buy even if it is only out of principal - thats what I did. The gaming industry needs a financial incentive to develop Linux games and we must not bitch about the lack of games if we do not support them. 


Remember OpenSauce is not free but freedom.


I'm happy with the performance on Linux. Can't compare it to a Windows install as I nuked my WinOS 2 months ago and seriously have no intention of installing it again.

:lolflag:

...Keep on gaming the Tux/ID way.

---

### Post by jagolis on 2007-10-29
Anyone able to use PulseAudio with Quake Wars?

Runs great FPS wise, it's less then the XP version but oh well.

---

### Post by Darganot on 2007-10-29
Everything worked great until I got into the game and seem to have the resolution wrong.  I can set up a username but after that I can't click on the bottom menu and can only see part of the screen.  The keyboard also doesnt work at the title screen (what ever happened to esc quitting lol).

If anyone knows of a fix for this id love to play this game.

---

### Post by Crafty Kisses on 2007-10-29
> **mb108 said:**
> Optional steps are (in parentheses).

**0.** Make sure you have the latest OpenGL-capable drivers installed for your graphics card. If you're not sure, open a terminal or use your deskbar applet to run "glxgears". If you see some nice 3D gears churning away, you're good to go.

**(0b.)** If you are running Gutsy 64-bit, you'll have to install 32-bit compatibility libraries:
```

sudo apt-get install ia32-libs

```

**1.** Buy the game (there is no Linux box, just get the Windows one), and then download the Linux client from any of [_these mirrors_]("http://community.enemyterritory.com/index.php?q=node/185") (the last item on the list is the official .torrent).

**2.** Go to the directory where you downloaded the installer, and run it.
```

chmod +x ETQW-client-1.1.r8.x86.run
./ETQW-client-1.1.r8.x86.run

```

*Note:* if you have problems running the the installer, make sure you are either running 32-bit Gutsy, or have done step 0b.

The installer will prompt you to accept a license, do so if you'd like to proceed.

**3.** Enter a path you would like to install to, ie. "/home/path/to/ETQW/". It will have to be in your home directory, as it's not recommended that you run a downloaded binary as root. Later you can use sudo to relocate wherever you'd like.

**4.** Choose whether to install PunkBuster and whether to copy from DVD. Punkbuster is an anti-cheat program. If you choose to install, it will ask you to accept the PB license. If you choose not to install it, you will be unable to play on many servers, and the servers you can play on will not have this anti-cheat protection.

If you choose to copy from DVD, you will need to insert your DVD before continuing.

**(4b.)** If you have an existing installation (say, on your windows partition), de-toggle the "Copy files from DVD" option. After the install is finished, copy the necessary files over from your existing installation:
```

cp -v /path/to/installed/files/base/pak* /usr/local/games/etqw/base/
cp -R /path/to/installed/files/base/megatextures /usr/local/games/etqw/base/

```

**5.** Play!
```

/path/to/ETQW/etqw

```
If you're feeling overwhelmed by this game, don't be frustrated! This is a very complex tactical shooter, and takes a while to learn. Check out [_this guide_]("http://4newbies.planetwolfenstein.gamespy.com/ETQW/") for some tips.

*Note:* you will have much better performance if you disable any GL desktop effects (Compiz) before running ETQW.

**(6.)** To create a launcher

Right-click on your desktop and select "Create Launcher...", and enter in the following:

Type: Application
Name: ETQW
Command: /path/to/ETQW/etqw
Comment: pwn some nubs (or whatever)

Click on the "No Icon" button, and enter
/path/to/ETQW/etqw_icon.png

The icon provided is kind of big, so feel free to choose/create your own. This launcher can be dragged onto your Gnome panel if you'd like.


Hope this helps some people... figures my first Ubuntu HowTo would be for a game. :)
My ETQW tag is "Madnis".

Nice tutorial thanks!

---

### Post by Darganot on 2007-10-30
ACK!! I can't get online!!!!  I got the game to run fine using a CRT monitor instead of my LCD and I had played all last night online.  This morning I wake up and can't sign into anything and get an anonymous error message that TELLS ME NOTHING!!!  

PLEASE HELP!!!!!!  I WANT TO PAY THIS GAME!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by almostlinux on 2007-10-30
> **Darganot said:**
> ACK!! I can't get online!!!!  I got the game to run fine using a CRT monitor instead of my LCD and I had played all last night online.  This morning I wake up and can't sign into anything and get an anonymous error message that TELLS ME NOTHING!!!  

PLEASE HELP!!!!!!  I WANT TO PAY THIS GAME!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
They've released a patch(v 1.2) today. The linux version is not out though.
You won't be able to play online till it's out.

EDIT: It will be out tonight/morrow: 
[http://community.enemyterritory.com/forums/showthread.php?t=15197](http://community.enemyterritory.com/forums/showthread.php?t=15197)

---

### Post by Darganot on 2007-10-30
> **almostlinux said:**
> They've released a patch(v 1.2) today. The linux version is not out though.
You won't be able to play online till it's out.

EDIT: It will be out tonight/morrow: 
[http://community.enemyterritory.com/forums/showthread.php?t=15197](http://community.enemyterritory.com/forums/showthread.php?t=15197)


Thank you!  :guitar:

---

### Post by Ek0nomik on 2007-10-31
The 1.2 Patch is out.

[http://zerowing.idsoftware.com:6969/](http://zerowing.idsoftware.com:6969/)

---

### Post by jmur on 2007-10-31
> **jagolis said:**
> Anyone able to use PulseAudio with Quake Wars?

from /etc/pulse/default.pa 
```
load-module module-alsa-sink device=plug:dmix:0
load-module module-alsa-sink device=plug:dmix:1
```
from etqwconfig.cfg
```
seta s_driver "alsa"
seta s_alsa_lib "libasound.so.2"
seta s_alsa_pcm "plug:dmix:1" (or "plug:dmix:0" , i have 2 soundcards)
```

---

### Post by frodon on 2007-10-31
> **mb108 said:**
> *Note:* you will have much better performance if you disable any GL desktop effects (Compiz) before running ETQW.You should suggest this first as for some users it may just be enough and it is in addition really painless :
[http://ubuntuforums.org/showpost.php?p=3453361&postcount=9](http://ubuntuforums.org/showpost.php?p=3453361&postcount=9)

---

### Post by LokeTheDog on 2007-10-31
Will there be a 1.2 patch for the demo too?

---

### Post by migla on 2007-10-31
Sometimes etqw drops out of full screen and then I can't control it. Nor can I control the desktop that has become visible. Sometimes the game does bounce back to fullscreen, but most of the time it doesn't.  (Same problem as [this guy ]("http://community.enemyterritory.com/forums/showpost.php?p=186864&postcount=118")has.)

ctrl-alt-F1 and then killing the process of the game (and then alt-F7, ofcourse) gets me in touch with the desktop again.

Anyone else have this problem and/or a solution?

(edit: I run the demo.)

---

### Post by mb108 on 2007-10-31
> **frodon said:**
> You should suggest this first as for some users it may just be enough and it is in addition really painless :
[http://ubuntuforums.org/showpost.php?p=3453361&postcount=9](http://ubuntuforums.org/showpost.php?p=3453361&postcount=9)

Thanks for the heads-up, I will incorporate this as it seems many people are having problems with Compiz.

---

### Post by mb108 on 2007-10-31
> **migla said:**
> Sometimes etqw drops out of full screen and then I can't control it. Nor can I control the desktop that has become visible. Sometimes the game does bounce back to fullscreen, but most of the time it doesn't.  (Same problem as [this guy ]("http://community.enemyterritory.com/forums/showpost.php?p=186864&postcount=118")has.)

ctrl-alt-F1 and then killing the process of the game (and then alt-F7, ofcourse) gets me in touch with the desktop again.

Anyone else have this problem and/or a solution?

(edit: I run the demo.)

migla, please try step 5b.

---

### Post by almostlinux on 2007-10-31
> **LokeTheDog said:**
> Will there be a 1.2 patch for the demo too?
The demo is still 1.1. This patch doesn't affect the demo.

See here: [http://zerowing.idsoftware.com/linux/etqw/](http://zerowing.idsoftware.com/linux/etqw/)

---

### Post by migla on 2007-10-31
> **mb108 said:**
> migla, please try step 5b.

Done that. Same thing. 

However, when I restarted x and logged in with another user, gnome-configuration-manager (or somesuch) (edit - it was GNOME Settings Daemon) failed to load (which it sometimes does), leaving me with ugly (default gnome, I guess) icons, mostly unreadable fonts and the wrong keymap (US, I think), instead of the swedish one I\m supposed to have... But etqw has not messed up since. Now I\ve been playing several rounds without a problem.

I also messed around with my logitech mx518 mouse and changed resolution and other things in etqw, so I don\t know what it was that did the trick. I\ll try to be more methodical tomorrow.

Edit 2 - Tried it with GNOME Settings Daemon working and the problem reappeared... Seems I have to trigger a bug in order not to trigger another bug. So, I can now have a really nice looking desktop and a supercool game, just not at the same time. But that is ok by  me, for now. :)

Edit 3 - Hmm... Now the game plays well even though the settings daemon did work. I'm confused.

---

### Post by theovercoat on 2007-11-01
just in case some of you quake wars players don't already know...  the game with high to max settings  will run 20 fps smoother (timingmethod 0) on average in 32 bit gutsy vs 64 bit gutsy.  gl desktop effects disabled in both.  i hope this claim can be challenged soon.

---

### Post by theovercoat on 2007-11-02
r_useFBODestinationBuffer  0    appears to have found those 20 lost frames per second =D

---

### Post by Darganot on 2007-11-03
> **theovercoat said:**
> r_useFBODestinationBuffer  0    appears to have found those 20 lost frames per second =D


Where does this go?  what does it do?

---

### Post by stil on 2007-11-04
Hi

I'm having problems installing the needed files.

I get...

sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia32-libs

This is Gutsy 7.10 :confused:

---

### Post by mb108 on 2007-11-04
> **Darganot said:**
> Where does this go?  what does it do?

r_useFBODestinationBuffer

is found in

~/.etqwcl/base/etqwconfig.cfg

It's already in there, just change the value. Setting it to 0 (zero) fixes a problem where some people were having ridiculously low fps and crashes. If you upgraded to 1.2 and lost ~20fps, you might try this setting.

However, some have reported that they tried this setting (even though their 1.2 was fine), and it caused a ton of cpu load indoors. So for them it was best to leave it at 1.

No real word on what it does or why the strange behavior.

---

### Post by wishyjr on 2007-11-04
hi guys, can i confirm with you all one the correct version of the game? i have 1.0.11247.11247 in my console - is that the only version available for linux users at the moment?

and does anyone know if/when there will be an update for the linux version? i know theres a windows patch coming soon.


...


oh, and does anyone experience a "cancelled" error when trying to log in and play online? i always seem to get it now but didn't the first couple of days i installed it.

cheers

---

### Post by Jazkal on 2007-11-04
> **wishyjr said:**
> hi guys, can i confirm with you all one the correct version of the game? i have 1.0.11247.11247 in my console - is that the only version available for linux users at the moment?

and does anyone know if/when there will be an update for the linux version? i know theres a windows patch coming soon.


...


oh, and does anyone experience a "cancelled" error when trying to log in and play online? i always seem to get it now but didn't the first couple of days i installed it.

cheers

You need the v1.2 update, it was released a few days ago (linux version)

And you are getting the 'canceled' error because you are at the wrong version.

---

### Post by wishyjr on 2007-11-05
now that is exactly the sorta answer i like to hear -thanks!

any particular link i should try?

---

### Post by wishyjr on 2007-11-05
ok, so i got the file (ETQW-client-1.2-full.r2.x86.run - is that the right one?). But it seems to be trying to re-install altogether rather than update mty current install - is this correct?

thanks

---

### Post by Vorticon on 2007-11-05
Nice tutorial!

I can't play it though i'm getting a weird error:

It loads the game, switches to fullscreen, loads some more until it says

Loading GUI..
and then it crashes and i see this error:

> ERROR: Invalid Number of Parms for Function 'getProfileString' ( expected 1 but received 2 )


Anyone got an idea?

Edit:

I think it might have something to do with the fact that i copied the base contents of my windows install onto my linux etqw base dir, but my windows client is v1.2 and i didn't use the 1.2 client for linux... yet :) (now trying 1.2 client for linux also ^_^)

Edit 2:

That fixed it!

---

### Post by mb108 on 2007-11-05
> **wishyjr said:**
> ok, so i got the file (ETQW-client-1.2-full.r2.x86.run - is that the right one?). But it seems to be trying to re-install altogether rather than update mty current install - is this correct?

thanks

It does sort of look like that. I'm not the best person to comment, cause I messed mine up and ended up doing a complete reinstall with the 1.2 script anyway.

But it should work.

---

### Post by rcmn on 2007-11-05
kde-gusty_linux-ati: GDF transparent, texture issue

So i installed ETQW(demo,1.0,1.2) on my fresh Gusty install. Everything is running fine .I'm able to connect to servers ,play with no lag and all.But i'm running into an issue where the texture of the GDF doesn't appear so basically any GDF is a floating gun .I cannot see the body.I have no problem with the strogg. Also there is certain building I cannot see unless I'm almost touching it.

My config : ATI 9800 pro / gusty 7.10(fresh) /driver default proprietary driver 4.37.


>>Do you have the latest drivers installed for your ATI vid?

well i tried to install the last version of the drivers but it's very very messy. I had to reinstall 4 times my system just by trying different way on installing the new driver.And the funny part is that after i remove the new driver that failed to function properly i cannot use the "supported proprietary driver 4.37". So i have to reinstall in a very specific way just by using the "restricted-manager" gui.Because if you try to use the kde control manager it will mess up xorg.conf. I also tried the Envy thing,and that totally ruined my config. Any other howto's or combined howto's just didn't work for me and i ended up with the "Mesa" nightmare.

---

### Post by stil on 2007-11-05
:confused:> **stil said:**
> Hi

I'm having problems installing the needed files.

I get...

sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ia32-libs

This is Gutsy 7.10


Sorry to quote myself, but... :)

I've installed the 32bit libs, run the installation (had to run it with ./ETQW~~?) and have now run into another problem.

"WARNING: SDL_SetVideoMode failed: Couldn't find matching GLX visual"

Further along, under R_InitOpenGL, I get a segmentatrion fault, si_code 1

I don't even know where to begin troubleshooting this :confused:

I'm using nvidia_glx (not _new)

---

### Post by Curlydave on 2007-11-09
Are there any fixes for the mouse lag other than using the aternate kernel? That doesn't fix it for me.

---

### Post by mb108 on 2007-11-09
> **stil said:**
> :confused:


Sorry to quote myself, but... :)

I've installed the 32bit libs, run the installation (had to run it with ./ETQW~~?) and have now run into another problem.

"WARNING: SDL_SetVideoMode failed: Couldn't find matching GLX visual"

Further along, under R_InitOpenGL, I get a segmentatrion fault, si_code 1

I don't even know where to begin troubleshooting this :confused:

I'm using nvidia_glx (not _new)

Is there a reason you're not using nvidia_new_glx?
Could you run glxgears and see what happens?

---

### Post by turbo7 on 2007-11-16
when i try to install to any location i choose i get  a mkdir error... any ideas how to correct this?
tried installing home/james/
and i tried installing into the games folder.... im a noob so help me out

---

### Post by rcmn on 2007-11-17
strange that you can't install it into your own directory .could you post the message somewhere or give a more specific description of the error,

---

### Post by turbo7 on 2007-11-17
ugh i figured out my problem... i was dragging the location and dropping it because i was to lazy to type it... works fine now

---

### Post by turbo7 on 2007-11-17
well i got quakewars running but i can not install the patch... im really starting to feel stupid

---

### Post by Curlydave on 2007-11-18
Has anyone found a fix for the nasty input lag? It runs great, with performance similar to in Windows, but there is bad input lag. I tried the RT kernel, and it didn't fix it.

---

### Post by mb108 on 2007-11-18
> **Curlydave said:**
> Has anyone found a fix for the nasty input lag? It runs great, with performance similar to in Windows, but there is bad input lag. I tried the RT kernel, and it didn't fix it.

I'm not sure what you mean, input's fine on mine. Have you tried the official forums?

---

### Post by Ram0ne on 2007-11-19
> **wishyjr said:**
> ok, so i got the file (ETQW-client-1.2-full.r2.x86.run - is that the right one?). But it seems to be trying to re-install altogether rather than update mty current install - is this correct?

thanks

Not exactly, I resolved the same issue by, when it reports FILE EXISTS and ask what to do I said NO to overwrite. It will still copy over the new files where needed.

Ram

---

### Post by BattleGnome on 2007-12-12
Hi, 

I am getting the following error when trying to launch the game, any ideas?

> double fault: 'Segmentation fault', bailing out
Segmentation fault (core dumped)

---

### Post by Stradius on 2007-12-19
> **BattleGnome said:**
> Hi, 

I am getting the following error when trying to launch the game, any ideas?

double fault: 'Segmentation fault', bailing out
Segmentation fault (core dumped)


I had a similar problem and it turned out to be a corrupted download file.  I'm not sure how it became corrupted by I suspect it was because I copied it to my Windows partition (NTFS) and then copied it back to my Ubuntu partition (EXT3).

I downloaded a fresh copy directly to my Ubuntu directories and it worked okay.

Thanks.

---

### Post by khowe on 2008-02-04
I found a good deal on an nvidia 7600gs 128mb card @ geeks.com for $34

[http://www.geeks.com/details.asp?invtid=GF7600GS-128HDTV-P&cat=VCD]("http://www.geeks.com/details.asp?invtid=GF7600GS-128HDTV-P&cat=VCD")

Details on the web site are a little off...

It has ddr3 instead of ddr2.
It has a heatsink and fan instead of giant 2 slot heatsink.

Some other details...

You can use "gottadeal" for a coupon code and get 10% off.
gpu is clocked @ 500mhz
ddr3 is clocked @ 500mhz (1000mhz effective)
gpu is 80nm g73-b1 revision introduced last January 2007.

I got 400+ fps in Quake3 @ 1024x768 with all settings maxed.
Plays Enemy Territory : Quake Wars much smoother than my old ati x1300 pro

---

### Post by lakersforce on 2008-02-06
Im running dual monitor setup with nvidias TwinView.

I have made a script to launch etqw on a separate X server instance.

Problem number 1) When I start the xserver session etqw is running on the wrong preferred screen (i.e. #0 instead of #1). I could try and switch the screens on my gfx card, have not tried it but I doubt it will work. So how do I place the etqw screen on a specific place on my X screen?

Problem number 2) I get the best possible speed in my game when I run at 800x600. But my X server (for screen #1, which is the screen I prefer it to run on) is set at 1280x1024, so the game appears in a too small window. Instead of adjusting the game to the screen, I would prefer to adjust the screen to my game. How do I do that?

Thanks in advance.

(x-posting ftw)

---

### Post by Jinx-Wolf on 2008-02-07
I'm having the same problem as migla, however I have the Retail version of the game.

---

### Post by frodon on 2008-02-09
BTW, is the full game faster than the demo ?

I tried the latest demo today and i find the game a bit laggy (medium quality, 1280x1024). My specs are :
AMD 3700+ 2.2GHz
2Go DDR ram
XFX 7600GT 256Mb
Nvidia drivers from the repo.

Maybe i will buy the game but since i won't change my computer i'mtrying to know if what i have now will be enough to play ET:QW smoothly.

---

### Post by mb108 on 2008-02-09
The new demo was released at about the same time as the latest patch (mid-January-ish); I would assume the two are pretty much the same at this point.

Those specs aren't that bad, I've seen lower posted on the ETQW forums and they were claiming smooth gameplay. You might try low quality, or post to their forums asking how you can tweak your cfg files for better performance. Pretty sure there are some tricks out there (I haven't done much cfg stuff, sorry).

---

### Post by frodon on 2008-02-10
Ok thanks, i will play with cfg file then :)

---

### Post by Catalonian on 2008-02-18
Hey! 
Been playing QW for a while on my windows partition but since I only get into windows to play QW I thought it would be good to try it on ubuntu.

I chose installing without the dvd (copied all the files from windows partition). When I start the game, when the intro should start ("the strogg...souless etc"), the game crashes and I only see a 800x600 part of my desktop. I can't do anything, not even moving mouse. I've got to ctrl+alt+bkspace and login again.
Any suggestions?

thx!

---

### Post by Velociraptor on 2008-02-19
Did you download the Linux client, or are you trying to install from wine?

It's just weird that you say you get the intro movie; cos I don't get that with the Linux client (only on Windows).

The linux native client is here: [http://zerowing.idsoftware.com/linux/etqw/]("http://zerowing.idsoftware.com/linux/etqw/")

If you run it in a terminal, do you get any error messages? Have you tried turing off 3D desktop effects?

---

### Post by Catalonian on 2008-02-19
Oh, I didn't know the linux version didnt have an intro. I said game crashed before playing it btw.
I can't access the menu, game crashes before.

And yeh, I followed the instructions on this post, so I'm using the native version, not wine.

I have tried with desktop effects on and off, but I had the same result. I'll try to run it from terminal and see what errors do I get (when I get home that is :))

---

### Post by Catalonian on 2008-02-21
Hmmm, I wonder how can I see the error messages if the game crashes and makes the desktop get stuck. I've tried redirecting it to a file but nothing happened.

---

### Post by mb108 on 2008-02-21
Use Ctl+Alt+Backspace to quit out of your desktop/etc, then use Ctl+Alt+F1 to go to another virtual terminal. Login and run from that command line, let us know what it spits out.

---

### Post by Catalonian on 2008-02-23
Ok, I get a lot of warnings here.

WARNING: unknown string ID '#str_00111205'. I get a lot of them with different str_*.

I also get a lot of:
WARNING: mainmenu: 'mnufriendscontext' has no font set.

These ones seem the problematic since after a lot of them there's a segmentation fault (core dumped).

Does this help?

---

### Post by Envirotech on 2008-02-24
@Naegling

How did you get your script to work.  I cannot seem to get it to work from the menu launcher.  I can only get it to work if I run it in the terminal from the directory that it is located.  I would love to get this to work because then I would use it with all my games including Cedega.

Envirotech

Never mind.  Figures as soon as i post this I would find my own answer.  I got rid of the .sh at the end of my file name and set it launch as a application it launches as it is sepposed to.  Thank you for your script though.

---

### Post by Velociraptor on 2008-02-25
@Catalonian

You said you installed by copying the files from Windows; but did you ever try installing using the data from the DVD instead? I'm just guessing you might have not copied some files, or something. Maybe it's worth trying the DVD.

I saw a forum entry in German, [here]("http://www.ubuntu-forum.de/artikel/28788/kein-text-schrift-in-etqw-enemy-territory-quake-wars.html"), which had similar error messages. And that guy also installed by copying from Windows, solved by (translated):

> copy the "etqw/base/video" directory and "zpak_english000.pk4" to etqw/base/

Hope you get this working, ETQW rules on linux!

---

### Post by Catalonian on 2008-02-25
Oooh that made the trick!
Thanks a lot raptor! :D, maybe you want to add this to your guide mb108 :)

Damn, this runs a lot faster on linux :), any way to use anti alias?

Thx again :)

---

### Post by Velociraptor on 2008-02-25
Cool!

Huh, I don't run anti-aliasing cos my 6600gt is too slow. But it sounds like the option is disabled for linux; it should be (in ETQW) Options -> Settings -> Advanced -> Anti-Aliasing.

There's a discussion here, with some suggestions:
 [http://community.enemyterritory.com/forums/showthread.php?t=22434]("http://community.enemyterritory.com/forums/showthread.php?t=22434")

I think you can also set anti-aliasing in the "nvidia-settings" application.

Edit: I tried running ETQW in a terminal, which gave some anti-aliasing (for nvidia cards), as follows: 

> __GL_FSAA_MODE=4 /usr/local/games/etqw/etqw

---

### Post by Catalonian on 2008-02-25
Alright thanks! I'll take a look now :)
BTW, I've tried to open the console to load my .cfg but I'm not able to. 
I tried cntrl+alt+tilde but it doesn't work, maybe it has to do with my keyboard configuration?

---

### Post by Vadi on 2008-02-25
Does anti-aliasing improve visual performance much?

I've been pretty happy with it myself though so far, not sure if I should try breaking etqw :|

---

### Post by Velociraptor on 2008-02-27
I've got really nice anti-aliasing working using the ETQW console. :) I think it's equivalent in quality to the Windows install I had. Not only are the edges/lines smoother, but you get the semi-transparent rendering around the edges of leaves (esp. in Valley).

In the console I entered:

> seta r_multiSamples 4

Getting the console up was a bit tricky, I have a UK keyboard, and Ctrl+Alt+Tilda doesn't work. What worked was *first* pressing Ctrl+Alt, and then (while still holding Ctrl+Alt) press the top-left key (just below Esc.). This is ` for me.

I'm guessing that ETQW doesn't detect what keyboard layout you have, and assumes a [US keyboard]("http://www.redgrittybrick.org/terminals/win95us.gif").

Edit: I prefer without AA for the faster frame rate.

---

### Post by MrJokester on 2008-03-07
hi if enyone can help
this is the eror msg on my terminal 
> beni@beni:~$ /home/path/to/ETQW/etqw
ETQW 1.4.12247.12247  linux-x86 Jan  4 2008 13:52:05
found interface lo - loopback
found interface eth0 - 192.168.1.2/255.255.255.0
CPU: AMD CPU with MMX & 3DNow! & SSE & SSE2 & SSE3
ETQW using generic code for SIMD processing
enabled Flush-To-Zero mode
------ Initializing File System ------
Loaded pk4 /home/path/to/ETQW/base/game000.pk4 with checksum 0x1eefa237
Loaded pk4 /home/path/to/ETQW/base/game002.pk4 with checksum 0x5f707685
Loaded pk4 /home/path/to/ETQW/base/pak005.pk4 with checksum 0x5ccc7213
Loaded pk4 /home/path/to/ETQW/base/pak006.pk4 with checksum 0x9edf1b7d
Loaded pk4 /home/path/to/ETQW/base/pak007.pk4 with checksum 0x74a1a2f
Loaded pk4 /home/path/to/ETQW/base/zpak_english001.pk4 with checksum 0x6583cd8
Loaded pk4 /home/path/to/ETQW/base/zpak_english002.pk4 with checksum 0x8dc70e3d
Loaded pk4 /home/path/to/ETQW/base/zpak_french001.pk4 with checksum 0x3bd7a062
Loaded pk4 /home/path/to/ETQW/base/zpak_french002.pk4 with checksum 0x79287190
Loaded pk4 /home/path/to/ETQW/base/zpak_german001.pk4 with checksum 0xa694c3f1
Loaded pk4 /home/path/to/ETQW/base/zpak_german002.pk4 with checksum 0x64bee731
Loaded pk4 /home/path/to/ETQW/base/zpak_korean000.pk4 with checksum 0xd42c084
Loaded pk4 /home/path/to/ETQW/base/zpak_korean001.pk4 with checksum 0x4de6a4e7
Loaded pk4 /home/path/to/ETQW/base/zpak_korean002.pk4 with checksum 0x15d2c9af
Loaded pk4 /home/path/to/ETQW/base/zpak_polish001.pk4 with checksum 0x2575ff8e
Loaded pk4 /home/path/to/ETQW/base/zpak_polish002.pk4 with checksum 0x3ab92dd6
Loaded pk4 /home/path/to/ETQW/base/zpak_russian001.pk4 with checksum 0xf3e91581
Loaded pk4 /home/path/to/ETQW/base/zpak_russian002.pk4 with checksum 0x38b1a37c
Loaded pk4 /home/path/to/ETQW/base/zpak_spanish001.pk4 with checksum 0xd609566c
Loaded pk4 /home/path/to/ETQW/base/zpak_spanish002.pk4 with checksum 0xcf994ada
Current search path:
/home/beni/.etqwcl/base
/home/path/to/ETQW/base
/home/path/to/ETQW/base/zpak_spanish002.pk4 (119 files)
/home/path/to/ETQW/base/zpak_spanish001.pk4 (13 files)
/home/path/to/ETQW/base/zpak_russian002.pk4 (119 files)
/home/path/to/ETQW/base/zpak_russian001.pk4 (13 files)
/home/path/to/ETQW/base/zpak_polish002.pk4 (119 files)
/home/path/to/ETQW/base/zpak_polish001.pk4 (13 files)
/home/path/to/ETQW/base/zpak_korean002.pk4 (12 files)
/home/path/to/ETQW/base/zpak_korean001.pk4 (12 files)
/home/path/to/ETQW/base/zpak_korean000.pk4 (6 files)
/home/path/to/ETQW/base/zpak_german002.pk4 (119 files)
/home/path/to/ETQW/base/zpak_german001.pk4 (13 files)
/home/path/to/ETQW/base/zpak_french002.pk4 (119 files)
/home/path/to/ETQW/base/zpak_french001.pk4 (13 files)
/home/path/to/ETQW/base/zpak_english002.pk4 (117 files)
/home/path/to/ETQW/base/zpak_english001.pk4 (9 files)
/home/path/to/ETQW/base/pak007.pk4 (1510 files)
/home/path/to/ETQW/base/pak006.pk4 (3 files)
/home/path/to/ETQW/base/pak005.pk4 (2172 files)
/home/path/to/ETQW/base/game002.pk4 (3 files)
/home/path/to/ETQW/base/game000.pk4 (3 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
fs_basepath = /home/path/to/ETQW
fs_savepath = /home/beni/.etqwcl
fs_userpath = /home/beni/.etqwcl
fs_cdpath = /home/path/to/ETQW
fs_devpath = /home/beni/.etqwcl
0x0
[0x082e7e71]
[0x0819b5f9]
[0x0819e912]
[0x0819f242]
[0x0819f41e]
[0x083dcd6e]
[0xb7b78050]
[0x0804ca61]
********************
FATAL ERROR: Couldn't load fs.chk
********************
--------------- BSE Shutdown ----------------
---------------------------------------------
Shutting down SDL subsystem
idRenderSystem::Shutdown()
Sys_Error: Couldn't load fs.chk
beni@beni:~$ 

i dont know what is it
i have cpu amd athlon +3000
1GB kingmax superram
nvidia GF 8500 GT 256MB
ubuntu gutsy 32bit

---

### Post by Vadi on 2008-03-07
It looks like you installed it wrong (from googling "FATAL ERROR: Couldn't load fs.chk"). Try reinstalling it.

Btw, I noticed you have this - /home/path/to/ETQW/etqw. The /path/to/ETQW was just given as an example, I think you were supposed to replace it with whatever the real path is.

---

### Post by grimdeath on 2008-03-07
> **migla said:**
> Sometimes etqw drops out of full screen and then I can't control it. Nor can I control the desktop that has become visible. Sometimes the game does bounce back to fullscreen, but most of the time it doesn't.  (Same problem as [this guy ]("http://community.enemyterritory.com/forums/showpost.php?p=186864&postcount=118")has.)

ctrl-alt-F1 and then killing the process of the game (and then alt-F7, ofcourse) gets me in touch with the desktop again.

Anyone else have this problem and/or a solution?

(edit: I run the demo.)

Im having this same problem. Im running 7.10 with the linux demo client. Im am trying to figure out if this is a bug that is only present in the demo or if it will affect the retail game as well. I can play for most of the warm up section of the game and sometimes a little while during the main game but it always seems to bump me into a windowed mode after a while making me lose all mouse and keyboard input to the game, alt tab doesnt work and im left doing a control+alt+backspace. It would be nice to find a fix in the demo though as I figure this issue will more then likely carry over!

I was showing ubuntu to a friend over the weekend and he was pretty impressed till I got this issue mid-game lol

---

### Post by grimdeath on 2008-03-10
decided to edit the above post rather then doing a straight double post or creating a new thread on this subject..any help?

---

### Post by Vadi on 2008-03-10
That'll only happen when Compiz is on, and a pop-up or something comes along. With compiz off, the popup is ignored and the game doesn't go out of fullscreen.

Here's what I do (and recommend to you). Get Compiz Switch from here ([click]("http://forlong.blogage.de/article/pages/Compiz-Switch")). Install it, and drag it into the top panel so you've got it's little icon. When you click on it, it'll toggle compiz on/off.

So usually I just click on the etqw icon, then on the compiz-switch icon to turn compiz off. After I'm done, I click on the compiz switch icon again to turn on compiz.

---

### Post by grimdeath on 2008-03-10
sounds like a similar problem to what I had way back in the day with windows and windowblinds in one of the splinter cell games :D thank you sir that looks to be exactly what  I needed

---

### Post by tj.brewster on 2008-06-03
Is there any easier way to load this game???  I'm a X microshaft user. new to linux and learning every day. Kinda used to point and click installs. 
I really like herron and hope to continue with it just need an easier way to load this game for my son.

Thanks in advance.
TJ

---

### Post by Vadi on 2008-06-03
It should be quite easy, just double-click on it to start the installer. Let us know if you need any help.

And herron is a fish I think... ubuntu 8.04 codename is "hardy heron" which is a bird

---

### Post by tj.brewster on 2008-06-04
Sorry bout that....is my Linux noobness showing??  Thanks for the reply, but I tried that and this what I got.
:NOTICE: Initial Lua setup failed. Cannot continue.
[hit enter]"
Any information please dumb it down for me.  I'm still trying to get a handle on command line.  Only been ubuntuing for a week, but I gotta say it's levels above anything M$ has to offer. I only keep Win XP on my computer for "some" games.  Just wish I new my way around it better.

Thanks, TJ

---

### Post by Vadi on 2008-06-04
It looks like a corrupted install file. Try re-downloading, and preferably from a torrent (torrents are more reliable than normal downloads).

---

### Post by tj.brewster on 2008-06-05
Re-downloaded the file from Bit Torrent.  Install is normal until I get to the step where it asks for path. I put "/usr/local/games/ETQW/".I get an error "Failed to mkdir" When looking at the file system I don't appear to have permissions to write to that location.  What have I done wrong and how do I fix it.  

Thanks, TJ

---

### Post by Sleaka J on 2008-06-06
> **tj.brewster said:**
> Re-downloaded the file from Bit Torrent.  Install is normal until I get to the step where it asks for path. I put "/usr/local/games/ETQW/".I get an error "Failed to mkdir" When looking at the file system I don't appear to have permissions to write to that location.  What have I done wrong and how do I fix it.  

Thanks, TJ

You can do either 2 things.

1. Change the install path to your home directory (/home/<username>/etqw)
2. Use the command "chown" on the /usr/local/games directory to give yourself permission to write to it (That's what I did)

I wouldn't recommend using capital letters in the path name either.

---

### Post by Perfect Storm on 2008-06-06
> **tj.brewster said:**
> Re-downloaded the file from Bit Torrent.  Install is normal until I get to the step where it asks for path. I put "/usr/local/games/ETQW/".I get an error "Failed to mkdir" When looking at the file system I don't appear to have permissions to write to that location.  What have I done wrong and how do I fix it.  

Thanks, TJ

sudo infront if you want to install globally on your system.

Guide: [http://gaming.gwos.org/doku.php/guides:64bit:etqw](http://gaming.gwos.org/doku.php/guides:64bit:etqw)

Just ignore sudo aptitude install ia32-libs if you're using 32-bit

---

### Post by tj.brewster on 2008-06-06
Thanks AI that link explained it all.  Got it working and I learned a little about Command line.  My first major victory with Linux.  Maybe someday I can drop Windows all together.  I'm now a believer in Linux, this distro rocks.

TJ

---

### Post by ShmengeTravel on 2008-07-14
Does anybody know what this is about? :

----- Initializing Decls -----
Decompressing the global token cache...3560Kb
------------------------------
couldn't exec 'etqwconfig.cfg'
execing 'localization/english/defaultbinds.cfg'
couldn't exec 'etqwbinds.cfg'
couldn't exec 'autoexec.cfg'
Vendor: Device:
/proc/cpuinfo CPU frequency: 2000 MHz
parse /proc/cpuinfo for CPU information
4 logical, 1 physical CPU(s)
detecting video ram (set sys_videoRam on command line to override) ..
found XNVCtrl extension 1.17
Detected
 	1 2.00 GHz CPU
	3952 MB of System memory
	1024 MB of Video memory on an optimal video architecture

This system qualifies for Low quality.
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
Segmentation fault

and it ends there. It wont let me fire up the game. This is with the new 1.5 install. I tried turning off compiz, but it gave me the same error. Any ideas?

---

### Post by Rhubarb on 2008-09-21
In-case anyone wants to get pulseaudio working with ETQW (on Hardy), you need to create a file in your home directory called .asoundrc
```
gedit ~/.asoundrc
```
Then paste this into the file:
```
pcm.!default { type pulse } ctl.!default { type pulse }
```
Then save it.

Now all applications that want to use alsa will be re-directed to pulseaudio.

Happy fragging ;)

---

### Post by Swarms on 2008-09-23
Above didn't work for me. I would still have a 1 sec soundlag.
In another forum someone wrote it helped to launch with this command inside the game folder: ./etqw.x86 +set s_alsa_pcm plughw:0 +set s_numberOfSpeakers2

Question is, what command do I use for the launcher to make it work?

The location of the game is: /usr/local/games/etqw

---

### Post by Swarms on 2008-09-23
Nobody knows?

---

### Post by Perfect Storm on 2008-09-23
Patience young padawan ;)

Make a script is an option;

```
nano launch-ETQW.sh
```

add;

[b]#!/bin/bash

metacity --replace &
/usr/local/games/etqw/etqw.x86 +set s_alsa_pcm plughw:0 +set 
compiz --replace & [/b]

save [ctrl]+[o] and exit [ctrl]+[x]

```
chmod +x launch-ETQW.sh
```

Now you can run the script. I've added it to disable compiz while you play ETQW

---

### Post by Swarms on 2008-09-23
Thanks, that worked great. Fragging away now! :)

---

### Post by CuraHack on 2008-12-05
Is tare any way that I can install it manually, or to install it from a ISO image :oops:

---

### Post by PendragonUK on 2009-05-02
I have the game installed and it would appear to run, the problem is that I have two monitors and in full screen mode it stretches over both monitors.

The monitors are running in "Twin" mode.

---

### Post by PendragonUK on 2009-05-02
I have switched to "separate Xscreens" as suggested in another post. now ETQW starts in the wrong screen rez. can I specify the screen rez in the starting command line? or better still go back to twin view and start ETQW in windows mode?

Separate xscreen is weird! two mouse pointers and such, it's will take some getting used to...

---

### Post by Awareness on 2011-08-03
A couple of years later, but i just bought ETQW from steam and downloaded the game. Then I dowloaded ETQW-client-1.4-full.x86.run and installed in /home/me/games/ETWQfull

then cp every file from /home/me/games/ETWQfull to the ETQW folder from steam and then everything back to /home/me/games/ETWQfull

This is the error i get :S

any help? 

```
$ ./etqw.x86

ETQW 1.4.12247.12247  linux-x86 Jan  4 2008 13:52:05
found interface lo - loopback
found interface eth1 - 192.168.1.128/255.255.255.0
CPU: Intel CPU with MMX & SSE & SSE2 & SSE3
ETQW using generic code for SIMD processing
enabled Flush-To-Zero mode
------ Initializing File System ------
Loaded pk4 /home/me/games/ETQWfull/base/game000.pk4 with checksum 0x1eefa237
Loaded pk4 /home/me/games/ETQWfull/base/game001.pk4 with checksum 0xa02f1c18
Loaded pk4 /home/me/games/ETQWfull/base/game002.pk4 with checksum 0x5f707685
Loaded pk4 /home/me/games/ETQWfull/base/pak000.pk4 with checksum 0x442eb08b
Loaded pk4 /home/me/games/ETQWfull/base/pak001.pk4 with checksum 0x10e16e6
Loaded pk4 /home/me/games/ETQWfull/base/pak002.pk4 with checksum 0x8dbe7353
Loaded pk4 /home/me/games/ETQWfull/base/pak003.pk4 with checksum 0x99dfcabb
Loaded pk4 /home/me/games/ETQWfull/base/pak004.pk4 with checksum 0x7e49f838
Loaded pk4 /home/me/games/ETQWfull/base/pak005.pk4 with checksum 0x5ccc7213
Loaded pk4 /home/me/games/ETQWfull/base/pak006.pk4 with checksum 0x9edf1b7d
Loaded pk4 /home/me/games/ETQWfull/base/pak007.pk4 with checksum 0x74a1a2f
Loaded pk4 /home/me/games/ETQWfull/base/pak008.pk4 with checksum 0x71a93b80
Loaded pk4 /home/me/games/ETQWfull/base/zpak_english000.pk4 with checksum 0x977c7bd0
Loaded pk4 /home/me/games/ETQWfull/base/zpak_english001.pk4 with checksum 0x6583cd8
Loaded pk4 /home/me/games/ETQWfull/base/zpak_english002.pk4 with checksum 0x8dc70e3d
Loaded pk4 /home/me/games/ETQWfull/base/zpak_english003.pk4 with checksum 0xc2d7ed49
Loaded pk4 /home/me/games/ETQWfull/base/zpak_french001.pk4 with checksum 0x3bd7a062
Loaded pk4 /home/me/games/ETQWfull/base/zpak_french002.pk4 with checksum 0x79287190
Loaded pk4 /home/me/games/ETQWfull/base/zpak_german001.pk4 with checksum 0xa694c3f1
Loaded pk4 /home/me/games/ETQWfull/base/zpak_german002.pk4 with checksum 0x64bee731
Loaded pk4 /home/me/games/ETQWfull/base/zpak_korean000.pk4 with checksum 0xd42c084
Loaded pk4 /home/me/games/ETQWfull/base/zpak_korean001.pk4 with checksum 0x4de6a4e7
Loaded pk4 /home/me/games/ETQWfull/base/zpak_korean002.pk4 with checksum 0x15d2c9af
Loaded pk4 /home/me/games/ETQWfull/base/zpak_polish001.pk4 with checksum 0x2575ff8e
Loaded pk4 /home/me/games/ETQWfull/base/zpak_polish002.pk4 with checksum 0x3ab92dd6
Loaded pk4 /home/me/games/ETQWfull/base/zpak_russian001.pk4 with checksum 0xf3e91581
Loaded pk4 /home/me/games/ETQWfull/base/zpak_russian002.pk4 with checksum 0x38b1a37c
Loaded pk4 /home/me/games/ETQWfull/base/zpak_spanish001.pk4 with checksum 0xd609566c
Loaded pk4 /home/me/games/ETQWfull/base/zpak_spanish002.pk4 with checksum 0xcf994ada
Current search path:
/home/me/.etqwcl/base
/home/me/games/ETQWfull/base
/home/me/games/ETQWfull/base/zpak_spanish002.pk4 (119 files)
/home/me/games/ETQWfull/base/zpak_spanish001.pk4 (13 files)
/home/me/games/ETQWfull/base/zpak_russian002.pk4 (119 files)
/home/me/games/ETQWfull/base/zpak_russian001.pk4 (13 files)
/home/me/games/ETQWfull/base/zpak_polish002.pk4 (119 files)
/home/me/games/ETQWfull/base/zpak_polish001.pk4 (13 files)
/home/me/games/ETQWfull/base/zpak_korean002.pk4 (12 files)
/home/me/games/ETQWfull/base/zpak_korean001.pk4 (12 files)
/home/me/games/ETQWfull/base/zpak_korean000.pk4 (6 files)
/home/me/games/ETQWfull/base/zpak_german002.pk4 (119 files)
/home/me/games/ETQWfull/base/zpak_german001.pk4 (13 files)
/home/me/games/ETQWfull/base/zpak_french002.pk4 (119 files)
/home/me/games/ETQWfull/base/zpak_french001.pk4 (13 files)
/home/me/games/ETQWfull/base/zpak_english003.pk4 (7 files)
/home/me/games/ETQWfull/base/zpak_english002.pk4 (117 files)
/home/me/games/ETQWfull/base/zpak_english001.pk4 (9 files)
/home/me/games/ETQWfull/base/zpak_english000.pk4 (1018 files)
/home/me/games/ETQWfull/base/pak008.pk4 (1496 files)
/home/me/games/ETQWfull/base/pak007.pk4 (1510 files)
/home/me/games/ETQWfull/base/pak006.pk4 (3 files)
/home/me/games/ETQWfull/base/pak005.pk4 (2172 files)
/home/me/games/ETQWfull/base/pak004.pk4 (72 files)
/home/me/games/ETQWfull/base/pak003.pk4 (1133 files)
/home/me/games/ETQWfull/base/pak002.pk4 (1637 files)
/home/me/games/ETQWfull/base/pak001.pk4 (1067 files)
/home/me/games/ETQWfull/base/pak000.pk4 (9350 files)
/home/me/games/ETQWfull/base/game002.pk4 (3 files)
/home/me/games/ETQWfull/base/game001.pk4 (11 files)
/home/me/games/ETQWfull/base/game000.pk4 (3 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
----- Initializing Decls -----
Decompressing the global token cache...3566Kb
------------------------------
execing 'etqwconfig.cfg'
execing 'localization/english/defaultbinds.cfg'
execing 'etqwbinds.cfg'
couldn't exec 'autoexec.cfg'
Vendor: Device:
thread priority set to 1
couldn't exec '/home/me/.etqwcl/sdnet/al/base/autoexec.cfg'
Opening IP socket: localhost:-1
Failed to open server license code file for reading.
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
Desktop resolution: 1280x1024
SDL_ListModes:
1280x1024 1280x960 1152x864 1024x768 960x600 960x540 840x525 832x624 800x600 720x450 700x525 
680x384 640x480 512x384 400x300 320x240 
SDL_ListModes are currently ignored for resolution filtering. Set r_useSDLModes to 1 if you want it
8/8/8/8 RGBA bits, 24 depth bits, 8 stencil bits
no multisampling
vsync: off
------- Initializing renderSystem --------
----- R_InitOpenGL -----
...using GL_ARB_multitexture
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_non_power_of_two
...using GL_ARB_texture_compression
...using GL_EXT_texture_compression_s3tc
...using GL_EXT_texture_filter_anisotropic
   maxTextureAnisotropy: 16.000000
...using GL_1.4_texture_lod_bias
X..GL_EXT_shared_texture_palette not found
...using GL_EXT_texture3D
...using GL_ARB_texture_rectangle
X..GL_EXT_texture_rectangle not found
...using GL_EXT_stencil_wrap
...using GL_EXT_stencil_two_side
...using GL_ARB_vertex_buffer_object
...using GL_ARB_vertex_program
...using GL_ARB_fragment_program
...using GL_EXT_depth_bounds_test
...using GL_ARB_point_sprite
...using GL_ARB_occlusion_query
...using GL_EXT_framebuffer_object
...using GL_EXT_packed_depth_stencil
...using GL_EXT_blend_minmax
...using GL_ARB_multisample
...using GL_ARB_shader_objects
...using GL_ARB_vertex_shader
...using GL_ARB_fragment_shader
...using GL_ARB_fragment_program_shadow
...using GL_ARB_shadow
...using GL_ARB_depth_texture
...using GL_EXT_gpu_program_parameters
...using GL_EXT_timer_query
X..GL_GREMEDY_string_marker not found
...using GL_EXT_texture_compression_latc
---------- R_ARB2_Init ----------
Cg available.
---------------------------------
thread priority set to 2
using ARB_vertex_buffer_object memory
thread priority set to 2
renderSystem initialized.
--------------------------------------
72 strings read from localization/english/strings/bindings.lang
486 strings read from localization/english/strings/chat.lang
884 strings read from localization/english/strings/code.lang
2187 strings read from localization/english/strings/game.lang
3208 strings read from localization/english/strings/guis.lang
3384 strings read from localization/english/strings/lifestats.lang
3522 strings read from localization/english/strings/loadtips.lang
3861 strings read from localization/english/strings/locations.lang
4386 strings read from localization/english/strings/maps.lang
4453 strings read from localization/english/strings/tasks.lang
/proc/cpuinfo CPU frequency: 2400 MHz
Couldn't open journal files
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
------ Alsa Sound Initialization -----
dlopen(libasound.so.2)
asoundlib version: 1.0.24.1
opened Alsa PCM device default for playback
device buffer size: 5644 frames (22576 bytes)
allocated a mix buffer of 16384 bytes
--------------------------------------
-------- ALSA Microphone Init --------
device buffer size: 3292 frames (6584 bytes)
microphone initialized
--------------------------------------
initializating SDL Joysticks
initialized 0 controller(s)
-------- Initializing Session --------
----------------- BSE Init ------------------
--------- BSE Created Successfully ----------
session initialized
--------------------------------------
found DLL in pak file: /home/me/games/ETQWfull/base/game002.pk4/gamex86.so
copy gamex86.so to /home/me/.etqwcl/base/gamex86.so
game using generic code for SIMD processing
enabled Flush-To-Zero mode
--------- Initializing Game ----------
gamename: baseETQW-1
gamedate: Dec 13 2007
Initializing global UI namespaces
...23 namespaces
...240 properties
Initializing event system
...898 event definitions
Initializing class hierarchy
...163 classes, 395120 bytes for event callbacks
WARNING: Couldn't load sound 'video/intro_1024x512.theora', defaulting
WARNING: idDeclLocal::ParseLocal Failed to Parse decl 'video/intro' in file 'sounds/cinematics.sndshd' line 0
0xad653530
[0x082e7e71]
[0x081a114f]
[0xad651d27]
[0xadab449d]
[0xadafbd2e]
[0xada84e49]
[0xadab30fd]
[0xadb5efb3]
[0xadb7dc05]
[0xad6a1529]
[0xad676201]
[0x0819aef4]
[0x0819ed70]
[0x0819f242]
[0x0819f41e]
[0x083dcd6e]
[0xb730ce46]
[0x0804ca61]
********************
ERROR: Event 'onCVarChanged' could not find cvar 'g_aptWarning'
********************
===============================================
onCVarChanged
lstGameSettings_APT_Warning
sdUserInterfaceLocal::CreateEvents for gui 'mainmenu'
===============================================
------------ Game Shutdown -----------
Shutdown event system
--------------------------------------
--------------- BSE Shutdown ----------------
---------------------------------------------
Shutting down sound hardware
----------- Alsa Shutdown ------------
close mic pcm
close pcm
dlclose
--------------------------------------
Shutting down SDL subsystem
idRenderSystem::Shutdown()
WARNING: Leaked 1 renderWorlds
WARNING: Leaking font dinpro (39 references left)
Sys_Error: Error during initialization

```

---

