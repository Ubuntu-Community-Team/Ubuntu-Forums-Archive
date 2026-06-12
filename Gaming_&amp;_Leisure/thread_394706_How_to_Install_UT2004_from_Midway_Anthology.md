---
title: "How to Install UT2004 from Midway Anthology"
date: 2007-03-27
forum: Gaming &amp; Leisure
---

### Post by adam_kimber on 2007-03-27
**Installing UT2004 from the Unreal Anthology by Midway **
*(thanks to type98 and coffeeadikt for their posts)*

NOTE: This How to takes notes from [ this guide]("http://utforums.epicgames.com/showthread.php?t=558146&page=1"). 
NOTE: This installation was undertaken on a 32 bit machine running Ubuntu Edgy Eft, but might be applicable for other versions.
NOTE: Unshield might not work properly on your installation, especially if running the 64bit version.[ This might help. (See caveat)]("http://utforums.epicgames.com/showthread.php?t=558146&page=1")
NOTE: This worked for me but might not for you, if you have helpful additions then I would be grateful. 


_Preparation for Installation_

The Midway Anthology DVD does not have an installer script. The files on the DVD are in an Installshield CAB format files that needs to be extracted. This cannot be done using [cabextract]("http://www.kyz.uklinux.net/cabextract.php") as that is for Microsoft CAB files, instead we need a copy of "unshield".

1) Obtain a copy of "unshield" using your package manager or from [SynCE - Unshield]("http://synce.sourceforge.net/synce/unshield.php")
2) Next, obtain the latest linux ut2004 patch (v3369 as of this writing) [http://treefort.icculus.org/ut2004/u...ch3369.tar.bz2](http://treefort.icculus.org/ut2004/u...ch3369.tar.bz2)
3) Free up roughly 16GB of space for the install process, about 5.3GB for CAB files and 11GB for extracted files.


_Installation_

4) Mount the DVD if not already loaded/mounted (For example, if the DVD drive is /dev/hdb and the mount point is /mnt): # mount -r -t iso9660 /dev/hdb /mnt 
5) Copy CAB files to a temporary location, this can be done by going into the 10 directories named Disk 1 to 10 and copying the CAB files using your favourite file manager or by;

# mkdir junk; cd junk 
/junk# cp /mnt/Disk?/data?.* .
/junk# cp /mnt/Disk10/data??.* .

[OPTIONAL METHOD IF UNSHIELD FAILS
5a - 6a) If unsheild is not working for you at all. [svtfmook]("http://ubuntuforums.org/member.php?u=372948") suggests extracting the CAB files using Wine and the windows version of Unshield, or just installing using the windows installer and copying the directories over afterward.]

6) Decompress the copied CAB files to the installation directory of choice (here  using the following command in the temporary directory;  unshield -d /install/directory -D3 x data1.cab

(Note:  -D 3 turns debugging on)
(Note: make sure you have all 11 CAB files otherwise extraction will not work properly)

You should have now all four games in the one installation directory.  
Note: It is probably possible to play the other games from this DVD but this guide is currently for UT2004

The other games are not needed, nor is windows executable, the directory called OCXFiles and any files starting with _ and Launcher 

7) Delete all directories beginning with _, 1_, 2_ and 3_  and the executable

# rm -rf _* 1_* 2_* 3_* Launcher* All_UT2004.EXE OCXFiles

You should now have a directory looking like this

4_UT2004_Animations
4_UT2004_Benchmark
4_UT2004_EXE
4_UT2004_ForceFeedback
4_UT2004_Help
4_UT2004_Help_English
4_UT2004_Help_French
4_UT2004_Help_GermanAll
4_UT2004_Help_Italian
4_UT2004_Help_Spanish
4_UT2004_KarmaData
4_UT2004_Manual_English
4_UT2004_Manual_French
4_UT2004_Manual_German
4_UT2004_Manual_Italian
4_UT2004_Manual_Spanish
4_UT2004_Maps
4_UT2004_Music
4_UT2004_Sounds_All
4_UT2004_Sounds_English
4_UT2004_Sounds_French
4_UT2004_Sounds_GermanAll
4_UT2004_Sounds_Italian
4_UT2004_Sounds_Spanish
4_UT2004_Speech_English
4_UT2004_Speech_French
4_UT2004_Speech_German
4_UT2004_Speech_Italian
4_UT2004_Speech_Spanish
4_UT2004_StaticMeshes
4_UT2004_System_All
4_UT2004_System_English
4_UT2004_System_French
4_UT2004_System_GermanAll
4_UT2004_System_Italian
4_UT2004_System_Spanish
4_UT2004_Textures
4_UT2004_Web

Note if you are not planning on playing in German, Spanish or French then remove any directories relating to those languages, this will save disk space

8) Remove other language options

# rm -rf *French *German* *Spanish *Italian

9) Remove UT2004 executable, again. 

# rm -rf 4_UT2004_EXE

10) Move any files in the English appended directory to corresponding directory, e.g. 4_UT2004_Help_English to 4_UT2004_Help. And rename any directories ending with _All to its root e.g. Sounds_All to Sounds

11) Rename all directories so that the 4_UT2004_ is removed

This can be done in your favourite file browser by using the following bash script

for file in 4_UT2004_*
do
newname=`echo $file | sed -e 's/4_UT2004_//'`
mv $file $newname
done

Directory should now look like this 

Animations
Benchmark
ForceFeedback
Help
KarmaData
Manual
Maps
Music
Sounds
Speech
StaticMeshes
System
Textures
Web

12) Now to get the Linux executables and other required files that are provided by the patch. Move the patch to the isntall directory and extract it. 

Unpack the ut2004 linux patch

/install/directory# tar -jxf ut2004-lnxpatch3369.tar.bz2

Copy the all files+dir under UT2004-Patch into the top level
directories

