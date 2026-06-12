---
title: "ETQW: Linux full client is out"
date: 2007-10-19
forum: Gaming &amp; Leisure
---

### Post by almostlinux on 2007-10-19
[http://community.enemyterritory.com/?q=node/185](http://community.enemyterritory.com/?q=node/185)


The linux version [doesn't have]("http://community.enemyterritory.com/forums/showpost.php?p=162260&postcount=24") in-game ads!! :)

---

### Post by Sockerdrickan on 2007-10-19
Cool :D:D

---

### Post by Wiebelhaus on 2007-10-19
Hella sweet!

---

### Post by BoardDWorld on 2007-10-19
This news has been in the Forums for the last 3 days:lolflag:

---

### Post by almostlinux on 2007-10-19
> **BoardDWorld said:**
> This news has been in the Forums for the last 3 days:lolflag:

Really? The full client was released just an hour ago.

---

### Post by Perfect Storm on 2007-10-19
almostlinux is right. The 3 day old news was for the demo.
(news posted on UGA).

---

### Post by BoardDWorld on 2007-10-19
> **Artificial Intelligence said:**
> almostlinux is right. The 3 day old news was for the demo.
(news posted on UGA).

Yes, my bad. It's nearly 4am, better go to bed so I can read!

---

### Post by Ek0nomik on 2007-10-19
Only 17.9MB?

---

### Post by Perfect Storm on 2007-10-19
You need to buy the CDs as well, which contains the data files.

---

### Post by Ek0nomik on 2007-10-19
> **Ek0nomik said:**
> Only 17.9MB?

Ah.  Nevermind.  Copies it from the purchased DVD.  :)

---

### Post by Naegling23 on 2007-10-19
sweet, now I wonder what everyone will be doing all weekend....hmmm

and on a side note, now the ubuntu gaming forums can resume the normal threads, that is, 57 different topics on why someones WoW wont play.

---

### Post by Sockerdrickan on 2007-10-19
hahaha right!

---

### Post by Ek0nomik on 2007-10-19
Where does the Linux version store your profile config files?  My sdnet folder is empty, but yet it is remembering my resolution settings, account name, etc.

---

### Post by almostlinux on 2007-10-19
> **Ek0nomik said:**
> Where does the Linux version store your profile config files?  My sdnet folder is empty, but yet it is remembering my resolution settings, account name, etc.

It's a hidden folder in your home directory.
~/.etqw

---

### Post by Ek0nomik on 2007-10-19
> **almostlinux said:**
> It's a hidden folder in your home directory.
~/.etqw

Ah. It's actually .etqwcl, but thanks.  :)

---

### Post by Sparckus on 2007-10-19
Nice :D

All i need now are the new ATI drivers (when they get round to releasing them :() and for my net connection to stop dropping every 2 minutes #-o

---

### Post by GooglieS on 2007-10-19
Does anybody have any problems with in-game performance? It feels that FPS is about 50% lower than in windows version... I have a c2d e6750 CPU, 2gb ram and 8600GTS video card and new ubuntu 7.10

---

### Post by aidanr on 2007-10-19
Works great! Seems to be on a par with windows performance but I haven't done any proper tests. The Makron is pleased :)

---

### Post by Megatog615 on 2007-10-19
Mine segfaults :(.
```
$ ./etqw
Segmentation fault (core dumped)
```

---

### Post by daimaru on 2007-10-20
mine runs better than under windows (fps wise) but i dont have sound. using sennheiser USB headset with alsa, works fine with normal gnome apps, but not with etqw. i found something in the etqwconfig.cfg file where one might maybe change the driver, but i dont know enough to start tampering with the cfg. ```
seta s_driver "alsa"
seta s_dsp "/dev/dsp"
seta s_alsa_lib "libasound.so.2"
```

anyone know how to get sound to work?
thx

oh just found this in console during game start.
```
Initializing class hierarchy
...166 classes, 441320 bytes for event callbacks
WARNING: Couldn't load sound 'video/intro_1024x512.theora', defaulting
WARNING: idDeclLocal::ParseLocal Failed to Parse decl 'video/intro' in file 'sounds/cinematics.sndshd' line 0
game initialized.
```

---

### Post by shad0w_walker on 2007-10-20
Runs lovely and fast for me (Turned everything upto high and still no performance issues) and now i have a use for it I have even setup SLI again, not seeing any lesser performance than I did on Windows, possibly a little higher but I am not a great benchmark.

---

### Post by JG53_Jaguar on 2007-10-20
Hi All,

Sorry for a silly question but how do I install/run the linux client ?

Once I unzipped the file I get ETQW-client-1.1.r8.x86.run file. I noticed that this file doesn't have execute attribute so I did chmod +x on it. I then typed:

sudo ./ETQW-client-1.1.r8.x86.run

the terminal prompts me for my account password but then I get the following error message:

"sudo: unable to execute ./ETQW-client-1.1.r8.x86.run: No such file or directory"


if I don't do chmod+x and just do the sudo command I get the following error message "sudo: ./ETQW-client-1.1.r8.x86.run: command not found"

Please help, thanks!

---

### Post by daimaru on 2007-10-20
> **JG53_Jaguar said:**
> Hi All,

Sorry for a silly question but how do I install/run the linux client ?

Thanks!

download then

chmod +x ETQW-client-1.1.r8.x86.run
./ETQW-client-1.1.r8.x86.run

---

### Post by JG53_Jaguar on 2007-10-20
> **daimaru said:**
> download then

chmod +x ETQW-client-1.1.r8.x86.run
./ETQW-client-1.1.r8.x86.run

I did that and I get this error:

"bash: ./ETQW-client-1.1.r8.x86.run: No such file or directory"

the file is there, and it does have execute attribute

---

### Post by daimaru on 2007-10-20
sorry didnt see your post i'd recommend redownloading, just tried it again on my machine and it works np.. 
md5sum: 
89210dadaf7b55842fe1472dafac7cf8  ETQW-client-1.1.r8.x86.run

oh just remembered in case redownloading does not work. i turned off apparmor because it messed with my antivir install so maybe that is messing with your install. dunno though dont really know anything about apparmor

---

### Post by JG53_Jaguar on 2007-10-20
> **daimaru said:**
> sorry didnt see your post i'd recommend redownloading, just tried it again on my machine and it works np.. 
md5sum: 
89210dadaf7b55842fe1472dafac7cf8  ETQW-client-1.1.r8.x86.run

oh just remembered in case redownloading does not work. i turned off apparmor because it messed with my antivir install so maybe that is messing with your install. dunno though dont really know anything about apparmor

I have deleted the file; downloaded it again from here 

[http://www.sciboy.com/files/ETQW-client-1.1.r8.x86.run](http://www.sciboy.com/files/ETQW-client-1.1.r8.x86.run)

I did the chmod +x on it and then I run it as you suggested...no go
I still get "bash: ./ETQW-client-1.1.r8.x86.run: No such file or directory"

I installed 7.10 yesterday, clean install. I have OpenGL driver installed as well...

---

### Post by JG53_Jaguar on 2007-10-20
> **daimaru said:**
> 
oh just remembered in case redownloading does not work. i turned off apparmor because it messed with my antivir install so maybe that is messing with your install. dunno though dont really know anything about apparmor

I didn't install that on my own...is it part of the default install ? How do I turn the thing ???

Thanks!

---

### Post by daimaru on 2007-10-20
ok i have no idea if this will work cause me noob too, but i'd like to know if it does. 
Disable AppArmor framework

```
sudo /etc/init.d/apparmor kill
sudo update-rc.d -f apparmor remove

```

got this form the apparmor page here: [https://help.ubuntu.com/community/AppArmor#head-ae986cdc853786be814f277c654a7e4c609d6583]("https://help.ubuntu.com/community/AppArmor#head-ae986cdc853786be814f277c654a7e4c609d6583")

your supposed to be able to enable it afterwards again, which did not work for me yet , havent restarted or anything + plus i installed the dazuko module maybe thats conflicting with apparmor module.

---

### Post by daimaru on 2007-10-20
@JG53_Jaguar
if u get ur game to run and if your sound works (mine sadly does not) could you post your ~/.etqwcl/base/etqwconfig.cfg file contents plz cause thats about the only file where i found sound driver stuff so maybe it helps me.

---

### Post by JG53_Jaguar on 2007-10-20
> **daimaru said:**
> @JG53_Jaguar
if u get ur game to run and if your sound works (mine sadly does not) could you post your ~/.etqwcl/base/etqwconfig.cfg file contents plz cause thats about the only file where i found sound driver stuff so maybe it helps me.

I did remove the apparmor as you suggested. I downloaded the file again, then did the chmod +x on it and then ./xxx.run  and still no go.

I get the error message "bash: ./ETQW-client-1.1.r8.x86.run: No such file or directory"

It shouldn't be a rocket science to run a file on linux!

I have Dell Mobile Precision Workstation M90, Core 2 Duo (T7200, 2Ghz), 2GB of ram and nVidia FX2500M video card 512MB ram (basically 7900GTX configured for 3D professional graphics)

once I get the damn thing running I will post the sound config, no problem :)

---

### Post by Curlydave on 2007-10-20
I'm getting the error

""ETQW-demo-client-1.1-full.r5.x86.run" cannot be opened. No application suitable for automatic installation is available for handling this kind of file." If I sudo sh it in the terminal, I get the error "/home/david/Desktop/ETQW-client-1.1.r8.x86.run: 1: Syntax error: "(" unexpected"


I downloaded the demo client last night, and the had the same problem as with the full upgrade client. Any ideas?


> **JG53_Jaguar said:**
> I did remove the apparmor as you suggested. I downloaded the file again, then did the chmod +x on it and then ./xxx.run  and still no go.

I get the error message "bash: ./ETQW-client-1.1.r8.x86.run: No such file or directory"

It shouldn't be a rocket science to run a file on linux!

I have Dell Mobile Precision Workstation M90, Core 2 Duo (T7200, 2Ghz), 2GB of ram and nVidia FX2500M video card 512MB ram (basically 7900GTX configured for 3D professional graphics)

once I get the damn thing running I will post the sound config, no problem :)

Same error here if I run it using ".". I'm also from a fresh install I just put on yesterday. Eagerly waiting a solution.

---

### Post by Curlydave on 2007-10-20
I have a fix. Don't use ".", or double click, just enter the directory/filename in the console with sudo, without the dot.



The game run's great, except for some nasty mouse lag. Any ideas?

---

### Post by JG53_Jaguar on 2007-10-20
> **Curlydave said:**
> I have a fix. Don't use ".", or double click, just enter the directory/filename in the console with sudo, without the dot.



The game run's great, except for some nasty mouse lag. Any ideas?

Well that doesn't work either... I have downloaded it again and run as you suggested and I get "sudo: ETQW-client-1.1.r8.x86.run: command not found"

I just don't understand if I just have a simple clean ubuntu 7.10 installed why it works for others and why it doesn't work for me....this is crazy!

What version of Ubuntu are you using ? did you make any changes to the OS ?

OK Here is another question: I have the ETQW in the DVDROM drive and as well as the linux client...is the linux client the first thing that needs to run on linux ?

---

### Post by Curlydave on 2007-10-20
Yes, you run it, then it will copy files from the DVD. 

To clarify, here's what you should be running, if its on your desktop

> sudo /home/YOURLOGINNAME/Desktop/ETQW-client-1.1.r8.x86.run

---

### Post by marquarc on 2007-10-20
I'm having the exact same problem. Fresh install, using amd64 desktop 7.10.

> 
plasticus@tarrasque:~/Desktop/download$ sudo sh /home/plasticus/Desktop/download/ETQW-client-1.1.r8.x86.run
/home/plasticus/Desktop/download/ETQW-client-1.1.r8.x86.run: 1: Syntax error: "(" unexpected


have tried use ./ETQW... in the current directory, have tried with and without sudo, and have tried modifying the permissions on the file. nothing's working, yet.

SOLVED FOR ME:
Scratch that, I got mine figured out. I guess after I changed the permissions to allow it to be executed as a program, then typing the "sudo ./ETQW-client-1.1.r8.x86.run" worked out alright for me. Of course, I was using a terminal and was already working from the directory containing said file.

---

### Post by JG53_Jaguar on 2007-10-20
Ok Guys, I have solved my problem based on this thread:

[http://ubuntuforums.org/showthread.php?t=583762](http://ubuntuforums.org/showthread.php?t=583762)

The key was this: **"sudo apt-get install ia32-libs"**

I have 64bit CPUs (Intel Core 2 Duo) so I installed 64bit verion of Ubunu 7.10. And the reason why I couldn't get the ETQW linux client installed was because the client is in 32bit!!!

So after I installed the 32bit libraries all my problems went away!!!

Holly smokes this game rocks on Linux :) I maxed out all the graphics using 1900x1280 resolution, with 5.1 sound and it is very fast !!! My system:

Dell Precision Mobile Workstation M90
Intel Core 2 Duo T7200 CPU - 2Ghz
2GB DDR2 667Mhz RAM
1900 x 1280 Widescreen LCD
nVidia Quadro FX 2500M - 512MB of ram (basically 7900 GTX tweaked for professional graphics)
SIGMATEL STAC 92XX C-Major HD Audio System

My sound is very clean and I don't have quality problem with the sound even in the thick of the action, I'm very impressed with Ubuntu 7.10 and ETQW!!! :)

---

### Post by Naegling23 on 2007-10-20
Is there any thought of having an ubuntu/linux gamer server/clan?

Judging by the activity here, I think there is interest if someone wants to "run" it

---

### Post by mb108 on 2007-10-20
I'd be interested, for sure. I don't have a lot of time to run things, but in about a month I'll be happy to be more involved.

For now we could just agree upon a clan tag and wear it? Ubuntu only or all-Linux inclusive?

---

### Post by KhaaL on 2007-10-21
.Ubuntu as a clantag on the end of the name, perhaps? Make sure to color it brown/orange, and I'll see ya ingame :p

(My ingame nick is BlackEyez)

---

### Post by KhaaL on 2007-10-21
Okay, created a ubuntu clan, name is "Ubuntu". Post your screenname so I can send you guys invites

---

### Post by Naegling23 on 2007-10-21
> **KhaaL said:**
> Okay, created a ubuntu clan, name is "Ubuntu". Post your screenname so I can send you guys invites

count me in

im naegling23 in game as well.

---

### Post by mb108 on 2007-10-21
[quote=TTimo]
We're going to setup a game to celebrate the Linux release, I am gathering up some players. We'll play tonight (Sunday 10/21 8pm CDT) .. likely on the id servers, I'm still working out the details, I'll post more later.[/quote]

[http://community.enemyterritory.com/forums/showthread.php?t=14032&page=6](http://community.enemyterritory.com/forums/showthread.php?t=14032&page=6)

:D


My ETQW tag is Madnis.

---

### Post by balleklorin on 2007-10-22
**Found a solution to my previous Core dump: Reinstalled Nvidia drivers after ia32-libs took care of the problem!**

Core dump.... ;(

--------------------------------------------------------
This system qualifies for Normal quality.
Initializing SDL subsystem
Loading GL driver 'libGL.so.1' through SDL
Segmentation fault (core dumped)
--------------------------------------------------------

Gutsy 7.10 x64

---

### Post by KhaaL on 2007-10-22
Whee, the clan is now at the magic number 3! :D 

(btw, i'd love to have some europeans join so I don't feel like a hermit)

---

### Post by go_beep_yourself on 2007-10-23
> **JG53_Jaguar said:**
> I did that and I get this error:

"bash: ./ETQW-client-1.1.r8.x86.run: No such file or directory"

the file is there, and it does have execute attribute

find ~/ -iname 'etqw*run' -exec bash -c "sudo chmod a+x {} && sudo ./{}" \;

---

### Post by go_beep_yourself on 2007-10-23
Is anyone playing this game with hamachi? PM me if you are.

---

### Post by Ripfox on 2007-10-23
Is this playable as a one person game or is there no story line and just another mmo fps?

---

### Post by KhaaL on 2007-10-23
> **ripfox said:**
> Is this playable as a one person game or is there no story line and just another mmo fps?

No real storyline no. And I haven't tried the bots AI offline, so I can't say either if it's on par with Unreals bots.

---

### Post by Ripfox on 2007-10-23
Man I wish someone would release a fps action adventure with a beginning and end for linux...

---

### Post by aidanr on 2007-10-23
> **ripfox said:**
> Is this playable as a one person game or is there no story line and just another mmo fps?

It's a multiplayer game but you can play with bots offline and the bots are very good.

> **ripfox said:**
> Man I wish someone would release a fps action adventure with a beginning and end for linux...

You mean like Doom3 or Quake4 or Penumbra Overture...

---

### Post by silentrhythm on 2007-10-24
Thank you! I was thinking it was an issue with 64-bit, due to the x86 in the file name. Had no idea what to do to fix it though. Installed the 32-bit libraries you mentioned and it worked perfectly.

I just upgraded my system with similar specs, X2 4400+, 2gb ram, nvidia 8500gt, 22" 1680x1050 monitor.

the game is crazy! lots going on, but very cool.

> **JG53_Jaguar said:**
> Ok Guys, I have solved my problem based on this thread:

[http://ubuntuforums.org/showthread.php?t=583762](http://ubuntuforums.org/showthread.php?t=583762)

The key was this: **"sudo apt-get install ia32-libs"**

I have 64bit CPUs (Intel Core 2 Duo) so I installed 64bit verion of Ubunu 7.10. And the reason why I couldn't get the ETQW linux client installed was because the client is in 32bit!!!

So after I installed the 32bit libraries all my problems went away!!!

Holly smokes this game rocks on Linux :) I maxed out all the graphics using 1900x1280 resolution, with 5.1 sound and it is very fast !!! My system:

Dell Precision Mobile Workstation M90
Intel Core 2 Duo T7200 CPU - 2Ghz
2GB DDR2 667Mhz RAM
1900 x 1280 Widescreen LCD
nVidia Quadro FX 2500M - 512MB of ram (basically 7900 GTX tweaked for professional graphics)
SIGMATEL STAC 92XX C-Major HD Audio System

My sound is very clean and I don't have quality problem with the sound even in the thick of the action, I'm very impressed with Ubuntu 7.10 and ETQW!!! :)

---

### Post by Ripfox on 2007-10-25
> **aidanr said:**
> It's a multiplayer game but you can play with bots offline and the bots are very good.



You mean like Doom3 or Quake4 or Penumbra Overture...

Too bad none of those work with my intel graphics under Ubuntu. I see a very wide open market for this sort of game, hopefully more to come.

---

### Post by NJN on 2007-10-26
> **GooglieS said:**
> Does anybody have any problems with in-game performance? It feels that FPS is about 50% lower than in windows version... 

I was seeing noticeably lower FPS under Gutsy compared to Windows.  After a bit of searching, I found a thread on the ETQW forums that suggested using nice to start it at -15.  That looks to do the trick for my system.

---

### Post by Naegling23 on 2007-10-28
> **KhaaL said:**
> Whee, the clan is now at the magic number 3! :D 

(btw, i'd love to have some europeans join so I don't feel like a hermit)

I know there are a bunch more ETQW players, what about posting the clan recruitment in its own thread?  There is also a guild/clan thread somewhere in these forums.  Phoronix is another place to look for some linux users.  It would be awesome if we got enough linux users and were able to have our own server (running teamspeak of course!).  I would love to see this work out, lets give it a better chance.

---

### Post by Tzuikka on 2007-11-05
> **KhaaL said:**
> Okay, created a ubuntu clan, name is "Ubuntu". Post your screenname so I can send you guys invites

I want to join too [-o<. I have the same name in game.

---

### Post by KhaaL on 2007-11-05
Invitation sent!

I'm thinking of arranging a common game for all of us... I just need to find someone who has a server avaible for us (or a suitable pub!).

Whatch the in-game broadcasts in the clan tab for updates! (or this thread :p)

---

### Post by wishyjr on 2007-11-05
ace, my in game name is just 'Wishy'.

---

### Post by SamsLembas on 2007-11-09
> **KhaaL said:**
> Okay, created a ubuntu clan, name is "Ubuntu". Post your screenname so I can send you guys invites

Finally got my full copy of the game. Could you send an invite my way too? My ingame name samslembas.

No one has ever said anything too me in multiplayer. Am I playing against bots that look exactly like humans, or is everyone using voip (not supported on the Linux client) and being too lazy to even inform me of it? Hopefully being in the clan will help me feel less lonely, especially if some more people join.

---

### Post by ketzerei on 2007-11-09
Isnt there a demo version out somewhere? Or does the demo work under wine?

---

### Post by samjh on 2007-11-09
Yes and yes.

---

### Post by SamsLembas on 2007-11-09
Here's the link for you:
[http://zerowing.idsoftware.com/linux/etqw/ETQWFrontPage#head-6ea18003d0437234c8184c6daeceffece2f1e5f6](http://zerowing.idsoftware.com/linux/etqw/ETQWFrontPage#head-6ea18003d0437234c8184c6daeceffece2f1e5f6)

Figured out how to tell the difference between bots and humans (it was quite obvious). That makes the game a lot more fun. There goes my productivity.

---

### Post by mb108 on 2007-11-10
> **SamsLembas said:**
> Here's the link for you:
[http://zerowing.idsoftware.com/linux/etqw/ETQWFrontPage#head-6ea18003d0437234c8184c6daeceffece2f1e5f6](http://zerowing.idsoftware.com/linux/etqw/ETQWFrontPage#head-6ea18003d0437234c8184c6daeceffece2f1e5f6)

Figured out how to tell the difference between bots and humans (it was quite obvious). That makes the game a lot more fun. There goes my **productivity**.

[http://stats.enemyterritory.com/](http://stats.enemyterritory.com/)

Sorry, can't find "productivity" anywhere. Is it in a mod or something? Maybe you mean Battlesense...

*shrug*

---

### Post by KhaaL on 2007-11-10
> **SamsLembas said:**
> Finally got my full copy of the game. Could you send an invite my way too? My ingame name samslembas.

No one has ever said anything too me in multiplayer. Am I playing against bots that look exactly like humans, or is everyone using voip (not supported on the Linux client) and being too lazy to even inform me of it? Hopefully being in the clan will help me feel less lonely, especially if some more people join.

Invitation will be sent as soon as I get to my desktop. Unfortunatly we haven't had a lot of clan events yet (maybe due to a lack of clan server & not all located in the same timezone)... But yeah, being in the clan will hopefully redeem your lonliness =)

---

### Post by Darganot on 2007-11-11
> **KhaaL said:**
> Okay, created a ubuntu clan, name is "Ubuntu". Post your screenname so I can send you guys invites

If you're still recruiting, I might be interested.  My name ingame is Darganot.

---

### Post by anthonyJC on 2007-11-14
uncomfortable playing because the sensitivity of the mouse bug

---

### Post by go_beep_yourself on 2007-11-17
I'm using the nomedia installer. The instructions in the README say this.

> -nomedia installers:
--------------------

The installer will copy the files from the DVD for you. For some 'no media' installers you maye have to copy
some files under the base/ folder yourself.

Here is the current file list with MD5 checksums:
For the server:
40730e1648f2c1005ccbb7aa9097fe1c  pak000.pk4
c396c40653e75de7bd99e026282beb14  pak001.pk4
11f4d1242615b6616d21ffd47b331c02  pak002.pk4
4fc16bd357e5481f4bdc05338dab7f1b  pak003.pk4
b041cf0dce2035e10894c472ba4f1bec  pak004.pk4
d6e5e67eb87700a6c1fa3dab9beec75e  pak005.pk4

For the client:
1e19cdbd2d5d3c928239908f31e7080c  pak000.pk4
a1efbe9fe0926b05ca9ff8c44345a5a0  pak001.pk4
b224ae88778651573786171663af071d  pak002.pk4
2415424906714b4c423d08eeefd82415  pak003.pk4
7c2a3a3feead0a3abfe4b3bac0554f18  pak004.pk4
8bcfcf420c655f8db1f4ebef51ed77fe  pak005.pk4
25c6a65e90ece71209812ab05f2d08ba  zpak_english000.pk4
7fbbf94c4341ebd2ed27d27595a177d9  zpak_english001.pk4
0e2f8e4f3bed9f56c70e3522a4c07c29  megatextures/area22_lit.mega
da961d539c81a95b31aa2ea91d4b8547  megatextures/ark_lit.mega
2596971cf05eb16b04cc20d8e6bcee91  megatextures/canyon_lit.mega
362c7c75fdc1be377df119f59dc6f7f8  megatextures/island_lit.mega
4583ceb9575394c523d700bbf2e5c03b  megatextures/outskirts_lit.mega
ab039fcd0cadb5f64007b69a1fa2aa95  megatextures/quarry_lit.mega
8743080ede4244e7811879429977dc3a  megatextures/refinery_lit.mega
0975c9dd236b6773e55c1887607d8462  megatextures/salvage_lit.mega
3a82787e9f3b9d548598941fb02515a0  megatextures/sewer_lit.mega
5bce54224875f3c60680c4c1280f1e5b  megatextures/slipgate_lit.mega
2f7428ba0bc34265e2770eeb86f7dfb2  megatextures/valley_lit.mega
839b23d5dccdb0cb763a662a68625cae  megatextures/volcano_lit.mega

These files are missing from the dvd. I even looked on my computer with the windows xp installation of the game, and those 2 files are not there. :confused:
pak005.pk4
zpak_english001.pk4

---

### Post by SamsLembas on 2007-11-17
Why not just use the regular installer?

---

### Post by go_beep_yourself on 2007-11-17
I don't have a dual layer dvd drive.

---

### Post by mb108 on 2007-11-18
> **go_beep_yourself said:**
> I'm using the nomedia installer. The instructions in the README say this.



These files are missing from the dvd. I even looked on my computer with the windows xp installation of the game, and those 2 files are not there. :confused:
[B]pak005.pk4
zpak_english001.pk4[/B]

These files are part of the -full installer. Whether you use -nomedia or -full has nothing to do with DVD access, as it is an option you can disable on both.

The only difference is that the -nomedia installer does not contain those files (you'll notice that the -full is like 250mb larger).

---

### Post by cancertoast on 2007-11-30
I am definitely going to try QW with linux now that I fixed that annoying issue whereupon grub refused to let my OS' (I dual boot) see my dvd/cd drive.  My only question is will my Sennheiser pc-166 USB headset work correctly?  As it is I do not believe it will.  I randomly get a weird sound on my desktop.  It reminds me of when you unplug/plugin a usb device in windows.  
Any linux/Sennheiser gamers care to chip in their 2c ?

---

### Post by SamsLembas on 2007-11-30
Any audio device that works in Ekiga should work in ET:OW.

---

### Post by satissh srinivasan on 2007-12-02
Hey If your still recruiting, my screen name is [FONT="Courier New"]Satissh[/FONT]

Thanks, 
satissh

---

