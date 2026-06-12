---
title: "Wine"
date: 2005-06-19
forum: Desktop Environments
---

### Post by Prudentissimus on 2005-06-19
How do I install Wine?

Do I download the SOURCE(binary)? Or must I download a *.deb file?

Can Utubun setup files from SOURCE(binary)? I'm a noob, and I donno anything.

---

### Post by Xe0n on 2005-06-19
you can use Synaptic to install wine and make things a lot easier for yourself :)

---

### Post by josephwalter on 2005-06-20
Prudentissimus, I installed wine using Synaptic Package Manager, but I'm unsure of the next step. I'm studying the configuration and use of wine, although I can't find the "config" configuration file - the one documented at winehq.com - because I installed wine from from a package rather than from source code. I'm uncertain how to run wine or install the windows program.

I'm still reading up on this, but I'd love to know if you have made any progress on your wine quest.

---

### Post by psychicdragon on 2005-06-20
Install the winetools package and then run it. It's a graphical setup for wine, really simple.

---

### Post by Karl S. on 2005-06-21
Check the Wine/CVS thread at the end. There's been serious problems with installing Explorer through Winetools. I've tried it with the trial version of Crossover Office, too, and it still doesn't work.

So, if you're able to get Wine working, let us know.

---

### Post by az on 2005-06-21
[QUOTE=Karl S.]Check the Wine/CVS thread at the end. There's been serious problems with installing Explorer through Winetools. I've tried it with the trial version of Crossover Office, too, and it still doesn't work.

So, if you're able to get Wine working, let us know.[/QUOTE]


Hmmm..  You can get that done with the version in Hoary.  You just need to get winetools from the backports.

Install wine, libwine wine-utils from Universe and winetools from backports.  Run winetools and follow the setup menu.

So, you do not need to install anything from source...  Just use synaptic.

---

### Post by Karl S. on 2005-06-21
[QUOTE=azz]Hmmm..  You can get that done with the version in Hoary.  You just need to get winetools from the backports.

Install wine, libwine wine-utils from Universe and winetools from backports.  Run winetools and follow the setup menu.

So, you do not need to install anything from source...  Just use synaptic.[/QUOTE]

Nope. Still doesn't work. Looks as though everyone who installed Wine a while back got lucky, but now it's just not working. I used synaptic to Install wine, libwine, wine-utils, and winetools, ran winetools, and everything works until Explorer. Here's the tail end of what was going on (seems to be the same problem as detailed here [http://bugs.winehq.org/show_bug.cgi?id=2308):](http://bugs.winehq.org/show_bug.cgi?id=2308):)

