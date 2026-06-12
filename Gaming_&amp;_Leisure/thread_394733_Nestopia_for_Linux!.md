---
title: "Nestopia for Linux!"
date: 2007-03-27
forum: Gaming &amp; Leisure
---

### Post by bebop_tango on 2007-03-27
The newest GUI versions have been released. You can get the latest patch [here]("http://rbelmont.mameworld.info/nst136_lnx_preview_4.zip").

You'll also need the [main source]("http://nestopia.sourceforge.net/") to compile.

Now we won't hear any complaints about "there's no good NES emulator for GNU/Linux outta here..."

;)

---

### Post by MaindotC on 2007-11-14
The sourceforge page links to another page to download the source who's download link links back to sourceforge.

---

### Post by braveerudite on 2007-11-28
Would some please compile this to work on Ubuntu 7.10 - the Gutsy Gibbon (64 bit edition)

---

### Post by dfreer on 2007-11-28
EDIT: Oh, duh, this thread is from March. No wonder I was confused.

@braveerudite - I can compile it for you, I gotta reboot though.

---

### Post by braveerudite on 2007-11-28
> **dfreer said:**
> EDIT: Oh, duh, this thread is from March. No wonder I was confused.

@braveerudite - I can compile it for you, I gotta reboot though.

That would be very nice of you.  Thank you so much , I'll check back tomorrow.

---

