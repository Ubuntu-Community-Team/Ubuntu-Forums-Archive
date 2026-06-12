---
title: "NWN Diamond dvd working in 12.10 yey! 64bit movies to"
date: 2012-11-09
forum: Gaming &amp; Leisure
---

### Post by vanquishedangel on 2012-11-09
Special thanks to Hipmaestro (I copied and pasted a lot from his post), Skildron ( I used many of his answers to other people's threads in other forums), Wolfram (wrote original guide), me (lol, I tried to make it more "copy and paste", many of these fixes were from my trial and error), and several people on the internet.

Some things in this guide are for 64bit (ia-32-libs) but this guide works for 32bit as well, also some tweaks and settings may work for a wine install and the good old games version. **Movies are working in 64bit! See below at bottom!**

 Also Kingmaker will not work because the one on the disk needs to authenticate on biowares website, that is no longer hosting for Neverwinter Nights, so I skipped those instructions but will update this guide if I find a way.

For some trouble shooting after installation check the bottom of this post under "***Other Tweaks that helped me improve performance***".

[COLOR="Magenta"]***To install Neverwinter Nights Diamond Edition (assuming DVDs automatically mount at /media/cdrom):***[/COLOR]


[SIZE="3"]**1. Install some dependencies that are needed.**[/SIZE]

_Code:_
sudo apt-get install libsdl1.2debian libsdl-sound1.2 libsdl-mixer1.2 libsdl-net1.2 libsdl-image1.2 libstdc++5 libx11-dev ia32-libs ia32-libs-multiarch


[SIZE="3"]**2. Create a directory where you wish to install Neverwinter Nights (the destination directory). Neverwinter Nights Diamond requires 4.6 GB of free hard disk space.**[/SIZE]

_Code:_
mkdir nwn

cd nwn


[SIZE="3"]**3. Unzip Data_Shared.zip from Diamond DVD into the destination directory. Unzip Data_linux.zip from Diamond DVD into the destination directory.**[/SIZE]

_Code:_
unzip /media/cdrom/Data_Shared.zip

unzip /media/cdrom/Data_linux.zip


[SIZE="3"]**4. Unzip data/XP1.zip from Diamond DVD into the destination directory (overwriting all). Unzip data/XP2.zip from Diamond DVD into the destination directory (overwriting all).**[/SIZE]

_Code:_
unzip -o /media/cdrom/data/XP1.zip

unzip -o /media/cdrom/data/XP2.zip


[SIZE="3"]**5. Download nwclientgold.tar.gz (7.2 MB) and extract it into the destination directory (overwriting all).**[/SIZE]

_Code:_
wget http://nwdownloads.bioware.com/neverwinternights/linux/gold/nwclientgold.tar.gz

tar -xzf ~/nwclientgold.tar.gz


[SIZE="3"]**6. Download nwclienthotu.tar.gz (37.7 MB) and extract it into your nwn directory, overwriting all.**[/SIZE]

_Code:_
 wget http://nwdownloads.bioware.com/neverwinternights/linux/161/nwclienthotu.tar.gz

tar -xzf ~/nwclienthotu.tar.gz


[SIZE="3"]**7. Update to latest version (506 MB).**[/SIZE]

_Code:_
wget http://na.llnet.bioware.cdn.ea.com/u/f/eagames/bioware/neverwinternights/updates/linux/169/English_linuxclient169_xp2.tar.gz

tar -xzf ~/English_linuxclient169_xp2.tar.gz


[SIZE="3"]**8.[Optional] Get the C.E.P. (Community Expansion Pack 2.4, required for many modules made by players)**[/SIZE]

_Code:_
wget http://vnfiles.ign.com/nwvault.ign.com/fms/files/hakpaks/7849/CEP_24_a.rar

The cep has instructions on how to install it here (pdf):

_Code:_
wget http://vnfiles.ign.com/nwvault.ign.com/fms/files/hakpaks/7849/Downloading_and_Installing_CEP.pdf


[SIZE="3"]**9. Run ./fixinstall from the destination directory.**[/SIZE]

_Code:_
./fixinstall


[[SIZE="3"]**10. To run Neverwinter Nights, run ./nwn or ./dmclient from the destination directory to run the player client or DM client respectively.**[/SIZE]

_Code:_
./nwn


[SIZE="3"]**11. If you get this message:**[/SIZE]

"nwmain: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Aborted"

- - Remove ./lib from LD_LIBRARY_PATH.

Code:
sed -i~ 's|\./lib:||' nwn


[COLOR="Magenta"]***NWMovies puts the movies back into the Linux client just like they are on the Windows clients.***[/COLOR]


[SIZE="3"]**1. Install NWMovies v4.0 RC1.**[/SIZE]

_Code:_
wget http://home.roadrunner.com/~nwmovies/nwmovies/nwmovies-latest.tar.gz

tar -xzvf nwmovies-latest.tar.gz



[SIZE="3"]**2. Install the Bink Video command line Player for x86 GNU/Linux.**[/SIZE]

_Code:_
wget http://www.radgametools.com/down/Bink/BinkLinuxPlayer.7z

unzip BinkLinuxPlayer.7z

sudo chmod 755 BinkPlayer


[SIZE="3"]**3. Modify the 'nwn' startup script.**[/SIZE]

_Code:_
sed -i~nwmovies '\|\./nwmain|iexport LD_PRELOAD=./nwmovies.so' nwn


**4. Optionally enable Screen Flickering at movie beginning/end fix:**

_Code:_
sed -i '\|nwmovies|aexport NWMOVIES_GRAB_HACK=1' nwn


[SIZE="3"]**5. Run NWN.**[/SIZE]

_Code:_
./nwn


[SIZE="3"]**6. You get this message:**[/SIZE]

"NOTICE: NWMovies: INI File written: Now exiting. **This is perfectly normal!**
NOTICE: Your next run of NWN should be complete, and include movies."

- - Run NWN a second time.

_Code:_
./nwn


[COLOR="Magenta"]***Other Tweaks that helped me improve performance***[/COLOR]


[SIZE="3"]**1. Neverwinter Nights is not multithreaded so dual cores and hyperthreaded processors may cause performance issues as it does for many people. Also access to more memory will help shuddering as well**[/SIZE]

_Solution:_
Open your file manager and open the "nwn" folder. Right click "nwnplayer.ini" and select your text editor (mine is leafpad). Copy the text below and paste it under the [Game Options] section.

Client CPU Affinity=1

Max Memory Usage=512 (or anywhere up to 4096 mb, depending on your ram)


[SIZE="3"]**2. Enabling better graphics capabilities that are not always available within the game menu's.**[/SIZE]

_Solution:_
Open your file manager and open the "nwn" folder. Right click "nwn.ini" and select your text editor (mine is leafpad). Then choose options you want to enable.

    *example:(ATI cards only)*

*Replace the line "Enable Truform=0" under [Video Options] with "Enable Truform=1"to enable a more round appearance on round objects, if that line isn't there then just copy and paste "Enable Truform=1" without the quotes.*


[SIZE="3"]**3. Possible permissions issues**[/SIZE]

_Solution:_
Highlight all the files in nwn folder, not the folders and right click, select permissions tab and set all option to anyone. Do this in all folders inside nwn folder. For some reason if you right click the folder(s) and go under permissions tab the option to make executable isn't there, and it will set all files to non-exacutable. So you will need to do all files inside the folder, and not the folder. Symlinks will give an error **that is normal.**


[SIZE="3"]**4. Help I cant see my character**[/SIZE]

_Solution:_
Disable Creature environment mapping in "options->video options>advanced video options" in game or change "Enable CreatureEnvironmentMapping=1" to "Enable CreatureEnvironmentMapping=0" in the nwn.ini file inside you nwn folder. I don't have this issue but some people do


[SIZE="3"]**5. Missing gui layout file error**[/SIZE]

_Solution:_
The data files off the disk were not fully copied, you will need to redo step 4 of installing nwn


[SIZE="3"]**6. Other sound options**[/SIZE]

Optionally if sound isn't working you can try to enter either of these lines in your nwn file inside you nwn folder.

export SDL_AUDIODRIVERS=alsa

export SDL_AUDIODRIVERS=pulse


[COLOR="Magenta"]***Movies in 64bit!***[/COLOR]

[SIZE="3"]**1. You need to make sure you have the appropriate 32bit libs then try to symlink them in the nwn folder**[/SIZE] (see below if there is an error)

_Code:_
cd /home/**user_name**/nwn

ln -s /usr/lib/i386-linux-gnu/libX11.so.6 libX11.so. (32bit will have to search where the file libX11.so.6 is at)

ln -s /usr/lib32/i386-linux-gnu/libSDL_gfx.so libSDL_gfx.so (32bit will have to search where the file libSDL_gfx.so is at)


[SIZE="3"]**2. Now you need to edit your nwn.ini.**[/SIZE]

Open your file manager and open the folder nwn, then right click the nwn.ini folder and pick your text editor. Under [Display Options] change the line "FullScreen=0" to "FullScreen=1" or add the line "FullScreen=1" if the option isn't there. Also add the line "AllowWindowedMode=0"


**[SIZE="3"]3. Now you need to edit your nwmovies.pl**[/SIZE]

Open your file manager and open the folder nwn and then nwmovies. Right click nwmovies.pl and pick you text editor. you will need to put a "#" symbol infront of the lines $ENV{"BINK_SCALE"} = 1;, $ENV{"BINK_SMOOTH"} = 1;, and $ENV{"BINK_NOPERF"} = 1; so they look like this

#$ENV{"BINK_SCALE"} = 1;
#$ENV{"BINK_SMOOTH"} = 1;
#$ENV{"BINK_NOPERF"} = 1;

and add these lines if you are using a resolution of 1024x768 in game and computer so the movies will be at same resolution.

#$ENV{"BINK_WIDTH"} = $1024;
#$ENV{"BINK_HEIGHT"} = $768;


[SIZE="3"]**4. You need to make sure that "binklib.so" is in your nwmovies folder.**[/SIZE]

Open your file manager and go to your nwn folder, then open your nwnmovies folder and make sure it is in there. If it isn't then you will need to download BinkLinuxPlayer.7z, decompress it and copy the file binklib.so to your /nwn/nwmovies folder.


[SIZE="3"]**5. If there was an error when trying to symlink the libSDL_gfx.so file then you need to download getlibs-all (64bit only, not in repository)**[/SIZE]

_Code:_
wget http://usablesoftware.files.wordpress.com/2011/02/getlibs-all-deb.pdf

Then delete the .pdf extension, it isnt a pdf, that is because wordpress didn't allow the .deb extension. Right click the resulting .deb file and install. Then you will need to install the libSDL_gfx.so file

_Code:_
getlibs -l libSDL_gfx.so

That will install the appropriate file and then you may symlink it. If it complains of permissions use sudo.

---

### Post by vanquishedangel on 2012-11-10
My system specs are:

Computer: hpdc5750
Operating System: Lubuntu 12.10 64bit
Processor: amd 4800+ 2.5ghz dual core processor
Memmory: 8gigs ram
Graphics card: Saffire ATI Radeon HD 6450, 1gig vram (Overclocked with amdoverdrivectl)

All software I have is from the repositories already in ubuntu except amdoverdrivectl and getlibs-all, my graphics drivers are proprietary ones from the repositories.

---

### Post by vanquishedangel on 2012-11-28
I also have Kingmaker, Witches Wake, Infinite dungeons, Wyvern crown, Pirates of the Sword Coast, and Shadow Guard working. I also have aurora toolset and nwhak.exe working from my nwn directory, it was rather easy, I copied the utils folder to my native nwn, and I copied nwtoolset.exe and Mss32.dll.

To download load the files for linux here:


**_Kingmaker:_**

wget http://content.bioware.com/neverwinternights/modules_premium/Kingmaker.zip


**_Witches Wake and Shadow Guard:_**

wget http://content.bioware.com/neverwinternights/modules_premium/ShadowGuardPlusWitchsWake.zip


**_Infinite dungeons:_**

wget http://bioware.vo.llnwd.net/o1/neverwinternights/modules_premium/InfiniteDungeons.zip


**_Wyvern crown:_**

wget http://bioware.vo.llnwd.net/o1/neverwinternights/modules_premium/WyvernCrown.zip


**_Pirates of the Sword Coast:_**

wget http://content.bioware.com/neverwinternights/modules_premium/PiratesOfTheSwordCoast.zip


And to install these you would do it the same as you would a module from the community. I have purchased these modules before so they may not work if you have bad cd keys and that I cannot help you with.


**Aurora Toolset and nwhak.exe**

I did this by installing nwn into wine (playonlinux) and then just coping the utils folder, nwtoolset.exe and Mss32.dll over to my nwn directory, then deleted the wine install of nwn (playonlinux).

to run them navigate to your nwn folder, right click the exe and choose wine.

I did not copy mwtoolset.ini from wine, I just used the one that was in my nwn folder.



**Hardware Mouse**


For hardware mouse instead of software mouse:

wget http://home.roadrunner.com/~nwmovies/nwmouse/nwmouse-latest.tar.gz

And follow the included instructions (may have errors)



**Updated textures and many good extras**


For better graphics and many extras go here: (It wont place the link XD)

http://social,bioware,com/forum/1/topic/199/index/3275241 (replace comma's with a [.]).

---

### Post by oldrocker99 on 2012-11-28
Fantastic! I had bought Infinite Dungeons back in 2008, and lost everything in a HD crash. It was (apparently) unavailable, until I saw your post. THANK YOU!

PS: Tried all the Premium modules, and they all work after taking a few seconds to "validate." Apparently, if you have a legit copy of Neverwinter Nights (and these days, who doesn't?), the modules validate just fine.

Between the Premium Modules' availability and this:

[http://ubuntuforums.org/showthread.php?t=2084592](http://ubuntuforums.org/showthread.php?t=2084592)

it's a Red Letter Day for Ubuntu users!

---

### Post by vanquishedangel on 2012-12-01
J

---

### Post by Sarys on 2012-12-04
If someone could tell me how to get this game to work from gog I'd be happy
Oh yeah I have 12.04

---

### Post by vanquishedangel on 2012-12-04
j

---

### Post by paridoth on 2012-12-06
> **vanquishedangel said:**
> 
[SIZE="3"]**5. Download nwclientgold.tar.gz (7.2 MB) and extract it into the destination directory (overwriting all).**[/SIZE]

_Code:_
wget [http://nwdownloads.bioware.com/neverwinternights/linux/gold/nwclientgold.tar.gz](http://nwdownloads.bioware.com/neverwinternights/linux/gold/nwclientgold.tar.gz)

tar -xzf ~/nwclientgold.tar.gz




I am getting ```
paridoth@sony-ubuntu:~/nwn$ tar -xzf ~/nwclientgold.tar.gz
tar: nwn: Cannot open: File exists
tar: Exiting with failure status due to previous errors
```

it looks like all the files extracted except nwn.

---

### Post by vanquishedangel on 2012-12-06
> **paridoth said:**
> I am getting ```
paridoth@sony-ubuntu:~/nwn$ tar -xzf ~/nwclientgold.tar.gz
tar: nwn: Cannot open: File exists
tar: Exiting with failure status due to previous errors
```

it looks like all the files extracted except nwn.

That is certainly weird, are you in the folder you created in step 2?

cd /home/**USER_NAME**/nwn

Also you can extract nwclientgold.tar.gz by right clicking and selecting "extract to" and choose the nwn folder you created in step 2. (if the nwn file is already in the nwn folder you may not need to worry, just overwrite it when asked or continue on)

Also you may need to install unshield from synaptic

I haven't seen this error at all so I am not sure what caused it, could be that files were extracted in the wrong order, or your terminal is in your home directory and not in your nwn directory. Also you may need to set permissions on the files in the nwn folder (permissions can cause alot of issues for the native install of nwn, right click the nwn file, select properties, go to permissions tab, set all to anyone).

maybe need to try to redownload it, file could have corrupted.

---

### Post by paridoth on 2012-12-06
> **vanquishedangel said:**
> That is certainly weird, are you in the folder you created in step 2?

cd /home/**USER_NAME**/nwn

Also you can extract nwclientgold.tar.gz by right clicking and selecting "extract to" and choose the nwn folder you created in step 2. (if the nwn file is already in the nwn folder you may not need to worry, just overwrite it when asked or continue on)

Also you may need to install unshield from synaptic

I haven't seen this error at all so I am not sure what caused it, could be that files were extracted in the wrong order, or your terminal is in your home directory and not in your nwn directory. Also you may need to set permissions on the files in the nwn folder (permissions can cause alot of issues for the native install of nwn, right click the nwn file, select properties, go to permissions tab, set all to anyone).

i think i figured it out, i extracted the iso's to a folder in the nwn folder called nwn so when i was extracting to the nwn folder it was trying to create a folder i had already created for the contents of the iso, ill retry from the begining with a diff folder for my iso contents.
edit:
Ok i redid everything and it seemed to be all be going well then this hapened.
```
paridoth@sony-ubuntu:~/nwn$ ./fixinstall
Checking for required files

PASSED: ambient directory exists
PASSED: data directory exists
PASSED: music directory exists
PASSED: override directory exists
PASSED: miles directory exists
PASSED: nwm directory exists
PASSED: chitin.key exists
PASSED: dialog.tlk exists
PASSED: nwmain exists

Fixing case

ambient
............................................................................................................
data
.............................
dmvault
..
hak
.
localvault
.......................
music
................................................................................
override
.............

Checking for problem files


Checking for permissions

PASSED: nwn.ini is writable
PASSED: nwnplayer.ini is writable
PASSED: nwncdkey.ini is writable
PASSED: saves is writable
PASSED: localvault is writable
PASSED: tempclient is writable
PASSED: dmvault is writable
PASSED: /home/paridoth/nwn is writable

You are ready to run Neverwinter Nights.

paridoth@sony-ubuntu:~/nwn$ ./nwn
Fatal signal: Segmentation Fault (SDL Parachute Deployed)
```

---

### Post by vanquishedangel on 2012-12-06
> **paridoth said:**
> i think i figured it out, i extracted the iso's to a folder in the nwn folder called nwn so when i was extracting to the nwn folder it was trying to create a folder i had already created for the contents of the iso, ill retry from the begining with a diff folder for my iso contents.
edit:
Ok i redid everything and it seemed to be all be going well then this hapened.
```
paridoth@sony-ubuntu:~/nwn$ ./fixinstall
Checking for required files

PASSED: ambient directory exists
PASSED: data directory exists
PASSED: music directory exists
PASSED: override directory exists
PASSED: miles directory exists
PASSED: nwm directory exists
PASSED: chitin.key exists
PASSED: dialog.tlk exists
PASSED: nwmain exists

Fixing case

ambient
............................................................................................................
data
.............................
dmvault
..
hak
.
localvault
.......................
music
................................................................................
override
.............

Checking for problem files


Checking for permissions

PASSED: nwn.ini is writable
PASSED: nwnplayer.ini is writable
PASSED: nwncdkey.ini is writable
PASSED: saves is writable
PASSED: localvault is writable
PASSED: tempclient is writable
PASSED: dmvault is writable
PASSED: /home/paridoth/nwn is writable

You are ready to run Neverwinter Nights.

paridoth@sony-ubuntu:~/nwn$ ./nwn
Fatal signal: Segmentation Fault (SDL Parachute Deployed)
```

Good news is the game is successfully installed :)

From a brief search on the internet it seems that may be a permissions issue, How I solved this was I highlighted all the files (not folders) in nwn and right clicked, properties, permissions tab, and set all to anyone. I opened every folder and did that to every file in nwn.

Maybe "sudo chmod -R nwn" would work but I really don't know much about "chmod" so try at your own risk, "maybe sudo chmod 755 nwn", I got the reference for chmod here: [http://forums.gentoo.org/viewtopic-t-493171.html](http://forums.gentoo.org/viewtopic-t-493171.html)

or try "sudo chmod -c -R 777 nwn" according to here but it didn't work for him: [http://ubuntuforums.org/archive/index.php/t-464467.html](http://ubuntuforums.org/archive/index.php/t-464467.html)

could try editing the nwn file to see if it is in there like maybe you need the ./lib: in the line in that file (doubt this one but who knows)

possible a file didn't fully copy over correct, I had a noGui file issue when I first installed, a data pack didn't install correctly.

A good explanation of that error is here: [http://forums.justlinux.com/showthread.php?142043-SDL-Parachute-Deployed](http://forums.justlinux.com/showthread.php?142043-SDL-Parachute-Deployed)

Also check your nwn logfile (in logs folder) for clues

---

### Post by paridoth on 2012-12-06
contents of my nwn file

```
#!/bin/sh

# This script runs Neverwinter Nights from the current directory

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=./lib:./miles:$LD_LIBRARY_PATH

./nwmain $@
```

every file is set for read write for my user, i will delete and  try from step one to see if that works, thanks for your time =)

---

### Post by oldrocker99 on 2012-12-07
> **paridoth said:**
> contents of my nwn file

```
#!/bin/sh

# This script runs Neverwinter Nights from the current directory

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=./lib:./miles:$LD_LIBRARY_PATH

./nwmain $@
```

every file is set for read write for my user, i will delete and  try from step one to see if that works, thanks for your time =)

What I have done is make a copy of the "export LD_LIBRARY_PATH..." line and paste it under the original. Then I add # to the beginning of one line to comment it out. Then render the other line thus (for a 32-bit system):

export LD_LIBRARY_PATH=./miles:$LD_LIBRARY_PATH

On my 64-bit system, the line reads:

export LD_LIBRARY_PATH=./miles/usr/lib32:LD_LIBRARY_PATH

I awlays keep a commented copy of a line I'm editing, just so I have a fresh copy to edit if I hose something.

Good luck!

---

### Post by paridoth on 2012-12-07
so no more parachute error, yay. i run ./nwn and now i just have a an empty terminal with a blinking promp ( so it thinks its doing something ) nothing in the log folder and no output in the terminal. my new nwn file
```
#!/bin/sh

# This script runs Neverwinter Nights from the current directory

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
#export LD_LIBRARY_PATH=./lib:./miles:$LD_LIBRARY_PATH
export LD_LIBRARY_PATH=./miles:$LD_LIBRARY_PATH

./nwmain $@
```

---

### Post by vanquishedangel on 2012-12-07
> **paridoth said:**
> so no more parachute error, yay. i run ./nwn and now i just have a an empty terminal with a blinking promp ( so it thinks its doing something ) nothing in the log folder and no output in the terminal. my new nwn file
```
#!/bin/sh

# This script runs Neverwinter Nights from the current directory

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
#export LD_LIBRARY_PATH=./lib:./miles:$LD_LIBRARY_PATH
export LD_LIBRARY_PATH=./miles:$LD_LIBRARY_PATH

./nwmain $@
```


Here is a copy of mine:


#!/bin/sh

# This script runs Neverwinter Nights from the current directory

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0
export SDL_AUDIODRIVER=alsa (not needed if sound works, only for alsa drivers)

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=:./miles:$LD_LIBRARY_PATH
export NWMOVIES_GRAB_HACK=1
export XCURSOR_PATH=`pwd` (only for hardware mouse)
export XCURSOR_THEME=nwmouse (only for hardware mouse)
export LD_PRELOAD=./nwmovies.so:./nwmouse.so (add this ":./nwmouse.so" only for hardware mouse)

./nwmain $@


You are missing the lines "export NWMOVIES_GRAB_HACK=1" and "export LD_PRELOAD=./nwmovies.so" if you installed the movies. check the log file for binkplayer (nwmovies.log), there is always alot in there but it seems like the movies are playing but you cant see them. if you copy mine, you need the hardware mouse installed and alsa drivers and dont copy the  () or the text in between, or leave those lines out.

The blinking prompt is most likely cause it is running the movies :) try and see if hitting the "esc" key a bunch of times works. I don't know if it will but ingame the esc key cancels the movies and ads.

I also have a tons of crap installed (updated textures, creature and several other things like the hardware mouse) so many of my files will be different.

---

### Post by paridoth on 2012-12-07
well better results.

current nwn
```
#!/bin/sh

# This script runs Neverwinter Nights from the current directory

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=:./miles:$LD_LIBRARY_PATH
export NWMOVIES_GRAB_HACK=1
export LD_PRELOAD=./nwmovies.so:

./nwmain $@
```

what i did
```
paridoth@sony-ubuntu:~/nwn$ ./nwn
NOTICE: NWMovies(./nwmain): Version: 20090223.080954
NOTICE: Looking up symbols in libSDL.....
NOTICE: NWMovies: Using libSDL via RTLD_NEXT.
NOTICE: SDL Library determined to be: /usr/lib/i386-linux-gnu/libSDL-1.2.so.0
NOTICE: NWMovies: SDL_WM_GrabInput() address: b75970b0
NOTICE: NWMovies: SDL_GetVideoSurface() address: b7595450
NOTICE: NWMovies: SDL_WM_ToggleFullScreen() address: b7598470
NOTICE: NWMovies: SDL_PollEvent() address: b75747a0
NOTICE: NWMovies: SDL_WM_IconifyWindow() address: b7598440
WARNING: NWMovies: No INI file.  Creating.
WARNING: NWMovies: INI recalculation required: 7780208:0 1215115938:0
NOTICE: NWMovies: (cookie) Entry point determined: 0x7830
NOTICE: NWMovies: (cookie) Searching executable: 28
NOTICE: NWMovies: (cookie) Cookie location: 0x1aec3e
NOTICE: NWMovies: (cookie) Searching executable: 29
NOTICE: NWMovies: (cookie) Call Location #1: 00028264
NOTICE: NWMovies: (cookie) Call Location #2: 00028278
NOTICE: NWMovies: (cookie) Call Location #3: 00028134
NOTICE: NWMovies: (cookie) Searching executable: 16
NOTICE: NWMovies: (cookie) Searching executable: 02
NOTICE: NWMovies: (cookie) Searching executable: 02
NOTICE: NWMovies: (cookie) Searching executable: 18
NOTICE: NWMovies: (cookie) Searching executable: 02
NOTICE: NWMovies: (movies) Searching executable: 28
NOTICE: NWMovies: (movies) Searching executable: 30
NOTICE: NWMovies: (movies) Cookie start_location: 0x1b8005
NOTICE: NWMovies: (movies) Searching executable: 30
NOTICE: NWMovies: (movies) Cookie end_location: 0x1b8028
NOTICE: NWMovies: (cookie) Recalculated calls 0: 08077a9d
NOTICE: NWMovies: (cookie) Recalculated calls 1: 08077ab1
NOTICE: NWMovies: (cookie) Recalculated calls 2: 0815b5f7
NOTICE: NWMovies: (cookie) Recalculated calls 3: 0815b611
NOTICE: NWMovies: (cookie) Recalculated calls 4: 0807796f
NOTICE: NWMovies: (movies) Recalculated calls 5: 08207835
NOTICE: NWMovies: (movies) Recalculated calls 6: 08207858
NOTICE: NWMovies: INI File written: Now exiting.  This is perfectly normal!
NOTICE: Your next run of NWN should be complete, and include movies.
28paridoth@sony-ubuntu:~/nwn$ ./nwn
NOTICE: NWMovies(./nwmain): Version: 20090223.080954
NOTICE: Looking up symbols in libSDL.....
NOTICE: NWMovies: Using libSDL via RTLD_NEXT.
NOTICE: SDL Library determined to be: /usr/lib/i386-linux-gnu/libSDL-1.2.so.0
NOTICE: NWMovies: SDL_WM_GrabInput() address: b751d0b0
NOTICE: NWMovies: SDL_GetVideoSurface() address: b751b450
NOTICE: NWMovies: SDL_WM_ToggleFullScreen() address: b751e470
NOTICE: NWMovies: SDL_PollEvent() address: b74fa7a0
NOTICE: NWMovies: SDL_WM_IconifyWindow() address: b751e440
NOTICE: NWMovies: Patch 0 Address: 0x08077a9d
NOTICE: NWMovies: Patch 1 Address: 0x08077ab1
NOTICE: NWMovies: Patch 2 Address: 0x0815b5f7
NOTICE: NWMovies: Patch 3 Address: 0x0815b611
NOTICE: NWMovies: Patch 4 Address: 0x0807796f
NOTICE: NWMovies: Patch 5 Address: 0x08207835
NOTICE: NWMovies: Patch 6 Address: 0x08207858
NOTICE: NWMovies: PrePatch0: 8b 80 78 02 00 00 5d c3 
NOTICE: NWMovies: PrePatch1: 8b 80 7c 02 00 00 5d c3 
NOTICE: NWMovies: PrePatch2: e8 68 c5 f1 ff 83 ec 08 
NOTICE: NWMovies: PrePatch3: 169+: eb 59 90 83 
NOTICE: NWMovies: PostPatch0: b8 00 00 00 00 90 5d c3 
NOTICE: NWMovies: PostPatch1: b8 00 00 00 00 90 5d c3 
NOTICE: NWMovies: PostPatch2: 90 90 90 90 90 83 ec 08 
NOTICE: NWMovies: PostPatch3: 169+: 90 90 90 83 
NOTICE: NWMovies: PrePatch4: 56 8d 5d e8 53 
NOTICE: NWMovies: PostPatch4: e9 20 d4 6c af 
NOTICE: NWMovies: MoviesPrePatch: 6a 00 53 bf 00 00 00 3f e8 72 4f 2a 00 8b 43 60 8b 10 c7 04 24 00 00 80 3f 57 57 57 50 ff 52 44 83 c4 1c 
NOTICE: NWMovies: MoviesPostPatch: 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 
NOTICE: NWMovies: Initialized.

```
and here i sit with a blinking command prompt. ls command contents of my nwn folder
[IMG]http://i.imgur.com/VfloR.jpg[/IMG]

---

### Post by vanquishedangel on 2012-12-08
> **paridoth said:**
> well better results.

current nwn
```
#!/bin/sh

# This script runs Neverwinter Nights from the current directory

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=:./miles:$LD_LIBRARY_PATH
export NWMOVIES_GRAB_HACK=1
export LD_PRELOAD=./nwmovies.so:

./nwmain $@
```

what i did
```
paridoth@sony-ubuntu:~/nwn$ ./nwn
NOTICE: NWMovies(./nwmain): Version: 20090223.080954
NOTICE: Looking up symbols in libSDL.....
NOTICE: NWMovies: Using libSDL via RTLD_NEXT.
NOTICE: SDL Library determined to be: /usr/lib/i386-linux-gnu/libSDL-1.2.so.0
NOTICE: NWMovies: SDL_WM_GrabInput() address: b75970b0
NOTICE: NWMovies: SDL_GetVideoSurface() address: b7595450
NOTICE: NWMovies: SDL_WM_ToggleFullScreen() address: b7598470
NOTICE: NWMovies: SDL_PollEvent() address: b75747a0
NOTICE: NWMovies: SDL_WM_IconifyWindow() address: b7598440
WARNING: NWMovies: No INI file.  Creating.
WARNING: NWMovies: INI recalculation required: 7780208:0 1215115938:0
NOTICE: NWMovies: (cookie) Entry point determined: 0x7830
NOTICE: NWMovies: (cookie) Searching executable: 28
NOTICE: NWMovies: (cookie) Cookie location: 0x1aec3e
NOTICE: NWMovies: (cookie) Searching executable: 29
NOTICE: NWMovies: (cookie) Call Location #1: 00028264
NOTICE: NWMovies: (cookie) Call Location #2: 00028278
NOTICE: NWMovies: (cookie) Call Location #3: 00028134
NOTICE: NWMovies: (cookie) Searching executable: 16
NOTICE: NWMovies: (cookie) Searching executable: 02
NOTICE: NWMovies: (cookie) Searching executable: 02
NOTICE: NWMovies: (cookie) Searching executable: 18
NOTICE: NWMovies: (cookie) Searching executable: 02
NOTICE: NWMovies: (movies) Searching executable: 28
NOTICE: NWMovies: (movies) Searching executable: 30
NOTICE: NWMovies: (movies) Cookie start_location: 0x1b8005
NOTICE: NWMovies: (movies) Searching executable: 30
NOTICE: NWMovies: (movies) Cookie end_location: 0x1b8028
NOTICE: NWMovies: (cookie) Recalculated calls 0: 08077a9d
NOTICE: NWMovies: (cookie) Recalculated calls 1: 08077ab1
NOTICE: NWMovies: (cookie) Recalculated calls 2: 0815b5f7
NOTICE: NWMovies: (cookie) Recalculated calls 3: 0815b611
NOTICE: NWMovies: (cookie) Recalculated calls 4: 0807796f
NOTICE: NWMovies: (movies) Recalculated calls 5: 08207835
NOTICE: NWMovies: (movies) Recalculated calls 6: 08207858
NOTICE: NWMovies: INI File written: Now exiting.  This is perfectly normal!
NOTICE: Your next run of NWN should be complete, and include movies.
28paridoth@sony-ubuntu:~/nwn$ ./nwn
NOTICE: NWMovies(./nwmain): Version: 20090223.080954
NOTICE: Looking up symbols in libSDL.....
NOTICE: NWMovies: Using libSDL via RTLD_NEXT.
NOTICE: SDL Library determined to be: /usr/lib/i386-linux-gnu/libSDL-1.2.so.0
NOTICE: NWMovies: SDL_WM_GrabInput() address: b751d0b0
NOTICE: NWMovies: SDL_GetVideoSurface() address: b751b450
NOTICE: NWMovies: SDL_WM_ToggleFullScreen() address: b751e470
NOTICE: NWMovies: SDL_PollEvent() address: b74fa7a0
NOTICE: NWMovies: SDL_WM_IconifyWindow() address: b751e440
NOTICE: NWMovies: Patch 0 Address: 0x08077a9d
NOTICE: NWMovies: Patch 1 Address: 0x08077ab1
NOTICE: NWMovies: Patch 2 Address: 0x0815b5f7
NOTICE: NWMovies: Patch 3 Address: 0x0815b611
NOTICE: NWMovies: Patch 4 Address: 0x0807796f
NOTICE: NWMovies: Patch 5 Address: 0x08207835
NOTICE: NWMovies: Patch 6 Address: 0x08207858
NOTICE: NWMovies: PrePatch0: 8b 80 78 02 00 00 5d c3 
NOTICE: NWMovies: PrePatch1: 8b 80 7c 02 00 00 5d c3 
NOTICE: NWMovies: PrePatch2: e8 68 c5 f1 ff 83 ec 08 
NOTICE: NWMovies: PrePatch3: 169+: eb 59 90 83 
NOTICE: NWMovies: PostPatch0: b8 00 00 00 00 90 5d c3 
NOTICE: NWMovies: PostPatch1: b8 00 00 00 00 90 5d c3 
NOTICE: NWMovies: PostPatch2: 90 90 90 90 90 83 ec 08 
NOTICE: NWMovies: PostPatch3: 169+: 90 90 90 83 
NOTICE: NWMovies: PrePatch4: 56 8d 5d e8 53 
NOTICE: NWMovies: PostPatch4: e9 20 d4 6c af 
NOTICE: NWMovies: MoviesPrePatch: 6a 00 53 bf 00 00 00 3f e8 72 4f 2a 00 8b 43 60 8b 10 c7 04 24 00 00 80 3f 57 57 57 50 ff 52 44 83 c4 1c 
NOTICE: NWMovies: MoviesPostPatch: 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 
NOTICE: NWMovies: Initialized.

```
and here i sit with a blinking command prompt. ls command contents of my nwn folder
[IMG]http://i.imgur.com/VfloR.jpg[/IMG]

I am having a hard time figuring it out lol, I have many files you wouldn't.

Try installing unshield (for drm issues) from synaptic, (or sudo apt-get install unshield) make sure you are using proprietary drivers for your graphics card. I will continue to search this out, I may have an idea. Also try running it in windowed mode by editing nwn.ini and under display options add or edit the lines to look like this

FullScreen=0
AllowWindowedMode=1

and see if it runs, some have had issues with fullscreen mode. also remove the ":" from "export LD_PRELOAD=./nwmovies.so:" so it looks like this "export LD_PRELOAD=./nwmovies.so"

---

### Post by rasmus91 on 2012-12-25
Hello all, I've been trying for a couple of hours now, and i just can't make it work. this is what happens when i run ./nwn

```
NOTICE: NWMovies(./nwmain): Version: 20090223.080954
NOTICE: Looking up symbols in libSDL.....
NOTICE: NWMovies: Using libSDL via RTLD_NEXT.
NOTICE: SDL Library determined to be: /usr/lib/i386-linux-gnu/libSDL-1.2.so.0
NOTICE: NWMovies: SDL_WM_GrabInput() address: f74b30b0
NOTICE: NWMovies: SDL_GetVideoSurface() address: f74b1450
NOTICE: NWMovies: SDL_WM_ToggleFullScreen() address: f74b4470
NOTICE: NWMovies: SDL_PollEvent() address: f74907a0
NOTICE: NWMovies: SDL_WM_IconifyWindow() address: f74b4440
NOTICE: NWMovies: Patch 0 Address: 0x08077a9d
NOTICE: NWMovies: Patch 1 Address: 0x08077ab1
NOTICE: NWMovies: Patch 2 Address: 0x0815b5f7
NOTICE: NWMovies: Patch 3 Address: 0x0815b611
NOTICE: NWMovies: Patch 4 Address: 0x0807796f
NOTICE: NWMovies: Patch 5 Address: 0x08207835
NOTICE: NWMovies: Patch 6 Address: 0x08207858
NOTICE: NWMovies: PrePatch0: 8b 80 78 02 00 00 5d c3 
NOTICE: NWMovies: PrePatch1: 8b 80 7c 02 00 00 5d c3 
NOTICE: NWMovies: PrePatch2: e8 68 c5 f1 ff 83 ec 08 
NOTICE: NWMovies: PrePatch3: 169+: eb 59 90 83 
NOTICE: NWMovies: PostPatch0: b8 00 00 00 00 90 5d c3 
NOTICE: NWMovies: PostPatch1: b8 00 00 00 00 90 5d c3 
NOTICE: NWMovies: PostPatch2: 90 90 90 90 90 83 ec 08 
NOTICE: NWMovies: PostPatch3: 169+: 90 90 90 83 
NOTICE: NWMovies: PrePatch4: 56 8d 5d e8 53 
NOTICE: NWMovies: PostPatch4: e9 20 f4 66 ef 
NOTICE: NWMovies: MoviesPrePatch: 6a 00 53 bf 00 00 00 3f e8 72 4f 2a 00 8b 43 60 8b 10 c7 04 24 00 00 80 3f 57 57 57 50 ff 52 44 83 c4 1c 
NOTICE: NWMovies: MoviesPostPatch: 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 
NOTICE: NWMovies: Initialized.

```

and then a cursor occurs that just stand there blinking.

my nwn file looks like this:

```
#!/bin/sh

# This script runs Neverwinter Nights from the current directory

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0

rm miles
ln -s miles_linux miles

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
#export LD_LIBRARY_PATH=./lib:./miles:"$LD_LIBRARY_PATH"

export LD_LIBRARY_PATH=./miles/usr/lib32:LD_LIBRARY_PATH

export LD_PRELOAD=./nwmovies.so
./nwmain $@

rm miles
ln -s miles_win miles
```

i tried adding:

```
export NWMOVIES_GRAB_HACK=1
```

but it didn't change anything. any insight? 
i would really like to play this game again.

---

### Post by Xo-Mige on 2012-12-25
As I was reading this and just got the movies to work

made the nwmovies.pl exicutable with

chmod a+x nwmovies.pl

I followed the instructions in the original post about linking the .so files and editing the nwn.ini file

the contents of my nwn launch script is:

```
#!/bin/sh

# This script runs Neverwinter Nights from the current directory
cd ~/nwn
#it now runs in the proper one
#export SDL_MOUSE_RELATIVE=0
#export SDL_VIDEO_X11_DGAMOUSE=0
#export SDL_DSP_NOSELECT=1
#export SDL_AUDIODRIVER=alsa
#export SDL_AUDIODRVERS=pulse

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=./miles:$LD_LIBRARY_PATH
export LD_PRELOAD=./nwmovies.so
export NWMOVIES_GRAB_HACK=1

./nwmain $@
``` notice I don't use the "./lib:" part and the two lines under the export library part

I hope this helps someone as I spent all day figering this out

additionaly if when you do "./nwmovies.pl " it says
```

NOTICE: NWMovies.pl playing: : Tue Dec 25 16:24:14 2012
ERROR: NWMovies.pl: Missing movie file: 
NOTICE: NWMovies.pl finished playing: : Tue Dec 25 16:24:14 2012
``` then you need to edit the nwn.ini with the 
FullScreen=1
AllowWindowedMode=0

options otherwise if  "./nwmovies.pl " "permission denied: ./nwmovies.pl"
 then chmod a+x nwmovies.pl

---

### Post by gtmaneki on 2013-01-13
I recently switched computers.  Aside from replacing six-year-old hardware with newer stuff, I also switched from Ubuntu 12.04 32-bit to 12.10 64-bit.  

I copied over all my NWN files that had worked so well on the old computer, installed all the libraries, but when I launch NWN now it hangs.  I see the nwmain process running, but the game never starts. 

ldd confirms all the libraries are in place.  Any suggestions as to what I'm doing wrong?

---

### Post by vanquishedangel on 2013-03-10
Sorry so long to respond, I am in school again. I dont really know at this point however try making the short cuts again (not for game but for files) I would run through the guide again to see if it is some to with the system.

---

### Post by frankob on 2013-03-29
> **gtmaneki said:**
> I recently switched computers.  Aside from replacing six-year-old hardware with newer stuff, I also switched from Ubuntu 12.04 32-bit to 12.10 64-bit.  

I copied over all my NWN files that had worked so well on the old computer, installed all the libraries, but when I launch NWN now it hangs.  I see the nwmain process running, but the game never starts. 

ldd confirms all the libraries are in place.  Any suggestions as to what I'm doing wrong?

That's pretty much the same thing happening to me. The main difference is that I didn't even change hardware nor architecture. I have just upgraded my laptop from Precise 64 to Quantal 64. In Precise it was working nicely, in Quantal it just hangs there, as described by gtmaneki. I even tried to redo the installation proces, but no luck -- it just hangs there. I really can't figure out what is causing this... So any idea would be still VERY appreciated. Thanks!

EDIT: Oh, and I forgot to say that I don't have the Diamond edition but the Deluxe one. But the installation process described here is pretty much identical to what I did years ago... So I see no reason why it wouldn't work now.

---

### Post by Sanus Compleo on 2013-04-02
Having the same problem here.

Enjoying NWN isn't getting easier, is it?

---

### Post by frankob on 2013-04-07
I guess it's not... :-/

---

### Post by vanquishedangel on 2013-04-11
I am pretty sure it is because the symlinks are off, and also the symlinks for the files in ia32, it is possible that some of them either moved or have slightly different names, however mine still works so i cannot reproduce the issue here,  but I am on the same computer.

You could try a reinstall, run ./fixinstall again maybe and check out any errors also check out the logs in the log files  somewhere in you nwn folder. Sorry i cant be of much help, being in school again  takes up my time.

---

### Post by vanquishedangel on 2013-04-11
> **frankob said:**
> That's pretty much the same thing happening to me. The main difference is that I didn't even change hardware nor architecture. I have just upgraded my laptop from Precise 64 to Quantal 64. In Precise it was working nicely, in Quantal it just hangs there, as described by gtmaneki. I even tried to redo the installation proces, but no luck -- it just hangs there. I really can't figure out what is causing this... So any idea would be still VERY appreciated. Thanks!

EDIT: Oh, and I forgot to say that I don't have the Diamond edition but the Deluxe one. But the installation process described here is pretty much identical to what I did years ago... So I see no reason why it wouldn't work now.


If you switched to 64bit i assume the problem is with a few things. like ia32libs and the symlinks wont match up, so they would all need to be redone, cant be copied over. some have totally changed the file location on the computer even. You would need to  redo the symlinks because they lead to the location of where the 3bit libs were on a 32bit system, they are located different places on a 64bit.

This is just one possability, it could be something wasnt installed, or a name of a file changed, mae sure you all have the sdl libraries to.l and you 
ay need to mae sure you have the 32 bit o0nes, dont forget multiarch as well.

---

### Post by frankob on 2013-04-18
As I said:
> ...**I didn't** even **change** hardware nor **architecture**., gtmaneki did.

In my case, everything is the same. At first It was complaining something about a lib, as usual after I upgrade my system. I fixed that, and it just hangs there, and not showing any error anywhere. So I really don't know what to do next.
I don't believe it's the symlinks, because in those cases it complains about missing libs or something... But than again, if it IS something about the links, where should any of us start from? It really doesn't show any error anywehere. I even tried to redo the whole intallation process -- same result.
It is obvious that there is something different with the system, but I can't figure out what...

Raring is coming soon. Who knows if there NWN will "magically" start to work again...

---

### Post by vanquishedangel on 2013-04-27
I updated to 13.04 and my nwn is still working fine, actually its working a little faster. sorry as i said I cant be of much help atm but I know skildron is still active in the forums on social bioware com (the spaces are periods, it wont let me post a link) so maybe if you post there some of them could help those of you still having issues.

---

### Post by mactalla on 2013-06-12
I ran into the same issue on 13.04 with NWN refusing to start.  With ./libs in the LD path it would segfault and without it it would hang (kill -9 required).

This fixed it for me:

```
sudo mv /usr/lib/i386-linux-gnu/libtxc_dxtn.so /usr/lib/i386-linux-gnu/libtxc_dxtn.nwncrapsout.so
```

---

### Post by Colsta on 2013-10-06
mactalla: please award yourself an extra choccie biccie from me.  Identical symptoms and a very frustrating 2 days.  Your trick works for me :)  How did you track it down to that particular lib?

---

### Post by MichelMatos on 2014-04-07
mactalla: as Colsta told: you deserve a special prize. It worked here too! The question is: why? why does it work this way? :)

