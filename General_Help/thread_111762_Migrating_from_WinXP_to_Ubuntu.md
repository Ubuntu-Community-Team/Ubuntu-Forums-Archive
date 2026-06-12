---
title: "Migrating from WinXP to Ubuntu"
date: 2006-01-02
forum: General Help
---

### Post by motorsep on 2006-01-02
Hi,

Since I started migration process from 3DS MAX to Blender3D, I really don't have anything I can't use under Linux. So I decided to mirgate from WinXP to Ubuntu. But I still have concerns (at I have never work with Linux before). 

1. Can I watch DivX, xVid, Windows AVI, Quicktime, Real Video movies, WMV, DVD-movies under Ubuntu? Is there a package with all-in-one codecs?

2. My daughter loves to play online games from Disney.com and Nickjr.com. And they are all Flash or Shockwave games. Will she be able to play Flash and Shockwave games under Ubuntu?

3. I use PDF Creator to create PDFs and Acrobat reader to read them? Is there any alternative to Adobe Acrobat reader?

4. Is there software to burn video DVDs under Ubuntu?

5. Is there any good Anti-virus software for Ubuntu?

6. I heard it's really hard to install network under Ubuntu. Is it true? I have DSL modem hooked up to PC via Ethernet adapter.

7. I read in one of reviews that Ubuntu's installer is less friendly than installers of other packages. Is it true?

I would greately appreciate your reply.
Thanks.

---

### Post by ardchoille on 2006-01-02
[QUOTE=motorsep]Hi,

Since I started migration process from 3DS MAX to Blender3D, I really don't have anything I can't use under Linux. So I decided to mirgate from WinXP to Ubuntu. But I still have concerns (at I have never work with Linux before). 

1. Can I watch DivX, xVid, Windows AVI, Quicktime, Real Video movies, WMV, DVD-movies under Ubuntu? Is there a package with all-in-one codecs?

2. My daughter loves to play online games from Disney.com and Nickjr.com. And they are all Flash or Shockwave games. Will she be able to play Flash and Shockwave games under Ubuntu?

3. I use PDF Creator to create PDFs and Acrobat reader to read them? Is there any alternative to Adobe Acrobat reader?

4. Is there software to burn video DVDs under Ubuntu?

5. Is there any good Anti-virus software for Ubuntu?

6. I heard it's really hard to install network under Ubuntu. Is it true? I have DSL modem hooked up to PC via Ethernet adapter.

7. I read in one of reviews that Ubuntu's installer is less friendly than installers of other packages. Is it true?

I would greately appreciate your reply.
Thanks.[/QUOTE]

1. Yes. I use xine-ui and have installed the w32codecs and I haven't found anything that I cannot watch.

2. Yes. Firefox has a plugin that plays flash content. You can find more plugins here: [https://pfs.mozilla.org/plugins/?application=firefox](https://pfs.mozilla.org/plugins/?application=firefox)

3. I use Evince to read .pdf files and Openoffice.org writer to create them.

4. There are lots of DVD/CD burning apps. The ones I can think of are K3b (for KDE), graveman (for gnome), gnomebaker.

5. clamav

6. I installed Ubuntu 5.10 and it picked up my DSL connection. I haven't had to do anything else except surf the net :)

7. Not true. Synaptic is point and click, can't get much easier than that. However, apt-get is the easiest command line installer that I have used. Synaptic is a gui front-end for apt-get, I believe.

I am not a gamer, so I cannot speak for the games, but I haven't found anything in Windows that I cannot do in Linux - except maybe go broke buying software.

Good luck :)

---

### Post by motorsep on 2006-01-02
Thanks a bunch!

I saw ppl on IRC talk alot about compiling something, working with command line, etc. Is it ususal routine or what? One of the things that frightens me about Linux is that in XXI century I would have to type all the time somethiong in command line :/

---

### Post by Sef on 2006-01-02
> 1. Can I watch DivX, xVid, Windows AVI, Quicktime, Real Video movies, WMV, DVD-movies under Ubuntu? Is there a package with all-in-one codecs?