# cd UT2004-Patch
UT2004-Patch# tar cf - . |( cd .. ; tar xvf -)

13) Copy System files to the games system folder, the game requires, OpenAL and SDL

Make sure that the /install/directory/System has a local copy
of libSDL-1.2.so.0 and openal.so.

/install/directory/System# cp /usr/lib/libSDL-1.2.so.0 ./libSDL-1.2.so.0
/install/directory/System# cp /usr/lib/libopenal.so.0.0.0 openal.so

14) Create text file called CDkey and insert your CD key into the first line 

15 Run and enjoy


_MODS_

16) If you want MODs then follow

a) If you are wanting any mods, the easiest way to install them is to use the Loki installers. However the Loki installer will error on, "Game not installed" if you follow the above instructions. This is due to the installer looking for a file in a hidden directory. To solve this, copy the following text into a text document, rename file to ut2004.xml and place in "~/.loki/installed"



Code:

<?xml version="1.0"?>
<product name="ut2004" desc="Unreal Tournament 2004" xmlversion="1.6" 
root="INSTALL_DIR" 
update_url="http://unreal.epicgames.com/updates/ut2004/updates.txt">
  <component name="__CDKEY__" version="3369" default="yes">
    <option name="English"></option>
    <option name="__CDKEY__" tag="__CDKEY__"></option>
  </component>
</product>

Replace INSTALL_DIR with the installation directory used above.

b) The Loki installed mods have their own play scripts. They will look for an executable file called "ut2004" in the root of the install directory. Simply copy the following code into a file called ut2004, place it in the installation directory chmod +x it and presto!

Code:

#!/bin/sh

SUBDIR="."

#----------------------------------------
script=$0
count=0

while [ -L "$script" ]  
do
    script=`perl -e "print readlink(\"$script\"), \"\n\""`
    count=`expr $count + 1`

	if [ $count -gt 100 ]  
	then
	    echo "Too many symbolic links"
	    exit 1
	fi
done

GAME_DIR=`dirname $script`

cd $GAME_DIR
cd System
./ut2004-bin "$@"

---

### Post by NESFreak on 2007-04-24
tnx for your howto. But i get some error when running: "Missingini"

Would you be so kind to post all, your *.ini from the system dir?

tnx, NESFreak

---

### Post by adam_kimber on 2007-04-24
> **NESFreak said:**
>  *.ini from the system dir?

tnx, NESFreak

```
~/bin/games/UT2004/System$ ls *.ini
AoClient.ini  Default.ini      Manifest.ini       UnrealEdTips.ini
AoServer.ini  DefUnrealEd.ini  ServerFilters.ini  User.ini
Build.ini     DefUser.ini      UDNHelpTopics.ini
```

I hope this helps!

---

### Post by NESFreak on 2007-04-25
> **adam_kimber said:**
> ```
~/bin/games/UT2004/System$ ls *.ini
AoClient.ini  Default.ini      Manifest.ini       UnrealEdTips.ini
AoServer.ini  DefUnrealEd.ini  ServerFilters.ini  User.ini
Build.ini     DefUser.ini      UDNHelpTopics.ini
```

I hope this helps!

I only have Build.ini  and Manifest.ini

How do i get the other files?

