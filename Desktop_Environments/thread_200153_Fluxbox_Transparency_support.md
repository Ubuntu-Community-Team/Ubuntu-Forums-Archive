---
title: "Fluxbox Transparency support"
date: 2006-06-19
forum: Desktop Environments
---

### Post by brantleyr on 2006-06-19
I have followed a guide on here about compiling the latest fluxbox from their site. After compiling I cannot run xcompmgr or set things as transparent. When compiling Fluxbox how do I enable transparency?

---

### Post by Bossieman on 2006-06-19
I cant get transparentcy to work either. :confused:

---

### Post by brantleyr on 2006-06-20
I mean ive had it to work before in the past when I've self compiled fluxbox from their site but I dont know if its the latest of version of fluxbox thats not agreeing with transparency or something new they added, so on and so on. I was hoping someone here had compiled the latest version and could help me out a little. If i find a solution ill be sure to post it to help you out.

---

### Post by Bossieman on 2006-06-20
I compilled the v1.0RC1 version, everything works perfect except for transparentcy.

---

### Post by Ramses de Norre on 2006-06-20
I never got xcompmgr running.. I'm using fluxbox (from the repo) as my only wm so I don't know whether it works in others.
I think the problem here is my ati but I'm not sure.

---

### Post by Bossieman on 2006-06-20
From [www.fluxbox.org](www.fluxbox.org)
> 
   1.  You must be running a Fluxbox version 0.9.2 or newer. 0.1.x does not contain transparency support.
   2. Fluxbox must be restarted for changes in the alpha value to take effect (just choose restart in the menu).
   3. You need to have the XRender extension enabled in X, and compiled into fluxbox. Running fluxbox -i and xdpyinfo | grep RENDER should both say "RENDER".
   4. You must have set the background with an XRender-compatible tool. fbsetbg comes with fluxbox and tries to make this easy for you, try it (the web page also has list of transparency supporting background tools). Run fbsetbg -i to see if it can find a suitable tool. 


When I do step 3 this info arrives
> 
maja@bossieman:~$ fluxbox -i
Fluxbox version: 1.0rc
Compiled: Jun 19 2006 22:02:35
Compiler: GCC
Compiler version: 4.0.3 (Ubuntu 4.0.3-1ubuntu5)

Defaults:
    menu: /usr/local/share/fluxbox/menu
   style: /usr/local/share/fluxbox/styles/Clean
    keys: /usr/local/share/fluxbox/keys
    init: /usr/local/share/fluxbox/init

Compiled options (- => disabled):
-DEBUG
SLIT
TOOLBAR
XPM
-IMLIB2
GNOME
KDE
EWMH
REMEMBER
SHAPE
-XFT
-XMB
-XINERAMA
-RENDER

maja@bossieman:~$


So, how do I change -RENDER to RENDER?

---

### Post by Ramses de Norre on 2006-06-20
I guess that means recompiling for you..

---

### Post by Bossieman on 2006-06-20
Lets hope that it will work after recompiling.

---

### Post by Bossieman on 2006-06-20
I recompilled with this parameters.
> 
 ./configure --enable-kde --enable-gnome --disable-xmb --enable-RENDER


And the result is:
> 
maja@bossieman:~$ fluxbox -i 
Fluxbox version: 1.0rc
Compiled: Jun 20 2006 16:07:06
Compiler: GCC
Compiler version: 4.0.3 (Ubuntu 4.0.3-1ubuntu5)

Defaults:
    menu: /usr/local/share/fluxbox/menu
   style: /usr/local/share/fluxbox/styles/Clean
    keys: /usr/local/share/fluxbox/keys
    init: /usr/local/share/fluxbox/init

Compiled options (- => disabled):
-DEBUG
SLIT
TOOLBAR
XPM
-IMLIB2
GNOME
KDE
EWMH
REMEMBER
SHAPE
-XFT
-XMB
-XINERAMA
-RENDER

maja@bossieman:~$


Why doesnt it work?

---

### Post by brantleyr on 2006-06-20
My xdpy | grep RENDER reports RENDER and so does fluxbox -i , i am using the Fluxbox version 1.0rc, have never had transparency support with other fluxbox versions, xcompmgr is wut im mainly after but when i run it in a terminal it starts spamming errors until i close it out and everything goes black except the terminal and such, menu or toolbar transparency dosnt even work. But i have made sure its not xcompmgr because it works in all other WM's i have on this system. So it all points back to fluxbox.

---

### Post by ayoli on 2006-06-20
try :

```
./configure --enable-imlib2 --enable-xrender --enable-gnome --enable-kde
```

---

### Post by brantleyr on 2006-06-20
Wow Thanks man

I Ran:

> 
./configure --enable-imlib2 --enable-xrender --enable-kde --enable-gnome --disable-xmb

That worked perfect for me