Yes, if you install the correct codes.  I believe they are win32.  Most of them are available from the Synaptic Package Manager.

> 2. My daughter loves to play online games from Disney.com and Nickjr.com. And they are all Flash or Shockwave games. Will she be able to play Flash and Shockwave games under Ubuntu?

Flash is available for a download from Synaptic.  There is no Shockwave for Linux as of yet.

> 3. I use PDF Creator to create PDFs and Acrobat reader to read them? Is there any alternative to Adobe Acrobat reader?

Yes alternatives to Acrobat reader are installed.   KDE's is KPDF.

> 4. Is there software to burn video DVDs under Ubuntu?

Yes there is.  Here is a thread on it: [http://ubuntuforums.org/showthread.php?t=94622&highlight=Burning+DVDs]("http://ubuntuforums.org/showthread.php?t=94622&highlight=Burning+DVDs")

> 5. Is there any good Anti-virus software for Ubuntu?

ClamAV is available; however, there are no viruses as of yet for Linux in the wild.  

> 6. I heard it's really hard to install network under Ubuntu. Is it true? I have DSL modem hooked up to PC via Ethernet adapter.

To install the internet, it does it automatically while installing.   If you want to network, it may be difficult or not, if you use wireless.  It depends on if drivers are available and downloaded  for you wireless cards.

> 7. I read in one of reviews that Ubuntu's installer is less friendly than installers of other packages. Is it true?

It is a fairly easy install.   The only problem would be if you would have to maually partition in order to set up a dual boot, a /home or both.  Here is an excellent tutorial on installing Ubuntu:  [http://www.users.bigpond.net.au/hermanzone/]("http://www.users.bigpond.net.au/hermanzone/")

---

### Post by Sef on 2006-01-02
> I saw ppl on IRC talk alot about compiling something, working with command line, etc. Is it ususal routine or what? One of the things that frightens me about Linux is that in XXI century I would have to type all the time somethiong in command line :/


With Ubuntu you have the option of using a gui package manager (Synaptic) or using the command line.  (GUI package manager = point and click with the mouse.)

---

### Post by motorsep on 2006-01-02
Thank you Sef.

---

### Post by ltmon on 2006-01-02
[QUOTE=motorsep]
I saw ppl on IRC talk alot about compiling something, working with command line, etc. Is it ususal routine or what? One of the things that frightens me about Linux is that in XXI century I would have to type all the time somethiong in command line :/[/QUOTE]

IRC (and these forums) are where people turn to when they have problems, so for better or worse you will pretty much see the worst aspects of (K)Ubuntu when you browse here or listen in on IRC.

In general you don't have to compile anything, and command line use is minimal (and really quite easy... if you can master 3d modelling tools you can use the command line!).

L.

---

### Post by motorsep on 2006-01-02
Ok. What is Kubuntu?

---

### Post by xtacocorex on 2006-01-03
[QUOTE=motorsep]Ok. What is Kubuntu?[/QUOTE]

Ubuntu uses Gnome for it's desktop,

Kubuntu is Ubuntu with KDE instead of Gnome: [http://www.kubuntu.org](http://www.kubuntu.org)

The two are pretty much the same except for the desktop. Programs written for Gnome will work under KDE and vice-versa.

If you have Ubuntu and want to try Kubuntu, in synaptic you can search for the package kubuntu-desktop and it will install KDE for you.

---

### Post by motorsep on 2006-01-03
Which one is more like WinXP, with GNOME or with KDE ?

---

### Post by tokyovigilante on 2006-01-03
Superficially, KDE is probably more similar to XP, as it has a similarly laid out (by default although this is customisable) taskbar and K (analogous to Start) menu at the bottom of the screen, a centralised Settings utility, and integrated File manager/web browser, Konqueror (ala Windows/Internet Explorer). But Gnome is customisable to resemble XP, so in the end, give both a try and use whichever is most comfortable.

Another gross generalisation is that KDE exposes many more system/interface settings and options via a GUI, whereas Gnome strives for simplicity.

Having said that, the same Linux/Ubuntu core underlies both environments, so command-line tools function identically in both, and there is no difference in hardware/software compatibility, ie GTK (Gnome library) apps run in KDE, and QT (KDE library) apps run under Gnome.

---

### Post by motorsep on 2006-01-03
Thanks a bunch guys!!

---

### Post by Sef on 2006-01-03
> Which one is more like WinXP, with GNOME or with KDE ?

Which one is better?   The better one is the one you prefer.  It all boils down to choice.

---

### Post by taseal on 2006-01-03
I started off with XP for a while, then I attempted to install OSX to my PC, and to do this, you needed to use a live cd from a linux based OS, so I chose ubuntu, and when I booted up ubuntu on live cd I loved it so much, I kept it... you can customize it alot (ubuntu) bu the GUI (the user interface) looked too simple for me, and I didnt know what kubuntu was... so I asked around here what it is, and with the help of the members here I installed kubuntu, (very easy process) I now use kubuntu, and will never switch back :)

oh, and installing things is easy as this 

```

sudo apt-get install blender

```
it will install it all for you, you dont do anything else :)
and to launch it, you can just type blender in the terminal window or select it from the programs menu

here is a screen shot of my desktop in kubuntu... like I said, its VERY customizable...

[img]http://img499.imageshack.us/img499/8531/desktop1wy.jpg[/img]

---

### Post by KRiSX on 2006-01-03
damn that is a sexy desktop!

just to answer one of the questions... u said u want a linux alternative to adobe reader... just use adobe reader for linux... lol

but yeah one thing u have to know before switching is that u can't be afraid of the command line cause ur gonna need to use it at least once or twice... mainly while getting things setup or installing programs...

apart from that its all good... just make sure ur hardware is supported, i've had a couple problems with hardware related things... unforunatly those problems are making me stay with windows for now :( i can do everything in linux... but when my system runs like crap due to not working properly on my hardware... i'm not gonna put up with it... maybe 6.04 will be my answer

---

### Post by taseal on 2006-01-03
[QUOTE=KRiSX]damn that is a sexy desktop!

just to answer one of the questions... u said u want a linux alternative to adobe reader... just use adobe reader for linux... lol

but yeah one thing u have to know before switching is that u can't be afraid of the command line cause ur gonna need to use it at least once or twice... mainly while getting things setup or installing programs...

apart from that its all good... just make sure ur hardware is supported, i've had a couple problems with hardware related things... unforunatly those problems are making me stay with windows for now :( i can do everything in linux... but when my system runs like crap due to not working properly on my hardware... i'm not gonna put up with it... maybe 6.04 will be my answer[/QUOTE]

thank you :)

