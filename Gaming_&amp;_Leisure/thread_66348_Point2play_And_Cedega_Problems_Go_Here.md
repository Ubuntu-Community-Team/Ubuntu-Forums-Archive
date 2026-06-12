---
title: "Point2play And Cedega Problems Go Here"
date: 2005-09-16
forum: Gaming &amp; Leisure
---

### Post by xbaez on 2005-09-16
So you have Ubuntu and want to play Windows problems a bit?
I have the latest version of Cedega and Point2Play and I'm willing to help anyone and I 'm really looking for others gamers help

I will really like to Play:
[list]
[*]Pro Evolution Soccer 5
[*]Fifa 2006
[*]GTA: San Andreas
[*]NHL 2006
[*]NBA Live 2006
[*]Sims 2 + Expansion Packs
[*]Need for Speed Titles
[*]Other EA Games + EA Sports titles
[/list]

I really hope we can make a usefull thread

---

### Post by xbaez on 2005-09-16
Ok I've been able to play:
Starcraft
Warcraft III

Right now I'm installing GTA: San Andreas

I install these titles on /Windows/D/Games

Therefore I will be able to install them on Windows as well, but my challenge is to play them via Ubuntu/Linux

I just recommend everybody to select "Use pthreads" to "Auto" while you install. I was unable to install GTA but now with that option I'm installing it

---

### Post by Kratos on 2005-09-16
I just barely installed cedega, and honestly, I'm lost...  I don't know what to do next... any help would rock...

Thanks

---

### Post by pinoyskull on 2005-09-16
[QUOTE=xbaez]So you have Ubuntu and want to play Windows problems a bit?
I have the latest version of Cedega and Point2Play and I'm willing to help anyone and I 'm really looking for others gamers help

I will really like to Play:
[list]
[*]Pro Evolution Soccer 5
[*]Fifa 2006
[*]GTA: San Andreas
[*]NHL 2006
[*]NBA Live 2006
[*]Sims 2 + Expansion Packs
[*]Need for Speed Titles
[*]Other EA Games + EA Sports titles
[/list]

I really hope we can make a usefull thread[/QUOTE]

dude, where can i download cedega debian package?

---

### Post by Perfect Storm on 2005-09-17
[QUOTE=pinoyskull]dude, where can i download cedega debian package?[/QUOTE]