---

### Post by ayoli on 2006-06-20
you're welcome, i just do a ./configure --help, read options thtat's all 8-)

---

### Post by brantleyr on 2006-06-20
well it all works now except for my background, when running xcompmgr I cant run a fbsetbg, dosnt work. But im making progress, has anyone else had this problem??

EDIT: Im back to the same errors as before :\ 

These are the errors I am receiving

> error 8 request 154 minor 4 serial 662
error 178 request 154 minor 8 serial 663
error 178 request 154 minor 8 serial 701
error 178 request 154 minor 8 serial 752
error 178 request 154 minor 8 serial 782
error 178 request 154 minor 8 serial 804
error 178 request 154 minor 8 serial 847
error 178 request 154 minor 8 serial 877
error 178 request 154 minor 8 serial 899
error 178 request 154 minor 8 serial 921
error 178 request 154 minor 8 serial 943
error 178 request 154 minor 8 serial 965
error 178 request 154 minor 8 serial 987
error 178 request 154 minor 8 serial 1009
error 178 request 154 minor 8 serial 1031
error 178 request 154 minor 8 serial 1053
error 178 request 154 minor 8 serial 1075
error 178 request 154 minor 8 serial 1097
error 178 request 154 minor 8 serial 1119
error 178 request 154 minor 8 serial 1141
error 178 request 154 minor 8 serial 1163
error 178 request 154 minor 8 serial 1185
error 178 request 154 minor 8 serial 1207
error 178 request 154 minor 8 serial 1229
error 178 request 154 minor 8 serial 1251
error 178 request 154 minor 8 serial 1273
error 178 request 154 minor 8 serial 1295
error 178 request 154 minor 8 serial 1317
error 178 request 154 minor 8 serial 1339
error 178 request 154 minor 8 serial 1361
error 178 request 154 minor 8 serial 1383
error 178 request 154 minor 8 serial 1405
error 178 request 154 minor 8 serial 1427
error 178 request 154 minor 8 serial 1449
error 178 request 154 minor 8 serial 1471
error 178 request 154 minor 8 serial 1493
error 178 request 154 minor 8 serial 1515
error 178 request 154 minor 8 serial 1537
error 178 request 154 minor 8 serial 1559
error 178 request 154 minor 8 serial 1581
error 178 request 154 minor 8 serial 1603
error 178 request 154 minor 8 serial 1625
error 178 request 154 minor 8 serial 1647
error 178 request 154 minor 8 serial 1669
error 178 request 154 minor 8 serial 1691
error 178 request 154 minor 8 serial 1713
error 178 request 154 minor 8 serial 1735
error 178 request 154 minor 8 serial 1757
error 178 request 154 minor 8 serial 1779
error 178 request 154 minor 8 serial 1801
error 178 request 154 minor 8 serial 1823
error 178 request 154 minor 8 serial 1845
error 178 request 154 minor 8 serial 1867
error 178 request 154 minor 8 serial 1889
error 178 request 154 minor 8 serial 1911
error 178 request 154 minor 8 serial 1933
error 178 request 154 minor 8 serial 1955
error 178 request 154 minor 8 serial 1977
error 178 request 154 minor 8 serial 1999
error 178 request 154 minor 8 serial 2021
error 178 request 154 minor 8 serial 2043
error 178 request 154 minor 8 serial 2065
error 178 request 154 minor 8 serial 2087
error 178 request 154 minor 8 serial 2109
error 178 request 154 minor 8 serial 2131
error 178 request 154 minor 8 serial 2153
error 178 request 154 minor 8 serial 2175
error 178 request 154 minor 8 serial 2197
error 178 request 154 minor 8 serial 2219
error 178 request 154 minor 8 serial 2241
error 178 request 154 minor 8 serial 2263
error 178 request 154 minor 8 serial 2285
error 178 request 154 minor 8 serial 2307
error 178 request 154 minor 8 serial 2329
error 178 request 154 minor 8 serial 2351
error 178 request 154 minor 8 serial 2373
error 178 request 154 minor 8 serial 2395
error 178 request 154 minor 8 serial 2417
error 178 request 154 minor 8 serial 2439
error 178 request 154 minor 8 serial 2461
error 178 request 154 minor 8 serial 2483
error 178 request 154 minor 8 serial 2505
error 178 request 154 minor 8 serial 2527
error 178 request 154 minor 8 serial 2549
error 178 request 154 minor 8 serial 2571
error 178 request 154 minor 8 serial 2593
error 178 request 154 minor 8 serial 2615
error 178 request 154 minor 8 serial 2637
error 178 request 154 minor 8 serial 2659
error 178 request 154 minor 8 serial 2681
error 178 request 154 minor 8 serial 2703
error 178 request 154 minor 8 serial 2725
error 178 request 154 minor 8 serial 2747
error 178 request 154 minor 8 serial 2769
error 178 request 154 minor 8 serial 2791
error 178 request 154 minor 8 serial 2813
error 178 request 154 minor 8 serial 2835
error 178 request 154 minor 8 serial 2857
error 178 request 154 minor 8 serial 2879
error 178 request 154 minor 8 serial 2901
error 178 request 154 minor 8 serial 2923
error 178 request 154 minor 8 serial 2945
error 178 request 154 minor 8 serial 2967
error 178 request 154 minor 8 serial 2989
error 178 request 154 minor 8 serial 3011
error 178 request 154 minor 8 serial 3033
error 178 request 154 minor 8 serial 3055
error 178 request 154 minor 8 serial 3077
error 178 request 154 minor 8 serial 3099
error 178 request 154 minor 8 serial 3121
error 178 request 154 minor 8 serial 3143
error 178 request 154 minor 8 serial 3165
error 178 request 154 minor 8 serial 3187
error 178 request 154 minor 8 serial 3209
error 178 request 154 minor 8 serial 3231
error 178 request 154 minor 8 serial 3253
error 178 request 154 minor 8 serial 3275
error 178 request 154 minor 8 serial 3297
error 178 request 154 minor 8 serial 3319
error 178 request 154 minor 8 serial 3341
error 178 request 154 minor 8 serial 3363
error 178 request 154 minor 8 serial 3385
error 178 request 154 minor 8 serial 3407
error 178 request 154 minor 8 serial 3429
error 178 request 154 minor 8 serial 3451
error 178 request 154 minor 8 serial 3473
error 178 request 154 minor 8 serial 3495
error 178 request 154 minor 8 serial 3517
error 178 request 154 minor 8 serial 3539
error 178 request 154 minor 8 serial 3561
error 178 request 154 minor 8 serial 3583
error 178 request 154 minor 8 serial 3605
error 178 request 154 minor 8 serial 3627
error 178 request 154 minor 8 serial 3649
error 178 request 154 minor 8 serial 3671
error 178 request 154 minor 8 serial 3693
error 178 request 154 minor 8 serial 3715
error 178 request 154 minor 8 serial 3737
error 178 request 154 minor 8 serial 3759
error 178 request 154 minor 8 serial 3781
error 178 request 154 minor 8 serial 3803
error 178 request 154 minor 8 serial 3825
error 178 request 154 minor 8 serial 3847
error 178 request 154 minor 8 serial 3869
error 178 request 154 minor 8 serial 3891
error 178 request 154 minor 8 serial 3913
error 178 request 154 minor 8 serial 3935
error 178 request 154 minor 8 serial 3957
error 178 request 154 minor 8 serial 3979
error 178 request 154 minor 8 serial 4001
error 178 request 154 minor 8 serial 4023
error 178 request 154 minor 8 serial 4045
error 178 request 154 minor 8 serial 4067
error 178 request 154 minor 8 serial 4089
error 178 request 154 minor 8 serial 4111
error 178 request 154 minor 8 serial 4133
error 178 request 154 minor 8 serial 4155
error 178 request 154 minor 8 serial 4177
error 178 request 154 minor 8 serial 4199
error 178 request 154 minor 8 serial 4221
error 178 request 154 minor 8 serial 4243
error 178 request 154 minor 8 serial 4265
error 178 request 154 minor 8 serial 4287
error 178 request 154 minor 8 serial 4309
error 178 request 154 minor 8 serial 4331
error 178 request 154 minor 8 serial 4353
error 178 request 154 minor 8 serial 4375
error 178 request 154 minor 8 serial 4397
error 178 request 154 minor 8 serial 4419
error 178 request 154 minor 8 serial 4441
error 178 request 154 minor 8 serial 4463
error 178 request 154 minor 8 serial 4485
error 178 request 154 minor 8 serial 4507
error 178 request 154 minor 8 serial 4529
error 178 request 154 minor 8 serial 4551

