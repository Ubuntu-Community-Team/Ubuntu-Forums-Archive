---
title: "Quake 1 anyone? (quick easy install script)"
date: 2012-08-04
forum: Gaming &amp; Leisure
---

### Post by homerhomer on 2012-08-04
I noticed that Quakecon is going on. 

Here's a quick little quake install script. 

This will;

Install ezQuake
Add the shareware needed from the original quake demo
Create a link in dash. so you can search and drag the quake icon on your desktop or unity taskbar


Run once to install 
Run again to uninstall 

enjoy  :D

---

### Post by honeybear on 2012-08-04
> **homerhomer said:**
> I noticed that Quakecon is going on. 

Here's a quick little quake install script. 

This will;

Install ezQuake
Add the shareware needed from the original quake demo
Create a link in dash. so you can search and drag the quake icon on your desktop or unity taskbar


Run once to install 
Run again to uninstall 

enjoy  :D



we should really see more installers like that in this ubuntu forum !!!


it is a pure sh installer that really works


Could you add a dialog with blue color to be even nicer?

fullscreen is not working.

Thank you very much. It is brillant.

---

### Post by DarkAmbient on 2012-08-04
Sweet, thanks a bunch! works out of the box. Quake is one of my favourite games of all time.

I was considering writing a short script that could download and autostart your script in xterm or gnome-terminal. (Making life even easier for people who's unfamiliar with running things from terminal) But wget didn't like downloading from "in-absolute" / "php-get" urls. :( (or what you call something like url.com/?file=123 instead of url.com/file.ext)

---

### Post by Jack Of Clubs on 2012-08-05
I ran this from the terminal in Xubuntu and everything seemed to install OK, but when I run ezQuake the screen changes my resolution, goes black, then dumps me back to the desktop.  Any idea what I need to do?

---

### Post by DarkAmbient on 2012-08-05
> **Jack Of Clubs said:**
> I ran this from the terminal in Xubuntu and everything seemed to install OK, but when I run ezQuake the screen changes my resolution, goes black, then dumps me back to the desktop.  Any idea what I need to do?

Quake has 640x480 in res. as default, might be to low for your monitor?

Try to play around with startup commands.. create a empty textfile on your desktop and paste this into that file:

```
cd ~/ezquake/
./ezquake-gl.glx -width 1024 -height 768 -window -notriplebuf

```

Rightclick the textfile and click the second tab, then check the file as executable, then you can just doubleclick it and pick Run.

Replace the commands with what you see fit.. Those commands sets your in-game resolution, makes the game in windowed mode and disables triplebuffering. Just picked a few one, you probably want triplebuffering activeted so remove that one if so.. You got a full list over available commands here:

[http://ezquake.sourceforge.net/docs/?command-line](http://ezquake.sourceforge.net/docs/?command-line)

*Since the removal of "starters" in Ubuntu I know as of now no easier way than writing a short bashscript to execute application in a your desired way. Fill me in if someone else know please. :)

---

### Post by Jack Of Clubs on 2012-08-05
Thanks for the pointer, DA.  I tried running this and it least gave me some output that might indicate the problem:

```
joc@metalman:~/ezquake$ ./ezquake-gl.glx -width 1024 -height 768 -window -notriplebuf
Received signal 11, exiting...
[xcb] Unknown request in queue while dequeuing
[xcb] Most likely this is a multi-threaded client and XInitThreads has not been called
[xcb] Aborting, sorry about that.
ezquake-gl.glx: ../../src/xcb_io.c:178: dequeue_pending_request: Assertion `!xcb_xlib_unknown_req_in_deq' failed.
DOUBLE SIGNAL FAULT: Received signal 6, exiting...

```

I then tried to run it as sudo, and it got me in as far as the level select hallway, and then...

```
joc@metalman:~/ezquake$ sudo ./ezquake-gl.glx -width 1024 -height 768 -window -notriplebuf
[sudo] password for joc: 
ezquake-gl.glx: ../../intel/intel_bufmgr_gem.c:1579: do_bo_emit_reloc: Assertion `offset <= bo->size - 4' failed.
Received signal 6, exiting...
```

I tried running it again with normal permissions and it one again let me in, then crashed in the level select zone.  Any thoughts?

---

### Post by Sarys on 2012-08-06
Um....May someone tell me what is this? Free Quoke 1? And since I barely know how to use Ubuntu so more information would not hurt, right?

---

### Post by DarkAmbient on 2012-08-06
> **Sarys said:**
> Um....May someone tell me what is this? Free Quoke 1? And since I barely know how to use Ubuntu so more information would not hurt, right?

Download the quakeinstaller.sh that homehomer attached in the first post to your homefolder. open a terminal (ctrl+t)  and type sh quakeinstaller.sh

If you care about where you install it (Installs to your homefolder as default) Open quakeinstaller.sh in a texteditor and change line 7 to desired path first.. Note that the folder gotta exist else it wont install. For example, I changed mine to: ```
INSTALLDIR=~/Spel/ezquake
```
So in my case I needed to create the folder "Spel" in my homefolder first.

> Jack Of Clubs

That is beyond my knowledge I'm sorry. 

Was gonna suggest you try the '-nomultithreadedgl' -command while running Quake.. but apparently it's OSX only.  :/ As it mentions multithreading in the error-output:

> Received signal 11, exiting...
[xcb] Unknown request in queue while dequeuing
[xcb] Most likely this is a multi-threaded client and XInitThreads has not been called
[xcb] Aborting, sorry about that.
ezquake-gl.glx: ../../src/xcb_io.c:178: dequeue_pending_request: Assertion `!xcb_xlib_unknown_req_in_deq' failed.

Prhaps someone else know more about this? Probably won't help but this is manpage for xInitThreads --> [http://manpages.ubuntu.com/manpages/precise/en/man3/XInitThreads.3.html]("http://manpages.ubuntu.com/manpages/precise/en/man3/XInitThreads.3.html")

---

### Post by Jack Of Clubs on 2012-08-06
No prob, DA -- thanks for the assistance.  I'll do some poking around to see if I can find a solution.

Also, thanks much to homerhomer for the install script!

---

### Post by homerhomer on 2012-08-06
This looks like it might be related to your issue. 

Seems a little confusing. When in doubt blame the video driver. 

[https://bugs.launchpad.net/ubuntu/+source/linuxdcpp/+bug/836117](https://bugs.launchpad.net/ubuntu/+source/linuxdcpp/+bug/836117)

---

### Post by leilei on 2012-08-08
It should be called the ezQuake install script rather, since ezQuake is highly unrepresentative of Quake as it's a Quake**world** engine with many default features designed for **competitive** players only (hence "ez", since it intends to make the multiplayer game **easier** for them by picmipping, brightskinning (turning players into solid glowing colors), level brightening, etc). 


It's a totally different animal.

---

### Post by vaporwear on 2012-08-29
Just download [nQuake]("http://nquake.com/"), it seems to do the same thing but better.

> **leilei said:**
> It should be called the ezQuake install script rather, since ezQuake is highly unrepresentative of Quake as it's a Quake**world** engine with many default features designed for **competitive** players only (hence "ez", since it intends to make the multiplayer game **easier** for them by picmipping, brightskinning (turning players into solid glowing colors), level brightening, etc). 


Well, yeah sure! But it's still the best way to play Quake.

[LIST=1]
[*]It has great single player support
[*]It works on Linux
[*]Have fun playing NQ multiplayer with yourself!
[/LIST]
[nQuake]("http://nquake.com/") makes everything easy peasy. The pak1 is just a search engine away if you don't want to find your Quake CD.

---

### Post by walker195 on 2012-08-31
> **homerhomer said:**
> I noticed that Quakecon is going on. 

Here's a quick little quake install script. 

This will;

Install ezQuake
Add the shareware needed from the original quake demo
Create a link in dash. so you can search and drag the quake icon on your desktop or unity taskbar


Run once to install 
Run again to uninstall 

enjoy  :D

its people like you who make me proud to be part of the ubuntu community

---

### Post by contributor on 2012-09-13
I love to play Quake whenever I get time. And thank you homerhomer for sharing it. I have downloaded it and it is working properly without giving any pain.

---