err:thunk:_loadthunk (commctrl.dll, Cctl1632_ThunkData16, comctl32.dll): Unable to load 'commctrl.dll', error 2
err:module:LdrInitializeThunk "comctl32.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\msdownld.tmp\\AS01DEEC.tmp\\acmsetup.exe" failed, status c0000142
fixme:crypt:CryptRegisterDefaultOIDFunction (1,CertDllVerifyRevocation,0,L"mscrlrev.dll") stub!
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_REGSRCPATH
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_CFGAUTO
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_REGSRCPATH
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_CFGAUTO
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_REGSRCPATH
fixme:setupapi:GenInstall16 unsupported flag: GENINSTALL_DO_CFGAUTO
all wineservers endet after 119 seconds...
Failed: 0
check installation by path or registry value...
waiting for wineservers to exit...
all wineservers endet after 0 seconds...
Microsoft Internet Explorer.*
software installation verified by /home/karl/.wine/winetools.log
Failed: 1
Failed: 1
du: cannot access `/home/karl/winetools/sys/Windows Update Setup Files': No such file or directory
Downloaded IE6-Files=18432
Winetools  IE6-Files=0

--

If I knew anything about computers, I might be able to do something about this.

---

### Post by Karl S. on 2005-06-21
Oops.

[http://bugs.winehq.org/show_bug.cgi?id=2308](http://bugs.winehq.org/show_bug.cgi?id=2308)

Don't know how I put that face in there.

---

### Post by shof2k on 2005-06-21
I've only managed to get WINE to work at version 20041019.  I tried to upgrade to 200504xx but ended up with a similar stream of messages.  Not knowing if this was just me or WINE, I reinstalled 20041019 and locked the version.  Let me know if you want more details.

Has anyone got WINE working beyond version 20041019?  If so, will the new version appear in the synaptic reps?

---

### Post by Karl S. on 2005-06-21
[QUOTE=shof2k]I've only managed to get WINE to work at version 20041019.  I tried to upgrade to 200504xx but ended up with a similar stream of messages.  Not knowing if this was just me or WINE, I reinstalled 20041019 and locked the version.  Let me know if you want more details.[/QUOTE]

Oh definitely, I'd like to know how you did this if you have time to write a little something up. Remember that I know pretty much next-to-nothing about computers. It looks as though you could cross-post your solution at [http://www.ubuntuforums.org/showthread.php?p=220350&highlight=winetools#post220350](http://www.ubuntuforums.org/showthread.php?p=220350&highlight=winetools#post220350), since they're having the same trouble I am.

Thanks.

---

### Post by shof2k on 2005-06-21
I'll dig up my notes and post something soon.  Not sure why anyone would want to have IE running when you have firefox.  Kinda like wanting a bicycle when you can have a porche :).

---

### Post by Karl S. on 2005-06-21
Oh, I don't want IE, but there's a few windows applications that I need that aren't available Ubuntu (VulSearch, which I like since I'm a medievalist, for instance). Also, I'd like to try to tweak Endnote, for instance, to work through Wine, since I can't get Bibus ([http://www.ubuntuforums.org/showthread.php?t=43144&highlight](http://www.ubuntuforums.org/showthread.php?t=43144&highlight)) to work. If I can get Bibus working, I won't need Wine at all...but I don't suppose that's the case for some of the other people.

Thanks!

---

### Post by az on 2005-06-21
kurn@ubuntu:~$ dpkg -l|grep wine
ii  libwine        0.0.20050310-1 Windows Emulator (Library)
ii  wine           0.0.20050310-1 Windows Emulator (Binary Emulator)
ii  wine-utils     0.0.20050310-1 Windows Emulator (Utilities)
ii  winetools      2.1.1-1        A graphical setup suite for Wine
kurn@ubuntu:~$


Wine works fine for me with these versions.  Everyting from Hoary except winetools which is only in backports.   Did you follow the winetools base system installation steps one-by-one?

And if anyone wants to know why I am running this crap, the answer is: morbid curiosity after Aq from Lugradio said you can run WinMx under wine...

You can.

---

### Post by Karl S. on 2005-06-21
[QUOTE=azz]kurn@ubuntu:~$ dpkg -l|grep wine
ii  libwine        0.0.20050310-1 Windows Emulator (Library)
ii  wine           0.0.20050310-1 Windows Emulator (Binary Emulator)
ii  wine-utils     0.0.20050310-1 Windows Emulator (Utilities)
ii  winetools      2.1.1-1        A graphical setup suite for Wine
kurn@ubuntu:~$


Wine works fine for me with these versions.  Everyting from Hoary except winetools which is only in backports.   Did you follow the winetools base system installation steps one-by-one?
[/QUOTE]

I just looked at Synaptic and those are the packages I have installed. I'm not sure what the "dpkg -l|grep wine" command is, though ..

So I'm running base setup right now. I just told it to create  a fake windows drive, and since I've tried this before, it asks me if I want "to remove existing Wine configuration" (yes), it asks me what the mount point of my cdrom/dvd drive is, and I go with /dev/hdd, which is /media/cdrom0, rather than /dev/hdc, which is /media/cdrom1 (no idea what this means), and it creates a fake windows drive in ./windows. So far this is familiar. Now to installing my Arial Font Family. Goes off without a hitch, as does installing DCOM98.  I try Explorer. Doesn't work, same problem as before. Back when I first trying to do this thing a couple of days ago, I did compile CVS -- whatever that is -- following the instuctions from that Wine/CVS thread ([http://www.ubuntuforums.org/showthread.php?t=29996&highlight=winetools)](http://www.ubuntuforums.org/showthread.php?t=29996&highlight=winetools)), but whether that has anything to do with why this thing isn't working is beyond me.

Again, though, if someone who knows what they're doing can get Bibus working on their machine and let me know how they did it, then all this WINE stuff is totally unnecessary. For me, anyway.

---

### Post by Zeroedout on 2005-06-22
hrmmm, with my brother, i tried using winetools to setup wine and it wouldn't let a couple applications run. I then used winesetuptk and ran winesetup and using that, it seemed to configure wine to let that application work. (BTW the app was tibia, some really shitty MMORPG he plays, thier linux client is outdated, so he neede the windows one.) Try that and hopefully it'll work.

---

### Post by dissident on 2005-06-22
FYI, the WineTools homepage doesn't recommend using their tool with the latest version of Wine.  :-? 

[http://www.von-thadden.de/Joachim/WineTools/](http://www.von-thadden.de/Joachim/WineTools/)

---

### Post by debian_n00b on 2005-06-22
[QUOTE=Karl S.]I just looked at Synaptic and those are the packages I have installed. I'm not sure what the "dpkg -l|grep wine" command is, though ..
[/QUOTE]

DPKG is the Debian package manager. APT, APTITUDE and SYNAPTIC are all just frontends to DPKG.

the   "-l"  switch used with dpkg instructs it to list all apps installed by apt.

the "|" directs the terminal to redirect the output to the command grep. as opposed to standard output which would be on your screen.

"grep wine" instructs bash to display information that only contains wine in the name.


You should read up on DPKG and APT. Learn all the switches for them. I know only a handful of useful switches for them, yet I feel fairly productive managing a Debian based system. And, once you understand these fundamental commands, you will then see the beauty and simplicity upon which Ubuntu is built on.

---

### Post by Kimm on 2005-06-22
I've got the latest version of wine running just nicely, I've got Winamp running right now (not that I know why...) and it works very nicely, IE works aswell, installed that to get MSN Messenger 6 running (works but badly!), I soon came back to gaim however (after like 10 secunds).
Btw, I installed WineTools using a converted RPM package from their website, the repository server was dreadfully slow...

[http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-2.1.2-jo.i386.rpm](http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-2.1.2-jo.i386.rpm) I then linked to get xdialog running.

[img]http://www.area51central.com/Temp/winamp.png[/img]

*(And yes, that is a song from Spy Kids 2 :-P )*

---

### Post by Prudentissimus on 2005-06-22
[QUOTE=Zeroedout]hrmmm, with my brother, i tried using winetools to setup wine and it wouldn't let a couple applications run. I then used winesetuptk and ran winesetup and using that, it seemed to configure wine to let that application work. (BTW the app was tibia, some really shitty MMORPG he plays, thier linux client is outdated, so he neede the windows one.) Try that and hopefully it'll work.[/QUOTE]
 lol what server is he in? I have a lvl 45 in Libera lol Libera sucks... full of pkers and BRz....


anyways...


Wine... sigh... 


I just want to run Office XP in Linux... for free.

---

### Post by Karl S. on 2005-06-22
Well, damn.

Kimm, I downloaded that package, got rid of my old winetools, and used the one you provided. Thanks for that.

Unfortunately, it still doesn't work. I get the same error message as before on Explorer as before. And before. Ad nauseum. (and when installing the Arial fontset, the installation just hung on 3%...which is a problem that was dealt with in that Winetools/CVS thread...)

Using the command that Debian_n00b explained -- thanks -- here's what I have:


> karl@ubuntu:~$ dpkg -l|grep wine
ii  libwine        0.0.20050419-1 Windows Emulator (Library)
ii  wine           0.0.20050419-1 Windows Emulator (Binary Emulator)
ii  wine-utils     0.0.20050419-1 Windows Emulator (Utilities)
ii  winetools      2.1.2-1        WineTools is a menu driven installer for ins
karl@ubuntu:~$

I suppose if I could uninstall everything and try this with an older version of Wine, it'd probably work, yeah? Their website says 20050419 is unstable. Problem is, I don't know which of the old files to download...

---

### Post by az on 2005-06-22
[QUOTE=Karl S.]Well, damn.

Kimm, I downloaded that package, got rid of my old winetools, and used the one you provided. Thanks for that.

Unfortunately, it still doesn't work. I get the same error message as before on Explorer as before. And before. Ad nauseum. (and when installing the Arial fontset, the installation just hung on 3%...which is a problem that was dealt with in that Winetools/CVS thread...)

Using the command that Debian_n00b explained -- thanks -- here's what I have:




I suppose if I could uninstall everything and try this with an older version of Wine, it'd probably work, yeah? Their website says 20050419 is unstable. Problem is, I don't know which of the old files to download...[/QUOTE]

I though you said you had the 20050310-1 version installed?

---

### Post by Karl S. on 2005-06-23
[QUOTE=azz]I though you said you had the 20050310-1 version installed?[/QUOTE]

Nope. You might be misreading my quoting of you -- you have 20050310-1 installed right?-- for me listing what's on my system (which, so far as I know, I did only [here](http://www.ubuntuforums.org/showpost.php?p=224626&postcount=20) ). I just did dpkg -l|grep wine and I definitely have 20050419-1 installed for libwine, wine-utils, and wine, and now Winetools 2.1.2-1. I have 20050419-1 installed because it's what's available through Synaptic. I see that the notes on this release tell me *This is an ALPHA release of Wine, the MS-Windows emulator.  This is still a developers* [sic] *release and many applications may still not work.* Would it be advisable to force Synaptic to take an earlier package, say, 20050310-1, for wine, wine-utils, and libwine, and switch back to the most recent version of winetools and try again?

I think I'll try that after breakfast and let y'all know how it works.

---

### Post by jsimmons on 2005-06-23
[QUOTE=Karl S.]Nope. You might be misreading my quoting of you -- you have 20050310-1 installed right?-- for me listing what's on my system (which, so far as I know, I did only [here](http://www.ubuntuforums.org/showpost.php?p=224626&postcount=20) ). I just did dpkg -l|grep wine and I definitely have 20050419-1 installed for libwine, wine-utils, and wine, and now Winetools 2.1.2-1. I have 20050419-1 installed because it's what's available through Synaptic. I see that the notes on this release tell me *This is an ALPHA release of Wine, the MS-Windows emulator.  This is still a developers* [sic] *release and many applications may still not work.* Would it be advisable to force Synaptic to take an earlier package, say, 20050310-1, for wine, wine-utils, and libwine, and switch back to the most recent version of winetools and try again?

I think I'll try that after breakfast and let y'all know how it works.[/QUOTE]
 All versions of Wine have been alpha (or so I thought).  The latest version is 20050524-1, and the Wine website has a binary package available for Ubuntu. :)

---

### Post by Karl S. on 2005-06-23
[QUOTE=jsimmons]All versions of Wine have been alpha (or so I thought).  The latest version is 20050524-1, and the Wine website has a binary package available for Ubuntu. :)[/QUOTE]

Oh. Okay. I'll look at that later. I just tried an install with 20050310-1. Same problems. I did a complete uninstall of Wine, wine-utils, winetools, and winelib, AND CVS (which I reinstalled, then), deleted the wine folders from my HOME folder, but then I did a search for wine in my filesystem and found wine files in my usr/local/lib and usr/local/bin. I thought I should delete those, too, but it struck me that I shouldn't go mucking about in those folders without knowing what I was doing: but could these extra wine files be what's causing all of my wine installations to have the same problem? I just did a dpkg -l|grep wine and nothing comes up, so wine should be gone all the way, yeah? But why are those files still there in usr/local/lib and usr/local/bin?

Again, if someone could just get [Bibus working](http://www.ubuntuforums.org/showthread.php?t=43144&highlight=bibus) and tell me how they did it, I won't need Wine at all. But while that would solve *my* problem, it'd be no good for the other people who are [having the same problem](http://www.ubuntuforums.org/showthread.php?p=220350&highlight=winetools#post220350) having the same problem.

---

### Post by az on 2005-06-24
[QUOTE=Karl S.]I thought I should delete those, too, but it struck me that I shouldn't go mucking about in those folders without knowing what I was doing: but could these extra wine files be what's causing all of my wine installations to have the same problem? .[/QUOTE]

Well, installing from source will do that.  You need to use the uninstall scripts from the source package.  Probably just deleting it will be okay...

Is this the reason why it is not working?  I dunno.

---

### Post by Prudentissimus on 2005-07-03
[QUOTE=azz]Well, installing from source will do that.  You need to use the uninstall scripts from the source package.  Probably just deleting it will be okay...

Is this the reason why it is not working?  I dunno.[/QUOTE]
 Can we Ubuntu users install Wine by Source? Or must we install it through *.DEB packages.?

Which one is better? (Source or DEB)?

How to install it from Source?

---

### Post by atomikku on 2005-07-04
trying to install wine i downloaded all packages using synaptic exept the winetools, because the Xdialog lib wasn't possible to install.
i tried to install the Xdialog from [these binaries](http://thgodef.nerim.net/xdialog/Xdialog-2.1.2-1.src.rpm) - after converting it with alien i've installed the .deb file (sudo dpkg -i xdialog_2.1.2-2_i386.deb). everything was just fine, i was almost happy.
but starting the winetools commend i've got that output:
```
placid@d-ngn:~$ winetools
LD_PRELOAD=
found gettext in /usr/bin
detecting Wine version... done.
Drive C: is /home/placid/.wine/drive_c
**Wine 20050524**
wine is executed as wine
Parameters are --noexit
Browser is /usr/bin/firefox.
**WINEVER is "20050524".**
/usr/local/bin/winetools: line 2947: /usr/local/winetools/**Xdialog**: No such file or directory
Calls to wine are executed as  "wine".
Config is /home/placid/.wine/winetools.log.
CDROM is .
/usr/local/bin/winetools: line 2859: /usr/local/winetools/**Xdialog**: No such file or directory
/usr/local/bin/winetools: line 2888: /usr/local/winetools/**Xdialog**: No such file or directory
placid@d-ngn:~$

```
it looks like i've never installed xdialog.. any suggestions?

---

### Post by amohanty on 2005-07-07
I dont even get to see wine listed in synaptic!! A search for wine only brings up wine-docs, even with the disabled repos turned on.

AM I doing something wrong?

Thanks.

AM

---

### Post by atomikku on 2005-07-07
you have to add the wine's repositories manually.
the easy way is to edit the **sources.list** document:

open a console and type
**sudo nano /etc/apt/sources.list**

and add these lines:
[B]deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/[/B]

then you should update the packages information by entering
**sudo apt-get update**

after that the synaptic lists the wine repositories and you can install them via the gui or by the console by typing **sudo apt-get install wine**

you can install new repositories via the synaptic gui using the add command, entering the URI the directory and the type (source or binary) when prompted.

everything runs fine until the ***winetools*** installation. any ideas to install this package?  :?

---

### Post by amohanty on 2005-07-07
Nope ... doest work:

my /etc/apt/setup.lst:

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/
~

results of apt-get update:
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release.gpg
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Release.gpg
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg [189B]
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Release
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Sources
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) source/ Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
.....

results of apt-get install wine:
root@kandinsky:~ # apt-get install wine
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate

from procinfo:
Linux 2.6.10-5-amd64-generic (buildd@yellow) (gcc 3.3.5 ) #1 1CPU [kandinsky]

SO what am I doing wrong here?

Thanks.

---

### Post by atomikku on 2005-07-07
[QUOTE=amohanty]Nope ... doest work:

my /etc/apt/setup.lst:

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/
~
[/QUOTE]

try to edit the /etc/apt/**sources.list**

---

### Post by amohanty on 2005-07-07
Sorry but that was a typo on my part: it is /etc/apt/sources.list

---

### Post by atomikku on 2005-07-07
i don't know what's the matter with your repositories... here are the lines describing my wine repositories:
...
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/ 
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/  
...
do not forget to run apt-get update after adding them. i hope it will work for you...

---