mind you, you CAN run XP and linux in 1 computer... its possible with GRUB, it lets you select what OS to run in the beginning...this is how I use both my computers... on the laptop, I have a SD card reader, and unfortunetly linux does not support this, so whenever I wanna load up pictures I have to switch to XP, same goes for my nano ipod... kubuntu doesnt recognize it :(

there is also a program called wine, that is a XP emulator... it lets you run many many win32 programs on your linux, like say photoshop, or IE 6 :)

---

### Post by KRiSX on 2006-01-03
i've been a linux user on and off for a long time... things are certainly a lot better then the old red hat 5.2 days (the first dist i ever used)...

i want to try and avoid dual booting... just annoys me... lol


oh and i just want to point out that wine is not an xp emulator... thats what wine stands for "Wine Is Not an Emulator" :) it does work very well in what it does tho

---

### Post by taseal on 2006-01-03
[QUOTE=KRiSX]i've been a linux user on and off for a long time... things are certainly a lot better then the old red hat 5.2 days (the first dist i ever used)...

i want to try and avoid dual booting... just annoys me... lol


oh and i just want to point out that wine is not an xp emulator... thats what wine stands for "Wine Is Not an Emulator" :) it does work very well in what it does tho[/QUOTE]


haha I never knew thats what it stands for!

it does emulate w32 programs in a non w32 enviroment though lol :x

---

### Post by coolclassic on 2006-01-03
[QUOTE=taseal]thank you :)