Here: [http://www.transgaming.com/](http://www.transgaming.com/)

---

### Post by xbaez on 2005-09-17
dpkg --info cedega_4.4.1-1_i386.deb

 new debian package, version 2.0.
 size 7649960 bytes: control archive= 5265 bytes.
       0 bytes,     0 lines      conffiles
     465 bytes,    11 lines      control
   14722 bytes,   165 lines      md5sums
     135 bytes,     7 lines   *  postinst             #!/bin/sh
     132 bytes,     7 lines   *  postrm               #!/bin/sh
      32 bytes,     2 lines      shlibs
 Package: cedega
 Version: 4.4.1-1
 Section: games
 Priority: extra
 Architecture: i386
 Depends: libc6 (>= 2.2.4-4), libjpeg62, xlibmesa3 | libgl1, xlibs (>> 4.1.0), zlib1g (>= 1:1.1.4), zlib1g
 Installed-Size: 21768
 Maintainer: Daniel Koch <daniel@transgaming.com>
 Description: TransGaming Technologies' Windows game compatability layer.
  This package contains Cedega from TransGaming Technologies Inc which allows you
  to play Windows games on your Linux distribution.

dpkg --info point2play_2.0.3_i386.deb
 new debian package, version 2.0.
 size 12275412 bytes: control archive= 61156 bytes.
     109 bytes,     2 lines      conffiles
     347 bytes,    10 lines      control
  277689 bytes,  2822 lines      md5sums
     173 bytes,     5 lines   *  postinst             #!/bin/sh
     160 bytes,     5 lines   *  postrm               #!/bin/sh
 Package: point2play
 Version: 2.0.3
 Section: games
 Priority: optional
 Architecture: i386
 Depends: libc6 (>= 2.2.4-4), xlibmesa3 | libgl1, xlibs (>> 4.1.0), wget
 Installed-Size: 50696
 Maintainer: TransGaming Technologies <info@transgaming.com>
 Description: The official frontend for Cedega
  TransGaming Point2Play, the official frontend for Cedega.

You can either buy or download the CVS version
Here are some good pages that tell you how to do that:
[http://www.linux-gamers.net](http://www.linux-gamers.net)
[http://www.transgaming.org](http://www.transgaming.org) (this one costs $5 per month, minimum 3 months and includes support with their forums)
[http://transgaming.org/gamesdb](http://transgaming.org/gamesdb)

---

### Post by weasel fierce on 2005-09-17
Halflife runs well on my box, even a little smoother than windows.

Hearts of Iron runs without a hitch.

I installed Soldier of fortune (I was rummaging through my old games ;) ) and it looked absolutely awful with cedega

---

### Post by xbaez on 2005-09-18
It will be great if users can post the games that they've been able to play
I've been able to play only two games:

Warcraft III
Starcraft

I'm really trying to get EA Sports games work, but they don't seem to have much support at transgaming

---

### Post by seethru on 2005-09-18
[QUOTE=xbaez]It will be great if users can post the games that they've been able to play
I've been able to play only two games:

Warcraft III
Starcraft

I'm really trying to get EA Sports games work, but they don't seem to have much support at transgaming[/QUOTE]
 I've been able to install and play:

World of Warcraft
Warcraft 3
Max Payne 2
Half-Life 2 & CS:Source

---

### Post by xbaez on 2005-09-18
Has anybody been able to play the Need for Speed Series?
That will be awesome
Since transgaming.org gaming database is not that good, here is an unofficial WIKI that really tells you which games work and wich don't 

[http://digital-conquest.ath.cx/wiki/index.php/Main_Page](http://digital-conquest.ath.cx/wiki/index.php/Main_Page)

I'm going to try to install GTA San Andreas ;)

---

### Post by xbaez on 2005-09-18
Gran Theft Auto - GTA San Andreas
HOWTO install

Well at least this will allow you to install GTA
First of all I recommend you to add the 'exec' in the /etct/fstab
that way you'll be able to run video games from your Windows partitions, and then you can play them from Windows or Linux (even though playing them from Linux is our goal)

Then you can edit $HOME/.transgaming/config and add the Windows drive, for instance I added my Windows D Drive

This installation is VERY strange
In the console type
# cd /media/cdrom0
# cedega setup.exe
(if the installer fails, do this as many times as you need until it works)

In my computer it worked in the 5th attempt, sooner or later, it works

I'll update this posts if I can make the game actually run from Ubuntu

---

### Post by atad6 on 2005-09-18
atad6 is Offline:
Join Date: Sep 2005
Posts: 4 atad6 is on a distinguished road
	
Default cedega permission problem
hi, i was able to install cedega but when i go to launch an exe file i always get this error

Code:

wine: '/home/username/.transgaming/wineserver-ubuntu' is not owned by you



did i do something wrong on install? any help would be great!

EDIT: I tried to change ownership of the folder but I still have the same error

Thanks!

---

### Post by xbaez on 2005-09-18
Did you tried or did you changed it?
you need to go to console, 'su', then you become root

---

### Post by atad6 on 2005-09-18
yeah, i did that, i did sudo and then the command and changed the permissions and it still does not work for some reason. What group should it be set to?

Thanks!

---

### Post by seethru on 2005-09-18
[QUOTE=atad6]atad6 is Offline:
Join Date: Sep 2005
Posts: 4 atad6 is on a distinguished road
	
Default cedega permission problem
hi, i was able to install cedega but when i go to launch an exe file i always get this error

Code:

wine: '/home/username/.transgaming/wineserver-ubuntu' is not owned by you



did i do something wrong on install? any help would be great!

EDIT: I tried to change ownership of the folder but I still have the same error

Thanks![/QUOTE]
 set your username as the owner, and make sure you only have read access to it.

---

### Post by atad6 on 2005-09-18
i'm sorry, how would i go about doing that?

---

### Post by xbaez on 2005-09-18
Man you need to GOogle a bit and learn at least the basic linux commands in order to receive support

chown -vR yourusername:yourpassword /home/username/.transgaming*

---

### Post by xbaez on 2005-09-18
**GTA SAN ANDREAS WOKRS!!!**

I will take screenshots tomorrow, really, just try 
#cd /media/cdrom
# cedega setup.exe (as many times as you need, until you can use the installer)

I'm playing it with sound and everything seems fine, I installed it without Point2PLay but I already included it at Point2PLay ;)

---

### Post by claydoh on 2005-09-18
Has anyone visited Transgaming's [forums]("http://www.transgaming.org/forum/") or their [games database]("http://transgaming.org/gamesdb/") ?
With all the variety in hardware, there will be many hints and tips for a wide range of users and games.
I have noticed a fair number of Ubuntu users in the forums as well :), and I greatly recommmend taking a look over there to anyone having trouble with their favorite games.

---

### Post by atad6 on 2005-09-18
sorry, i was just a bit confused

anyway, if anyone would still like to help me, i tried to change the permissions, and it worked, but i'm still getting the same error. what could i be doing wrong

thanks again

---

### Post by Airpizza on 2005-09-18
i'm trying to run eve-online with cedega-cvs. I get the spash screen and then it crashes.

Heres the log

[email]mike@Mike-Ubuntu:~/.cvsc[/email]edega/drive_c/Program Files/EVE$ cvscedega eve.exe
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
err:font:ReadFontDir Can't open directory "/usr/X11R6/lib/X11/fonts/truetype/"
fixme:console:SetConsoleCtrlHandler (0x1012f25b,1) - no error checking or testing yet
fixme:thread:GetThreadTimes (0xfffffffe): stub
err:file:CreateFileA Couldn't open device 'CON'!
err:file:CreateFileA Couldn't open device 'CON'!
err:bitmap:X11DRV_DIB_CreateShmPixmap pitch mismatch in ShmPixmap creation
err:module:BUILTIN_LoadModule loaded .so but dll winealsa.drv still not found
fixme:thread:GetThreadTimes (0xfffffffe): stub
fixme:file:FindFirstChangeNotificationA this is not supported yet (non-trivial).fixme:file:FindFirstChangeNotificationA this is not supported yet (non-trivial).fixme:console:SetConsoleCtrlHandler (0x100f2350,1) - no error checking or testing yet
fixme:win32:PE_CreateModule Load Configuration directory ignored
fixme:win32:PE_CreateModule Load Configuration directory ignored
fixme:win32:PE_CreateModule Load Configuration directory ignored
err:x11drv:X11DRV_GLX_MakeCurrent failed to set OpenGL context
err:x11drv:X11DRV_GLX_ContextCreate error creating 3D context
(alot more of these cut outa the log)
err:x11drv:X11DRV_GLX_MakeCurrent failed to set OpenGL context
err:x11drv:X11DRV_GLX_ContextCreate error creating 3D context
err:x11drv:X11DRV_GLX_MakeCurrent failed to set OpenGL context
err:x11drv:X11DRV_GLX_ContextCreate error creating 3D context
err:x11drv:X11DRV_GLX_MakeCurrent failed to set OpenGL context

err:x11drv:X11DRV_GLX_ContextCreate error creating 3D context
fixme:win32:PE_CreateModule Load Configuration directory ignored
fixme:ver:GetVersionExA OSVERSIONINFOA is too large (possibly OSVERSIONINFOEXA)
fixme:thread:GetThreadTimes (0x00000290): stub

anyone have any idea whats goin on?

---

### Post by seethru on 2005-09-19
> **Airpizza]i'm trying to run eve-online with cedega-cvs. I get the spash screen and then it crashes.

Heres the log

[email]mike@Mike-Ubuntu:~/.cvsc[/email]edega/drive_c/Program Files/EVE$ cvscedega eve.exe
For language 'en' several language ids were found:
en_US - 0409 said:**
> 
 thats something I found w/ cvscedega also, opengl is hit and miss, so I broke down and paid for it.

[quote]sorry, i was just a bit confused

anyway, if anyone would still like to help me, i tried to change the permissions, and it worked, but i'm still getting the same error. what could i be doing wrong

thanks again

it's giving you the same error? that you don't own it, despite having set yourself as the owner? Right click on the folder and please make sure it doesn't say root is the owner.

---

### Post by atad6 on 2005-09-19
hi,

yes it does say that i own the file, i'm getting this error

```
wine: '/home/adam/.transgaming/wineserver-ubuntu' must not be accessible by other users
``` 

thanks again!

---

### Post by Airpizza on 2005-09-19
[QUOTE=atad6]hi,

yes it does say that i own the file, i'm getting this error

```
wine: '/home/adam/.transgaming/wineserver-ubuntu' must not be accessible by other users
``` 

thanks again![/QUOTE]

You have to set the permisions to that folder so only you can access it . Right click the folder > properties > Permissions > make sure only your user name has a check by it.

---

### Post by atad6 on 2005-09-19
That's the funny thing, the permissions do come up under my username (adam) and i still am getting that error.

---

### Post by orb_nsc on 2005-09-19
I've been playing Battlefield 1942 and Battlefield Vietnam with Cedega, and both run great... though it's impossible to play online on any server that has Punkbuster enabled.

I did try to install the Road to Rome and/or Secret Weapons of WWII expansion packs, but they don't seem to install, and it ends up being a waste of disk space.  Has anyone gotten these to work?  Cedega lets you install BF patches, but not the expansion packs apparently.

I also got MOHAA to work, though it has persistant sound problems that I haven't yet worked out.

I'm also using Cedega to give another try at Blade Runner, an adventure game from the late 90s that I never finished.  :)  Now that game runs perfectly.

---

### Post by xbaez on 2005-09-19
[QUOTE=claydoh]Has anyone visited Transgaming's [forums]("http://www.transgaming.org/forum/") or their [games database]("http://transgaming.org/gamesdb/") ?
With all the variety in hardware, there will be many hints and tips for a wide range of users and games.
I have noticed a fair number of Ubuntu users in the forums as well :), and I greatly recommmend taking a look over there to anyone having trouble with their favorite games.[/QUOTE]
 claydoh I really recommend you to visit the
Unofficial Transgaming Wiki wich is MUCH better than Transgamings database
[http://digital-conquest.ath.cx/wiki](http://digital-conquest.ath.cx/wiki)

All that Transgaming does is puts all the games that it cans, wether they work or not (check Fifa for instance, they list the game, but NOBODY has reported it to work). You might actually buy Cedega and then find out that Fifa was "listed"

For instance it helped me install Need for Speed Underground, I'm currently installing Need for Speed Underground 2 ;)

---

### Post by xbaez on 2005-09-19
[QUOTE=atad6]That's the funny thing, the permissions do come up under my username (adam) and i still am getting that error.[/QUOTE]
 why don't you just delete that folder and do everything from scratch?
I bet that's easier right?

---

### Post by mdozama on 2005-09-19
just came new to Ubuntu.

can we play online games like Gunbound and Ragnarok Online using cedega and point2play?

---

### Post by Weav on 2005-09-19
I was wondering how well these games and applications run? Are they basically the same speed as the Windows counterpart or do they need to be run in a windows emulated enviorment?

Thanks for any feedback.

---

### Post by seethru on 2005-09-19
[QUOTE=atad6]That's the funny thing, the permissions do come up under my username (adam) and i still am getting that error.[/QUOTE]
 are the checks ONLY by your name?

> I was wondering how well these games and applications run? Are they basically the same speed as the Windows counterpart or do they need to be run in a windows emulated enviorment?

Thanks for any feedback.

if I run WoW with -opengl it runs just as fast fps wise, and I have a much better ping.

---

### Post by Weav on 2005-09-19
[QUOTE=seethru]if I run WoW with -opengl it runs just as fast fps wise, and I have a much better ping.[/QUOTE]
thats pretty sweet was it really hard to isntall and configure? I'm more worried about having to change around files in each patch or worrying about upgrading certain files will screw it up. Has anyone had any painful or annoying problems with that? I just want it to be stable and not have to worry about it closing down or randomly shutting down while i'm in BG

Thanks

---

### Post by seethru on 2005-09-19
[QUOTE=Weav]thats pretty sweet was it really hard to isntall and configure? I'm more worried about having to change around files in each patch or worrying about upgrading certain files will screw it up. Has anyone had any painful or annoying problems with that? I just want it to be stable and not have to worry about it closing down or randomly shutting down while i'm in BG

Thanks[/QUOTE]
 I had problems up until I actually bought cedega and point2play, then all problems went away. Also, if you're running Breezy or the 2.6.12 kernel you don't have to worry about the mouse targetting not working, no work around is required.

If a patch ever makes it incompatible, transgaming is fairly quick about releasing a fix from my understanding.

---

### Post by lindyslack on 2005-09-19
Anarchy Online works awsome... Noticably less lag on Ubuntu then in Windoze - Only ran into a graphics issue when running in window mode instead of full screen but full screen works great. Running at 1280 x 1024... Getting 1389 fps w/ glxgears... Oh and yes I pay for Cedega / p2p... Think I will install HL2 next...

AMD Athlon64 2800+
ASUS K8N
2 Gig memory
256 Meg nVidia GeForce 6200 Turbo Cache

---

### Post by claydoh on 2005-09-20
[QUOTE=xbaez]claydoh I really recommend you to visit the
Unofficial Transgaming Wiki wich is MUCH better than Transgamings database
[http://digital-conquest.ath.cx/wiki]("http://digital-conquest.ath.cx/wiki")
[/QUOTE]

Yes, there are direct links to there from each game's page on Transgaming's database :)

---

### Post by seethru on 2005-09-20
[QUOTE=seethru]are the checks ONLY by your name?



if I run WoW with -opengl it runs just as fast fps wise, and I have a much better ping.[/QUOTE]
 I think my pc hates me, I come home and WoW is no longer working. Getting Error 132 :/

edit: nvm me, setting the window version to win98 fixed it

---

### Post by xbaez on 2005-09-20
[QUOTE=Weav]I was wondering how well these games and applications run? Are they basically the same speed as the Windows counterpart or do they need to be run in a windows emulated enviorment?

Thanks for any feedback.[/QUOTE]
 WEAV

Read my next post to see the games I've been able to play so far:

They run like in Windows, I played Need for Speed Underground in my computer's laptop, sending the game to the TV, with a Nvidia GeForce ToGo (16 MB of RAM)

So if that game runs in my laptops graphic card, I should say they run the same.

You can visit the Unofficial Transgaming Wiki to find out issues that the games have. Some games are not playable, but the ones that work, they work fine usually

---

### Post by xbaez on 2005-09-20
For people using Ubuntu and Nvidia I recommend you to backup the /etc/X11/xorg.conf file, and add this option in the "Driver" section
**Option          "NoLogo"                "true"**
THat way you'll always now if you're running xorg with Nvidia's drivers working ok.

For some reason, yesterday I was playing Need for Speed Underground 2, and the game freezed. I tried running it again without luck, I was in a hurry so I left. Today, the same thing happened. 

The **BEST ADVICE** when something like this happens is to do
Tools -> System Tests -> Run All tests

My Open GL tests were failing, so I noticed (I suppose via synaptic) that my xorg.conf file was changed the day before.

Since I seriously tried Cedega+Point2Play I've been able to play:

Need for Speed Underground
Need for Speed Underground 2
Grand Theft Auto San Andreas
Starcraft
Warcraft III

**I was also able to play NFS Underground on my laptop's Nvidia 16MB graphic card, while having a blank screen on my laptop and the game working on my TV**

Changing subjects, I am owner of a site called [www.gamingaccess.com](www.gamingaccess.com) and [www.socceraccess.com](www.socceraccess.com)
Will anyone be interested in reading articles about the games that I've been able to play, as well as submitting stories about yours?

I have been thinking in posting other files that are very valuable for me, like the /etc/X11/xorg.file that I have at my house. That file allows you to play games on your TV while having a second screen on your laptop. When you disconnect your TV, you run Ubuntu normally.  The advantage of this file is that it doesn't makes your Ubuntu slower because it doesn't generates TWO desktops (each one with it's own KDE/Gnome menu, icons...). It just makes the TV the first desktop, and the laptop/computer an extension of the first desktop

For instance you can launch Point2Play, drag it to the right of the screen until it appears in your laptop's desktop, and launch Need for Speed from there, and the game will appear on the TV! (full screen)

I've been wondering if you will like me to enable a **"Linux games"** sections at [www.gamingaccess.com](www.gamingaccess.com), and at my Download Zone "[downloads.gamingaccess.com](downloads.gamingaccess.com)"

I will also love to receive stories from games hard to install. Hear this one:
GTA San Andreas. It's not on the Unofficial Wiki and at transgaming it sais it works ok, but it doesn't
I discovered that the installation works around 1/5 of the times you try, so you just have to try, try, try... until the installer works. Apart from that issue, the game runs just fine, with my Niko AirFlo joystick autodetected ;)

And if there are cool 3D games that are not in Ubuntu (worms, Racer...) that have a "configure, make, make install" procedure, I can make some .debs for them ;)

---

### Post by xbaez on 2005-09-21
Hey folks
Until now this is my game list, they all work ok (except for NFS Underground 2 which I still need to configure my NyKO Airlo, it works well with my InterAct HammerHead FX)

Need for Speed Undergound
Need for Speed Undergound 2
GTA San Andreas
Warcraft III
Starcraft

I just finished installing NBA Live 2004 (allthough both Transgaming and the UnoFficial Wiki say that you can't install the game)

Let's see if I can make at least some EA Sports games run, that will be really neat!

---

### Post by krak on 2005-09-21
would be nice to run new fifa 06 when it will come out. but cedega has rubbish support for ati ble ble ble

has anyone manage to run GTA SA on ATI Radeon??
i get this error when trying to run GTA SA
mmtime pid=15587 tid=15596
X Error of failed request: BadValue (integer parameter out of range for operation)
Major opcode of failed request: 146 (ATIFGLRXDRI)
Minor opcode of failed request: 1 ()
Value in failed request: 0x4200005
Serial number of failed request: 342
Current serial number in output stream: 342
xbaez  can u post ur cedega config?

---

### Post by xbaez on 2005-09-21
**FOLKS I WAS ABLE TO PLAY NBA LIVE 2004!!!!**

I need to tweak the game a bit more because it runs very slow at the moment, but really I was able to play it with my NyKO AIRFLO, a game between La Lakers and the Pistons.

I guess that if I select Windows XP the game will run better, I really hope so. I've taken around 6 screenshtos of the installer, plus an in-game screenshot ;)

I REALLY hope that I can play Fifa 2004 and other EA Games!

---

### Post by krak on 2005-09-21
i get this error when trying to luch GTA SA 
mmtime pid=15587 tid=15596
X Error of failed request: BadValue (integer parameter out of range for operation)
Major opcode of failed request: 146 (ATIFGLRXDRI)
Minor opcode of failed request: 1 ()
Value in failed request: 0x4200005
Serial number of failed request: 342
Current serial number in output stream: 342

good news that u can run NBA its 1 big step to run fifa :)

---

### Post by xbaez on 2005-09-21
Are you trying to install it via Point2Play or did you managed to install the game?

Try using Point2Play
Select "auto" in pthreads, select "winxp" in the os, try messing with those options to see if you get it working

Try running it on a desktop as well

I was able to install NBA Live 2004 ONLY by selecting "WinXP" in the installer, Flash reported an INF error, but it said it was installed correctly, and the installer worked ;)

