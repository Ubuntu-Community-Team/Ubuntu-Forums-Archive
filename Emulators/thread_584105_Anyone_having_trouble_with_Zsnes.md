---
title: "Anyone having trouble with Zsnes?"
date: 2007-10-20
forum: Emulators
---

### Post by kevindubrow on 2007-10-20
Hey, Zsnes wont run in Gusty for me. It opens as a black screen and than closes. It is version 1.5 (I got it from the package manager). I have the full text output, but it is huge, so I'll just put the end. Thanks in advance for any help!

"Aborted (core dumped)
"
I can put more of the output, just tell me and you will have it!

---

### Post by mister_k81 on 2007-10-20
Yeah, ZSNES didn't work for me either when I tried to install it from the repositories, I had the exact same problem on Gutsy. The only way I could get it to work, was by going to the ZSNES homepage and get the .tar.bz2 from there and install from source. But it works great for me now. 

Website can be found here: [http://www.zsnes.com/](http://www.zsnes.com/)

---

### Post by acoustibop on 2007-10-20
Does [this thread]("http://ubuntuforums.org/showthread.php?t=582289") help, kevindubrow?  It helps to look for other threads on your problem before posting! ;)

---

### Post by kevindubrow on 2007-10-21
Sorry, I did look for a thread, but found nothing like that. Also, that isnt my exact problem. :) Anyway, I am optimistic that acoustibop's way will fix my problem, but the problem is that I have no clue how to install ZSNES with the .tar.bz2 file. Any help? Thanks a lot for the replies!

---

### Post by disturbedite on 2007-10-21
zsnes (1.51 & previous releases) work fine and always have for me.  the one from the gutsy repo actually works better in one way:  the audio works as expected.
i compile from svn & apparently with svn if one has an onboard sound card (chip) audio can be scratchy...

---

### Post by mister_k81 on 2007-10-21
Hmm... I haven't noticed any problems running it from source, sound and graphics all seem fine to me. Maybe installing it from the repo configured the sound differently for you though, disturbedite. 

> **kevindubrow said:**
> Sorry, I did look for a thread, but found nothing like that. Also, that isnt my exact problem. Anyway, I am optimistic that acoustibop's way will fix my problem, but the problem is that I have no clue how to install ZSNES with the .tar.bz2 file. Any help? Thanks a lot for the replies!

If you have to install from the .tar.bz2 file, here's some directions: 

1.  unzip zsnes_1_5.tar.bz2

2. open terminal and change directory to the "src" folder in the "zsnes_1_5" folder by typing: 
    
desktop:~$ cd  ~/Desktop/zsnes_1_51/src (or whatever directory your zsnes_1_51 folder is in)

3.  run the "configure" file in the  "zsnes_1_51/src/"  folder. You can do that by typing: 

desktop:~/Desktop/zsnes_1_51/src$ ~/Desktop/zsnes_1_51/src/configure (or yet again, to where ever your zsnes file is located)

(note, that it may ask for a certain dependency when running the configure command... it did for me, I forget what the dependency was called, but I easily found it in the repositories.)  

4. Next, in terminal type: 

desktop:~$ make

5. when that is done, type: 

desktop:~$ make install

And that should be it. It doesn't create a shortcut by making it from source, but you can just start Zsnes by opening the terminal and typing: "zsnes" (without the quotes)... or you can just make a launcher and put "zsnes" in the command line. There are also icons in the zsnes src folder that you can use. 

I hope that helps. :)

---

### Post by FranMichaels on 2007-10-21
> **mister_k81 said:**
> Hmm... I haven't noticed any problems running it from source, sound and graphics all seem fine to me. Maybe installing it from the repo configured the sound differently for you though, disturbedite. 



If you have to install from the .tar.bz2 file, here's some directions: 

1.  unzip zsnes_1_5.tar.bz2

2. open terminal and change directory to the "src" folder in the "zsnes_1_5" folder by typing: 
    
desktop:~$ cd  ~/Desktop/zsnes_1_51/src (or whatever directory your zsnes_1_51 folder is in)

3. *snip*


Good directions, I'd like to recommend variations from step 3 on. :)

This will gather the required dependencies to build zsnes
```

sudo apt-get build-dep zsnes
sudo apt-get install libao-dev
./autogen.sh

```

```

./configure --enable-libao --enable-release
make
sudo make install

```

I just compiled zsnes an hour ago to get libao support, I don't think the one in the repositories uses it...

Best of luck. :D

P.S. If you have a dual core setup
make -j2
Will speed things up quite a bit. :KS

---

### Post by mister_k81 on 2007-10-21
^ Those are much better directions :D .  

I didn't know that you could gather dependencies like that. I'm still new to Linux and have only been using it for about a month, so there's a lot I don't know. 

Also, I have to ask, whats the name of that rom? It doesn't look like Zelda 3: Link to the Past.

---

### Post by kevindubrow on 2007-10-21
Hey, no luck with those instructions, can I get some more help? Sorry if its a bother.

**The first error came after the sudo apt-get build- dep zsnes:**
E: Could not open file /var/lib/apt/lists/medibuntu.sos-sts.com_repo_dists_feisty_free_source_Sources - open (2 No such file or directory)

**The next after the ./autogen.sh:**
Generating build information using aclocal and autoconf...
./autogen.sh: 6: aclocal: not found
./autogen.sh: 7: autoconf: not found

**Another error within that same code:**
configure: error: You need NASM installed to compile ZSNES

Do any of these errors make any sense to you all? Thanks for all of the help!

-------------------------
Oh and hey FranMichaels, which Zelda is that? I have never seen that one...and it is even more confusing that is is in super nintendo!

---

### Post by dfreer on 2007-10-21
@kevindubrow:
```
sudo apt-get install nasm build-essential libsdl1.2-dev zlib1g-dev libpng12-dev
```

There's an even EASIER way to install zsnes 1.51 in gutsy... *points at sig*

@FranMichaels - I like the Star Ocean pic, I wish I had more time to play that game...

---

### Post by FranMichaels on 2007-10-21
@dfreer
Thank you, I made it rather quickly with GIMP. As for making time, save states might help ;)

@kevindubrow 
dfreer gave the command you need. build-dep does work though, I'm not using medi-buntu, but the command is exactly:

```

sudo apt-get build-dep zsnes

```

No space between the hyphen. Try and see if that does the trick.
Also, 
```
sudo apt-get install autoconf
```
that should take care of the autogen error

@mister_k81
Yes, there are a lot of great commands and tricks... You just kind of stumble upon them though... Unless you read a lot of manual pages. :KS

As for rom, and yes I know the forum rules, this is not a link to the rom itself, just a patch file:

[http://www.romhacking.net/hacks/197/](http://www.romhacking.net/hacks/197/)

It's fun and extensive zelda III hack (requires the original zelda III rom), much harder than the original... Although a few save states and cheat codes I made balance things out :biggrin:

Anyway, zsnes supports soft patching.
So just put the ips file with the same name as the rom, and you'll be good to go. 

P.S. Dfreer, hope you don't mind me copying your response style :)

---

### Post by kevindubrow on 2007-10-21
I'm really sorry, these codes are still not working. I now have a lot of new errors. I have gotten the repo that dfreer made but I don't know how I use that to get ZSNES. I thought it would be in the package manager, but I do not see it.

Oh and thanks for the info FranMichaels!

---

### Post by FranMichaels on 2007-10-21
You are very welcome. 
Let's get this working. :)

What do the errors look like.
Did zsnes used to work before, maybe you should backup the config files stored in .zsnes

---

### Post by kevindubrow on 2007-10-21
It was working in Feisty, but stopped when I upgraded. I'll just put the whole output...I don't care if you guys know my name!

[B]stephen@stephen-laptop:~$ cd ~/Desktop/zsnes_1_51/src
stephen@stephen-laptop:~/Desktop/zsnes_1_51/src$ sudo apt-get build-dep zsnes[/B]
[sudo] password for stephen:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/medibuntu.sos-sts.com_repo_dists_feisty_free_source_Sources - open (2 No such file or directory)
**stephen@stephen-laptop:~/Desktop/zsnes_1_51/src$ sudo apt-get install libao-dev**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libao-dev is already the newest version.
The following packages were automatically installed and are no longer required:
  libnl1-pre6 libnm-util0 dhcdbd
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
**stephen@stephen-laptop:~/Desktop/zsnes_1_51/src$ sudo apt-get install autoconf**
Reading package lists... Done
Building dependency tree        
Reading state information... Done
autoconf is already the newest version.
The following packages were automatically installed and are no longer required:
  libnl1-pre6 libnm-util0 dhcdbd
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
**stephen@stephen-laptop:~/Desktop/zsnes_1_51/src$ ./autogen.sh**
Generating build information using aclocal and autoconf...
./autogen.sh: 6: aclocal: not found
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for nasm... nasm
./configure: line 3437: syntax error near unexpected token `1.2.0,,AC_MSG_ERROR'
./configure: line 3437: `AM_PATH_SDL(1.2.0,,AC_MSG_ERROR(SDL >= 1.2.0 is required))'
**stephen@stephen-laptop:~/Desktop/zsnes_1_51/src$ ./configure --enable-libao --enable-release**
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for nasm... nasm
./configure: line 3437: syntax error near unexpected token `1.2.0,,AC_MSG_ERROR'
./configure: line 3437: `AM_PATH_SDL(1.2.0,,AC_MSG_ERROR(SDL >= 1.2.0 is required))'
**stephen@stephen-laptop:~/Desktop/zsnes_1_51/src$ make**
make: *** No targets specified and no makefile found.  Stop.
**stephen@stephen-laptop:~/Desktop/zsnes_1_51/src$ sudo make install**
make: *** No rule to make target `install'.  Stop.
**stephen@stephen-laptop:~/Desktop/zsnes_1_51/src$**

Thank you very much for your help!

---

### Post by FranMichaels on 2007-10-21
> **kevindubrow said:**
> It was working in Feisty, but stopped when I upgraded. I'll just put the whole output...*snip*
./configure: line 3437: syntax error near unexpected token `1.2.0,,AC_MSG_ERROR'
./configure: line 3437: `AM_PATH_SDL(1.2.0,,AC_MSG_ERROR(SDL >= 1.2.0 is required))'
**stephen@stephen-laptop:~/Desktop/zsnes_1_51/src$ make**
make: *** No targets specified and no makefile found.  Stop.
**stephen@stephen-laptop:~/Desktop/zsnes_1_51/src$ sudo make install**
make: *** No rule to make target `install'.  Stop.
**stephen@stephen-laptop:~/Desktop/zsnes_1_51/src$**

Thank you very much for your help!

Okay, well it might be the new zsnes doesn't like your old config.

In nautilus, press ctrl + h (or view hidden files) go the .zsnes folder

rename your zsnescfg (or some file like that) to zsnescfg.old or move it to the Trash can. Try launching zsnes, and see if it works :)

