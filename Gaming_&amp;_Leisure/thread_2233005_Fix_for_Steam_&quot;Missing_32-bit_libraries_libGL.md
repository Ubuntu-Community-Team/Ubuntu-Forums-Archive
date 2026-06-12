---
title: "Fix for Steam: &quot;Missing 32-bit libraries: libGL.so.1&quot;"
date: 2014-07-05
forum: Gaming &amp; Leisure
---

### Post by GreenRaccoon on 2014-07-05
Hey guys, I'm going to post a *SIMPLE* thread showing you *EXACTLY* how to fix this bug because I know it'll be a common one. Even if the black Terminal screen scares you, I was thorough enough in this guide that you'll be able to fix it without having any idea what you're doing. :biggrin:

This bug occurs when you install Steam on 64-bit Linux (such as 64-bit Ubuntu) on a computer that has an Intel/Nvidia processor. The problem's on Nvidia's end, not Steam's (from what I've heard).

1- If you haven't updated your computer in a while, [COLOR=#008000]copy[/COLOR] (ctrl+c) and [COLOR=#008000]paste[/COLOR] (ctrl+SHIFT+v) this (and then hit[COLOR=#008000] enter[/COLOR] to run it). If you don't know what this is, just do it. :):
```
sudo apt-get update && sudo apt-get -y upgrade
```
2- [COLOR=#0000ff]If you've installed Steam already[/COLOR], skip to step 3. [COLOR=#0000ff]If you haven't installed Steam[/COLOR], [COLOR=#008000]open Terminal[/COLOR] with ctrl+alt+t. Then [COLOR=#008000]copy[/COLOR] (ctrl+c) and [COLOR=#008000]paste[/COLOR] (ctrl+SHIFT+v) this (and then hit [COLOR=#008000]enter[/COLOR] to run it):
```
sudo apt-get install -y steam
```

3- Now for the fix. [COLOR=#008000]Copy[/COLOR] (ctrl+c) and [COLOR=#008000]paste[/COLOR] (ctrl+SHIFT+v) this to edit Steam's configuration file (and then hit [COLOR=#008000]enter[/COLOR] to run it):
```
sudo nano /etc/ld.so.conf.d/steam.conf
```
4- It'll probably be blank. [COLOR=#0000ff]If it's blank[/COLOR], paste these two lines. [COLOR=#0000ff]If it's[/COLOR] [COLOR=#0000ff]not blank[/COLOR], just paste these two lines to the very bottom. [COLOR=#008000]Copy[/COLOR] (ctrl+c) and [COLOR=#008000]paste[/COLOR] (ctrl+SHIFT+v) this (and then [COLOR=#008000]enter [/COLOR]to run it):
```
/usr/lib32
/usr/lib/i386-linux-gnu/mesa

```
5- Save it by hitting [COLOR=#008000]ctrl-x[/COLOR], then [COLOR=#008000]y[/COLOR], then [COLOR=#008000]enter[/COLOR].

6- Now [COLOR=#008000]copy[/COLOR] (ctrl+c) and [COLOR=#008000]paste[/COLOR] (ctrl+SHIFT+v) this (and then hit [COLOR=#008000]enter[/COLOR] to run it).:
```
sudo ldconfig
```
7- Finally, [COLOR=#008000]copy[/COLOR] (ctrl+c) and [COLOR=#008000]paste[/COLOR] (ctrl+SHIFT+v) this (and then hit [COLOR=#008000]enter[/COLOR] to run it). It reinstalls a Mesa/OpenGL library:
```
sudo apt-get install --reinstall libgl1-mesa-glx:i386
```
8- Open [COLOR=#008000]Steam,[/COLOR] download Team Fortress 2, and go kill some folks.

Source: [https://github.com/ValveSoftware/steam-for-linux/issues/321](https://github.com/ValveSoftware/steam-for-linux/issues/321)

---

### Post by sayvanfire on 2015-03-28
doesnt work

---

### Post by chronicfathead on 2015-04-05
> **sayvanfire said:**
> doesnt work

For me, I added the following step at point 7 above:

```
 sudo apt-get install --reinstall libgl1-mesa-dri:i386
```

After that Steam starts just fine for me on Elementary OS, but should be the same on Ubuntu and its derivatives.

---

### Post by erikroyall on 2015-04-15
For those who're being displayed this error even after following the suggestions from the posts above, try this:

```
sudo ln -s /usr/lib/i386-linux-gnu/mesa/libGL.so.1 /usr/lib/libGL.so.1
```

The problem is that the necessary 32-bit libraries can't be found by Steam on 64-bit Ubuntu (and its derivatives).

---

### Post by wally8 on 2015-04-16
wally@wally-Inspiron-N4050:~$  sudo apt-get install--reinstall libgl1-mesa-dri:i386
[sudo] password for wally: 
E: Invalid operation install--reinstall
wally@wally-Inspiron-N4050:~$

---

### Post by lrajat on 2015-04-19
This fixed the issue for me. Thanks !!

---

### Post by chronicfathead on 2015-04-20
I realised I had missed a space out between install --.

Try again with my command above.

---

### Post by mischivousmic on 2015-04-20
I've tried all of the above steps and I'm still getting this when I try to open steam
Steam needs to install these additional packages: 
    libgl1-mesa-dri:i386, libgl1-mesa-glx:i386, libc6:i386
[sudo] password for mike: 
...............................................................................................
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgl1-mesa-glx:i386 : Depends: libglapi-mesa:i386 (= 10.1.3-0ubuntu0.4)
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
Press return to continue: 


(Then when I hit return)

You are missing the following 32-bit libraries, and Steam may not run:
libGL.so.1



ubuntu 14.04 lts

---

### Post by mischivousmic on 2015-04-20
sudo apt-get install -y steam


I ran this again and now it works!

---

### Post by majoraccident99 on 2015-04-26
> **mischivousmic said:**
> sudo apt-get install -y steam


I ran this again and now it works!


this works for me too! thank you very much!

---

### Post by 2ignup on 2015-05-10
This is a solution that works:
sudo apt-get install libgl1-mesa-glx-lts-utopic:i386

---

### Post by wncwalker on 2015-05-16
This worked for me too.  Installing steam from the command line worked for me too.  For some reason Ubuntu software center failed to add the 32 bit libraries but installing using apt did.  Go figure.  Is the -y really necessary?

---

### Post by sffvba[e0rt on 2015-05-17
> **2ignup said:**
> This is a solution that works:
sudo apt-get install libgl1-mesa-glx-lts-utopic:i386

As far as I can recall this is all I had to do to fix this issue too.

---

### Post by Ipis_Boomz on 2015-07-11
[COLOR=#000000]This line work with me after a day of fixing it XD
> [/COLOR][COLOR=#000000]sudo apt-get install -y steam[/COLOR][COLOR=#000000]
[/COLOR]

---

### Post by Nirvana001 on 2015-07-12
> **wncwalker said:**
> This worked for me too.  Installing steam from the command line worked for me too.  For some reason Ubuntu software center failed to add the 32 bit libraries but installing using apt did.  Go figure.  Is the -y really necessary?

The -y is just the positive reply to the question apt-get asks

---

### Post by oldrocker99 on 2015-07-12
> **wncwalker said:**
> <snip>  Installing steam from the command line worked for me too.  For some reason Ubuntu software center failed to add the 32 bit libraries but installing using apt did.  Go figure.  Is the -y really necessary?

I just (after becoming annoyed with 15.10's little quirks (so sue me)) reinstallled 14.04. I used the command line to install Steam,```
sudo apt-get install steam
```and every dependency was also pulled in. Steam worked first time. One of the great many things about apt which I love.

---

### Post by campanella-alex on 2015-08-27
THANK YOU SO MUCH!

I have only had Linux for 2 or 3 days and this forum fixed all my problems!!!

---

### Post by reynardus on 2015-08-28
Had all the same issues and did al the same modifications, but it started to work for me when I entered the very first command which updated the system with 32 bit libraries...

Thanks!

---

### Post by festers on 2015-09-26
> **mischivousmic said:**
> sudo apt-get install -y steam


I ran this again and now it works!

After going through all the others this was the one that got me up and running, thank you.

Using 14.04, on a toshiba 10D

---

### Post by Jamstercool on 2015-10-08
This issue isn't fixed on my machine with Ubuntu 14. I followed the above procedure,steam starts ( with the usually message "OpenGL GLX context is not using direct rendering, which may cause performance problems.)

 But after I tried to run Robocraft I received error message ( Validate EACException - restart Robocraft)  and I have to use the system monitor to completely close robocraft and steam  ( the in game/steam exit doesn&#8217;t work) . 

Robocraft was running fine before I tried the above methods though I was getting the Open GLX performance message. 

Just letting people know in case the the same happens on their machine, as a few have said the above solution fixed their problem. It created more for me.

---

### Post by libertax on 2015-10-10
None of these are working for me either.

Running 14.04, and every time I run sudo apt-get update it says

    failed to fetch "long url" unable to find expected entry 'main/binary-1386/packages

either that, or when I do sudo apt-get install -y steam it says that it depends on some packages (libgl1-mesa-dri-i386) but it is not going to be installed

ive tried editing source.list too, but all it has in there are some links, and I couldn't find 1386 or i386 at all, even with ctrl + F

---

### Post by gutowskydaniel on 2015-11-23
It's working for me (without 7-th step), thanks!!

---

### Post by defiance5050 on 2015-11-29
I had the same issue and this helped! Re-ran this install steam command and steam popped right up. Thank you so much!!!

---

### Post by thomas76 on 2015-12-19
Wow thanks everyone! Post 10 got it working for me.

---

### Post by p.callan on 2016-01-01
Just confirming what wncwalker said:
> [COLOR=#000000]This worked for me too. Installing steam from the command line worked for me too. For some reason Ubuntu software center failed to add the 32 bit libraries but installing using apt did. Go figure[/COLOR]
Worked on Elementary OS 3.2 (Ubuntu 14.04)

---

### Post by toufel on 2016-01-18
The error went away with this simple command - 

> sudo apt-get install --reinstall steam

Hope it helps :-)

(My System - Ubuntu 14.04 LTS 64bit)

---

### Post by bledsoereese on 2016-02-13
You forgot to put a space in between "install" and "--reinstall"

---

### Post by xxxheadshot87xxx on 2016-02-22
whenever i try to install steam using the terminal it says Package steam is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source However the following package replaces it: steam-launcher E: Package 'steam' has no installation candidate     Before i tried to install using terminal i used software center but it kept saying i was missing the 32-bit libraries libc.so.6

---

### Post by jehu17 on 2016-03-09
sudo apt-get install --reinstall libgl1-mesa-dri:i386
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1089;&#1087;&#1080;&#1089;&#1082;&#1086;&#1074; &#1087;&#1072;&#1082;&#1077;&#1090;&#1086;&#1074;&#8230; &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
&#1055;&#1086;&#1089;&#1090;&#1088;&#1086;&#1077;&#1085;&#1080;&#1077; &#1076;&#1077;&#1088;&#1077;&#1074;&#1072; &#1079;&#1072;&#1074;&#1080;&#1089;&#1080;&#1084;&#1086;&#1089;&#1090;&#1077;&#1081;       
&#1063;&#1090;&#1077;&#1085;&#1080;&#1077; &#1080;&#1085;&#1092;&#1086;&#1088;&#1084;&#1072;&#1094;&#1080;&#1080; &#1086; &#1089;&#1086;&#1089;&#1090;&#1086;&#1103;&#1085;&#1080;&#1080;&#8230; &#1043;&#1086;&#1090;&#1086;&#1074;&#1086;
&#1053;&#1077;&#1082;&#1086;&#1090;&#1086;&#1088;&#1099;&#1077; &#1087;&#1072;&#1082;&#1077;&#1090;&#1099; &#1085;&#1077;&#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1080;&#1090;&#1100;. &#1042;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086;, &#1074;&#1099; &#1087;&#1088;&#1086;&#1089;&#1080;&#1090;&#1077; &#1085;&#1077;&#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086;&#1075;&#1086;,
&#1080;&#1083;&#1080; &#1078;&#1077; &#1080;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1091;&#1077;&#1090;&#1077; &#1085;&#1077;&#1089;&#1090;&#1072;&#1073;&#1080;&#1083;&#1100;&#1085;&#1091;&#1102; &#1074;&#1077;&#1088;&#1089;&#1080;&#1102; &#1076;&#1080;&#1089;&#1090;&#1088;&#1080;&#1073;&#1091;&#1090;&#1080;&#1074;&#1072;, &#1075;&#1076;&#1077; &#1079;&#1072;&#1087;&#1088;&#1086;&#1096;&#1077;&#1085;&#1085;&#1099;&#1077; &#1074;&#1072;&#1084;&#1080;
&#1087;&#1072;&#1082;&#1077;&#1090;&#1099; &#1077;&#1097;&#1105; &#1085;&#1077; &#1089;&#1086;&#1079;&#1076;&#1072;&#1085;&#1099; &#1080;&#1083;&#1080; &#1073;&#1099;&#1083;&#1080; &#1091;&#1076;&#1072;&#1083;&#1077;&#1085;&#1099; &#1080;&#1079; Incoming.
&#1057;&#1083;&#1077;&#1076;&#1091;&#1102;&#1097;&#1072;&#1103; &#1080;&#1085;&#1092;&#1086;&#1088;&#1084;&#1072;&#1094;&#1080;&#1103;, &#1074;&#1086;&#1079;&#1084;&#1086;&#1078;&#1085;&#1086;, &#1087;&#1086;&#1084;&#1086;&#1078;&#1077;&#1090; &#1074;&#1072;&#1084;:

&#1055;&#1072;&#1082;&#1077;&#1090;&#1099;, &#1080;&#1084;&#1077;&#1102;&#1097;&#1080;&#1077; &#1085;&#1077;&#1091;&#1076;&#1086;&#1074;&#1083;&#1077;&#1090;&#1074;&#1086;&#1088;&#1105;&#1085;&#1085;&#1099;&#1077; &#1079;&#1072;&#1074;&#1080;&#1089;&#1080;&#1084;&#1086;&#1089;&#1090;&#1080;:
 libgl1-mesa-dri:i386 : &#1047;&#1072;&#1074;&#1080;&#1089;&#1080;&#1090;: libc6:i386 (>= 2.17) &#1085;&#1086; &#1086;&#1085; &#1085;&#1077; &#1073;&#1091;&#1076;&#1077;&#1090; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;
                        &#1047;&#1072;&#1074;&#1080;&#1089;&#1080;&#1090;: libdrm-intel1:i386 (>= 2.4.48) &#1085;&#1086; &#1086;&#1085; &#1085;&#1077; &#1073;&#1091;&#1076;&#1077;&#1090; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;
                        &#1047;&#1072;&#1074;&#1080;&#1089;&#1080;&#1090;: libdrm-nouveau2:i386 (>= 2.4.38) &#1085;&#1086; &#1086;&#1085; &#1085;&#1077; &#1073;&#1091;&#1076;&#1077;&#1090; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;
                        &#1047;&#1072;&#1074;&#1080;&#1089;&#1080;&#1090;: libdrm-radeon1:i386 (>= 2.4.31) &#1085;&#1086; &#1086;&#1085; &#1085;&#1077; &#1073;&#1091;&#1076;&#1077;&#1090; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;
                        &#1047;&#1072;&#1074;&#1080;&#1089;&#1080;&#1090;: libdrm2:i386 (>= 2.4.38) &#1085;&#1086; &#1086;&#1085; &#1085;&#1077; &#1073;&#1091;&#1076;&#1077;&#1090; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;
                        &#1047;&#1072;&#1074;&#1080;&#1089;&#1080;&#1090;: libelf1:i386 (>= 0.142) &#1085;&#1086; &#1086;&#1085; &#1085;&#1077; &#1073;&#1091;&#1076;&#1077;&#1090; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;
                        &#1047;&#1072;&#1074;&#1080;&#1089;&#1080;&#1090;: libexpat1:i386 (>= 2.0.1) &#1085;&#1086; &#1086;&#1085; &#1085;&#1077; &#1073;&#1091;&#1076;&#1077;&#1090; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;
                        &#1047;&#1072;&#1074;&#1080;&#1089;&#1080;&#1090;: libgcc1:i386 (>= 1:4.1.1) &#1085;&#1086; &#1086;&#1085; &#1085;&#1077; &#1073;&#1091;&#1076;&#1077;&#1090; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;
                        &#1047;&#1072;&#1074;&#1080;&#1089;&#1080;&#1090;: libllvm3.4:i386 &#1085;&#1086; &#1086;&#1085; &#1085;&#1077; &#1073;&#1091;&#1076;&#1077;&#1090; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;
                        &#1047;&#1072;&#1074;&#1080;&#1089;&#1080;&#1090;: libstdc++6:i386 (>= 4.6) &#1085;&#1086; &#1086;&#1085; &#1085;&#1077; &#1073;&#1091;&#1076;&#1077;&#1090; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;
                        &#1056;&#1077;&#1082;&#1086;&#1084;&#1077;&#1085;&#1076;&#1091;&#1077;&#1090;: libtxc-dxtn-s2tc0:i386 &#1085;&#1086; &#1086;&#1085; &#1085;&#1077; &#1073;&#1091;&#1076;&#1077;&#1090; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085; &#1080;&#1083;&#1080;
                                                libtxc-dxtn0:i386
 unity-control-center : &#1047;&#1072;&#1074;&#1080;&#1089;&#1080;&#1090;: libcheese-gtk23 (>= 3.4.0) &#1085;&#1086; &#1086;&#1085; &#1085;&#1077; &#1073;&#1091;&#1076;&#1077;&#1090; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;
                        &#1047;&#1072;&#1074;&#1080;&#1089;&#1080;&#1090;: libcheese7 (>= 3.0.1) &#1085;&#1086; &#1086;&#1085; &#1085;&#1077; &#1073;&#1091;&#1076;&#1077;&#1090; &#1091;&#1089;&#1090;&#1072;&#1085;&#1086;&#1074;&#1083;&#1077;&#1085;
E: &#1054;&#1096;&#1080;&#1073;&#1082;&#1072;, pkgProblemResolver::Resolve &#1089;&#1075;&#1077;&#1085;&#1077;&#1088;&#1080;&#1088;&#1086;&#1074;&#1072;&#1083; &#1087;&#1086;&#1074;&#1088;&#1077;&#1078;&#1076;&#1105;&#1085;&#1085;&#1099;&#1077; &#1087;&#1072;&#1082;&#1077;&#1090;&#1099;. &#1069;&#1090;&#1086; &#1084;&#1086;&#1078;&#1077;&#1090; &#1073;&#1099;&#1090;&#1100; &#1074;&#1099;&#1079;&#1074;&#1072;&#1085;&#1086; &#1086;&#1090;&#1083;&#1086;&#1078;&#1077;&#1085;&#1085;&#1099;&#1084;&#1080; (held) &#1087;&#1072;&#1082;&#1077;&#1090;&#1072;&#1084;&#1080;.


Every "solution" listed above in this thread didn't work. Any ideas?

---

### Post by mglolenstine on 2016-03-11
You're missing the space between install and --reinstall.
Command should be following: sudo apt-get install --reinstall libgl1-mesa-dri:i386
or
sudo apt-get --reinstall install libgl1-mesa-dri:i386

---

### Post by erick-m-sepulveda on 2016-03-13
It works!!!! Thanks!!!!

---

### Post by MikeCyber on 2016-03-23
There are two steam packages. One from synaptic and the other download  from steam. I would remove all, including in your home the hidden steam  folder. 
cd ~
rm -rf .steam
Than try the other one.

---

### Post by aray81 on 2016-03-26
A big thank you to the helpful folks in this thread!  After a few missteps this Linux neophyte was able to get Steam up and running using the commands shown above.
Thank You!

---

### Post by epuckop on 2016-03-29
> **majoraccident99 said:**
> this works for me too! thank you very much!


And for me :D

---

### Post by mian-shahzad-raza on 2016-04-09
Hi guys,
Just installed Ubuntu today and came here with same error by googling when i run given commands i got following errors. really appreciate quick help 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libgl1-mesa-dri:i386 : Depends: libc6:i386 (>= 2.17) but it is not going to be installed
                        Depends: libdrm-intel1:i386 (>= 2.4.48) but it is not going to be installed
                        Depends: libdrm-nouveau2:i386 (>= 2.4.38) but it is not going to be installed
                        Depends: libdrm-radeon1:i386 (>= 2.4.31) but it is not going to be installed
                        Depends: libdrm2:i386 (>= 2.4.38) but it is not going to be installed
                        Depends: libelf1:i386 (>= 0.142) but it is not going to be installed
                        Depends: libexpat1:i386 (>= 2.0.1) but it is not going to be installed
                        Depends: libgcc1:i386 (>= 1:4.1.1) but it is not going to be installed
                        Depends: libllvm3.4:i386 but it is not going to be installed
                        Depends: libstdc++6:i386 (>= 4.6) but it is not going to be installed
                        Recommends: libtxc-dxtn-s2tc0:i386 but it is not going to be installed or
                                    libtxc-dxtn0:i386
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

---

### Post by The_Craft on 2016-06-01
Fixed my problem, smart fix with the steam.conf file :)

---

### Post by cj-fuzzl on 2016-07-22
This was the solution for me using Elementary OS Freya
> **erikroyall said:**
> For those who're being displayed this error even after following the suggestions from the posts above, try this:

```
sudo ln -s /usr/lib/i386-linux-gnu/mesa/libGL.so.1 /usr/lib/libGL.so.1
```

The problem is that the necessary 32-bit libraries can't be found by Steam on 64-bit Ubuntu (and its derivatives).

---

### Post by solaremoon on 2016-11-27
it didn't work for me, got to step 3 and it said the command doesn't exist, I made a thread about this, after i reset from this, so this is inacurate now and i dont know how to delete a reply so here: [https://ubuntuforums.org/showthread.php?t=2344700](https://ubuntuforums.org/showthread.php?t=2344700)

```
(precise)solaremoon@localhost:~$ sudo apt-get update
[sudo] password for solaremoon: 
Get:1 [http://repo.steampowered.com](http://repo.steampowered.com) precise Release.gpg [490 B]             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release.gpg                          
Get:2 [http://repo.steampowered.com](http://repo.steampowered.com) precise Release [2,303 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release.gpg
Get:3 [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Sources [550 B]
Get:4 [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam amd64 Packages [601 B]
Get:5 [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam i386 Packages [799 B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates Release
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam TranslationIndex        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe i386 Packages      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse i386 Packages    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main TranslationIndex       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse TranslationIndex 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted TranslationIndex 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe TranslationIndex   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Sources        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Sources  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Sources    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Sources  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main amd64 Packages 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Sources 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse amd64 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main i386 Packages 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/main Translation-en         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/multiverse Translation-en   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/restricted Translation-en   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise/universe Translation-en     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/main Translation-en 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/main Translation-en  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) precise-security/universe Translation-en
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en_US    
Ign [http://repo.steampowered.com](http://repo.steampowered.com) precise/steam Translation-en
Fetched 4,743 B in 8s (533 B/s)                                             
Reading package lists... Done
(precise)solaremoon@localhost:~$ sudo apt-get -y upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
(precise)solaremoon@localhost:~$ sudo nano /etc/ld.so.conf.d/steam.conf
sudo: nano: command not found
(precise)solaremoon@localhost:~$ sudo  /etc/ld.so.conf.d/steam.conf
sudo: /etc/ld.so.conf.d/steam.conf: command not found
(precise)solaremoon@localhost:~$ sudo /etc/ld.so.conf.d/steam.conf
sudo: /etc/ld.so.conf.d/steam.conf: command not found
(precise)solaremoon@localhost:~$ 
(precise)solaremoon@localhost:~$
```

---

### Post by xeacorn on 2017-03-01
works, thanks

---

### Post by andipc1996 on 2017-04-17
Thank's a ton man!
Now I can finally play my games, this worked like a charm. :cool:

---

### Post by masterg2 on 2017-10-04
> **erikroyall said:**
> For those who're being displayed this error even after following the suggestions from the posts above, try this:

```
sudo ln -s /usr/lib/i386-linux-gnu/mesa/libGL.so.1 /usr/lib/libGL.so.1
```

The problem is that the necessary 32-bit libraries can't be found by Steam on 64-bit Ubuntu (and its derivatives).

Hello all,

I add my own feedback, even if the post is old and has been [SOLVED], because I still encounter the error under Ubuntu Mate 16.04 and have found a shortcut so solve.

After installing original Ubuntu steam package ("sudo apt-get install steam"), the soft has laucnhed a first time, then successfully updated itself automatically.
At second lunch try, the libraries error has come up.

In my case, the "sudo ln -s ..." command indicated by **erikroyall** (many thanks!!!) has been enough for Steam to launch normally.

So, for a fresh install, just type these:

```
sudo ln -s /usr/lib/i386-linux-gnu/mesa/libGL.so.1 /usr/lib/libGL.so.1
```
```
sudo apt-get install steam
```

Hope this can simplify a bit all attempts to come ;)

Regards!

---

### Post by SponezillA on 2017-11-23
I was able to fix it with:

apt install nvidia-driver-libs:i386

---

### Post by sashwattanay on 2018-04-18
It works. Thank you!

---

### Post by rifwan-toenjoy on 2018-05-03
[COLOR=#000000]sudo apt-get install -y steam work for me[/COLOR]

---

### Post by giony123 on 2018-06-17
Thank you so much man it worked i've been trying for a week to fix it and you just gave me hope again

---

### Post by william-tambellini on 2019-04-27
> **giony123 said:**
> Thank you so much man it worked i've been trying for a week to fix it and you just gave me hope again

got that error after upgrading to nvidia drivers 418.40 : 

ldconfig -p | grep libGL.s
    libGL.so.1 (libc6,x86-64) => /usr/lib32/nvidia-418/libGL.so.1  <  BUG : that lib is supposed to be 32b !
    libGL.so.1 (libc6,x86-64) => /usr/lib/nvidia-418/libGL.so.1
    libGL.so (libc6,x86-64) => /usr/lib32/nvidia-418/libGL.so
    libGL.so (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libGL.so
    libGL.so (libc6,x86-64) => /usr/lib/nvidia-418/libGL.so

expected:
    libGL.so.1 (libc6,x86-64) => /usr/lib/nvidia-418/libGL.so.1
    libGL.so.1 (libc6) => /usr/lib32/nvidia-418/libGL.so.1

Upgrading to 418.56 seems to make steam work again.

---