I was able to play a 20 Min match between Duncan (San Antonio) and Oneal (La Lakers)
I messed with the settings and was able to play at 1280x1024 with 32 bits, most of the options set to MAX, except shadows and Reflections (set to slow)

Game was excactly like in Windows ;)

I'm uploading 3 in-game screenshots right now, as well as 5-6 installation 

Stay tuned ;)

---

### Post by xbaez on 2005-09-21
**FIFA 2004 MAY RUN AS WELL!!!**
I am following the same procedure as I did to install NBA Live 2004, and currently the installer is working fine (no progress bar like in Need for Speed Underground)

Neither this game or NBA Live 2004 have good descriptions at Transgaming.org and/or the Unofficial Transgaming Wiki

I bet this will be great news for sports/Linux fans!

Right now I have taken 13 pictures explaining how to install Fifa 2004, step by step pictures that will hopefully allow easy installation of these games.

Expect a full article about these games soon, I already uploaded the NBA Live 2004 pictures, will post the link soon ;)

---

### Post by xbaez on 2005-09-21
For the people that want to see the **NBA Live 2004** screenshots (Point2Play installation screenshots + actual game screenshots) please go to this URL:

[http://screenshots.gamingaccess.com/category.php?cat=368](http://screenshots.gamingaccess.com/category.php?cat=368)

I've also placed a news (I'm very excited indeed) about the "discovery" that was made today (I Never ever expected to play an EA Sports game at Linux to be honest, maybe a few supported games, but never this!), you can read it here:

[http://www.gamingaccess.com/index.php?news_id=3416](http://www.gamingaccess.com/index.php?news_id=3416)

---

### Post by xbaez on 2005-09-21
**FIFA 2004 WORKS ON CEDEGA!!!**

[http://screenshots.gamingaccess.com/category.php?cat=369](http://screenshots.gamingaccess.com/category.php?cat=369)

Here you can see the Fifa 2004 installation and the actual game screenshots, I've just installed it using Cedega 4.4.1+Point2Play, the same way I did with NBA Live 2004

Here is the link to the detailed news article:
[http://www.gamingaccess.com/index.php?news_id=3421](http://www.gamingaccess.com/index.php?news_id=3421)

Please visit **[www.gamingaccess.com](www.gamingaccess.com)** to check the news + screenshots about Sports video games (mostly games from EA Sports and Konami) that I will try to install on Linux

My goal is to be able to play Fifa 2006 + Pro Evolution Soccer 4/5

---

### Post by krak on 2005-09-22
If u will run fifa 06 ill buy nvidia card :)

---

### Post by pinoyskull on 2005-09-22
i managed to install cedega 4.4.1-1, installed counterstrike 1.7, i managed to load it upto the menu, but when i try to create game, or just clicking on training, the game freezes, just black screen...

any ideas guys?

---

### Post by pinoyskull on 2005-09-22
this is the error

```

wine: Unhandled exception, starting debugger...
WineDbg starting on pid 1
No debug information in ELF '/usr/lib/transgaming_cedega//winex/bin/wine' (0x00000000)
Breakpoint 1 at 0x4000c780
No debug information in ELF '/usr/lib/transgaming_cedega//winex/pthread_lib/libntdll.so' (0x40018000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/pthread_lib/libwine.so' (0x4011d000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_unicode.so' (0x40132000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_port.so' (0x401f9000)
No debug information in ELF '/lib/tls/i686/cmov/libm.so.6' (0x40206000)
No debug information in ELF '/lib/tls/i686/cmov/libc.so.6' (0x40227000)
No debug information in ELF '/lib/tls/i686/cmov/libpthread.so.0' (0x40354000)
No debug information in ELF '/lib/tls/i686/cmov/libdl.so.2' (0x40365000)
No debug information in ELF '/lib/ld-linux.so.2' (0x40000000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libkernel32.so' (0x407f3000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libuser32.so' (0x4096b000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libgdi32.so' (0x40a93000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libadvapi32.so' (0x40b0a000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libddraw.so' (0x40b31000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwine_tsx11.so' (0x40b76000)
No debug information in ELF '/usr/X11R6/lib/libSM.so.6' (0x40b92000)
No debug information in ELF '/usr/X11R6/lib/libICE.so.6' (0x40b9b000)
No debug information in ELF '/usr/lib/libGL.so.1' (0x40bb3000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libGLU.so.1' (0x40c2b000)
No debug information in ELF '/usr/X11R6/lib/libXext.so.6' (0x40ce6000)
No debug information in ELF '/usr/X11R6/lib/libX11.so.6' (0x40cf3000)
No debug information in ELF '/usr/lib/libGLcore.so.1' (0x40db8000)
No debug information in ELF '/usr/lib/tls/libnvidia-tls.so.1' (0x41509000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwinmm.so' (0x415a3000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libcomdlg32.so' (0x415f9000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libshell32.so' (0x4165e000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libpng.so.3' (0x416da000)
No debug information in ELF '/usr/lib/libz.so.1' (0x41710000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libole32.so' (0x41721000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/librpcrt4.so' (0x41786000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libshlwapi.so' (0x417cc000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libcomctl32.so' (0x4180c000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwinspool.drv.so' (0x41891000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwsock32.so' (0x418a6000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libws2_32.so' (0x418b3000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libiphlpapi.so' (0x418cb000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwininet.so' (0x418da000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwineserver.so' (0x418f9000)
No debug information in ELF '/usr/lib/libfreetype.so.6' (0x4236a000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libx11drv.so' (0x423d7000)
No debug information in ELF '/usr/X11R6/lib/X11/locale/lib/common/xlcUTF8Load.so.2' (0x42457000)
No debug information in ELF '/usr/X11R6/lib/X11/locale/lib/common/ximcp.so.2' (0x42459000)
No debug information in ELF '/usr/lib/libXcursor.so.1' (0x4247f000)
No debug information in ELF '/usr/lib/libXrender.so.1' (0x42488000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libwineoss.drv.so' (0x42a50000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libmsacm32.so' (0x42a69000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libmsacm.drv.so' (0x42b90000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libmidimap.drv.so' (0x42b98000)
No debug information in ELF '/lib/libgcc_s.so.1' (0x458aa000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libmsvfw32.so' (0x46d07000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libversion.so' (0x46d18000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/liblz32.so' (0x46d22000)
No debug information in ELF '/usr/lib/transgaming_cedega//winex/lib/libopengl32.so' (0x48060000)
No debug information in 32bit DLL 'C:\Sierra\Counter-Strike\cstrike.exe' (0x00400000)
No debug information in 32bit DLL 'NTDLL.DLL' (0x40056000)
No debug information in 32bit DLL 'KERNEL32.DLL' (0x40826000)
No debug information in 32bit DLL 'C:\SIERRA\COUNTER-STRIKE\WONAUTH.DLL' (0x10000000)
No debug information in 32bit DLL 'C:\SIERRA\COUNTER-STRIKE\WONCRYPT.DLL' (0x40874000)
No debug information in 32bit DLL 'ADVAPI32.DLL' (0x40b1c000)
No debug information in 32bit DLL 'GDI32.DLL' (0x40ab2000)
No debug information in 32bit DLL 'USER32.DLL' (0x409a2000)
No debug information in 32bit DLL 'C:\SIERRA\COUNTER-STRIKE\VGUI.DLL' (0x40915000)
No debug information in 32bit DLL 'WINMM.DLL' (0x415b1000)
No debug information in 32bit DLL 'RPCRT4.DLL' (0x417a9000)
No debug information in 32bit DLL 'OLE32.DLL' (0x41740000)
No debug information in 32bit DLL 'SHLWAPI.DLL' (0x417e9000)
No debug information in 32bit DLL 'SHELL32.DLL' (0x41684000)
No debug information in 32bit DLL 'WINSPOOL.DRV' (0x41899000)
No debug information in 32bit DLL 'COMDLG32.DLL' (0x4160b000)
No debug information in 32bit DLL 'IPHLPAPI.DLL' (0x418d2000)
No debug information in 32bit DLL 'WS2_32.DLL' (0x418bb000)
No debug information in 32bit DLL 'WSOCK32.DLL' (0x418aa000)
No debug information in 32bit DLL 'WININET.DLL' (0x418e5000)
No debug information in 32bit DLL 'X11DRV.DLL' (0x423f6000)
No debug information in 32bit DLL 'MSACM32.DLL' (0x42a6e000)
No debug information in 32bit DLL 'WINEOSS.DRV' (0x42a53000)
No debug information in 32bit DLL 'MSACM.DRV' (0x42b93000)
No debug information in 32bit DLL 'MIDIMAP.DRV' (0x42b9a000)
No debug information in 32bit DLL 'C:\SIERRA\COUNTER-STRIKE\HL_RES.DLL' (0x17000000)
No debug information in 32bit DLL 'LZ32.DLL' (0x46d25000)
No debug information in 32bit DLL 'VERSION.DLL' (0x46d1b000)
No debug information in 32bit DLL 'MSVFW32.DLL' (0x46d0c000)
No debug information in 32bit DLL 'OPENGL32.DLL' (0x480a7000)
0003:: Bad stuff: client ignore setting select events for 0x90052df8 to 1
Unhandled exception: wait failed on critical section 0x40106f04 (NTDLL.DLL.NlsMbOemCodePageTag+0x6c6f in libntdll.so)
Unhandled exception: wait failed on critical section 0x40106f04 (NTDLL.DLL.NlsMbOemCodePageTag+0x6c6f in libntdll.so)
0003:: Bad stuff: client ignore setting select events for 0x90052df8 to 1

```

i hope you guys can help me

---

### Post by xbaez on 2005-09-22
Try running from Point2Play, try setting the OS to WinXP, Win98

did you tried the Unofficial Wiki and Transgaming.org games database?

How did you installed the game, what graphic card do you have?

Try finding another EXE for that file, it worked for me in Fifa 2004

---

### Post by JairunCaloth on 2005-09-22
I've got Star Wars Galaxies running better under cedega than it ever ran under windows. Need for speed underground I & II install and run, but have some serious graphics problems that have to be resolved by transgaming. I've tried and failed to get Xwing alliance and Xwing VS Tie working. I think the orriginal Xwing is supposed to work though.

---

### Post by seethru on 2005-09-22
[QUOTE=xbaez]**FIFA 2004 WORKS ON CEDEGA!!!**

[http://screenshots.gamingaccess.com/category.php?cat=369](http://screenshots.gamingaccess.com/category.php?cat=369)

Here you can see the Fifa 2004 installation and the actual game screenshots, I've just installed it using Cedega 4.4.1+Point2Play, the same way I did with NBA Live 2004

Here is the link to the detailed news article:
[http://www.gamingaccess.com/index.php?news_id=3421](http://www.gamingaccess.com/index.php?news_id=3421)

Please visit **[www.gamingaccess.com](www.gamingaccess.com)** to check the news + screenshots about Sports video games (mostly games from EA Sports and Konami) that I will try to install on Linux

My goal is to be able to play Fifa 2006 + Pro Evolution Soccer 4/5[/QUOTE]
 this is good news, because I'd LOVE to run Madden/NHL 06.

---

### Post by xbaez on 2005-09-22
*"but have some serious graphics problems that have to be resolved by transgaming"*
Which serious problems?
I run both games just fine

I will soon try NHL 2004, Nascar 2004.
Then I will try NBA Live 2005, Fifa 2005, Madden 2005
And I really, really hope to be able to play the 2006 titles as well

I will post more screenshots and updates on monday

---

### Post by kudu on 2005-09-23
Highway to the Reich works perfectly with Cedega. I installed Cedega, mozctl, and mscorefonts. I don't like or use Point2Play. :)

Kudu OUT

---

### Post by rollercoaster on 2005-09-23
i got error running ragnarok online...
[IMG]http://www.geocities.com/lunzelhot/Screenshot.png[/IMG] 

ive used hexed client so it wont get error in gameguard

---

### Post by pinoyskull on 2005-09-23
[QUOTE=xbaez]Try running from Point2Play, try setting the OS to WinXP, Win98

did you tried the Unofficial Wiki and Transgaming.org games database?

How did you installed the game, what graphic card do you have?

Try finding another EXE for that file, it worked for me in Fifa 2004[/QUOTE]

- tried setting different OSes
- i have a geforce 4 card, with nvidia-glx installed


here's a snippet of another error that i have

```

0003:: Bad stuff: client ignore setting select events for 0x900531b4 to 1
Unhandled exception: wait failed on critical section 0x40106f04 (NTDLL.DLL.NlsMbOemCodePageTag+0x6c6f in libntdll.so)
Unhandled exception: wait failed on critical section 0x40106f04 (NTDLL.DLL.NlsMbOemCodePageTag+0x6c6f in libntdll.so)
0003:: Bad stuff: client ignore setting select events for 0x900531b4 to 1
First chance exception: wait failed on critical section 0x40106f04 (NTDLL.DLL.NlsMbOemCodePageTag+0x6c6f in libntdll.so)
0003:: Bad stuff: client ignore setting select events for 0x900531b4 to 1
First chance exception: wait failed on critical section 0x40106f04 (NTDLL.DLL.NlsMbOemCodePageTag+0x6c6f in libntdll.so)
0003:: Bad stuff: client ignore setting select events for 0x900531b4 to 1
First chance exception: wait failed on critical section 0x40106f04 (NTDLL.DLL.NlsMbOemCodePageTag+0x6c6f in libntdll.so)
First chance exception: wait failed on critical section 0x40106f04 (NTDLL.DLL.NlsMbOemCodePageTag+0x6c6f in libntdll.so)
0003:: Bad stuff: client ignore setting select events for 0x900531b4 to 1
First chance exception: wait failed on critical section 0x40106f04 (NTDLL.DLL.NlsMbOemCodePageTag+0x6c6f in libntdll.so)
First chance exception: wait failed on critical section 0x40106f04 (NTDLL.DLL.NlsMbOemCodePageTag+0x6c6f in libntdll.so)
0003:: Bad stuff: client ignore setting select events for 0x900531b4 to 1
First chance exception: wait failed on critical section 0x40106f04 (NTDLL.DLL.NlsMbOemCodePageTag+0x6c6f in libntdll.so)
First chance exception: wait failed on critical section 0x40106f04 (NTDLL.DLL.NlsMbOemCodePageTag+0x6c6f in libntdll.so)
0003:: Bad stuff: client ignore setting select events for 0x900531b4 to 1
First chance exception: wait failed on critical section 0x40106f04 (NTDLL.DLL.NlsMbOemCodePageTag+0x6c6f in libntdll.so)
First chance exception: wait failed on critical section 0x40106f04 (NTDLL.DLL.NlsMbOemCodePageTag+0x6c6f in libntdll.so)
0003:: Bad stuff: client ignore setting select events for 0x900531b4 to 1
First chance exception: wait failed on critical section 0x40106f04 (NTDLL.DLL.NlsMbOemCodePageTag+0x6c6f in libntdll.so)
0003:: Bad stuff: client ignore setting select events for 0x900531b4 to 1
First chance exception: wait failed on critical section 0x40106f04 (NTDLL.DLL.NlsMbOemCodePageTag+0x6c6f in libntdll.so)
0003:: Bad stuff: client ignore setting select events for 0x900531b4 to 1
First chance exception: wait failed on critical section 0x40106f04 (NTDLL.DLL.NlsMbOemCodePageTag+0x6c6f in libntdll.so)
0003:: Bad stuff: client ignore setting select events for 0x900531b4 to 1
First chance exception: wait failed on critical section 0x40106f04 (NTDLL.DLL.NlsMbOemCodePageTag+0x6c6f in libntdll.so)
0003:: Bad stuff: client ignore setting select events for 0x900531b4 to 1

```
that's a looping message

---

### Post by xbaez on 2005-09-23
Is that game supported in the Unofficial Wiki and/or Transgaming?

---

### Post by pinoyskull on 2005-09-23
yes it is

---

### Post by krak on 2005-09-23
whats the web for unoficial wiki for cedega and unofical game db?

---

### Post by xbaez on 2005-09-23
Check this thread's previous pages forum as I've linked to it various times
The **BEST** thing to do is check Transgamings.org Games database and the Unofficial Transgaming Wiki, then decide if you want to try installing the game

I was able to install NBA Live 2004 and FIfa 2004, even though they were not listed there. However I got tips (such as the problem with the flash installation) there that were helpfull (I tried to install the flash player successfully by using winxp instead of win98 and that solved the problem)

---

### Post by xbaez on 2005-09-23
[QUOTE=pinoyskull]yes it is[/QUOTE]
 Can you give me the link?
maybe I could help you if you tell me what steps you followed
have you been able to play any other game?

---

### Post by seethru on 2005-09-23
decided to play with madden '06 this morning, so far no success with installing through point2play.

---

### Post by pinoyskull on 2005-09-24
out of frustration, i reinstalled my ubuntu, tried to install cedega and cstrike again, now it worked :), maybe i got some dependencies broken or not installed on my previous cedega.

now im trying to make cedega from cvs work

---

### Post by pinoyskull on 2005-09-24
installed cedega cvs just now, but when i try to install warcraft III ROC, i got this

```

fixme:cdrom:CDROM_GetIdeInterface not implemented for true scsi drives
/home/kira/bin/cvscedega: line 97: 10068 Segmentation fault      "$ConfigurePrefix/bin/$WineExecName" "$@"

```
then it died :(

any ideas?

---

### Post by krak on 2005-09-24
what ever 3d game ill try to run ill get this message
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  146 (ATIFGLRXDRI)
  Minor opcode of failed request:  1 ()
  Value in failed request:  0x3600007
  Serial number of failed request:  511
  Current serial number in output stream:  511

when i was running debian never had this error maybe its because debian uses Xfree86 and ubuntu uses x.org

those any one had sam problem and solve it.
i have radeon 9600 PRO

games which i have made to run are:
Painkiller
Tibia :) which runs on wine.

---

### Post by seethru on 2005-09-24
[QUOTE=krak]what ever 3d game ill try to run ill get this message
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  146 (ATIFGLRXDRI)
  Minor opcode of failed request:  1 ()
  Value in failed request:  0x3600007
  Serial number of failed request:  511
  Current serial number in output stream:  511

when i was running debian never had this error maybe its because debian uses Xfree86 and ubuntu uses x.org

those any one had sam problem and solve it.
i have radeon 9600 PRO

games which i have made to run are:
Painkiller
Tibia :) which runs on wine.[/QUOTE]
 glxgears works?

---

### Post by xbaez on 2005-09-24
[QUOTE=pinoyskull]out of frustration, i reinstalled my ubuntu, tried to install cedega and cstrike again, now it worked :), maybe i got some dependencies broken or not installed on my previous cedega.

now im trying to make cedega from cvs work[/QUOTE]
 It's always important to run the 3D tests in Point2Play, that will definitively tell you if your Xorg is configured for 3D Gaming

---

### Post by krak on 2005-09-25
krak@ubuntu:~$  glxgears
11660 frames in 5.0 seconds = 2332.000 FPS
14415 frames in 5.0 seconds = 2883.000 FPS
14418 frames in 5.0 seconds = 2883.600 FPS
14420 frames in 5.0 seconds = 2884.000 FPS
14420 frames in 5.0 seconds = 2884.000 FPS
14417 frames in 5.0 seconds = 2883.400 FPS

glxgeras works fine and i play ET/TCE which i find working faster than in windows

---

### Post by edemark on 2005-09-25
Hi all
So as this is for questions i have one. I am trying to run Emperor the battle for Dune. I got that far that I can istall the game wothout problem (i can do that in wine as well) but than when i try to run i get the following error message "Can not create 3d device" than it states that GAME.EXE terminated abnormally

Any good idea? 

thanks

---

### Post by krak on 2005-09-26
yeah! i have manage to run Lineage 2 but it runs really slow! but any way its big step for me :)

