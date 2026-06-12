---
title: "FoF rf-mod 4.0 released!!"
date: 2007-09-05
forum: Gaming &amp; Leisure
---

### Post by Naegling23 on 2007-09-05
Well, sort of.  The windows version is complete, the linux version still needs to be compiled.

[http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=11;t=11473]("http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=11;t=11473")

can anyone help rogue-f, and the rest of the FoF linux junkies out?

---

### Post by buttons on 2007-09-10
> **Naegling23 said:**
> Well, sort of.  The windows version is complete, the linux version still needs to be compiled.

[http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=11;t=11473]("http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=11;t=11473")

can anyone help rogue-f, and the rest of the FoF linux junkies out?

Holy crap I didn't even notice!  I'll take a look at it this evening and see if I can compile it from syberdave's pyaminith source, etc.  If not I'll just bother him ;)

Wow I can't waaaiiiit

---

### Post by buttons on 2007-09-10
Ugh.  This is the very worst program to try to compile, ever.

So far I've got Amanith and PyAminith compiled, and the program finally builds.  However, I'm getting this error:

```
Traceback (most recent call last):
  File "/opt/cx-freeze/initscripts/Console.py", line 27, in <module>
    exec code in m.__dict__
  File "src/FretsOnFire.py", line 36, in <module>
  File "src/GameEngine.py", line 24, in <module>
  File "/usr/lib/python2.5/site-packages/OpenGL/__init__.py", line 18, in <module>
    __set_attributes()
  File "/usr/lib/python2.5/site-packages/OpenGL/__init__.py", line 14, in __set_attributes
    __version__ = string.strip(open(filename).read())
IOError: [Errno 20] Not a directory: '/home/buttons/Desktop/rfmod/dist/FretsOnFire.bin/OpenGL/version'

```

Seems simple, but I've been so irritated with this program I'm going to quit for now.

---

### Post by Naegling23 on 2007-09-11
not sure if any of this will help

[http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=11;t=4896](http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=11;t=4896)

its for windows, but it might give you an idea, it also mentions an open-gl bug/problem.

by the way, how did you get amanith, pyamanith, and cx_freeze installed and running?  I cant get any of them to work.

---

### Post by buttons on 2007-09-11
> **Naegling23 said:**
> not sure if any of this will help

[http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=11;t=4896](http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=11;t=4896)

its for windows, but it might give you an idea, it also mentions an open-gl bug/problem.

by the way, how did you get amanith, pyamanith, and cx_freeze installed and running?  I cant get any of them to work.

Thanks!  I'll take a look.

I'm on Arch atm, and cx_freeze is in our repos.  Keep in mind that you only have to install it, and then edit the amanith makefile to point to "FreezePython".  Otherwise it gets confused.

I got amanith and pyamanith to compile by taking a look at the gentoo ebuilds and using their patches.  Kinda.  Here's the breakdown:

Their fretsonfire ebuild is [here]("http://bugs.gentoo.org/show_bug.cgi?id=143388").  Note they have a pyxml patch for distros with pyxml 0.8.4, which includes Arch.

An amanith ebuild is located [here]("http://osmirrors.cerias.purdue.edu/pub/gentoo/portage/media-libs/amanith/"), with patch in the files dir.  Actually I kinda wish I'd seen that one first, as the ebuild I found on google didn't have the GCC 4.1 patch, which I found on the [amanith forums]("http://www.amanith.org/forum/viewtopic.php?pid=118").  It also tries to use QT4.  For the record, I compiled it with QT3 and it compiled fine.  Not that rfmod 4 works yet, but I don't think that's related from the stack trace there.

And the PyAmanith ebuild is [here]("http://mirrors.usc.edu/pub/linux/distributions/gentoo/dev-python/PyAmanith/"), along with the compile patch in the files dir as always.  The ebuild has some funny comments, too.  Alas, the frets dev hosting the pyamanith source has since taken down his site (or it was forced down, I forget the story).  The unmodified source for pyamanith is currently available from syberdave's site, [here]("http://syberdave.net/archive/PyAmanith-0.3.34.tar.gz").

