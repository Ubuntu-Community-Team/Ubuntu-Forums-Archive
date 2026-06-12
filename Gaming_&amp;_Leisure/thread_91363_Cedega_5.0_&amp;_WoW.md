---
title: "Cedega 5.0 &amp; WoW"
date: 2005-11-17
forum: Gaming &amp; Leisure
---

### Post by Grafster on 2005-11-17
Has anybody tried these two together?
Do they work?

Sometiems updated Cedega does bad things to WoW. On the other hand a new GUI would be nice.

Anybody tried it?
Did it work out?
Problems? (solutions you found?)

cheers!

---

### Post by Zodiac on 2005-11-17
Its funny but WoW is the single reason I will not switch to Ubuntu on my desktop.

Until it can be played easily and perfectly I just cannot make the switch.

---

### Post by themainecane on 2005-11-17
I've gotten WoW to run, and more smoothly than in Windows even, in various forms of Wine and Cedega. However, in Linux, I cannot get past the infamous "mouse bug" that has plagged WoW in Linux for several patches now. Argh. My lone reason for keeping Windows around... ick.

---

### Post by Zodiac on 2005-11-17
I know.... 

The second Wine can play WoW is the second I no longer use Windows...

---

### Post by cydizen on 2005-11-17
Hey guys, 

 I run WoW perfectly under Cedega 5 (and previous) with the mouse fix on my box and it runs great!! Infact, with Breezy, I am running TeamSpeak + WoW (including a few mods) with no problem.  How can I help you guys get going on it?  

Let me know if you need a config file etc...   Also, I have a fully working N52 Nostromo working for a sweet gaming experience.


Let me know,
Bruce

---

### Post by glaze on 2005-11-17
[QUOTE=Zodiac]I know.... 

The second Wine can play WoW is the second I no longer use Windows...[/QUOTE]

Wine runs WoW just fine. I have zero problems with it. What is your problem, maybe i can help?

---

### Post by brdweb on 2005-11-17
I had run WoW with cedega back in like 1.2 or 1.3 patch days, not long after Cedega 4 had come out. 

Now i'm trying to run it with Cedega 5 and the installer blinks up a window and disappears right away. All of the Cedega tests pass without a problem and it's an almost new breezy install.

---

### Post by themainecane on 2005-11-18
My latest attempt at WoW was with the newest version of WINE and WoW with the 1.8.3 patch. It runs smoothly (moreso than in Windows, heh!), but it makes the mouse act like all of the background objects are in front of the characters so I cannot target or click on anything in-game. I have heard of a few fixes or patches for the mousebug, but most were deigned solely for Gentoo or I wan unable to get them to work. I am fairly new with Linux, but getting better each day at working around with different things. Any help would be uch appreciated.

---

### Post by Grafster on 2005-11-18
The mouse thing is actually surprisingly easy to fix. 

There are two fixes listed in the transgaming forum stickies. 

The second one (which involved editing and command lines and sounds scary) worked for me. Its a one shot fix so I've forgotten what I did precisely but I basically followed the following instructions (maybe refering to the thread).

(And there was no framerate drop, at least that I noticed).

************************************
Originally Posted on transgaming forum as a sticky

2) This workaround should work for all users on all distros but may cause a frame rate drop.
Edit the World of WarCraft configuration file with your favorite text editor:
command line users: /home/USERNAME/.transgaming/config
Point2Play users: /home/USERNAME/.point2play/configuration_profiles/NAME_OF_WOW_CONFIG
Add the following section to the config file:
[AppDefaults\\wow.exe\\memory]
"MemoryLayoutOverride" = "0x10000000"
This change will remain persistent as long as you continue to use that configuration file for World of WarCraft. This change may need to be removed for future versions of Cedega.
**********

original post from <http://transgaming.org/forum/viewtopic.php?t=3149&sid=3b9dda464ccef1197439b36c5c1bc36c>
[edit= fixed link]