---

### Post by Weav on 2005-09-26
Could someone point me into to the website or instructions for getting these games to work? I don't mean how to get my ati driver working or anything like that, but exact almost noob instructions. I am trying to get WoW working and when i go to that unoficial site it just says after you have gotten it installed.

I want just basic instructions, i would really appreciate dumping windows to get WoW up and running with linux.

Thanks a lot and i'm sorry if someone has already asked that, i guess i'm just looking for a simplified version.

---

### Post by seethru on 2005-09-26
cedega, cvscedega?

---

### Post by Weav on 2005-09-26
[QUOTE=seethru]cedega, cvscedega?[/QUOTE]
I'm really not sure whatever is more reliable or works great.

---

### Post by seethru on 2005-09-26
[QUOTE=Weav]I'm really not sure whatever is more reliable or works great.[/QUOTE]

I use Cedega, however it costs money. $15 for 3 months of access to Transgaming.com. Works like a charm, infact I get a better ping and same, if not better, fps. If you're relatively new to linux like I was/am spend the $15. You'll get precompiled debian packages for cedega and point2play.

If you go ahead and buy it, only download the point2play deb, install it, and it will install everything you need for you.

---

### Post by JairunCaloth on 2005-09-26
[QUOTE=xbaez]*"but have some serious graphics problems that have to be resolved by transgaming"*
Which serious problems?
I run both games just fine