Other options, you are close to compiling it, just missing libsdl-dev stuff according to the error.

```
sudo apt-get install libsdl1.2-dev
```

---

### Post by kevindubrow on 2007-10-21
Ok, well I already had whatever your code was going to give me:
[B]libsdl1.2-dev is already the newest version.
The following packages were automatically installed and are no longer required:
  libnl1-pre6 libnm-util0 dhcdbd
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/B]

I deleted the zsnesl.cfg file and when I opened zsnes, it rewrote the file in the .zsnes folder and I had the same issue occurred (zsnes opened with a black box and closed).

---

### Post by FranMichaels on 2007-10-21
> **kevindubrow said:**
> *snip*
I deleted the zsnesl.cfg file and when I opened zsnes, it rewrote the file in the .zsnes folder and I had the same issue occurred (zsnes opened with a black box and closed).

Hmm it must be another libsdl dev dependency, I installed mine more than 1/2 a year ago, so I don't rememeber exactly what's missing. Installing dependencies normally a one time thing.

```
sudo apt-get install libsdl-image1.2-dev libsdl-mixer1.2-dev libsdl-net1.2-dev libsdl-sound1.2-dev
```

Darn. :(
What happens when you type zsnes in terminal
does it show an error message?

EDIT: One other thought, did you change anything in your upgrade to Gutsy? Maybe enabling/disabling desktop effects will make a difference?

---

### Post by mister_k81 on 2007-10-21
> stephen@stephen-laptop:~/Desktop/zsnes_1_51/src$ ./autogen.sh
Generating build information using aclocal and autoconf...
./autogen.sh: 6: aclocal: not found

I don't know if this helps, but you can get aclocal by typing: "sudo apt-get install automake".

---

### Post by kevindubrow on 2007-10-21
Woh! The code mister_k81 gave me did the trick! I Ran the code, ran an uninstall on ZSNES, reinstalled it and all is well! Thanks so much for all of your help, all you guys are great! And thanks for all of your time, FranzMichaels!

I don't understand this....it is doing the same thing again!

**Output:**
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

This is a work in progress build. It contains code which
May or may not be complete

If this is supposed to be an official release, you forgot to
run configure with --enable-release, go rebuild.

It runs fine in the terminal, it tells me that it can not find a mouse, but mine still works.

---

### Post by kevindubrow on 2007-10-21
It will run fine if I run it from the terminal, but if I open it in the menu it will crash. Any clue what that is about?

---

### Post by FranMichaels on 2007-10-21
> **kevindubrow said:**
> It will run fine if I run it from the terminal, but if I open it in the menu it will crash. Any clue what that is about?

Right click on the Applications menu, choose Edit Menus
Go to Games
Right click on zsnes and choose Properties.
for the command make sure it's just
zsnes

Hopefully that's does it.

Glad you got it working again! :KS

---

### Post by kevindubrow on 2007-10-21
Well, it is just ZSNES, here is all the info:

Name: ZSNES
Command: /usr/local/games/zsnes/zsnes

Occasionally ZSNES will crash and I get this error: 
Segmentation fault (core dumped)

I guess I can live with it just working in the terminal...but apparently I can not go full screen...it makes my video output when I am done playing all odd. Also, the audio quality is very badr. Thanks for all of the help.

---

### Post by mister_k81 on 2007-10-21
are you typing it ZSNES with all caps? that might be the problem. it should be all lower case.

Oh, I just saw your edit, all you need to type is "zsnes" for the command... 

I'm not sure what the problems could be with fullscreen,  bad sound and other bugs?  Really can't help you there. sorry. :/

---

### Post by kevindubrow on 2007-10-21
When I type in the terminal I use lower case, and I must of made a typo, it is lowercase in the menu editor also.

---

### Post by FranMichaels on 2007-10-21
> **kevindubrow said:**
> Well, it is just ZSNES, here is all the info:

Name: ZSNES
Command: /usr/local/games/zsnes/zsnes

Occasionally ZSNES will crash and I get this error: 
Segmentation fault (core dumped)

I guess I can live with it just working in the terminal...but apparently I can not go full screen...it makes my video output when I am done playing all odd. Also, the audio quality is very badr. Thanks for all of the help.

That's what I mean, the command

"Command: /usr/local/games/zsnes/zsnes"
change it to only 
zsnes

not /blah/blah/zsnes

That will do it :)

As for the audio, try putting to 48000hz?

As for video, play with the settings, maybe try opengl ones ODR OD etc.

---

### Post by kevindubrow on 2007-10-21
THANK YOU SO MUCH! It still occasionally crashes and the sound is still iffy, but don't worry about it, I am happy for what I have (honestly, you've done enough). I really appreciate all of the help you have given me. If I ever learn Linux well enough, I may be able to help you out one day in return. Seriously, thanks again everyone, you all are great.

---

### Post by dfreer on 2007-10-21
I'm guessing, due to zsnes being in /usr/local/games/zsnes/, that you installed my zsnes package, and then compiled a version of zsnes as well? This may cause the error you are experiencing, although I don't know why my version would be seg faulting (I just made the gutsy packages, perhaps there is a problem). 
[list]
[*]Install libsdl1.2debian-oss has been known to help scratchy sound.
[*]Alternatively, compiling 1.51 with --enable-libao, and then running zsnes with -ad oss has fixed my sound issues completely. *EDIT: FranMichaels already showed how to do this in the first page of this thread*
[*]Compiling with --enable-release gets rid of the "WIP" error at startup, beyond that I'm not sure what advantages/disadvantages it presents.
[*]Increasing the sound from 32000hz to 48000hz can, in some cases, improve sound quality (although zsnes developer's will not accept sound-related bug reports when using anything but 32000hz.
[*]Play with the video modes, and make sure your video card drivers are installed correctly is about all I can say about graphical glitches.
[*]The error you get when updating with apt-get is probably due to a typo in /etc/apt/sources.list, you should be able to see an entry concerning medibuntu. 
[/list]

> I have gotten the repo that dfreer made but I don't know how I use that to get ZSNES. I thought it would be in the package manager, but I do not see it.
Using the repository should be as simply as copy+pasting, and should show up in the package manager if done right. But if you already got zsnes working, I wouldn't mess with it:
```
echo "deb http://packages.dfreer.org gutsy main" | sudo tee -a /etc/apt/sources.list
wget http://packages.dfreer.org/7572013D.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install zsnes
```

@FranMicheals - lol, I borrowed my commenting style from others on the forum, so whatever ;)

---

### Post by kevindubrow on 2007-10-21
Do you think if I uninstall and use your code, I will have ZSNES running well? Thanks.

Hah, I ran the code and all is well! Thanks again!

---

### Post by dfreer on 2007-10-21
Well, before you go through a uninstall, you can simply test my binary. If that works for you, THEN you can clean out zsnes completely and try my package.
So, to test my binary, create a folder on your desktop (like **dfreer**), and place this file in it:
[http://www.dfreer.org/~dfreer/zsnes/binaries/zsnes_1.51](http://www.dfreer.org/~dfreer/zsnes/binaries/zsnes_1.51)
Then, just in case, backup your saved games like so:
```
sudo mv -v ~/.zsnes/ ~/zsnes_backup
```

Then, you can try out my binary (I'd appreciate it, if there is something wrong I'd like to know about it). Try running it like this:
```
cd ~/Desktop/**dfreer**/
./zsnes -ad oss
```
That will use the libao2 library, so hopefully you'll notice better sound quality.

If it crashes, post the output, and then run this command and post:
```
ldd ./zsnes
```

Thanks in advance, and I hope this helps you out as well!

---

### Post by kevindubrow on 2007-10-21
Umm...I didnt use the codes you just put, but I have already used your codes from three posts ago and everything is great! Is that enough info for you, or do you want me to use these new codes?

---

### Post by dfreer on 2007-10-21
No need if my package works, thanks! So sound is working ok now, and video after installing my package?

---

### Post by FranMichaels on 2007-10-22
I was very glad to help you. Just make sure to have fun. :)

Anyway, maybe it's time we make a bash script that handles downloading, building, and installing for zsnes.

Maybe dfreer you'd like to help with 64-bit (I don't have a 64-bit box at the moment...)

:KS

---

### Post by kevindubrow on 2007-10-22
Everything is great! Thanks so much for your help!

---

### Post by dfreer on 2007-10-22
> **FranMichaels said:**
> I was very glad to help you. Just make sure to have fun. :)

Anyway, maybe it's time we make a bash script that handles downloading, building, and installing for zsnes.

Maybe dfreer you'd like to help with 64-bit (I don't have a 64-bit box at the moment...)

:KS

I can certainly help out, but it's far easier to build the binaries on a 32-bit OS, I have yet to figure out how to compile 32-bit binaries from a 64-bit host. (You can't actually build a true 64-bit version of zsnes, due to the way zsnes is currently developed. My ZSNES packages are 32-bit binaries in a 64-bit package, because current intel/amd 64-bit processors can execute 32-bit code).

