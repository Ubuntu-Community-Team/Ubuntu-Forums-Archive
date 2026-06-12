---
title: "Team Fortress 2 , horrible FPS"
date: 2014-08-07
forum: Gaming &amp; Leisure
---

### Post by kamhagh on 2014-08-07
Hi, i just got an Gigabyte R7 250x oc version

it givess like 160fps on windows without vsync and with everything max and

same thing on ubuntu gives me like 15 fps, why is ti like that? when i turn off multisample it gives like 70 fps, which is playable, but i want mutlisample, why is performance so horrible in ubuntu while its good on windows, my card is pwoerfull enough !

---

### Post by oldrocker99 on 2014-08-07
The R7 250X is an ATI card, and ATI's fglrx drivers for Linux, which you probably have installed, are notoriously lousy drivers, which is why many Linux gamers use nVidia cards.

You may (seriously) get better results by removing the ATI drivers and using the open-source radeon driver, which, according to posts I've seen on the Steam forums, frequently works better than the fglrx driver. 

Fox example, Painkiller:Hell and Damnation, which ran for me on the first day with nVidia, had a raft of frustrated ATI users who waited over a month for ATI to get its act together and put out drivers which would work with that game.

Just sayin'. I would try the radron driver, and remove the fglrx.

Also, the Unity interface is pretty heavyweight; many Linux gamers install LXDE, which uses far fewer resources, for gaming.

---