just got what i did wrong.
I moved System_English tot system instead of moving System_English/* to system.
tnx anyway

---

### Post by NESFreak on 2007-04-25
I took the liberty to make this howto into a small script, with some minor changes. Instead of copying all the cab files, it creates symlinks and instead of unpacking it all it only extract whats needed.

it still has the following dependencies: libopenal, libsdl, and unshield:
for feisty:
```
 sudo aptitude install libopenal0a unshield libsdl1.2debian
```

make an empty directory and place the script in it. Run it from the commandline ```
sh ./utinst.sh
```

it'll run step one to fifteen for u. And only consumes the space the full install itself will use ~6GB.

Hope someone finds this useful.

NESFreak.

btw the in linux-x86.tar.bz2 included libsdl and libopenal give better sound performance. (these are the ones from the UT2k4 demo. On my system the system default tend to sound a bit cracky)

---

### Post by Tumpster on 2007-05-07
I'm still not understanding how to patch UT2004? I got it installed just fine but don't understand the patchign process.

---

### Post by adam_kimber on 2007-05-07
What are you trying to patch? The UT2004 game? Or are you trying to install a MOD? The reason for this question is whilst both are similar methods to install there are differences. 

Hey thanks NESFreak for the installer script. I hope people find that useful.

---

### Post by TsukasaT.tiger on 2007-06-10
Sorry for any problems. I just got Unreal Anthology today, and was extreamly pissed to find that i couldnt install/run it under linx. I am really new to linux to be honest. 

I ran the script that was provided. and for some reason every time i try to run the UT2004.exe  it will pop up with a window stateing that my CD key is wrong. where am I suppose to play the text file, how is it suppose to be named (the file itself) and last, how do I properly run the game under linux, it seems to me that if I am useing the exe file, I am useing wine, but I could be wrong.  thank you.

---

### Post by adam_kimber on 2007-06-11
> **TsukasaT.tiger said:**
>  it seems to me that if I am useing the exe file, I am useing wine, but I could be wrong.  thank you.

Hey not at all! The problem with moving from Windows to Linux in general is that the file structure is different and can be confusing. In windows programs that run are generally .exe however this is not the case in Linux. 

You are indeed using the wrong file. ut2004.exe should have been deleted by the script and if it still exists delete it as it is no use to Linux. The Linux executable binary should have been installed when the script applied the patch. 

You should be using the ut2004-bin file to start the game in Linux. Double click should work. I have set up a launcher (shortcut) as this makes life easier.

---

### Post by TsukasaT.tiger on 2007-06-11
hmmm, I found the bin file. clicked it and nothing happened. I ran terminal and used the command ./ut2004-bin and it came up with this

/UT99/System$ ./ut2004-bin
./ut2004-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
tsukasa@Gertrude:~/UT99/System$ sudo ./ut2004-bin

I take it i didnt run the scrpt correctly, I am useing Kubuntu feisty on an HP laptop, dunno if that has anything to do with it. nVIDIA GeForce go 7600 as well.

---

### Post by Cappy on 2007-06-12
I'll show you how to find it using the terminal:
```

~$ **apt-cache search libstdc**
libgmp3-dev - Multiprecision arithmetic library developers tools
_libstdc++5 - The GNU Standard C++ Library v3_
libstdc++5-3.3-dev - The GNU Standard C++ Library v3 (development files)
libstdc++6 - The GNU Standard C++ Library v3
libstdc++6-4.1-dbg - The GNU Standard C++ Library v3 (debugging files)
libstdc++6-4.1-dev - The GNU Standard C++ Library v3 (development files)
libstdc++6-4.1-doc - The GNU Standard C++ Library v3 (documentation files)
lib32stdc++6-4.1-dbg - The GNU Standard C++ Library v3 (debugging files)
libstdc++5-3.3-dbg - The GNU Standard C++ Library v3 (debugging files)
libstdc++5-3.3-doc - The GNU Standard C++ Library v3 (documentation files)
libstdc++5-3.3-pic - The GNU Standard C++ Library v3 (shared library subset kit)
libstdc++6-4.1-pic - The GNU Standard C++ Library v3 (shared library subset kit)
libstdc++6-dbg - The GNU Standard C++ Library v3 (debugging files)
libstdc++6-dev - The GNU Standard C++ Library v3 (development files)
libstdc++6-doc - The GNU Standard C++ Library v3 (documentation files)
libstdc++6-pic - The GNU Standard C++ Library v3 (shared library subset kit)

```
I underlined the correct line.

Alternatively, you can goto (System-->Administration-->Synaptic Package Manager) and search on say, "libstdc". You can click and install it from there. I just prefer the Terminal.

Anyway, just run this in the terminal:
```

sudo apt-get install libstdc++5

```

---

### Post by thinsoldier on 2007-09-04
what if you already have the game installed in windows and would rather not waste another couple gigs of hard drive space?

How can I just run the files I already have with the linux executable?

---

### Post by NESFreak on 2007-09-07
> **thinsoldier said:**
> what if you already have the game installed in windows and would rather not waste another couple gigs of hard drive space?

How can I just run the files I already have with the linux executable?

you could make some symlinks to the directories containing big gamefiles. You could for instance just do a full install and then remove Maps and Textures and make a symlink to your windows install for those two directories.

---

### Post by thinsoldier on 2007-09-09
I think simplifying that symlink stuff and making it common knowledge would greatly help to get people to convert to Ubuntu. I've gotten a lot of people to move away from proprietary windows applications and use open source alternatives available in windows and then the idea of switching to linux starts sounding good to them when I say that all of their favorite apps were originally made for linux.

But one of the major turn offs is that they have to reconfigure all those apps all over again when they get ubuntu. And they find it especially _stupid_(their words) that if they're dual booting windows and Ubuntu and they have all the same apps installed in both OSes, why isn't there a way to synchronize settings across both OSes so that it's a more enjoyable experience to switch back and forth between the two.

---

### Post by dasy2k1 on 2007-09-16
IU found the easiest way to instll was to use the installer thatr came with the disk under wine to unpack everything
then just moove the files to a better directory, apply the pach, add the links to the libaries and go

now i just need to find out how to get the other 3 working, 
(UT GOTY shoudlent be difficult as there is allready a lokoi installer around)

---

### Post by dasy2k1 on 2007-09-22
well ive not found a way of getting U99 working yet, anyone had any luck?

---

### Post by Absolut139 on 2007-10-05
> **NESFreak said:**
> I only have Build.ini  and Manifest.ini

How do i get the other files?

just got what i did wrong.
I moved System_English tot system instead of moving System_English/* to system.
tnx anyway

I ran your script and I have the exact same problem, only have Build.ini and Manifest.ini However, i do not understand how to fix it.  Can someone point me in the right direction.
Heres what i have:
rick@rick-desktop:~/ut/System$ ./ut2004-bin
MissingIni

History: 

Exiting due to error

---

### Post by fadastic on 2007-10-06
Hmm...near the end of that script when after I enter my CD key I get this:

```
MissingIni

History: 

Exiting due to error

```

---

### Post by NESFreak on 2007-10-06
> **Absolut139 said:**
> I ran your script and I have the exact same problem, only have Build.ini and Manifest.ini However, i do not understand how to fix it.  Can someone point me in the right direction.
Heres what i have:
rick@rick-desktop:~/ut/System$ ./ut2004-bin
MissingIni

History: 

Exiting due to error

> **NESFreak said:**
> 
just got what i did wrong.
I moved System_English tot system instead of moving System_English/* to system.
tnx anyway

so it may be a different problem.

can you go to the "system" (the dir where ut2004-bin is supposed to live) directory and post here your output of ```
ls *.ini
```

I'm not a professional script writer, so the script hasn't got any error handling at all. srry for that, maybe sometime, when i'm really bored ill rewrite it, but don't count on it.

---

### Post by Absolut139 on 2007-10-06
actually I found an installer which operates on the midway editors choice dvd,  [http://liflg.org/files/testinstaller5.run](http://liflg.org/files/testinstaller5.run)
thanks though...

---

### Post by NESFreak on 2007-10-08
> **Absolut139 said:**
> actually I found an installer which operates on the midway editors choice dvd,  [http://liflg.org/files/testinstaller5.run](http://liflg.org/files/testinstaller5.run)
thanks though...

nice, is probably better than mine. I haven't  like tried it out, but is this one 2k4 only or does it allow you to select all 4 games?

-NESFreak

---

### Post by nekosama on 2007-10-12
> **Absolut139 said:**
> actually I found an installer which operates on the midway editors choice dvd,  [http://liflg.org/files/testinstaller5.run](http://liflg.org/files/testinstaller5.run)
thanks though...

that sounds nice, now how do you use it?

---

### Post by NESFreak on 2007-10-15
> **nekosama said:**
> that sounds nice, now how do you use it?

Haven't tried it out, but I guess right click--> save as. Select the file, properties (or whatever it's called in your language) go to the rights tab, give it the right to run. Run the file. (by clicking on it)

---

### Post by dasy2k1 on 2007-10-20
I Have found installers for the vanilla UT and the unreal gold from the Anthology...
they can be found at [http://utforums.epicgames.com/showthread.php?t=556876](http://utforums.epicgames.com/showthread.php?t=556876)

---

### Post by jpittack on 2007-10-24
I could use your guys help.  I have the 64 bit installtion of Gutsy and am trying to follow the link given in the first post.  I am not yet familar with all of the commands.  I don't know how to decompress or how to patch to 5.3.  Thank you so much for writting this how to.  Getting off of windows is slowly getting easier.

---

### Post by db0 on 2007-12-07
I followed the guide and I worked flawlessly (thans a bunch btw) but I have a very annoying problem now. You see I bought the game in germany and unfortunately I do not speak German. Now, as with most german games, not only have they totally translated/dubbed everything, but they toned down the violence to a ridiculous level (green blood and stuff).
In my windows installation I managed to switch on the english language by changing a option in UT2004.ini : language=eng
unfortunately, for some reason the same trick does not work in Linux. 

Do you have any idea how to switch to english?

EDIT/UPDATE: Nevermind, solution found: Go into system > rm *.det :)

---

### Post by Jaramo on 2007-12-15
> **NESFreak said:**
> I only have Build.ini  and Manifest.ini

How do i get the other files?

just got what i did wrong.
I moved System_English tot system instead of moving System_English/* to system.
tnx anyway

Your script is fantastic, thank you very much!

---

### Post by dasy2k1 on 2007-12-21
much of the blood in UT2004 is green!
thats because one of the alien races has green blood!

---

### Post by twiistedkaos on 2008-01-09
Hmm , I used the script and it seemed to install flawlessly, but when I open the game the first time it showed the Nvidia logo, then went to a black screen, now it just plainly goes to a black screen when I open ut2004-bin, any ideas on why this would happen?

---

### Post by svtfmook on 2008-03-21
sorry to bring back an old thread, but i'm trying to install this, i tried the first method, and the script.  but end failingly with md5checksum errors.

anyone know of a newer way of installing ut2k4 from the anthology disc?

using gutsy 64bit

---

### Post by adam_kimber on 2008-03-21
I believe there were some problems with both the installer script, installers and the how to I partially wrote on 64 bit systems. 

Did you check out the links to acquiring a 64 bit version of the cab extractor??? That might be causing your error? 

If not run script from command line and post the errors, someone might be able to help. I am not running 64bit ubuntu unfortunately....

---

### Post by svtfmook on 2008-03-21
i was able to get it installed by installing it in wine, then copying over the library.

however, now my problem is when i start the game, the sound works, but my video turns completely off (no signal on monitor).  i can hear the sounds and what not, i can move the mouse and here it highlight menus, but nothing as far as video goes.  i can't even alt-tab out of it.

---

### Post by tbeo on 2008-03-23
hey guys,
first of all: thanks for your manual - worked great for me! 
But I've got a problem left: there is some kind of crackling noise disturbing the in-game-sound - i already tried to change the openal and libsdl files in System, but then my sound was completly gone :) 
anyone got an idea on how to solve this?

---

### Post by adam_kimber on 2008-03-23
> **svtfmook said:**
> i was able to get it installed by installing it in wine, then copying over the library.

however, now my problem is when i start the game, the sound works, but my video turns completely off (no signal on monitor).  i can hear the sounds and what not, i can move the mouse and here it highlight menus, but nothing as far as video goes.  i can't even alt-tab out of it.

Ah! A lot of people seem to have tried installing with Wine, this guide is how to run the game natively without using Wine.... Try winehq for wine help. :)

---

### Post by svtfmook on 2008-03-23
but i'm not running it in wine.  i used wine to extract all the cab files since unshield didn't work for me.  so basically, i had the same result as the guide, i just used wine as unshield.

---

### Post by adam_kimber on 2008-03-25
My bad. I thought you were trying to install it Wine. Using Wine to extract the files is a method that I did not think would work. Cool. I will edit the first post to state that this is an option.

---

### Post by svtfmook on 2008-03-25
it's an option, but unfortunately, i don't have any video, lol.

---

### Post by caravel on 2008-05-03
I got this working, only problem is that some textures, notably the redeemer and some other environment and missile textures are replaced by the zebra one.  Working great apart from that but would like to get it resolved.  Any ideas?

Thanks

caravel

:)

---

### Post by jaedaen on 2008-05-26
You might have moved on by now, but I had the same problem as you did. I've discovered that it's a problem with the most recent stable nvidia driver. Assuming this matches your scenerio as well, upgrade to nvidia's beta driver. The problems were solved after I did this.

---

### Post by lavinog on 2008-06-08
Any ideas on getting text to speech working?
I came across this link: [http://icculus.org/lgfaq/#ut2k4tts]("http://icculus.org/lgfaq/#ut2k4tts")
but the speechd program seems to be outdated.

---

### Post by eternalwolfman on 2009-04-05
NESFreak and everyone, thank you so much for your help! I used the scripts provided and the game installed smoothly and works better than it did under windows! Thank you!

---

### Post by rizzeh on 2009-04-06
anyone else gets sound problem where ingame online i can hear all players sounds ( pickups, dodge, weapon fire ) regardless how far away they are on the map? It is very annoying tbh, although some might consider this as cheating, specially in 1v1.
I tried various rolloff values in ALAudioSubsystem , no luck so far.

---

### Post by lavinog on 2009-04-07
> **rizzeh said:**
> anyone else gets sound problem where ingame online i can hear all players sounds ( pickups, dodge, weapon fire ) regardless how far away they are on the map? It is very annoying tbh, although some might consider this as cheating, specially in 1v1.
I tried various rolloff values in ALAudioSubsystem , no luck so far.

I haven't played it with linux in a couple of months, but I am pretty sure I didn't have that issue. What sound card are you using?

---

### Post by rizzeh on 2009-04-07
from lspci

00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)

this problem is only in ut2004. i've tried audio from demo version too, the problem presists.

---

### Post by alexlliandri on 2009-05-24
NESfreak, thanks for your installer-script!!!

a very comfortable way to install ut 2k4 on a pc running ubuntu^^

greets

---

### Post by vmifox on 2009-07-27
Old thread, but everyone knows why I found it... Thanks Midway for being so awesome.

Huge thanks, though, for writing that script and the other helpful posts... with just a little tweaking I was able to get ut2004 running on x64 jaunty!

---

### Post by mike* on 2009-08-17
Hi, I just bought this game and want to install ut2004 at work.
Can anyone tell me, will it be possible for a few of us to play LAN matches with just the one install and one cd key that comes with the game?
It's the unreal anthology 1 dvd version.

---

### Post by lavinog on 2009-08-17
> **mike* said:**
> Hi, I just bought this game and want to install ut2004 at work.
Can anyone tell me, will it be possible for a few of us to play LAN matches with just the one install and one cd key that comes with the game?
It's the unreal anthology 1 dvd version.

As long as the server isn't setup to track statistics, I don't think the server does any key checking.  When statistics are turned on, if multiple keys will be disconnected. I am going from memory though.

Have you tried any of the open source alternatives like Nexiuz: [http://www.alientrap.org/nexuiz/](http://www.alientrap.org/nexuiz/)

---

### Post by mike* on 2009-08-18
Thanks, I have never heard of it.
There is also this [http://www.quakelive.com/](http://www.quakelive.com/)which says linux coming soon.
It's browser based but it might be good.

---

### Post by Bollepolle on 2009-08-27
Hello there people. After 2 hours of work fiddling about (i run OpenSUSE, so i had to do a bit of translating n stuff) now it works, but when i start it up, my monitor of all things starts protesting that i can't run the resolution. How can i change the resolution without entering the game?

---

### Post by Perfect Storm on 2009-08-27
> **Bollepolle said:**
> Hello there people. After 2 hours of work fiddling about (i run OpenSUSE, so i had to do a bit of translating n stuff) now it works, but when i start it up, my monitor of all things starts protesting that i can't run the resolution. How can i change the resolution without entering the game?

Make the changes you need in;
```
nano ~/.ut2004/System/UT2004.ini
```

sub. "[SDLDrv.SDLClient]"

---

### Post by Bollepolle on 2009-08-27
Thanks a lot. Works flawless now

---

### Post by dasy2k1 on 2009-09-20
Well ive managed to get the script to work on my AMD64 system but when i try to run i get the following error

```

mchi8ds2@mchi8ds2-desktop:~/Games/Unreal/System$ ./ut2004-bin-linux-amd64 
Failed to enter Entry: Can't find file for package 'AS_FX_TX'

History: 

Exiting due to error
mchi8ds2@mchi8ds2-desktop:~/Games/Unreal/System$ 

```

anyone know whats going on here?

---

### Post by Brebs on 2009-09-21
> **dasy2k1 said:**
> Failed to enter Entry: Can't find file for package 'AS_FX_TX'

Check that you have these files:

```
/opt/ut2004# find -type f -print0 | xargs -0 grep AS_FX_TX
Binary file ./Textures/AS_FX_TX.utx matches
Binary file ./StaticMeshes/AS_Weapons_SM.usx matches
Binary file ./System/UT2k4AssaultFull.u matches
Binary file ./System/UnrealGame.u matches
Binary file ./System/UT2k4Assault.u matches
Binary file ./System/StreamLineFX.u matches
Binary file ./System/OnslaughtBP.u matches
Binary file ./System/XWeapons.u matches
Binary file ./System/SkaarjPack.u matches
Binary file ./System/Onslaught.u matches
Binary file ./System/OnslaughtFull.u matches
(plus lots of maps files)
```

---

### Post by irritated skin on 2009-09-30
Has anyone installed this on Jaunty 64-bit? I have not sound. I'm having problems finding the correct OpenAL libs. I only have libopenal.so.1.

 Does anyone know of a workaround to get the proper OpenAL files?

---

### Post by Perfect Storm on 2009-09-30
nwm

---

### Post by Brebs on 2009-10-02
> **irritated skin said:**
> I only have libopenal.so.1.

What's the problem? Run:
```
ln -sfn /usr/lib64/libopenal.so.1 /opt/ut2004/System/openal.so
```

---

### Post by pseudonym on 2009-12-27
I followed the howto on page 1 of this thread but I get this error when trying to start the game -
```
error while loading shared libraries: ./libSDL-1.2.so.0: cannot open shared object file: No such file or directory
```
I've tried both copying and linking the SDL/OpenAL libraries to the game 'System' folder. The same problem occurs with both the 32-bit and 64-bit libraries/executables.

It's been a while since I gamed on Linux but from memory this kind of issue would be easily resolved with renaming/linking, both of which I've tried.

Any clues?

TIA

---

### Post by lavinog on 2009-12-27
> **pseudonym said:**
> I followed the howto on page 1 of this thread but I get this error when trying to start the game -
```
error while loading shared libraries: ./libSDL-1.2.so.0: cannot open shared object file: No such file or directory
```
I've tried both copying and linking the SDL/OpenAL libraries to the game 'System' folder. The same problem occurs with both the 32-bit and 64-bit libraries/executables.

It's been a while since I gamed on Linux but from memory this kind of issue would be easily resolved with renaming/linking, both of which I've tried.

Any clues?

TIA
How are you linking the files.
The installed library filenames are not the same as the files that ut2004 is looking for.

what does this give:
```

ls /usr/lib/libSDL*

```

---

### Post by pseudonym on 2009-12-27
> **lavinog said:**
> what does this give:
```

ls /usr/lib/libSDL*

```

The output is -
```
/usr/lib/libSDL-1.2.so.0  /usr/lib/libSDL-1.2.so.0.11.2
```

But I'm making sure the links are named the way it says in the howto ie libSDL-1.2.so.0 and openal.so.

---

### Post by lavinog on 2009-12-28
Are the symlinks in the same folder as ucc-bin?

What type of installation disk do you have (dvd/cd) and which version?
I have the Editor's Choice Edition DVD which has a linux installer.  If you happen to have the same version, you could try that.

---

### Post by pseudonym on 2009-12-28
> **lavinog said:**
> Are the symlinks in the same folder as ucc-bin?
No, they are in the 'System' folder in the game's install folder. This is according to the howto on page 1 of this thread. But I will try what you say when I have time again.

> **lavinog said:**
> What type of installation disk do you have (dvd/cd) and which version?
It's the Unreal Anthology version by Midway, which includes Unreal 1 & 2 plus UT99 and UT2004. This thread is only about the Anthology version, which unfortunately doesn't have a Linux installer.

Thanks for your help.

---

### Post by Brebs on 2009-12-28
> **pseudonym said:**
> error while loading shared libraries

Use my startup script:

```
#!/bin/bash

# For libstdc++.so.5:  yum install compat-libstdc++-33 compat-libstdc++-33.i386

# 0 seems OK. Alternative is 1.
# 0 can fix mouse issues:  http://forums.gentoo.org/viewtopic-t-746300.html
export SDL_VIDEO_X11_DGAMOUSE=0

cd "/opt/ut2004/System"
export LD_LIBRARY_PATH="${LD_LIBRARY_PATH}:..:."

#echo "Press Esc before it crashes on the intro!"
# sed -i -e "/^LocalMap=/s/.*/LocalMap=NoIntro.ut2/" ~/.ut2004/System/UT2004.ini
# As posted at http://forums.gentoo.org/viewtopic-p-4841117.html#4841117