I'll have more for you later tonight, one thing to look out for is the "can't create mcop directory" that a lot of gutsy users are having problems with. I have yet to hear a definitive answer on the cause and solution for that problem.

---

### Post by FranMichaels on 2007-10-22
Very cool, and thanks. :)

My sister ran into that mcop issue after upgrading to Gutsy. 
I proposed a solution in another thread here, but can't really test it myself... :) Nor do I know the cause...

---

### Post by dfreer on 2007-10-22
I'm thinking it has to be specific to the gutsy package of zsnes in the main repos. I'll set up a virtual machine or live CD here, and see if I can replicate on a fresh version of gutsy.

As for the script, it wouldn't be hard at all. The only issue I'd have would be how to check for if there is any errors when compiling, and halt properly once something fouls up. 

Maybe I'm bias, but AFAIK my packages already work fine for gutsy, is there a need for such a script?

---

### Post by Tuxoid on 2007-10-22
when run from the terminal, zsnes tells me:

```
mike@Mike:~$ zsnes

ZSNES v1.36 (c) 1997-2002, ZSNES Team (zsKnight & _Demo_)

Be sure to check http://www.zsnes.com/ for the latest version.
Please report crashes to zsnes-devel@lists.sourceforge.net.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE' thoroughly before using it.

Use ZSNES -? for command line definitions.

MMX support found and enabled.

Could not set 512x448 video mode.
```

I tried installing some sdl pakages that were suggested, and it nothing.

---

### Post by FranMichaels on 2007-10-22
> **dfreer said:**
> I'm thinking it has to be specific to the gutsy package of zsnes in the main repos. I'll set up a virtual machine or live CD here, and see if I can replicate on a fresh version of gutsy.

As for the script, it wouldn't be hard at all. The only issue I'd have would be how to check for if there is any errors when compiling, and halt properly once something fouls up. 

Maybe I'm bias, but AFAIK my packages already work fine for gutsy, is there a need for such a script?

Come to think of it, I agree :)
Considering how long zsnes 1.51 has been out. 
Maybe if a new release comes out or the svn has some obvious benefits.

I guess I thought it might be handy since there seem to be a lot of "zsnes issues" threads in this section. Probably better handled by squashing outside bugs, I don't think zsnes is responsible for it, except maybe sound issues ;)

Thanks.

---

### Post by dfreer on 2007-10-22
@FranMichaels - That mcop error may very well be solved by using a custom bash script, but as a package maintainer I can't really (*shouldn't* is more correct) modify files in user's home directories. But I'm really thinking that the official package is to blame, not gutsy itself.

Didn't we just have this same error elsewhere?? Anyways:
My advice would be to backup, and then delete your existing ~/.zsnes/ directory. If that doesn't work, then try manually specifying the resolution you want zsnes to run in, either in your ~/.zsnes/zsnesl.cfg file, or when launching zsnes by passing it an argument like so:
```
-v #    Select video mode :
             0 = 256x224      R WIN     1 = 256x224      R FULL
             2 = 512x448     DR WIN     3 = 512x448     DR FULL
             4 = 640x480     DR FULL
             5 = 256x224    O R WIN     6 = 512x448    ODR WIN
             7 = 640x480    ODS FULL    8 = 640x480    ODS WIN
             9 = 640x560    ODR WIN    10 = 768x672    ODR WIN
            11 = 800x600    ODS FULL   12 = 800x600    ODS WIN
            13 = 896x784    ODR WIN    14 = 1024x768   ODS FULL
            15 = 1024x768   ODS WIN    16 = 1024x896   ODR WIN
            17 = 1280x960   ODS FULL   18 = 1280x1024  ODS FULL
            19 = 1600x1200  ODS FULL   20 = VARIABLE   ODR WIN
            21 = VARIABLE   ODS WIN    22 = CUSTOM     OD  FULL
```

EDIT: not quite the same error, I see:
[http://ubuntuforums.org/showthread.php?t=571666&highlight=zsnes](http://ubuntuforums.org/showthread.php?t=571666&highlight=zsnes)

---

### Post by FranMichaels on 2007-10-22
> **Tuxoid said:**
> when run from the terminal, zsnes tells me:

```
mike@Mike:~$ zsnes

ZSNES v1.36 (c) 1997-2002, ZSNES Team (zsKnight & _Demo_)

Be sure to check http://www.zsnes.com/ for the latest version.
Please report crashes to zsnes-devel@lists.sourceforge.net.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE' thoroughly before using it.

Use ZSNES -? for command line definitions.

MMX support found and enabled.

Could not set 512x448 video mode.
```

I tried installing some sdl pakages that were suggested, and it nothing.

Zsnes 1.36... Why? :) Try using 1.51 and see if it works for you. 

Or is there a reason you want that particular version (old zmv file?)

Hope that helps.

---

### Post by dfreer on 2007-10-23
BTW, I just tested i386 package of zsnes on a Gutsy Live CD. I had no issues with the mcop directory missing, so it's definitely got to be an issue with the main repository package.

---

### Post by botulismo on 2007-10-23
I was having this problem... Let it go a couple days, then I remembered "Hey, run it from the terminal" and the mcops directory thing was the problem...

The solution? I made the directory it was having a problem creating for it. It's worked fine ever since.

Has this solution already been posted? If so, I apologize. I tried skimming the thread as quickly as possible without missing details, but I may have. It seemed like most of the solution involved compiling the program oneself, but to me, just making a directory for a (slightly) faulty program is easier.

---

### Post by Tuxoid on 2007-10-23
> **FranMichaels said:**
> Zsnes 1.36... Why? :) Try using 1.51 and see if it works for you. 

Or is there a reason you want that particular version (old zmv file?)

Hope that helps.

Won't upgrading the zsnes delete my state files?

---

### Post by acoustibop on 2007-10-24
Unless you're using non-default locations, Tuxoid, your saves, save states, configuration etc should be in /home/<user>/.zsnes.  Removing the rest of the installation shouldn't affect this folder.  However, if you're wondering whether your save states will still work with a new version - quite possibly, they won't.  Particularly with as big a jump between versions of this, the emulator may well be emulating games differently, which will mean save states, which are a 'snapshot' of the game at that point, may differ from version to version of the emulator.

It's not a good idea with most emulators to rely on save states exclusively.  Errors can creep into a game when playing for some time, and these accumulate.  Conventional saves usually just record the parameters of the game at that point, so errors should be stripped away by the save.  Restarting the game and reloading the save is like starting anew but with different parameters that put you at the point in the game where you saved.

Save states, on the other hand, usually record the entire state of the game, including any errors that may have occurred.  So when you load from a save state, it's like continuing the game you were playing before, errors included.  Eventually, they can accumulate to the point where the game becomes unplayable.

This is particularly noticeable with emulators for consoles where games can last a considerable length of time - with Playstation emulators, for instance, it's a standard point to check when someone has problems late in a game - are you playing entirely on save states?

It would also be a good idea to delete your configuration files (in  /home/<user>/.zsnes) if you upgrade and configure the new version afresh.  Again, with the differences you can get with as big a jump as this, your old configuration could mess the emulator up, and it's not difficult or time-consuming to configure ZSNES.

---

### Post by Tuxoid on 2007-10-24
> **acoustibop said:**
> - are you playing entirely on save states?


I do save through the natural game save screens, but I use save states for convenience.

---

### Post by dfreer on 2007-10-24
If you wish to upgrade why not play each game that is currently at a save state through until you reach a save point, and then save. Delete the old save states, upgrade. Continue on using new save states with the new emulator.

---

### Post by disturbedite on 2007-10-25
just to clarify, in my post a long time ago, i failed to mention *[I]why*[/I] the audio was scratchy when compiling from svn source:   it is a known problem for mobos with integrated sound cards (chips).

---

### Post by Tuxoid on 2007-11-12
> **dfreer said:**
> If you wish to upgrade why not play each game that is currently at a save state through until you reach a save point, and then save. Delete the old save states, upgrade. Continue on using new save states with the new emulator.

I wish I could but i can't even get the emulator to load.

EDIT: I actually have (oddly enough) both 1.51 and 1.36.
Now that I remember, before 7.10, 1.51 would run.
the 1.36 file never worked. In, I think
I had the same error in the terminal.
I don't how I could possibly have both, and I
have even less of an idea on how to remove the
1.36 one.

---

### Post by Tuxoid on 2007-11-15
Alright, I have tried to run 1.51 via the terminal now and here's what it spits out:

```
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
ManyMouse: 2 mice detected.
Using ManyMouse for:
Mouse 0: SynPS/2 Synaptics TouchPad
Mouse 1: Macintosh mouse button emulation
Could not set 512x448 video mode: No available video device

```

---

### Post by dfreer on 2007-11-15
Move your ~/.zsnes folder elsewhere, and try again. Example:
```
mv -v ~/.zsnes/ ~/.zsnes_backup
```

---

### Post by Tuxoid on 2007-11-15
It's still showing out basically the same error after trying to move my .zsnes directory:

```
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
ManyMouse: 2 mice detected.
Using ManyMouse for:
Mouse 0: SynPS/2 Synaptics TouchPad
Mouse 1: Macintosh mouse button emulation
Could not set 512x448 video mode: No available video device

```

Everything else works, but most of my emulators don't work with my video adapter. The only emulator working is mupen64. I have a 945g intel graphics accelerator. It all worked with feisty, but it just won't work in gusty.

---

### Post by FranMichaels on 2007-11-15
> **Tuxoid said:**
> 
Could not set 512x448 video mode: No available video device
[/CODE]

Everything else works, but most of my emulators don't work with my video adapter. The only emulator working is mupen64. I have a 945g intel graphics accelerator. It all worked with feisty, but it just won't work in gusty.

That is odd, mine is a 945gm, and all works well... Did you do an upgrade from Fiesty to Gutsy? It's possible you might be using i810 driver, instead of the new mode-setting driver "intel".

Try editing your xorg.conf (make a backup though!), change "i810" to "intel"