### Post by kamhagh on 2014-08-07
i read somewher they are same, :(

i got flrx-update drivers instead of stock opensrouce + catclyst and now i get 100 - 120, on same map and setting im getting only 20 lower only, which i never get under 80 which is good, but now i get these weird glitech, on game specially, i get telepored backward for a second, and i get lag Spikes, i tought amd is better because of its opensrouce stuff:( thats so bad, if i knew this i spent 40=50$ more for nvidia, or got an gtx 650 :(

i notice my Ubuntu Gui is even laggy, a little, and SO teary, the setting in catacyst helped, but anyway im so disapointed;( my 7750 wasn't like that at all! (sapphire)

---

### Post by oldrocker99 on 2014-08-07
I have seen people swear that the radeon drivers (which have been developed with ATI's help, for what that's worth) are superior to fglrx, but I remain an nVidia guy.

---

### Post by kamhagh on 2014-08-07
omg this is horrile, i cant belivce this, i spent 150$ on a graphics card which can't even work with unity and lags like hell, tf2 ppl slow down and screen get freez like and weird stuff happen, this is horrible, i can't belive this, my tf2 is totaly unplayable even at min setting ! let me try another drivers,,,, i can't velive this, i only needed 20$ for 750 ti but i saved it !

im donwloading another driver,

a litte not: my fps is 60fps when i get the weird slowing, sometimes my background flashes for 100ms,

also it takes soooo long to open tf2 but much less than windows to join servers, takes long to be able to choose class !

---

### Post by dannyboy79 on 2014-08-07
check out the oibaf ppa for the most recent version of the radeonsi driver. If it's not to late you should return your AMD based card and get an equivalent priced Nvidia card, maybe the Nvidia 750ti IF you're serious about gaming in linux. Sadly AMD is lagging behind in the driver department.

---

### Post by R33D3M33R on 2014-08-08
R7 250X is renamed HD 7770. If your HD 7750 worked well, R7 250X should also with the **same drivers**, because it's the **same chip** (Cape Verde). Also, the card is only 25% faster than HD 7750, so don't expect miracles.

---

### Post by kamhagh on 2014-08-08
I actually only changed it because it died, i didn't have performance issues, 
New drivers dont have weird slow down, bit gives 30 or 60 fps, they wont accept it because oc performance they'll telll me you should have known!!! Im gonna hunt the person told me nvidia and amd have both good drivers!!! I will try the drivers you mentioned when i get home, i can't believe this

Wasted 300mb of data and stayed awake. Till 4 am to find out they're horrible too

---

### Post by kamhagh on 2014-08-08
can you tell me which version to download ???(not amd ones, opensrources you mentioned)   amd side is forbidden for be:( i currently have and had (flrx-update) the 13.4 version. maybe beta will help?

i will never buy amd again, even if it means i should buy GTX titan for playing packman xD

---

### Post by R33D3M33R on 2014-08-08
Before doing anything with the drivers, please take a screenshot of your Catalyst Control Center -> Information and upload it here. It should look like something below:

[ATTACH=CONFIG]255319[/ATTACH]

---

### Post by kamhagh on 2014-08-08
[ATTACH=CONFIG]255320[/ATTACH]

:| i hope i can fix this :|

i dont know why this pic is so ahrd to read !

---

### Post by R33D3M33R on 2014-08-08
Ok, so the drivers seem to be installed fine. Can you now write down what CPU you are using?

---

### Post by kamhagh on 2014-08-08
my pu is 3570k

my motherboard  is b75-b (i know its stupid but its a long story!)

just let me tell me whole system:

CPU: I5-3570K
Motherboard: Asus P8B75-V
RAM: (4x2)8GB Kingston hyperX blue 1600mhz
HDD: WD WD10EZEX 1000GB(Blue)
SSD: Intel 520 120GB 
CPU Cooler: Stock
Fans: 2x140mm Intake front fans  1x120mm Exhaust fan
PSU: Green GP650B-OC

i just pasted it and removed some unneccessery stuff

---

### Post by R33D3M33R on 2014-08-08
Ok, so what resolution are you running the game on? And did you disable the onboard graphics card?

---

### Post by kamhagh on 2014-08-08
hmm, im not sure if IGPU is disabled, but that fps can't come from IGPU, IGPU gave me 10fps at max this one gives min 30fps

my resulution is 1920x1080p

i just took out my poor sapphire 7750 and went IGPU for like 2 weeks till i get new one i saw ubuntu done everything for me(removed amd stuff)

after that i just put the new one in but went windows and did some stuff(drivers , oCed if for fun :D and ect), than i came ubuntu, i saw same performance, after i got new drivers it went better but with weird lag, the drivers i told you doesn't get weird slowmotion and lag spikes but sometimes like in MVM fps gets horrible!

---

### Post by R33D3M33R on 2014-08-08
So Tear Free and V-sync are turned off in CCC? Can you try disabling Catalyst A.I. (uncheck the box)?

---

### Post by kamhagh on 2014-08-08
i disabled CC a.i i even lag harder now, VSync is disabled, and after getting non update drivers i still get spikes, 

also less fps, then update drivers !!!

i dont know how much FPS i get in spawn on windows but i get good fps on spawn on linux! with CS Ai disabled but it gets 70-20 when i get out, it also lag spikes even when i have good fps!

---

### Post by R33D3M33R on 2014-08-08
Does stutter happen when a new sound loads? For example a big explosion, somebody says something, and so on?

---

### Post by kamhagh on 2014-08-08
mostly happens at combat, i dont think it happens with a sound, 

i restored windows backup and downloaded 1.6 more files to play it on linux if it helps!

---

### Post by kamhagh on 2014-08-08
Oh , i didn't get it, yes , i guess yes it happened, but not surr, its 3 am i make sure tomarroe but gues it happened!

edit: i get 200-300 at spawn in windows, 100~ in middle of battle 160~ while going to fight !

---

### Post by kamhagh on 2014-08-09
im pretty sure the voice goes like this and fps is a lot less than windows and today it lags like hell:
"the enemy has stolen our reac reac reactor core !!!!"
"c c c c ccheers !" or "me e e e e dik !"

i also got this from console, but guess same happened with windows which i dont have problem with !
[I]
No caption found for 'soldier.go02' 
No caption found for 'pyro.medic01' 
No caption found for 'medic.autochargeready01' 
No caption found for 'pyro.medic01' 
No caption found for 'soldier.medic02' 
No caption found for 'pyro.medic01' 
[[/I]

---

### Post by kamhagh on 2014-08-09
im pretty sure the voice goes like this and fps is a lot less than windows and today it lags like hell:
"the enemy has stolen our reac reac reactor core !!!!"
"c c c c ccheers !" or "me e e e e dik !"

btw now i got constant lags, its like game is not smooth but voices were good, the sound stutter happend 1 time only from time i started playing today, but now i pressed c1 and game lagged and voice had stutter, it only happenes sometimes!

btw i think its more like my game goes slowmotion for short time!

---

### Post by R33D3M33R on 2014-08-09
Can you check the temperature of the card when this happens? Maybe its overheating in Linux. Also try setting the sound quality ingame to low. Is it better? What about turning off desktop effects?

For me the game stutters only sometimes at start when a new sound loads, but after playing for a while (a few minutes), the stutter seems to disappear. Here is more info: [http://ubuntuforums.org/showthread.php?t=2209704](http://ubuntuforums.org/showthread.php?t=2209704)

---

### Post by kamhagh on 2014-08-09
yes but other lags didn't make any slightly stutter but i check temp but i dont think its temp!, let me google how to do it in linux ! i will also try the sound quality, sutter only happens in game ! it takes a year to load the game :(

EDIT: i tried using low quality voice, still lags, even my mouse on menu, i also checked temp, they are 45~ normal.

the lag isn't always same kind, the game is just overally not smooth and anoyying!

---

### Post by R33D3M33R on 2014-08-09
Can you post the contents of file: /etc/X11/xorg.conf

---

### Post by kamhagh on 2014-08-09
theres no such file :o

but theres a file called corg.conf.failsafe that has this in it:

[I]Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection[/I]

---

### Post by R33D3M33R on 2014-08-09
Then run:

```
 sudo amdconfig --initial
```

Reboot and try running the game again. If it doesn't improve, then post the file contents here.

---

### Post by kamhagh on 2014-08-09
[I]Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

[/I]it still laged :(

---

### Post by R33D3M33R on 2014-08-09
If you disabled desktop effects and it didn't help, then the last thing I can advise you is: ```
sudo apt-get purge fglrx*
``` and ```
sudo apt-get install fglrx-updates
```. It might be a good idea to restart between purge and install, but remove /etc/X11/xorg.conf before restarting.

---

### Post by kamhagh on 2014-08-09
i already done that, no change, but can't remove the xorg.conf file :o i can't,

my firefox horribly tears too, any fix for that?

---

### Post by R33D3M33R on 2014-08-09
I found out that the 2D tearing/flickering usually happens if the memory clocks are set too low in desktop mode. Running:
```
 aticonfig --adapter=0 --od-getclocks
``` will show you the current clocks.


 It might be smart if you Alt+Tab out of your TF2 and run this command. The clocks should be at peak, if they aren't, this might be the cause of lag.

If you wan't to know what else aticonfig can do, you can run:

```
aticonfig --help
```

---

### Post by kamhagh on 2014-08-09
i already tried that before making xorg.cong, but i can't remove xorg.conf,

but also my firefox tears like hell, and when i scroll down, my video on right side lags LIKE HELL ! when i scroll

---

### Post by kamhagh on 2014-08-09
thanks i will try, also my python compilying is taking long and apps are slow(slow startup), whats wrong with my pc ! all happeneds after installing new graphics card , also windows got slow, the (super + w) takes a little long to load, it didn't used to

edit: heres result , clocks are ok, i will try with tf2 !

[I]Adapter 0 - AMD Radeon R7 200 Series                  
                            Core (MHz)    Memory (MHz)
           Current Clocks :    1020           1125
             Current Peak :    1020           1125
  Configurable Peak Range : [300-1300]     [150-1300]
                 GPU load :    31%
[/I]
31% is high for desktop :o but before that i got 8%

in middle of doing nothing my gpu usage goes really high sometimes !!!! like 78% while viewing stuff on sublime, it never laged on IGPU!

my gpu is 40% when playing tf2, and its weird that clock is always max no matter what !

i got update drivers and restarted,  i still get tearing, but freq is max at tf2, and perforamnce is same, even maybe worst, i remember updae drivers had a lo better performance !!!

oh god this is horrible, it even lags worst, maybe i should reinstall ubuntu,i wish i took an backup:(((((((( i dont want to download these agin, a week of staying awake till 3am

atleast i have to forget about playing tf2 on linux, can you help me fix sublime and tearing in firefox and lags problem? i dont remember anything like this on my old 7750 before it died !

edit: i used live cd and it doens't have tearing, dont have any apps to try on it but firefox doesn't even have slightest tearing !!! windows move smoothly

---

### Post by R33D3M33R on 2014-08-09
31% GPU load on desktop is way too high in idle.  Also, 40% GPU load when playing TF2 indicates that the Graphics card isn't even working at the highest potential. At this resolution and MSAA level, the usage should be close to 100%. Did you plug in the 1x6pin power connector properly? What power supply do you have?

Can you also run the command top and see if some program is overusing your CPU?

---

### Post by kamhagh on 2014-08-09
hmm on windows tf2 uses 30%-40% i guess, multicore is on,

tomb raider uses 99% gpu on windows so its not the problem ! its a GP650B-OC and im sure i connected power collectedly

EDIT: im on windows, i was wrong, it uses 80+% gpu!!!!

---

### Post by kamhagh on 2014-08-09
i found out something, my load is exactly the same with linux with VSync on, and the weird thing is the fps keeps jumping from 120 to 60 for less than a second and than staying 60, maybe the 2 VSyncs one is off and other one isn't so it's interrupting each other thats why i tear too ! because i get 30-40% usage with VSync on!

im kinda sure there's some other VSync enabled somewhere else!

do you have any idea?!

when it works on windows(near 100%) it means everything is fine, its a setting or driver prob in linux!

EDIT:

Dont know why results were diffrent but now it gives me 99% with no VSync available(while playing) and 50%with VSync enabled(it was 40% max on windwos i guess :( ) i get 0% at idle, !!! so everythings fine, and fps no longer jumps to 60fps and go back near 100 , with VSync sometimes my fps gets 28-30 

but anyway with or without VSync my game still get lag spikes, its so horrible, my game goes like slowmotion or.... do you have any idea what else it might be?:(

and sublime scrolling feels like 1fps, i dont remember any scrolling problem befroe i get new gpu or even maybe when i had 7750!

---

### Post by kamhagh on 2014-08-11
i was wrong i get 0% on desktop !!! and i was wrong again, its 99-80% gpu usage with tf2,

no program is overusing my cpu according to top, most cpu using program was compiz!

---