Again, these ebuilds basically point to download locations and any tricks to getting compile to work.  They have a pretty simple syntax, things like ${PV} is the package version, etc.

And after all that I have an opengl bug.  Sigh.

EDIT:  How quickly we forget the stupid things.  Amanith "working" is a total misnomer.  It has no make install that does anything useful.  There's no set place to put the include files it's got (so pyamanith can find them), so I had to copy them over to the pyamanith build dir manually.  In fact, I had to do the same with the pyamanith source they've got squirreled away in some "changes" directory.  Basically, you try to build pyamanith once (after patching), watch the errors to see where it's looking for the source, and cp -r everything in the amanith include dir and everything in the pyamanith /changes and it should build.  Amanith also has nowhere to put its libs once compiled.  It just puts them in its "lib" dir.  Since the fretsonfire makefile expects them in /usr/local/lib, I just put all the new libamanith stuff (including symlinks) in there.  And the devs wonder why like two distros ship amanith natively. /RANT

---

### Post by buttons on 2007-09-11
VICTORY!  Thanks for that link!  There were other problems, but that got me into the game at least, and the rest were pretty easy.

It runs!  There are flames and all sorts of goodies!

It's slow as %)(#*$!

Rig:
AMD x2 2.6 Ghz
Geforce 7800GT

Compared to RF-mod 3.5, this RF-mod 4.0 runs like poop.  Okay, not complete poop, but the best and most playable (I like silky smooth) framerate has been 640x480 with Noob mods (COME WITH RFMOD! YAY!) and no flames or note sfx.  Pretty boring, but it works.

Turning up the detail, though, WOW.  This version is pretty. The flames especially are amazing.

I just need to package this and it's yours.

---

### Post by buttons on 2007-09-11
Here you go: [Links below]("http://ubuntuforums.org/showthread.php?t=543515&p=3349720")

This is a fully playable release!  Just extract the archive and run FretsOnFire.  If you put this in your old fretsonfire mod directory it will blink at you innocently.

Tips:
[LIST]
[*]rm -rf ~/.fretsonfire or move it if you want it for posterity
[*]Move your songs dir to yourinstallpath/data/
[*]If you want black HOPO notes and/or the mythical orangey fret of doom, you need only go to Game Settings->Mods and select these to On.
[/LIST]

You MUST have your songs dir in /data (symlinked is OK) or it'll just sit there until you kill it from another virtual terminal.

If something breaks post here and I'll cry.  And maybe help you.

---

### Post by Naegling23 on 2007-09-11
cool, thanks for the link...well, when you get it posted anyway.

the looks is why I was trying to get this working so badly.  I started playing the game when it was 1.2 something, then I started using rf-mod, rf-mod had some nice effects, but they were different than the 1.2 stuff, all in all they were about equal, but now with rf-4, we can have the best of both worlds, plus some other mods (like flamed notes) that were windows only mods (for me anyway...since I cant get it to compile).

thanks for your help, the FoF community thanks you.

you might also want to send this to rogue_F on the fretsonfire.net forums, I know he was looking for someone the compile the linux version.

---

