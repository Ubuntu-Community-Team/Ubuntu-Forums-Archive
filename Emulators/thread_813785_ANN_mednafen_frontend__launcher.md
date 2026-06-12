---
title: "ANN: mednafen frontend / launcher"
date: 2008-05-31
forum: Emulators
---

### Post by MonkeeSage on 2008-05-31
Hi folks,

Here is a simple mednafen frontend / launcher, written in python and GTK+. No .debs yet (I'll make some soon...promise).

Screenshots:

[img]http://sourceforge.net/dbimage.php?id=174635[/img]

[img]http://sourceforge.net/dbimage.php?id=174633[/img]

[img]http://sourceforge.net/dbimage.php?id=174631[/img]

In planning (or at least up for consideration) are an input configuration dialog and a cheat code editor. But those are prolly still a ways off. See the INSTALL file in the tarball for install instructions (standard python distutils installation), but installation is not required; it should run from any directory in which you unpack it.

Get it here: [http://sourceforge.net/projects/mednafenfe/](http://sourceforge.net/projects/mednafenfe/)

---

### Post by disturbedite on 2008-05-31
OMG!  awesome!  i can't till you make deb packages.  i await in anticipation.

i know this is a far shot, or a shot in the dark.....but do you think you could also make a qt4 version of your frontend?

---

### Post by MonkeeSage on 2008-06-01
> **disturbedite said:**
> OMG!  awesome!  i can't till you make deb packages.  i await in anticipation.

Alright, a deb is up at sourceforge. :)


> **disturbedite said:**
> i know this is a far shot, or a shot in the dark.....but do you think you could also make a qt4 version of your frontend?

I've never used pyQt, so I'm probably not going to make a QT version (unless a lot of people want it). But the source is MIT licensed (which is basically just public domain with a legal disclaimer), and people are welcome to hack it all they like. It should be fairly quick and easy for someone familiar with pyQt to knock out a GUI in Designer and change the glade / gtk stuff in mfe.py.

---

### Post by acoustibop on 2008-06-01
> **MonkeeSage said:**
> Alright, a deb is up at sourceforge. :)... 

To be found [here]("https://sourceforge.net/projects/mednafenfe/"). ;)

---

### Post by MonkeeSage on 2008-06-01
Slight bugfix up (ver 0.1.1).

* Fix spacing issues with glade widgets (minor)
* Trap signals (SIGTERM, SIGINT) and exit cleanly
* Fix code to de-/sensitize "Force Mono" checkbutton on init

New deb up at SF.

---

### Post by MonkeeSage on 2008-06-01
> **acoustibop said:**
> To be found [here]("https://sourceforge.net/projects/mednafenfe/"). ;)

Thanks. :)

---

### Post by FranMichaels on 2008-06-01
Very nicely done! :KS

---

### Post by Occasionally Correct on 2008-06-01
I had just started working on a similar frontend for Mednafen a few days ago. Now I don't have to! :p

Nice work.

---

### Post by DoktorSeven on 2008-06-01
1) I would made the window resizable since I have issues with options spilling down over the elements below them.
2) Change your source package to extract to its own directory, instead of the current directory.
3) The ROM selection should be made a bit more obvious; being at the bottom of the second tab is a bit odd.

Just constructive criticism, nice work so far.

---

### Post by disturbedite on 2008-06-01
dang!  i test intrepid & there are dependency problems, so i can't install this package.  :(
(python conflicts & whatnot).

---

### Post by MonkeeSage on 2008-06-01
> **DoktorSeven said:**
> 1) I would made the window resizable since I have issues with options spilling down over the elements below them.

Done. New tarball and deb up (I didn't bump the version, still 0.1.1).

> **DoktorSeven said:**
> 2) Change your source package to extract to its own directory, instead of the current directory.

It should have, I accidentally uploaded wrong tarball. Fixed now.


> **DoktorSeven said:**
> 3) The ROM selection should be made a bit more obvious; being at the bottom of the second tab is a bit odd.

Eh, doesn't seem like a big deal to me, but I'll keep that in mind.


> **DoktorSeven said:**
> Just constructive criticism, nice work so far.

NP :) Thanks for the feedback, it is welcome.

---

### Post by MonkeeSage on 2008-06-01
> **disturbedite said:**
> dang!  i test intrepid & there are dependency problems, so i can't install this package.  :(
(python conflicts & whatnot).

