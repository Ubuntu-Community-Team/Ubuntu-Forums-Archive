---
title: "Super Mario War"
date: 2006-07-22
forum: Gaming &amp; Leisure
---

### Post by jISh on 2006-07-22
Wow, came accross this AMAZING game this morning. 
[http://smw.72dpiarmy.com/](http://smw.72dpiarmy.com/)

Seriously it's got to be the most fun offline multiplayer game I've ever seen. Looking forward to having some fun with this when my friends come over this afternoon. There's even an Xbox version I'd like to get running sometime.

Really though, multiplayer mario with a tonne of game modes and options. What could be better?

---

### Post by jincast90 on 2006-07-22
I once tried it a little. Didint really catch me, but who knows maby I just didint get enough into it.

---

### Post by jISh on 2006-07-22
Well, the single player, IMO, is only to learn how to play. 
Play it with a few friends..OMG..this rocks =/

---

### Post by oobnuker on 2006-07-22
I tried installing this on my machine but it is looking for sdl-config. When I try to install SDL, I get errors indicating it can't install because of some MESA package or other. Any ideas?

---

### Post by jISh on 2006-07-22
Oh, you don't need to install it.
Just get this precompiled binary:
[http://mikelim0.cjb.net:1337/knuxt15/smw-1.6-linux-bin.7z](http://mikelim0.cjb.net:1337/knuxt15/smw-1.6-linux-bin.7z)
Unzip to a folder and run smw

---

### Post by MonkeyBoy on 2006-07-23
Great link!  Hooray for Mario fangames!

---

### Post by Mr_HeNtAi on 2006-07-23
I wish this game had an ONLINE Multiplayer option. Otherwise it is fun to play when you've got nothing else going on.

---

### Post by jISh on 2006-07-23
Oh, if it ever gets online function...you'd have to pry me away from the computer...

---

### Post by %hMa@?b&lt;C on 2006-07-23
how do you do the xbox version. HOW-TO Please!!

---

### Post by Lonthong on 2006-09-15
> **jISh said:**
> Oh, you don't need to install it.
Just get this precompiled binary:
[http://mikelim0.cjb.net:1337/knuxt15/smw-1.6-linux-bin.7z](http://mikelim0.cjb.net:1337/knuxt15/smw-1.6-linux-bin.7z)
Unzip to a folder and run smw

Downloaded & unzipped the file.
How exactly to " run smw"
I cd to unzipped directory, typing smw + enter resulted in nothing.
Alt+F2, pointed to unzipped folder & got an error "could not open location"

---

### Post by anaoum on 2006-09-15
> **Lonthong said:**
> Downloaded & unzipped the file.
How exactly to " run smw"
I cd to unzipped directory, typing smw + enter resulted in nothing.
Alt+F2, pointed to unzipped folder & got an error "could not open location"

cd into the folder containing the binary, then make it exectutable:

$ chmod +x smw

then to run it:

$ ./smw

---

### Post by SIXAXIS on 2008-02-08
Sorry to bring this topic back, but the compiled link does not work and I'm a noob so I was wondering if someone can point me in the right direction. How do I install this game from the original binaries? When I untar the file, it makes 2 folders. One is called 'install' and one 'usr'. In the install folder, there is one file called 'slack-desc' which is basically a description of the game. I tried using chmod and stuff on this file and nothing happened. In the usr folder, there are all the files for the game. I chmod-ed the smw game file and ran it, but it says that the shared library is not available. Is this because I can't play Super Mario War on a 64-bit system? Anyways, can someone tell me step-by-step what to do to install the game or if the game will even work on my Ubuntu 7.10 64-bit?

---

### Post by Zzzach on 2008-02-08
lol looks like a pretty sweet game

---

### Post by rootlinuxusr on 2008-02-09
```
sudo apt-get install libsdl1.2-dev libsdl1.2debian
```
Try doing that in terminal.

I got the same error as you(./smw: error while loading shared libraries: libSDL_image-1.2.so.0: wrong ELF class: ELFCLASS64
), and this fixed it for me.

---

### Post by nikoPSK on 2008-02-09
> **rekha1 said:**
> Super Mario War is to stomp on your opponents as many times as you can. You can play with up to 4 players, and you can have any of them be human or computer. There are 5 different game modes: fraglimit, time limit, classic,GetTheChicken, and no limit.The goal is to stomp as many other Marios as possible to win the game.

haha lol

---

### Post by OmegaBLK on 2008-02-09
Hmmm...looks fun.  I'll check this out later.

---

### Post by nikoPSK on 2008-02-09
> **OmegaBLK said:**
> Hmmm...looks fun.  I'll check this out later.

well it doesn't work for me either... :{

---

### Post by Perfect Storm on 2008-02-09
I just checked it. It's one big mess, even the source codes is messy. The subversion are asking for your password (DON'T do it).

Recommended not using it until it's solved.
Head over and grab either SuperTux or Secret Maryo Chronicles.

---

### Post by BigSilly on 2008-02-09
> **Artificial Intelligence said:**
> I just checked it. It's one big mess, even the source codes is messy. The subversion are asking for your password (DON'T do it).

Recommended not using it until it's solved.
Head over and grab either SuperTux or Secret Maryo Chronicles.

Crikey. Are you saying it's potentially unsafe to try to run this game?

I downloaded it too, but I couldn't get it to work either so I just deleted it.

---

### Post by Perfect Storm on 2008-02-09
No, I say it's fishy that the subversion is asking for my password.
When I enter the subversion command, it ask for your password.

---

### Post by kryth on 2008-02-09
Nice. I like it like it :O :P

---

### Post by SIXAXIS on 2008-02-10
> **rootlinuxusr said:**
> ```
sudo apt-get install libsdl1.2-dev libsdl1.2debian
```
Try doing that in terminal.

I got the same error as you(./smw: error while loading shared libraries: libSDL_image-1.2.so.0: wrong ELF class: ELFCLASS64
), and this fixed it for me.
I did that and it didn't work. Does anyone know how to compile a binary source without Slackware or at least install another version of Super Mario War?

---

### Post by SIXAXIS on 2008-02-10
I managed to get this far: With the conifugration file, it was apparently written in Windows adding special, non-viewable characters at the end of each line. I get the error "bash: ./configure: /bin/sh^M: bad interpreter: No such file or directory" when trying to configure. I checked the internet and there's a Windows to Linux converter. I tried that but it also gives me an error (both ways).

---

### Post by nikoPSK on 2008-02-10
well, I got lazy and am running it under wine.

---

### Post by SIXAXIS on 2008-02-15
> **nikoPSK said:**
> well, I got lazy and am running it under wine.

I would try that, but unfortunately, this is my first Linux install so I installed the 64-bit version which runs slow under Wine. Also, my laptop is crappy. So I would really appreciate it if someone told me exactly how to install this game either from source code or binary.

Thanks.

---

### Post by SIXAXIS on 2008-03-01
Again, sorry to revive this thread, but I have switched to the 32-bit version of Gutsy (mainly due to the fact that not as many things work in 64-bit) and now I've installed the game. When I run it, it says "ERROR: Empty map directory!". I know that the map directory is not empty. It is in the usr/share/smw folder. Super Mario is in the usr/bin folder.

Anyone have any suggestions on how to get SMW up and running?

---

### Post by SIXAXIS on 2008-03-01
Nevermind. I figured out how to get it working. It turns out that the smw folder wasn't copied to the share folder. I had to use the "cp -r" command, but I originally used "cp". 

BTW, if anyone is having trouble installing, this is what you do. You have to untar everything. Copy the smw and bin folders to their respective places in the usr folder at the root of the filesystem. Then to start Super Mario War, type in "smw" in the Terminal. Or, you can make a launcher to the desktop or panel. Just make the command "smw".

---

### Post by OmegaBLK on 2008-04-12
Finally got around to installing the game tonight--fun times ahead.  Good find OP.  Back to the game!

---

### Post by Hells_Dark on 2008-06-27
Any **proper** way to install the last version ?

---