I have a SD card reader, and unfortunetly linux does not support this, so whenever I wanna load up pictures I have to switch to XP, same goes for my nano ipod... kubuntu doesnt recognize it :(

[/QUOTE]

Just by reading a few threads it appears your ipod can work in breezy and if your card reader is usb, breezy should be able to read it.

---

### Post by Brando569 on 2006-01-04
[QUOTE=motorsep]Hi,
1. Can I watch DivX, xVid, Windows AVI, Quicktime, Real Video movies, WMV, DVD-movies under Ubuntu? Is there a package with all-in-one codecs?

2. My daughter loves to play online games from Disney.com and Nickjr.com. And they are all Flash or Shockwave games. Will she be able to play Flash and Shockwave games under Ubuntu?

3. I use PDF Creator to create PDFs and Acrobat reader to read them? Is there any alternative to Adobe Acrobat reader?

4. Is there software to burn video DVDs under Ubuntu?

5. Is there any good Anti-virus software for Ubuntu?

6. I heard it's really hard to install network under Ubuntu. Is it true? I have DSL modem hooked up to PC via Ethernet adapter.

7. I read in one of reviews that Ubuntu's installer is less friendly than installers of other packages. Is it true?

I would greately appreciate your reply.
Thanks.[/QUOTE]

for mostly all of these (?s 1,2 & 3) i recommend using arnieboy's Automatix, works really good. he even has a version for both ubuntu and kubuntu. both work great.

5. thats one of the GREAT things about linux: no virii and no spyware :D 

6.in (k)ubuntu its really easy to setup your network, if you can do it in windows with very little more effort you can do it in (k)ubuntu im running a network right now. took me maybe 20 mins at the most to set it up.

7. alot of linux distros are hard to install, some are EXTREMELY hard to install and contain no installer at all (gentoo comes to mind, tried atleast 10x to install it and never got a GUI :mad: ) i love how packages are installed under (k)ubuntu, its so much easier then installing one program at a time in windows. i hated clicking "Next" 20 thousand times :D with synaptic you can install 200 programs at the click of a button :D Kubuntu comes with Adept package manager, personally i dont like it its not as feature packed as synaptic.

as for the "windows like GUI" id say go with KDE (Kubuntu) most windows to linux converts use it cuz it has a lot of eye candy and it easy to use. ive been using solely KDE now for 4 months and love it, i never wanna go back to windows unless i have to :p if you have alot of space id recommend installing Ubuntu then adding on the kubuntu-desktop package. thats what i did initially back in 5.04 cuz i think kubuntu was just getting started and wasnt as "feature packed" as ubuntu. i cant stand gnome, ppl say its supposed to be for simplicity i say its just for annoyance :rolleyes: 

bottom line: dont be afraid of linux. if anything you should be afraid of windows. once you use linux, you be like "damn theres so much i can do and nothing is stopping me!" have fun.

one thing i forgot ot add, the installation of (k)ubuntu (i think) is easier then installing windows. well atleast updating it is :D no hotfixes comming out everyweek that you "have to have"

---

### Post by ramjet on 2006-01-04
in regards to the command line, im going to have to disagree with some posts..  
As long as your hardware is not too exotic and needs some hacking to get working (and even lots of exotic hardware is pretty well supported now) you should not have to touch a command prompt.  
Many people still use the command prompt because they have used a *nix for a while and are used to it or find it faster or dont know the new way.

install and use software and perform most tasks on deskto oriented linux's like ubuntu will not require the console.

I have ubuntu on my IBM x40 laptop and everythign is supported on first install and despite having since customised my install considerably i have not yet had to use the command prompt.

---

### Post by taseal on 2006-01-04
I have to use the terminal to upgrade, cuz I dont have the red button in synpatics since i'm using KDE...

---

### Post by coolclassic on 2006-01-04
[QUOTE=taseal]I have to use the terminal to upgrade, cuz I dont have the red button in synpatics since i'm using KDE...[/QUOTE]

But KDE has adept for single click upgrade.

---

### Post by taseal on 2006-01-04
[QUOTE=coolclassic]But KDE has adept for single click upgrade.[/QUOTE]

as funny as it sounds, I dont think I have used it yet

I think I uninstalled some stuff through it

---