### Post by buttons on 2007-09-11
Unfortunately I just tried to run it in my ubuntu install and it fails, apparently because feisty's openssl is an older version.  EDIT: I'm very frustrated now :(

Download link back up.  Can someone test with gutsy?  Until I figure out how to compile this with an earlier openssl, I think gutsy is the only platform it'll work on.

---

### Post by buttons on 2007-09-11
Whoop!  All done!

Note - i686 only for the moment.  This *is* a 64-bit box, but I don't have any 64-bit linux installations currently.  So...someone else do it.

[Download - Feisty]("http://rapidshare.com/files/55040296/rfmod-4-linux-i686-feisty.tar.bz2.html")

[Download - Gutsy]("http://rapidshare.com/files/55005134/rf-mod-4-linux-i686.tar.bz2.html")

See above for notes about this release.  Specifically the part about adding a songs folder and deleting your current ~/.fretsonfire directory.  You've been warned!

Have fun! :guitar:

---

### Post by Naegling23 on 2007-09-11
wow, this is amazing, runs great, looks great.

thanks for all your work.  All of us ubuntu/FoF players, who for some reason all live in NJ, extend our greatest thanks.

---

### Post by khornerz on 2007-09-21
which version of rf-mod 4. the debs are?

I think the last win32 version is 4.12...

Can you make a little how-to showing us to compile it ourselves?

Thanks in advance!

---

### Post by buttons on 2007-09-21
> **khornerz said:**
> which version of rf-mod 4. the debs are?

I think the last win32 version is 4.12...

Can you make a little how-to showing us to compile it ourselves?

Thanks in advance!

To be honest, I'm not at all sure what version it is.  As for the howto, yes I think I'll have to.  So far I've not been able to compile any version that works cross-system, though I've been idly thinking about installing gentoo and seeing if I can reproduce the environment syberdave used initially.

Either way, I'll see if I can get a howto up today or tomorrow.  Be warned: It's absurd.

---

### Post by buttons on 2007-09-21
All right, you'll need the following (might be incomplete, who knows what -dev files I've got on here):