And it keeps going and going and going and going.....

---

### Post by key on 2006-08-11
Hello fellow fluxboxers,
If you want the standard fluxbox alpha blending in 1.0rc2 (not the fancy xcompmgr stuff) and you are sure you compiled everything correctly, make sure the 'Force Psuedo-Transparancy' box is checked under configuration-> transparency. 

I don't think this option is present in the ubuntu v0.9 fluxbox menus.

key

---

### Post by willca on 2007-04-08
I've been tinkering on this for a while. Like the rest of the folks on this thread I downloaded the latest release from fluxbox.org and compiled it with --enable-xrender but it doesnt seem to have the RENDER feature when I ran fluxbox -i though xdpyinfo says I have that ability built into my X11.

Here are the caveats:
1- I installed the Edgy repository for fluxbox which is

~$ dpkg -l | grep -i fluxbox
ii  fluxbox                                    0.9.15.1+1.0rc2-1                    Highly configurable and low resource X11 Window manage

2- After I compile the 1.0rc3 from fluxbox.org dpkg still tells me I have this 0.9.15 installed.

3- Check how many fluxbox binary you have.
/usr/bin/fluxbox
/usr/local/bin/fluxbox

Run each one of those fluxbox binaries with the -i and -v (which will tell you which one you compiled) and use the one with RENDER support.

