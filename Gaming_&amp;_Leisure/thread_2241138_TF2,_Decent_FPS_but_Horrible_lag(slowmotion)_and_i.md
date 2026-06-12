---
title: "TF2, Decent FPS but Horrible lag(slowmotion) and input lag + long loading time!"
date: 2014-08-24
forum: Gaming &amp; Leisure
---

### Post by kamhagh on 2014-08-24
hi, my problem is almost exactly like here :
[http://devgurus.amd.com/thread/160265](http://devgurus.amd.com/thread/160265)

i get 8~ more fps than windows, i use flrx-update , in windows its buttery smooth, in linux, its just horrible, it sometimes go into slow motion, stutter , lags, and i got Horrible input lag, i push my mouse and after it stops i see the corsair move there ! today the fps was 60 , but All the V-syncs were off, other days it was 130~ i see it once jumped 30fps today, (if it helps i switched to gnome for fun today ! but this was present from first second of installing 14.04, before that i played it on windows only !) also laod takes like 1-3mins, in windows it less than 16 seconds !

here are specs:


[COLOR=#CCCCCC][/COLOR][COLOR=#000000][FONT=verdana]CPU: I5-3570K[/FONT]
[FONT=verdana]Motherboard: Asus P8B75-V[/FONT]
[FONT=verdana]Graphics card: Gigabyte R7 250x 2GB-OC <---- Graphics card similar too 7770[/FONT]
[FONT=verdana]RAM: (4x2)8GB Kingston hyperX 1600mhz[/FONT]
[FONT=verdana]HDD: WD WD10EZEX 1000GB(Blue)[/FONT]
[FONT=verdana]SSD: Intel 520 120GB [/FONT]
[FONT=verdana]CPU Cooler: Stock[/FONT]
[FONT=verdana]Fans: 2x140mm Intake front fans 1x120mm Exhaust fan[/FONT]
[FONT=verdana]Case: Green Dragon Pro[/FONT]
[FONT=verdana]PSU: Green GP650B-OC[/FONT]
[FONT=verdana]OS: Ubuntu 14.04 LTS[/FONT][/COLOR][COLOR=#CCCCCC]
[/COLOR][COLOR=#000000]
this problem is not similiar to my old thread, old one was that i dont get decent fps, now i get good fps(fixed it) but i still lag, get weird slowmotion, it's more like slowmotion rather than low FPS ![/COLOR]
[COLOR=#000000][/COLOR]

---

### Post by kamhagh on 2014-08-25
if i fix that i will have no reason at all to go too windows at all :)

---

### Post by bizhat on 2014-08-25
Post result of 

```

glxinfo | grep OpenGL

```

---

### Post by kamhagh on 2014-08-25
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon R7 200 Series                  
OpenGL core profile version string: 4.3.12798 Core Profile Context 13.35.1005
OpenGL core profile shading language version string: 4.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 4.3.12798 Compatibility Profile Context 13.35.1005
OpenGL shading language version string: 4.30
OpenGL context flags: (none)
OpenGL profile mask: compatibility profile
OpenGL extensions:

sorry for delay!

---

### Post by bizhat on 2014-08-26
You are using Catalyst. Since your card is newer, not sure how good open source support is. It may be better try the open source driver and see if that fix or improve performance.

To revert back to open source driver, run

```

sudo apt-get purge fglrx*
sudo rm /etc/X11/xorg.conf
sudo apt-get install --reinstall xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg
reboot

```

We need fglrx removed as it can cause problem with open source driver.

The catalyst you installed is from ubuntu or downloaded from AMD web site ? If open source driver won't improve performance, go to AMD site and download and install latest Linux driver (beta).

[http://support.amd.com/en-us/kb-articles/Pages/Latest-LINUX-Beta-Driver.aspx](http://support.amd.com/en-us/kb-articles/Pages/Latest-LINUX-Beta-Driver.aspx)

Try benchmarking with different drivers using

```

glmark2

```

---

### Post by kamhagh on 2014-08-26
i first used open source, i get 16 - 30max fps but no weird problems (slowmototion)
it took me so much time and money too download flrx too :( but first when i installed the cart it had opensrouce it had like 30max fps !

the amd website is forbidden for us :( i cant open it !

i will benchmark current one ! edit: i got 60, no slowmotions !

---

### Post by bizhat on 2014-08-26
When you install fglrx, make sure old versions of fglrx is removed. These version conflict each other.  Once you have downloaded catalyst, you can use the same files again... no need to download again. So get it once and keep it safe, i still have it on my pc even though i am not using it.


> **kamhagh said:**
> 
the amd website is forbidden for us :( i cant open it !


If you need, i can download it save put it on my site for you to download. Make sure you verify md5 before using it, i take no responsibility :)

---

### Post by kamhagh on 2014-08-26
thanks so much :) can you upload it? and also i can't check the MD5 there can you post it with md5?

btw im gonna take a full backup of my system before that, not sure how too, i made a thread about it before making this, im waiting for answer (i want to backup packages without downloading them again!)

---

### Post by bizhat on 2014-08-26
You can download it from

[http://webhostingneeds.com/tmp_fp/linux-amd-catalyst-14.6-beta-v1.0-jul11.zip](http://webhostingneeds.com/tmp_fp/linux-amd-catalyst-14.6-beta-v1.0-jul11.zip)

This is latest beta as of today.

```

[root@server70 tmp_fp]# md5sum linux-amd-catalyst-14.6-beta-v1.0-jul11.zip
dbe3bcd406b4ca2e63e745f7183657fc  linux-amd-catalyst-14.6-beta-v1.0-jul11.zip
[root@server70 tmp_fp]# 

```

I will remove the file after you get it.

---

### Post by kamhagh on 2014-08-26
thanks a lot,i was gonna put it to shedule to download at 3am (wrote app for it) but i will just download it now :) will pos here after its done :!

---

### Post by bizhat on 2014-08-26
Nice, share the app, i am using wget for my downloads.. Don't want to install a graphical GUI after switching from Windows. I was using JDownloader on Windows. Only problem Ctrl+C for pausing download :)

---

### Post by kamhagh on 2014-08-26
its done :) when installing it it required me few stuff and said to check log, let me check it

and the app i wrote is nothing special, it just runs wget or sudo apt-get install at the specified time ! it has a simple gui, time and name and password ! i also made non gui version !

---

### Post by kamhagh on 2014-08-26
nvm this is what i got , im going to install again as i don't have controll panel ! i think i made few mistakes choosing some stuff!
Detected configuration:
Architecture: x86_64 (64-bit)
X Server: X.Org 6.9 or later 64-bit
./lokixml.sh: 143: ./lokixml.sh: [[: not found
loki_setup: directory: (null)

---

### Post by kamhagh on 2014-08-26
its still taking extremely long, im waiting for it too load ! i got control panel now, i made mistake last time installing it ! but i will edit this when i found out about the slow motions and ect!

edit: it gave black screen at making a server , and my system was competently frozen, numlock didn't work, alt tab didn't work ctrl+alt+f1 didn't work either !

edit: i was trying to do something and when i wanted to reinstall it says you have previuse installation of fglrx! i did remove --purge fglrx*

heres fglrx-install.log:

NOTE: If your system has logged the missing packages required for installation, install them in the order as per the log file to resolve package-dependency issues.Supported adapter detected.
Detected a previous installation, /usr/share/ati/amd-uninstall.sh


[Error]A previous installation of fglrx driver detected.
User must uninstall using /usr/share/ati/amd-uninstall.sh with force 
or run install with force option. 
Forcing the installation is not recommended.

EDIT: installed it again with --force !

---

### Post by bizhat on 2014-08-26
During install, you have to select package option, that is it will create .deb packages, that is easy to uninstall.  

> /usr/share/ati/amd-uninstall.sh

This is only needed if you have previously installed with out making deb package.

---

### Post by kamhagh on 2014-08-27
i installed it with force but now i do it with he one you gave me and try again ! but the first install which was successful made my screen to go black and not respond at all(even num) after few seconds of tf2 making the server ! but when i alt tabed the next time, (restarted pc) it made the game to go windowed mode , and was so small, when it was windowed i was able to play !

still it took extremly long to load, installing again with /usr/share/ati/amd-uninstall.sh!

---

### Post by kamhagh on 2014-08-27
i did what you said, it fixed the black screen problem, but sadly, new drivers didn't help, i had sttuter and lag, my fps was 60 with all the V-Syncs disabled, thats disappointing :(

it almost always stutters and lags but when i shoot at someone(not air) it goes slowmotion/freeze for a second and than back to normal for 5~ first times, after that it doens't always happen, same thing for killing

but still always it stutters and lags ! fps gets red(jumps to low fps for a second when this happens, normaly my fps is 30-60, its so horrible, on windows and i dont know what drivers and what setting it was (fglrx) i had 130 fps, but still lagged anyway !

btw: if you want the app i wrote (simple app just calls wget or sudo apt-get install package-name) at specific time and has  simple GUI, i can upload it to dropbox ! i also have non gui version of it, (in python, gui is in in c++)

summary: problem isn't gone and when lag happen fps jumps low, and fps is also normally low (60) and some stutter !

---

### Post by bizhat on 2014-08-27
I think we have to wait for AMD or Open Source guys to make a better driver for the GPU, hope they do it faster :)

Keep a windows partition for Gaming, until you finished all windows games, by the time Ubuntu drivers will improve and we will have more games to play on Ubuntu. I have not booted to my Windows last few days as i don't play much games/little TF2 on Ubuntu.

Thanks for the info about your application, don't you use version control software like GIT ? It is better use github for software than using dropbox, that make it easy to keep software updated/track changes.

---

### Post by kamhagh on 2014-08-27
ok, i almost never play endable games ! i played few like bf4 Bioshock tombraider ! also i dont play games much, i used to, i dont have time, specially that schools are starting ~1 months from now tahts kinda good, i will feel lazy to play games so i can focus more on learning!

anyway about the GIT/Github, im not sure what they're !!!! i only use dropbox to upload file for others and had some data to backup there (small size :) i needed to accesses it everywhere) i mainly used to too proof to my friends that i kited ~15 lvl 45 minions with hunter at lvl 40 :D , in wotlk,

---

### Post by bizhat on 2014-08-27
> **kamhagh said:**
> anyway about the GIT/Github, im not sure what they're !!!! 

It is a command line program, you install with command "apt-get install git", this allow you to better develop software. Linux kernel use git. Linus created it. 

> **kamhagh said:**
>  i mainly used to too proof to my friends that i kited ~15 lvl 45 minions with hunter at lvl 40 :D , in wotlk,

Which game it is ? Wow ?

---

### Post by kamhagh on 2014-08-27
yes world of warcraft :D wrath of the lick king (3.3.5a)  i will try it !(git:P)

i see its for working team project, not good for me because i don't do group project, although i think if i try one it will help my skills !

btw what if some noob or sick guy changes the whole project to : cout << "MUHAHAHAHA" ? :)

---

### Post by bizhat on 2014-08-28
Never played WarCraft, RuneScape here :) I already quit playing it 2 years back. Since this game works on Ubuntu (Java game), i play at times.

git is good for non team projects. I use it for my password files, my financial accounting text file etc.. It is even good if you are a writer and writing a story, what it do is allow you to go to previous version of a file. Something like a time machine. For example, if you need get version of a file like it was 2 months back, you get it, you can compare changes made in these files. When working with a team, it allow you to see what changes other members have made. Even when you work your own, you can see what changes you made after last commit, so nothing go unnoticed.

---

### Post by kamhagh on 2014-08-28
wow is one of the best games i have seen in my life, btw its playable from wine (the old version, i think new one is too! new one uses battle.net)

git seems awesome for me :D i made many stupid mistakes and accidentally changed it and saved it !

---

### Post by bizhat on 2014-08-28
How much download size for old wow that work on Ubuntu ?

---

