---
title: "Any Game video capturing software (like fraps)?"
date: 2006-07-05
forum: Gaming &amp; Leisure
---

### Post by Intangir on 2006-07-05
is there any software like fraps for linux?

fraps basically makes movies off of your games that are running.. it seems to know to capture only windows that are using directX or openGL

it has a hotkey to turn it on and off

it records to a big uncompressed format, that you can then encode to whatever lossy codecs, or video edit in uncompressed unlossy formats


it is pretty good for making demos/vids off of games

is there anything like that for linux? i used one called istanbul but it doesnt capture from game windows

---

### Post by XVampireX on 2006-07-06
You might be able to try fraps on wine, but I don't promise anything as I haven't used fraps myself. And I'm also not sure if it will capture native games.

Best of luck.

---

### Post by Intangir on 2006-07-06
im seriously doubting it will work
i suppose i could try it though

---

### Post by keithjr on 2006-07-06
it seems like any software that would exist would severly hamper game performance... especially if it is doing frame grabbing in-line... I do not know of any such linux program but I can take a look around later.

does fraps hurt performance in windows much?  I've never used it.

---

### Post by dubnmike on 2006-07-06
[QUOTE=keithjr]
does fraps hurt performance in windows much?  I've never used it.[/QUOTE]

Yes it does.  You usually have to turn off eye candy and lower resolutions to get it to run at a decent FPS while recording.

---

### Post by Katryx on 2006-07-06
I'm also interested in this.

I don't care about framerate loss - I realized that if I ran fraps (in Windows) briefly once or twice before starting the actual recording, there was much less issue.  I bet the same might be true of a Linux video recording app (if there is one).

---

### Post by n00blar on 2006-08-29
I tried installing the latest version of fraps and wine failed to do the installation.

I wish there was a company that would write something like this for linux....I'd buy it just as I purchased Fraps. ](*,)

---

### Post by justin whitaker on 2006-08-29
I saw an app on LinuX Gamers, but I can't get to the site from work: websense. :evil:

---

### Post by n00blar on 2006-08-29
> **justin whitaker said:**
> I saw an app on LinuX Gamers, but I can't get to the site from work: websense. :evil:

Is Yukon what you're referring to?

---

### Post by justin whitaker on 2006-08-29
> **n00blar said:**
> Is Yukon what you're referring to?

Yeah, that's it. It's very alpha from what I understand.

---

### Post by n00blar on 2006-08-29
Yes, it is.

I'll come back to that application in a few months.

---

### Post by wereHamster on 2006-09-15
It's alpha.. but who does decide when the software hits beta or release status? Yukon has undergone quite big changes in the last few days.. and it works for me and for (almost) all people who contacted me and reported bugs (which I've then fixed..)

