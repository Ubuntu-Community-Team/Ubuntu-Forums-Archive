---
title: "NWN Neverwinter Nights Diamond DVD working in 13.10 with movies! 64bit"
date: 2013-11-04
forum: Gaming &amp; Leisure
---

### Post by vanquishedangel on 2013-11-04
This is just a copy and paste of my old guide with some updates (Also I could not get it to post text only, so the commands to download may not work, you may click the links and manually move them to your nwn folder, and those stupid smileys, when editing a file the command may not work, just right click and choose gedit)

Special thanks to Hipmaestro (I copied and pasted a lot from his post), Skildron ( I used many of his answers to other people's threads in other forums), Wolfram (wrote original guide), me (lol, I tried to make it more "copy and paste", many of these fixes were from my trial and error), and several people on the internet.

Some things in this guide are for 64bit (ia-32-libs) but this guide works for 32bit as well, also some tweaks and settings may work for a wine install and the good old games version. Movies are working in 64bit! See below at bottom!

Also Kingmaker will not work because the one on the disk needs to authenticate on biowares website, that is no longer hosting for Neverwinter Nights. (see below for how)

For some trouble shooting after installation check the bottom of this post under "**Other Tweaks that helped me improve performance**".

[COLOR="#FF0000"]**To install Neverwinter Nights Diamond Edition (assuming DVDs automatically mount at /media/cdrom):**[/COLOR]


**1. Install some dependencies that are needed. ia32-libs and ia32-libs-multiarch are no longer available in the repos**

_Code:_
sudo apt-get install libsdl1.2debian libsdl-sound1.2 libsdl-mixer1.2 libsdl-net1.2 libsdl-image1.2 libstdc++5 libx11-dev

    To install ia32-libs and ia32-libs-multiarch I had to open the list of repositories and add the repo for raring ringtail. To do this I used synaptic and clicked on settings-->Repositories, the went to the "other software" tab. I then clicked "ADD" and pasted this next line in the box marked "apt line" 

_apt line:_
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring main restricted universe multiverse


   Then install ia32-libs and anyother dependancies it will need. Afterwars you may remove this. Without ia32-libs you wont have libSDL.so.0 in 32 bit (multiarch lacks this) and the 64 bit file wont work if you symlink it (duh! but I tried).

_code:_
sudo apt-get install ia32-libs


[B]2. Create a directory where you wish to install Neverwinter Nights (the destination directory). Neverwinter Nights Diamond requires 4.6 GB of free hard disk space.
[/B]
_Code:_
mkdir nwn

cd nwn


**3. Unzip Data_Shared.zip from Diamond DVD into the destination directory. Unzip Data_linux.zip from Diamond DVD into the destination directory.**

_Code:_
unzip /media/cdrom/Data_Shared.zip

unzip /media/cdrom/Data_linux.zip


**4. Unzip data/XP1.zip from Diamond DVD into the destination directory (overwriting all). Unzip data/XP2.zip from Diamond DVD into the destination directory (overwriting all).**

_Code:_
unzip -o /media/cdrom/data/XP1.zip

unzip -o /media/cdrom/data/XP2.zip


**5. Download nwclientgold.tar.gz (7.2 MB) and extract it into the destination directory (overwriting all).**

_Code:_
wget [http://nwdownloads.bioware.com/neverwinternights/linux/gold/nwclientgold.tar.gz](http://nwdownloads.bioware.com/neverwinternights/linux/gold/nwclientgold.tar.gz)

tar -xzf ~/nwclientgold.tar.gz


  *There have been alot of errors with fileroller for extracting in 13.10, so you may have to move the downloaded file manualy to the nwn folder and extract in terminal with this command*

_Code:_
tar zxf nwclientgold.tar.gz


**6. Download nwclienthotu.tar.gz (37.7 MB) and extract it into your nwn directory, overwriting all.**

_Code:_
wget [http://nwdownloads.bioware.com/neverwinternights/linux/161/nwclienthotu.tar.gz](http://nwdownloads.bioware.com/neverwinternights/linux/161/nwclienthotu.tar.gz)

tar -xzf ~/nwclienthotu.tar.gz


[I]There have been alot of errors with fileroller for extracting in 13.10, so you may have to move the downloaded file manualy to the nwn folder and extract in terminal with this command
[/I]
_Code:_
tar zxf nwclienthotu.tar.gz


**7. Update to latest version (506 MB).**

_Code:_
wget [http://nwvault.ign.com/fms/Download.php?id=162255](http://nwvault.ign.com/fms/Download.php?id=162255)

tar -xzf ~/English_linuxclient169_xp2.tar.gz


*There have been alot of errors with fileroller for extracting in 13.10, so you may have to move the downloaded file manualy to the nwn folder and extract in terminal with this command*

_Code:_
tar zxf English_linuxclient169_xp2.tar.gz


[B]8.[Optional] Get the C.E.P. (Community Expansion Pack 2.4, required for many modules made by players)
[/B]
_Code:_
wget [http://vnfiles.ign.com/nwvault.ign.com/fms/files/hakpaks/7849/CEP_24_a.rar](http://vnfiles.ign.com/nwvault.ign.com/fms/files/hakpaks/7849/CEP_24_a.rar)

The cep has instructions on how to install it here (pdf):

_Code:_
wget [http://vnfiles.ign.com/nwvault.ign.com/fms/files/hakpaks/7849/Downloading_and_Installing_CEP.pdf](http://vnfiles.ign.com/nwvault.ign.com/fms/files/hakpaks/7849/Downloading_and_Installing_CEP.pdf)


**9. Run ./fixinstall from the destination directory.**

_Code:_
./fixinstall


[B]10. To run Neverwinter Nights, run ./nwn or ./dmclient from the destination directory to run the player client or DM client respectively.
[/B]
_Code:_
./nwn


**11. If you get this message:**

"nwmain: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Aborted"

- - Remove ./lib from LD_LIBRARY_PATH.

_Code:_
sed -i~ 's|\./lib:||' nwn


[COLOR="#FF0000"]**NWMovies puts the movies back into the Linux client just like they are on the Windows clients.**[/COLOR]


**1. Install NWMovies v4.0 RC1.**

_Code:_
wget [http://home.roadrunner.com/~nwmovies/nwmovies/nwmovies-latest.tar.gz](http://home.roadrunner.com/~nwmovies/nwmovies/nwmovies-latest.tar.gz)

tar -xzvf nwmovies-latest.tar.gz


*There have been alot of errors with fileroller for extracting in 13.10, so you may have to move the downloaded file manualy to the nwn folder and extract in terminal with this command*

tar zxf nwmovies-latest.tar.gz



**2. Install the Bink Video command line Player for x86 GNU/Linux.**

_Code:_
wget [http://www.radgametools.com/down/Bink/BinkLinuxPlayer.7z](http://www.radgametools.com/down/Bink/BinkLinuxPlayer.7z)

unzip BinkLinuxPlayer.7z

sudo chmod 755 BinkPlayer


**3. Modify the 'nwn' startup script.**

_Code:_
sed -i~nwmovies '\|\./nwmain|iexport LD_PRELOAD=./nwmovies.so' nwn


**4. Optionally enable Screen Flickering at movie beginning/end fix:**

_Code:_
sed -i '\|nwmovies|aexport NWMOVIES_GRAB_HACK=1' nwn


**5. Run NWN.**

_Code:_
./nwn


**6. You get this message:**

"NOTICE: NWMovies: INI File written: Now exiting. This is perfectly normal!
NOTICE: Your next run of NWN should be complete, and include movies."

- - Run NWN a second time.

_Code:_
./nwn


**[COLOR="#FF0000"]Other Tweaks that helped me improve performance[/COLOR]**


[B]1. Neverwinter Nights is not multithreaded so dual cores and hyperthreaded processors may cause performance issues as it does for many people. Also access to more memory will help shuddering as well
[/B]
Solution:
Open your file manager and open the "nwn" folder. Right click "nwnplayer.ini" and select your text editor (mine is leafpad). Copy the text below and paste it under the [Game Options] section.

Client CPU Affinity=1

Max Memory Usage=512 (or anywhere up to 4096 mb, depending on your ram)


[B]2. Enabling better graphics capabilities that are not always available within the game menu's.
[/B]
_Solution:_
Open your file manager and open the "nwn" folder. Right click "nwn.ini" and select your text editor (mine is leafpad). Then choose options you want to enable.

example:(ATI cards only)

Replace the line "Enable Truform=0" under [Video Options] with "Enable Truform=1"to enable a more round appearance on round objects, if that line isn't there then just copy and paste "Enable Truform=1" without the quotes.


[B]3. Possible permissions issues
[/B]
Solution:
Highlight all the files in nwn folder, not the folders and right click, select permissions tab and set all option to anyone. Do this in all folders inside nwn folder. For some reason if you right click the folder(s) and go under permissions tab the option to make executable isn't there, and it will set all files to non-exacutable. So you will need to do all files inside the folder, and not the folder. Symlinks will give an error that is normal.


**4. Help I cant see my character**

_Solution:_
Disable Creature environment mapping in "options->video options>advanced video options" in game or change "Enable CreatureEnvironmentMapping=1" to "Enable CreatureEnvironmentMapping=0" in the nwn.ini file inside you nwn folder. I don't have this issue but some people do


**5. Missing gui layout file error**

_Solution:_
The data files off the disk were not fully copied, you will need to redo step 4 of installing nwn


**6. Other sound options**

Optionally if sound isn't working you can try to enter either of these lines in your nwn file inside you nwn folder.

export SDL_AUDIODRIVERS=alsa

export SDL_AUDIODRIVERS=pulse


[COLOR="#FF0000"]**Movies in 64bit!**[/COLOR]

[B]1. You need to make sure you have the appropriate 32bit libs then try to symlink them in the nwn folder (see below if there is an error)
[/B]
_Code:_
cd /home/user_name/nwn

ln -s /usr/lib/i386-linux-gnu/libX11.so.6 libX11.so. (32bit will have to search where the file libX11.so.6 is at)

ln -s /usr/lib32/i386-linux-gnu/libSDL_gfx.so libSDL_gfx.so (32bit will have to search where the file libSDL_gfx.so is at)


[B]2. Now you need to edit your nwn.ini.
[/B]
Open your file manager and open the folder nwn, then right click the nwn.ini folder and pick your text editor. Under [Display Options] change the line "FullScreen=0" to "FullScreen=1" or add the line "FullScreen=1" if the option isn't there. Also add the line "AllowWindowedMode=0"


[B]3. Now you need to edit your nwmovies.pl
[/B]
Open your file manager and open the folder nwn and then nwmovies. Right click nwmovies.pl and pick you text editor. you will need to put a "#" symbol infront of the lines $ENV{"BINK_SCALE"} = 1;, $ENV{"BINK_SMOOTH"} = 1;, and $ENV{"BINK_NOPERF"} = 1; so they look like this

#$ENV{"BINK_SCALE"} = 1;
#$ENV{"BINK_SMOOTH"} = 1;
#$ENV{"BINK_NOPERF"} = 1;

and add these lines if you are using a resolution of 1024x768 in game and computer so the movies will be at same resolution.

#$ENV{"BINK_WIDTH"} = $1024;
#$ENV{"BINK_HEIGHT"} = $768;


**4. You need to make sure that "binklib.so" is in your nwmovies folder.**

Open your file manager and go to your nwn folder, then open your nwnmovies folder and make sure it is in there. If it isn't then you will need to download BinkLinuxPlayer.7z, decompress it and copy the file binklib.so to your /nwn/nwmovies folder.


[B]5. If there was an error when trying to symlink the libSDL_gfx.so file then you need to download getlibs-all (64bit only, not in repository)
[/B]
_Code:_
wget [http://usablesoftware.files.wordpress.com/2011/02/getlibs-all-deb.pdf](http://usablesoftware.files.wordpress.com/2011/02/getlibs-all-deb.pdf)

Then delete the .pdf extension, it isnt a pdf, that is because wordpress didn't allow the .deb extension. Right click the resulting .deb file and install. Then you will need to install the libSDL_gfx.so file

Code:
getlibs -l libSDL_gfx.so

That will install the appropriate file and then you may symlink it. If it complains of permissions use sudo. 


**[COLOR="#FF0000"]Premium modules![/COLOR]**

I also have Kingmaker, Witches Wake, Infinite dungeons, Wyvern crown, Pirates of the Sword Coast, and Shadow Guard working. I also have aurora toolset and nwhak.exe working from my nwn directory, it was rather easy, I copied the utils folder to my native nwn, and I copied nwtoolset.exe and Mss32.dll.

To download load the files for linux here:


**Kingmaker:**

wget [http://content.bioware.com/neverwinternights/modules_premium/Kingmaker.zip](http://content.bioware.com/neverwinternights/modules_premium/Kingmaker.zip)


**Witches Wake and Shadow Guard:**

wget [http://content.bioware.com/neverwinternights/modules_premium/ShadowGuardPlusWitchsWake.zip](http://content.bioware.com/neverwinternights/modules_premium/ShadowGuardPlusWitchsWake.zip)


**Infinite dungeons:**

[http://files.bioware.com/neverwinternights/modules_premium/InfiniteDungeons.zip](http://files.bioware.com/neverwinternights/modules_premium/InfiniteDungeons.zip)


[B]Wyvern crown:
[/B]
[http://files.bioware.com/neverwinternights/modules_premium/WyvernCrown.zip](http://files.bioware.com/neverwinternights/modules_premium/WyvernCrown.zip)


**Pirates of the Sword Coast:**

wget [http://content.bioware.com/neverwinternights/modules_premium/PiratesOfTheSwordCoast.zip](http://content.bioware.com/neverwinternights/modules_premium/PiratesOfTheSwordCoast.zip)


And to install these you would do it the same as you would a module from the community. I have purchased these modules before so they may not work if you have bad cd keys and that I cannot help you with.


**Aurora Toolset and nwhak.exe**

I did this by installing nwn into wine (playonlinux) and then just coping the utils folder, nwtoolset.exe and Mss32.dll over to my nwn directory, then deleted the wine install of nwn (playonlinux).

to run them navigate to your nwn folder, right click the exe and choose wine.

I did not copy mwtoolset.ini from wine, I just used the one that was in my nwn folder.



**Hardware Mouse**


For hardware mouse instead of software mouse:

wget [http://home.roadrunner.com/~nwmovies/nwmouse/nwmouse-latest.tar.gz](http://home.roadrunner.com/~nwmovies/nwmouse/nwmouse-latest.tar.gz)

And follow the included instructions (may have errors)



**Updated textures and many good extras**


For better graphics and many extras go here: (It wont place the link XD)

[http://social,bioware,com/forum/1/topic/199/index/3275241](http://social,bioware,com/forum/1/topic/199/index/3275241) (replace comma's with a [.]).

---

### Post by oldrocker99 on 2013-11-05
After five years of playing Linux NWN, it never occurred to me to search for the wiki. Holy cow. Your post, BTW is excellent, collecting a great deal of information into one comprehensive page. Well done.

---

### Post by vanquishedangel on 2013-11-06
Also in the line where it says:

[B]3. Now you need to edit your nwmovies.pl

Open your file manager and open the folder nwn and then nwmovies. Right click nwmovies.pl and pick you text editor. you will need to put a "#" symbol infront of the lines $ENV{"BINK_SCALE"} = 1;, $ENV{"BINK_SMOOTH"} = 1;, and $ENV{"BINK_NOPERF"} = 1; so they look like this

#$ENV{"BINK_SCALE"} = 1;
#$ENV{"BINK_SMOOTH"} = 1;
#$ENV{"BINK_NOPERF"} = 1;

and add these lines if you are using a resolution of 1024x768 in game and computer so the movies will be at same resolution.

#$ENV{"BINK_WIDTH"} = $1024;
#$ENV{"BINK_HEIGHT"} = $768;[/B]

May not work because it messes with the permissions and may make the movies unplayable, if that is the case then movies wont play afterwards. Just extract the movies "NWMovies v4.0 RC1" again to any folder and replace nwmovies.pl.

**There is an issue with not being able to see the movies but you can hear them**. I fixed this years ago but cannot remember how. The movies are playing in the bink player (in a separate window) but they are not playing on top of the nwn window at full screen. When you allow windowed mode The movies can be seen. to allow windowed mode edit the nwn.ini under [Display Options] with these lines:

FullScreen=0
AllowWindowedMode=1

You will then see the movies but the ingame camera controls will not respond to the mouse touching the side of the screen but you will need to use the arrow keys.

Maybe some can find a fix to this, I so far cannot remember.

---

### Post by vanquishedangel on 2013-11-07
I also got the PRC pack version 3.5 installed and working for the OC modules and for the "citadel" by jim grimsley (along side CEP 2.4).

The only drawback is that when ever I install the prc pack to any module, the built in character creator has issues and will crash right after createing the character, however the character is saved. You can then open the module and choose "select premade character" and pick the one you previously made and all works great.

I have also gone through and installed many overrides (23,648 files, 1.6 gigs!) of custom content including

Cutsom gui, icons, scrolls, elementals, weapons (all of amatheyst dragons work)
nwncq (all new tilesets)
custom creature complilation (many authors)
Alternate combat animations (CEP compatible)
Better trees
better hands
skyboxes
Tony k's AI
Companion fixes

And so many more by various authors I cant posssibly remember them all. I went through and eliminated the ones that caused issues with linux (may also just not have worked). I also made many compatible with linux and when I have completed this task to my happieness, I will upload some files so that everyone on linux can enjoy these awsome works.

---

### Post by oldrocker99 on 2013-11-07
One thing to remember, is in the nwn/hak directory, **all** files **MUST** have names in lower case!

---

### Post by vanquishedangel on 2013-11-08
> **oldrocker99 said:**
> One thing to remember, is in the nwn/hak directory, **all** files **MUST** have names in lower case!

Not true, some will not work when the caps are changed to lower case (the premium modules like kingmaker) others will not work if they arent changed.

---

### Post by oldrocker99 on 2013-11-10
Yes, I'd forgotten that the Premium modules' haks are not all lower case, but every other hak's name must be lower-case.

---

### Post by vanquishedangel on 2013-11-13
ok to get **nwmouse** to work you need to put symlinks into the usr/lib32 folder. A little odd but you would think that the 32 bit files needed would be in there but they are not. so what i did was in the nwn folder create symlinks to the 32bit library, then copy the symlinks to usr/lib32. **nwuser** worked right out of the box.

**_Commands:_**

cd nwn

ln -s /usr/lib/i386-linux-gnu/libelf.so.1 libelf.so

ln -s /usr/lib/i386-linux-gnu/libSDL-1.2.so.0 libSDL.so

ln -s /usr/lib/i386-linux-gnu/libXcursor.so.1 libXcursor.so

Then copy these files to usr/lib32 from your nwn directory. You will need permissions to do this, perhaps there is an easier way. To copy them over with permissions I just would type "sudo nautilus" in a terminal then navigate to usr/lib32, then just copy and paste.

another way to do this would be to edit nwmouse_install.pl and tell it to look in /usr/lib/i386-linux-gnu. I havent tried this but I imagine you would add the line "-L/usr/lib/i386-linux-gnu" to part where is lists the following (add it in the bolded area):

$machine = `/bin/uname -m`; chomp($machine);
if( $machine =~ "x86_64" ) {
	$x86_64 = "**-I/emul/ia32-linux/usr/include -L/emul/ia32-linux/usr/lib -L/emul/ia32-linux/lib -L/lib32 -L/usr/lib32[COLOR="#FF0000"]-L/usr/lib/i386-linux-gnu[/COLOR]**";

But it still may give an error of not finding them because its looking for libXcursor.so, libSDL.so, and libelf.so, not libelf.so.1, libSDL-1.2.so.0, or libXcursor.so.1. Eitherway the symlinks created in the first part will have the correct names and you may place then either in usr/lib32.

after you start nwn you should get an output like this in terminal:

shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~$ cd nwn
shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~/nwn$ ./nwn
NOTICE: NWMouse: Using libSDL via RTLD_NEXT.
NOTICE: NWMouse: Version: 20090906.183839
WARNING: NWMouse: No INI file.  Creating.
WARNING: NWMouse: INI recalculation required: 7780208:0 1215115938:0
NOTICE: NWMouse: (cookie) Entry point determined: 0x7830
NOTICE: NWMouse: (cookie) Searching executable: 96
NOTICE: NWMouse: (cookie) Cookie0 location: 0x084e9380
NOTICE: NWMouse: (cookie) Searching executable: 80
NOTICE: NWMouse: (cookie) Cookie1 location: 0x084e009c
NOTICE: NWMouse: (cookie) Cookie2 location: 0x0863d880
NOTICE: NWMouse: (cookie) Searching executable: 80
NOTICE: NWMouse: (cookie) Cookie3 location: 0x084ffd44
NOTICE: NWMouse: (cookie) Searching executable: 80
NOTICE: NWMouse: (cookie) Cookie4 location: 0x084e3018
NOTICE: NWMouse: (cookie) Searching executable: 80
NOTICE: NWMouse: (cookie) Cookie5 location: 0x084e05b7
NOTICE: NWMouse: (cookie) Searching for proper Orientation function, this may take a while...
NOTICE: NWMouse: (cookie) Cookie6 location: 0x084e8440
NOTICE: NWMouse: INI File written: Now exiting.  This is perfectly normal!
NOTICE: Your next run of NWN should be complete, and include hardware mouse.
80shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~/nwn$

---

### Post by vanquishedangel on 2013-11-14
Ok, discovered something interesting about the movies and full screen, they can play full screen. It seems there is yet another missing library in ubuntu's multiarch support :( libSDL-gfx.so. (get-libs does not work anymore, it only installed libSDL_gfx.a, that wont work) I couldnt get it through synaptic either.

I fixed this by downloading it from here and installing with gdebi:

[http://mirrors.kernel.org/ubuntu/pool/universe/s/sdlgfx/libsdl-gfx1.2-4_2.0.23-3_i386.deb](http://mirrors.kernel.org/ubuntu/pool/universe/s/sdlgfx/libsdl-gfx1.2-4_2.0.23-3_i386.deb)

Then from the nwn directory I ran this command from terminal:

ln -s /usr/lib/i386-linux-gnu/libSDL_gfx.so.4 libSDL_gfx.so

And movies that did play were full screen. I still have the issue with every other movie plaing however but getting closer, I may have to write a new guide from scratch.

---

### Post by rednecktek on 2013-12-14
I have everything done up to the first launch of nwn and it just hangs. Narrowed it down to nwmain, but have no idea how to figure out was is exactly wrong. Running 64 bit Xubuntu

---

### Post by Previous1 on 2013-12-20
Works for me, though I had to modify a few steps as the Platinum Edition has a different directory structure. You can find my script [here]("http://forums.linuxmint.com/viewtopic.php?f=225&p=798222&sid=cd7c72e0821729b61c06556861e82274#p798222"). I'm curious on how to get to play movies in nwn full screen as well. As a workaround, you can patch SDL to easily switch between full screen and windowed mode.

[http://home.roadrunner.com/~nwmovies/libsdl.html](http://home.roadrunner.com/~nwmovies/libsdl.html)

Also, do you know of a way to get the gamespy listing back in-game? I've tried to [edit the hosts file]("http://www.neverwinternights.info/builders_hosts.htm"), but that didn't work.

---

### Post by vanquishedangel on 2013-12-22
Previous1:

I am not sure about how to get game spy working sorry, I know the community is working on something but I am not sure how close they are to completeing it. Here is a link:

[http://social,bioware,com/forum/1/topic/199/index/15195370/11](http://social,bioware,com/forum/1/topic/199/index/15195370/11) ( right click and select "copy link location" then paste it in your browsers address bar. Replace commas with a ".", there are 2 comma's. Ubuntu forums have issues with links to this site).



rednecktek:

I am not sure what the issue is, the terminal should output something that can be searched, also there is a log file or two in the nwn folder that may also shed light on the subject. without any information to go on I would assume there is a file misplaced somewhere, check you home directory.

---

### Post by Previous1 on 2013-12-22
Thanks for the link. Apparently modifying hosts has no effect on the game client (only the server). I've added this to my guide:

> Main drawback is that there's no game server listing via [NWNCX]("http://neverwinternights.info/nwncx.htm"). Modifying [/etc/hosts]("http://www.neverwinternights.info/builders_hosts.htm") doesn't restore it, but removes the delay when logging in.

You can still [direct connect]("http://yourserverlist.com/index.php?juego=nwn1"), use [gfire (tcpdump)]("http://trac.assembla.com/gfire/wiki/ServerDetection"), or add servers to [nwnplayer.ini]("http://yourserverlist.com/gettxtips.php?juego=nwn1&tipopart=roleplay").

---

### Post by rasmus91 on 2014-03-20
Hello.

I've a computer with an Optimus card "GT 620" and while this is easily capable of running nwn, i'm having some issues getting it to actually run.
t ran in 13.04 using the old guide from here, but now i get this:

```
rasmus@rasmus-UX32VD:~/Games/Neverwinter Nights Diamond Edition$ ./nwn
./nwmain: error while loading shared libraries: libturbojpeg.so: cannot open shared object file: No such file or directory

```

or with primusrun

```
rasmus@rasmus-UX32VD:~/Games/Neverwinter Nights Diamond Edition$ primusrun ./nwn 
./nwmain: error while loading shared libraries: libturbojpeg.so: cannot open shared object file: No such file or directory

```

and the exact same with optirun, i don't quite get why. I did [this]("http://www.webupd8.org/2013/10/fix-bumblebee-libturbojpegso-issue-in.html"), but that didn't make a difference at all. Any insight?

thanks for the guide. I hope you feel up for the task for updating it again for the next version of Ubuntu - playing your favourite game on your favourite distro is just awesome.

---

### Post by rasmus91 on 2014-03-21
Reinstalled (as the one i had was the one i used in 13.04) and now i when i do try to run nwn, i get ```
Segmentation fault (core dumped)
```

---