# From http://www.nvnews.net/vbulletin/showthread.php?t=104776
# Can't notice any difference
#export __GL_FSAA_MODE=5

#export __GL_YIELD="NOTHING"
export __GL_SYNC_TO_VBLANK=1

# Symlinks:
# ln -sfn /usr/lib/libopenal.so.1 /opt/ut2004/System/openal.so
# ln -sfn /usr/lib/libSDL-1.2.so.0 /opt/ut2004/System/libSDL-1.2.so.0

# Jerkiness is solved by turning "handedness" off.
# As posted at http://forums.gentoo.org/viewtopic-p-4173559.html#4173559
# sed -i -e "/^Handedness=/s/.*/Handedness=2.000000/" ~/.ut2004/System/User.ini

exe="ut2004-bin-linux-amd64"
[[ $(uname -m) == "i686" ]] && exe="ut2004-bin"
./"${exe}" "$@"
```

Notice the "LD_LIBRARY_PATH" stuff, which should fix your library issue.

---

### Post by pseudonym on 2009-12-29
> **Brebs said:**
> Use my startup script <snip> which should fix your library issue.

Yes, I used your script (after editing to my needs - different install dir and no nvidia) and the game starts now. Thanks.

Only there's one other showstopping issue - the sound goes all crackly and distorted. I read that installing the pulseaudio SDL audio library might help. It didn't, and nor did the others (alsa, esd etc).

I'm guessing that somehow pulseaudio is the culprit?? On Hardy I just removed it but unfortunately that's not so simple on Karmic. In any case I'd prefer to keep it because I have a TV connected to my PC via HDMI, and pulse makes switching between that and the default sound card quite easy.

Oh well :(

---

### Post by Brebs on 2009-12-29
UT2004 uses openal, and definitely prefers 44100hz to 48000hz, so put in ~/.alsoftrc

```
format = AL_FORMAT_STEREO16
frequency = 44100
drivers = alsa
```

---

### Post by pseudonym on 2009-12-29
Unfortunately the ~/.alsoftrc hasn't fixed the sound issue (I logged out and back in again before trying).

FWIW the terminal shows this when I run the game -
```
AL lib: alsa.c:675: set access failed: Invalid argument
```
Is there a way I can make the game use something beside OpenAL? Like, say, software sound? I looked in the in-game options plus the .ini files in ~/.ut2004 but I couldn't see a way...

---

### Post by Brebs on 2009-12-31
> **pseudonym said:**
> logged out
Not needed - just restart the game, for openal to re-read its config.

UT2004 uses openal and only openal for sound, AFAIK. Presumably, you have a cheapo soundcard :(

Try adding:
```
[alsa]
## mmap:
#  Sets whether to try using mmap mode (helps reduce latencies and CPU
#  consumption). If mmap isn't available, it will automatically fall back to
#  non-mmap mode. True, yes, on, and non-0 values will attempt to use mmap. 0
#  and anything else will force mmap off.
mmap = false
```

---

### Post by pseudonym on 2009-12-31
> **Brebs said:**
> Presumably, you have a cheapo soundcard
No, it's an Auzentech X-Plosion - based on C-Media 8770, which gives very nice SPDIF sound (and in Windows it's real-time encoded Dolby Digital Live). I've never had any problems with this card before, albeit with previous versions of Ubuntu.

FYI I also get the same crackling/distortion when I output the sound through the HDMI port on my video card. So I don't think it's a hardware issue.

> **Brebs said:**
> Try adding:
```
[alsa]
## mmap:
#  Sets whether to try using mmap mode (helps reduce latencies and CPU
#  consumption). If mmap isn't available, it will automatically fall back to non-mmap mode. True, yes, on, and non-0 values will attempt to use mmap. 0
#  and anything else will force mmap off.
mmap = false
```
No dice, assuming you meant add this section to ~/.alsoftrc.

---

### Post by Audi.RS4 on 2010-04-09
I find it hard to believe no one has posted this yet but there is a installer for the Midway version of Unreal Tournament 2004. It was developed by Loki Installers.

I have the Midway version and have used the installer and can say that it works great. You just insert the DVD and it will handle extracting the cab files for you. Its so simple a caveman could do it.

[http://www.liflg.org/?catid=6&gameid=17](http://www.liflg.org/?catid=6&gameid=17)

Hope this helps anyone who is still playing this game.

---

### Post by lavinog on 2010-04-09
> **Audi.RS4 said:**
> I find it hard to believe no one has posted this yet but there is a installer for the Midway version of Unreal Tournament 2004. It was developed by Loki Installers.

I have the Midway version and have used the installer and can say that it works great. You just insert the DVD and it will handle extracting the cab files for you. Its so simple a caveman could do it.

[http://www.liflg.org/?catid=6&gameid=17](http://www.liflg.org/?catid=6&gameid=17)

Hope this helps anyone who is still playing this game.

It was mentioned, but it only exists on the DVD, not the cd versions.

---

### Post by gerowen on 2010-05-11
Ok, so I'm trying this out, I have all of the files except the oldest version of libstdc++ available in the 10.04 repos is 6, and UT is looking for 5.  I tried renaming and copying the libstdc++.so.6 file to libstdc++.so.5 in the System folder but then it gave me an error about certain commands that weren't there.  Any ideas?

Edit: Is there a standalone copy of this library that I could just download and stick in the System folder?  Anybody have a copy they wouldn't mind posting on a dropbox or something?

---

### Post by gerowen on 2010-05-11
Ok so just in case anybody else runs into my problem(read above), here is the solution.  I managed to snag a copy of 32 bit and 64 bit libstdc++.so.5 libraries.  I've tarred them up together and put them on my dropbox.  After putting the library in my UT 2004's system folder it works fine, even though the version of libstdc++ that's actually installed on my system is a newer version.  Basically all I did was search for a .rpm or .deb of libstdc++5x and then extracted it to get to the library, took me a bit to find a 64 bit one though, which is why I'm posting it here to save you all the trouble.

**[Linkage](http://dl.dropbox.com/u/6017319/Software/libstdc%2B%2B.so.5.tar.gz)**

Edit: I've got to go to bed so I have to read the EULA for Unreal, but if anybody knows please answer this question for me.  If I were to script an install including the entire game with the appropriate libraries to avoid the above issue with dependencies, and just require a CD key to continue, would it be legal to release to the public as long as I didn't charge for it?  P.S. Mine works great, higher framerate than I had in Windows for some reason.

---

### Post by ELD on 2010-05-11
> **marcusdean.adams said:**
> Ok so just in case anybody else runs into my problem(read above), here is the solution.  I managed to snag a copy of 32 bit and 64 bit libstdc++.so.5 libraries.  I've tarred them up together and put them on my dropbox.  After putting the library in my UT 2004's system folder it works fine, even though the version of libstdc++ that's actually installed on my system is a newer version.  Basically all I did was search for a .rpm or .deb of libstdc++5x and then extracted it to get to the library, took me a bit to find a 64 bit one though, which is why I'm posting it here to save you all the trouble.

**[Linkage]("http://dl.dropbox.com/u/6017319/Software/libstdc%2B%2B.so.5.tar.gz")**

Edit: I've got to go to bed so I have to read the EULA for Unreal, but if anybody knows please answer this question for me.  If I were to script an install including the entire game with the appropriate libraries to avoid the above issue with dependencies, and just require a CD key to continue, would it be legal to release to the public as long as I didn't charge for it?  P.S. Mine works great, higher framerate than I had in Windows for some reason.

Do you really need to ask such a question. You will be distributing copyrighted material of course it will be illegal.

---

### Post by lavinog on 2010-05-12
> **ELD said:**
> Do you really need to ask such a question. You will be distributing copyrighted material of course it will be illegal.

Yes.
Also would you really want to distribute a 4g install script?
The better way to go about this is to buy a more recent version of the game that has the linux installer already.

---

### Post by ELD on 2010-05-12
> **lavinog said:**
> Yes.
Also would you really want to distribute a 4g install script?
The better way to go about this is to buy a more recent version of the game that has the linux installer already.

Yeah a weird idea to say the least.

---

### Post by milanfin on 2010-12-29
This is bit old topic but I'll ask

I have "installed" the game, but I don't have few of .ini files.
I have these already:
```
milan@milan-desktop:~/ut2004/System/System$ ls *.ini
Build.ini    DefUnrealEd.ini  Manifest.ini       UDNHelpTopics.ini
Default.ini  DefUser.ini      ServerFilters.ini  UnrealEdTips.ini