I will soon try NHL 2004, Nascar 2004.
Then I will try NBA Live 2005, Fifa 2005, Madden 2005
And I really, really hope to be able to play the 2006 titles as well

I will post more screenshots and updates on monday[/QUOTE]

I would be really interested in seeing how you have the NFSU games configured, I have the games installed and working, but I get horrible graphics and terrible framerates. Everyone else I've talked to have the same problems as me. So whatever magic you worked to make these games work properly, I would love to get mine going too.

---

### Post by krak on 2005-09-27
yeah xbaez please post your cedega config :)

---

### Post by xbaez on 2005-09-27
[QUOTE=edemark]Hi all
So as this is for questions i have one. I am trying to run Emperor the battle for Dune. I got that far that I can istall the game wothout problem (i can do that in wine as well) but than when i try to run i get the following error message "Can not create 3d device" than it states that GAME.EXE terminated abnormally

Any good idea? 

thanks[/QUOTE]

Try playing with another EXE

Folks I've been able to play various games nows, most of them with different EXE files that the ones that came with the CDs

---

### Post by xbaez on 2005-09-27
cvscedega doesn't supports copy protected games
cedega + point2play is always a better option allthought it should be around the same

---

### Post by xbaez on 2005-09-27
[QUOTE=JairunCaloth]I would be really interested in seeing how you have the NFSU games configured, I have the games installed and working, but I get horrible graphics and terrible framerates. Everyone else I've talked to have the same problems as me. So whatever magic you worked to make these games work properly, I would love to get mine going too.[/QUOTE]
I've even managed to play Need For Speed Underground with my 16 Nvidia toGo Laptop, displaying the game at 1024x728 with my Toshiba (only after pressing CTRL+ALT+F1 and then CNTRL+ALT+F7)

