---
title: "Humble Indie Bundle 4"
date: 2011-12-13
forum: Gaming &amp; Leisure
---

### Post by R33D3M33R on 2011-12-13
It's up, and it has some fantastic games in it: [http://www.humblebundle.com/](http://www.humblebundle.com/)

Super Meat Boy
Shank
NightSkyHD
Jamestown
Bit.Trip Runner

Pay more than the average and you get:
Cave Story+
Gratuitous Space Battles

Update:
If you pay more than average you get also Humble Indie Bundle #3
Crayon Physics Deluxe
Cogs
VVVVVV
Hammerfight
And Yet it Moves

---

### Post by Perfect Storm on 2011-12-13
Sticked, and bought.


Gratuitous Space Battles is GOLD!!
I didn't knew there was a Linux version, but there is! w00t!

---

### Post by petriborg on 2011-12-13
It looks like GSB crashes out of the box for me on Ubuntu 10.04.

I managed to get it into gdb and got the following back-trace when it segfaulted.

> 
Program received signal SIGSEGV, Segmentation fault.
0x0838dc5d in D3DXCreateTextureFromFileEx(IDirect3DDevice9*, char const*, unsigned int, unsigned int, unsigned int, unsigned int, _D3DFORMAT, _D3DPOOL, unsigned int, unsigned int, unsigned int, void*, void*, IDirect3DTexture9**) ()
(gdb) bt
#0  0x0838dc5d in D3DXCreateTextureFromFileEx(IDirect3DDevice9*, char const*, unsigned int, unsigned int, unsigned int, unsigned int, _D3DFORMAT, _D3DPOOL, unsigned int, unsigned int, unsigned int, void*, void*, IDirect3DTexture9**) ()
#1  0x08111a87 in D3DEngine::CreateTexture(char*, char*) ()
#2  0x08111f57 in D3DEngine::FindTexture(char*, char*, bool) ()
#3  0x0811224a in D3DEngine::CreateTextureOnDemand(char*) ()
#4  0x081125a5 in D3DEngine::GetTexture(char*) ()
#5  0x08115009 in LibFont::Initialise(char*, char*, int, int, int, int) ()
#6  0x081152b0 in LibTextEngine::AddFont(char*, char*, int, int, int, int) ()
#7  0x0825614d in Game::InitText() ()
#8  0x082585b8 in Game::InitApp() ()
#9  0x082e23a5 in WinMain(void*, void*, char*, int) ()
#10 0x08385e5a in main ()


---

### Post by Dlambert on 2011-12-13
Buying FRIDAY! I don't wanna wait though! :(

---

### Post by petriborg on 2011-12-13
This ones looks like a winner (to me), but Gratuitous Space Battles is what I'm mainly buying it for.

---

### Post by petriborg on 2011-12-13
Looks like there is a [thread]("http://www.positech.co.uk/forums/phpBB3/viewtopic.php?f=21&t=6831") on their support page about it now

---

### Post by NESFreak on 2011-12-13
Awesome bundle but (64bit ubuntu 10.04):
```
$ bit.trip.runner
bit.trip.runner: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.15' not found (required by bit.trip.runner)
$ getlibs /usr/bin/bit.trip.runner
./bit.trip.runner: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.15' not found (required by ./bit.trip.runner)
This application isn't missing any dependencies
$
```