```

I have two system folders is that the problem?

---

### Post by Brebs on 2010-12-29
> **milanfin said:**
> I have two system folders is that the problem?
Yes.

---

### Post by milanfin on 2010-12-29
Yes it was the problem :D
Now it works great.

---

### Post by brunowarne on 2010-12-30
But I found some error in this when i was running.

---

### Post by Virus666 on 2011-06-25
Finally, thanks to **[adam_kimber]("http://ubuntuforums.org/member.php?u=46101")** and **[NESFreak]("http://ubuntuforums.org/member.php?u=77308")** I could install **Unreal Tournament 2004** natively from **Unreal Anthology**. Thank you!...

Since the **Unshield** did not work for me, I skiped step 1, 4, 5, 6, 7, 8, 9, 10, 11. I used **PlayOnLinux** to unshield the **CAB** files by installig the game manually as adam_kimber refered **5a - 6a**. Then I carried **UT2004** folder and added the Linux patch. With a small number of stuff, the game is working like a charm... :-)

Here is my easier and less code needed method:
[SIZE=2]
[/SIZE]
[LIST=1]
[*][SIZE=2]Install **playonlinux**, **libopenal1**, **libsdl1.2debian**, **alsa-oss** packages via **Synaptic**.[/SIZE]
[*][SIZE=2]Get the lastest Linux patch of Unreal Tournament 2004 (which is now **v3369.2**): [ut2004-lnxpatch3369-2.tar.bz2]("http://www.gamershell.com/download_11985.shtml")[/SIZE]
[*][SIZE=2]Get NESFreak's sound files: [linux-x86.tar.bz2]("http://ubuntuforums.org/attachment.php?attachmentid=30925&d=1177599405")[/SIZE]
[*][SIZE=2]After inserting the DVD, install **only** Unreal Tournament 2004 via PlayOnLinux: PlayOnLinux > Install > Install a .pol package or an unspported application > *the rest is the Windows way*; setup.exe is in **Disk1** folder.[/SIZE]
[*][SIZE=2]Copy **UT2004** folder of PlayOnLinux to your **Home** folder. The location of UT2004 folder: ~/.PlayOnLinux/wineprefix/YourPrefixName/drive_c/Unreal Anthology[/SIZE]
[*][SIZE=2]Delete all the **.exe** files in the System folder of UT2004.[/SIZE]
[*][SIZE=2]You may delete PlayOnLinux installation of Unreal Tournament 2004 via PlayOnLinux.
[/SIZE]
[*][SIZE=2]Unpack the UT2004's Linux patch and copy the content folder to the UT2004 folder; apply all the changes.[/SIZE]
[*][SIZE=2]Unpack linux-x86.tar.bz2 and copy the System folder to the UT2004 folder; apply all the changes.[/SIZE]
[*][SIZE=2]Make a text file via a text editor (such as **Gedit**); put your CD KEY to the first line (like that: XXXXX-XXXXX-XXXXX-XXXXX); save the file to the System folder of UT2004 as **CDkey**.[/SIZE]
[*][SIZE=2]Your game is ready; you may start it by double clicking **ut2004-bin** file; however as you noticed there is no sound in the lasted versions of **Ubuntu**; we need to start the game with a sound **wrapper**. We will come to that soon.[/SIZE]
[*][SIZE=2]Now, we will make a **bin** which launches the game with a sound wrapper: ```
sudo nano /usr/local/bin/ut2004
``` Add following lines according to the location of UT2004 folder in your system: ```
cd ~/UT2004/System
``` ```
aoss ./ut2004-bin 
``` **OR** ```
padsp ./ut2004-bin
``` Save file.[/SIZE]
[*][SIZE=2]The last thing we need to do is to make a shortcut of the game; right click to the desktop > Create Launcher > Name: Unreal Tournament 2004, Command: ut2004 > OK[/SIZE]
[/LIST]
That's all! Now can start the game via double clickling the **Unreal Tournament 2004** icon in the desktop. Enjoy this nice multiplayer game... :guitar:

**Sources**:
[http://ubuntuforums.org/showpost.php?p=2360859&postcount=1](http://ubuntuforums.org/showpost.php?p=2360859&postcount=1)
[http://ubuntuforums.org/showpost.php?p=2532915&postcount=5](http://ubuntuforums.org/showpost.php?p=2532915&postcount=5)
[http://utforums.epicgames.com/showpost.php?p=24710581&postcount=1](http://utforums.epicgames.com/showpost.php?p=24710581&postcount=1)
[https://help.ubuntu.com/community/HowToAddaLauncher](https://help.ubuntu.com/community/HowToAddaLauncher)
[https://help.ubuntu.com/community/Games/Native/UnrealTournament2004](https://help.ubuntu.com/community/Games/Native/UnrealTournament2004)


**Note**: This method applies only for the Unreal Anthology pack. For those who have just Unreal Tournament 2004 CD/DVD may look at following link:
[https://help.ubuntu.com/community/Games/Native/UnrealTournament2004](https://help.ubuntu.com/community/Games/Native/UnrealTournament2004)

---

### Post by PIDGINZ on 2011-08-02
I was about to type out a whole long post about how I was having issues with the libraries being of the wrong ELF class, but then I changed my ut2004 script to start ut2004-bin-linux-amd64 and now it all works. Derp. :D

EDIT: If you get issues with libstdc++5, it is in the backports repo on Ubuntu 10.04

---

### Post by Deadtrooper on 2012-05-04
One damn problem after another to get this to run. After 8 hours pratting about I get it to run - but -I have no sound. Extract linux-x86.tar.bz2 and copy system files. Simples? Have a guess. The Archive Manager tells me this is not a bzip2 file and exits. Can some kind person tell me how to open this/direct me to something that will open/zip the content of the System folder and post it or a link to such please? Fingers Xed. Thanks

---

### Post by Brebs on 2012-05-04
> **Deadtrooper said:**
> I have no sound
So look at the messages that UT2004 puts on the screen. Anything about sound?

> The Archive Manager tells me this is not a bzip2 file
You probably have a bad download. Try downloading it again.

---

### Post by Deadtrooper on 2012-05-05
It ran. No error messages just no sound. Downloaded .bz2 file several times, none would open. Have solved it with Alsa wrapper for OSS. Played thru five levels fine apart from crashing out several times. Game probably needs patching. I'll do that later. All the faffing about was actually fun. It is true what they say - you learn nothing if everything is going okay. Thanks and ttfn.

---