I've been also able to play the game on my TV while displaying Point2Play on my laptop

If you want I could post the configurations for ALL the games that I've been able to play (without any major issue, they all play well)
**NFL 2004**
**NBA Live 2004**
**Fifa 2004**
**GTA San Andreas**
**Need for Speed Underground**
**Warcraft III**
**Starcraft**
**Fifa 2005 (game runs incredibly slow)**
I will post links to the Madden NFL 2004 screenshots in my next post

---

### Post by xbaez on 2005-09-27
**MADDEN NFL 2004 works on Linux!**
[http://screenshots.gamingaccess.com/category.php?cat=376](http://screenshots.gamingaccess.com/category.php?cat=376)
There are the screenshots for Madden NFL 2004. What I've tried to do with these screenshots is to make a graphical HOWTO, I've managed to install and play without any troubles these 2004 EA title: NBA Live, Madden NFL and FIFA. I will buy NHL soon in order to try that one as well
The coolest thing about Madden NFL 2004 is that it runs GREAT (even plays my MP3 player collection)

The good news for the 2005 series is that FIFA 2005 was playable, however the game was way too slow, and it seems like it doesn't recognizes the controllers (neither keyboard) during the game so basically all that you can do is watch the slow montion Fifa 2005
Anyway here are the screenshots:
[http://screenshots.gamingaccess.com/category.php?cat=375](http://screenshots.gamingaccess.com/category.php?cat=375)

I will really appreciate if somebody else could get these (EA Sports 2005 titles) games working to see if they were able to play it. My Madden NFL 2005 CD is scratched so I didn't passed the installation process.

Changing subjects I was THIS close to play Prince of Persia: Warrior Within and Sands of Time. The game detects my video card (Nvidia GeForce FX 5200) as "Direct 3D Hal" so I am able to enter the game, hear the sounds, and I can't see anything (basically I can play the game without video, not much of a use)

I also tried WWE RAW but the videos run too slow.

I'm thinking in manking a web page with screenshots + downloads of all these games, so that you can save time installing games that work and avoid loosing time installing games that don't work (WWE Raw, Prince of Persia...)

Will anyone be interested?
I install my game on
D:\Games\Game Company\Game Title

Therefore I can play these games in either Windows XP or in Linux. Of course that there are some games that I can only play in Windows (Prince of Persia...)

Does anybody knows how can I create a graphical installer for this? Is anyone interested? The installer should basically ask you: "Were do you want to install the game?" and then change \Windows\D\Games\Game Company\... to the folder that you chossed.

I don't see that many people interested in these configurations in order to publish that
I may just post the configurations, and then you might open the system.reg and user.reg files in Kate, and replace "\Windows\D\Games\Game Company\Game Title" with the path of your installation.

I'm going to try UEFA Euro 2004 now

---

### Post by Tad030 on 2005-09-29
i'm having a very odd problem with sim city 4.  the game seemingly installs ok, but when i access transgaming drive/program files there is no maxis or sim city file folder to be found.  

what is even more odd is that when i mount sc 4 through point 2 play, the game plays just fine.  the main issue i'm having is that since i cannot locate where p2p actually installed sc4 on my system, i cannot install the rush hour expansion pack.  the game just isn't the same without the expansion pack.  

anyone else experience this?  suggestions?

---

### Post by xbaez on 2005-09-29
[QUOTE=Tad030]i'm having a very odd problem with sim city 4.  the game seemingly installs ok, but when i access transgaming drive/program files there is no maxis or sim city file folder to be found.  

what is even more odd is that when i mount sc 4 through point 2 play, the game plays just fine.  the main issue i'm having is that since i cannot locate where p2p actually installed sc4 on my system, i cannot install the rush hour expansion pack.  the game just isn't the same without the expansion pack.  

anyone else experience this?  suggestions?[/QUOTE]
You need to go to
$HOME/.poin2play

there you will be able to see "Sim City 4" (or the name that you used to install it with Point2Play)

That way you'll have different config files.. for each game

/usr/lib/transgaming_point2play/default_configuration_profiles/
In that folder you'll find the default profiles

---

### Post by xbaez on 2005-09-29
I've changed by configuration_profiles to the following:

**/usr/lib/transgaming_point2play/default_configuration_profiles/config.cedega_4.4.1**

[Drive C]
"Path" = "@C_DRIVE@"
"Type" = "hd"
"Label" = "Dos Drive"
"Filesystem" = "win95"

[b]
[Drive D]
"Path" = "/Windows/D"
"Type" = "hd"
"Label" = "Windows D"
"Filesystem" = "win95"
[/b]

[Drive E]
"Path" = "/tmp"
"Type" = "hd"
"Label" = "tmp"
"Filesystem" = "win95"

[Drive X]
"Path" = "${HOME}"
"Type" = "hd"
"Label" = "My Home"
"Filesystem" = "win95"

[Drive Z]
"Path" = "/"
"Type" = "hd"
"Label" = "root"
"Filesystem" = "win95"

That way when I install a game I can install my Windows partition (grep from /etc/fstab)
/dev/hda5       /Windows/D      vfat    defaults,umask=000,dmask=000,uid=1000,gid=1000,rw,exec   0       0

Then when I use Poin2Play, I select "install", I enter a new title for the game, and then I can select drive "D" (which is my read-write Fat 32 100GB+ drive)

By doing that I can play games in both linux and windows, or at least I can run/install them in Windows and then try to run them from Linux

---

### Post by Tad030 on 2005-09-29
[QUOTE=xbaez]You need to go to
$HOME/.poin2play

there you will be able to see "Sim City 4" (or the name that you used to install it with Point2Play)

That way you'll have different config files.. for each game

/usr/lib/transgaming_point2play/default_configuration_profiles/
In that folder you'll find the default profiles[/QUOTE]

you rock.  that totally worked.  thank you. 

i'm still confused though as to why when i follow the link to my transgaming drive that civ3 conquests show up, but sim city does not.  i'm still somewhat new to cedega, so i'm sorry if this is a totally boneheaded newbie question.  :)

thanks again!

---

### Post by xbaez on 2005-10-01
Ok that will be
$HOME/.point2play/civ3
$HOME/.point2play/sim_city (or somethng like that)
**HERE IS A TIP FOR EVERYONE**
If you install a game on cedega (for install I was able to install GTA San Andreas from the konsole, using cedega, and not using point2play) you can creat a folder called $HOME/.point2play/GTA_San_Andreas

Make sure you edit the config file so that it will include 
[Drive C]
"Path" = "@C_DRIVE@"
"Type" = "hd"
"Label" = "Dos Drive"
"Filesystem" = "win95"
Then open up point2play and there you go, you can launch your cedega installed game from point2play and remove the $HOME/.transgaming folder

From what I think cedega should be used as an alternative way to install ways, when you manage to install one, then you can "transfer" it to point2play

---

### Post by Jerrac on 2005-10-01
I just installed Cedega. It seems to work just fine, but the one game I have installed so far has no sound. What is going on? The sound tests it has in the config say they failed... How do I get it working?

---

### Post by xbaez on 2005-10-01
[QUOTE=Jerrac]I just installed Cedega. It seems to work just fine, but the one game I have installed so far has no sound. What is going on? The sound tests it has in the config say they failed... How do I get it working?[/QUOTE]
What game was it? Did you checked the unofficial Transgaming wiki?
Are you using KDE or Gnome?

You can try to search this forum for "sounds" + gnome, I remember there is a usefull thread that explains you some alsa configs in order to hear sounds at the same time (kshowmail+amarok+gaim... for example)

What I do before running a game is I close amarok, and if the game still has no sound, I type this at the konsole "killall -v artsd", "killall -v esd" (depens if you use arts or esd, both of them can be running actually - for example I've used artsd but in gaim I've used ESD)

That should do the trick

---

### Post by seethru on 2005-10-01
[QUOTE=xbaez]What game was it? Did you checked the unofficial Transgaming wiki?
Are you using KDE or Gnome?

You can try to search this forum for "sounds" + gnome, I remember there is a usefull thread that explains you some alsa configs in order to hear sounds at the same time (kshowmail+amarok+gaim... for example)

What I do before running a game is I close amarok, and if the game still has no sound, I type this at the konsole "killall -v artsd", "killall -v esd" (depens if you use arts or esd, both of them can be running actually - for example I've used artsd but in gaim I've used ESD)

That should do the trick[/QUOTE]

also, post your asound.conf file, I can give you an idea to get your sound working then.

---

### Post by Jerrac on 2005-10-01
Ok, I will do that search. I intalled Baldurs Gate 2. Where is the transgaming wiki? I couldn't find it on google...

I am using gnome, but I installed amarok and kopete, so I have some of the kde stuff as well.

I'll try those killall commands in a bit.

Where is my asound.conf file? :D

---

### Post by seethru on 2005-10-01
[QUOTE=Jerrac]Ok, I will do that search. I intalled Baldurs Gate 2. Where is the transgaming wiki? I couldn't find it on google...

I am using gnome, but I installed amarok and kopete, so I have some of the kde stuff as well.

I'll try those killall commands in a bit.

Where is my asound.conf file? :D[/QUOTE]

/etc/asound.conf

but considering you didn't know that, I'll assume you've never touched it.

With that said, are you using point2play? If yes, edit your profile, click on audio, and use Alsa and make sure both are set to "hw"

---

### Post by Duncan_Idaho on 2005-10-02
does anyone has managed to make run ragnarok online with cedega??
I dunno why i can't make in run ToT

---

### Post by xbaez on 2005-10-02
ok for the people having sound problems, here is a usefull post:
[http://www.ubuntuforums.org/showthread.php?t=32063](http://www.ubuntuforums.org/showthread.php?t=32063)

I used other post though, I can't find it now but it was very similar to this

If you still have problems, you can close amarok, gaim, and enter
#killall -v esd
#killall -v artsd
Then play the game

I have been unable to play a game while listening to amarok for example

---

### Post by seethru on 2005-10-03
[QUOTE=Duncan_Idaho]does anyone has managed to make run ragnarok online with cedega??
I dunno why i can't make in run ToT[/QUOTE]
GameGuard is the reason, you can thank the developers for including it like I thanked NCSoft for including it in Lineage 2. By discontinuing your subscription.

---

### Post by Duncan_Idaho on 2005-10-03
[QUOTE=seethru]GameGuard is the reason, you can thank the developers for including it like I thanked NCSoft for including it in Lineage 2. By discontinuing your subscription.[/QUOTE]

so, gameguard is not letting me play tru cedega or something?
I don't get it, can you explain yourself a little bit please?

---

### Post by seethru on 2005-10-03
GameGuard won't run in cedega, and since GameGuard isn't running the game won't run.

---

### Post by Duncan_Idaho on 2005-10-04
thanx for the info
so, it's completely imposible tu run it tru cedega?
and with wine?:confused:

---

### Post by seethru on 2005-10-04
Thats correct, and a google search actually reveals that there are unpatched vulnerabilities in GameGuard which is possibly partly why TG isn't in a big rush to get it working, so you can thank the developers for including a poorly written piece of software with their game.

---

### Post by geniium on 2005-11-21
Did anyone manage to run Pro Evolution Soccer 5? Damn I'm having hard times to install it.

---

### Post by xbaez on 2005-11-22
I would LOVE to play Pro Evolution Soccer 5 on Cedega, please message me if you are able to do that!

From what I understand, Pro Evolution Soccer 5 needs the 'dxdiag' to run, if you are able to run that program under cedega, then you should be able to run the game in linux (if the EXE runs) since the problems with Pro Evolution Soccer 3 were that the game worked but the keyboards or joysticks weren't supported.

I read that from other forum, I haven't been able to install it myself.

---

### Post by giany911 on 2005-11-29
Well xbaez if u can help me get  GTA San Andreas work i would like to know how, cause right now im stuck. With wine i get a error saying i dont hv a sound card installed and with cedega the game starts but crashes right before the game menu is loaded.

---

### Post by xbaez on 2005-11-29
I just tried the installation like 10 times (from the console) until I didn't received an error when the installer starts.

Then the installer runs fine, the game works fine too

---

### Post by Fallom on 2006-06-16
I'm trying to install Baldur's Gate 2, and when it asks for CD3 and I put it in the drive it says it can't find the files it needs. When I look at the mounted cd in File Browser it looks empty. What's going on?

---

### Post by danny0085 on 2008-04-04
Here I give you a link with a useful tip

[http://tips-debian.blogspot.com/2008/04/cedega-60.html]("http://tips-debian.blogspot.com/2008/04/cedega-60.html")

---