Or use Screens and Graphics in System -> Administration.

Also, if you switch to this driver, the 915resolution hack is no longer needed. :)

Hope this is the solution you need. :razz:

---

### Post by jorgerosa on 2007-11-15
Any znes trouble? Please try this first.

**Install:  **"Applications" ---> "Add/Remove" (and search there for zsnes, check it, and click on "Apply")
**or, in terminal:  **sudo apt-get install zsnes

**ok, then:**  sudo mkdir -p ~/.kde/socket-*[COLOR=Blue]yourname[/COLOR]*-desktop

**try run it now, **hope this helps. Cya.

---

### Post by Tuxoid on 2007-11-15
i changed my drivers, and it still does cannot find my video adapter. I tried to change it through xorg.conf and Screens and Graphics.

---

### Post by Tuxoid on 2007-11-16
I have tried re-installing my zsnes. still getting the same error.

---

### Post by FranMichaels on 2007-11-18
> **Tuxoid said:**
> i changed my drivers, and it still does cannot find my video adapter. I tried to change it through xorg.conf and Screens and Graphics.

Could you post your xorg.conf?

---

### Post by Tuxoid on 2007-11-19
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by FranMichaels on 2007-11-19
Hmm mine looks similar, same driver, different resolution, less modules loaded... I'm tempted to ask you to back yours up, and generate a new one from scratch...