---

### Post by MichelMatos on 2014-04-07
And vanquishedangel, your setup for hardware mouse worked very good here too. I was slowly and jumping. Now it's good. No movies here. I dont need them ;)

---

### Post by oldrocker99 on 2014-04-08
I had to rely on 32-bit libraries installed by PlayOnLinux in ~/.PlayOnLinux/wine/linux-x86/1.4-dos_support_0.5, and copied libSDL-1.2.so.0, libesd.so.0, libdirectfb-1.2.so.0, libfusion-1.2.so.0, libdirect-1.2.so.0, libaa.so.1, libaudiofile.so.0 to ~/nwn,  and had to rename a couple before ./nwn would start the game on my 14.04 64-bit box.

BUT: It did work. Big thanx to PlayOnLinux for making the libraries available, since installing 32-bit programs on a 64-bit system is problematical, and ia32-libs is no more.

EDIT: I have made up a small .rar file of the needed libs. without which ./nwn complained of missing libraries. Extract these to your nwn folder, and the game will run on a 64-bit box. Here's the link:

[https://dl.dropboxusercontent.com/u/29881131/NWN_libs.rar](https://dl.dropboxusercontent.com/u/29881131/NWN_libs.rar). Let me know if this works for anyone.

---

### Post by vanquishedangel on 2014-04-23
> **oldrocker99 said:**
> I had to rely on 32-bit libraries installed by PlayOnLinux in ~/.PlayOnLinux/wine/linux-x86/1.4-dos_support_0.5, and copied libSDL-1.2.so.0, libesd.so.0, libdirectfb-1.2.so.0, libfusion-1.2.so.0, libdirect-1.2.so.0, libaa.so.1, libaudiofile.so.0 to ~/nwn,  and had to rename a couple before ./nwn would start the game on my 14.04 64-bit box.

BUT: It did work. Big thanx to PlayOnLinux for making the libraries available, since installing 32-bit programs on a 64-bit system is problematical, and ia32-libs is no more.

EDIT: I have made up a small .rar file of the needed libs. without which ./nwn complained of missing libraries. Extract these to your nwn folder, and the game will run on a 64-bit box. Here's the link:

[https://dl.dropboxusercontent.com/u/29881131/NWN_libs.rar](https://dl.dropboxusercontent.com/u/29881131/NWN_libs.rar). Let me know if this works for anyone.


epic thank you, I left trying to get it working natively because of the aging native dependencies, but this fix you have could very well be a more permanent fix. I will try to post this in the bioware EA forums for this game. I just started to get it working through playonlinux because this game needed another route.

To get it working with playonlinux or wine with an ATI card you have to rename the nwnmain.exe to nwnmain2.exe and start from that file. ATI cards will force their own graphics settings when it sees the nwnmain.exe being run and those settings dont work with wine.

---

### Post by oldrocker99 on 2014-04-23
Glad it worked!

---

### Post by Colsta on 2014-11-23
After getting this sorted out on 12.04, I recently tried upgrading to 14.04.  With no other changes, now Neverwinter Nights 'crashes' on start exactly like [the problem described here]("http://askubuntu.com/questions/205131/neverwinter-nights-does-not-run-in-12-10").  I hadn't realised prior to going ahead that ia32-libs had been removed between the two versions, so on re-visiting this thread I was hopeful that using oldrocker99's lib pack solution described above would resolve the problem.  Unfortunately it made no difference, nor did any of the various suggestions offered in answer on the other thread.  Just to make sure I tried the latest Intel drivers also without success.  The game takes a bit of a perfomance hit under Wine on this machine so I would prefer to run native if at all possible.  Perhaps anyone that has used the above method to get the game working  again can tell me whether they are using an Intel iGPU or discrete graphics?  oldrocker99: when you say about the libs you added that you "had to rename a couple before ./nwn would start the game on my 14.04 64-bit box" what did you have to rename exactly?

Has anyone any other thoughts on this at all?

---

### Post by oldrocker99 on 2014-11-23
One thing to do (it's been several months that I did this) is to open a terminal and ./nwn. If libraries are missing, they should be named. You can then install libname-i386 and then see which library it then needs. Did you see the Dropbox link in my April post? That should contain all the 32-bit libraries you need. Here it is again:
[https://dl.dropboxusercontent.com/u/29881131/NWN_libs.rar](https://dl.dropboxusercontent.com/u/29881131/NWN_libs.rar)

---

### Post by Colsta on 2014-11-26
Sorry - lack of clarity on my part probably.  I had already tried adding the libraries from your rar archive (although I still don't know which if any you had to rename in order to get things to work).  Likewise I had already tried starting the game from a terminal with the same result as from the icon: that is no obvious errors or notification of libraries missing, nwmain starts but just runs as a process in the background with no graphical output unfortunately.  Incidentally, since my last comment and on a whim, I tried installing xfce and running the game that way but with the same result.  Still stumped :(

---

### Post by paulisdead on 2015-06-09
I hate to dredge up an old thread, but trying to get this working on ubuntu gnome 15.04, and the mouse won't work in the game.  I carried over a working install from a few years back, but it stopped working after upgrading to 14.10.  I did a clean install, minus movies at this point, and have the same problem, the mouse won't move at all, with hardware or software cursor.  Not completely breaking, like not being able to use the mouse, but really annoying, the game disables my secondary monitor and I have to re-enable it under display afterwards, also my main display's res gets changed to whatever the game is set to run at.

---

### Post by Colsta on 2015-06-12
After upgrading from 12.04 I'm sorry to say that I never managed to get it running satisfactorily on 14.04 64-bit.  It got to the point where I realised I was spending all my time reading trying to find the magic combo of libs/fixes to get it to run natively again rather than actually enjoy playing it!  Although it goes against the grain I relented and installed it under Wine using Play on Linux where at least it performs flawlessly.  I figured if I was that worried about it I could always install it under a dedicated 32-bit install on another partition [but not thus far ;)].

---