oh.. btw, the homepage is here: [http://www.neopsis.com/projects/yukon/](http://www.neopsis.com/projects/yukon/)

---

### Post by remoir on 2006-09-17
i can't download yukon. 

got this error message -> "protocol "svn" isn't associated with any program" 

What's wrong ?

---

### Post by deeek on 2006-09-17
> **remoir said:**
> i can't download yukon. 

got this error message -> "protocol "svn" isn't associated with any program" 

What's wrong ?
You must use a program called SVN to "check out" the source code.  You can use a program called rapidsvn, which makes it pretty easy.

---

### Post by Eazy© on 2006-09-17
Anyone knows how to install and use this? I seem to be to stupid to figure it out.

I get this when I try to install:
```
eazy@linux:~/Desktop/hmm$ sudo ./build.sh lib x86
Cleaning directory...
Compiling patcher...
Duplicating libraries...
   libGL.so
   libX11.so
Building yukon...
yasm: FATAL: unrecognized object format `elf32'
scons: *** [build/x86/asm/x86/huffman.os] Error 1
Restoring libraries...
cp: kan inte ta status på "build/x86/yPreload.x86.so": Filen eller katalogen finns inte
   libGL.so
   libX11.so
Cleaning up...

Please add "$HOME/.preload/lib" to LD_LIBRARY_PATH
```

---

### Post by wereHamster on 2006-09-17
> **Eazy© said:**
> Anyone knows how to install and use this? I seem to be 

let me guess.. you didn't read the wiki. Specifically the part about the required software where I mention that you need yasm, version 0.5.0 or newer.

BTW, I never mentioned that you need root rights to install it.

---

### Post by Eazy© on 2006-09-17
I had a too old yasm so I compiled it and installed the latest yasm.

I did read the wiki but I didn't understand it. If I dont install with sudo it will not install.

After I installed i did this in console: export LD_LIBRARY_PATH=~/.preload/lib

Now I just need to figure ot how to run it. Though I would have a file called ".yukon" where to setup options in, but I dont have that file.

Think the wiki needs a howto made for not so smart ppl. like myselfe.

---

### Post by wereHamster on 2006-09-17
> **Eazy© said:**
> 
If I dont install with sudo it will not install.

Please, tell me why you think it didn't install properly without sudo. I never write to system directories and there is no reason whatsoever to have root right during installation.
Depending on how sudo handles enviroment variables it's possible that sudo installs the files to the wrong directory. I don;t use sudo so I don't now exactly.

> **Eazy© said:**
> 
Though I would have a file called ".yukon" where to setup options in, but I dont have that file.


$HOME/.yukon should be a directory, not a file! You need to create that directory, and there is an example how to set each option on the wiki.

---

### Post by Eazy© on 2006-09-17
You are right. After I deleted .preload (that the previous install with the too old yasm installed) it installed nicely without sudo.

I did added all options in $HOME/.yukon and made the yukonOutput dir for the for the output.

when I start in consol with: ./yServer 9000 and press numpad minus I get no file. Dont think Yukon starts correctly. When I start Yukon, what am I expected to se in the console, so I can see if it started correctly?

---

### Post by wereHamster on 2006-09-17
> **Eazy© said:**
> 
when I start in consol with: ./yServer 9000 and press numpad minus I get no file.

You also need to start the game you want to capture!

---

### Post by Eazy© on 2006-09-17
I tried different hotkeys but I cant get this to work. The game I use is UT2004 and I think ut2004 keeps all keys for it selfe. I tried to record glxgears but that dont work either. Perhaps I have to give up on this :/

---

### Post by wereHamster on 2006-09-17
> **Eazy© said:**
> I tried different hotkeys but I cant get this to work. The game I use is UT2004 and I think ut2004 keeps all keys for it selfe. I tried to record glxgears but that dont work either. Perhaps I have to give up on this :/

I can't help you if you don't tell me what exactly happens! glxgears should work always, if that fails then you did something wrong.

What do you see in the console?

---

### Post by Eazy© on 2006-09-17
I dont see anything
[http://web.telia.com/~u00175529/desk6.png](http://web.telia.com/~u00175529/desk6.png)


When I install last time I didnt see any errors. Would be nice if I could make movies of my demo I have.

---

### Post by wereHamster on 2006-09-17
> **Eazy© said:**
> I dont see anything

And your game is where? yServer does nothing else than dumping the data it recieves from your game to the harddrive.

---

### Post by Eazy© on 2006-09-17
1. I start Yokon with this in console: /home/eazy/Desktop/hmm/build/x86/yServer 9000

2. Start UT2004

3. Press the hotkey to start recording

I tried to do the same but with glxgears but I get no outputfile in /home/eazy/yukonOutput

hmm, where my game is? If you mean where it is installed, then: /home/eazy/ut2004

---

### Post by wereHamster on 2006-09-17
> **Eazy© said:**
> 2. Start UT2004

3. Press the hotkey to start recording

Start the game from a console and post the output here.

---

### Post by Eazy© on 2006-09-17
eazy@linux:~/ut2004$ /home/eazy/ut2004/ut2004
Defaulting to false
Defaulting to false
Resolved ut2004master2.epicgames.com -> 207.135.145.7
Connection established.
eazy@linux:~/ut2004$

---

### Post by wereHamster on 2006-09-18
I don't have the game but I installed the demo and it works just fine:

```
tomc@eiger ~ $ ./ut2004demo
Resolved ut2004master1.epicgames.com -> 207.135.145.6
Connection established.
 *** here I pressed the hotkey ***
yEngineEvent: start
yEngineStart(): 0x8f1b728 - 0x01600013
yEngineStart(): 0xa83e8d8, insets: 0:0:0:0
scale: full
server address is: 192.168.0.6:9000
connection to server established
yEngineStart(): 0xa83e8d8, capturing 1280:1024
yEngine thread started
yEngine: size: 1280:1024 => 1280:1024
```

---

### Post by Eazy© on 2006-09-18
I have tried most I can think of, but I cant get this to work. Maybe if I had a idiot proof step by step guide to rule out misstakes I might have done, but I can ask for that I think. After reading the wiki many times and done exactly as it says, I wonder why I cant get it to work for me. Maybe it might be that I use Kubuntu. I did try with another windowmanager (e17) to perhaps rule out if it might be a hotkey problem. I would like to thank you wereHamster for your effort to try to help me. To bad I couldnt get this to work. Guesse I have to use windows with Fraps, to make movies of my demos.

Regards
Eazy

---

### Post by Eazy© on 2006-09-26
I had another go with this. After last time I tried this, I just deleted the directory where I had Yukon (I guesse there is no uninstall scrpit to uninstall this).

When I try to install this now I get:
```
eazy@linux:~/Desktop/yukon$ ./build.sh lib x86
Cleaning directory...
Compiling patcher...
Duplicating libraries...
   libGL.so
   libX11.so
Building yukon...
build/x86/yukonPreload/yEngine.c: In function 'yEngineStart':
build/x86/yukonPreload/yEngine.c:347: warning: pointer targets in passing argume
nt 6 of 'XGetGeometry' differ in signedness
build/x86/yukonPreload/yEngine.c:347: warning: pointer targets in passing argume
nt 7 of 'XGetGeometry' differ in signedness
build/x86/yukonPreload/yEngine.c:347: warning: pointer targets in passing argume
nt 8 of 'XGetGeometry' differ in signedness
build/x86/yukonPreload/yEngine.c:347: warning: pointer targets in passing argume
nt 9 of 'XGetGeometry' differ in signedness
build/x86/yukonPreload/yHooks.c: In function 'glXGetProcAddressARB':
build/x86/yukonPreload/yHooks.c:171: warning: pointer targets in passing argumen
t 1 of 'strlen' differ in signedness
build/x86/yukonPreload/yHooks.c:171: warning: pointer targets in passing argumen
t 1 of '__builtin_strcmp' differ in signedness
build/x86/yukonPreload/yHooks.c:171: warning: pointer targets in passing argumen
t 1 of 'strlen' differ in signedness
build/x86/yukonPreload/yHooks.c:171: warning: pointer targets in passing argumen
t 1 of '__builtin_strcmp' differ in signedness
build/x86/yukonPreload/yHooks.c:171: warning: pointer targets in passing argumen
t 1 of '__builtin_strcmp' differ in signedness
build/x86/yukonPreload/yHooks.c:171: warning: pointer targets in passing argumen
t 1 of '__builtin_strcmp' differ in signedness
build/x86/yukonCore/yCompressor.c: In function 'test':
build/x86/yukonCore/yCompressor.c:161: warning: pointer targets in passing argum
ent 1 of 'strcpy' differ in signedness
build/x86/yukonCore/yCompressor.c: In function 'huffDecompress':
build/x86/yukonCore/yCompressor.c:261: warning: pointer targets in initializatio
n differ in signedness
build/x86/yukonCore/yCompressor.c: In function 'test':
build/x86/yukonCore/yCompressor.c:161: warning: pointer targets in passing argum
ent 1 of 'strcpy' differ in signedness
build/x86/yukonCore/yCompressor.c: In function 'huffDecompress':
build/x86/yukonCore/yCompressor.c:261: warning: pointer targets in initializatio                                                                                n differ in signedness
Restoring libraries...
   libGL.so
   libX11.so
Cleaning up...

Please add "$HOME/.preload/lib" to LD_LIBRARY_PATH
```

Strange thing is, when I install it again I get no warnings/errors:

```
eazy@linux:~/Desktop/yukon$ ./build.sh lib x86
Cleaning directory...
Compiling patcher...
Duplicating libraries...
   libGL.so
   libX11.so
Building yukon...
Restoring libraries...
   libGL.so
   libX11.so
Cleaning up...

Please add "$HOME/.preload/lib" to LD_LIBRARY_PATH

eazy@linux:~/Desktop/yukon$ 
```

Anyone with Ubuntu got this to work?

---

### Post by Ferrat on 2007-03-07
I know this is an old thread but Yukon now has a guide on it's homepage that's real easy and shows just how to install to Ubuntu, worked on the first try for me =)

---

### Post by cor2y on 2007-03-07
The Program works just as the author said and as the wiki indicated.
However does anyone know how to optimize it for a smoother frame rate capture?
Unfortunately i don't have a Hyperthreaded Intel  or an AMD 64 CPU.
AS indicated for the best screencapture in the Wiki on the site.
The Ram and harddrive space i have plenty of but i am still using an ATHLON XP CPU

When i capture Neverwinter Nights the frame rate slows down, and even the captured vid is at a reduced frame rate.


Anyway i can adjust the frame rate capture to say 15 fps instead of  the standrard 25?


Edit
Ok looked at the conf file and found the option to lower frame capture speed.
Unfortunately it didn't make much difference in the speed the system was under like other screencapture software.
Looks like you will need either a hyperthreaded cpu or 64bit one or a seperate partition/disk for the file to be output to, to reduce system strain.

---

### Post by Ferrat on 2007-03-08
yeah I have that problem aswell tho I have AMD64 and so on  but messing around with it for capturing at greater speed

---

### Post by primski on 2007-03-08
Could this great program be used to record desktop, like make presentation of compiz ?

---

### Post by Intangir on 2007-03-19
wow this thread is still semi active
thats amazing

looks like alot of great new info on it too, im gonna check out this yukon

ive been trying xvidcap, it sorta works, but i had some issues with it before and stopped, i dont recall exactly what went wrong

i think it was when any 3d stuff was on screen it was crapping out

---

### Post by Intangir on 2007-03-19
i got it working on glxgears, but not World of Warcraft in Wine

---

### Post by wereHamster on 2007-03-20
> **primski said:**
> Could this great program be used to record desktop, like make presentation of compiz ?

beryl has a plugin which uses yukon's backend to capture the screen (beryl-plugins-vidcap). Though no such thing exists for compiz.. at least none that I know of.

---

### Post by wereHamster on 2007-03-22
> **cor2y said:**
> 
When i capture Neverwinter Nights the frame rate slows down, and even the captured vid is at a reduced frame rate.

Looks like you will need either a hyperthreaded cpu or 64bit one or a seperate partition/disk for the file to be output to, to reduce system strain.

No, these kind of issues (low framerate in game and/or resulting video) are caused by unoptimized drivers. NVidia cards work best (with the proprietary driver), don't know about the opensource 'nv' driver though, never tried it. ATI cards suck badly, the drivers have a very bad quality! I haven't found any user yet who has an ATI card and is able to capture at a decent framerate.

You don't need a hypertheaded/64bit CPU nor a separate partition (which wouldn't help anyway). Yukon supports multithreading, so you'll get better performance on a SMP system, but it doesn't mean you are required to have one. If you want to reduce system load save the video on a different harddrive than your game is on. This way saving the video won't interfere with the game loading game data (textures, models etc).

---

### Post by lakersforce on 2007-03-22
There is also a program in the repositories named "Instanbul Desktop Session Recorder".

---

### Post by cor2y on 2007-03-23
wereHamster you could be right i have always heard of the substandard of ATI drivers but only experienced this when trying to get either beryl or compiz to work (never could get them to work correctly) and as i am using an ATI card this could be the problem.
The open source ones don't work too well on hardware 3d accelerated stuff unfortunately.

---

### Post by Popperatum on 2007-04-09
hello guys

i have installed yukon with success and i make a video with glxgears but i have some problem with enemy-territory

plz help me!!!

in a few day i'll hope contact the development of yukon project's for more help

---

### Post by chuck_h1987 on 2007-08-22
Ok look no one is going to even try to fix/create new vid programs for linux. almost 3/4's of todays games are for Win32 systems. I will talk to my friend he is in college for computer programing. I will see what he says about it. maybe even write ya somthin. so chill for now.

oh and instanbul lags ur FPS bad

---

### Post by satupe@gmail.com on 2008-11-18
LIVES ([http://lives.sourceforge.net/index.php?do=downloads](http://lives.sourceforge.net/index.php?do=downloads)) gets the job done.  The biggest issue I had was getting the jack server to work with my MAUDIO sound card.  Once you successfully install LIVES, start it up and click Tools/Capture External Window, and LIVES will lead you the rest of the way.

LIVES also works great for creating movies in Google Earth:)

---

### Post by ementos on 2009-04-02
Hmmm...
I think recordmydesktop may be good.
```
sudo apt-get install recordmydesktop
```
```
recordmydesktop
```
and 
**Ctrl + C** - end record...
The movie should appear in home folder
Greet =)

---

### Post by Emanuele_Z on 2009-04-02
**glc** is very powerful and fast.
[http://nullkey.ath.cx/projects/glc/wiki/HowtoCapture](http://nullkey.ath.cx/projects/glc/wiki/HowtoCapture)

---

### Post by BrokenKingpin on 2009-04-02
Record My Desktop worked great for me when recording my Compiz desktop. I will give it a try with a game tonight to see how it works.

---

### Post by Simian Man on 2009-04-02
> **Intangir said:**
> is there anything like that for linux? i used one called istanbul but it doesnt capture from game windows

Yes it does!  I use it for exactly this purpose.  Right click the icon and select "Select Window to Record" and click on your game window.  I don't know if it works for full screen, but most games can be run windowed anyway.

---

### Post by ementos on 2009-04-02
And I've problem with **glc-capture**
```
jozio@ementos-desktop:~$ glc-capture /opt/google-earth//googleearth %f
Warning: Unable to create prefs directory '/home/jozio/.googleearth'. File exists.
Google Earth appears to be running already. Please kill the
 existing process, or delete /home/jozio/.googleearth/instance-running-lock if this is an error.
[  20.10s       file error ] can't open googleearth-bin-6370-0.glc: Permission denied (13)
[  20.10s       main error ] can't start capturing: Permission denied (13)
```
Greet :)

---

### Post by BrokenKingpin on 2009-04-02
Record My Desktop did not work for games. istanbul works for games, but it kills the frame rate to the point the game is unplayable, and I have a decent gaming rig.

---

### Post by ariedry on 2009-04-03
> **Intangir said:**
> is there any software like fraps for linux?

fraps basically makes movies off of your games that are running.. it seems to know to capture only windows that are using directX or openGL

it has a hotkey to turn it on and off

it records to a big uncompressed format, that you can then encode to whatever lossy codecs, or video edit in uncompressed unlossy formats


it is pretty good for making demos/vids off of games

is there anything like that for linux? i used one called istanbul but it doesnt capture from game windows

Applications > Add / Remove... and search for "screen recorder"

u should find Istanbul Desktop Session Recorder ...intall it 

that should do the job ...

but i have to warn u that graphics are not somethng well :lolflag:

---

### Post by wolfyking2 on 2009-04-04
> **Eazy© said:**
> I tried different hotkeys but I cant get this to work. The game I use is UT2004 and I think ut2004 keeps all keys for it selfe. I tried to record glxgears but that dont work either. Perhaps I have to give up on this :/

this might be off topic, but Eazy, is your penguin holding the lightning gun from UT2004? :p

---

### Post by LoloftheRings on 2009-04-05
I'm using gtk-recordmydesktop for screen capturing, it's in the ubuntu repos.

---

### Post by zerin on 2010-08-13
Yeah i just used the GTK Screen Recorder from the Repository, and it seems to work fine recording my Live For Speed replays, now i can make movies! but frame-rate does drop like 10 FPS. so bummer, but an ok program and simple to use with that new front-end. I can't record sound yet well, and some of my games go dark when recording, so i still have yet to mess with the settings or something.

---

### Post by Åtta on 2010-08-13
Some guy in the comments over at OMG! Ubuntu! recommended using ffmpeg to record both audio and video.

Here's an example:
```
ffmpeg -f alsa -ac 2 -i pulse -f x11grab -r 25 -s 800x600 -i :0.0+321,172 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 Desktop/intro.mkv
```

The thing you're going to want to change is -s WIDTHxHEIGHT -i :0.0+X_OFFSET,Y_OFFSET

If you're going to record the entire screen, just replace WIDTH and HEIGHT with your screen resolution, and set X_OFFSET and Y_OFFSET to 0. 

If you want to record just one window, use xwininfo and click on the window. Then check the part that says -geometry. The first two numbers are the width and height, and the second numbers are the x and y offsets.

---

### Post by AlmightyMokona on 2012-03-02
hey i don't know if any of the people in this topic are still looking for something, but you might want to try GLC
[http://www.dedoimedo.com/computers/glc.html](http://www.dedoimedo.com/computers/glc.html)

---