### Post by dfreer on 2007-11-29
Really though, all you needed to do to compile this was to grab the two source code packages (one's the official source code from nestopia's site, and the other is linux specific code from here: [http://rbelmont.mameworld.info/?page_id=200](http://rbelmont.mameworld.info/?page_id=200) ). Then you extract the two packages into the same new folder, open up a terminal, change to that new folder and type "make". It'll create a executable called "nst" in that new folder.

[http://www.dfreer.org:8080/dfreer/nestopia/nestopia_1.37.tar.gz](http://www.dfreer.org:8080/dfreer/nestopia/nestopia_1.37.tar.gz)

That's what I've done here, so if you just download the above file from me, all you will need to do is:
(1) uncompress the file
(2) Create the folder ~/.nestopia/
(3) move the files called "nstcontrols" and "NstDatabase.dat" into the ~/.nestopia/ folder
(4) Run nst!

I'm also mirroring the Nestopia source files and Linux source overlay on my site:
[http://www.dfreer.org:8080/dfreer/nestopia/nestopia_1.37_src.zip](http://www.dfreer.org:8080/dfreer/nestopia/nestopia_1.37_src.zip)
[http://www.dfreer.org:8080/dfreer/nestopia/nestopia_1.37-0.5_linuxsrc.zip](http://www.dfreer.org:8080/dfreer/nestopia/nestopia_1.37-0.5_linuxsrc.zip)

---

### Post by braveerudite on 2007-11-29
> **dfreer said:**
> Really though, all you needed to do to compile this was to grab the two source code packages (one's the official source code from nestopia's site, and the other is linux specific code from here: [http://rbelmont.mameworld.info/?page_id=200](http://rbelmont.mameworld.info/?page_id=200) ). Then you extract the two packages into the same new folder, open up a terminal, change to that new folder and type "make". It'll create a executable called "nst" in that new folder.

[http://www.dfreer.org/dfreer/nestopia/nestopia_1.37.tar.gz](http://www.dfreer.org/dfreer/nestopia/nestopia_1.37.tar.gz)

That's what I've done here, so if you just download the above file from me, all you will need to do is:
(1) uncompress the file
(2) Create the folder ~/.nestopia/
(3) move the files called "nstcontrols" and "NstDatabase.dat" into the ~/.nestopia/ folder
(4) Run nst!

I'm also mirroring the Nestopia source files and Linux source overlay on my site:
[http://www.dfreer.org/dfreer/nestopia/nestopia_1.37_src.zip](http://www.dfreer.org/dfreer/nestopia/nestopia_1.37_src.zip)
[http://www.dfreer.org/dfreer/nestopia/nestopia_1.37-0.5_linuxsrc.zip](http://www.dfreer.org/dfreer/nestopia/nestopia_1.37-0.5_linuxsrc.zip)

Thank you but all that sounds to complicated for me at this point.  Why not just release a .deb file? Thank you for your time.

---

### Post by dfreer on 2007-11-29
Here, I can give you **step by step instructions**, literally just open up the terminal (Accessories > Terminal), and copy + paste the following commands one at a time.
```
cd ~/
wget -c http://www.dfreer.org/dfreer/nestopia/nestopia_1.37.tar.gz
tar xvf nestopia_1.37.tar.gz
cd nestopia/
mkdir ~/.nestopia
cp nstcontrols ~/.nestopia/
cp NstDatabase.dat ~/.nestopia/
./nst

```

If that works, you should be able to launch nestopia by double-clicking the **nst** file in your home folder, in the nestopia directory.





I might be willing to create a .deb in the future, but there's really no point right now. Mainly, because it seems like there is no way to use an USB controller and map the keys. There is the ~/.nestopia/nstcontrols file, but AFAIK there's no way to translate the gamepad key presses into NES buttons. Here's the nstcontrols file:
```
;
; NEStopia Linux controls file
;
; First column cannot be changed or you'll break the emulator
; Second column is the key for the first column, or one of these special names:
;
; _ENTER, _LCTRL, _RCTRL, _LALT, _RALT, _SPACE, _LSHIFT, _RSHIFT, _TAB
; _UP, _DOWN, _LEFT, _RIGHT, _KPENTER, _KP0, _KP1, _KP2, _KP3, _KP4, _KP5, _KP6,
; _KP7, _KP8, _KP9, _KPDOT, _KPSLASH, _KPSTAR, _KPMINUS, _KPPLUS (use __ to bind the actual _)
;
; Third column maps joypads:
; _JxAyPLUS = joystick #x axis #y positive direction
; _JxAyMINUS = joystick #x axis #y negative direction
; _JxBy = joystick #x button #y pressed
;
; Some keys are special:
; ESC always exits
; ALT-ENTER always toggles screen modes
;

; player 1
; default joypad values are for a PlayStation 2 controller via an EMS USB adaptor
;
P1UP            _UP             _J0A1MINUS
P1DN            _DOWN           _J0A1PLUS
P1LT            _LEFT           _J0A0MINUS
P1RT            _RIGHT          _J0A0PLUS
P1A             z               _J0B2
P1B             x               _J0B3
P1START         _ENTER          _J0B9
P1SELECT        _SPACE          _J0B8

; player 2
P2UP    _KP8    _J1A1MINUS
P2DN    _KP2    _J1A1PLUS
P2LT    _KP4    _J1A0MINUS
P2RT    _KP6    _J1A0PLUS
P2A     _KPSLASH        _J1B2
P2B     _KPSTAR _J1B3
P2START _KPENTER        _J1B9
P2SELECT        _KPPLUS _J1B8

; end of file

```

As for the above instructions, it's really simple. Creating a .deb won't help anyways, because I can't create the folder in your home directory anyways without a bash script of some sort.

---

### Post by MaindotC on 2007-12-02
Hi, dfreer, and thank you so much for posting the source code and instructions for installation.  When I try to execute the nst, I get a "cannot execute binary file".  From googling I can see that this is a pretty common error, but I'd like to see if you can figure out what would cause this specifically related to Nestopia.  Any ideas?  Thanks again for your time!

---

### Post by dfreer on 2007-12-03
Hmmm... not sure strAlan. Did you compile the program yourself, or did you use the binary I compiled for braveerudite? It's probably best to compile the program yourself if you are having problems with it not executing.

Beyond that, I'm not entire sure what the problem would be, since I didn't get the error myself :( . Did you make sure the file is executable (permissions set to 755)? Also, I see you already posted an error message, but if you didn't try launching nst from the terminal, do so now because it might give you some more error information (I'm not sure whether your error came from the GUI or from terminal).

---

### Post by MaindotC on 2007-12-04
Hi, dfreer.  I do have 777 permissions on the nst file.  I followed your instructions step by step (cutting & pasting into the terminal).  Here's the output: ```
 root@mamour-laptop:~/nestopia# ./nst
bash: ./nst: cannot execute binary file 
```

I tried running it as root, my user account, and sudo my user account.  From googling, I see this is a pretty common error - it's just difficult to pinpoint where to attack the problem.

Also, you listed the rbelmont link as a place to get the nestopia source code, but as I pointed out earlier: this site's download url links back to the nestopia sourceforge site, which links back to rebelmont, and back to sourceforge, etc.

---

### Post by dfreer on 2007-12-04
> **strAlan said:**
> Also, you listed the rbelmont link as a place to get the nestopia source code, but as I pointed out earlier: this site's download url links back to the nestopia sourceforge site, which links back to rebelmont, and back to sourceforge, etc.

Lol, I think I see the problem. Alright, on the rbelmont.mameworld.info site, all you are downloading is the [PR #5 Linux overlay source]("http://rbelmont.mameworld.info/nst137_lnx_preview_5.zip"). You still need to download the actual source code for the project, on rebelmont's site, the [1.37 Source Code]("http://nestopia.sourceforge.net/") link takes you to the nestopia sourceforge homepage. From there, if you click on the **Downloads** tab, you'll see the link to the [Nestopia v1.37 Source Code]("http://prdownloads.sourceforge.net/nestopia/Nestopia137src.zip?download") **underneath the *Windows* section**.

The problem you were having, I suspect, is that you clicked on the Nestopia Linux link underneath the Linux section, which takes you to the rbelmont site where the linux source code overlay resides. You need to download the Windows Source Code, and then extract the Linux Source Code Overlay in the same folder.


As for your error, I made that binary on my 64-bit machine for braveerudite, so if you following the instructions I gave in: [http://ubuntuforums.org/showpost.php?p=3862259&postcount=8](http://ubuntuforums.org/showpost.php?p=3862259&postcount=8)
It probably won't work for you in 32-bit.

So, **brand new step-by-step instructions**, for compiling nestopia directly from source! Deleting the old stuff first:
```
rm -Rv ~/nestopia
rm -Rv ~/.nestopia
```

Downloading the Windows source code.
```
sudo apt-get install build-essential zip unzip
cd ~/
wget -c http://superb-east.dl.sourceforge.net/sourceforge/nestopia/Nestopia137src.zip
unzip Nestopia137src.zip -d ~/nestopia
```

Unfortunately, you can't wget the linux source code :roll: . So you need to actually click on [the link to the linux source code overlay]("http://rbelmont.mameworld.info/nst137_lnx_preview_5.zip") on rbelmont's site and save the *nst137_lns_preview_5.zip* file to your **Desktop**. Moving on:

```
unzip ~/Desktop/nst137_lnx_preview_5.zip -d ~/nestopia
cd ~/nestopia/
make
mkdir ~/.nestopia
cp nstcontrols ~/.nestopia/
cp NstDatabase.dat ~/.nestopia/
./nst
```

If there is a problem, try this command and post output:
```
ldd ./nst
```

---

### Post by MaindotC on 2007-12-05
Just wanted to post a quickie and thank you for the time you spent to construct the previous post.  I haven't read it all but I will when I get a chance.  Thanks freer.

---

### Post by MaindotC on 2007-12-25
Hi, dfreer.  Sorry I've been afk but it was final exam season :(  Anyway, I ended up reinstalling 7.04 and I re-downloaded and followed your directions again.  I also tried using the additional instructions you posted, but still cannot execute binary file :(  

I followed the NEW directions but what confuses me is that you instruct me to download the windows source.  Is that correct?  I know C and C++ are C and C++ but I just want to verify your directions.

Everything was fine until I typed "make" and then I received a slew of errors - seem to be a bunch of undefined variables.  The top of the output was that I was missing gtk2.0, so I apt-get'd gtk+2.0-dev and I made some progress.  Now, when I type make, I get the following shorter list of errors:

```
Compiling source/linux/main.cpp...
Compiling source/linux/oss.cpp...
source/linux/oss.cpp:16:28: error: alsa/asoundlib.h: No such file or directory

```

Can you advise me of what I should do next?  Perhaps there's a log or output I can post that will give you some clues?  Thank you again for all that you do.

Edit:  Bah, I really wish I would wait on posting thist stuff.  No sooner than I posted did I google and I checked the repos.  I apt-get'd libasound2-dev.  Did an updatedb and typed make.  It took about 4 minutes to compile, but IT WORKED!  I haven't tested it yet - like trying to load roms and such - but I've made this progress and wanted to let you know.  So, for the future, get gtk2.0-dev and libasound2-dev :)  I'll keep you posted on how it works.

---

### Post by MaindotC on 2007-12-25
Hi, dfreer.  It works fine, but there's no netplay.  Isn't it supposed to have netplay?

---

### Post by dfreer on 2007-12-25
> **strAlan said:**
> Hi, dfreer.  It works fine, but there's no netplay.  Isn't it supposed to have netplay?

No idea :( I don't really ever use netplay in my emulators, so it's something I don't tend to check. 

Yes, basically the idea is this: You download the Windows Source Code, and then you unpack the linux source code overlay on top of the windows source code. This will create new linux-specific files, and possibly update existing source code files with code so it can be compiled correctly in linux.

---

### Post by MaindotC on 2007-12-25
That whole overlay thing is way above my head.  I'm learning C but am nowhere near that level yet.

I'm sorry to put you through all this and ask your help but the fact that it has NO netplay kind of defeats the whole purpose of installing nestopia instead of just installing fceu from the repos.  Sorry again - but this is a huge disappointment.

Let me ask you this - why would you NOT want netplay?  Do you not find any fun in playing games with other people?  I've read on the mamedev FAQ that netplay "encourages the wrong type of user".  What does that mean?

---

### Post by dfreer on 2007-12-26
> **strAlan said:**
> That whole overlay thing is way above my head.  I'm learning C but am nowhere near that level yet.

It really has nothing to do with C, or any other programming language. All you are doing is extracting new files into the source code directory that let's you compile it in linux. Think of it this way: 

Let's say you made this awesome toy. It's a bit complicated and comes in several pieces, so in order to show people how to use it, you made a little guide in English that describes how to put it together and how to play with it.

Now, let's say your toy is so awesome, that people in japan want to play with it. But they don't know how to play with it. So instead of creating an English version of your toy with one English instruction manual, and a Japanese version of your toy with one Japanese instruction manual, you decide to just create **one** manual that has *both english and japanese instructions* in it.

The original source code for Nestopia was probably designed only for windows, and linux came as an afterthought. And so when they decided to port their game to linux, instead of creating a separate set of source code just for linux (or making the original code compatible with both OS's :( ), they just made a linux overlay package, and left the linux users to drop the new code on top of the existing windows code. Hope that clears things up :lol:


> **strAlan said:**
> I'm sorry to put you through all this and ask your help but the fact that it has NO netplay kind of defeats the whole purpose of installing nestopia instead of just installing fceu from the repos.  Sorry again - but this is a huge disappointment.

Not really a problem, I was more disappointed that there's no clear way for me to map my USB gamepad's. I happen to like FCEU and GFCEU myself.

> **strAlan said:**
> Let me ask you this - why would you NOT want netplay?  Do you not find any fun in playing games with other people?

I like playing with people on *the same machine*, in the same house. I hook my laptop up to my TV and we all sit down and play it. There's nothing wrong with netplay, I just don't need it myself. 

The only reason why I would NOT want netplay, would be if it interfered with the development of the emulator itself, i.e. if the developer's spent all their time getting netplay working when the emulator itself can only play 2 games correctly. Why bother with extra features when there is other work to be done?
  
> **strAlan said:**
> I've read on the mamedev FAQ that netplay "encourages the wrong type of user".  What does that mean?

No idea, that's a good question to ask the mame developers :p

---

### Post by MaindotC on 2007-12-28
Thank you again, dfreer :)  I agree with your explanation of the fact that it's not about writing code and I like your analogy, I just figured it would help if I had a deeper understanding of the source code.  In any event, I learned something :)

---

### Post by Gammell on 2008-02-15
> **dfreer said:**
> I was more disappointed that there's no clear way for me to map my USB gamepad's.
[http://www.mythtv.org/wiki/index.php/MythGameEmulationSetup#NEStopia](http://www.mythtv.org/wiki/index.php/MythGameEmulationSetup#NEStopia)

I'm not sure if the patch works or not, I'm in the process of trying it myself.

---

### Post by Gammell on 2008-02-15
It works a treat for me with a PS2 controller through a USB adapter... gennstcontrols doesn't give you the option to map the rewind button, but you can just edit the file directly, borrowing the syntax... if you don't know your joystick's buttons, give *jstest* (or similar) a try.

---

### Post by memps001 on 2008-02-20
I've searched through message boards for hours now, and have finally decided that I'm going to need specific help compiling Nestopia.  (Part of the issue may be my one total week of experience with Ubuntu/Linux).

I'm able to start compiling the Nestopia source w/ Linux overlay, but during the process a number of files come up as "not found".  Below is my Terminal process:

```
:~$ cd Desktop
:~/Desktop$ cd Nestopia137src
:~/Desktop/Nestopia137src$ make
Creating output directory objs
Creating output directory objs/core
Creating output directory objs/core/api
Creating output directory objs/core/board
Creating output directory objs/core/input
Creating output directory objs/core/mapper
Creating output directory objs/core/vssystem
Creating output directory objs/linux
Creating output directory objs/linux/7zip
Creating output directory objs/linux/unzip
Creating output directory objs/nes_ntsc
Compiling source/linux/main.cpp...
/bin/sh: sdl-config: not found
Compiling source/linux/oss.cpp...
/bin/sh: sdl-config: not found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
gcc: error trying to exec 'cc1plus': execvp: No such file or directory
gcc: error trying to exec 'cc1plus': execvp: No such file or directory
make: *** [objs/linux/oss.o] Error 1
make: *** Waiting for unfinished jobs....
make: *** [objs/linux/main.o] Error 1
```

I'm at a complete loss, and any help would be greatly appreciated!

---

### Post by Gammell on 2008-02-20
> **memps001 said:**
> Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found


I think that means you're missing the development package of gtk, I believe it's mentioned somewhere else in this thread... but no worries, just install:
gtk+2.0-dev
from apt-get/synaptic/wherever. Make a note of which other -dev packages it pulls in, since once you're done compiling you can remove them.

Alternatively, you might want to take a look at [mednafen](http://mednafen.sourceforge.net/). It's in the repositories (install with apt-get/synaptic/whatever) and does NES quite well. I prefer it.

---

### Post by disturbedite on 2008-02-20
nestopia is still better than mednafen's nes emulation imo.

---

### Post by Gammell on 2008-02-20
> **disturbedite said:**
> nestopia is still better than mednafen's nes emulation imo.
To be honest, other than the GUIs I see little emulation difference... But I haven't used either one that much... Mednafen does have the benefits of being easiest to install for a new user though. If you do try and install NEStopia, grab that patch from mythtv.org that lets you use USB controllers...

---

### Post by BigSilly on 2008-03-09
Just wanted to post up and say thank you very much to Dfreer for his excellent guide to installing this emulator. It's doubly brilliant as I was just about to give up on it. I was trying to 'make install' it, and it wasn't working, but thanks to your detailed guide I've managed to successfully utilise this emulator. It even works with my USB joypad! I have to say I do think it's the best NES emu I've played, so I'm going to have to bookmark your guide for when I want to install it in Hardy.

I'm not experienced at all when it comes to compiling from source, and even after reading the instructions in the program files it made nothing clear As always, the devil's in the details, and your guide provided the details.

Thanks very much again for the Linux lesson. :)

---

### Post by dfreer on 2008-03-09
> **BigSilly said:**
> Just wanted to post up and say thank you very much to Dfreer for his excellent guide to installing this emulator. It's doubly brilliant as I was just about to give up on it. I was trying to 'make install' it, and it wasn't working, but thanks to your detailed guide I've managed to successfully utilise this emulator. It even works with my USB joypad! I have to say I do think it's the best NES emu I've played, so I'm going to have to bookmark your guide for when I want to install it in Hardy.

I'm not experienced at all when it comes to compiling from source, and even after reading the instructions in the program files it made nothing clear As always, the devil's in the details, and your guide provided the details.

Thanks very much again for the Linux lesson. :)

You're welcome! :D

---

### Post by disturbedite on 2008-03-09
i just noticed that R. Belmont posted an update on the Nestopia forum (that i belong to) saying that a new version is on the way.  the only detail he gave as to what is new is that it will have a built in (command line) key configurator (for lack a better term).  no more gennstcontrols.

---

### Post by BigSilly on 2008-03-09
> **dfreer said:**
> You're welcome! :D

Thanks for posting up. I've been able to add my thanks to your list now. I couldn't do it before, I think because your posts were too old or something, but the "Thanks" button wasn't available. 

I know I'm a bit gushy, but do you know how difficult it can be to find a guide that's detailed enough to make things clear? Once I'd followed your steps, I could see clearly what was happening, and once you see the logic of what you're doing it helps you learn how it all works. I knew I had to get the requisite libraries, which I did, but the rest of it flummoxed me completely. I think it's the first thing I've ever successfully compiled from source! 

Magic!

---

### Post by dfreer on 2008-03-20
@BigSilly - You're very welcome!

I have attached the linux source overlay for anyone having issues with reaching the rbelmont site.

---

### Post by andy_blah on 2008-04-05
What are the controls? I am unable to control the emulator.

---

### Post by disturbedite on 2008-04-05
@ dfreer
i haven't had any problems reaching R Belmont's site ever.

@ andy_blah
to configure the controls for use with joypad, keyboard, or whatever else is supported, one has to run the gennstcontrols file from command line.  then if one wants to make further changes, he/she can edit the config file.

---

### Post by dfreer on 2008-04-05
> **disturbedite said:**
> @ dfreer
i haven't had any problems reaching R Belmont's site ever.

Neither have I, however evidently some people either can't access it/can't follow written instructions and so I posted the files. Eh.

---

### Post by michel_iwaniec on 2008-04-08
Compiling Nestopia worked fine for me, but the sound won't work at all.

OSS says:
"/dev/dsp: Device or resource busy
ERROR: unable to open soundcard. Aborting."

ALSA says:
"Could not open soundcard (Device or resource busy)"

Does anyone know what the problem might be? I'm running Ubuntu 7.10 on a Znote 6224W laptop.

---

### Post by disturbedite on 2008-04-08
there is an option in the frontend in the sound section, its the only option in the sound section, use it!
its to switch between oss & alsa.  try it & see if it works.

---

### Post by michel_iwaniec on 2008-04-08
> **disturbedite said:**
> there is an option in the frontend in the sound section, its the only option in the sound section, use it!
its to switch between oss & alsa.  try it & see if it works.
As mentioned above, both OSS or ALSA give me errors and no sound, no matter which I select in the Nestopia GUI. The only difference is the error message written to the console.

---

### Post by michel_iwaniec on 2008-04-08
Well, it seems this error was easily solved by closing Firefox. Some webpage must have managed to block the sound drivers completely.

However, even though the sound works, it pops and cracks and is a pain to listen to. Switching to other programs pauses playback even longer.

I have actually been having these kind of latency issues with many programs. Isn't there someway to fix this? Or at least give a higher priority to a certain running application in some way. :(

---

### Post by disturbedite on 2008-04-09
well then... it sounds like it might be a driver issue as opposed to a nestopia issue.

---

### Post by jjk7288 on 2008-04-09
I don't know if Nestopia has an option for this, but I was having a similar problem in ZSNES which I fixed by setting the sound sampling rate to 48000 KHz

---

### Post by disturbedite on 2008-04-11
no, there isn't an option for that in the nestopia (frontend) for linux.  it may be possible to change it in the config file though.

---

### Post by DanseNoir on 2008-04-13
> Everything was fine until I typed "make" and then I received a slew of errors - seem to be a bunch of undefined variables.  The top of the output was that I was missing gtk2.0, so I apt-get'd gtk+2.0-dev and I made some progress.  Now, when I type make, I get the following shorter list of errors:

```
Compiling source/linux/main.cpp...
Compiling source/linux/oss.cpp...
source/linux/oss.cpp:16:28: error: alsa/asoundlib.h: No such file or directory

```

Can you advise me of what I should do next?  Perhaps there's a log or output I can post that will give you some clues?  Thank you again for all that you do.

Edit:  Bah, I really wish I would wait on posting thist stuff.  No sooner than I posted did I google and I checked the repos.  I apt-get'd libasound2-dev.  Did an updatedb and typed make.  It took about 4 minutes to compile, but IT WORKED!  I haven't tested it yet - like trying to load roms and such - but I've made this progress and wanted to let you know.  So, for the future, get gtk2.0-dev and libasound2-dev :)  I'll keep you posted on how it works.

I'm having the same issue that you were originally having.  I get down to the "make" line before getting a long string of error messages.  Unfortunately, the output is so long, I can't even get to the top of it.  But it's basically a bunch of this:

> source/linux/callbacks.h:50: error: ‘GtkRange’ was not declared in this scope
source/linux/callbacks.h:50: error: ‘range’ was not declared in this scope
source/linux/callbacks.h:51: error: ‘gpointer’ was not declared in this scope
source/linux/callbacks.h:51: error: initializer expression list treated as compound expression

Is there any way someone can walk-me through how to fix this?  Reading over the requirements on the bottom of [the official website]("http://rbelmont.mameworld.info/?page_id=200"):

(1) It would appear that I have GCC.  
(2) G++-Multilib is available via the Synaptic Package Manager (SPM), but not installed
(3) There are a bunch of "GTK2" related files in SPM, but no GTK+ 2.4 or later
(4) alsa-base and alsa-utils are installed.
(5) I'm not sure about SDL.  I see a libsdl1.2debian and a libsdl1.2debian-alsa both installed.

Anyone have any clue what the problem might be from this data?

---

### Post by dfreer on 2008-04-14
When the output is really long, you can do several things: piping it through less or dumping the output to a text file are possible solutions. In any case, you need to find the FIRST few errors when trying to figure out why a program isn't compiling: 90% of the time the later errors are directly related to the first one.

Pipe the output through "less":
```
./configure **| less**
```

Dump output into a text file:
```
./configure **> output.txt**
```

Futhermore, you can always grep the output for errors (not on linux right now, so can't say for certain this is the correct/best way to do it):
```
cat output.txt | grep error
```

---

### Post by Bagleemo on 2008-10-19
I have the same first error, and the alsa libraries appear to be installed. Anyone have any ideas about how to fix this build error?

"source/linux/oss.cpp:16:28: error: alsa/asoundlib.h: No such file or directory"

---

### Post by dfreer on 2008-10-19
Do a search on packages.ubuntu.com whenever it complains you are missing a file.
[http://packages.ubuntu.com/search?searchon=contents&keywords=asoundlib.h&mode=exactfilename&suite=hardy&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=asoundlib.h&mode=exactfilename&suite=hardy&arch=any)

In this case the package you need is libasound2-dev. Note also, when you compile programs, if the program needs xyz to run, you will need xyz-dev to compile.

---

### Post by Bagleemo on 2008-10-19
Thanks dfreer! Got it, and it built just fine. I appreciate the help.

---

### Post by dkrus on 2008-12-10
Working fine here..I have the newest version nst140_lnx_release_h if anyone wants it

---

### Post by Faolan84 on 2009-02-07
I would be interested in trying Nestopia 1.40 if someone could provide a 32-bit deb package. I know friends who have Windows that use it and it's honestly go to be one of the best emulators I've even gotten a chance to use. Shame it took so long to port.

I'd like to see Super Nintendo and GameBoy emulation layers built in after the core is finished. that would be awesome to have an emulator that could support multiple systems and have an easy to use GUI.

And please no one tell me to use MAME / MESS because I could never get any version of them to ever wold on multiple computers. It always complains about not having a ROM or something even when I supply it with one: ie, it doesn't like my ROM collection.

---

### Post by disturbedite on 2009-02-09
> **Faolan Devyn Aodfin said:**
> I'd like to see Super Nintendo and GameBoy emulation layers built in after the core is finished.

i know for a fact that will never happen. the devs are completely against this type of thing. the snes equivalent of nestopia is bsnes. (no, not zsnes, bsnes).

> **Faolan Devyn Aodfin said:**
> And please no one tell me to use MAME / MESS because I could never get any version of them to ever wold on multiple computers. It always complains about not having a ROM or something even when I supply it with one: ie, it doesn't like my ROM collection.
i wasn't going to tell you to use mame, but the reason you couldn't get it work is cuz you aren't/weren't familiar enough with mame to get it to work.
mame generally requires an up-to-date romset. it is updated every time mame is...

---

### Post by Faolan84 on 2009-02-09
bsnes? unfortunate name. anyways, i tried it and it's quite slow. but they are correct that it is accurate. however, i do think it could be faster. really, you should have to have a 64-bit dual core running at 2.0 GHz and 2 GB of RAM. My computer is an older 2.26 GHz Pentium 4 with 3/4 GB of RAM and a ATI Radeon card with 128 MB of VRAM. Not exactly a beast by today's standards. It has difficulty ripping and playing music at the same time sometimes so i definitely will be putting in some more RAM once I can afford it and maybe a video card and processor upgrade too if my motherboard can handle it.

---

### Post by disturbedite on 2009-02-09
> **Faolan Devyn Aodfin said:**
> bsnes? unfortunate name. anyways, i tried it and it's quite slow. but they are correct that it is accurate. however, i do think it could be faster. really, you should have to have a 64-bit dual core running at 2.0 GHz and 2 GB of RAM. My computer is an older 2.26 GHz Pentium 4 with 3/4 GB of RAM and a ATI Radeon card with 128 MB of VRAM. Not exactly a beast by today's standards. It has difficulty ripping and playing music at the same time sometimes so i definitely will be putting in some more RAM once I can afford it and maybe a video card and processor upgrade too if my motherboard can handle it.
that is because is made to be as **perfect** as possible as far as emulation is concerned. features are only secondary. its requires a very "hefty" system so to speak.
i just upgraded my system with a 3.33 GHz intel dual core duo & 2GB DDR2 800 RAM. i haven't tried out bsnes yet though...

---

### Post by Faolan84 on 2009-02-09
> **disturbedite said:**
> i just upgraded my system with a 3.33 GHz intel dual core duo & 2GB DDR2 800 RAM. i haven't tried out bsnes yet though...

That is a beast of a machine. I'd like to hear how it runs on it when you get a chance to do so.

---

### Post by Solid One on 2009-03-15
I did as said before: got first the source code from sourceforge and uncompressed it to a directory called "Nestopia", then the overlay source from Arbee and uncompressed it to the same "Nestopia" directory. But when I tried do compile with the command "make", I get this error:

> leo@leo-desktop:~/Jogos/Nestopia140src$ make
Compiling source/linux/main.cpp...
source/linux/main.cpp:504: error: ‘Nes::Api::User::FileData’ has not been declared
source/linux/main.cpp:504: error: cannot declare parameter ‘operation’ to be of abstract type ‘Nes::Api::User::File’
source/core/api/NstApiUser.hpp:125: note:   because the following virtual functions are pure within ‘Nes::Api::User::File’:
source/core/api/NstApiUser.hpp:221: note: 	virtual Nes::Api::User::File::Action Nes::Api::User::File::GetAction() const
source/linux/main.cpp: In function ‘void DoFileIO(void*, Nes::Api::User::File, int&)’:
source/linux/main.cpp:506: error: switch quantity not an integer
source/linux/main.cpp:508: error: ‘FILE_LOAD_BATTERY’ is not a member of ‘Nes::Api::User’
source/linux/main.cpp:509: error: ‘FILE_LOAD_EEPROM’ is not a member of ‘Nes::Api::User’
source/linux/main.cpp:527: error: request for member ‘resize’ in ‘data’, which is of non-class type ‘int’
source/linux/main.cpp:528: error: request for member ‘front’ in ‘data’, which is of non-class type ‘int’
source/linux/main.cpp:533: error: ‘FILE_SAVE_BATTERY’ is not a member of ‘Nes::Api::User’
source/linux/main.cpp:534: error: ‘FILE_SAVE_EEPROM’ is not a member of ‘Nes::Api::User’
source/linux/main.cpp:539: error: request for member ‘front’ in ‘data’, which is of non-class type ‘int’
source/linux/main.cpp:539: error: request for member ‘size’ in ‘data’, which is of non-class type ‘int’
source/linux/main.cpp:544: error: ‘FILE_SAVE_FDS’ is not a member of ‘Nes::Api::User’
source/linux/main.cpp:553: error: request for member ‘front’ in ‘data’, which is of non-class type ‘int’
source/linux/main.cpp:553: error: request for member ‘size’ in ‘data’, which is of non-class type ‘int’
source/linux/main.cpp:558: error: ‘FILE_LOAD_TAPE’ is not a member of ‘Nes::Api::User’
source/linux/main.cpp:559: error: ‘FILE_SAVE_TAPE’ is not a member of ‘Nes::Api::User’
source/linux/main.cpp:560: error: ‘FILE_LOAD_TURBOFILE’ is not a member of ‘Nes::Api::User’
source/linux/main.cpp:561: error: ‘FILE_SAVE_TURBOFILE’ is not a member of ‘Nes::Api::User’
source/linux/main.cpp: In function ‘int main(int, char**)’:
source/linux/main.cpp:916: warning: deprecated conversion from string constant to ‘gchar*’
source/linux/main.cpp:932: error: invalid conversion from ‘void (*)(void*, Nes::Api::User::File, int&)’ to ‘void (*)(void*, Nes::Api::User::File&)’
source/linux/main.cpp:932: error:   initializing argument 1 of ‘void Nes::Core::UserCallback<T>::Set(T, void*) [with T = void (*)(void*, Nes::Api::User::File&)]’
source/linux/main.cpp: In function ‘void SetupVideo()’:
source/linux/main.cpp:1102: error: ‘NTSC_HEIGHT’ is not a member of ‘Nes::Core::Video::Output’
source/linux/main.cpp:1135: error: ‘class Nes::Api::Cartridge::Database’ has no member named ‘GetRegion’
source/linux/main.cpp:1135: error: ‘REGION_PAL’ is not a member of ‘Nes::Api::Cartridge’
source/linux/main.cpp:1197: error: ‘struct Nes::Api::Video::RenderState’ has no member named ‘scanlines’
source/linux/main.cpp:1237: error: ‘exit’ is not a member of ‘std’
source/linux/main.cpp: In function ‘void LoadGame(const char*)’:
source/linux/main.cpp:1317: error: no matching function for call to ‘Nes::Api::Cartridge::Database::FindEntry(void*, int&)’
source/core/api/NstApiCartridge.hpp:1047: note: candidates are: Nes::Api::Cartridge::Database::Entry Nes::Api::Cartridge::Database::FindEntry(const Nes::Api::Cartridge::Profile::Hash&, Nes::Api::Machine::FavoredSystem) const
source/core/api/NstApiCartridge.hpp:1057: note:                 Nes::Api::Cartridge::Database::Entry Nes::Api::Cartridge::Database::FindEntry(const void*, Nes::ulong, Nes::Api::Machine::FavoredSystem) const
source/linux/main.cpp:1321: error: no matching function for call to ‘Nes::Api::Machine::Load(std::istrstream&)’
source/core/api/NstApiMachine.hpp:184: note: candidates are: Nes::Result Nes::Api::Machine::Load(std::istream&, Nes::Api::Machine::FavoredSystem, Nes::Api::Machine::AskProfile)
source/core/api/NstApiMachine.hpp:195: note:                 Nes::Result Nes::Api::Machine::Load(std::istream&, Nes::Api::Machine::FavoredSystem, Nes::Api::Machine::Patch&, Nes::Api::Machine::AskProfile)
source/core/api/NstApiMachine.hpp:403: note:                 Nes::Result Nes::Api::Machine::Load(std::istream&, Nes::Api::Machine::FavoredSystem, Nes::Api::Machine::AskProfile, Nes::Api::Machine::Patch*, Nes::uint)
source/linux/main.cpp:1351: error: no matching function for call to ‘Nes::Api::Cartridge::Database::FindEntry(unsigned char*&, int&)’
source/core/api/NstApiCartridge.hpp:1047: note: candidates are: Nes::Api::Cartridge::Database::Entry Nes::Api::Cartridge::Database::FindEntry(const Nes::Api::Cartridge::Profile::Hash&, Nes::Api::Machine::FavoredSystem) const
source/core/api/NstApiCartridge.hpp:1057: note:                 Nes::Api::Cartridge::Database::Entry Nes::Api::Cartridge::Database::FindEntry(const void*, Nes::ulong, Nes::Api::Machine::FavoredSystem) const
source/linux/main.cpp:1360: error: no matching function for call to ‘Nes::Api::Machine::Load(std::ifstream&)’
source/core/api/NstApiMachine.hpp:184: note: candidates are: Nes::Result Nes::Api::Machine::Load(std::istream&, Nes::Api::Machine::FavoredSystem, Nes::Api::Machine::AskProfile)
source/core/api/NstApiMachine.hpp:195: note:                 Nes::Result Nes::Api::Machine::Load(std::istream&, Nes::Api::Machine::FavoredSystem, Nes::Api::Machine::Patch&, Nes::Api::Machine::AskProfile)
source/core/api/NstApiMachine.hpp:403: note:                 Nes::Result Nes::Api::Machine::Load(std::istream&, Nes::Api::Machine::FavoredSystem, Nes::Api::Machine::AskProfile, Nes::Api::Machine::Patch*, Nes::uint)
source/linux/main.cpp:1413: error: ‘class Nes::Api::Nsf’ has no member named ‘GetMaker’
source/linux/main.cpp:1348: warning: ignoring return value of ‘size_t fread(void*, size_t, size_t, FILE*)’, declared with attribute warn_unused_result
make: ** [objs/linux/main.o] Erro 1


I'm using Ubuntu 8.10 and it seems I have all needed dependancies. But I don't know why I'm getting this strange error. Any ideas?

---

### Post by disturbedite on 2009-03-15
> **Faolan Devyn Aodfin said:**
> That is a beast of a machine. I'd like to hear how it runs on it when you get a chance to do so.

it runs like i'm running a text editor, unless i use the hq2x filter (but i don't like that filter compared to the ntsc filter). the only reason that it runs slower with the hq2x filter is cuz i'm temporarly using the onboard intel g45 video.

---

### Post by medwyn on 2009-04-18
I just downloaded the windows version and used WINE; everything works fine including the joypad.

---

### Post by disturbedite on 2009-04-18
> **medwyn said:**
> I just downloaded the windows version and used WINE; everything works fine including the joypad.

why would you do that when there is a native linux port with a gui?

---

### Post by BigSilly on 2009-04-19
> **disturbedite said:**
> why would you do that when there is a native linux port with a gui?

Because it's a PITA to compile? :biggrin:

Normally I'd agree with you, but for such a small program it can be a sod to successfully compile. So while I don't imagine I'll use the Windows version via WINE, I'll stick with Mednafen for NES for now. :(

---

### Post by disturbedite on 2009-04-19
> **BigSilly said:**
> Because it's a PITA to compile? :biggrin:

Normally I'd agree with you, but for such a small program it can be a sod to successfully compile. So while I don't imagine I'll use the Windows version via WINE, I'll stick with Mednafen for NES for now. :(

how is it a PITA to compile? i've never ever heard this complaint. it is about as easy as it gets in my experience...

although i haven't had to compile it in a long time cuz it is packaged for opensuse.

---

### Post by BigSilly on 2009-04-19
It was fine when I compiled the last version, and I had no problems, but I just couldn't get past errors with the new release. I don't think it's ideal dropping the "overlay" into the directory if I'm honest, but hey what do I know? :biggrin:

---

### Post by Artemis3 on 2009-09-28
I just compiled this and it seems to run well but... it is running slower than it should, and audio is stuttering a little, as if it were lock into 80% speed, no matter what video or sound settings.

---

### Post by disturbedite on 2009-09-29
> **Artemis3 said:**
> I just compiled this and it seems to run well but... it is running slower than it should, and audio is stuttering a little, as if it were lock into 80% speed, no matter what video or sound settings.

if you want some help, you might try posting over at nestopia's forum: [http://www.bannister.org/forums/ubbthreads.php?ubb=postlist&Board=7&page=1](http://www.bannister.org/forums/ubbthreads.php?ubb=postlist&Board=7&page=1)

---

### Post by dfreer on 2009-09-29
On a side note: bsnes system requirements have dropped down to just a Intel Core Solo. Further releases (the emulator is under constant active development) will see that get dropped even futher I believe.

---

### Post by Artemis3 on 2009-09-29
That looks like an snes emu, i need a good nes emu :P

On a side note, make sure your emu can do the Tales of Phantasia opening twice flawless :)

---

### Post by dfreer on 2009-09-29
> **Artemis3 said:**
> That looks like an snes emu, i need a good nes emu :P

On a side note, make sure your emu can do the Tales of Phantasia opening twice flawless :)

Yeah, I realize this is a NES thread but bsnes somehow came up, I was responding to previous posts. And I'm pretty sure it does, I'm not intimately familiar with ToP but it seemed to me like the music was in sync. Try it yourself, or at least pop by the forums at [http://byuu.org/](http://byuu.org/) and see what others have to say.

---

### Post by amano on 2009-10-26
It is a shame that there is no movement within the packaging request: [https://bugs.launchpad.net/ubuntu/+bug/178034](https://bugs.launchpad.net/ubuntu/+bug/178034)

Nestopia is great. It deserves a Debian/Ubuntu package. Maybe you can help with this "bug"?

---

### Post by disturbedite on 2009-10-27
> **amano said:**
> It is a shame that there is no movement within the packaging request: [https://bugs.launchpad.net/ubuntu/+bug/178034](https://bugs.launchpad.net/ubuntu/+bug/178034)

Nestopia is great. It deserves a Debian/Ubuntu package. Maybe you can help with this "bug"?

a shame yes. i was the one that filed that bug a long time ago when i still used *ubuntu. i use opensuse now and it is packaged for my distro. :p

maybe you could convert the rpm package to a deb package. i know converting a deb package to an rpm package is possible with alien but i don't know if it is possible to do the opposite.

---

### Post by DouglasAWh on 2010-01-04
I find it really hard to believe all these people want a .deb and no one tried alien...or did I just miss it?

---

### Post by dfreer on 2010-01-06
> **DouglasAWh said:**
> I find it really hard to believe all these people want a .deb and no one tried alien...or did I just miss it?

IIRC the thread is concerned with compiling Nestopia from it's original windows source using a patch to make it work in linux. Alien can't help there, although if some other distro has created an RPM package users could use it then. 

Me myself, I'd just decompress the RPM package and run the binary locally as opposed to trusting Alien to install it correctly for me.

---

### Post by farrell2k on 2010-01-06
Why is a .deb needed?   Why not just compile, enter src dir, grab binary, and move it to a custom directory in home?   You don't have to make install.

---

### Post by zer010 on 2010-08-08
i've had problems compiling nestopia. can anyone help me out on this issue? Ubuntu STILL won't put it into the repos! It's STILL listed in launchpad.:(  It just doesn't run as well under WINE and GFCEUX (whatever it is) doesn't compare to nestopia. For one I can't map buttons in GFCEUX..whatever! I guess i could just run it in Windows, but why?

---

### Post by gewone on 2010-11-23
Anyone with a hint? Or anyone with experience who could create a .DEB package for Ubuntu 10.10 (Maverick) perhaps? Feels like dependencies could easily fall apart if trying anything now. Also, I have great experience from Nestopia since all my years with Windows. Now, I'm in Ubuntu and first tried FCEU. It's really nice and smooth, only thing I miss is the ability to record with an actual audio/video codec, instead of writing text-based recordings, like FCEU/Linux does. Any other emulator that is apt-gettable that supports eg. AVI recording? Nestopia would probably be the best, for me anyways.

[I]Regards~
Ty in adv for helping a fellow out~
[/I]

---

### Post by disturbedite on 2010-11-23
disclaimer: i make NO claim whatsoever this package will install or work. it is converted from an opensuse package so it may not work at all because of differences in the names of dependencies on opensuse and ubuntu.

here is a 64-bit deb package i converted from an opensuse rpm package: [http://www.megaupload.com/?d=S11845JA](http://www.megaupload.com/?d=S11845JA)

i tried converting a 32-bit package but alien would not generate a package. strangely, it did not generate a warning or error of any kind. it just acted as if it was converted successfully. i'm guessing it might be because i'm on 64-bit architecture.
you can download the 32-bit opensuse rpm here: [http://software.opensuse.org/search/download?base=openSUSE%3A11.3&file=Emulators%2FopenSUSE_11.3%2Fi586%2Fnestopia-1.40rh-2.1.i586.rpm&query=nestopia](http://software.opensuse.org/search/download?base=openSUSE%3A11.3&file=Emulators%2FopenSUSE_11.3%2Fi586%2Fnestopia-1.40rh-2.1.i586.rpm&query=nestopia)
(right-click save as)
to convert it with alien do this:
(make sure alien is installed of course)
```
sudo alien -d /path/to/package -k
```
alien must be run a su/root. the -d tells alien to convert to a debian package. the -k option tells alien to keep the version number (which is of course optional).
its that simple. then just install the package.

BTW, the person that mentioned before that alien can't help with patching is incorrect: alien DOES have patching capability.

---

### Post by zer010 on 2010-11-28
1.)   I guess I'll try using alien, it sounds like an idea anyways. How reliable is alien?
2.)   I'd still like a concise way to compile Nestopia. When I used to try to compile Nestopia, I'd always get some cryptic errors and then I'd get no help in resolving the issue so I basically gave up trying to compile anything months ago.

---

### Post by zer010 on 2010-11-28
I just tried using alien on the .RPM and it made a .deb in /home. I installed it and at first I couldn't find the binary! I found it in /usr/bin and added it to the Games menu with a nice Nestopia icon I found. Got a few ROMS of some old games that I have and it works great! Thanks, disturbedite!  
I've included my 32-bit .deb with the nestopia icon.

---

### Post by mister_playboy on 2010-11-30
> **disturbedite said:**
> here is a 64-bit deb package i converted from an opensuse rpm package: [http://www.megaupload.com/?d=S11845JA](http://www.megaupload.com/?d=S11845JA)

Thanks a lot for the .deb... it worked great for me. :D  I haven't been able to get sound working correctly in FCEUX on 10.10, but Nestopia is working perfectly.

---

### Post by disturbedite on 2010-11-30
> **mister_playboy said:**
> Thanks a lot for the .deb... it worked great for me. :D  I haven't been able to get sound working correctly in FCEUX on 10.10, but Nestopia is working perfectly.

no problem.

---