python-all-dev
python-psyco - in the repo
glewpy - [http://glewpy.sourceforge.net/](http://glewpy.sourceforge.net/) requires both pyrex and glew, which are in the repos
python-opengl - repo
pygame - you have this for FoF anyway
python-numeric - repo
python-pyogg, python-pyvorbis - 'po
swig - 'po
libpng-dev, libjpeg-dev
cx_freeze - [http://prdownloads.sourceforge.net/cx-freeze/cx_Freeze-3.0.3-source.tgz?download](http://prdownloads.sourceforge.net/cx-freeze/cx_Freeze-3.0.3-source.tgz?download)
read the instructions and don't forget to build it!  afterwards stick it in /opt/cx-freeze
Amanith - [http://www.amanith.org/download/pafiledb.php?action=file&id=10](http://www.amanith.org/download/pafiledb.php?action=file&id=10)

Then grab at least the gcc4 patch from [http://osmirrors.cerias.purdue.edu/pub/gentoo/portage/media-libs/amanith/files/](http://osmirrors.cerias.purdue.edu/pub/gentoo/portage/media-libs/amanith/files/) The QT4 patch changes configuration settings, and I have no idea what the freetype patch does.  Could fix a gentoo-specific bug.  It isn't needed to *compile*.

Read the amanith docs and build it.  I mean it, read them.  It involves setting several environment variables.  Copy the contents of amanith's /lib into /usr/local/lib using "cp -d libaman* /usr/local/lib" to do it, because that's where fof wants them, and they need to stay symlinks.

PyAmanith - I couldn't let you do this yourself.  It's too obnoxious.  Here, I've attached the sources, complete with the gentoo patches already applied and the include files in the right places.  Just read the readme and build accordingly, it *should* compile.  If not, get the sources and the gentoo patch and good luck.  I posted instructions in an earlier post.

I then unzipped a copy of the 1.2.451 source: [http://downloads.sourceforge.net/fretsonfire/FretsOnFire-src-1.2.451.tar.gz](http://downloads.sourceforge.net/fretsonfire/FretsOnFire-src-1.2.451.tar.gz)

And copied the src from the rfmod package over the src directory, I think.  Then I edited the makefile, which I've included in fofmake.tar.gz, and copied that over the fof one.  Then..uhh..I ran it.  There should be a new dir called dist/  which contains your shiny new game.  Copy a "FretsOnFire" launcher into the directory and see if it runs.

If it gives you the opengl error, the fix is on the site Naegling mentioned.  You just edit the __init__.pyc in /usr/lib/python2.5/site-packages/OpenGL to change __version__ to '2.0.2.01' , then run make again.

As I recall, make crapped out the first or second time complaining about missing things like the tutorial.  It's all there in the rfmod distribution, just in a place make wasn't looking for it at the time.  Just move stuff around until it stops complaining.

TIPS: Basically when compiling this you'll have to remember a time before decent package management.  Your programs, which all come from source packages that put themselves in nonstandard places or simply don't install themselves anywhere at all, will need to be gently guided towards each other so they can mate and have freshly compiled offspring.


Good luck.

OH, I almost forgot.  I patched the rfmod sources with gentoo's pyxml patch.  It's available: [http://bugs.gentoo.org/attachment.cgi?id=104332](http://bugs.gentoo.org/attachment.cgi?id=104332)

---

### Post by khornerz on 2007-09-26
Omfg!!!!!

---

### Post by buttons on 2007-09-26
> **khornerz said:**
> Omfg!!!!!

Is that...good?  :-P

---

### Post by khornerz on 2007-09-27
Ok

here is my answer to your question:

[http://rapidshare.com/files/60399972/RF-mod-4.12-generic.tar.gz.html]("http://rapidshare.com/files/60399972/RF-mod-4.12-generic.tar.gz.html")

I make this compilation because when I use the others in this web (page 1) I got errors... I supose I will not get these now.

It's for feisty an it's 4.12


See you!

---

### Post by khornerz on 2007-10-05
bump!

---

### Post by truptrup on 2007-10-26
Great work porting over these mods for us but i have a problem.
It may be on my end since nobody else has reported any problems but im running Feisty.

This is with both the 4.0 and 4.12 version.
I extract it and delete my .fretsonfire folder. Copy in my symlinked songs folder. then i run it. no mods enabled just to be sure.

I get an error after some songs that says 

____class____ not accessible in restricted mode

 This shows within fof and there is an ok button so i hit enter. Then it goes to the loading screen and seems to hang until i kill the process.

Or it randomly exits after some songs.

the error is

/FretsOnFire/FretsOnFire.bin/View.py:172: DeprecationWarning: integer argument expected, got float
/FretsOnFire/FretsOnFire.bin/View.py:173: DeprecationWarning: integer argument expected, got float
Fatal Python error: (pygame parachute) Segmentation Fault

Any ideas

---

### Post by truptrup on 2007-10-26
I am only using gh1/2/80s songs.

Vanilla 1.2.451 fof runs it fine.

---

### Post by Niklas Schröder on 2007-10-30
yes truptrup, but the point of this mod isn't to make it work, it's to make it "*work*."

maybe i should explain the quotes...  :p

we mod because we can.  we're not attempting to get this mod working to make the program functional, we're trying to install it so we can have the improved functionality and extra eye candy it offers.  ;)

---

### Post by Niklas Schröder on 2007-10-30
ok.  i have a problem here.

when i download the gutsy version, i untar it, delete my .fretsonfire folder, delete the data-bak folder in the tarball (since it doesn't appear to be needed), and run the FretsOnFire script.  it starts out with the wrong resolution and text size (which is easily fixed), but once i try to enable a mod (**ANY** mod, whether it came with the tarball or not), the program hangs on either the "loading" or "browsing library" screens.  

any ideas?

i LOVE the flames, return of the wavy hold-notes, and the other, various enhancements, but i just can't play Frets without my GH mod.  :p

---

### Post by helino on 2007-11-06
Wow, this is great!

I only have one little problem left, and that's getting crazy.neos score amp ([http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=11;t=8346](http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=11;t=8346)) and herings mod ([http://h3r1n6.googlepages.com/](http://h3r1n6.googlepages.com/)) to work with it.

Do you have any idea how to solve this?

Thx a lot

---

### Post by m4gnesium on 2007-11-12
Hopefully somebody else has run into this: The game runs fine, but refuses to play the guitar track. This happens with every song I have available. If I miss a note it just cuts out the song.ogg track. I tried reinstalling the game and deleting the .fretsonfire folder but it's still doing it.

---

### Post by jnuz on 2007-11-25
[http://www.mediafire.com/?2tihkg12tio](http://www.mediafire.com/?2tihkg12tio)

it still gets the crashes as described earlier by someone else... the _class_ restrcited and the pygame seg fault

that's a link to my binary that has a bunch of the graphics mods included with the win32 version. 

yeah yeah i know it's .zip format... flame later...

Edit: I forgot to mention that I have friends that have gotten this working on SuSE and Fedora. So it's not limited to Ubuntu. just copy your songs folder into the data dir.

---

### Post by khornerz on 2007-11-29
I will try it when I arrive at home today.

Thank you!

---

### Post by xat_ on 2007-12-23
Edit: nevermind

---

### Post by xat_ on 2007-12-23
Has anyone managed to get hyperspeed working in rfmod? Capo's mod doesn't seem to be enabling properly for me.

[http://rs229.rapidshare.com/files/65219465/cmod522.zip](http://rs229.rapidshare.com/files/65219465/cmod522.zip) for anyone who wants to give it a shot.

---

### Post by truptrup on 2007-12-25
Rfmod 4.14 is out here. It has linux fixes supposed to fix the crashes at end of songs and __class__ restricted errors. I havent been able to run it. I get an Importerror pyunicodeucs2_fromunicode
[http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=11;t=11473]("http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=11;t=11473")

```
[/tmp/FretsOnFire-1.2.451-RF-mod-4.14-linux32]$ ./FretsOnFire
Traceback (most recent call last):
 File "/usr/local/src/lang/cx_Freeze-3.0.3/initscripts/Console.py", line 27, in ?
 File "FretsOnFire.py", line 36, in ?
 File "GameEngine.py", line 35, in ?
 File "Data.py", line 23, in ?
 File "Font.py", line 27, in ?
 File "Texture.py", line 27, in ?
 File "/usr/lib/python2.4/site-packages/PIL/Image.py", line 73, in ?
 File "/usr/lib/python2.4/site-packages/PIL/ImagePalette.py", line 19, in ?
ImportError: /tmp/FretsOnFire-1.2.451-RF-mod-4.14-linux32/array.so: undefined symbol: PyUnicodeUCS2_FromUnicode
```

---

### Post by conjur3r on 2007-12-27
> **truptrup said:**
> Rfmod 4.14 is out here. It has linux fixes supposed to fix the crashes at end of songs and __class__ restricted errors. I havent been able to run it. I get an Importerror pyunicodeucs2_fromunicode
[http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=11;t=11473]("http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=11;t=11473")

```
[/tmp/FretsOnFire-1.2.451-RF-mod-4.14-linux32]$ ./FretsOnFire
Traceback (most recent call last):
 File "/usr/local/src/lang/cx_Freeze-3.0.3/initscripts/Console.py", line 27, in ?
 File "FretsOnFire.py", line 36, in ?
 File "GameEngine.py", line 35, in ?
 File "Data.py", line 23, in ?
 File "Font.py", line 27, in ?
 File "Texture.py", line 27, in ?
 File "/usr/lib/python2.4/site-packages/PIL/Image.py", line 73, in ?
 File "/usr/lib/python2.4/site-packages/PIL/ImagePalette.py", line 19, in ?
ImportError: /tmp/FretsOnFire-1.2.451-RF-mod-4.14-linux32/array.so: undefined symbol: PyUnicodeUCS2_FromUnicode
```

I get the exact same error message as you.  No idea how to proceed.

---

### Post by mrcold on 2007-12-27
> **conjur3r said:**
> I get the exact same error message as you.  No idea how to proceed.


me too

---

### Post by smeuuh on 2008-01-02
I think the problem is that this version was frozen using a different version of python. I've made a package that should work on ubuntu/debian without problems :
[http://smeuuh.free.fr/fretsonfire-rfmod-4.14.deb](http://smeuuh.free.fr/fretsonfire-rfmod-4.14.deb)
It's just a quick fix, not a real debian archive. Change your version of python-opengl to 2, or it'll be very slow.

edit : modified to solve the __class__ unavailable in restricted mode bug

---

### Post by mirkuma on 2008-01-04
> **smeuuh said:**
> I think the problem is that this version was frozen using a different version of python. I've made a package that should work on ubuntu/debian without problems :
[http://smeuuh.free.fr/fretsonfire-rfmod-4.14.deb](http://smeuuh.free.fr/fretsonfire-rfmod-4.14.deb)
It's just a quick fix, not a real debian archive. Change your version of python-opengl to 2, or it'll be very slow.

edit : modified to solve the __class__ unavailable in restricted mode bug

Can you please be more specific how to do that? 
Yours installation works, but as you stated it is very slow!
Using Ubuntu 7.10. Have the same error as stated in **truptrup** post

I also have this errors in terminal when I run your package:
> 
/usr/share/games/fretsonfire/game/amanith.py:7: RuntimeWarning: Python C API version mismatch for module _amanith: This Python has API version 1013, module _amanith has version 1012.
  import _amanith
/usr/share/games/fretsonfire/game/amanith.py:7: RuntimeWarning: Python C API version mismatch for module swig_runtime_data3: This Python has API version 1013, module swig_runtime_data3 has version 1012.
  import _amanith


Also is it correct that I must put new songs in "/usr/share/games/fretsonfire/data/songs" directory?

---

### Post by smeuuh on 2008-01-04
The official build is an executable, built for a specific version. This is just the python source, along with some things to make it work.
To make it fast, you need python-openGL version 2, which is not available in the deps (they have v3, which, amazingly, is horribly slow). You can dl it here : 
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=python-opengl](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=python-opengl)
(select the feisty release)
You must also uninstall your current python-opengl, and once you've installed v2, choose to freeze the version in synaptics, or else it'll complain about upgrading.
The errors you speak about are just warnings, ignore them.
I do not really know where to put the songs. There is also a folder for it in ~/.fretsonfire, and this version comes with a library selector, which allows you to select your songs directory ingame (as long as it is named "songs", actually, which is quite strange, but well ...). My advice is use the selector.
Happy playing

---

### Post by mirkuma on 2008-01-04
> **smeuuh said:**
> The official build is an executable, built for a specific version. This is just the python source, along with some things to make it work.
To make it fast, you need python-openGL version 2, which is not available in the deps (they have v3, which, amazingly, is horribly slow). You can dl it here : 
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=python-opengl](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=python-opengl)
(select the feisty release)
You must also uninstall your current python-opengl, and once you've installed v2, choose to freeze the version in synaptics, or else it'll complain about upgrading.
The errors you speak about are just warnings, ignore them.
I do not really know where to put the songs. There is also a folder for it in ~/.fretsonfire, and this version comes with a library selector, which allows you to select your songs directory ingame (as long as it is named "songs", actually, which is quite strange, but well ...). My advice is use the selector.
Happy playing

Thank you very much for your quick answer.
Just a few info needed:
From Synaptic if I try to remove phyton-opengl v3 it want's also to remove your fretsonfore-rfmod.
So should I uninstaled and the reinstall your mod (package)?
How do I frezze phyton-opengl v2 version in Synaptics? Is chosing the menu "Package" in Synaptics and then "Lock version" ok?
Thanks for your help and sorry for my supid questions as I'm a new fresh user of Ubuntu 7.10.


EDIT:
Done all upper, works ok now...but have some other issues with guitar sound now. Playing Santanas Black Magic Women from SG3 doesn't play guitar song, just higher volume back sound.
It works 100% ok with official FretsOnFire-1.2.512-linux version and with FretsOnFire-1.1.324-RFmod-3.5-linux-i686 mod but not with 4.14 RFmod from your package.
The same case is with the original tree songs (by Tommi Inkila) supplied with the official version!
I have deleted both files in /.fretsonfire, restarted, but this doesen't help.

Any idea how to fix that?

EDIT2:
I have checked the fretsonfire.log file...
Is too long to post whole log, but I find this in it, thay may have something to do with missing guitare sound:
> 
[1;33m(W)[0m PyOGG not found. OGG files will be fully decoded prior to playing; expect absurd memory usage.
.
.
.
[1;33m(W)[0m Unable to load guitar track: global name 'StreamingOggSound' is not defined
[1;33m(W)[0m Unable to load rhythm track: global name 'StreamingOggSound' is not defined
.
.
.

PyOGG (python-pyogg 1.3.1.1ubuntu4) is installed in my system....
I have no clue what else can I try.
Please help!

---

### Post by smeuuh on 2008-01-04
Wow, I really don't know. Verify that the faulty song is in the correct format, with all the ogg what they should be. Compare to other songs.


Try also to install these packages :
python-pyvorbis
vorbis-tools
If it works, tell me and I'll update the .deb with the correct dependencies

If it still doesn't work, try copying /usr/lib/python-support/python-pyogg/python2.5/ogg/_ogg.so to /usr/share/games/fretsonfire/game/_ogg.so, but I don't guarantee anything (actually, i'm quite a noob in these matters too)

---

### Post by mirkuma on 2008-01-04
> **smeuuh said:**
> Wow, I really don't know. Verify that the faulty song is in the correct format, with all the ogg what they should be. Compare to other songs.


Try also to install these packages :
python-pyvorbis
vorbis-tools
If it works, tell me and I'll update the .deb with the correct dependencies

If it still doesn't work, try copying /usr/lib/python-support/python-pyogg/python2.5/ogg/_ogg.so to /usr/share/games/fretsonfire/game/_ogg.so, but I don't guarantee anything (actually, i'm quite a noob in these matters too)

Is not the the song. All songs works correctly in others versions and without mod.
Will try to install those packages and let you know.
I will also try my songs with Windows vesion of latest RF-mod.

EDIT: In WindowsXP latest RF-mod-4 works fine with all my songs and original ones. So there is nothing wrong with songs.

EDIT2:
Back to Ubuntu 7.10...
Installed vorbis-tools via Synaptics. Tried FoF RF-mod4. No go.
After that installed python-pyvorbis. Tried FoF RF-mod4. **Success!!!!! Guitar solo is working now!!!!**
Unistalled vorbis-tools via Synaptics. Tried and still works!!

So the key was in python-pyvorbis package!

Thank you very much for your help!

Best regards, must go playing now :-)

P.S.
Just for info: the game works now better in Ubuntu as in WindowsXP on 2GHz P4 machine with 512Mb ram and GeForce Ti4200 with 32MB of RAM. No slowdowns, not glictches..perfectly playable!
I can perfectly play all GHIII songs on my machnine now...Original PC verison for Windows of GH3 won't even install because my PC can't reach even minimal system requiriments (RAM & Graphic card)!

---

### Post by smeuuh on 2008-01-04
Okay. Thanks, i'll update the package now to reflect the change in dependencies. 
Btw, I recently have encountered a "__dict__ unavailable in restricted mode". Is this your case ?

---

### Post by mirkuma on 2008-01-04
> **smeuuh said:**
> Okay. Thanks, i'll update the package now to reflect the change in dependencies. 
Btw, I recently have encountered a "__dict__ unavailable in restricted mode". Is this your case ?
_dict__ unavailable in restricted mode...don't know what are you talking about...sorry I'm really noob regarding Ubuntu/Linux. Is this some kind of error in FoF also?

---

### Post by smeuuh on 2008-01-04
No, just some error I had yesterday while launching a song. Don't worry about it if you don't have it ^^

---

### Post by truptrup on 2008-01-05
Thanks smeuuh install went like a champ and opengl2 sped things up.

I did need to reinstall pygame. It gave me an error about "no audio devices availiable" or something similar. 

Great work

---

### Post by Person_1873 on 2008-02-08
GAH help, 64 bit ubuntu :S :S :S :S :S :S, i need the pyamanith thing n i suck at compiling, could someone please post a link???

---

### Post by PsychedelicReaction on 2008-02-19
it works :)

---

### Post by Vlafdi on 2008-03-07
I'm using Ubuntu 7.10 64bit.
I managed to compile amanith, pyamanith and eventually Frets on Fire, but I can't get it to run. When trying "python FretsOnFire.py" It complains:

Traceback (most recent call last):
  File "FretsOnFire.py", line 94, in <module>
    engine = GameEngine(config)
  File "/home/ile/fof/FretsOnFire-src-1.2.451/src/GameEngine.py", line 194, in __init__
    self.svg = SvgContext(geometry)
  File "/home/ile/fof/FretsOnFire-src-1.2.451/src/Svg.py", line 78, in __init__
    self.setGeometry(geometry)
  File "/home/ile/fof/FretsOnFire-src-1.2.451/src/Svg.py", line 91, in setGeometry
    geometry[2], geometry[3])
  File "/usr/lib/python2.5/site-packages/amanith.py", line 3903, in SetViewport
    def SetViewport(*args): return _amanith.GDrawBoard_SetViewport(*args)
TypeError: in method 'GDrawBoard_SetViewport', argument 4 of type 'unsigned int'

When I try to launch the game in dist/ using a copied launcher, it changes the resolution, crashes and freezes my mouse so I have to do an X restart. I can't copy the output since I don't have any control over my mouse, but it complains something about an opengl-wrapper and that it doesn't have any output module at all, not even ctypes or something.

---

### Post by Vlafdi on 2008-03-19
I now reverted to the Feisty-package of PyOpenGL 2.0.1.09 and got Frets on Fire to start for a second. I hear background music and then the game crashes:

Traceback (most recent call last):
  File "/home/ile/fof/451-src/src/GameEngine.py", line 346, in run
    return self.mainloop()
  File "/home/ile/fof/451-src/src/GameEngine.py", line 320, in loading
    self.view.render()
  File "/home/ile/fof/451-src/src/View.py", line 183, in render
    layer.render(self.visibility[layer], layer == self.layers[-1])
  File "/home/ile/fof/451-src/src/Dialogs.py", line 264, in render
    font.render(self.text, (x, y))
  File "/home/ile/fof/451-src/src/Font.py", line 119, in render
    g = self.getGlyph(ch)
  File "/home/ile/fof/451-src/src/Font.py", line 197, in getGlyph
    t.loadSurface(s, alphaChannel = True)
  File "/home/ile/fof/451-src/src/Texture.py", line 264, in loadSurface
    self.loadRaw(surface.get_size(), string, GL_RGBA, 4)
  File "/home/ile/fof/451-src/src/Texture.py", line 281, in loadRaw
    gluBuild2DMipmaps(self.glTarget, components, w, h, format, GL_UNSIGNED_BYTE, string)
GLUerror: [Errno 100901] invalid value

which is the same error as described here:
[http://ubuntuforums.org/archive/index.php/t-540633.html]("http://ubuntuforums.org/archive/index.php/t-540633.html")

Apparently the Gutsy-version of PyOpenGL delivers a different error to which there is a solution, but there is no Gutsy package of PyOpenGL 2.x anymore and I am unable to compile it.

---

### Post by khornerz on 2008-03-26
Maybe some of you will be interested in this post, it's from fretsonfire.net
it contains ultimate coffee mod ported to linux (with tons of bugs! lot of fun!)

[link here]("http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST&f=11&t=20252&st=&&#entry188201")

---

### Post by Goofee691 on 2008-04-11
has anyone gotten this built for x86_64?

if not how should i go about doing that and what will i need?

---

### Post by thom_raindog on 2008-04-12
> **m4gnesium said:**
> Hopefully somebody else has run into this: The game runs fine, but refuses to play the guitar track. This happens with every song I have available. If I miss a note it just cuts out the song.ogg track. I tried reinstalling the game and deleting the .fretsonfire folder but it's still doing it.

Same problem here.
I suppose you run 64bit as well?

---

### Post by mirkuma on 2008-04-22
Upgraded to Ubuntu 8.04....slowdowns again, probably python-opengl problem again.
Any way to fix this in Hardy?

EDIT:
Works fast again..just uninstall new python-opengl 3.0 package that comes with Hardy Heron and install the old one v2.0 for Fiesty.

---

### Post by jnuz on 2008-04-29
to thom_raindog: install the package pyvorbis. pyogg doesn't register with the game right in ubuntu. once i did that i had guitar.

to mirkuma: thanks for the suggestion of using the feisty package, I'm at full speed again

to anyone: If you guys want a compilation of the newest DS-Alarian UC Mod I made a binary:

[http://www.mediafire.com/?idzmi4mo4gc](http://www.mediafire.com/?idzmi4mo4gc)

I did edit the GHIII and Rock Band Themes, so if you want the originals, just download the windows version of the mod from the FoF fan forums and use the GHIIIMod and RockBandMod folders from there.

---