--edit--
sort of fixed it by extracting a new version of libstdc++ from [http://packages.ubuntu.com/oneiric/libstdc++6](http://packages.ubuntu.com/oneiric/libstdc++6) and adding it to bit trip runners directory, creating a script that adds it to LD_LIBRARY_PATH and then running bit trip runner.

---

### Post by Perfect Storm on 2011-12-13
Seems there's problem with older Ubuntu releases. Works fine here on Ubuntu 11.10 64-bit.

---

### Post by NESFreak on 2011-12-13
Cave Story also failed@64bit 10.04

fixed it by removing the included libsdl.

Cavestory also needs to be run from inside it's own directory. So instead i'm running it with a script i called 'cavestory':
```
#!/bin/sh

# Change to game directory
CANONPATH=`readlink -f "$0"`
cd "`dirname "$CANONPATH"`"

./doukutsu "$@"

```
and added a symlink from ~/bin/cavestory to the script instead

---

### Post by weasel fierce on 2011-12-13
Tested GSB and it worked okay on my end. Jamestown is mad fun, but the 64bit binary didn't work for me. Had to use the 32bit one, and it ran fine, oddly.

Shank looks amazing though my gamepad worked a bit sluggishly with it.

---

### Post by bash on 2011-12-13
Doesn't just seem to be problems with older ubuntu versions. Running 12.04 64bit pre-release here and so far only game worked out of the box.

**GSB:** Got the same crash as quite few other have.

**Super Meat Boy:** Getting the same error as [this person](http://supermeatboy.com/forum/index.php/topic,2231.0.html). *Update: They added a .deb file now. Downloaded, installed it, crashes with the same error as the .bin file. But at least it has a nice menu icon now.*

**CaveStory:** Includes a lib folder with libs looking for only specific versions of system libs in /usr/lib. Of course mine weren't the right ones. Fixed it by just deleting the lib folder that came with CaveStory.

**NightSkyHD:** Seems to be 32bit only. So if you're using 64bit Ubuntu you need to install at least libgl1-mesa-glx:i386, libgl1-mesa-dri:i386 and libglu1-mesa:i386 to get it to work.

**Jamestown:** Install ok, but when trying to launch just exits with a segfault. When trying to use the 32bit version, made some headway, but finally got stuck on libSDL, for which it seems you can't install a 32bit version alongside the 64bit one.

**bit.trip.runner**: Actually works and even includes a proper 64bit deb file. Which, apperantely to keep up with the spirit of the other ports, is missing a .desktop file, so you'll need to start the game via terminal

**Shank:** Still downloading ...


On another note: Only 2 of the seven games are actually packages in deb file, one of which is missing the .desktop file though. Some of the zipped files even still include the __MACOSX folder. So whoever packaged them, forgot to remove the system specific folders. Don't know if I should find that mildly amusing or another sign of the, at least for me, disappointing quality of the Linux ports. Not the games itself though, because when they work, they are lots of fun and the reason for which I bought this bundle.

---

### Post by uriel1998 on 2011-12-13
Agreed with everyone above about Linux ports.  I mean, I'd rather have fewer ports with good quality than keep bashing my head against the wall because of icky half-working ports.

As it is, I'm currently installing GSB through PlayOnLinux, which annoys me to no end...

---

### Post by Spydax on 2011-12-13
> **bash said:**
> Doesn't just seem to be problems with older ubuntu versions. Running 12.04 64bit pre-release here and so far only game worked out of the box.

**GSB:** Got the same crash as quite few other have.

**Super Meat Boy:** Getting the same error as [this person](http://supermeatboy.com/forum/index.php/topic,2231.0.html). *Update: They added a .deb file now. Downloaded, installed it, crashes with the same error as the .bin file. But at least it has a nice menu icon now.*

**CaveStory:** Includes a lib folder with libs looking for only specific versions of system libs in /usr/lib. Of course mine weren't the right ones. Fixed it by just deleting the lib folder that came with CaveStory.

**NightSkyHD:** Seems to be 32bit only. So if you're using 64bit Ubuntu you need to install at least libgl1-mesa-glx:i386, libgl1-mesa-dri:i386 and libglu1-mesa:i386 to get it to work.

**Jamestown:** Install ok, but when trying to launch just exits with a segfault

**bit.trip.runner**: Actually works and even includes a proper 64bit deb file. Which, apperantely to keep up with the spirit of the other ports, is missing a .desktop file, so you'll need to start the game via terminal

**Shank:** Still downloading ...


On another note: Only 2 of the seven games are actually packages in deb file, one of which is missing the .desktop file though. Some of the zipped files even still include the __MACOSX folder. So whoever packaged them, forgot to remove the system specific folders. Don't know if I should find that mildly amusing or another sign of the, at least for me, disappointing quality of the Linux ports. Not the games itself though, because when they work, they are lots of fun and the reason for which I bought this bundle.

Bought for SMB.  Not even remotely concerned with the others, aaaannnndddd..... it doesn't work.  I can't really give details because I'm an Ubuntu noob.  Says it installed successfully, when I try to open any of the files I think are executables or what should run the game, nothing happens.  Le sigh.  Hopefully someone can give me a decent walkthrough to make this work for me, would make me super happy.  Followed typical .deb instructions, and that all worked well.  Just no dice.

---

### Post by weasel fierce on 2011-12-13
Installed the deb for Super meat boy and it runs well here. 64bit kubuntu 11.10

EDIT: As an aside, Cavestory + works... but only if I run the 32 bit version, same issue as I had with Jamestown. Odd...

---

### Post by qwentin355 on 2011-12-13
I'm with you Spydax, I do not get any sort of notification that it properly installed though, I don't even know if I'm doing it right, It just opens terminal and closes it, so please help out a complete linux noob

---

### Post by uriel1998 on 2011-12-13
Spydax and Qwentin:

Open a terminal window in the directory you're running it from, then execute it from the command line there.  That way you should be able to see the errors.

Still trying with GSB...

---

### Post by Alwimo on 2011-12-13
Super Meat Boy doesn't work due to my integrated Intel graphics. I've been wanting it to be released for Linux for a long time, so this is very disappointing.

Cave Story+, Jonestown and NightSky aren't working and I don't know why. I set them to 

I installed bit.trip.runner but it's not showing up anywhere.

And I haven't tried the others.

---

### Post by thatguruguy on 2011-12-13
> **Alwimo said:**
> 
I installed bit.trip.runner but it's not showing up anywhere.


That's because of this:
> **bash said:**
> 
**bit.trip.runner**: Actually works and even includes a proper 64bit  deb file. Which, apperantely to keep up with the spirit of the other  ports, is missing a .desktop file, so you'll need to start the game via  terminal


Luckily, it's easy enough to create your own launcher (.desktop file).  First, download the graphic I attached to this message, and move it into your /usr/share/icons/hicolor/64x64/apps/ folder. The easiest way to do that is to open a terminal in whatever directory you've saved the file in, and type:
```
sudo mv bit-trip-runner.png /usr/share/icons/hicolor/64x64/apps/
```Now, we'll make the .desktop file. Type the following in a terminal:
```
gksu gedit /usr/share/applications/bit-trip-runner.desktop
```Type or copy-and-paste the following into the text editor that comes up:
```
[Desktop Entry]
Version=1.0
Type=Application
Name=Bit Trip Runner
Comment=A retro-styled, musical platformer
Exec=/usr/bin/bit.trip.runner
Icon=/usr/share/icons/hicolor/64x64/apps/bit-trip-runner.png
Categories=Game
```Save the file, and you should now be able to find the game in the Dash by searching the word "Bit" (without the quotes, of course).

---

### Post by uriel1998 on 2011-12-13
> **thatguruguy said:**
> That's because of this:
...and you should now be able to find the game in the Dash by searching the word "Bit" (without the quotes, of course).

For clarity's sake, that should also get it to show up in earlier versions (such as 10.04) if you're using a launcher like Synapse, Launchy, etc.  Not sure if it automagically shows up in the menu that way, though.

Great walkthrough there, thatguruguy!

---

### Post by thatguruguy on 2011-12-13
> **uriel1998 said:**
> For clarity's sake, that should also get it to show up in earlier versions (such as 10.04) if you're using a launcher like Synapse, Launchy, etc.  Not sure if it automagically shows up in the menu that way, though.

Great walkthrough there, thatguruguy!

Thanks!

I checked, and it does work in both Gnome Shell and Gnome Classic (including being listed in the Games section) on my 11.10 install. If it doesn't work on earlier versions of Ubuntu, or on other distros/desktops, I'm sure someone will point that out.

---

### Post by scu-ba-de-buntu on 2011-12-14
**SuperMeatBoy:** 
[INDENT]First version released crashes. Downloading the new .deb as I write this (wrote by the time you read this?). [/INDENT]

**Jamestown:**
[INDENT] Crashes on playing the game. Menu is pretty though.
> $...
Jamestown: Installed in '/usr/local/games/jamestown'.
Jamestown: Using x86 version.

Allocating 512 x 512 radeon RBO (pitch 512)
failure to revalidate BOs - badness
Jamestown-x86: ../../radeon/radeon_cs_gem.c:129: cs_gem_write_reloc: Assertion `boi->space_accounted' failed.
Aborted
[/INDENT]
**Bit.Trip Runner:**[INDENT] Crashes on load. 

> Some bit.trip.runner: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.15' not found (required by bit.trip.runner)
[/INDENT]
**Cave Story+:**
[INDENT]This one works fine if started from some subfolder within the zip. No enemy damage. They seem to have uploaded a new one. The old one had some useless MacOS file-droppings though.[/INDENT]

Ubuntu: 10.04
Linux: 2.6.32-34-generic

---

### Post by scu-ba-de-buntu on 2011-12-14
[U][B][I]
Updates:[/I][/B][/U]
**SuperMeatBoy:**[INDENT]
New  .deb (super-meat-boy_20111213_all.deb) crashes on load. It does however provide a new icon from the .bin previously installed.[/INDENT]

**CaveStory:**
[INDENT]First version released lacked enemy-caused-damage. New release fixed this. Also the .Zip is better.[/INDENT]

**NightSky:**
[INDENT]Seems to work. Must run from folder.[/INDENT]

---

### Post by Alwimo on 2011-12-14
I followed the instructions from thatguruguy and although the icon for Bit Trip Runner now shows up in the Activities screen (I use Gnome Shell), clicking on it doesn't do anything. I am using Ubuntu 11.10.

It says when installing it through the Software Centre that the package is of a bad quality and that "The package doesn't provide a valid Installed-Size control field. See Debian Policy 5.6.20." But I tell it to ignore that and install anyway.

Trying to start it from the terminal responds with: "error while loading shared libraries: libopenal.so.1: cannot open shared object file: No such file or directory"

---

### Post by ExileAmongYou on 2011-12-14
Just for the record, the only two games I've tried so far, Bit.Trip.Runner and Super Meat Boy, work fine on my 64-bit 11.10 install. The only issue I had was having to hack together a .desktop file for Bit.Trip. I've got an old-ish, moderately decent NVIDIA graphics card with the proprietary drivers.

I've noticed some people in this thread trying to run the relevant executables directly- I've always had the best luck running games from the main Unity menu, which is often linking to a shell script that loads the right libraries and then launches the game.

---

### Post by ExileAmongYou on 2011-12-14
> **Alwimo said:**
> I followed the instructions from thatguruguy and although the icon for Bit Trip Runner now shows up in the Activities screen (I use Gnome Shell), clicking on it doesn't do anything. I am using Ubuntu 11.10.

It says when installing it through the Software Centre that the package is of a bad quality and that "The package doesn't provide a valid Installed-Size control field. See Debian Policy 5.6.20." But I tell it to ignore that and install anyway.

Trying to start it from the terminal responds with: "error while loading shared libraries: libopenal.so.1: cannot open shared object file: No such file or directory"

I also got the "package is of bad quality" error when installing, but my game runs fine.

Try installing openal:
```
sudo apt-get install libopenal1
```

---

### Post by Alwimo on 2011-12-14
It works now. Thank you and thatguruguy. :)

---

### Post by ExileAmongYou on 2011-12-14
> **Alwimo said:**
> It works now. Thank you and thatguruguy. :)

Good to hear. It's a bit odd that they have a .deb file, but it doesn't actually pull in the dependencies the game needs. I guess they're relying on the libraries they package with the game?

---

### Post by sirverdemer on 2011-12-14
Hi guys!

I'm having the same problem in both Shank and SMB, if I try to run it in 64 bit, I get:

Super Meat Boy: Installed in '.'.
Super Meat Boy: Using amd64 version.



Fatal Error: MojoShader compile failed!

If I try to run it under 32 bit:

Super Meat Boy: Installed in '.'.
Super Meat Boy: Using x86 version.
ERROR: Missing required OpenGL extensions:
    - GL_ARB_vertex_buffer_object
    - GL_ARB_shader_objects
    - GL_ARB_vertex_shader
    - GL_ARB_fragment_shader
    - GL_ARB_shading_language_100

I've got an Intel HD3000 graphics card... is that my problem? If not, is there anything I could do to solve it?

GSB runs nicely, as does bit-runner. I haven't tried the other ones...
Hope you can give me a hand on all this!

---

### Post by GeneralZod on 2011-12-14
> **sirverdemer said:**
> 
I've got an Intel HD3000 graphics card... is that my problem? If not, is there anything I could do to solve it?


If you click on the System Requirements for Super Meat Boy on the Humble Bundle page, it says it doesn't work with Intel Integrated cards, sadly - bit annoying as it doesn't look like the sort of game that should require a particularly sophisticated card!

---

### Post by gregmits on 2011-12-14
^ I also get the OpenGL error on Arch32bit. I have an ATI gpu. I have the SeTC libraries installed.
> under 32 bit:

Super Meat Boy: Installed in '.'.
Super Meat Boy: Using x86 version.
ERROR: Missing required OpenGL extensions:
    - GL_ARB_vertex_buffer_object
    - GL_ARB_shader_objects
    - GL_ARB_vertex_shader
    - GL_ARB_fragment_shader
    - GL_ARB_shading_language_100

---

### Post by jony121 on 2011-12-14
I can't get the new music to play on Cave Story+ but the old music works fine... anyone experience the same?

---

### Post by BaconCat on 2011-12-14
So, bought the Bundle (yay) but am having problems with over half the games. :'( Bit disappointing as I've never had issues with any other of the bundles. :confused:

Using Natty 64bit and I get the Following:
**Super Meat Boy**
New .deb runs but if I try and change the resolution it hangs.

**GSB**
Runs flawlessly but I cannot change the resolution. Not fun when I have only 2 monitors so the bezel is right in the middle.

**CaveStory+**
Following Error:
> BaconCat@B-NIX ~/Downloads/CaveStoryPlus $ ./CaveStory+ 
OS...
Mem...
Graphics...
Segmentation fault


**bit.trip.runner**
No Desktop File. Following Error when running:
> BaconCat@B-NIX ~ $ bit.trip.runner 
bit.trip.runner: /usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `GLIBCXX_3.4.15' not found (required by bit.trip.runner)


**NightSky HD**
Following Error:
> BaconCat@B-NIX ~/Downloads/NightSkyHD_Linux/NightSkyHD_Linux $ ./NightSkyHD 
CalcWindowSize screen[2880, 900] window[1200, 672] scale[4]
Run - SoundDriver_Init
SoundDriver_Init
alcCreateContext
alcMakeContextCurrent
alcProcessContext
SoundDriver_Init - OK
Run - SavesDriver_Init
Initial (portable) writable path: Settings
Run - glutInitWindowPosition
freeglut WARNING - Display string token not recognized:  rgba>=1
freeglut WARNING - Display string token not recognized:  slow=0
Run - glutCreateWindow
freeglut  ERROR:  Internal error <Visual with necessary capabilities not found> in function fgOpenWindow
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  4 (X_DestroyWindow)
  Resource id in failed request:  0x0
  Serial number of failed request:  25
  Current serial number in output stream:  28
AL lib: ALc.c:1879: exit(): closing 1 Device
AL lib: ALc.c:1808: alcCloseDevice(): destroying 1 Context(s)


[B]Jamestown:
[/B]Following Error:
> BaconCat@B-NIX ~/Downloads/jamestown $ ./Jamestown
Jamestown: Installed in '.'.
Jamestown: Using amd64 version.
Segmentation fault


[B]Shank:
[/B]Still downloading.

As I said, rather disappointed as I've never had problems before.

---

### Post by thatguruguy on 2011-12-14
> **BaconCat said:**
> 
**bit.trip.runner**
No Desktop File. Following Error when running:


You might try the following, to make sure that the extra c++ libraries are installed:
```
sudo apt-get install libstdc++6
```
As far as the .desktop file is concerned, I've posted instructions on how to build one [here]("http://ubuntuforums.org/showpost.php?p=11536162&postcount=18").

---

### Post by BaconCat on 2011-12-14
> **thatguruguy said:**
> You might try the following, to make sure that the extra c++ libraries are installed:
```
sudo apt-get install libstdc++6
```
As far as the .desktop file is concerned, I've posted instructions on how to build one [here]("http://ubuntuforums.org/showpost.php?p=11536162&postcount=18").

libstdc++6 is already the newest version.

And yeah, I did that for the Desktop file. :)

---

### Post by Perfect Storm on 2011-12-14
I have been in contact with Cliff, he says that the whole GSB Collector Edition (extensions etc.) will also be available for Linux very soon and can will be purchased here: [http://positech.co.uk/gratuitousspacebattles/](http://positech.co.uk/gratuitousspacebattles/)   \o/

A good idea to bug report the Humble Bundle version so the bugs can be ironed out, both in the Humble Bundle version, but also in the Collector Edition.

---

### Post by BaconCat on 2011-12-14
> **Artificial Intelligence said:**
> I have been in contact with Cliff, he says that the whole GSB Collector Edition (extensions etc.) will also be available for Linux very soon and can will be purchased here: [http://positech.co.uk/gratuitousspacebattles/](http://positech.co.uk/gratuitousspacebattles/)   \o/

A good idea to bug report the Humble Bundle version so the bugs can be ironed out, both in the Humble Bundle version, but also in the Collector Edition.
Will do.

Still, with literally not a single game working in linux for me (I can't risk downloading Shank until I know it works, yay for limited internet) I am really disappointed. I may just not play them since I don't want to use Wine. Oh well, at least the charity got their money. xD

---

### Post by thatguruguy on 2011-12-14
> **BaconCat said:**
> libstdc++6 is already the newest version.

And yeah, I did that for the Desktop file. :)

You may want to report the library issue as a bug on the humblebundle page. It appears you're not the only one affected.

---

### Post by happyshirt on 2011-12-14
I installed ia32-libs, and that pulled in a number of other libraries. Not sure which installed the 32 bit libgl.so.1, or if it's necessary to install all of those. Anyway, I can play the 32bit Jamestown now.

---

### Post by uriel1998 on 2011-12-14
> **Artificial Intelligence said:**
> I have been in contact with Cliff, he says that the whole GSB Collector Edition (extensions etc.) will also be available for Linux very soon and can will be purchased here: [http://positech.co.uk/gratuitousspacebattles/](http://positech.co.uk/gratuitousspacebattles/)   \o/

A good idea to bug report the Humble Bundle version so the bugs can be ironed out, both in the Humble Bundle version, but also in the Collector Edition.

As another person mentioned, there's an extensive thread on GSB segfaulting on linux [here]("http://positech.co.uk/forums/phpBB3/viewtopic.php?f=21&t=6831")

---

### Post by JHolmes763 on 2011-12-14
I did install ia32-libs and libGLU1-mesa-dev. Running 11.10. 

**Super Meat Boy** - Installed correctly and runs without errors.  

**bit.trip.runner** - Installed after ignoring warning; added .desktop so the kids could run it easily; runs without errors. 

**CaveStory+** - Unzipped and ran from terminal; runs without errors. 

**Jamestown** - Have to run the 32-bit version as root (sudo) in order for the game to work. Running the amd64 version results in a segmentation fault or just does nothing. 
```
john@Spearmint:~/Downloads/jamestown$ sudo ./Jamestown-amd64
john@Spearmint:~/Downloads/jamestown$ ./Jamestown-amd64
Segmentation fault
john@Spearmint:~/Downloads/jamestown$ ./Jamestown-x86
Segmentation fault

```

**GSB** - runs without errors, but multi-screen support is bad. Unchecking "fullscreen" gives you a window the size of both monitors and no way to change the resolution (only one option in list) or resize the window. Unplayable for me as I have two monitors with different resolutions and some buttons are not visible on the second monitor. 

**NightSkyHD** - unzipped and ran from the terminal; runs without errors. 

**Shank** - Won't run. I get the below message about a text file. Running as root (sudo) just returns me to the prompt and does nothing. Downloading again because I changed the name and maybe that jacked it up. 
```
john@Spearmint:~/Downloads$ ./shank
bash: ./shank: Text file busy

```

When I started this post, I could only get two of these games working. Now they're all working, but one. I think installing ia32 helped most of them out, but I really have no idea. 

Just need to figure out how to organize these so they show up under the games menus so the kids can play 'em. What's the best way to make these accessible to everyone? 

-John

---

### Post by weasel fierce on 2011-12-14
I wonder if there's some sort of difference between kubuntu and ubuntu in this regard, as most of this stuff works for me, so I was surprised that so many people report issues.

---

### Post by Modplanman on 2011-12-15
> **weasel fierce said:**
> I wonder if there's some sort of difference between kubuntu and ubuntu in this regard, as most of this stuff works for me, so I was surprised that so many people report issues.

Seems like the games haven't been properly tested on older distros. Bit.Trip Runner will work on 11.10 for example, but not 11.04 or earlier. They've also admitted they're not final builds - these may as well be labelled public beta versions. They've just got a bunch of volunteer testers to help work out issues:

[https://twitter.com/#!/humble/status/147024588197474305](https://twitter.com/#!/humble/status/147024588197474305)

[https://twitter.com/#!/humble/status/147068784144945152](https://twitter.com/#!/humble/status/147068784144945152)

P.S. New installers for GSB have been posted. Anyone having issues should update.

---

### Post by weasel fierce on 2011-12-15
I kinda wish there was some sort of notification when new versions are available.

---

### Post by R33D3M33R on 2011-12-15
Please note that these are **initial Linux builds** for all the seven games. So, report bugs and you will be soon able to play them without problems.

---

### Post by teeedubb on 2011-12-15
Does anyone here know how to start Super Meat Boy from the commandline? I need to do so to activate my nvidia card. I cant seem to even find anything regarding the installed SMB .deb in synaptic.

---

### Post by JHolmes763 on 2011-12-15
I made a NightSkyHD.desktop with the following, but the game will not start. 

```
[Desktop Entry]
Version=1.0
Type=Application
Name=Night Sky HD
Comment=Action-puzzle game
Exec=/opt/NightSkyHD/NightSKyHD
Icon=/usr/share/icons/hicolor/64x64/apps/NightSkyHD.png
Categories=Game
```

It shows up in the Dash search, but when I click the icon, it lights up and nothing happens. When I run /opt/NightSkyHD/NightSkyHD from the terminal, it loads the game correctly.

```
john@Spearmint:/opt/NightSkyHD$ pwd
/opt/NightSkyHD
john@Spearmint:/opt/NightSkyHD$ ls -al
total 900
drwxr-xr-x 12 john john   4096 2011-12-15 08:24 .
drwxr-xr-x  6 root root   4096 2011-12-15 08:11 ..
drwxr-xr-x 11 john john   4096 2011-12-13 04:04 Default
-rwxr-xr-x  1 john john     22 2011-01-28 02:23 Engine.ini
drwxr-xr-x  2 john john   4096 2011-12-13 04:04 Fonts
-rwxr-xr-x  1 john john    139 2011-01-07 00:28 Game.ini
drwxr-xr-x  2 john john   4096 2011-12-13 04:04 HDImages
drwxr-xr-x 14 john john   4096 2011-12-13 04:04 HDWorld
drwxr-xr-x  2 john john   4096 2011-12-13 04:04 Images
drwxr-xr-x  2 john john   4096 2011-12-12 09:49 Layouts
drwxr-xr-x  2 john john   4096 2011-12-15 00:54 lib
-rw-r--r--  1 root root   7553 2011-12-15 08:24 logfile_20111215_082406.log
-rwxrwxrwx  1 john john 854216 2011-12-13 00:27 NightSkyHD
drwxr-xr-x  2 john john   4096 2011-12-13 04:04 Settings
drwxr-xr-x  2 john john   4096 2011-12-13 04:04 setup
drwxr-xr-x 14 john john   4096 2011-12-13 04:04 World
```

Any idea what I'm missing? Thanks. 

-John

---

### Post by JHolmes763 on 2011-12-15
> **teeedubb said:**
> Does anyone here know how to start Super Meat Boy from the commandline? I need to do so to activate my nvidia card. I cant seem to even find anything regarding the installed SMB .deb in synaptic.

My .desktop for SMB lists the exec as /usr/local/games/supermeatboy/SuperMeatBoy

---

### Post by AMD1212 on 2011-12-15
> **JHolmes763 said:**
> 

**GSB** - runs without errors, but multi-screen support is bad. Unchecking "fullscreen" gives you a window the size of both monitors and no way to change the resolution (only one option in list) or resize the window. Unplayable for me as I have two monitors with different resolutions and some buttons are not visible on the second monitor. 

-John

There is a easy fix for that problem.
Go to ~/.positech/GSB and edit the prefs.ini
set width and height to something which better fit's your screens.

best,
Stefan

---

### Post by Alwimo on 2011-12-15
Starting Super Meat Boy from the terminal, it says "Fatal Error: MojoShader compile failed!"

Exclamation mark and everything.

Mojoshader was made by the person who did the Linux port. 
[http://icculus.org/mojoshader/](http://icculus.org/mojoshader/)

---

### Post by WienerWuerstel on 2011-12-15
> **Alwimo said:**
> Starting Super Meat Boy from the terminal, it says "Fatal Error: MojoShader compile failed!"

Exclamation mark and everything.

Mojoshader was made by the person who did the Linux port. 
[http://icculus.org/mojoshader/](http://icculus.org/mojoshader/)

It seems that you are using Open Source Drivers wich don't work that great with SMB. Or you are using an integrated Intel Graphics Chip which doesn't work at all with SMB.

---

### Post by Alwimo on 2011-12-15
Yes, it's the integrated intel graphics and I'm aware that.

Even though it worked on this computer with Windows. Very frustrating and disappointing.

Hopefully it is considered a bug and will be fixed, but I doubt it.

---

### Post by aisyko on 2011-12-15
> **WienerWuerstel said:**
> It seems that you are using Open Source Drivers wich don't work that great with SMB. Or you are using an integrated Intel Graphics Chip which doesn't work at all with SMB.
same error for me, i'm using open source radeon drivers and can't use others (catalyst doesn't function with radeon hd 3650 agp card).

---

### Post by thatguruguy on 2011-12-15
> **JHolmes763 said:**
> I made a NightSkyHD.desktop with the following, but the game will not start. 

```
[Desktop Entry]
Version=1.0
Type=Application
Name=Night Sky HD
Comment=Action-puzzle game
Exec=/opt/NightSkyHD/NightSKyHD
Icon=/usr/share/icons/hicolor/64x64/apps/NightSkyHD.png
Categories=Game
```It shows up in the Dash search, but when I click the icon, it lights up and nothing happens. When I run /opt/NightSkyHD/NightSkyHD from the terminal, it loads the game correctly.


Two issues.

[LIST=1]
[*]I don't know if this is true for the actual file on your system, but the .desktop file you posted here has a typo in it. You capitalized the "k" in the second instance of "NightSkyHD" in the Exec call. Instead of "Exec=/opt/NightSkyHD/NightS**K**yHD", it should read "Exec=/opt/NightSkyHD/NightS**k**yHD"/
[*]Night Sky requires that you include the path.  The correct .desktop file should look like this:
[/LIST]
```
[Desktop Entry]
Version=1.0
Type=Application
Name=Night Sky HD
Comment=Action-puzzle game
Path=/opt/NightSkyHD
Exec=/opt/NightSkyHD/NightSkyHD
Icon=/usr/share/icons/hicolor/64x64/apps/NightSkyHD.png
Categories=Game
```

---

### Post by zuti on 2011-12-15
Anyone else missing audio with the 64-bit version of SMB on 11.10? Game seems completely silent, but when running the x86-version all is fine.  

I'd be checking the icculus bugzilla, but it seems to be down right now.

---

### Post by Another Monkey on 2011-12-15
> **BaconCat said:**
> 
**bit.trip.runner**
No Desktop File. Following Error when running:
> BaconCat@B-NIX ~ $ bit.trip.runner
bit.trip.runner: /usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `GLIBCXX_3.4.15' not found (required by bit.trip.runner) 

Same here on 10.10 Maverick 64bit.  Fully updated as far as possible.
Hope they have a fix/workaround soon.

---

### Post by R33D3M33R on 2011-12-15
SuperMeatBoy: It installs fine and runs kind of ok if you enable V-sync for your graphics card, but it doesn't exit correctly. Also, sound seems to slowdown and speedup. After some time it is completely gone.

NightSkyHD: Everything works, except the fullscreen mode. Fullscreen is only a maximized window.

Other games weren't tested yet.

---

### Post by uriel1998 on 2011-12-15
GSB is reorganizing their forums, so the old link to the forum topic doesn't work.  That said, the new .deb (posted 2011-12-14) works beautifully for me so far.

---

### Post by Perfect Storm on 2011-12-15
GSB linux support subforum: [http://positech.co.uk/forums/phpBB3/viewforum.php?f=29](http://positech.co.uk/forums/phpBB3/viewforum.php?f=29)

---

### Post by R33D3M33R on 2011-12-15
**Jamestown**: works ok, just the sound seems to be skipping sometimes

**Bit.Trip.Runner**: I get GLIBCXX_3.4.15 error. A dirty fix: download and install jamestown. Then before running bit.trip.runner do:

```
export LD_LIBRARY_PATH=/path/to/jamestown/x86/
```

It should work after that. libstdc++ should be definitely packaged with this game.

---

### Post by mikeym on 2011-12-15
I'm getting the same problem on NightSkyHD on Fedora 16 with FreeGLUT 2.6.0 and an NVidia card.

Not sure how to report any problems, couldn't find a link.

---

### Post by computerboy on 2011-12-15
One thing you could do is run super meat boy under wine

---

### Post by Modplanman on 2011-12-15
> **R33D3M33R said:**
> **Jamestown**: works ok, just the sound seems to be skipping sometimes

**Bit.Trip.Runner**: I get GLIBCXX_3.4.15 error. A dirty fix: download and install jamestown. Then before running bit.trip.runner do:

```
export LD_LIBRARY_PATH=/path/to/jamestown/x86/
```

It should work after that. libstdc++ should be definitely packaged with this game.

Even easier fix, particularly if you're not interested in Jamestown anyway:

simply download more recent libstdc++ from ubuntu packages: [http://packages.ubuntu.com/oneiric/libstdc++6](http://packages.ubuntu.com/oneiric/libstdc++6)

create a lib folder in your bit.trip folder wherever it's installed to e.g.

```
export LD_LIBRARY_PATH=/home/user/Games/bit.trip.runner/lib/
```

DON'T install  the .deb you downloaded. use archive manager to extract libstdc++.so.6 and .so.6.0.16 from the .deb to the lib folder.

even better, create an sh file or use the .desktop export option mentioned earlier to do it automatically.

---

### Post by beno on 2011-12-15
> **R33D3M33R said:**
> **Jamestown**: works ok, just the sound seems to be skipping sometimes

**Bit.Trip.Runner**: I get GLIBCXX_3.4.15 error. A dirty fix: download and install jamestown. Then before running bit.trip.runner do:

```
export LD_LIBRARY_PATH=/path/to/jamestown/x86/
```

It should work after that. libstdc++ should be definitely packaged with this game.

+1 - fixed this for me (using the amd64 libs instead though)

```
 $ LD_LIBRARY_PATH=/path/to/latest/jamestown/amd64 bit.trip.runner 
```

---

### Post by Alwimo on 2011-12-16
> **computerboy said:**
> One thing you could do is run super meat boy under wine
Oh!

I did that and it works. Thank you! :)

I think I tried that one time before, through Steam under WINE but it wasn't good. But doing it directly with the Humble Bundle .exe was fine.

---

### Post by svpypgeek on 2011-12-16
Shank: the hero is constantly running to the left, even if you do not press on the "left"

impossible to play (

---

### Post by Ripu on 2011-12-16
**Gratuituous Space Battles**: Works fine
**Cave Story+**: Works fine
**Super Meat Boy**: Fine
**Shank**: Haven't tried yet
**NightSky HD**: Works fine
**Jamestown**: Works fine

**Bit.Trip Runner**: Sound doesn't work
When I open Bit.Trip Runner, terminal says the following:

sound: available devices:
     : No Output (default)
sound: requested device ALSA Default
sound: failed to access device ALSA Default, will try default device No Output
sound: using device No Output, OpenAL 1.1
sound: available extensions:
ALC_ENUMERATE_ALL_EXT ALC_ENUMERATION_EXT ALC_EXT_CAPTURE ALC_EXT_disconnect
ALC_EXT_EFX

I'm using Ubuntu 11.10. I install the game from the .deb file.

---

### Post by R33D3M33R on 2011-12-16
> **svpypgeek said:**
> Shank: the hero is constantly running to the left, even if you do not press on the "left"

impossible to play (

Do you have a game controller plugged in? Calibrate it or turn it off. Some laptops seem to have a accelerometer that is detected as a game controller. Try to turn that off too.

---

### Post by Found on 2011-12-16
**Bit.Trip.Runner**
After the lib fix suggested by *Modplanman*
```

sound: available devices:
     : PulseAudio Software (default)
     : ALSA Software
     : OSS Software
sound: requested device ALSA Default
sound: failed to access device ALSA Default, will t
Fatal error
sound: failed to access device PulseAudio Software

```
aoss doesn't help either, and i'm using alsa

---

### Post by JHolmes763 on 2011-12-16
> **thatguruguy said:**
> Two issues.
[LIST=1][*]I don't know if this is true for the actual file on your system, but the .desktop file you posted here has a typo in it. You capitalized the "k" in the second instance of "NightSkyHD" in the Exec call. Instead of "Exec=/opt/NightSkyHD/NightS**K**yHD", it should read "Exec=/opt/NightSkyHD/NightS**k**yHD"/
[*]Night Sky requires that you include the path.  The correct .desktop file should look like this:[/LIST]

Thanks for the typo catch. That and the PATH fixed the issue. 

-John

---

### Post by JHolmes763 on 2011-12-16
> **AMD1212 said:**
> There is a easy fix for that problem.
Go to ~/.positech/GSB and edit the prefs.ini
set width and height to something which better fit's your screens.

Thanks. That fixed this issue for me. :)

---

### Post by cprofitt on 2011-12-16
I have a small full color rectangle of color in Shank with the rest of the screen being 'semi-transparent' black. Is that normal?

---

### Post by svpypgeek on 2011-12-16
> **R33D3M33R said:**
> Do you have a game controller plugged in? Calibrate it or turn it off. Some laptops seem to have a accelerometer that is detected as a game controller. Try to turn that off too.

No game controller. notebook ASUS  k50in
touchpad is disabled

---

### Post by Dlambert on 2011-12-16
Just Bought! WOOOOOOOOOOOOOOO!

---

### Post by xondak on 2011-12-17
I get a segfault when I try to launch Super Meat Boy. (I have Intel Graphics GM965, idk if this could be the problem)

Also when I try to play Bit.Trip I get a similar error as other people do:

xxxxxx@xxxxx-pc:~$ bit.trip.runner
bit.trip.runner: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.15' not found (required by bit.trip.runner)

Is there a resolution to either of these errors?

---

### Post by thatguruguy on 2011-12-17
> **xondak said:**
> I get a segfault when I try to launch Super Meat Boy. (I have Intel Graphics GM965, idk if this could be the problem)

Yes, that's the problem. As has already been noted repeatedly in this thread, Super Meat Boy doesn't work with the Intel integrated graphics.  You can download the Windows version, and see if it works under Wine (I haven't tried that yet, so I can't tell you if it will work.

> **xondak said:**
>  Also when I try to play Bit.Trip I get a similar error as other people do:

xxxxxx@xxxxx-pc:~$ bit.trip.runner
bit.trip.runner: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.15' not found (required by bit.trip.runner)

Is there a resolution to either of these errors?

Two different fixes have been proposed in this thread for Bit.Trip.Runner GBLIBCXX_3.4.15 problem. Try either of them, or both.

---

### Post by RavensKrag on 2011-12-17
Can someone edit the original post to list the known problems with the linux versions of these games and possible fixes/workarounds?  Would be nice to have them all in one place for the benefit of people new to the thread.

---

### Post by Krux on 2011-12-17
> **R33D3M33R said:**
> **Jamestown**: works ok, just the sound seems to be skipping sometimes

**Bit.Trip.Runner**: I get GLIBCXX_3.4.15 error. A dirty fix: download and install jamestown. Then before running bit.trip.runner do:

```
export LD_LIBRARY_PATH=/path/to/jamestown/x86/
```

It should work after that. libstdc++ should be definitely packaged with this game.

tried this, did not work for me.

---

### Post by tudor117 on 2011-12-18
Got every game to work except Shank. (Ubuntu 10.10 x64)
Even installed the update they had.
If running the launcher that they provided it just says:
```
$ ./Shank 
Shank: Installed in '.'.

```
If I run the executable in the bin folder, it just quits. Nothing else. It just quits. Gdb says it creates a bunch of threads, and then exits them immediately.

---

### Post by Surlent777 on 2011-12-19
Re: Shank

If I'm not mistaken, that ./Shank bit needs to be run with sudo; this will prompt you to install it. From there it'll install to either ~/shank or /usr/local/games/Shank, as you choose. From there, run the executable.

---

### Post by tudor117 on 2011-12-19
RE: Shank

I forgot to mention that running either launcher or executable of Shank does the *exact* same thing. No output, or just the "Installed in '.'". Also, the update of shank came in a deb file. It still does not work.
I'd be nice if it would produce some output...

---

### Post by Perfect Storm on 2011-12-19
> **Surlent777 said:**
> Re: Shank

If I'm not mistaken, that ./Shank bit needs to be run with sudo; this will prompt you to install it. From there it'll install to either ~/shank or /usr/local/games/Shank, as you choose. From there, run the executable.

Only if you want to install it systemwide. You can install it without sudo.

---

### Post by tudor117 on 2011-12-19
Correct me if I'm wrong, but Artificial Intelligence and Surlent777	
 are both referring to the *.bin package. 
The *.deb package must be installed system wide.
And regardless, it still does not run for me. At all. With no output.

---

### Post by Perfect Storm on 2011-12-19
> **tudor117 said:**
> Correct me if I'm wrong, but Artificial Intelligence and Surlent777	
 are both referring to the *.bin package. 
The *.deb package must be installed system wide.
And regardless, it still does not run for me. At all. With no output.

Aye, the .bin package.
I didn't have much luck with the .deb so I went for .bin/.sh packages instead and installed them locally instead of systemwide. I have a separated partitions called /games that are set to my user, it's where I install all my games.

---

### Post by thatguruguy on 2011-12-19
> **RavensKrag said:**
> Can someone edit the original post to list the known problems with the linux versions of these games and possible fixes/workarounds?  Would be nice to have them all in one place for the benefit of people new to the thread.

Sounds like a good idea. Perhaps you should start a thread with all known problems and proposed fixes.

---

### Post by R33D3M33R on 2011-12-19
Can those with problems with Shank try: 

```
ldd /path/to/executable
```

?

---

### Post by tudor117 on 2011-12-19
I've tried the bin too, and it the exact same problem, regardless of whether its sudo or not or installed system wide or locally.

ldd does not report any missing libraries...
```
$ ldd Shank 
	linux-gate.so.1 =>  (0xf76f7000)
	libSDL-1.2.so.0 => /usr/lib32/libSDL-1.2.so.0 (0xf7637000)
	libfmodex-4.30.02.so => /usr/local/games/shank/bin/./libfmodex-4.30.02.so (0xf7421000)
	libfmodevent-4.30.02.so => /usr/local/games/shank/bin/./libfmodevent-4.30.02.so (0xf737a000)
	libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf728f000)
	libm.so.6 => /lib32/libm.so.6 (0xf7269000)
	libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf724d000)
	libc.so.6 => /lib32/libc.so.6 (0xf70f1000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf70d8000)
	libasound.so.2 => /usr/lib32/libasound.so.2 (0xf700b000)
	librt.so.1 => /lib32/librt.so.1 (0xf7002000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf6ffe000)
	/lib/ld-linux.so.2 (0xf76f8000)

```
You might notice that the SDL library is not from shank's directory, that is because I moved it (most humble games had problems with the provided SDL library). Shank would not run with its own libraries anyways.

---

### Post by brainard52 on 2011-12-20
To start, what are the games that are unusable from the start (without any workarounds) and what are the workarounds for them? I have tried Super Meat Boy (deb and bin, 32 bit) and I've tried Bit.Trip Runner (deb, 32 bit). Neither have worked. 

Edit: Yes, I read the thread. I really hope the Dev's pull through and fix everything...

---

### Post by Modplanman on 2011-12-20
Latest version of NightSky HD 64 bit doesn't work. It states this:

```
./NightSkyHD_64: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.14' not found (required by /home/user/Other/Games/HumbleBundle/NightSky/lib64/libalut.so.0)

```

Thing is, there is no higher version available for Ubuntu that would fit the requirements. In all versions, the highest libc is 2.13 (including even in 12.04)

I'm really questioning who in the Hell is packaging these games, and who the Hell they got to test them, because right now the same mistakes are being made over and over for each game. It really doesn't even seem like they give a crap about any distro older than the last few months. And despite what [was said on reddit]("http://www.reddit.com/r/linux_gaming/comments/nd36h/the_humble_indie_bundle_4_64_bit_nothing_works/c385q5g"), a new version of Bit.Trip Runner has still not been released.

Best selection of games, Worst ports (and it almost seems like worst porters too). Why could they have not waited an extra month or 2, was it really that important to have another bundle for Christmas?

---

### Post by Apewall on 2011-12-20
I'm running Xubuntu 11.10 x64

**Super Meat Boy** - wont save settings, resets every launch(Where the hell are they even located?)

**Bit Trip Runner** - install missing library

**Jamestown** - No issues, make sure you are using /.jamestown to launch

**NightSky** - No issues

**CaveStory+** - No issues

**Gratuitous Space Battles** - Edit prefs.ini

**Shank** - ia32-libs required, problem with configuring gamepads, game has slowdowns.

Some of the files from the bundle have been updated since release, you can follow releases on their twitter, these are the latest releases at the time of this post.

SuperMeatBoy and Shank will *_-not-_* work on intel HD cards, not sure about the other games.

---

### Post by R33D3M33R on 2011-12-20
> **Apewall said:**
> I'm running Xubuntu 11.10 x64

**Super Meat Boy** - wont save settings, resets every launch(Where the hell are they even located?)


Look in:

```
~/.local/share/SuperMeatBoy/UserData
```

---

### Post by thatguruguy on 2011-12-20
> **Modplanman said:**
> Latest version of NightSky HD 64 bit doesn't work. It states this:

```
./NightSkyHD_64: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.14' not found (required by /home/user/Other/Games/HumbleBundle/NightSky/lib64/libalut.so.0)

```Thing is, there is no higher version available for Ubuntu that would fit the requirements. In all versions, the highest libc is 2.13 (including even in 12.04)


Same issue here with newest version of NightSky HD. Odd, since it worked before the update.

---

### Post by thatguruguy on 2011-12-20
Oddly enough, the 32-bit build of NightSky now works better than it did before.

---

### Post by Hengst0r on 2011-12-20
After extracting libstdc++.so.6 and .so.6.0.16 to get rid of that lib issue bit.trip.runner still refuses to start.

```

sound: available devices:
     : PulseAudio Software (default)
     : ALSA Software
     : OSS Software
     : PortAudio Software
sound: requested device ALSA Default
sound: failed to access device ALSA Default, will try default device PulseAudio Software
Fatal error
sound: failed to access device PulseAudio Software

```There is a game.cfg in ~/.gaijin_games/bit.trip.runner containing the following line:
```
SoundDevice = ALSA Default
```Change this to:

```
SoundDevice = ALSA Software
```and go start playing, even without PulseAudio.

I am running Ubuntu 10.04.3 32bit with pure ALSA Setup and installed using .deb.

It took some time to fiddle that out, indeed.

---

### Post by R33D3M33R on 2011-12-20
Humble Bundle #3 was added for those that pay more than average.

---

### Post by ubudog on 2011-12-20
Awesome Bundle, like usual.  :D

Bought!  :)

---

### Post by Apewall on 2011-12-20
> **R33D3M33R said:**
> Look in:

```
~/.local/share/SuperMeatBoy/UserData
```

reg0.dat had fullscreen already set, if i delete it, i still cannot save the resolution and it reverts to 1024x768 fullscreen:no

The audio settings on the other hand keep between launches of the game.  Only the resolution is resetting.

[https://bugzilla.icculus.org/show_bug.cgi?id=5316](https://bugzilla.icculus.org/show_bug.cgi?id=5316)

---

### Post by R33D3M33R on 2011-12-21
It appears that the some of the bonus games (HIB #3) have new versions. Check them out if you had problems with them before.

Also: please use BitTorrent for downloading and seed at least up to 1.0 ratio. The server owners will surely be grateful for every seeder, because it reduces their costs.

---

### Post by Perfect Storm on 2011-12-21
12 games:

Shank 
Super Meat Boy
Nightsky
Jamestown
Bit Trip Runner
GSB
Cave Story +
Crayon Physics Deluxe
Cogs
VVVVVV
Hammerfight
And Yet it Moves

EDIT: too slow.

---

### Post by R33D3M33R on 2011-12-22
SuperMeatBoy works properly for me now. Just** force V-Sync** and** disable Catalyst A.I.**

---

### Post by heelguru on 2011-12-22
Has anyone had any luck in making a .desktop file for Cave Story+?

I'm running Xubuntu 11.10The game runs fine when double clicking on the icon inside the untarred folder or when running from terminal within the folder ie. need to cd into CS+ directory to run. If I try to run from a different directory it gives the following:

```
hector@oneiric:~$ ./Games/CaveStory+/CaveStory+
OS...
Mem...
Graphics...
File...Parsing mod list...
  ...FAILED: list file didn't exist.
Menu...
Loading file: UI.bmp
  (Could not find!)
Loading file: ogph/UI.bmp
  (Could not find!)
Loading file: csfont.fnt
  (Could not find!)
Segmentation fault

``` 

Unsurprisingly when using the following .desktop file it gives the same seg fault.

```
[Desktop Entry]
Type=Application
Name=Cave Story+
Exec=/home/hector/Games/CaveStory+/CaveStory+
Icon=/home/hector/Games/CaveStory+/data/icon.bmp
Categories=Game

```

I tried saving the .desktop file in /usr/share/applications but it didn't execute and ~/.local/share/applications but to no avail. 

Any help will be greatly appreciated.

---

### Post by R33D3M33R on 2011-12-22
You should set the working directory of the executable with:

```
Path=/path/to/game/
```

More here: [http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html)

---

### Post by gewalker on 2011-12-22
> **Modplanman said:**
> Latest version of NightSky HD 64 bit doesn't work. It states this:
Best selection of games, Worst ports (and it almost seems like worst porters too). Why could they have not waited an extra month or 2, was it really that important to have another bundle for Christmas?

Did you miss somewhere that this is a charity effort?

---

### Post by thatguruguy on 2011-12-22
FWIW, the latest build of the 64-bit version of NightSkyHD seems to work just fine.

---

### Post by heelguru on 2011-12-23
Cheers mate! Worked like a charm.

---

### Post by Cookyt on 2011-12-23
After a few hours of dependency problems, I finally got all the games working!

For anyone getting this error with Bit Trip Runner:

```
bit.trip.runner: /usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `GLIBCXX_3.4.15' not found (required by bit.trip.runner)
```

Here's a workaround:

1. Download the updated libstdc++6 from [http://packages.ubuntu.com/oneiric/libstdc++6](http://packages.ubuntu.com/oneiric/libstdc++6)

2. Extract the contents of the .deb file, we want the library files located under <folder of extracted .deb file>/usr/lib/<your architecture>-linux-gnu 
NOTE: angled brackets are substitutes for actual filenames, so on my system the path is /home/carlos/Desktop/libstdc++6_4.6.1-9ubuntu3_amd64/usr/lib/x86_64-linux-gnu

3. copy the two library files from the extracted directory into /usr/share/bit.trip.runner/lib/ 
NOTE: it doesn't matter where you copy the files to specifically, as long as you know where they are

4. put the following code into a shell script and make it executable:

```
#!/bin/bash
export LD_LIBRARY_PATH='/usr/share/bit.trip.runner/lib/'
/usr/bin/bit.trip.runner
```

5. run the script and the game should work


explanation:

The porter is using a library which does not comes standard with Ubuntu below 11.10, so we just have to download the libraries and tell the game to look at the downloaded libraries instead of the standard system ones.  Maybe it's not the best fix, but it works.


Kudos to NESFreak for doing exactly this way back on page one

---

### Post by Perfect Storm on 2011-12-28
The humble Bundle 4 have ended. hopefully we'll see a Humble Bundle 5 :D

Thread unstick'd and closed.
If people want further help with their humble bundle games, please start a thread in our game forum.


regards
A.I. Dude

---