How do I make mine forceably use the one with RENDER support?

vi /home/yourusername/.fluxbox/startup and have at least these 2 useful lines.
/usr/bin/fbsetbg -l &
sleep 1
exec /usr/bin/fluxbox -log ~/.fluxbox/log

** For me, I found out /usr/bin/fluxbox is the one with RENDER support and the one I compiled.

HTH
-W

[www.boondoons.com](www.boondoons.com)

---

### Post by snakyjake on 2007-04-18
I'm on RC3 now from [http://www.fluxbox.org](http://www.fluxbox.org).  When I enable transparency by pseudo-transparency and by changing the alphas, the only thing that changes in the top title bar (for either the menu, window, or toolbar).

For example, for the menu alpha, it's only the top portion of the title, but not the entire window.   Same with focused and unfocused window alpha settings.  It's just the window title bar, but not the entire window itself.

Should I be expecting total window transparency, or just the title bar?

If the entire window should be transparent, what do I need to do make this work.  I have "RENDER" in all the proper places as described on the sites.  I do not have a background though, but pseudo-transparency works.

Thank you,

Jake

---

### Post by RedSquirrel on 2007-04-18
> **snakyjake said:**
> I'm on RC3 now from [http://www.fluxbox.org](http://www.fluxbox.org).  When I enable transparency by pseudo-transparency and by changing the alphas, the only thing that changes in the top title bar (for either the menu, window, or toolbar).

For example, for the menu alpha, it's only the top portion of the title, but not the entire window.   Same with focused and unfocused window alpha settings.  It's just the window title bar, but not the entire window itself.

Should I be expecting total window transparency, or just the title bar?

If the entire window should be transparent, what do I need to do make this work.  I have "RENDER" in all the proper places as described on the sites.  I do not have a background though, but pseudo-transparency works.

Thank you,

Jake


That's the extent of transparency in Fluxbox. 

To have a transparent menu, you need to install a decent wallpaper program. feh is a nice one:

```
sudo apt-get update
sudo apt-get install feh

```

If you want *full window transparency*, you can play around with xcompmgr and transset. They're both in the repos. They are rather slow, especially on old hardware.

---

### Post by RedSquirrel on 2007-04-18
> **willca said:**
> I've been tinkering on this for a while. Like the rest of the folks on this thread I downloaded the latest release from fluxbox.org and compiled it with --enable-xrender but it doesnt seem to have the RENDER feature when I ran fluxbox -i though xdpyinfo says I have that ability built into my X11.

Here are the caveats:
1- I installed the Edgy repository for fluxbox which is

~$ dpkg -l | grep -i fluxbox
ii  fluxbox                                    0.9.15.1+1.0rc2-1                    Highly configurable and low resource X11 Window manage

2- After I compile the 1.0rc3 from fluxbox.org dpkg still tells me I have this 0.9.15 installed.

3- Check how many fluxbox binary you have.
/usr/bin/fluxbox
/usr/local/bin/fluxbox

Run each one of those fluxbox binaries with the -i and -v (which will tell you which one you compiled) and use the one with RENDER support.

How do I make mine forceably use the one with RENDER support?

vi /home/yourusername/.fluxbox/startup and have at least these 2 useful lines.
/usr/bin/fbsetbg -l &
sleep 1
exec /usr/bin/fluxbox -log ~/.fluxbox/log

** For me, I found out /usr/bin/fluxbox is the one with RENDER support and the one I compiled.

HTH
-W

[www.boondoons.com]("http://www.boondoons.com")


The one from the repos (1.0rc2) has RENDER support. If you compiled your own Fluxbox and didn't pass any flags to the configure script, RENDER is compiled in by default.

In the future, you might want to have only one Fluxbox installed on your system.

It's best to use "sudo checkinstall" instead of "sudo make install". checkinstall will build a deb package so that you can install it and remove it any time you want.

If you have the version from the repos installed, it's just a matter of doing 

```
sudo apt-get remove fluxbox
```That will leave most of the configuration files in place but removes the program itself.

When you have finished compiling (after make), do:

```
sudo checkinstall
```which will create and install a Fluxbox deb package from the code you compiled. Later, if you don't want it anymore or you want to compile a new version, you can remove it with:

```
sudo dpkg -r fluxbox
```If you do some searches on these forums for "compiling fluxbox" and/or "compile fluxbox" you will find lots of useful information. :)

---

