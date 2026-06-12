---
title: "Warzone 2100 RTS Update"
date: 2006-05-16
forum: Gaming &amp; Leisure
---

### Post by charlieg on 2006-05-16
This project is moving forward steadily:
[http://www.coppercore.net/~wztoys/modules/news/article.php?storyid=38](http://www.coppercore.net/~wztoys/modules/news/article.php?storyid=38)

Bearing in mind that Warzone 2100 was already a complete game before it went GPL, this is definitely one people should check out.  It is not alpha software nor missing content.

---

### Post by charlieg on 2006-05-17
Does this work for anybody?

I get the following error:```
$ warzone
Registry file config is empty!
Error: SDL_SetVideoMode failed (Couldn't find matching GLX visual).
```
It also appears that the .deb author hasn't run dist-upgrade on his system in a while as the .deb (created on Dapper) depends on libopenal0 which (on Dapper) is no longer part of Ubuntu.

---

### Post by dolny on 2006-05-17
It works for me, but I when I run it with -fullscreen, I get a weird output: the game window is smaller than it should be so it's like windowed mode with black area around :/ I have Intel 910 GML Express card (on Acer Travelmate laptop).

Anybody knows how to fix this and get the normal fullscreen mode?

How can I change the resolution?

---

### Post by Moebius on 2006-05-17
Full screen mode will use 800x600 resolution

To get a proper fullscreen use your laptop standard definition.

Ex: My Acer runs on 1280x1024, so to start warzone I use
```
warzone -1280x1024
```
to get a real fullscreen resolution.

---

### Post by ELD on 2006-05-18
[QUOTE=Moebius]Full screen mode will use 800x600 resolution

To get a proper fullscreen use your laptop standard definition.

Ex: My Acer runs on 1280x1024, so to start warzone I use
```
warzone -1280x1024
```
to get a real fullscreen resolution.[/QUOTE]

Looks like they need to work on that to do something like that by defualt?

I used to play this game LOTS on playstation, may download it again sometime.

---

### Post by JockeTF on 2006-06-01
Hello!
and sorry for the late reply :mrgreen:

I'm the one creating the Warzone 2100 ubuntu packages and I'm very happy that people actually are using it! :) 

And to prevent some missunderstandings: I don't code anything in warzone 2100 and I don't know any programming languages anyway. 

But I can do some shell scripting though :P . But the only thing i create for warzone 2100 is the packages for ubuntu and some scripts. 

> **"charlieg"]Bearing in mind that Warzone 2100 was already a complete game before it went GPL, this is definitely one people should check out.[/quote]

Yeah, it already was a great before it began to use the GPL license and the developers of the "GPL version" worked hard on converting it from DirectX 5.0 to OpenGL, sdl and OpenAL :D
But the code we got contained some Playstation code and there still are some bugs in the game.
And yeah, check it out, its really an awesome game! :D

[quote="charlieg"]It is not alpha software nor missing content.[/quote]

Nope, its not an alpha but sadly there are some missing content:
The sequences (videos) was not included in the source code that we recived, nor was the codecs for them. So the people who have the sequences can't use them in the GPL version of warzone and we could not convert them to another format and include them in Warzone 2100 as it would have been illegal. The original sequence format is rpl. Eidos created a player called escape player for some time ago. It can be downloaded from my webserver and it works fine in wine if someone would to look at their old Warzone sequences again. :P

[quote="charlieg"]It also appears that the .deb author hasn't run dist-upgrade on his system in a while as the .deb (created on Dapper) depends on libopenal0 which (on Dapper) is no longer part of Ubuntu.[/quote]

Yeah, sorry for that, some of my laptops hardware broke during the time when they changed libopenal0 package and it took a week to repair it, but the dependencie problem should be fixed now.  said:**
> Looks like they need to work on that to do something like that by defualt?

Yes, I'm actually working on a shell script that should make it very easy for everyone to change things like that in the warzone 2100 config file. The "original Warzone 2100" game for MS windows used shortcuts in the "Start menu" to change things like resolution, window/fullscreen mode and 3D acceleration.
But using the resolution 640x480 in a window by default might be good idea for some reasons like that **everyone** (well... very close to atleast ^_^ ) will be able to start it directly after install, even those who uses low resolution and old hardware.
But hopefully my script will solve some of those problems. :)

We sure have some work to do before we get "finnished" with Warzone 2100. 
But we have a problem:

As far as i know we only have 1-3 programmers coding on warzone right now, and they are very busy with other stuff so they don't have much time left for coding on warzone. So if there are some programmers in here who would like to help out, please contact us!!

I've asked the developers about putting the package into the ubuntu reposies but they didn't think that warzone 2100 was ready for that yet.

you can download my debian packages from the following locations:

[http://www.coppercore.net/~wztoys/modules/news/](http://www.coppercore.net/~wztoys/modules/news/)
You will need to register first in order to get to the dowloads.

[http://jocketf.no-ip.info/ubuntu_packages/dapper/warzone](http://jocketf.no-ip.info/ubuntu_packages/dapper/warzone)
My own webserver... on my laptop... It will always contain the lastest package but it might be extremly slow and sometimes not online at all. I use port 8001 due to my ISP who blocks port 80.

Ill try to realease a new packages often.

you can also download the escape player from my webserver
[http://jocketf.no-ip.info/other/rpl-player.tar.gz](http://jocketf.no-ip.info/other/rpl-player.tar.gz) 

the warzone SVN is nowadays located at gna that we also use as out "Project page":
[https://gna.org/projects/warzone/](https://gna.org/projects/warzone/)

There are alot of useful info on this "site", The warzone 2100 documents project: 
[http://tinyurl.com/mgg8g](http://tinyurl.com/mgg8g)

our forums:
[http://www.realtimestrategies.net/forums/index.php](http://www.realtimestrategies.net/forums/index.php)

you may also find us at
#warzone at irc.freenode.net



Phew, i guess that is enough for now :)
Thanks for reading :mrgreen:

/ JockeTF

---