As the first thread in this post indicated I have -not- updated to cedega 5.0 yet so I can't verify. But it worked on the prior versions and reading other posters it sounds like it works for 5.0 as well.

---

### Post by ramba on 2005-11-18
WoW works well on my comp. I got the mouse issue fixed using the first step of the link below. I also made a script from it so it runs it automatically and starts WoW right away, no thanks for the p2p interface :J 

[http://transgaming.org/forum/viewtopic.php?t=3149]("http://transgaming.org/forum/viewtopic.php?t=3149")

I can post the script later here if you want to try it. (nah, I'll just post it anyway, as soon as I get home) ;)

Here it is...

```
#!/bin/bash
export WINEPRELOADER_SETVALEGACY="no" 
/usr/bin/cedega -run "Your wow folder in cedega" "your World of Warcraft icon's name in cedega" -use-pthreads Yes

```

You have to change the parts which say "Your wow folder in cedega" "your World of Warcraft icon's name in cedega" to ones in your cedega GUI. For example "Dot Transgaming" and "World of Warcraft".

Now save the file and name it what you want, it will be called later by this name. Then move the file in one of the directories seen when you write 

```
echo $PATH
```

I have put it in /usr/games/. Now bash knows where to look for the file and the script is ready. You can write ./wow in console  or make a desktop icon from it. The correct launcher command is "sh <your script's name here>", mine is "sh wow".

I included the -opengl flag in profiles so it isn't featured in the script.

Sorry about this noobish tutorial, it's my first :J

---

### Post by Saku on 2005-11-18
I just wish I actualy could get either to actualy compile from CVS or work correctly on my PC. :P (I followed two diffrent guides down to every singel detail.)

---

### Post by thegnark on 2005-11-18
[quote=Saku]I just wish I actualy could get either to actualy compile from CVS or work correctly on my PC. :P (I followed two diffrent guides down to every singel detail.)[/quote] 

You don't need Cedega to run WoW. I hope the below is fairly accurate. I did this last night and I'm at work now, so I can't verify everything. Please append as needed.

Install latest Wine (0.9.1). ([Instructions on how to add repositories]("http://www.winehq.org/site/download-deb"))
Mount each WoW installation CD and copy the contents to a single directory somewhere. (cp /media/cdrom/* ~/wowinstall)
*** Do this while doing above step ***
Download the latest major patch: [http://www.filemirrors.com/search.src?type=begins&file=wow-1.8.0&action=Find]("http://www.filemirrors.com/search.src?type=begins&file=wow-1.8.0&action=Find")(Make sure to grab the correct langauge)
Install Mozilla (wine mozilla-win32-1.7.7-installer.exe) [http://www.zentek-international.com/mirrors/mozilla/releases/mozilla1.7.7/mozilla-win32-1.7.7-installer.exe]("http://www.zentek-international.com/mirrors/mozilla/releases/mozilla1.7.7/mozilla-win32-1.7.7-installer.exe")
Install ActiveX for Mozilla (wine MozillaControl177.exe) [http://www.iol.ie/~locka/mozilla/MozillaControl177.exe]("http://www.iol.ie/%7Elocka/mozilla/MozillaControl177.exe")
DLL1: [http://www.dll-files.com/dllindex/dll-files.shtml?msvcp60]("http://www.dll-files.com/dllindex/dll-files.shtml?msvcp60") (unzip msvcp60.dll to ~/.wine/drive_c/windows/system/)
DLL2: [http://www.dll-files.com/dllindex/dll-files.shtml?mfc42]("http://www.dll-files.com/dllindex/dll-files.shtml?mfc42") (unzip mfc42.dll  to ~/.wine/drive_c/windows/system/)
*** End parallelism ***
cd ~/wowinstall
wine Installer.exe
cd [FONT=Arial,Helvetica,sans-serif]~/.wine/drive_c/Progam\ Files/World\ of\ Warcraft/[/FONT]
mv ~/Desktop/[FONT=Arial,Helvetica,sans-serif]wow-1.8.0-enus-patch.exe .
wine [/FONT][FONT=Arial,Helvetica,sans-serif]wow-1.8.0-enus-patch.exe[/FONT]
wine WoW.exe (about 3 times to get all the minor updates)
winecfg (set sound to OSS)
pico [FONT=Arial,Helvetica,sans-serif]~/.wine/drive_c/Progam\ Files/World\ of\ Warcraft/[/FONT]WTF/Config.wtf
add this line: SET SoundBufferSize "70"
nice -n 19 wine WoW.exe -opengl

Everything seems fine, except I CAN'T TARGET ANYTHING! There's a couple of "fixes" floating around, but I'm still searching.

Another problem I ran into was that before setting WoW to windowed mode, it would wack out my resolution and not fix it when it exited (running 2 monitors in 2560x1024). Turning on windowed mode fixed the problem.
I haven't actually played yet, just ran around Ironforge a bit.

---

### Post by Zodiac on 2005-11-18
Okay... see how many steps and extra stuff that is?

When it becomes, insert CD, install, play is when I will switch.

Sorry... Just. Can't. Do. It.

---

### Post by brdweb on 2005-11-18
Yea I was just able to install and run it with the mouse targeting problem last night as well. I didn't try any of the patches. Cedega 5 wouldn't even install so I'm happy at this point.

Also, what does the 'nice' command do? Does it give the wine process a higher priority?

---

### Post by thegnark on 2005-11-18
[quote=brdweb]Also, what does the 'nice' command do? Does it give the wine process a higher priority?[/quote]


man nice



**NAME**
       [nice]("http://seth.positivism.org/man.cgi/nice")([1]("http://seth.positivism.org/man.cgi/1/nice"),[2]("http://seth.positivism.org/man.cgi/2/nice")) - run a program with modified scheduling priority

**SYNOPSIS**
       **[nice]("http://seth.positivism.org/man.cgi/nice")([1]("http://seth.positivism.org/man.cgi/1/nice"),[2]("http://seth.positivism.org/man.cgi/2/nice")) **[OPTION] [COMMAND [ARG]...]

**DESCRIPTION**
       Run  COMMAND  with  an  adjusted scheduling priority.  With no COMMAND,
       print the current scheduling priority.  ADJUST is 10 by default.  Range
       goes from **-20 **(highest priority) to 19 (lowest)[.]("http://seth.positivism.org/man.cgi/1/builtins")

       **-n**, **--adjustment**=ADJUST
              increment priority by ADJUST first

       **--help **[display]("http://seth.positivism.org/man.cgi/1/display") this [help]("http://seth.positivism.org/man.cgi/1/builtins") and [exit]("http://seth.positivism.org/man.cgi/exit")([3]("http://seth.positivism.org/man.cgi/3/exit"),[n]("http://seth.positivism.org/man.cgi/n/exit"),[1 builtins]("http://seth.positivism.org/man.cgi/1/builtins"))

       **--version**
              output [version]("http://seth.positivism.org/man.cgi/version")([1]("http://seth.positivism.org/man.cgi/1/version"),[3]("http://seth.positivism.org/man.cgi/3/version"),[5]("http://seth.positivism.org/man.cgi/5/version")) information and [exit]("http://seth.positivism.org/man.cgi/exit")([3]("http://seth.positivism.org/man.cgi/3/exit"),[n]("http://seth.positivism.org/man.cgi/n/exit"),[1 builtins]("http://seth.positivism.org/man.cgi/1/builtins"))

**AUTHOR**
       Written by David MacKenzie.

**REPORTING BUGS**
       Report bugs to <bug-coreutils@gnu.org>[.]("http://seth.positivism.org/man.cgi/1/builtins")

**COPYRIGHT**
       Copyright © 2004 Free Software Foundation, Inc.
       This is [free]("http://seth.positivism.org/man.cgi/1/free") software; see the [source]("http://seth.positivism.org/man.cgi/n/source") [for]("http://seth.positivism.org/man.cgi/n/for") copying conditions.  There is
       NO warranty; not even [for]("http://seth.positivism.org/man.cgi/n/for") MERCHANTABILITY or FITNESS FOR  A  PARTICULAR
       PURPOSE.

**SEE ALSO**
       The  [full]("http://seth.positivism.org/man.cgi/4/full") documentation [for]("http://seth.positivism.org/man.cgi/n/for") **[nice]("http://seth.positivism.org/man.cgi/nice")([1]("http://seth.positivism.org/man.cgi/1/nice"),[2]("http://seth.positivism.org/man.cgi/2/nice")) **is maintained [as]("http://seth.positivism.org/man.cgi/1/as") a Texinfo manual.  If
       the **[info]("http://seth.positivism.org/man.cgi/info")([1]("http://seth.positivism.org/man.cgi/1/info"),[5]("http://seth.positivism.org/man.cgi/5/info"),[n]("http://seth.positivism.org/man.cgi/n/info")) **and **[nice]("http://seth.positivism.org/man.cgi/nice")([1]("http://seth.positivism.org/man.cgi/1/nice"),[2]("http://seth.positivism.org/man.cgi/2/nice")) **programs are properly installed  [at]("http://seth.positivism.org/man.cgi/1/at")  your  site,  the
       [command]("http://seth.positivism.org/man.cgi/1/builtins")

              **[info]("http://seth.positivism.org/man.cgi/info")([1]("http://seth.positivism.org/man.cgi/1/info"),[5]("http://seth.positivism.org/man.cgi/5/info"),[n]("http://seth.positivism.org/man.cgi/n/info")) coreutils [nice]("http://seth.positivism.org/man.cgi/nice")([1]("http://seth.positivism.org/man.cgi/1/nice"),[2]("http://seth.positivism.org/man.cgi/2/nice"))**

       should give you [access]("http://seth.positivism.org/man.cgi/access")([2]("http://seth.positivism.org/man.cgi/2/access"),[5]("http://seth.positivism.org/man.cgi/5/access")) to the [complete]("http://seth.positivism.org/man.cgi/1/builtins") manual.

---

### Post by thegnark on 2005-11-18
[quote=Zodiac]Okay... see how many steps and extra stuff that is?

When it becomes, insert CD, install, play is when I will switch.

Sorry... Just. Can't. Do. It.[/quote]

I suppose there are additional setup steps, but in the end, I'm $15 richer for not paying the inital Cedega subscription fee.

In the end what's the difference to run the game? Nothing really

---

### Post by SKLP on 2005-11-18
I'm playing WoW and using Ventrilo under the same Wine 0.9.1 install very nicely ;-)

thegnark: the patch you need to apply for clicking npcs to work is [http://polynomial-c.homelinux.net/pub/gentoo/portage/app-emulation/wine/files/wine-wow_fixes.patch](http://polynomial-c.homelinux.net/pub/gentoo/portage/app-emulation/wine/files/wine-wow_fixes.patch)
also, if you want to see the targeting circles similar stuff edit dlls/opengl32/opengl_norm.c and change glPolygonOffset( factor, units );
to glPolygonOffset( -factor, units ); .

Also, this is the config.wtf stuff i have:
```
SET SoundBufferSize "130"
SET SoundOutputSystem "1"
SET gxApi "OpenGL"
```

Works fine with me without nicing or anything... but YMMV

---

### Post by Donnut on 2005-11-18
Cedega is unnecessary, I use cedega, wine, and crossover office.  All these are based off wine and winehq will run anything if tweaked enough.

---

### Post by SKLP on 2005-11-19
see my howto if u wanna play wow ;-)

[https://wiki.ubuntu.com/WorldofWarcraftHowto](https://wiki.ubuntu.com/WorldofWarcraftHowto)

---

### Post by enaelis on 2008-11-20
I have personal issues with cedega, the people at trans gaming just took wine, added some stuff, and a copywright, then called it cedega. One of my favorite things about almost everything in linux is the fact that most of it is free and open source. cedega is the antithesis of free and open source.

---