So bizzare :(

Does 

*zsnes -v 2*

From commandline do anything?

Here is mine, I can't help but wonder if it's just a resolution issue though...

```

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Boardname	"intel"
	Busid		"PCI:0:2:0"
	Driver		"intel"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1920x1200"
	Horizsync	31.5-74.5
	Vertrefresh	56.0-65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1920	1200
		Modes		"1920x1200@60"	"1680x1050@60"	"1600x1024@60"	"1440x900@60"	"1280x800@60"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@56"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"intel"
	Busid		"PCI:0:2:0"
	Driver		"intel"
	Screen	1
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

---

### Post by Tuxoid on 2007-11-21
zsnes -v gives me same error I have been getting all this time.

---

### Post by inversekinetix on 2007-11-21
i just use the windows version in wine, it runs fine.

---

### Post by Tuxoid on 2007-11-23
I think I've narrowed it down. I tried downloading the SDL port of Abuse. It did not work either. The zsnes uses SDL to operate some of the graphics with OpenGL handling the rest of them. So, I believe this is an SDL-related problem. I also tried Using OpenGL with similar results. here's what happened:

Abuse-sdl
```
mike@Mike:~$ abuse
Disabling memory manager, using libc instead
Abuse-SDL 0.7.0
Unable to initialise SDL : No available video device

```

zsnes under OpenGL:
```
mike@Mike:~$ sudo /usr/bin/zsnes -v 5
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
ManyMouse: 2 mice detected.
Using ManyMouse for:
Mouse 0: SynPS/2 Synaptics TouchPad
Mouse 1: Macintosh mouse button emulation
Could not set 256x224-GL video mode.

```

---

### Post by Tuxoid on 2007-12-04
I copied your xorg.conf FranMichaels, into my xorg.conf. The zsnes still does not work. I did upgrade from gusty.

---

### Post by Inquisitorthemad on 2008-12-25
Trying to compile ZSnes on Intrepid, have followed all instructions up to typing in 'make'. This is what happens when I attempt to make:

```
g++  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -D__LIBAO__ -D__OPENGL__ -march=native -O3 -fomit-frame-pointer -fprefetch-loop-arrays -fforce-addr -s -D__RELEASE__ -fno-rtti -o tools/strutil.o -c tools/strutil.cpp
In file included from tools/strutil.cpp:22:
tools/strutil.h: In static member function ‘static int ci_char_traits::compare(const char*, const char*, size_t)’:
tools/strutil.h:34: error: ‘strncasecmp’ was not declared in this scope
make: *** [tools/strutil.o] Error 1
```

I don't even know what's going on here, much less how to fix it.

---

### Post by FranMichaels on 2008-12-25
Get one of the binaries here
[http://board.zsnes.com/phpBB2/viewtopic.php?t=11513](http://board.zsnes.com/phpBB2/viewtopic.php?t=11513)

---

### Post by dfreer on 2008-12-26
> **Inquisitorthemad said:**
> **Trying to compile ZSnes on Intrepid**
... 
I don't even know what's going on here, much less how to fix it.

Yep, basically as the above poster stated, just grab a precompiled binary. There's a couple threads/reasons about your particular problems, I can explain more if needed.

---

### Post by frenchn00b on 2008-12-27
> **kevindubrow said:**
> Hey, Zsnes wont run in Gusty for me. It opens as a black screen and than closes. It is version 1.5 (I got it from the package manager). I have the full text output, but it is huge, so I'll just put the end. Thanks in advance for any help!

"Aborted (core dumped)
"
I can put more of the output, just tell me and you will have it!

- zsnes_1.420.orig.tar.gz  has multiplayer via internet
- stable zsnes: V1.51  get this file : zsnes_1.510.orig.tar.gz 
   then cd /tmp ; tar xvf zsnes_1.510.orig.tar.gz 
   ./configure; make ; make install 
- mednafen could maybe do some multiplayer too

---

### Post by ninexunix on 2009-04-20
Aight this may or may not help someone with current intrepid problems. I first installed mupen64, zsnes was working fine before that point.  Then I had to install some things in mupen64 to get the opengl plugin to even become visual. After all that I run zsnes just to run into this problem:
```

ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
Could not set 1280x960-GL video mode.


```

If you run the command zsnes as sudo you can run it fine with no problems.  So....ok, chown the /dev/(for testing reasons) and set permissions to it.  Set the display settings back to their default and I get this.

```

ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
ManyMouse: 2 mice detected.
Using ManyMouse for:
Mouse 0: PS/2 Generic Mouse
Mouse 1: Macintosh mouse button emulation
Could not set 512x448 video mode: Unable to open a console terminal

```

Hmm lets see what strace zsnes says:

```

execve("/usr/bin/zsnes", ["zsnes"], [/* 34 vars */]) = 0
brk(0)                                  = 0xa211000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f4b000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=68455, ...}) = 0
mmap2(NULL, 68455, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f3a000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libz.so.1", O_RDONLY)    = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P\31\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=83552, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f39000
mmap2(NULL, 86284, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7f23000
mmap2(0xb7f37000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x13) = 0xb7f37000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/local/lib/libSDL-1.2.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\340O\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=1000559, ...}) = 0
mmap2(NULL, 469032, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7eb0000
mmap2(0xb7efa000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x49) = 0xb7efa000
mmap2(0xb7efc000, 157736, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7efc000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libpng12.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\240=\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=149288, ...}) = 0
mmap2(NULL, 152124, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7e8a000
mmap2(0xb7eae000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x23) = 0xb7eae000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libao.so.2", O_RDONLY)   = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\360\17"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=18292, ...}) = 0
mmap2(NULL, 17056, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7e85000
mmap2(0xb7e88000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x3) = 0xb7e88000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libGL.so.1", O_RDONLY)   = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20\304"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=568140, ...}) = 0
mmap2(NULL, 572480, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7df9000
mmap2(0xb7e6a000, 106496, PROT_READ|PROT_WRITE|PROT_EXEC, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x70) = 0xb7e6a000
mmap2(0xb7e84000, 3136, PROT_READ|PROT_WRITE|PROT_EXEC, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7e84000
mprotect(0xbfb67000, 4096, PROT_READ|PROT_WRITE|PROT_EXEC|PROT_GROWSDOWN) = 0
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libstdc++.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0 B\4\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=950392, ...}) = 0
mmap2(NULL, 972972, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7d0b000
mmap2(0xb7dee000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xe3) = 0xb7dee000
mmap2(0xb7df3000, 22700, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7df3000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libm.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0@4\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=149332, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7d0a000
mmap2(NULL, 151680, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7ce4000
mmap2(0xb7d08000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x23) = 0xb7d08000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libgcc_s.so.1", O_RDONLY)    = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260\34"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=54740, ...}) = 0
mmap2(NULL, 57864, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7cd5000
mmap2(0xb7ce2000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xc) = 0xb7ce2000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\340g\1"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=1425800, ...}) = 0
mmap2(NULL, 1431152, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7b77000
mmap2(0xb7ccf000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x158) = 0xb7ccf000
mmap2(0xb7cd2000, 9840, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7cd2000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libpthread.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000H\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=116457, ...}) = 0
mmap2(NULL, 98784, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7b5e000
mmap2(0xb7b73000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x14) = 0xb7b73000
mmap2(0xb7b75000, 4576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7b75000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libdl.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0 \n\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=9676, ...}) = 0
mmap2(NULL, 12408, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7b5a000
mmap2(0xb7b5c000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xb7b5c000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libGLcore.so.1", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\0(\f\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=8961144, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7b59000
mmap2(NULL, 8936320, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb72d3000
mmap2(0xb7b20000, 217088, PROT_READ|PROT_WRITE|PROT_EXEC, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x84d) = 0xb7b20000
mmap2(0xb7b55000, 15232, PROT_READ|PROT_WRITE|PROT_EXEC, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7b55000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/libnvidia-tls.so.1", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P\4\0\000"..., 512) = 512
lseek(3, 1300, SEEK_SET)                = 1300
read(3, "\4\0\0\0\20\0\0\0\1\0\0\0GNU\0\0\0\0\0\2\0\0\0\3\0\0\0"..., 32) = 32
fstat64(3, {st_mode=S_IFREG|0644, st_size=2324, ...}) = 0
mmap2(NULL, 5588, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb72d1000
mmap2(0xb72d2000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0) = 0xb72d2000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libXext.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0 *\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=55772, ...}) = 0
mmap2(NULL, 58940, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb72c2000
mmap2(0xb72cf000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xc) = 0xb72cf000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libX11.so.6", O_RDONLY)  = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\3605\1"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=971436, ...}) = 0
mmap2(NULL, 975508, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb71d3000
mmap2(0xb72be000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xea) = 0xb72be000
mmap2(0xb72c1000, 660, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb72c1000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libXau.so.6", O_RDONLY)  = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\240\t\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=7408, ...}) = 0
mmap2(NULL, 10312, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb71d0000
mmap2(0xb71d2000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xb71d2000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libxcb-xlib.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\300\6\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=5364, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb71cf000
mmap2(NULL, 8252, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb71cc000
mmap2(0xb71cd000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0) = 0xb71cd000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libxcb.so.1", O_RDONLY)  = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\340z\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=95676, ...}) = 0
mmap2(NULL, 98584, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb71b3000
mmap2(0xb71ca000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x16) = 0xb71ca000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libXdmcp.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P\16\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=16628, ...}) = 0
mmap2(NULL, 19520, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb71ae000
mmap2(0xb71b2000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x3) = 0xb71b2000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb71ad000
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb71ac000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb71ac6e0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xb71ca000, 4096, PROT_READ)   = 0
mprotect(0xb71cd000, 4096, PROT_READ)   = 0
mprotect(0xb72be000, 4096, PROT_READ)   = 0
mprotect(0xb72d1000, 4096, PROT_READ|PROT_WRITE) = 0
mprotect(0xb72d1000, 4096, PROT_READ|PROT_EXEC) = 0
mprotect(0xb72d3000, 8704000, PROT_READ|PROT_WRITE) = 0
mprotect(0xb72d3000, 8704000, PROT_READ|PROT_EXEC) = 0
mprotect(0xb7b5c000, 4096, PROT_READ)   = 0
mprotect(0xb7b73000, 4096, PROT_READ)   = 0
mprotect(0xb7ccf000, 8192, PROT_READ)   = 0
mprotect(0xb7ce2000, 4096, PROT_READ)   = 0
mprotect(0xb7d08000, 4096, PROT_READ)   = 0
mprotect(0xb7dee000, 16384, PROT_READ)  = 0
mprotect(0xb7df9000, 462848, PROT_READ|PROT_WRITE) = 0
mprotect(0xb7df9000, 462848, PROT_READ|PROT_EXEC) = 0
mprotect(0xb7eae000, 4096, PROT_READ)   = 0
mprotect(0xb7efa000, 4096, PROT_READ)   = 0
mprotect(0x8304000, 4096, PROT_READ)    = 0
mprotect(0xb7f67000, 4096, PROT_READ)   = 0
munmap(0xb7f3a000, 68455)               = 0
set_tid_address(0xb71ac728)             = 8986
set_robust_list(0xb71ac730, 0xc)        = 0
futex(0xbfb678e0, 0x81 /* FUTEX_??? */, 1) = 0
rt_sigaction(SIGRTMIN, {0xb7b622e0, [], SA_SIGINFO}, NULL, 8) = 0
rt_sigaction(SIGRT_1, {0xb7b62720, [], SA_RESTART|SA_SIGINFO}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL, 8) = 0
getrlimit(RLIMIT_STACK, {rlim_cur=8192*1024, rlim_max=RLIM_INFINITY}) = 0
uname({sys="Linux", node="ninexunix", ...}) = 0
brk(0)                                  = 0xa211000
brk(0xa232000)                          = 0xa232000
futex(0xb7b5d06c, 0x81 /* FUTEX_??? */, 2147483647) = 0
gettimeofday({1240278983, 214157}, NULL) = 0
open("/dev/zero", O_RDWR)               = 3
mmap2(NULL, 8192, PROT_READ|PROT_WRITE|PROT_EXEC, MAP_PRIVATE, 3, 0) = 0xb7f49000
close(3)                                = 0
mmap2(NULL, 405504, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7149000
futex(0xb7e721f8, 0x81 /* FUTEX_??? */, 2147483647) = 0
gettimeofday({1240278983, 216111}, NULL) = 0
gettimeofday({1240278983, 216270}, NULL) = 0
getcwd("/home/ninexunix", 4096)         = 16
getuid32()                              = 1000
socket(PF_FILE, SOCK_STREAM, 0)         = 3
fcntl64(3, F_SETFL, O_RDWR|O_NONBLOCK)  = 0
connect(3, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(3)                                = 0
socket(PF_FILE, SOCK_STREAM, 0)         = 3
fcntl64(3, F_SETFL, O_RDWR|O_NONBLOCK)  = 0
connect(3, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(3)                                = 0
open("/etc/nsswitch.conf", O_RDONLY)    = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=513, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f48000
read(3, "# /etc/nsswitch.conf\n#\n# Example"..., 4096) = 513
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb7f48000, 4096)                = 0
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=68455, ...}) = 0
mmap2(NULL, 68455, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7138000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libnss_compat.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20\16\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=30436, ...}) = 0
mmap2(NULL, 33356, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7f40000
mmap2(0xb7f47000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6) = 0xb7f47000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libnsl.so.1", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\00001\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=87804, ...}) = 0
mmap2(NULL, 100328, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb711f000
mmap2(0xb7134000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x14) = 0xb7134000
mmap2(0xb7136000, 6120, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7136000
close(3)                                = 0
mprotect(0xb7134000, 4096, PROT_READ)   = 0
mprotect(0xb7f47000, 4096, PROT_READ)   = 0
munmap(0xb7138000, 68455)               = 0
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=68455, ...}) = 0
mmap2(NULL, 68455, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7138000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libnss_nis.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20\31\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=38448, ...}) = 0
mmap2(NULL, 41532, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7114000
mmap2(0xb711d000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x8) = 0xb711d000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libnss_files.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\320\30"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=42508, ...}) = 0
mmap2(NULL, 45720, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7108000
mmap2(0xb7112000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x9) = 0xb7112000
close(3)                                = 0
mprotect(0xb7112000, 4096, PROT_READ)   = 0
mprotect(0xb711d000, 4096, PROT_READ)   = 0
munmap(0xb7138000, 68455)               = 0
open("/etc/passwd", O_RDONLY|0x80000 /* O_??? */) = 3
fcntl64(3, F_GETFD)                     = 0x1 (flags FD_CLOEXEC)
_llseek(3, 0, [0], SEEK_CUR)            = 0
fstat64(3, {st_mode=S_IFREG|0644, st_size=1463, ...}) = 0
mmap2(NULL, 1463, PROT_READ, MAP_SHARED, 3, 0) = 0xb7f3f000
_llseek(3, 1463, [1463], SEEK_SET)      = 0
munmap(0xb7f3f000, 1463)                = 0
close(3)                                = 0
mkdir("/home", 0755)                    = -1 EEXIST (File exists)
mkdir("/home/ninexunix", 0755)          = -1 EEXIST (File exists)
mkdir("/home/ninexunix/.zsnes", 0755)   = -1 EEXIST (File exists)
stat64("/home/ninexunix/.zsnes", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
access("/home/ninexunix/.zsnes", W_OK)  = 0
open("/home/ninexunix/.zsnes/zsnesl.cfg", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=16621, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f3f000
read(3, "; PSR-produced config file (stoc"..., 4096) = 4096
read(3, " created. These are very CPU int"..., 4096) = 4096
read(3, "atest Save State Slot on Game Lo"..., 4096) = 4096
read(3, " Quit        19:Paths\n;         "..., 4096) = 4096
read(3, " Checksum & Hash: Don\'t Edit by "..., 4096) = 237
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb7f3f000, 4096)                = 0
open("/home/ninexunix/.zsnes/zsnesl.cfg", O_WRONLY|O_CREAT|O_TRUNC, 0666) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f3f000
write(3, "; PSR-produced config file (stoc"..., 4096) = 4096
write(3, " created. These are very CPU int"..., 4096) = 4096
write(3, "atest Save State Slot on Game Lo"..., 4096) = 4096
write(3, " Quit        19:Paths\n;         "..., 4096) = 4096
write(3, " Checksum & Hash: Don\'t Edit by "..., 237) = 237
close(3)                                = 0
munmap(0xb7f3f000, 4096)                = 0
open("/home/ninexunix/.zsnes/zmovie.cfg", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=2428, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f3f000
read(3, "md_raw_file=\"rawvideo.bin\" ; Onl"..., 4096) = 2428
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb7f3f000, 4096)                = 0
open("/home/ninexunix/.zsnes/zmovie.cfg", O_WRONLY|O_CREAT|O_TRUNC, 0666) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f3f000
write(3, "md_raw_file=\"rawvideo.bin\" ; Onl"..., 2428) = 2428
close(3)                                = 0
munmap(0xb7f3f000, 4096)                = 0
open("/home/ninexunix/.zsnes/zinput.cfg", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=3421, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f3f000
read(3, "; PSR-produced config file (stoc"..., 4096) = 3421
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb7f3f000, 4096)                = 0
open("/home/ninexunix/.zsnes/zinput.cfg", O_WRONLY|O_CREAT|O_TRUNC, 0666) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f3f000
write(3, "; PSR-produced config file (stoc"..., 3421) = 3421
close(3)                                = 0
munmap(0xb7f3f000, 4096)                = 0
open("/home/ninexunix/.zsnes/data.cmb", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/home/ninexunix/.zsnes/zfont.txt", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=8105, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f3f000
read(3, "; empty space 0x00\n00000000\n0000"..., 4096) = 4096
read(3, "mize (Win) 0x4B\n11111100\n1000010"..., 4096) = 4009
close(3)                                = 0
munmap(0xb7f3f000, 4096)                = 0
access("/home/ninexunix", R_OK|X_OK)    = 0
open("/etc/libao.conf", O_RDONLY)       = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=20, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f3f000
read(3, "default_driver=alsa\n", 4096)  = 20
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb7f3f000, 4096)                = 0
open("/home/ninexunix/.libao", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/ao/plugins-2", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|0x80000) = 3
fstat64(3, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
fcntl64(3, F_GETFD)                     = 0x1 (flags FD_CLOEXEC)
getdents(3, /* 20 entries */, 4096)     = 452
stat64("/usr/lib/ao/plugins-2/libalsa09.so", {st_mode=S_IFREG|0644, st_size=13740, ...}) = 0
open("/usr/lib/ao/plugins-2/libalsa09.so", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\360\16"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=13740, ...}) = 0
mmap2(NULL, 16636, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb7f3b000
mmap2(0xb7f3e000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x2) = 0xb7f3e000
close(4)                                = 0
open("/etc/ld.so.cache", O_RDONLY)      = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=68455, ...}) = 0
mmap2(NULL, 68455, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb7138000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libasound.so.2", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000\325"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=813216, ...}) = 0
mmap2(NULL, 816140, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb7040000
mmap2(0xb7103000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0xc2) = 0xb7103000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/librt.so.1", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0`\31\0\000"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=34720, ...}) = 0
mmap2(NULL, 33388, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb7037000
mmap2(0xb703e000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x7) = 0xb703e000
close(4)                                = 0
mprotect(0xb703e000, 4096, PROT_READ)   = 0
mprotect(0xb7103000, 8192, PROT_READ)   = 0
munmap(0xb7138000, 68455)               = 0
stat64("/usr/lib/ao/plugins-2/libalsa09.a", {st_mode=S_IFREG|0644, st_size=7878, ...}) = 0
stat64("/usr/lib/ao/plugins-2/libpulse.so", {st_mode=S_IFREG|0644, st_size=9536, ...}) = 0
open("/usr/lib/ao/plugins-2/libpulse.so", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0 \t\0\000"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=9536, ...}) = 0
mmap2(NULL, 12436, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb7145000
mmap2(0xb7147000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x1) = 0xb7147000
close(4)                                = 0
open("/etc/ld.so.cache", O_RDONLY)      = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=68455, ...}) = 0
mmap2(NULL, 68455, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb7026000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libpulse-simple.so.0", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0p(\0\000"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=50988, ...}) = 0
mmap2(NULL, 53896, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb7018000
mmap2(0xb7024000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0xb) = 0xb7024000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libpulse.so.0", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0`\\\0\000"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=321500, ...}) = 0
mmap2(NULL, 324452, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb6fc8000
mmap2(0xb7016000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x4d) = 0xb7016000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libSM.so.6", O_RDONLY)   = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20\30\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=30064, ...}) = 0
mmap2(NULL, 32980, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb713c000
mmap2(0xb7143000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x6) = 0xb7143000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libICE.so.6", O_RDONLY)  = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\220;\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=86160, ...}) = 0
mmap2(NULL, 96368, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb6fb0000
mmap2(0xb6fc5000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x14) = 0xb6fc5000
mmap2(0xb6fc6000, 6256, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb6fc6000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libcap.so.1", O_RDONLY)      = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\220\t\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=10316, ...}) = 0
mmap2(NULL, 13812, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb7138000
mmap2(0xb713b000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x2) = 0xb713b000
close(4)                                = 0
mprotect(0xb7143000, 4096, PROT_READ)   = 0
mprotect(0xb7016000, 4096, PROT_READ)   = 0
mprotect(0xb7024000, 4096, PROT_READ)   = 0
munmap(0xb7026000, 68455)               = 0
stat64("/usr/lib/ao/plugins-2/libarts.a", {st_mode=S_IFREG|0644, st_size=2454, ...}) = 0
stat64("/usr/lib/ao/plugins-2/libpulse.a", {st_mode=S_IFREG|0644, st_size=5186, ...}) = 0
stat64("/usr/lib/ao/plugins-2/libarts.so", {st_mode=S_IFREG|0644, st_size=5432, ...}) = 0
open("/usr/lib/ao/plugins-2/libarts.so", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0 \7\0\000"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=5432, ...}) = 0
mmap2(NULL, 8336, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb7034000
mmap2(0xb7035000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0) = 0xb7035000
close(4)                                = 0
open("/etc/ld.so.cache", O_RDONLY)      = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=68455, ...}) = 0
mmap2(NULL, 68455, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb6f9f000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libartsc.so.0", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\360\21"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=21904, ...}) = 0
mmap2(NULL, 24868, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb6f98000
mmap2(0xb6f9d000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x4) = 0xb6f9d000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libgmodule-2.0.so.0", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0 \16\0\000"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=13696, ...}) = 0
mmap2(NULL, 16664, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb702f000
mmap2(0xb7032000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x2) = 0xb7032000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libgthread-2.0.so.0", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0@\21\0\000"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=17880, ...}) = 0
mmap2(NULL, 20804, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb7029000
mmap2(0xb702d000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x3) = 0xb702d000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libglib-2.0.so.0", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000\31\1"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=743852, ...}) = 0
mmap2(NULL, 747716, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb6ee1000
mmap2(0xb6f96000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0xb4) = 0xb6f96000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libpcre.so.3", O_RDONLY)     = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000\17\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=165124, ...}) = 0
mmap2(NULL, 168020, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb6eb7000
mmap2(0xb6edf000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x27) = 0xb6edf000
close(4)                                = 0
mprotect(0xb6edf000, 4096, PROT_READ)   = 0
mprotect(0xb6f96000, 4096, PROT_READ)   = 0
mprotect(0xb702d000, 4096, PROT_READ)   = 0
mprotect(0xb7032000, 4096, PROT_READ)   = 0
mprotect(0xb6f9d000, 4096, PROT_READ)   = 0
munmap(0xb6f9f000, 68455)               = 0
stat64("/usr/lib/ao/plugins-2/libesd.la", {st_mode=S_IFREG|0644, st_size=857, ...}) = 0
stat64("/usr/lib/ao/plugins-2/.", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat64("/usr/lib/ao/plugins-2/libalsa09.la", {st_mode=S_IFREG|0644, st_size=850, ...}) = 0
stat64("/usr/lib/ao/plugins-2/liboss.so", {st_mode=S_IFREG|0644, st_size=9532, ...}) = 0
open("/usr/lib/ao/plugins-2/liboss.so", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0 \10\0\000"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=9532, ...}) = 0
mmap2(NULL, 12432, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb6fac000
mmap2(0xb6fae000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x1) = 0xb6fae000
close(4)                                = 0
stat64("/usr/lib/ao/plugins-2/libarts.la", {st_mode=S_IFREG|0644, st_size=941, ...}) = 0
stat64("/usr/lib/ao/plugins-2/libesd.a", {st_mode=S_IFREG|0644, st_size=2666, ...}) = 0
stat64("/usr/lib/ao/plugins-2/libpulse.la", {st_mode=S_IFREG|0644, st_size=827, ...}) = 0
stat64("/usr/lib/ao/plugins-2/..", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat64("/usr/lib/ao/plugins-2/libesd.so", {st_mode=S_IFREG|0644, st_size=5436, ...}) = 0
open("/usr/lib/ao/plugins-2/libesd.so", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P\7\0\000"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=5436, ...}) = 0
mmap2(NULL, 8336, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb7026000
mmap2(0xb7027000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0) = 0xb7027000
close(4)                                = 0
open("/etc/ld.so.cache", O_RDONLY)      = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=68455, ...}) = 0
mmap2(NULL, 68455, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb6ea6000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libesd.so.0", O_RDONLY)  = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20)\0\000"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=40616, ...}) = 0
mmap2(NULL, 43556, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb6fa1000
mmap2(0xb6faa000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x8) = 0xb6faa000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libaudiofile.so.0", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\3007\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=147196, ...}) = 0
mmap2(NULL, 149972, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb6e81000
mmap2(0xb6ea3000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x21) = 0xb6ea3000
close(4)                                = 0
mprotect(0xb6faa000, 4096, PROT_READ)   = 0
munmap(0xb6ea6000, 68455)               = 0
stat64("/usr/lib/ao/plugins-2/liboss.la", {st_mode=S_IFREG|0644, st_size=798, ...}) = 0
stat64("/usr/lib/ao/plugins-2/libnas.la", {st_mode=S_IFREG|0644, st_size=812, ...}) = 0
stat64("/usr/lib/ao/plugins-2/libnas.a", {st_mode=S_IFREG|0644, st_size=3486, ...}) = 0
stat64("/usr/lib/ao/plugins-2/liboss.a", {st_mode=S_IFREG|0644, st_size=4350, ...}) = 0
stat64("/usr/lib/ao/plugins-2/libnas.so", {st_mode=S_IFREG|0644, st_size=5440, ...}) = 0
open("/usr/lib/ao/plugins-2/libnas.so", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\340\7\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=5440, ...}) = 0
mmap2(NULL, 8340, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb6eb4000
mmap2(0xb6eb5000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0) = 0xb6eb5000
close(4)                                = 0
open("/etc/ld.so.cache", O_RDONLY)      = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=68455, ...}) = 0
mmap2(NULL, 68455, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb6e70000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libaudio.so.2", O_RDONLY) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260H\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=91996, ...}) = 0
mmap2(NULL, 95196, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb6e58000
mmap2(0xb6e6e000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x15) = 0xb6e6e000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libXt.so.6", O_RDONLY)   = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\0\313\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0644, st_size=326564, ...}) = 0
mmap2(NULL, 331188, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb6e07000
mmap2(0xb6e54000, 16384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x4c) = 0xb6e54000
close(4)                                = 0
mprotect(0xb6e6e000, 4096, PROT_READ)   = 0
munmap(0xb6e70000, 68455)               = 0
getdents(3, /* 0 entries */, 4096)      = 0
close(3)                                = 0
time(NULL)                              = 1240278983
fstat64(1, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 0), ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f3a000
write(1, "ZSNES v1.51, (c) 1997-2007, ZSNE"..., 39ZSNES v1.51, (c) 1997-2007, ZSNES Team
) = 39
write(1, "Be sure to check http://www.zsne"..., 63Be sure to check http://www.zsnes.com/ for the latest version.
) = 63
write(1, "\n", 1
)                       = 1
write(1, "ZSNES is written by the ZSNES Te"..., 53ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
) = 53
write(1, "ZSNES comes with ABSOLUTELY NO W"..., 65ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
) = 65
write(1, "and you are welcome to redistrib"..., 65and you are welcome to redistribute it under certain conditions;
) = 65
write(1, "please read \'LICENSE.TXT\' thorou"..., 54please read 'LICENSE.TXT' thoroughly before doing so.
) = 54
write(1, "\n", 1
)                       = 1
write(1, "Use ZSNES -? for command line de"..., 43Use ZSNES -? for command line definitions.
) = 43
write(1, "\n", 1
)                       = 1
write(1, "Starting Mouse detection.\n", 26Starting Mouse detection.
) = 26
open("/dev/input", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|0x80000) = 3
fstat64(3, {st_mode=S_IFDIR|0777, st_size=320, ...}) = 0
getdents(3, /* 16 entries */, 4096)     = 304
access("/dev/input/event7", R_OK)       = 0
access("/dev/input/event6", R_OK)       = 0
access("/dev/input/event5", R_OK)       = 0
access("/dev/input/event3", R_OK)       = 0
access("/dev/input/event2", R_OK)       = 0
access("/dev/input/event4", R_OK)       = 0
access("/dev/input/event1", R_OK)       = 0
access("/dev/input/event0", R_OK)       = 0
getdents(3, /* 0 entries */, 4096)      = 0
close(3)                                = 0
open("/dev/input", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|0x80000) = 3
fstat64(3, {st_mode=S_IFDIR|0777, st_size=320, ...}) = 0
getdents(3, /* 16 entries */, 4096)     = 304
stat64("/dev/input/.", {st_mode=S_IFDIR|0777, st_size=320, ...}) = 0
stat64("/dev/input/..", {st_mode=S_IFDIR|0755, st_size=14100, ...}) = 0
stat64("/dev/input/js0", {st_mode=S_IFCHR|0660, st_rdev=makedev(13, 0), ...}) = 0
stat64("/dev/input/event7", {st_mode=S_IFCHR|0660, st_rdev=makedev(13, 71), ...}) = 0
open("/dev/input/event7", O_RDONLY|O_NONBLOCK) = 4
ioctl(4, 0x80404521, 0xbfb67820)        = 64
ioctl(4, 0x80024522, 0xbfb6779e)        = 2
ioctl(4, 0x80084523, 0xbfb67860)        = 8
ioctl(4, 0x80404506, 0x845b4b4)         = 19
stat64("/dev/input/event6", {st_mode=S_IFCHR|0660, st_rdev=makedev(13, 70), ...}) = 0
open("/dev/input/event6", O_RDONLY|O_NONBLOCK) = 5
ioctl(5, 0x80404521, 0xbfb67820)        = 64
ioctl(5, 0x80024522, 0xbfb6779e)        = 2
ioctl(5, 0x80084523, 0xbfb67860)        = 8
close(5)                                = 0
stat64("/dev/input/event5", {st_mode=S_IFCHR|0660, st_rdev=makedev(13, 69), ...}) = 0
open("/dev/input/event5", O_RDONLY|O_NONBLOCK) = 5
ioctl(5, 0x80404521, 0xbfb67820)        = 64
ioctl(5, 0x80024522, 0xbfb6779e)        = 2
ioctl(5, 0x80084523, 0xbfb67860)        = 8
close(5)                                = 0
stat64("/dev/input/event3", {st_mode=S_IFCHR|0660, st_rdev=makedev(13, 67), ...}) = 0
open("/dev/input/event3", O_RDONLY|O_NONBLOCK) = 5
ioctl(5, 0x80404521, 0xbfb67820)        = 64
ioctl(5, 0x80024522, 0xbfb6779e)        = 2
ioctl(5, 0x80084523, 0xbfb67860)        = 8
close(5)                                = 0
stat64("/dev/input/event2", {st_mode=S_IFCHR|0660, st_rdev=makedev(13, 66), ...}) = 0
open("/dev/input/event2", O_RDONLY|O_NONBLOCK) = 5
ioctl(5, 0x80404521, 0xbfb67820)        = 64
ioctl(5, 0x80024522, 0xbfb6779e)        = 2
ioctl(5, 0x80084523, 0xbfb67860)        = 8
close(5)                                = 0
stat64("/dev/input/event4", {st_mode=S_IFCHR|0660, st_rdev=makedev(13, 68), ...}) = 0
open("/dev/input/event4", O_RDONLY|O_NONBLOCK) = 5
ioctl(5, 0x80404521, 0xbfb67820)        = 64
ioctl(5, 0x80024522, 0xbfb6779e)        = 2
ioctl(5, 0x80084523, 0xbfb67860)        = 8
close(5)                                = 0
stat64("/dev/input/by-id", {st_mode=S_IFDIR|0755, st_size=100, ...}) = 0
stat64("/dev/input/event1", {st_mode=S_IFCHR|0660, st_rdev=makedev(13, 65), ...}) = 0
open("/dev/input/event1", O_RDONLY|O_NONBLOCK) = 5
ioctl(5, 0x80404521, 0xbfb67820)        = 64
ioctl(5, 0x80024522, 0xbfb6779e)        = 2
ioctl(5, 0x80084523, 0xbfb67860)        = 8
close(5)                                = 0
stat64("/dev/input/by-path", {st_mode=S_IFDIR|0755, st_size=180, ...}) = 0
stat64("/dev/input/mouse1", {st_mode=S_IFCHR|0660, st_rdev=makedev(13, 33), ...}) = 0
stat64("/dev/input/event0", {st_mode=S_IFCHR|0660, st_rdev=makedev(13, 64), ...}) = 0
open("/dev/input/event0", O_RDONLY|O_NONBLOCK) = 5
ioctl(5, 0x80404521, 0xbfb67820)        = 64
ioctl(5, 0x80024522, 0xbfb6779e)        = 2
ioctl(5, 0x80084523, 0xbfb67860)        = 8
ioctl(5, 0x80404506, 0x845b508)         = 33
stat64("/dev/input/mouse0", {st_mode=S_IFCHR|0660, st_rdev=makedev(13, 32), ...}) = 0
stat64("/dev/input/mice", {st_mode=S_IFCHR|0660, st_rdev=makedev(13, 63), ...}) = 0
getdents(3, /* 0 entries */, 4096)      = 0
close(3)                                = 0
write(1, "ManyMouse: 2 mice detected.\n", 28ManyMouse: 2 mice detected.
) = 28
write(1, "Using ManyMouse for:\n", 21Using ManyMouse for:
)  = 21
write(1, "Mouse 0: PS/2 Generic Mouse\n", 28Mouse 0: PS/2 Generic Mouse
) = 28
write(1, "Mouse 1: Macintosh mouse button "..., 42Mouse 1: Macintosh mouse button emulation
) = 42
mmap2(NULL, 1056768, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6d05000
mmap2(NULL, 270336, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6cc3000
mmap2(NULL, 270336, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6c81000
mmap2(NULL, 139264, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6c5f000
mmap2(NULL, 765952, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6ba4000
mmap2(NULL, 155648, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6b7e000
mmap2(NULL, 307200, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6b33000
mmap2(NULL, 1056768, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6a31000
mmap2(NULL, 532480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb69af000
mmap2(NULL, 270336, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb696d000
mmap2(NULL, 135168, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb694c000
mmap2(NULL, 266240, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb690b000
mmap2(NULL, 135168, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb68ea000
brk(0xa25c000)                          = 0xa25c000
mmap2(NULL, 6365184, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb62d8000
mmap2(NULL, 8392704, PROT_READ|PROT_WRITE|PROT_EXEC, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb5ad7000
mprotect(0xb5ad7000, 4096, PROT_NONE)   = 0
clone(child_stack=0xb62d7494, flags=CLONE_VM|CLONE_FS|CLONE_FILES|CLONE_SIGHAND|CLONE_THREAD|CLONE_SYSVSEM|CLONE_SETTLS|CLONE_PARENT_SETTID|CLONE_CHILD_CLEARTID, parent_tidptr=0xb62d7bd8, {entry_number:6, base_addr:0xb62d7b90, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}, child_tidptr=0xb62d7bd8) = 8987
futex(0xa216860, 0x80 /* FUTEX_??? */, 0) = 0
open("/dev/fb0", O_RDWR)                = 3
close(3)                                = 0
open("/dev/fb0", O_RDWR)                = 3
ioctl(3, FBIOGET_FSCREENINFO, 0xbfb6770c) = 0
mmap2(NULL, 10485760, PROT_READ|PROT_WRITE, MAP_SHARED, 3, 0) = 0xb50d7000
ioctl(3, FBIOGET_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
open("/etc/fb.modes", O_RDONLY)         = -1 ENOENT (No such file or directory)
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67664) = 0
open("/dev/tty0", O_WRONLY)             = 6
ioctl(6, VIDIOC_QUERYCAP or VT_OPENQRY, 0xa216d5c) = 0
close(6)                                = 0
geteuid32()                             = 1000
open("/dev/tty", O_RDWR)                = 6
ioctl(6, VT_GETSTATE, 0xbfb675d6)       = -1 EINVAL (Invalid argument)
ioctl(6, KDGKBMODE, 0xbfb675e0)         = -1 EINVAL (Invalid argument)
close(6)                                = 0
munmap(0xb50d7000, 10485760)            = 0
close(3)                                = 0
rt_sigaction(SIGINT, {SIG_DFL}, {SIG_DFL}, 8) = 0
rt_sigaction(SIGINT, {SIG_DFL}, {SIG_DFL}, 8) = 0
rt_sigaction(SIGTERM, {SIG_DFL}, {SIG_DFL}, 8) = 0
rt_sigaction(SIGTERM, {SIG_DFL}, {SIG_DFL}, 8) = 0
open("/dev/fb0", O_RDWR)                = 3
close(3)                                = 0
open("/dev/fb0", O_RDWR)                = 3
ioctl(3, FBIOGET_FSCREENINFO, 0xbfb6762c) = 0
mmap2(NULL, 10485760, PROT_READ|PROT_WRITE, MAP_SHARED, 3, 0) = 0xb50d7000
ioctl(3, FBIOGET_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
open("/etc/fb.modes", O_RDONLY)         = -1 ENOENT (No such file or directory)
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
ioctl(3, FBIOPUT_VSCREENINFO, 0xbfb67584) = 0
open("/dev/tty0", O_WRONLY)             = 6
ioctl(6, VIDIOC_QUERYCAP or VT_OPENQRY, 0xa216d5c) = 0
close(6)                                = 0
geteuid32()                             = 1000
open("/dev/tty", O_RDWR)                = 6
ioctl(6, VT_GETSTATE, 0xbfb674f6)       = -1 EINVAL (Invalid argument)
ioctl(6, KDGKBMODE, 0xbfb67500)         = -1 EINVAL (Invalid argument)
close(6)                                = 0
munmap(0xb50d7000, 10485760)            = 0
close(3)                                = 0
rt_sigaction(SIGINT, {SIG_DFL}, {SIG_DFL}, 8) = 0
rt_sigaction(SIGINT, {SIG_DFL}, {SIG_DFL}, 8) = 0
rt_sigaction(SIGTERM, {SIG_DFL}, {SIG_DFL}, 8) = 0
rt_sigaction(SIGTERM, {SIG_DFL}, {SIG_DFL}, 8) = 0
write(2, "Could not set 512x448 video mode"..., 68Could not set 512x448 video mode: Unable to open a console terminal
) = 68
close(5)                                = 0
open("/home/ninexunix/.zsnes/zsnesl.cfg", O_WRONLY|O_CREAT|O_TRUNC, 0666) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb5ad6000
write(3, "; PSR-produced config file (stoc"..., 4096) = 4096
write(3, " created. These are very CPU int"..., 4096) = 4096
write(3, "atest Save State Slot on Game Lo"..., 4096) = 4096
write(3, " Quit        19:Paths\n;         "..., 4096) = 4096
write(3, " Checksum & Hash: Don\'t Edit by "..., 237) = 237
close(3)                                = 0
munmap(0xb5ad6000, 4096)                = 0
open("/home/ninexunix/.zsnes/zinput.cfg", O_WRONLY|O_CREAT|O_TRUNC, 0666) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb5ad6000
write(3, "; PSR-produced config file (stoc"..., 3421) = 3421
close(3)                                = 0
munmap(0xb5ad6000, 4096)                = 0
open("/home/ninexunix/.zsnes/zinput.cfg", O_WRONLY|O_CREAT|O_TRUNC, 0666) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb5ad6000
write(3, "; PSR-produced config file (stoc"..., 3421) = 3421
close(3)                                = 0
munmap(0xb5ad6000, 4096)                = 0
munmap(0xb6d05000, 1056768)             = 0
munmap(0xb6cc3000, 270336)              = 0
munmap(0xb6c81000, 270336)              = 0
munmap(0xb6c5f000, 139264)              = 0
munmap(0xb6ba4000, 765952)              = 0
munmap(0xb6b7e000, 155648)              = 0
munmap(0xb6b33000, 307200)              = 0
munmap(0xb62d8000, 6365184)             = 0
munmap(0xb6a31000, 1056768)             = 0
munmap(0xb69af000, 532480)              = 0
munmap(0xb696d000, 270336)              = 0
munmap(0xb690b000, 266240)              = 0
munmap(0xb68ea000, 135168)              = 0
munmap(0xb694c000, 135168)              = 0
futex(0xb62d7bd8, FUTEX_WAIT, 8987, NULL) = 0
rt_sigaction(SIGSEGV, NULL, {SIG_DFL}, 8) = 0
rt_sigaction(SIGBUS, NULL, {SIG_DFL}, 8) = 0
rt_sigaction(SIGFPE, NULL, {SIG_DFL}, 8) = 0
rt_sigaction(SIGQUIT, NULL, {SIG_DFL}, 8) = 0
munmap(0xb7034000, 8336)                = 0
munmap(0xb6f98000, 24868)               = 0
munmap(0xb702f000, 16664)               = 0
munmap(0xb7029000, 20804)               = 0
munmap(0xb6ee1000, 747716)              = 0
munmap(0xb6eb7000, 168020)              = 0
munmap(0xb7145000, 12436)               = 0
munmap(0xb7018000, 53896)               = 0
munmap(0xb6fc8000, 324452)              = 0
munmap(0xb7138000, 13812)               = 0
munmap(0xb7026000, 8336)                = 0
munmap(0xb6fa1000, 43556)               = 0
munmap(0xb6e81000, 149972)              = 0
munmap(0xb7f3b000, 16636)               = 0
munmap(0xb7040000, 816140)              = 0
munmap(0xb6fac000, 12432)               = 0
munmap(0xb6eb4000, 8340)                = 0
munmap(0xb6e58000, 95196)               = 0
munmap(0xb6e07000, 331188)              = 0
munmap(0xb713c000, 32980)               = 0
munmap(0xb6fb0000, 96368)               = 0
munmap(0xb7149000, 405504)              = 0
munmap(0xb7f49000, 8192)                = 0
exit_group(0)                           = ?
Process 8986 detached


```

now according to one of those statements /etc/ld.so.nohwcap is not even there.  Now to my understanding that's my nvidia settings right?  Is there anything I'm not understanding here?

Edit Note*  Found that the zsnes itself is actually running under wine if you go into /usr/bin/zsnes and right click the file and go into the properties of it.  It's setup to run from wine.  This is the ubuntu's release from the add and removes section.  So not sure if anything else is contributing to this problem or not.  Wine seems to run fine. Not sure what's goin on.  Anyone got any ideas?

Edit Note 2*  Seems the /etc/ld.so.nohwcap is a problem with strace itself reporting incorrectly so disregard it.

---

### Post by nightrazer on 2010-10-03
hi! i am putting some life into this thread with something i dont quite understand.. :confused:

i have followed every step i could find with the compileing from source but it just wont work.
this is my output.

[PHP]g++  -pipe -I. -I/usr/local/include -I/usr/include -D__UNIXSDL__  -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT  -D__LIBAO__ -D__OPENGL__ -march=native -O3 -fomit-frame-pointer -fprefetch-loop-arrays -fforce-addr -s -D__RELEASE__ -fno-rtti -o tools/strutil.o -c tools/strutil.cpp
In file included from tools/strutil.cpp:22:
tools/strutil.h: In static member function ‘static int ci_char_traits::compare(const char*, const char*, size_t)’:
tools/strutil.h:34: error: ‘strncasecmp’ was not declared in this scope
make: *** [tools/strutil.o] Error 1[/PHP]

i tried following the link mentioned by one of the posters, but it was broken and i could not find any good information elsewhere.

this is my config output that looks fine..
[PHP]root@Skydrive:/home/nightrazer/Downloads/Snes/zsnes_1_51/src# ./configure
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking target system type... x86_64-unknown-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for nasm... nasm
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.2.0... yes
checking for zlib - version >= 1.2.3... yes
checking for libpng - version >= 1.2.0... yes
checking if you want the zsnes debugger... yes
checking for initscr in -lcurses... yes
checking for initscr in -lncurses... yes
checking for initscr in -lpdcurses... no
checking if you want libao support... no
checking how to run the C preprocessor... gcc -E
checking for X... libraries , headers 
checking for glGetError in -lGL... yes
checking for OpenGL... yes
checking for JMA support... yes
checking for cpu info... found
checking if you want gdb friendly executable... no
checking which cpu architecture to optimize for... native
checking if you want crazy optimizations... no
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking whether sys/types.h defines makedev... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged


ZSNES v1.51

SDL support                   Version 1.2.14
NASM support                  NASM version 2.08.01 compiled on Jun  2 2010
zlib support                  Version 1.2.3.4
PNG support                   Yes, version 1.2.44
OpenGL support                Yes
JMA support                   Yes
ZSNES debugger                Enabled[/PHP]


i am running 64bit debian squeeze testing :KS
i hope you can help. :)
// with kind regards from nightrazer

---

### Post by dfreer on 2010-10-03
> **nightrazer said:**
> 
i am running 64bit debian squeeze testing :KS
i hope you can help. :)
// with kind regards from nightrazer

ZSNES contains 32-bit ASM code, which means it can only be compiled as a 32-bit binary. You can run 32-bit binaries on your 64-bit system, if you have the correct libraries installed.

If you MUST compile from source, you have several options:
(1). Compile from another 32-bit machine, making sure that it is optimized correctly for your 64-bit CPU instruction set. You can also use a generic instruction set like i686.
(2). Load up a 32-bit live CD on your machine and compile from there, it will be a bit slow but whatever. Than save the binary to a USB drive and bring it over.
(3). Set up a 32-bit chroot on your 64-bit machine and compile in that.

The best option, though, would be to grab a precompiled binary. Also, make sure you get one that was compiled with the latest source for linux 1.51b, located here:
[http://board.zsnes.com/phpBB3/viewtopic.php?f=2&t=11513](http://board.zsnes.com/phpBB3/viewtopic.php?f=2&t=11513)

He has precompiled 1.51b binaries there as well. Just grab the right one and make sure your libao is set up correctly as these binaries use it.

---

### Post by chr1sto on 2013-02-18
I tried to set the resolution to 1600x1200, but zsnes was crashed. I removed all program files. Even searched the whole drive for them and deleted all, but when I reinstall the program, still want to run in 1600x1200 and crashes. Any suggestions?

---

### Post by chr1sto on 2013-02-18
Okey. I solved. In terminal: "zsnes -v 2"

> **chr1sto said:**
> I tried to set the resolution to 1600x1200, but zsnes was crashed. I removed all program files. Even searched the whole drive for them and deleted all, but when I reinstall the program, still want to run in 1600x1200 and crashes. Any suggestions?

---

### Post by overdrank on 2013-02-18
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

