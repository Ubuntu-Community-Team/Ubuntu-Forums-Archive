---
title: "Maybe simple question? For installing games. ."
date: 2012-03-09
forum: Gaming &amp; Leisure
---

### Post by BJCV86 on 2012-03-09
[SOLVED]'ish. :P

Are there professional linux people here?
I'm so confused I could just give up. Like anything else I do. lawls. . . 

Ok. So I don't want to install something from the Software Center because that software for a particular package is out of date.

I have to compile a bunch of things. Is there a step by step process to compile a software. Ummm. Ok. I want flightgear 2.4. It won't install on Ubuntu 11.10. And only a lower version of flighgear will install from the software center. I download and follow directions, but I always seem to have an inactive response from the .run things.

Question is, how do I do that? how do I put all this "STUFF" and make it go?


[LIST]
[*]Download the latest FlightGear source code release:[[Mirror 1]]("ftp://ftp.linux.kiev.ua/pub/mirrors/ftp.flightgear.org/flightgear/Source/") [[Mirror 2]]("ftp://mirrors.ibiblio.org/pub/mirrors/flightgear/ftp/Source/") [[Mirror 3]]("ftp://flightgear.wo0t.de/Source/")
[*]Download the latest [SimGear source code release]("http://mirrors.ibiblio.org/pub/mirrors/simgear/ftp/Source/"). (Required)  Note: the SimGear version number **must** match FlightGear version number.
[*]Download the latest base package release (530Mb). (Includes Textures, models, data, aircraft, sample scenery, and config files):[[Mirror 1]]("ftp://ftp.linux.kiev.ua/pub/mirrors/ftp.flightgear.org/flightgear/Shared/") [[Mirror 2]]("http://mirrors.ibiblio.org/pub/mirrors/flightgear/ftp/Shared/") [[Mirror 3]]("ftp://ftp.kingmont.com/flightsims/flightgear/Shared/")
[*]Prerequisite: [Open Scene Graph]("http://www.openscenegraph.org/") -  An open source scene graph management and graphics effects library.   OSG version 3.0.1 or newer is recommended for best results.
[*]Prerequisite: [Boost]("http://www.boost.org/") -  free peer-reviewed portable C++ source libraries. Boost v1.44 or newer  is recommended. (A suitable version is included with many (most?) Linux  distributions.)
[*]Prerequisite: [Glut (FreeGlut)]("http://freeglut.sf.net/") - OpenGL Utility Toolkit (GLUT) library.
[*]Prerequisite: [OpenAL]("http://kcat.strangesoft.net/openal.html") -  We recommend OpenAl Soft 1.11.753 (or higher). Many current Linux  distributions now include OpenAL Soft so check and you may already have  this installed or available.
[*]Prerequisite: [plib]("http://plib.sourceforge.net/") - portability libraries and scene graph. You need plib-1.8.5 or newer to build FlightGear 2.4.0.
[*]Documentation is included with the base package.
[/LIST]
 [B]I just want to download and click go :( I NEED TO JUST CLICK I DON"T WANT TO BREAK ANYTHING :(


I didn't take computer  science. What is this shyt? [/B]o run the applications you need to set up the path to the  applications, and its recommend that you add these environmental  settings to you login setup such as autoexec.bat under Windows, or  .tcshrc, or .bashrc under Unix. The binaries paths to set up are:[INDENT]  Unix, tcsh: **setenv PATH {$PATH}:/usr/local/share/OpenSceneGraph/bin**

 [/INDENT]Unix, bash: **export PATH={$PATH}:/usr/local/share/OpenSceneGraph/bin**
Windows : **set PATH=Mypath;where\I\put\my\OpenSceneGraph\bin**
Windows Vista : **setx PATH "%PATH;c:\apps\OpenSceneGraph\bin"** (one-time command)

  Then set the OpenSceneGraph file path up, so that the examples can find the data:[INDENT]  Unix, tcsh: **setenv OSG_FILE_PATH /home/myaccount/MyData/OpenSceneGraph-Data**

 [/INDENT]Unix, bash: **export OSG_FILE_PATH=/home/myaccount/MyData/OpenSceneGraph-Data**
OSX, use the above expressions plus : **setenv DYLD_BIND_AT_LAUNCH**
Windows: **set OSG_FILE_PATH=where\I\put\my\OpenSceneGraph-Data**
Windows Vista : **setx OSG_FILE_PATH c:\apps\OpenSceneGraph-Data** (one-time command)

  Then to run a single application type in a console: I just want to run a cool game that isn't involved with shooting bullets.

---

### Post by mastablasta on 2012-03-10
how about you go to software center, search for flight gear and then install it? if it's not there then add the link to playdeb in software center sources and it will appear there.
[http://www.playdeb.net/updates/Ubuntu/11.10](http://www.playdeb.net/updates/Ubuntu/11.10)

also don't type to terminal as you can copy & paste to it.

edit: sorry i see they have theolder verison. no matter instead of playdeb xyou can use another PPA: . for example: [https://launchpad.net/ubuntu/+source/flightgear](https://launchpad.net/ubuntu/+source/flightgear)

---

### Post by TejasMChavan on 2012-03-10
[http://pkgs.org/ubuntu-11.10/getdeb-games-i386/flightgear_2.6.0-1~getdeb1_i386.deb.html](http://pkgs.org/ubuntu-11.10/getdeb-games-i386/flightgear_2.6.0-1~getdeb1_i386.deb.html)

Even I was looking for same and got to this link above.
Follow instructions here... They are pretty simple.

By the have you posted somewhere else too?? ;) :)

If you find difficult adding keys, click this link [http://archive.getdeb.net/install_deb/playdeb_0.3-1~getdeb1_all.deb](http://archive.getdeb.net/install_deb/playdeb_0.3-1~getdeb1_all.deb) and open it.
And then open terminal and type; sudo apt-get update
then; sudo apt-get install flightgear

Hope you find this easy.. ;)

---

### Post by oldrocker99 on 2012-03-10
All these posts are GOOD advice, and this is the kind of thing that makes this forum special. 

BJCV86, I know you're not a computer scientist, but learning how to add a PPA with sudo add-apt-repository can make your life a lot simpler, and updates will always give you the latest version.

---

### Post by BJCV86 on 2012-03-10
> **oldrocker99 said:**
> All these posts are GOOD advice, and this is the kind of thing that makes this forum special. 

BJCV86, I know you're not a computer scientist, but learning how to add a PPA with sudo add-apt-repository can make your life a lot simpler, and updates will always give you the latest version.


Ok I typed in the 
# wget -q -O- [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add -  thing. but nothing happened.

---

### Post by Paddy Landau on 2012-03-10
You must not type the "#" before the command, because that turns it into a comment (i.e. the computer will ignore it).

---

### Post by BJCV86 on 2012-03-10
[ATTACH]214062[/ATTACH]> **Paddy Landau said:**
> You must not type the "#" before the command, because that turns it into a comment (i.e. the computer will ignore it).


That confuses the eyes. WHY ON EARTH THEY PUT THE # THERE? OK LETS SEE IF IT GOES.

Ya no. Nothing. NOdda. I must have an I.Q lower than a fly.

So I do not have to download anything, but type this? 
wget -q -O- [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add -

---

### Post by Paddy Landau on 2012-03-10
> **BJCV86 said:**
> That confuses the eyes. WHY ON EARTH THEY PUT THE # THERE? OK LETS SEE IF IT GOES.
Please don't shout. It is there to distinguish between what *you* type and what the *computer* types. Most Linux systems use either the hash ("#") or the dollar sign ("$"). Ubuntu uses $ for a normal user, and # for root.

> **BJCV86 said:**
> Ya no. Nothing. NOdda. I must have an I.Q lower than a fly.
LOL, no, you're just learning. We all have gone through that learning curve. Personally, I prefer using the GUI rather than the command line.

Your wget worked fine (see the "OK" in your screen shot)?

Find your downloaded .deb file using Nautilus (your file browser). Double-click (or right-click and Open). It will open your Ubuntu Software Centre to install it for you.

> **BJCV86 said:**
>  So I do not have to download anything, but type this? 
wget -q -O- [http://archive.getdeb.net/getdeb-archive.key](http://archive.getdeb.net/getdeb-archive.key) | sudo apt-key add -
wget is a program that fetches a file from the Internet. The *pipe* ("|") means to not save the file, but send it to the next command. "apt-key add" then adds the key (a type of digital signature) to the package manager. Adding this signature means that the package manager (and therefore the Ubuntu Software Centre) will know that the deb file that you downloaded is valid and not a fraudulent one.

---

### Post by BJCV86 on 2012-03-10
> **Paddy Landau said:**
> Please don't shout. It is there to distinguish between what *you* type and what the *computer* types. Most Linux systems use either the hash ("#") or the dollar sign ("$"). Ubuntu uses $ for a normal user, and # for root.


LOL, no, you're just learning. We all have gone through that learning curve. Personally, I prefer using the GUI rather than the command line. What is the GUI? Graphical User Interface of some kind.

Your wget worked fine (see the "OK" in your screen shot)?

Find your downloaded .deb file using Nautilus (your file browser). Double-click (or right-click and Open). It will open your Ubuntu Software Centre to install it for you.


wget is a program that fetches a file from the Internet. The *pipe* ("|") means to not save the file, but send it to the next command. "apt-key add" then adds the key (a type of digital signature) to the package manager. Adding this signature means that the package manager (and therefore the Ubuntu Software Centre) will know that the deb file that you downloaded is valid and not a fraudulent one. I hit my head real hard from a bike accident few years ago. Sooooo w/e.

May we exchange brains for only a moment?  I searched files for Natutilus. Is that the thing when I click "Home"? The Window full of Files? Okay. This is where I am to get the .deb? What does .deb mean? How do I download the .deb?   ---   This is what I learnt so far. the | does not download but send it to the next command line. And not to put a # because of some reason. and $ means personal user?

---

### Post by BJCV86 on 2012-03-10
WHOAH SOMETHING NEW AND CHANGED! PROGRESS I THINK> YAY yes I can shout something MOVED! LLOLOL SCRATCH THAT. It went back to normal when I continued the terminal process. If I buy the CD, and install it from the CD they sell? WILL IT WORK? Or is My O.S a fake piece of ****.

in the software centre, it sais 2.6 available. but the GUI is a bit messy and i'm afraid 2.0 and 2.6 will install. But I am also still confused with the terminal

IT IS NOT ALLOWING ME ANYTHING. BUT TO say, oh sry, we cannot modify this because you are not the owner of your own computer.

---

### Post by BJCV86 on 2012-03-10
I'm just going to assume I will have to reinstall the O.S when I finally done screwing it up. k bai.

Does anyone know what it is I'm doing wrong?

---

### Post by BJCV86 on 2012-03-10
> **BJCV86 said:**
> I'm just going to assume I will have to reinstall the O.S when I finally done screwing it up. k bai.

Does anyone know what it is I'm doing wrong?
cvdf

---

### Post by Paddy Landau on 2012-03-10
> **BJCV86 said:**
> ... Natutilus. Is that the thing when I click "Home"? The Window full of Files?
Yes, you got it.

> **BJCV86 said:**
> in the software centre, it sais 2.6 available. but the GUI is a bit messy and i'm afraid 2.0 and 2.6 will install.
The package manager is quite "intelligent" and won't install two versions at the same time. It will automatically uninstall the old version and install the new version in its place.

However, your screen shows you that it cannot install because "Dependency is not satisfiable: simgear 2.6.0".

In other words, it cannot install Flightgear because it needs an updated version of simgear.

You found the deb file for Flightgear 2.6.0. Now, you have to find the deb file for simgear 2.6.0. Once you have it, you can install it, and then try again with Flightgear.

> **BJCV86 said:**
> But I am also still confused with the terminal
No problem. Stick with the GUI for now if you can. I usually do because I prefer it.

---

### Post by BJCV86 on 2012-03-10
> **Paddy Landau said:**
> Yes, you got it.


The package manager is quite "intelligent" and won't install two versions at the same time. It will automatically uninstall the old version and install the new version in its place.

However, your screen shows you that it cannot install because "Dependency is not satisfiable: simgear 2.6.0".

In other words, it cannot install Flightgear because it needs an updated version of simgear.

You found the deb file for Flightgear 2.6.0. Now, you have to find the deb file for simgear 2.6.0. Once you have it, you can install it, and then try again with Flightgear.


No problem. Stick with the GUI for now if you can. I usually do because I prefer it.

OK I got the 2.6 screen back with not satisfiable dependancy, now I have this screen ok i'll push install I hit my head rly hard into a concrete slab when I rode my bike once fall I was going about 35MPH no helmet so w/e. So, thank you for the patients.

---

### Post by BJCV86 on 2012-03-10
> **BJCV86 said:**
> OK I got the 2.6 screen back with not satisfiable dependancy, now I have this screen ok i'll push install I hit my head rly hard into a concrete slab when I rode my bike once fall I was going about 35MPH no helmet so w/e. So, thank you for the patients.


Ok. Now what. Still not satisfied. Interesting how a computer program tells me it's not satisfied when rly. I am not satisfied lol maybe if we work together, the computer and I, it we'll be both satisfied. I like ubuntu cuz it saves ur snapshot right away. Sim gear installed. It said it was 4000kb, but in the end it install 25 MB worth if files. Is this ok Paddy you genius you. lol

---

### Post by Paddy Landau on 2012-03-10
> **BJCV86 said:**
> Is this ok Paddy you genius you. lol
LOL, not a genius, just persistent, and very lucky when it works.

So, it's the same thing here: you need the updated fgfs-base. I presume you get that from the same website?

When you install directly from the Ubuntu Software Centre, all dependencies are available for immediate download. Your problems arise because you are trying to download something not available in the Ubuntu Software Centre, so it cannot find the dependencies.

If you can find fgfs-base (version 2.6.0 or greater), install it and try again. Keep going until it no longer complains about dependencies and just installs.

Somewhere, the website may tell you everything you need to download (it should, really, but that doesn't mean it does). If you can find that, you can download the lot and install it in one go.

---

### Post by BJCV86 on 2012-03-10
Ok so it had installed. But when I try and activate the game it doesn't do anything. And the icon of the game is blank. Thanks for the most part on getting the files on it.

---

### Post by Paddy Landau on 2012-03-11
You need to catch the errors. First, find the command line that needs to run:

[LIST=1]
[*]Open Main Menu. If it doesn't exist on your system, install [alacarte]("apt:alacarte") and try again.
[*]Find your game (it should be in the Games section).
[*]Select it, then press "Properties".
[*]Note the full command in "Command" (you can highlight, right-click and Copy to prevent typing mistakes).
[*]Close (without making any changes) the Properties and Main Menu.
[/LIST]
Now, run the command in a terminal to catch the errors.

[LIST=1]
[*]Open a Terminal.
[*]Type the command from step 4 above (you can right-click and Paste to prevent typing errors).
[*]Press Enter.
[*]When the command has finished running, copy the messages and post them here (between [FONT=Lucida Console][noparse]```
[/noparse][/FONT] and [FONT=Lucida Console][noparse]
```[/noparse][/FONT] please).
[/LIST]

---

### Post by TejasMChavan on 2012-03-11
Loading of game takes time you maybe left with blank window with black screen.
And icon, it comes with "question mark" in grey colour.

Also,
sudo apt-add-repository ppa:diesch/testing
sudo apt-get update
sudo apt-get install classicmenu-indicator

Type this in terminal
you must go through this before you proceed in 11.10 with alacarte I suppose.
Just for info :) :D

---