Hmmm...what is the error message? AFAIK, intrepid should have python, python-gtk2, and pyton-glade2 installed (since update-manager needs them). So maybe I botched the dependencies. Please attach (or post, if it's short enough) a log of your console output when you try to install the deb.

---

### Post by disturbedite on 2008-06-02
@ MonkeeSage
sure, no problem, here is the message(s):

sudo dpkg -i /media/disk/software/gaming/mednafenfe_0.1.1-0ubuntu1_all.deb
Selecting previously deselected package mednafenfe.
(Reading database ... 146323 files and directories currently installed.)
Unpacking mednafenfe (from .../mednafenfe_0.1.1-0ubuntu1_all.deb) ...
dpkg: dependency problems prevent configuration of mednafenfe:
 mednafenfe depends on python-configobj; however:
  Package python-configobj is not installed.
 mednafenfe depends on python-glade2; however:
  Package python-glade2 is not installed.
 mednafenfe depends on python-gtk2; however:
  Package python-gtk2 is not installed.
dpkg: error processing mednafenfe (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mednafenfe

so:

sudo apt-get install python-configobj python-glade2 python-gtk2
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  python-gtk2: Depends: python-cairo (>= 1.0.2-1.1) but it is not going to be installed
               Depends: python-gobject (>= 2.14) but it is not going to be installed
               Depends: python-numeric (>= 24.2-3) but it is not going to be installed
               Depends: python2.4-cairo
               Depends: python2.4-gobject
               Depends: python2.4-numeric
               Depends: python2.5-cairo
               Depends: python2.5-gobject
               Depends: python2.5-numeric
               Recommends: python-gtk2-doc but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

btw, i didn't mean that *you* goofed up the dependencies, i meant the dependencies are goofed up in the ubuntu repo right now, for intrepid at least, as evidenced by the latter message.

---

### Post by MonkeeSage on 2008-06-02
> **disturbedite said:**
> @ MonkeeSage
sure, no problem, here is the message(s):

sudo dpkg -i /media/disk/software/gaming/mednafenfe_0.1.1-0ubuntu1_all.deb
Selecting previously deselected package mednafenfe.
(Reading database ... 146323 files and directories currently installed.)
Unpacking mednafenfe (from .../mednafenfe_0.1.1-0ubuntu1_all.deb) ...
dpkg: dependency problems prevent configuration of mednafenfe:
 mednafenfe depends on python-configobj; however:
  Package python-configobj is not installed.
 mednafenfe depends on python-glade2; however:
  Package python-glade2 is not installed.
 mednafenfe depends on python-gtk2; however:
  Package python-gtk2 is not installed.
dpkg: error processing mednafenfe (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mednafenfe

so:

sudo apt-get install python-configobj python-glade2 python-gtk2
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  python-gtk2: Depends: python-cairo (>= 1.0.2-1.1) but it is not going to be installed
               Depends: python-gobject (>= 2.14) but it is not going to be installed
               Depends: python-numeric (>= 24.2-3) but it is not going to be installed
               Depends: python2.4-cairo
               Depends: python2.4-gobject
               Depends: python2.4-numeric
               Depends: python2.5-cairo
               Depends: python2.5-gobject
               Depends: python2.5-numeric
               Recommends: python-gtk2-doc but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Hmmm...something definitely seems screwy...according to packages.ubuntu.com[[1](http://packages.ubuntu.com/intrepid/update-manager)], update-manager (which is part of the base system, so it's gotta be installed!) depends on python-glade2. But apt is saying that python-glade2 isn't installed??? Huh?

Hmmm...*is* update-manager installed in intrepid? What do you get when you run:

```
apt-cache policy update-manager 2>&1 | awk '/Installed:/ {print $2}'
```

And what do you get from a dry run (no-op) of apt with the -f switch?

```
sudo apt-get --dry-run -f install python-configobj python-glade2 python-gtk2
```


> **disturbedite said:**
> btw, i didn't mean that *you* goofed up the dependencies, i meant the dependencies are goofed up in the ubuntu repo right now, for intrepid at least, as evidenced by the latter message.

Hey, no worries. I'm new to debian-based systems. I've only been running Ubuntu for about 6 months. Previously my experience is with source-based distros like Slack, Gentoo and Arch, and before that, rpm / yum based systems. So this whole deb thing is new to me. I'll prolly goof-up from time to time. ;)

---

### Post by disturbedite on 2008-06-04
maybe it is due to the fact that i use kubuntu?...  (kde 4.1b1)

---

### Post by Cresho on 2008-06-04
just to help fix an issue, first launch mednafen and then mfe in terminal for new users who never used it.  If you launch mfe first, you get an error missing ~mednafen/mfe.ini  so launching mednafen first in terminal puts it in here and you wont get the error

---

### Post by MonkeeSage on 2008-06-04
> **Cresho said:**
> just to help fix an issue, first launch mednafen and then mfe in terminal for new users who never used it.  If you launch mfe first, you get an error missing ~mednafen/mfe.ini  so launching mednafen first in terminal puts it in here and you wont get the error
Thank you, I just fixed the problem. Now it should work whether you have a ~/.mednafen directory or don't when you first run mfe (or any time after that as well). New tarball and deb at SF.

---

### Post by MonkeeSage on 2008-06-04
> **disturbedite said:**
> maybe it is due to the fact that i use kubuntu?...  (kde 4.1b1)

Hmmm, actually I think that is why. I think Kubuntu does use a different package manager / update notification system, now that I think about it. Sorry about that.

When I have time tonight, I'll try to figure out what kubuntu needs to run mfe on intrepid and get the deps straight in the deb so it will automatically pull in whatever it needs (and those packages will be marked as auto-installed, so if mfe is removed, they can be removed automatically).

---

### Post by Cresho on 2008-06-04
another problem that i see..in ubuntu hardy heron, I have a problem with mfe in the start menu.  It will not start up.  If I do it from the terminal, it launches fine with mfe.  sometimes it will start and when i select rom, it ill not launch the actual game rom but stay hanging in the mfe front end.  If I do mfe from terminal, there is no problems what so ever.
```
location: /usr/lib/xulrunner-1.9b5/libxpcom.so 
before 3
/usr/games/mednafen -path_snap /home/ranxerox/.mednafen/snaps -path_sav /home/ranxerox/.mednafen/sav -path_state /home/ranxerox/.mednafen/sav -path_movie /home/ranxerox/.mednafen/movies -path_cheat /home/ranxerox/.mednafen/cheats -path_palette /home/ranxerox/.mednafen/palettes -vdriver opengl -glvsync 1 -pce.pixshader none -fs 0 -sound 1 -soundrate 32000 -sounddriver alsa -soundvol 100 -pce.forcemono 0 -cheats 0 -autosave 0 -pce.xscale 3 -pce.yscale 3 -pce.xres 800 -pce.yres 600 -pce.stretch 1 -pce.videoip 0 -pce.vblur 0 -pce.scanlines 0 -pce.special none /home/ranxerox/Installed_Programs/roms/turbografx16-unzipped-mednafen/devilcru.pce
Starting Mednafen 0.8.7
 Loading settings from "/home/ranxerox/.mednafen/mednafen.cfg"...
 Compiled against SDL 1.2.12, running with SDL 1.2.12

 Initializing joysticks...
 Loading /home/ranxerox/Installed_Programs/roms/turbografx16-unzipped-mednafen/devilcru.pce...

  ROM:       384KiB
  ROM CRC32: 0x157b4492
  ROM MD5:   0x92fbe89d4c87bf283dbfbeac69a64e6e

  Loading cheats from /home/ranxerox/.mednafen/cheats/pce.cht...
   Error opening file: No such file or directory

 Initializing sound...
  Using "ALSA" audio driver with device "default":
   Bits: 16
   Rate: 32000
   Channels: 2
   Byte order: CPU Native
   Buffer size: 1024 sample frames(32.000000 ms)
 Initializing video...

Signal 11 has been caught and dealt with...
Iyeeeeeeeee!!!  A segmentation fault has occurred.  Have a fluffy day.

```

i did a sudo mfe in a script to see the error.  HOpe this helps.

---

### Post by Cresho on 2008-06-04
Here is an update to the top post.  In order for me to run the game front end and the game from the start menu, I changed the execute from mfe to "gnome-terminal --execute mfe" without quotes.  Now it launches with terminal and have no problems at all

sorry, it works better this way

create a mfe.sh and give it execute  rights

now but this code in it
```
#!/bin/bash
gnome-terminal --execute mfe
```
and in edit menus and launcher mednafen front end, direct executable to the mfe.sh file.  it will work then.

hmm did not work either

---

### Post by MonkeeSage on 2008-06-04
Cresho,

Signal 11 is SIGSEGV, i.e., "Segmentation Fault" -- it means mednafen is crashing because it tried to access a protected memory address. It has nothing directly to do with mfe (though, indirectly, it may be caused by some combination of settings to mednafen). Try running the same command directly from a terminal that mfe was running.

I.e., The line right after "before 3" and before "Starting Mednafen 0.8.7". E.g., in your post:

```
/usr/games/mednafen -path_snap /home/ranxerox/.mednafen/snaps -path_sav /home/ranxerox/.mednafen/sav -path_state /home/ranxerox/.mednafen/sav -path_movie /home/ranxerox/.mednafen/movies -path_cheat /home/ranxerox/.mednafen/cheats -path_palette /home/ranxerox/.mednafen/palettes -vdriver opengl -glvsync 1 -pce.pixshader none -fs 0 -sound 1 -soundrate 32000 -sounddriver alsa -soundvol 100 -pce.forcemono 0 -cheats 0 -autosave 0 -pce.xscale 3 -pce.yscale 3 -pce.xres 800 -pce.yres 600 -pce.stretch 1 -pce.videoip 0 -pce.vblur 0 -pce.scanlines 0 -pce.special none /home/ranxerox/Installed_Programs/roms/turbografx16-unzipped-mednafen/devilcru.pce
```

Run it several times and see if you get the same error. ("Signal 11 has been caught and dealt with...
Iyeeeeeeeee!!!  A segmentation fault has occurred.  Have a fluffy day.")

mfe should be polling the subprocess running mednafen, and should detect if it returns (whether from a segfault or being closed manually or whatever); so, if when you get that error on the console, the "Stop" button doesn't return to "Play" and the window become sensitive again, that may be a bug. So let me know about that.

As for launching in a terminal, just edit /usr/share/applications/mfe.desktop (with superuser privs.) and change "Terminal=false" to "Terminal=true". Using a terminal shouldn't make a bit of difference in how mfe behaves though.

---

### Post by disturbedite on 2008-06-04
> **MonkeeSage said:**
> Hmmm, actually I think that is why. I think Kubuntu does use a different package manager / update notification system, now that I think about it. Sorry about that.

When I have time tonight, I'll try to figure out what kubuntu needs to run mfe on intrepid and get the deps straight in the deb so it will automatically pull in whatever it needs (and those packages will be marked as auto-installed, so if mfe is removed, they can be removed automatically).
well, it isn't the package manager that is causing any problem whatsoever, it is the dependencies.  (kubuntu uses the same repos as ubuntu).  but i do look forward to you resolving the issue, perhaps by tweaking it's dependencies, or the ubuntu packagers getting the dependencies straightened out.

---

### Post by Cresho on 2008-06-05
> **MonkeeSage said:**
> Cresho,

Signal 11 is SIGSEGV, i.e., "Segmentation Fault" -- it means mednafen is crashing because it tried to access a protected memory address. It has nothing directly to do with mfe (though, indirectly, it may be caused by some combination of settings to mednafen). Try running the same command directly from a terminal that mfe was running.

I.e., The line right after "before 3" and before "Starting Mednafen 0.8.7". E.g., in your post:

```
/usr/games/mednafen -path_snap /home/ranxerox/.mednafen/snaps -path_sav /home/ranxerox/.mednafen/sav -path_state /home/ranxerox/.mednafen/sav -path_movie /home/ranxerox/.mednafen/movies -path_cheat /home/ranxerox/.mednafen/cheats -path_palette /home/ranxerox/.mednafen/palettes -vdriver opengl -glvsync 1 -pce.pixshader none -fs 0 -sound 1 -soundrate 32000 -sounddriver alsa -soundvol 100 -pce.forcemono 0 -cheats 0 -autosave 0 -pce.xscale 3 -pce.yscale 3 -pce.xres 800 -pce.yres 600 -pce.stretch 1 -pce.videoip 0 -pce.vblur 0 -pce.scanlines 0 -pce.special none /home/ranxerox/Installed_Programs/roms/turbografx16-unzipped-mednafen/devilcru.pce
```

Run it several times and see if you get the same error. ("Signal 11 has been caught and dealt with...
Iyeeeeeeeee!!!  A segmentation fault has occurred.  Have a fluffy day.")

mfe should be polling the subprocess running mednafen, and should detect if it returns (whether from a segfault or being closed manually or whatever); so, if when you get that error on the console, the "Stop" button doesn't return to "Play" and the window become sensitive again, that may be a bug. So let me know about that.

As for launching in a terminal, just edit /usr/share/applications/mfe.desktop (with superuser privs.) and change "Terminal=false" to "Terminal=true". Using a terminal shouldn't make a bit of difference in how mfe behaves though.

OKAY PROBLEM SOLVED!

I did as you asked and still saw some the same error.  NOW totally made sense when you directed it to be a memory error segmentation fault and a setting.  under general, i played with the settings and came to the conclusion that playing with cheats and openGL and vsync in different combinations, unticking Vsync fixed my problem

So unticking Vsync and OpenGL and Cheats works just fine.  Even Unticking all works fine. and leaving fullscreen ticked works fine at all.  Vsync is the cause of the segfault 11 error I posted.  Having compiz-fusion on or off has the same behavior.  I am using an 8800gt btw with a modified thermaltake fan on the video card.  Now I am wondering if I have lost a heatsink from the memory chip.

Thanks

---

### Post by MonkeeSage on 2008-06-05
> **disturbedite said:**
> well, it isn't the package manager that is causing any problem whatsoever, it is the dependencies.  (kubuntu uses the same repos as ubuntu).  but i do look forward to you resolving the issue, perhaps by tweaking it's dependencies, or the ubuntu packagers getting the dependencies straightened out.

Sorry I didn't get around to it last night. I started working on a joypad configuration frontend for joy2key (also possibly serving as a basis for a future input config tab for mfe).

Try this dry run (it won't actually install anything, just do the depgraph and brokeness checking and such) and tell me if apt-get still complains about dependencies:

```
apt-get --dry-run install python-configobj python-glade2 python-gtk2 python2.4-cairo python2.4-gobject python2.4-numeric python2.5-cairo python2.5-gobject python2.5-numeric
```

*Ps. Yes, oddly, python-gtk2 really does depend on both the 2.5 and 2.4 versions of those packages[[1]]("http://packages.ubuntu.com/intrepid/python-gtk2")*

Thanks.

---

### Post by MonkeeSage on 2008-06-05
> **Cresho said:**
> OKAY PROBLEM SOLVED!

Glad you got it sorted! :)

Ps. I'm using an ATI card with fglrx drivers, and I also get glitches and wierd stuff from time to time. Darn their proprietary drivers, I say. ;)

Also, when you get the segfault when running from mfe, does the interface become responsive again after the console message about the error? The Stop button goes back to Play and so forth?

---

### Post by MonkeeSage on 2008-06-05
Hmmm...the buttons next to the Extra Options entry on the General tab, were supposed to have tooltips...coulda swore I added 'em, but maybe I should really quite drinking, heh. Anyhow, they are there now (in svn, will be up in tarball and deb next minor release). Just for reference, the first button next to the entry (lil' broom thing) clears the entry for the current launch, and clears any any saved values; the second button saves the current values for this and future launches; the third button opens the mednafen docs (in a pygtkmozembed widget if supported, otherwise in external browser).

---

### Post by Cresho on 2008-06-06
> **MonkeeSage said:**
> Glad you got it sorted! :)

Ps. I'm using an ATI card with fglrx drivers, and I also get glitches and wierd stuff from time to time. Darn their proprietary drivers, I say. ;)

Also, when you get the segfault when running from mfe, does the interface become responsive again after the console message about the error? The Stop button goes back to Play and so forth?

everything is very responive!  even after closing the main game window.  I can launch a second game with no problem after closing the first one.  no corruption.  Just vsync causing problems.

---

### Post by slave-zeo on 2008-06-06
I get an error when starting mfe. 

> jeremy@pikachu:~$ mfe 
Traceback (most recent call last):
  File "/usr/bin/mfe", line 6, in <module>
    mfe.MednafenFE()
  File "/home/sage/mydocs/devel/projects/mfe-0.1.0/mednafenfe/debian/mednafenfe/usr/lib/python2.5/site-packages/mfe/mfe.py", line 29, in __init__
  File "/home/sage/mydocs/devel/projects/mfe-0.1.0/mednafenfe/debian/mednafenfe/usr/lib/python2.5/site-packages/mfe/mfeutil.py", line 175, in __init__
NameError: global name 'CreateConfigPathError' is not defined


I'm running 8.04 with latest updates. Geforce 7900gs with nvidia's driver. Nothing else special hardware wise.

Any thoughts or suguestions?

---

### Post by MonkeeSage on 2008-06-07
> **slave-zeo said:**
> I get an error when starting mfe. 

[. . .]

I'm running 8.04 with latest updates. Geforce 7900gs with nvidia's driver. Nothing else special hardware wise.

Any thoughts or suguestions?

Oops. Two bugs there. The first is a scoping issue -- I raised the exception without "self.". The second is that os.makedirs excepts when the target directory already exists. I thought it behaved like mkdir -p. My bad. New tarball / deb at SF (0.1.3), fixes these bugs.

---

### Post by slave-zeo on 2008-06-07
Man this front end is so kick butt. It is exactly what I need to actually enjoy Mednafen. BTW, it works like a charm now. Thanks.

Now to go thru the config file and get my gamepad working. Yikes!

---

### Post by FranMichaels on 2008-06-07
> **slave-zeo said:**
> 
Now to go thru the config file and get my gamepad working. Yikes!

Or press alt + shift + 1 in mednafen :)

---

### Post by slave-zeo on 2008-06-07
> **FranMichaels said:**
> Or press alt + shift + 1 in mednafen :)

Fran, you are my new personal hero. It worked like a CHARM.

BTW, thanks for stopping by my news site and signing up for an account. I appreciate all the support I can get.

---

### Post by MonkeeSage on 2008-06-08
> **slave-zeo said:**
> Man this front end is so kick butt. It is exactly what I need to actually enjoy Mednafen. BTW, it works like a charm now. Thanks.

Now to go thru the config file and get my gamepad working. Yikes!

Glad you're enjoying it! :)

I'm planning (and doing some rough test implementation of) an input editor for keyboard / gamepad. Currently, mednafen has built-in, on-the-fly input configuration (i.e., press ALT+SHIFT+1 to configure input 1 for the current system), but it would be cool to have a nice GUI configuration I think.

*Edit:* Oops. Hadn't refreshed the page. Didn't see that FranMichaels already mentioned mednafen's built-in input configuration.

---

### Post by MonkeeSage on 2008-06-08
Hmmmm..."/home/sage/mydocs/devel/projects/mfe-0.1.0/mednafenfe/debian/mednafenfe/usr/lib/python2.5/site-packages/mfe/mfe.py"

I wonder why the error message included that path...that's the path on *my* computer where I was tracking the source ("/home/sage/mydocs/devel/projects/mfe-0.1.0/mednafenfe"). I can't figure out why it would appear on your computer. It should have looked like "/usr/lib/python2.5/site-packages/mfe/mfe.py"....hmmm. What version of mednafenfe were you using and was it the deb or the tarball?

---

### Post by ikki_72 on 2008-06-08
a feature on button config would be nice.

---

### Post by slave-zeo on 2008-06-08
> **MonkeeSage said:**
> Hmmmm..."/home/sage/mydocs/devel/projects/mfe-0.1.0/mednafenfe/debian/mednafenfe/usr/lib/python2.5/site-packages/mfe/mfe.py"

I wonder why the error message included that path...that's the path on *my* computer where I was tracking the source ("/home/sage/mydocs/devel/projects/mfe-0.1.0/mednafenfe"). I can't figure out why it would appear on your computer. It should have looked like "/usr/lib/python2.5/site-packages/mfe/mfe.py"....hmmm. What version of mednafenfe were you using and was it the deb or the tarball?

I was running version 1.2 I think. It was the one that was released before you did the fix up. I got the same error message from both the tar ball and the deb.

hope this helps.

Also, I may be a bit on the dim side, but how do you tell mednafen to load PC Engine CD games via mfe? or can you yet.

thanks again for the great work on this front end.

---

### Post by Bill_Gates on 2008-06-09
Nice Frontend. But a QT4 version for Kubuntu users would be fantastic.

---

### Post by ikki_72 on 2008-06-09
> **Bill_Gates said:**
> Nice Frontend. But a QT4 version for Kubuntu users would be fantastic.

not after he did those button config thing :)

:popcorn:

---

### Post by VicAlpha on 2008-06-09
> **ikki_72 said:**
> a feature on button config would be nice.

I agree

---

### Post by slave-zeo on 2008-06-09
While not frontend related there was a new release of Mednafen today! version 0.8.9

---

### Post by MonkeeSage on 2008-06-10
Sorry for the delay in responding, my internet b0rked (oh noes!). Gophers or moles or something chewed up the co-ax underground. Cable guy came out today and ran a new line.


@slave-zeo:

Weird...I'll have a look and see if I can figure out what the deal with that is. There are no embeded paths like that, so that is very odd.


@ikki_72:

What is button config? Can you give me an example of another app that has this feature, so I know what you mean?

**Edit:** Do you mean a GUI to configure the buttons on a gamepad? If so, I'm working on something along those lines, but it won't be ready right away. I already have skeleton GUI for it and some of the logic done (I'm prototyping it by making a joy2key frontend. [screenshot]("http://mednafenfe.svn.sourceforge.net/viewvc/*checkout*/mednafenfe/screenshots/gjoy2key.png?revision=35") [active button on gamepad in green])

**Edit:** If this is what you mean, then as has been mentioned, you can currently use mednafen's built-in input configuration feature by pressing Alt+Shift+N, where N is the number of the input device to configure (so pressing Alt+Shift+1 configures the first input device). While a GUI config will be slightly nicer, the current method works just fine.


@Bill_Gates:

As I said previously, I have no experience with pyQT, so I probably won't be porting it to QT. Someone with knowledge of pyQT / Designer could do so easily (and I'd be glad to host it with this project on SF); it's basically just a bunch of buttons and checkboxes, and a bit of wrapper for callbacks and formatting the options to pass them to mednafen. The config file stuff and the stuff to run mednafen is in a separate module and shouldn't need anything done to it for a pyQT port.

---

### Post by MonkeeSage on 2008-06-11
> **slave-zeo said:**
> Also, I may be a bit on the dim side, but how do you tell mednafen to load PC Engine CD games via mfe? or can you yet.

thanks again for the great work on this front end.

Don't worry, it's not (too) hard....

Under the "General" tab, enter a path to the CD BIOS in the "Extra Options" entry (like "-pce.cdbios /path/to/SYSCARD3.PCE").

Then under the "Engine" tab, choose "PC-Engine (TurboGrafx-16)" for the Backend.

Then, in the "ROM file" dropdown, select the .CUE sheet / .ISO file to load.

It should start the PCE CD bios, and then the game. :)

---

### Post by MonkeeSage on 2008-06-11
You still here disturbedite?

---

### Post by disturbedite on 2008-06-11
yeah. what's up?

---

### Post by Cresho on 2008-06-15
nevermind

---

### Post by BigSilly on 2008-06-15
Holy cow!

Just downloaded your .deb from Source Forge, and wow! Fantastic achievement. Just wanted to add my thanks for this, and post up my gratitude. I love Mednafen. It's one of the very best emus for Linux, but boy, did it need this wonderful frontend!

My thanks again for making this. Well done MonkeeSage!

:guitar:

---

### Post by MonkeeSage on 2008-06-21
Hi peeps.

Sorry for the delay, but this time my freakin hard drive started to die on me. The heads started clicking and it would spin up and down really fast and make a whining noise. Then it started getting file system errors. Then kernel panics. Then not even being detected by the bios. :( I finally got another drive and got everything reinstalled, and luckily got my old drive to run as a slave for long enough to pull all my important stuff off it (whew!).

So, yeah...anyway:


@BigSilly:

Glad you're enjoying it. :)


@disturbedite:

> **MonkeeSage said:**
> Try this dry run (it won't actually install anything, just do the depgraph and brokeness checking and such) and tell me if apt-get still complains about dependencies:

```
apt-get --dry-run install python-configobj python-glade2 python-gtk2 python2.4-cairo python2.4-gobject python2.4-numeric python2.5-cairo python2.5-gobject python2.5-numeric
```

*Ps. Yes, oddly, python-gtk2 really does depend on both the 2.5 and 2.4 versions of those packages[[1]]("http://packages.ubuntu.com/intrepid/python-gtk2")*

Thanks.


@KDE users:

You guys may be interested in the [gtk-qt-engine]("http://packages.ubuntu.com/search?keywords=gtk-qt-engine")([-kde4]("http://packages.ubuntu.com/search?keywords=gtk-qt-engine-kde4")) package. It's a GTK2 theme engine that uses QT3 (or QT4) widgets; so, in theory, your GTK2 apps (like mfe) will look the same as your KDE / QT apps. I assume that you just apt-get install it (or use synaptic or whatever), then use the gnome / xfce utilities for setting the GTK theme (or a stand-alone program like the one from the gtk-chtheme package).

---

### Post by disturbedite on 2008-06-21
@ MonkeeSage, i already use gtk-qt-engine & know about gtk-chtheme.

i recently jumped ship to opensuse though. it is a billion times better than (k)ubuntu in some ways.

---

### Post by MonkeeSage on 2008-06-21
> **disturbedite said:**
> @ MonkeeSage, i already use gtk-qt-engine & know about gtk-chtheme.

i recently jumped ship to opensuse though. it is a billion times better than (k)ubuntu in some ways. i do hope at some point someone can package your frontend for opensuse.

Ah, well no worries.

You can also just run mfe directly without installing it (you still of course need the dependencies: configobj, pygtk, ...).

To run it directly, get the tarball and extract it somewhere, cd into the directory and run ./__init__.py. The only thing it will touch outside of that install directory is to write a config file to ~/.mednafen/mfe.ini, so it won't hurt anything to run it this way.

---

### Post by fktt on 2008-06-28
ooh, nice, just what i was looking for, wonder if the deb works on feisty.. :/

---

### Post by MonkeeSage on 2008-06-28
> **fktt said:**
> ooh, nice, just what i was looking for, wonder if the deb works on feisty.. :/

Haven't tested it, but if the requirements are met (should be, I think), it will install fine on Feisty. Please let me know if it doesn't.

---

### Post by hernyman on 2008-06-29
Great software, simple and makes easier the use of Mednafen (another great software!)

Thanks!

---

### Post by cova on 2008-06-29
love this sweet little gui. cant wait for versions with things like cheat codes on too! keep up the good work!
Ben

---

### Post by MonkeeSage on 2008-06-30
> **cova said:**
> love this sweet little gui. cant wait for versions with things like cheat codes on too! keep up the good work!
Ben

Thanks! Glad you're enjoying it. Since I'm working on several other projects as well as this one (and also getting ready to relocate), it will probably be a couple weeks before I integrate the input configuration stuff, and even longer before I get to the cheat code editor.

*Ps.* If anyone wants to contribute to the project, I'll be happy to grant SVN rights.

---

### Post by abelthorne on 2008-08-09
Hello,
I just tried going to the project web page on SourceForge ([http://sourceforge.net/projects/mednafenfe/](http://sourceforge.net/projects/mednafenfe/)) and I get an error message "Invalid project".
Has it been abandoned or is there a problem with SF ?

---

### Post by DoktorSeven on 2008-08-09
> **abelthorne said:**
> Hello,
I just tried going to the project web page on SourceForge ([http://sourceforge.net/projects/mednafenfe/](http://sourceforge.net/projects/mednafenfe/)) and I get an error message "Invalid project".
Has it been abandoned or is there a problem with SF ?

Works fine here, maybe it was a momentary glitch with SF.

---

### Post by disturbedite on 2008-08-23
i don't suppose anyone could package this for opensuse 11 i586?

---

### Post by MEGAMANULTIMATE on 2008-10-22
Hi, I'm having a problem with mfe, and I can't fix it for the life of me. It happened recently...any ideas? Here's what happened:

matthew@matthew-laptop:~$ mfe
location: /usr/lib/xulrunner-1.9.0.3/libxpcom.so 
before 3
Traceback (most recent call last):
  File "/usr/bin/mfe", line 6, in <module>
    mfe.MednafenFE()
  File "/home/sage/mydocs/devel/projects/mfe-0.1.0/mednafenfe/debian/mednafenfe/usr/lib/python2.5/site-packages/mfe/mfe.py", line 36, in __init__
  File "/home/sage/mydocs/devel/projects/mfe-0.1.0/mednafenfe/debian/mednafenfe/usr/lib/python2.5/site-packages/mfe/mfeutil.py", line 58, in __init__
  File "/home/sage/mydocs/devel/projects/mfe-0.1.0/mednafenfe/debian/mednafenfe/usr/lib/python2.5/site-packages/mfe/mfeutil.py", line 69, in locate
OSError: [Errno 2] No such file or directory: '/usr/local/bin'

Any help at all would be greatly appreciated. (Oh, and distubedite, thanks for the directions.)

---

### Post by fatblueduck on 2008-11-04
Hi there,

I've been using this program for a while on Ubuntu. Its very useful.

I just wanted to let you know that it is not compatible with python 2.6. Please add the code that allows operable 2.6 syntax for pre-2.6 python and update the syntax.

Thanks :)

---

### Post by buckeyered80 on 2008-11-06
Awesome front end.  I am surprised that mednafen was able to get the fullscreen video scaling correct without any tweaking....very cool!

---

### Post by MonkeeSage on 2008-11-19
@MEGAMANULTIMATE:

That is funky. You get weird paths (paths from *my* computer) and I can't find anything that hardcodes any paths (let alone '/usr/local' paths). What version of mfe are you using? Is it the .deb version or the tarball?


@fatblueduck:

What breaks with python 2.6? Can you post a traceback, please.

---

### Post by Mega_Mike on 2008-11-19
Just try this out on a fresh install of Ubuntu 8.10 Intrepid.  Works flawlessly and I am up in playing in seconds.  Excellent work man!

Now I just gotta figure out how to remap the keyboard layout...

*EDIT*
Just figured out to map inputst.  Just press alt+shift+1 while in game
F5 to save, F7 to load.  thats all I need to know to game!


Question.  I'm playing Dracula X now.  The emulation is great but the music is really fast.  Anybody have a fix for this?

*EDIT*

Figured out the music sync/fast problem.  I encoded the wavs for the game inproperly.  This command fixed it.
sox Track01.mp3 -r 44100 -c 2 Track01.wav resample

---

### Post by Mega_Mike on 2008-11-22
Throwing in one more feature request.  It would be nice to be able to point to the system card bios (for PCE CD emulation) through the gui (i.e. set the pce.cdbios variable in the mednafen.cfg file).

---

### Post by MonkeeSage on 2008-11-23
> **Mega_Mike said:**
> Throwing in one more feature request.  It would be nice to be able to point to the system card bios (for PCE CD emulation) through the gui (i.e. set the pce.cdbios variable in the mednafen.cfg file).

In the first tab, at the bottom, is an entry box to set any extra options to pass to mednafen on the command line. You can save them so that every time mfe starts it loads them, and you can clear them from memory (use the buttons right next to the entry box--hover them for tooltips). There is also a button at the far right that will load the mednafen documentation (where the keybindings and command-line options and so forth are given). For your case, use something like this in the extra options: -pce.cdbios "/path/to/bios", and press the save button.

---

### Post by buckeyered80 on 2008-12-12
Hey, I just upgraded to 8.10 Intrepid.  My sound won't work with mednafen anymore.  Is anyone else having that problem?  I've tried alsa and oss...no luck.

---

### Post by buckeyered80 on 2008-12-13
Nevermind, I figured it out.  Opened up the mednafen.cfg:
I had to change the sounddriver to oss and the sounddevice to /dev/dsp1.
I imagine this problem might happen to anyone who is not able to truly disable the onboard sound card, like on my system.

---

### Post by MonkeeSage on 2008-12-15
> **buckeyered80 said:**
> Nevermind, I figured it out.  Opened up the mednafen.cfg:
I had to change the sounddriver to oss and the sounddevice to /dev/dsp1.
I imagine this problem might happen to anyone who is not able to truly disable the onboard sound card, like on my system.

Does this still happen when you set the "Sound Driver" option correctly in the second ("Engine") tab?

---

### Post by buckeyered80 on 2009-03-13
Sorry it took me forever to respond to you, MonkeeSage. Yes, it did not work when I did the GUI sound engine settings.  I had to configure the mednafen.cfg file for some reason.  In fact, I have an update for those who have this problem and come across this post.  

I found that if you install alsa-oss, it should add an adsp0 and 1,2, etc. for each sound device you have.  So, since mine is using adsp1, I made an update to my mednafen.cfg file.

;Select sound driver.
sounddriver oss

;Select sound output device.
sounddevice /dev/adsp1

Cheers!

---

### Post by FaberfoX on 2009-03-18
Thanks for this great app. Just wanted to let you know it doesn't work as is on jaunty, as it defaults to python 2.6.
I simply changed the first line on /usr/bin/mfe to 
#!/usr/bin/python2.5
I can't tell if python2.5 was installed by default on jaunty or was a dep from something else I installed but I'm almost sure it is.

With jaunty just around the corner (and working great btw) maybe you'd want to fix it at sourceforge?

---

### Post by klemperal on 2009-03-23
When using the front end for gameboy color games, it doesn't save the game, or update the .sav.  I tried just using mednafen without the frontend and it saves just fine.  I'm using intrepid by the way.  Any idea what the problem is?

---

### Post by MonkeeSage on 2009-03-26
@buckeyered80:

That's what the "Extra options" box in the "General" tab is for. ;) Add "-sounddevice /dev/adsp1" there and press the save button (little disk icon) to the right of it.

@FaberfoX:

What is currently used (#!/usr/bin/env python) will find the first instance of a an executable file named python on the PATH. If you install 2.6, the installer should overwrite the link in /usr/bin/python to point to /usr/bin/python2.6 and env will find that.

[**Edit:** Oh! I see what you mean. I've got the files in /usr/lib/python2.5. They should go in /usr/lib/python-support/mfe. I'll fix that. New deb will be up soon.]

@klemperal:

Can't reproduce. Maybe you have a permission problem with the directories you're using with the front end? Are you saving to the same place as the back end?

---

### Post by klemperal on 2009-03-26
Maybe I was just using the front end wrong.  The order of doing things, which resulted in the game not being saved, was that I would save the game with the front end still open--then, I would click 'stop' to stop mednafen--then, I would click 'quit' to quit out of the front end.  After that process, the save file didn't register or update.  I changed things up a little, and now my games save just fine.  My new method of quiting out of mednafen(fe) is to save, then hit the escape key to quit mednafen, and finally to click 'quit' to quit the front end.  I'm not sure if this is a bug, or me just using the front end wrong.  In any case, thanks for the reply and the great front end.

---

### Post by MonkeeSage on 2009-03-26
@klemperal:

Wierd. I'll try to reproduce and fix if I can spot the bug.

---

### Post by MonkeeSage on 2009-03-26
OK. [New deb is up](https://sourceforge.net/project/showfiles.php?group_id=229596&package_id=278189&release_id=671223) that installs to /usr/lib/python2.4, /usr/lib/python2.5, and /usr/lib/python2.6 (if they exist).

---

### Post by cloudscream on 2009-04-14
Just want to say thanks to you, MonkeeSage. A fantastic emulator wouldn't be so tasty without a frontend, and your FE just delivers! Nice...;)

---

### Post by MonkeeSage on 2009-04-23
> **cloudscream said:**
> Just want to say thanks to you, MonkeeSage. A fantastic emulator wouldn't be so tasty without a frontend, and your FE just delivers! Nice...;)

Glad you like it. :)

---

### Post by Mega_Mike on 2009-04-24
I just checked back in cuz I upgraded to Jaunty and I needed to grab the latest version of the Front End.  Awesome that you keep this front end so up to date MonkeeSage.  Again, great work and you really should petition to get this awesome app added into the repositories.

---

### Post by MonkeeSage on 2009-04-24
@Mega_Mike:

Thanks. I try. :)

I imagine that eventually it will be added to the repos, but I currently don't have the time (or experience) to be a package maintainer for it in this or any other distro.

---

### Post by buckeyered80 on 2009-05-10
Hey MonkeeSage,
I was able to get mfe running successfully on Ubuntu and Mandriva, but I can't get it to compile on Opensuse 11.1.  Do you know a way to get it to work there?  I have all the dependencies, I am just getting a few comipile errors after I run the setup.

---

### Post by Grishka on 2009-05-10
> **buckeyered80 said:**
> Hey MonkeeSage,
I was able to get mfe running successfully on Ubuntu and Mandriva, but I can't get it to compile on Opensuse 11.1.  Do you know a way to get it to work there?  I have all the dependencies, I am just getting a few comipile errors after I run the setup.

post your errors. there's no way to diagnose otherwise.

---

### Post by MonkeeSage on 2009-05-10
> **buckeyered80 said:**
> Hey MonkeeSage,
I was able to get mfe running successfully on Ubuntu and Mandriva, but I can't get it to compile on Opensuse 11.1.  Do you know a way to get it to work there?  I have all the dependencies, I am just getting a few comipile errors after I run the setup.

If it worked in Mandriva (I'm assuming you used the python distutils method with setup.py in Mandriva rather than using alien to convert the deb to an rpm?) then it should work fine in OpenSuSe. I had a box with OpenSuSe 11 on it a few months ago and I recall that it worked fine.

As Grishka says, I can't even hazard a guess as to the problem without seeing the installation errors.

---

### Post by buckeyered80 on 2009-05-10
Ok, here are the errors.  It didn't complain about dependencies, I made sure I had all of them.  
```
$ mfe
Traceback (most recent call last):
  File "/usr/local/bin/mfe", line 6, in <module>
    mfe.MednafenFE()
  File "/usr/local/lib/python2.6/site-packages/mfe/mfe.py", line 29, in __init__
    self.config = mfeutil.Config()
  File "/usr/local/lib/python2.6/site-packages/mfe/mfeutil.py", line 132, in __init__
    self.config["default"]["snap_path_sar"]    = False
  File "/usr/lib/python2.6/site-packages/configobj.py", line 583, in __getitem__
    val = dict.__getitem__(self, key)
KeyError: 'default'

```

Yes, I did use the python setup.py install method.

---

### Post by MonkeeSage on 2009-05-10
> **buckeyered80 said:**
> Ok, here are the errors.  It didn't complain about dependencies, I made sure I had all of them.  
```
$ mfe
Traceback (most recent call last):
  File "/usr/local/bin/mfe", line 6, in <module>
    mfe.MednafenFE()
  File "/usr/local/lib/python2.6/site-packages/mfe/mfe.py", line 29, in __init__
    self.config = mfeutil.Config()
  File "/usr/local/lib/python2.6/site-packages/mfe/mfeutil.py", line 132, in __init__
    self.config["default"]["snap_path_sar"]    = False
  File "/usr/lib/python2.6/site-packages/configobj.py", line 583, in __getitem__
    val = dict.__getitem__(self, key)
KeyError: 'default'

```

Yes, I did use the python setup.py install method.

Hmm. That's strange. Can you post the content of ~/.mednafen/mfe.ini please. Also, try removing that file and running mfe again.

---

### Post by buckeyered80 on 2009-05-10
Hmm...
Interestingly enough, there is no mfe.ini in that folder...here are the contents of that folder.
```
/home/rob/.mednafen # ls
cheats  gameinfo  mcm  mcs  mednafen.cfg  sav  snaps

```

---

### Post by MonkeeSage on 2009-05-11
> **buckeyered80 said:**
> Hmm...
Interestingly enough, there is no mfe.ini in that folder...here are the contents of that folder.
```
/home/rob/.mednafen # ls
cheats  gameinfo  mcm  mcs  mednafen.cfg  sav  snaps

```


That is strange. The configuration file (mfe.ini) is supposed to be generated if it doesn't exist. I'll look into that tomorrow. Since it worked on Mandriva, I'm wondering if, perhaps, it's a permissions issue--can you write to ~/.mednafen from the same user you're running mfe with (e.g., does *touch ~/.mednafen/mfe.ini* work)?

---

### Post by buckeyered80 on 2009-05-11
```
[/HTML]$ touch ~./mednafen/mfe.ini
```
Does not return anything in root, but it does say access denied from my username.  However, I was able to create a blank file in the .mednafen folder and named it mfe.ini.  Now it returns:

```
$ mfe
/usr/local/lib/python2.6/site-packages/mfe/mfe.py:32: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  xml = glade.XML(mfeutil.gladefile)
Traceback (most recent call last):
  File "/usr/local/bin/mfe", line 6, in <module>
    mfe.MednafenFE()
  File "/usr/local/lib/python2.6/site-packages/mfe/mfe.py", line 42, in __init__
    self.setup_ui()
  File "/usr/local/lib/python2.6/site-packages/mfe/mfe.py", line 237, in setup_ui
    self.snapcheck.set_active(self.config["snap_path_sar"])
  File "/usr/local/lib/python2.6/site-packages/mfe/mfeutil.py", line 181, in __getitem__
    return self.config["default"][key]
  File "/usr/lib/python2.6/site-packages/configobj.py", line 583, in __getitem__
    val = dict.__getitem__(self, key)
KeyError: 'snap_path_sar'

```

---

### Post by MonkeeSage on 2009-05-12
> **buckeyered80 said:**
> ```
[/HTML]$ touch ~./mednafen/mfe.ini
```
Does not return anything in root, but it does say access denied from my username.

That's quite strange. From your user account try removing ~/.mednafen/mfe.ini, then issue the following command to take ownership of the ~/.mednafen directory:

```
$ sudo chown -R $USER:$USER ~/.mednafen
```

Then see if mfe works properly.

---

### Post by buckeyered80 on 2009-05-12
Ok I entered that command and it did change my username to the owner of the .mednafen folder.  But when I run mfe, I get the same errors.  Darn, tough one eh?

---

### Post by MonkeeSage on 2009-05-13
> **buckeyered80 said:**
> Ok I entered that command and it did change my username to the owner of the .mednafen folder.  But when I run mfe, I get the same errors.  Darn, tough one eh?

Yeah. :\ Judging by the fact that it worked for me with OpenSuSe, and worked for you on Mandriva, and ~/.mednafen wasn't owned by your user account already, I definitely think it's a permissions problem. Maybe try chown'ing /home and /home/$USER as well. I recall having some problems in OpenSuSe with Samba shares under /home due to permissions. I can't recall the exact problem ATM, but I think it was because /home (and /home/*) was not globally readable / writeable.

---

### Post by buckeyered80 on 2009-05-16
Hey MonkeeSage,

Thanks for helping me out with that.  I didn't resolve the problem because there was a .gvfs folder that would not let me take ownership of the /home folder. I actually decided to just stick with Mandriva on this system, because Opensuse seemed to have an issue with my network card as well.  I think I'll stick with Ubuntu and Mandriva.  Thanks anyway!

---

### Post by Cresho on 2009-06-06
I can't believe this is still being worked on!  THanks dude!
:popcorn:

---

### Post by MonkeeSage on 2009-06-09
> **Cresho said:**
> I can't believe this is still being worked on!  THanks dude!
:popcorn:

NP! :)

I'm still keeping it up-to-date, but I haven't been working on features. I've actually been working on a new joystick-to-keyboard mapper (a la joy2key) with a GTK configuration interface and profile support. I've pretty much got it 99% done (just need to write a calibrator and test the analog mapping a bit more). I plan to eventually integrate that interface into mfe, and add a cheat code editor, but thats not high on my priority list, so don't expect it any time soon (or ever, heh...I'm kinda lazy :p).

---

### Post by loungedaddy on 2009-06-09
Best frontend ever :cool:

---

### Post by klemperal on 2009-06-22
I'm having some trouble making _windowed_ mednafen the size I want through the front end.  I see that changing the x and y scale make things taller or wider, but I'm looking for a more exact size (920-700).  When I try putting those settings into the height and width areas below the x and y scale it doesn't seem to have any affect.  What am I doing wrong?  Thanks in advance.

---

### Post by MonkeeSage on 2009-06-24
> **klemperal said:**
> I'm having some trouble making _windowed_ mednafen the size I want through the front end.  I see that changing the x and y scale make things taller or wider, but I'm looking for a more exact size (920-700).  When I try putting those settings into the height and width areas below the x and y scale it doesn't seem to have any affect.  What am I doing wrong?  Thanks in advance.

According to the [mednafen docs](http://mednafen.sourceforge.net/documentation/), setting -<system>.xres x / -<system>.yres y (which is what the width / height spinners do) sets "the desired horizontal/vertical resolution when in fullscreen mode." I will update the UI to reflect that in the next few days (they will be grayed out unless the fullscreen option is checked on the first page). The x / y scale values can apparently be real numbers (i.e., decimals)--I'll also have to fix that in the UI--right now it only allows whole numbers. Even though it is not pixel-perfect, with the scale factor being capable of real numbers, you should be able to get pretty close to what you want if you play with it a bit (e.g., 1.1250 / 1.1666 if native resolution is 800 / 600 == 920 / 700 result).

---

### Post by klemperal on 2009-06-24
Thats great news about the x/y scale being able to be set to real numbers.  I eagerly await the update.

Thanks for the great front end.

---

### Post by MonkeeSage on 2009-07-02
> **klemperal said:**
> Thats great news about the x/y scale being able to be set to real numbers.  I eagerly await the update.

Thanks for the great front end.

I've not forgotten about this, I've just been busy. I'll get a new package up soon (probably after this weekend). :)

---

### Post by gigabeast on 2009-07-10
I have same problem with buckeyered80 in Fedora 11. But I have working mfe in Fedora 10. Then I did these to get mfe working in F11 :
1. Disable selinux (I'm not sure whether this is one of the problems)
2. Clean previous mfe installation:
# rm -rf /usr/share/mfe/
# rm /usr/share/pixmaps/mfe.png
# rm -rf /usr/lib/python2.6/site-packages/mfe/
# rm /usr/lib/python2.6/site-packages/mfe-0.1.4-py2.6.egg-info
# rm /usr/bin/mfe
# rm /usr/share/applications/mfe.desktop
3. Reinstall mfe
#./setup.py install
4. Copy .mednafen folder from F10 home directory to F11 home directory
5. I have different username ini F10 and F11. So I have to change the content of mednafen.cfg and mfe.ini file (my username in F10 is gigabeast and F11 is bayu)
$ sed -i -e 's/gigabeast/bayu/gi' ~/.mednafen/mednafen.cfg
$ sed -i -e 's/gigabeast/bayu/gi' ~/.mednafen/mfe.ini
6. Run mfe

---

### Post by kwash on 2009-07-13
I'm also having the error reported by buckeyered80 when installed with 'python setup.py install'.

Here is it:

```
Traceback (most recent call last):
  File "/usr/bin/mfe", line 6, in <module>
    mfe.MednafenFE()
  File "/usr/lib/python2.6/site-packages/mfe/mfe.py", line 29, in __init__
    self.config = mfeutil.Config()
  File "/usr/lib/python2.6/site-packages/mfe/mfeutil.py", line 132, in __init__
    self.config["default"]["snap_path_sar"]    = False
  File "/usr/lib/python2.6/site-packages/configobj.py", line 583, in __getitem__
    val = dict.__getitem__(self, key)
KeyError: 'default'

```


Also, calling it with '__init__.py' or 'mfe/mfe.py' gives me this similar error:

```
Traceback (most recent call last):
  File "./mfe.py", line 645, in <module>
    mfe = MednafenFE()
  File "./mfe.py", line 29, in __init__
    self.config = mfeutil.Config()
  File "/home/kwash/temp1/mfe-0.1.4/mfe/mfeutil.py", line 132, in __init__
    self.config["default"]["snap_path_sar"]    = False
  File "/usr/lib/python2.6/site-packages/configobj.py", line 583, in __getitem__
    val = dict.__getitem__(self, key)
KeyError: 'default'

```

Using:
Fedora 11 32-bit with Kernel 2.6.29.5 (PAE)
Python 2.6 (r26:66714)
GCC 4.4.0 20090506 (Red Hat 4.4.0-4)

---

### Post by minder on 2009-09-16
```
Traceback (most recent call last):
  File "/usr/bin/mfe", line 6, in <module>
    mfe.MednafenFE()
  File "/usr/lib64/python2.6/site-packages/mfe/mfe.py", line 29, in __init__
    self.config = mfeutil.Config()
  File "/usr/lib64/python2.6/site-packages/mfe/mfeutil.py", line 132, in __init__
    self.config["default"]["snap_path_sar"]    = False
  File "/usr/lib64/python2.6/site-packages/configobj.py", line 583, in __getitem__
    val = dict.__getitem__(self, key)
KeyError: 'default'

```

Using:
Gentoo 64-bit with Kernel 2.6.30-r4
Python 2.6 
GCC 4.3.2 (Gentoo 4.3.2-r3 p1.6, pie-10.1.5)

---

### Post by buckeyered80 on 2009-11-07
Yep...the problem is back for me also.  I just upgraded to Mandriva 2010.0. It seems something has changed in the distro...before, MonkeeSage went through some permissions troubleshooting steps with the /home directory...however, now there is no .mednafen folder in the /home directory.  I wonder if that has anything to do with this.  Hmm??  MonkeeSage, any ideas?

---

### Post by buckeyered80 on 2009-11-08
Here is the output:

```
$ mfe
Traceback (most recent call last):
  File "/usr/bin/mfe", line 6, in <module>
    mfe.MednafenFE()
  File "/usr/lib/python2.6/site-packages/mfe/mfe.py", line 29, in __init__
    self.config = mfeutil.Config()
  File "/usr/lib/python2.6/site-packages/mfe/mfeutil.py", line 132, in __init__
    self.config["default"]["snap_path_sar"]    = False
  File "/usr/lib/python2.6/site-packages/configobj.py", line 583, in __getitem__
    val = dict.__getitem__(self, key)
KeyError: 'default'

```

I have made sure that I am the owner of /home /home/$user and /home/$user/.mednafen

---

### Post by MonkeeSage on 2009-11-11
> **buckeyered80 said:**
> Here is the output:

```
$ mfe
Traceback (most recent call last):
  File "/usr/bin/mfe", line 6, in <module>
    mfe.MednafenFE()
  File "/usr/lib/python2.6/site-packages/mfe/mfe.py", line 29, in __init__
    self.config = mfeutil.Config()
  File "/usr/lib/python2.6/site-packages/mfe/mfeutil.py", line 132, in __init__
    self.config["default"]["snap_path_sar"]    = False
  File "/usr/lib/python2.6/site-packages/configobj.py", line 583, in __getitem__
    val = dict.__getitem__(self, key)
KeyError: 'default'

```

I have made sure that I am the owner of /home /home/$user and /home/$user/.mednafen

Hmm...very strange. Give me a few days to see what I can turn up. I'm pretty busy lately, but I'm still here. :)

---

### Post by MonkeeSage on 2009-11-12
> **MonkeeSage said:**
> Hmm...very strange. Give me a few days to see what I can turn up. I'm pretty busy lately, but I'm still here. :)

OK, I fixed the problem. New tarball is up on SF (ver 0.1.5). I'll try to get a new deb for it up by tomorrow evening.

[**Edit:**] New deb is up now. [Direct link](http://sourceforge.net/projects/mednafenfe/files/mednafenfe_0.1.5-0ubuntu1_all.deb/download)

---

### Post by buckeyered80 on 2009-11-14
Thanks MonkeeSage.  It works!

---

### Post by buckeyered80 on 2009-11-20
Wait...I hate to say this.  I spoke too soon.  Error on compile.  Here it is:

```
[root@localhost mfe-0.1.5]# python setup.py install
running install
running build
running build_py
creating build
creating build/lib
creating build/lib/mfe
copying mfe/mfeutil.py -> build/lib/mfe
copying mfe/mfeconst.py -> build/lib/mfe
copying mfe/mfe.py -> build/lib/mfe
copying mfe/__init__.py -> build/lib/mfe
running build_scripts
creating build/scripts-2.6
copying and adjusting scripts/mfe -> build/scripts-2.6
changing mode of build/scripts-2.6/mfe from 644 to 755
running install_lib
running install_scripts
copying build/scripts-2.6/mfe -> /usr/bin
changing mode of /usr/bin/mfe to 755
running install_data
error: can't copy 'resources/mfe.glade': doesn't exist or not a regular file
```

---

### Post by MonkeeSage on 2009-11-20
> **buckeyered80 said:**
> Wait...I hate to say this.  I spoke too soon.  Error on compile.  Here it is:

Doh. Fixed now. New package (and .deb) up [here]("http://sourceforge.net/projects/mednafenfe/files/mfe-0.1.6.tar.gz/download"). This version also properly disables the width/height spinners unless fullscreen is checked and labels them "FS Width/Height" to avoid confusion.

---

### Post by buckeyered80 on 2009-11-21
Yep.  You sure did fix it.  Dang you're good.  Ok I can confirm it now works on Mandriva 2010.0.  It should probably work on Suse and Fedora now too.

---

### Post by Saiko Berry on 2010-02-02
Mednafen's front end isnt saving for me. Its only creating save files when I have autosave on and when I use the "Save" option in games its not saving anything.. but at the same time it is. I have to use Save States. I tried using the location of rom checkbox for it and moving the folder around to see if the save file appears but I can't get it to.

And whenever I DO end up saving when I go into the game it says my file is corrupted, but it loads the save anyways. This happens every time.

---

### Post by MonkeeSage on 2010-02-18
> **Saiko Berry said:**
> Mednafen's front end isnt saving for me. Its only creating save files when I have autosave on and when I use the "Save" option in games its not saving anything.. but at the same time it is. I have to use Save States. I tried using the location of rom checkbox for it and moving the folder around to see if the save file appears but I can't get it to.

And whenever I DO end up saving when I go into the game it says my file is corrupted, but it loads the save anyways. This happens every time.

Mednafenfe is just a launcher for mednafen. It just forms a command line, based on the options selected in the GUI, and then passes the command line to the mednafen binary. Any wierdness with saving or such like, would have to be caused by mednafen itself. What happens if you just run mednafen from the command line?

---

### Post by punkrockguy318 on 2010-02-18
TC:

Hey, I'm very impressed with your front end!  I did the same for fceu back in the day when it was command line only.

As a fceuX dev, fceuX is obviously my NES emulator of choice, but this is really nicely done regardless.  It's nice that now the community can have options between two great emulators (without muddling around with the command line)

Best of luck to your project!  You should push to get this in universe!

---

### Post by litemirrors on 2010-02-18
Here is the one punky is working on for another emulator [http://ubuntuforums.org/showthread.php?t=971455&page=2](http://ubuntuforums.org/showthread.php?t=971455&page=2)

Hey punky :D this is amusing to me to see u post here, glad I could show you a new front end ya didn't know about :S I agree with ur sentiments!

---

### Post by punkrockguy318 on 2010-02-18
> **litemirrors said:**
> Here is the one punky is working on for another emulator [http://ubuntuforums.org/showthread.php?t=971455&page=2](http://ubuntuforums.org/showthread.php?t=971455&page=2)

Hey punky :D this is amusing to me to see u post here, glad I could show you a new front end ya didn't know about :S I agree with ur sentiments!

Yeah, I almost forgot about this emulator and I didn't know this front-end existed.  Very good to know that I'm not the only person working on the NES emu scene for linux

---

### Post by slave-zeo on 2010-09-02
RISE FROM YOUR GRAVE!

I wanted to try out mfe but couldn't find a recent package of mednafen. I compiled the latest source version (0.8.D.2) from the official site and packaged it up for download. It's a .deb for easy installation and uninstallation.

It's located at [http://alphaboxmedia.net/home/?p=194](http://alphaboxmedia.net/home/?p=194)

:KS It works just peachy with mfe 0.1.6 :KS

---

### Post by Bill_Gates on 2010-09-27
@MonkeeSage

Can you update your frontend to support latest mednafen-wip release? It has support for SNES, Genesis and Virtual Boy. Thanks.

[http://forum.fobby.net/index.php?t=msg&th=566&start=0&](http://forum.fobby.net/index.php?t=msg&th=566&start=0&)

---

### Post by mister_playboy on 2010-10-01
Is it possible to add input configuration to the GUI?  The Alt+Shift+1 method is braindead.

Press the same button to move on the next input configuration?  Sounds simple, but I certainly can't get it to work correctly.

---

### Post by PirateChef on 2012-07-11
This program recently quit working for me, after an upgrade. Maybe something in a newer version of Python broke it? Here are the errors I'm getting from the command line:

```
$ ./__init__.py 
Traceback (most recent call last):
  File "./__init__.py", line 6, in <module>
    mfe.MednafenFE()
  File "/home/pants/Downloads/mfe-0.1.7/mfe/mfe.py", line 44, in __init__
    self.setup_ui()
  File "/home/pants/Downloads/mfe-0.1.7/mfe/mfe.py", line 248, in setup_ui
    self.snapcheck.set_active(self.config["snap_path_sar"])
  File "/home/pants/Downloads/mfe-0.1.7/mfe/mfeutil.py", line 186, in __getitem__
    return self.config["default"][key]
  File "/usr/lib/python2.7/dist-packages/configobj.py", line 567, in __getitem__
    val = dict.__getitem__(self, key)
KeyError: 'snap_path_sar'
```

(Note: I'm using mfe 0.1.7. I tried installing 0.1.6, but that doesn't work either.)

---

### Post by Perfect Storm on 2012-07-14
Very old thread.

Thread closed.

---

