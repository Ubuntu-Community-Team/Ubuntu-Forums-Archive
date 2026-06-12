---
title: "Counter strike clone for linux"
date: 2005-10-18
forum: Gaming &amp; Leisure
---

### Post by Ibuntu_52 on 2005-10-18
Enemy territory is a counter strike like game that runs natively in linux.It's a mod based on wolfenstein enemy territory.Both the game and the mod can be downloaded for free.

Enemy territory can be found here:

[http://linux.softpedia.com/progDownload/Wolfenstein-Enemy-Territory-Download-3948.html](http://linux.softpedia.com/progDownload/Wolfenstein-Enemy-Territory-Download-3948.html)

just choose the  fastest mirror and when it's done go to the applications menu acesories/terminal then type
```
#sudo sh /home/yourusername/et-linux-2.60.x86.run
```

then download the true combat mod (torrent):

[http://liflg.matrixau.com/torrents/true.combat.elite_0.48-english-5.run.torrent](http://liflg.matrixau.com/torrents/true.combat.elite_0.48-english-5.run.torrent)

then install it like this
```
#sudo sh /home/yourusername/true.combat.elite_0.48-english-5.run
```

before you play it type
```
# echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss

```

otherwise the sound won't work

I think the game has to run in root I'm not sure tho anyways type
```
#sudo tc-elite
```

to play, or if you can play online without being root just go to the application menu and it should be in the "other" tab

---

### Post by MetalMusicAddict on 2005-10-18
Thanx for this man. Anyone looking at this it was *VERY* easy to do this. Worth the try. :)

Im using Breezy-Final on a Dell Inspiron 2200 and I dont need to do the "**echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss**" command if I run as sudo.

I have a question. I can run games @1024x796 on this machine but no matter what I try I can only get this to run @800x600. Also its in a 800x600 mode that puts the screen in the lower left of my 1024x768 screen. Not windowed but with black bars.

Any Ideas on how to fix it? Im ok with running @800x600 if it filled the screen. I guess its not changing my desktop res properly.

---

### Post by bored2k on 2005-10-18
Not to player hate but, there is no Counter Strike clone in the universe. Sure, it's a FPS just like CS, but that's where similarities stop.. modded or not. CS needs a genre of it's own. I'd say KA-FPE for Kick.Ass-First.Person.Experience.

---

### Post by MetalMusicAddict on 2005-10-18
Hater. :) Are their any FPS in the repos?

Have you tried this? Its pretty cool. I just need to get this 1 bug worked out.

---

### Post by Samuel on 2005-10-18
i havnt tried the mod yet (downloading now) but when it tried to download a map when i connect to a server the game crashes to desktop, not tried as root though, isnt that a little iffy? logging onto someones server as root?

---

### Post by charlieg on 2005-10-18
[QUOTE=MetalMusicAddict]I have a question. I can run games @1024x796 on this machine but no matter what I try I can only get this to run @800x600. Also its in a 800x600 mode that puts the screen in the lower left of my 1024x768 screen. Not windowed but with black bars.[/QUOTE]
Have you tried using the manual controls on the monitor to adjust screen position/size?  Y'know, the buttons on the bottom of the front of the monitor.

As for running as sudo?  No, don't.

Did you just try 'sh tc-elite.run' to install it locally?  Or did you try adding yourself to the games group or whatever group owns the directory it installed to (should be /opt/somewhere).

---

### Post by rsulli55 on 2005-10-18
How do I download it when I click on the mirror all I get is this
```

#!/bin/sh
# This script was generated using Makeself 2.1.4

CRCsum="764704454"#!/bin/sh
# This script was generated using Makeself 2.1.4

CRCsum="764704454"
MD5="b8b59bc515d86cc845fb52f5d2c14423"
TMPROOT=${TMPDIR:=/tmp}

label="Enemy Territory 2.60 Full Install"
script="./setup.sh"
scriptargs=""
targetdir="build-install-2.60"
filesizes="270956492"
keep=n

print_cmd_arg=""
if type printf > /dev/null; then
    print_cmd="printf"
elif test -x /usr/ucb/echo; then
    print_cmd="/usr/ucb/echo"
else
    print_cmd="echo"
fi

MS_Printf()
{
    $print_cmd $print_cmd_arg "$1"
}

MS_Progress()
{
    while read a; do
	MS_Printf .
    done
}

MS_dd()
{
    blocks=`expr $3 / 1024`
    bytes=`expr $3 % 1024`
    dd if="$1" ibs=$2 skip=1 obs=1024 conv=sync 2> /dev/null | \
    { test $blocks -gt 0 && dd ibs=1024 obs=1024 count=$blocks ; \print_cmd_arg=""
if type printf > /dev/null; then
    print_cmd="printf"
elif test -x /usr/ucb/echo; then
    print_cmd="/usr/ucb/echo"
else
    print_cmd="echo"
fi

MS_Printf()
{
    $print_cmd $print_cmd_arg "$1"
}

MS_Progress()
{
    while read a; do
	MS_Printf .
    done
}

MS_dd()
{
    blocks=`expr $3 / 1024`
    bytes=`expr $3 % 1024`
    dd if="$1" ibs=$2 skip=1 obs=1024 conv=sync 2> /dev/null | \
    { test $blocks -gt 0 && dd ibs=1024 obs=1024 count=$blocks ; \
      test $bytes  -gt 0 && dd ibs=1 obs=1024 count=$bytes ; } 2> /dev/null
}

MS_Help()
{
    cat << EOH >&2
Makeself version 2.1.4
 1) Getting help or info about $0 :
  $0 --help   Print this message
  $0 --info   Print embedded info : title, default target directory, embedded script ...
  $0 --lsm    Print embedded lsm entry (or no LSM)
  $0 --list   Print the list of files in the archive
  $0 --check  Checks integrity of the archive
 
 2) Running $0 :
  $0 [options] [--] [additional arguments to embedded script]
  with following options (in that order)
  --confirm             Ask before running embedded script
  --noexec              Do not run embedded script
  --keep                Do not erase target directory after running
			the embedded script
  --nox11               Do not spawn an xterm
  --nochown             Do not give the extracted files to the current user
  --target NewDirectory Extract in NewDirectory
  --tar arg1 [arg2 ...] Access the contents of the archive through the tar command
  --                    Following arguments will be passed to the embedded script
EOH
}
      test $bytes  -gt 0 && dd ibs=1 obs=1024 count=$bytes ; } 2> /dev/null
}

```

except theres a lot more.   I am not sure what I need to do?  Sorry for the hassle I am new to linux. Thanks

---

### Post by Ibuntu_52 on 2005-10-18
> I have a question. I can run games @1024x796 on this machine but no matter what I try I can only get this to run @800x600. Also its in a 800x600 mode that puts the screen in the lower left of my 1024x768 screen. Not windowed but with black bars.

I'm sorry I have no idea how to fix this.There is a section on the true combat forums for linux tech support.

[http://www.truecombat.com/forum/viewforum.php?f=9&sid=e8619d4f7948676d035647609e894480](http://www.truecombat.com/forum/viewforum.php?f=9&sid=e8619d4f7948676d035647609e894480)

Maybe someone there knows about the problem.

Lol, I know it's not a total clone of counter strike.I just posted that in the title to atract people who like counter strike.Because it is in the same vein as counter strike.

I personally like it better as a game than counter strike:source, but the fanbase/servers is better in cs:source.I havent even bothered with installing cs:source through wine.

**rsulli55** right click and save as.I don't know why but fiefox dosn't seem to recognize some shell scripts.

---

### Post by skirkpatrick on 2005-10-18
I don't run TC:E using sudo at all.  And the only reason I do the "echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss" is to use TC:E and Teamspeak at the same time.

---

### Post by rsulli55 on 2005-10-18
Do I save the link as, or do I click on it then save as, or what?  And also, what do I do after I save it?  Thanks

EDIT: I got it now, thanks though.

---

### Post by oxEz on 2005-10-19
If anyone is interested in a freaking fast mirror, here is a link to filefront:

[http://files.filefront.com/et+linux+260x86run/;3830837;/fileinfo.html]("http://files.filefront.com/et+linux+260x86run/;3830837;/fileinfo.html")

(By the way, thank you for this game, I think it should be fun since I loved wolfenstein on xbox live :])

---

### Post by jeffreyvergara.NET on 2005-10-19
thanks for the link oxEz, softpedia link is so slow...

---

### Post by oxEz on 2005-10-19
I didn't find a server for the mod.. they were all empty! And when I want to create my own so I can get the idea of the game it crashes to the desktop. Anyway I can play ET (no mods) quite well.. I cannot see my precise FPS but I get around 90-120 easily (with an ATI card, which is amazing)..

---

### Post by dgoodwin on 2005-10-19
> **rsulli55]How do I download it when I click on the mirror all I get is this
```

#!/bin/sh
# This script was generated using Makeself 2.1.4

CRCsum="764704454"#!/bin/sh
# This script was generated using Makeself 2.1.4

CRCsum="764704454"
MD5="b8b59bc515d86cc845fb52f5d2c14423"
TMPROOT=${TMPDIR:=/tmp}

label="Enemy Territory 2.60 Full Install"
script="./setup.sh"
scriptargs=""
targetdir="build-install-2.60"
filesizes="270956492"
keep=n

print_cmd_arg=""
if type printf > /dev/null said:**
>  [--] [additional arguments to embedded script]
  with following options (in that order)
  --confirm             Ask before running embedded script
  --noexec              Do not run embedded script
  --keep                Do not erase target directory after running
			the embedded script
  --nox11               Do not spawn an xterm
  --nochown             Do not give the extracted files to the current user
  --target NewDirectory Extract in NewDirectory
  --tar arg1 [arg2 ...] Access the contents of the archive through the tar command
  --                    Following arguments will be passed to the embedded script
EOH
}
      test $bytes  -gt 0 && dd ibs=1 obs=1024 count=$bytes ; } 2> /dev/null
}

```

except theres a lot more.   I am not sure what I need to do?  Sorry for the hassle I am new to linux. Thanks



You can right click with your mouse and choose "Save Link As" and this should start your download

---

### Post by B.B on 2005-10-19
How do i unstall this ?

---

### Post by Mustard on 2005-10-19
I appreciate this thread.  I've been missing playing CS. This is a decent enough substitute.

---

### Post by Elmorulz on 2005-10-19
[QUOTE=Ibuntu_52]Enemy territory is a counter strike like game that runs natively in linux.It's a mod based on wolfenstein enemy territory.Both the game and the mod can be downloaded for free.

Enemy territory can be found here:

[http://linux.softpedia.com/progDownload/Wolfenstein-Enemy-Territory-Download-3948.html](http://linux.softpedia.com/progDownload/Wolfenstein-Enemy-Territory-Download-3948.html)

just choose the  fastest mirror and when it's done go to the applications menu acesories/terminal then type
```
#sudo sh /home/yourusername/et-linux-2.60.x86.run
```

then download the true combat mod (torrent):

[http://liflg.matrixau.com/torrents/true.combat.elite_0.48-english-5.run.torrent](http://liflg.matrixau.com/torrents/true.combat.elite_0.48-english-5.run.torrent)

then install it like this
```
#sudo sh /home/yourusername/true.combat.elite_0.48-english-5.run
```[/QUOTE]

after this step i got an error: Gdk-WARNING **: locale not supported by C library

when I'm trying to play this game I get a totally black screen but I've got sound someone any idee how to fix this??

---

### Post by jeffreyvergara.NET on 2005-10-19
weird... Im just playing this game with sound after I finished installing it, but after I restart my PC there's no sound anymore

---

### Post by GazaM on 2005-10-19
Ok now I'm angry, I was nearly finished a HUGE reply trying to help the issues people are having, pressed backspace to delete a mistake and instead of deleting a letter it made Firefox go back a page, losing my almost complete reply :(

Anyway, not going to type it all again (sorry) but here are the main points...

MetalMusicAddict: I experienced these issues before and know how to fix them, although I would prefer to do so through IM or PM as it would take me ages to right it out (again :P) so if you want help just PM or MSN me (MSN address in my profile, I really want a Jabber option in Profile though)... I have an ATI card but I think the options which cause that behaviour are common to both ATI and nVidia xorg.conf's.

Secondly, anyone interested in joining the European Ubuntu Clan (ubu-e) please just check out the sticky thread (which may still be in the hoary section, sorry if it is :P), go to IRC at #ubu-e on freenode or check out the website at [http://www.katanoon.nl/ubu-e/]("http://www.katanoon.nl/ubu-e/") (which I am currently trying to get the clan leaders permission to redesign, which should include some more thorough tutorials and stuff). We currently play TC:E mainly and would like to play ET as well. Every Ubuntu user is welcome!

Do not run the game as sudo, sound issues are beyond the scope of this reply (it would take too long to explain them) but just go to a root terminal and use these commands (root terminal, NOT sudo in normal terminal):

echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss

A lot of people who use onboard sound, such as myself have this issue, but people with a good sound card probably will not. It is due to a thing called mmap which the Quake3 engine uses for audio, although I dont know full details, what I do know is that it seems the drivers for AC'97 onboard audio chipsets that comes with Ubuntu and other distros does not yet support the mmap function properly and I'm not sure if this is being planned, will or can be fixed in future drivers (possibly with Dapper?)

If you need to run as sudo to download extra content from servers then something is wrong, probably you made a mistake when installing it and now permissions are messed up etc... ET can be installed with sudo, into the default directory, and the TC:E zip's from the official site can be put there as normal and everything should run fine.

[edit] Almost forgot, the ingame server browser seems to be broken as of the current version, so please use XQF which can be found in the repos... it's a great Server Browser and I would recommend it over using any in game server browser, working or not. Just go the Enemy Territory server list, reload the list if required and type the word 'tcetest' into the filter box in order to see only TC:E games... there are always a good few very active servers up, it's a very popular game :D

Anyway, hope I've helped, because if not my fingers are gonna fall off for nothin :P

---

### Post by jeffreyvergara.NET on 2005-10-19
i've installed TC:E and run it for the first and I got no problem with sound, it really worked fine, as what I have said earlier on my post, the next time i run the game it does not have sound anymore.

I tried 
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
but I just keep getting "permission denied"

I installed the game in it's default directory, do you think it is better to install it under /home/user/folder????

---

### Post by tHub on 2005-10-19
yeah this mod is great, makes this game playable(ET is freaking hilarious with those ppl jumping like bunnys)
too bad im from brazil and we have no TCE servers so i have to play with 180+ ping
another annoying thing is that most servers that actually have ppl playing have a bunch of 6mb+ custom maps heh (well at least its annoying for me coz i have a 256k connection, so when i finnish the download they're already playing another map so i have to download it too lol)
Overall is worth the download

---

### Post by GazaM on 2005-10-19
[QUOTE=jeffreyvergara.NET]i've installed TC:E and run it for the first and I got no problem with sound, it really worked fine, as what I have said earlier on my post, the next time i run the game it does not have sound anymore.

I tried 
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
but I just keep getting "permission denied"

I installed the game in it's default directory, do you think it is better to install it under /home/user/folder????[/QUOTE]
Have you run those commands through a ROOT terminal? You need to go to Applications>System Tools>Root Terminal as a normal terminal will not work for this purpose, even with sudo.

If you have done this and are sure you have done so correctly then i would advise you to post the terminal output of TC:E for the time when sound doesnt work.

---

### Post by MetalMusicAddict on 2005-10-19
[QUOTE=B.B]How do i unstall this ?[/QUOTE]
Yea. I borked something and need to reinstall.

---

### Post by skirkpatrick on 2005-10-19
jeffreyvergara.NET: the problem is that you need to be root or sudo to mess with the proc files.  Here's an easier way and you don't have to remember to run the commands everytime you want to play:

> 
1) Open a command-line console. Obtain super-user access by either using "su" to change your access or using "sudo" in front of each command. I'll be using "sudo" here.

2) Execute the "runlevel" command. This will tell you what access-level your system is running at. Ubuntu uses runlevel 2 and I believe Fedora Core and Redhat use runlevel 3. I'll be using 2 here.

3) Change to the /etc/init.d directory. Create and edit a file called GameSound. Put the following lines in it for ET:
[quote]

#!/bin/bash
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm0c/oss
echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
echo "et.x86 0 0 disable" > /proc/asound/card0/pcm1c/oss

You can add or substitue q3.x86 for et.x86 for Quake 3.

4) Change the permissions on GameSound with the following:
> 
sudo chmod 755 /etc/init.d/GameSound


5) Change to the /etc/rc2.d directory

6) Create a symbolic link to have GameSound automatically run on startup:
> 

sudo ln -s /etc/init.d/GameSound ./S99GameSound


Reboot and things should be taken care of. If you find another game that's having a problem, add it to the GameSound file.
[/quote]


Also, I've got the latest version and have no problems seeing servers in the Server Browser.

---

### Post by Ibuntu_52 on 2005-10-20
I'm glad someone posted a better solution to the sound issue.Thank you, **skirkpatrick**:).

I thinkt the servers not showing up may be a router issue.Try to find a tutorial on port-forwarding for your router.If you have a 2link modem I may be able to help you.

---

### Post by jeffreyvergara.NET on 2005-10-20
@skirkpatrick, i did what you posted but still my sound wont work. I dont know If i did it correctly but I did not encounter any error. I dont quite understand what you meant by make GameSound file so I did "sudo gedit" then paste the codes and saved it as GameSound.

I also have a problem with "cannot write hunkusage.dat" something like that so there's a problem with my permission? I installed it on it's default directory.

---

### Post by jeffreyvergara.NET on 2005-10-20
I run "sudo tc-elite" but the sound won't work, I exit TC:E then run "sudo tc-elite" again, the sound worked now. 

Is there any other way to play this properly without going to terminal and do sudo? like "applications>others>TC:E

---

### Post by amatthews_1 on 2005-10-20
I am having the same Issue with the sound.  Ir worked at first, rebooted, and then it didn't work.  I edited my init.d and rc2 and still the same problem.


Awesome game otherwise

---

### Post by skirkpatrick on 2005-10-20
I'm running Hoary right now.  I also had to get the sound to play nice which is detailed in a few HowTo's here and also at [http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly).

Hopefully, that will fix your problem.

I created a menu item for TC:E using SMEG which just calls the file .tce-elite in my home directory.  All the download maps get stored in ~/.etwolf so you shouldn't need to worry about where it installed.

---

### Post by rimmer on 2005-10-20
[QUOTE=MetalMusicAddict]Yea. I borked something and need to reinstall.[/QUOTE]

Install ET first then grab the TC:E files, all the files are here [truecombat.com]("http://truecombat.com/intro.php?x=d")

Makeing sure you are using the 2.60 ET version on your system. 

Then grab the TC:E main files and the update. Once you got them unarchive them and place them in either /home/yourname/.etwolf in your home dir or in /usr/local/games/Enemyter....../ It's up to you which one you choose it will / should work from both and that's it.
 
At the base level it's just about placing files in the right dir. There is no install script!
 
And don't run it as root ever It's NOT GOOD for your health :)

As for sound problems, I can't really help as I've never had any problem other than trying to run TS2 with TC:E in hoary, and I've not tryed that yet in breezy with my onboard sound, having said that I can now play xmms and play TC:E at the same time straight out of the sunny side up breezy box.
(there is a in game volume control have a look and see if it's turned up)

And after the install start the game with > et +set fs_game tcetest If you got problems with that then start ET from the konsol with > et then from the menu on the right select MOD, there you should find TC:E if not then it's not installed properly.

As for not being able to find any servers in the in game browser that's got to do with your router you can find more info [Here]("http://truecombat.com/forum/viewforum.php?f=9&sid=06d13c99cd0a8394949553c1a4f97947")

And if you need more install advice here is the link for the info [Info]("http://webpages.charter.net/cirithungol/tcetest/elite_install-guide.html")

And don't forget this is a work in progress it's still a beta release, were all waiting with bated breath for the final showdown.

The official site [http://truecombat.com/]("http://truecombat.com/")

If you get it installed and you like it come on to IRC #ubu-e on Freenode
The rest of the info was posted in a earler thread.

Good luck and happy fraggin ;)

ichi

And on another note to any mods who might read this would it be possable to move the ubu-e thread from the hoary topic to a slightly more visable location on the board :)

---

### Post by Elmorulz on 2005-10-20
Can someone tell me please how te uninstall this game, because when I start th game I get a black screen:S I just want to uninstall anyone an idee how to do that??

---

### Post by jeffreyvergara.NET on 2005-10-20
[QUOTE=GazaM]Have you run those commands through a ROOT terminal? You need to go to Applications>System Tools>Root Terminal as a normal terminal will not work for this purpose, even with sudo.

If you have done this and are sure you have done so correctly then i would advise you to post the terminal output of TC:E for the time when sound doesnt work.[/QUOTE]

I don't see any root terminal in application >  system tools. Im using breezy-final

---

### Post by jeffreyvergara.NET on 2005-10-21
is there anyway to play TC:E (with sounds) without running Terminal and typing sudo tc-elite?

---

### Post by rimmer on 2005-10-21
[QUOTE=Elmorulz]Can someone tell me please how te uninstall this game, because when I start th game I get a black screen:S I just want to uninstall anyone an idee how to do that??[/QUOTE]

To uninstall TC:E and ET all youv'e got to do is delete the files from the relevant directories.

---

### Post by jeffreyvergara.NET on 2005-10-21
[QUOTE=rimmer]Can someone tell me please how te uninstall this game, because when I start th game I get a black screen:S I just want to uninstall anyone an idee how to do that??[/QUOTE]

i dont know what it is but i saw uninstall.sh inside "/usr/local/games/enemy-territory/tcetest" you might want to try that.

I also get black screen sometimes, try to wait for awhile the intro movie will play soon.

---

### Post by jeffreyvergara.NET on 2005-10-21
ok.. I figured it out to make the sound working, I was not a "root" in user & groups.

---

### Post by GazaM on 2005-10-21
jeffreyvergara.NET: the root terminal is (sorry i forgot about this at first) hidden by default in breezy... just open up the SMEG menu editor and unhide it :P sorry again

---

### Post by jeffreyvergara.NET on 2005-10-21
[QUOTE=GazaM]jeffreyvergara.NET: the root terminal is (sorry i forgot about this at first) hidden by default in breezy... just open up the SMEG menu editor and unhide it :P sorry again[/QUOTE]

Thanks! now I know!.. ehehe, anyways Im now belong to root user&groups will it be alright?

---

### Post by GazaM on 2005-10-21
I'm not a linux guru in any way, but I doubt it is a good thing to have your normal user a part of the root group, as this would effectively be the same as running as root permanently, which is not good... my advice to is to restore your users normal privilages and just use the root terminal for those commands... as far as I know there is a way to have these commands run at boot, using an init script, but I will have to look for it :P

---

### Post by Mustard on 2005-10-21
I've downloaded the Wolfenstein Enemy Territory, but I haven't downloaded the TC-Elite mod yet.  I thought I would mention that when I installed Wolfenstein ET, I just used...
```
cd ~/
./et-linux-2.60.x86.run

```

The install asked me some question about wanting my root password to install in /usr/something/something, but I opted for the installation as current user in my /home directory, by pressing cancel.  Is this going to affect the installation of the TC-Elite mod?

Wolfenstein seems to run ok, and I have sound so far.  I haven't joined a server yet to find out if it runs sound in game, but it certainly seems to be functioning.

---

### Post by rimmer on 2005-10-22
[QUOTE=Mustard]I've downloaded the Wolfenstein Enemy Territory, but I haven't downloaded the TC-Elite mod yet.  I thought I would mention that when I installed Wolfenstein ET, I just used...
```
cd ~/
./et-linux-2.60.x86.run

```

The install asked me some question about wanting my root password to install in /usr/something/something, but I opted for the installation as current user in my /home directory, by pressing cancel.  Is this going to affect the installation of the TC-Elite mod?

Wolfenstein seems to run ok, and I have sound so far.  I haven't joined a server yet to find out if it runs sound in game, but it certainly seems to be functioning.[/QUOTE]

Hi the home install will not effect the runnung of the mod, in most cases it's the safest place to put it. 
Reason: it keeps you away from root.

And to install TC:E place the files in the ./etwolf folder the one that ET created, and dont forget the TC:E update, you need it in order to play the game.
Reason : The update contains the pack pak3.pk3 and this is needed by TC:E.

---

### Post by jeffreyvergara.NET on 2005-10-22
[QUOTE=GazaM]as far as I know there is a way to have these commands run at boot, using an init script, but I will have to look for it :P[/QUOTE]

thanks for the advice! ^_^ and im looking forward to the init script you are telling. :KS

---

### Post by Mustard on 2005-10-22
[QUOTE=rimmer]Hi the home install will not effect the runnung of the mod, in most cases it's the safest place to put it. 
Reason: it keeps you away from root.

And to install TC:E place the files in the ./etwolf folder the one that ET created, and dont forget the TC:E update, you need it in order to play the game.
Reason : The update contains the pack pak3.pk3 and this is needed by TC:E.[/QUOTE]

Excellent.  Thanks. :)

---

### Post by jeffreyvergara.NET on 2005-10-24
ok, Im now not in ROOT users & groups, when I run tc-elite without sudo I get something like this.

> 
------- sound initialization -------
/dev/dsp: Device or resource busy
Could not open /dev/dsp
------------------------------------
Sound memory manager started
Sys_LoadDll(/home/jeffrey/.etwolf/tcetest/ui.mp.i386.so)...
Sys_LoadDll(/home/jeffrey/.etwolf/tcetest/ui.mp.i386.so) failed:
"/home/jeffrey/.etwolf/tcetest/ui.mp.i386.so: cannot open shared object file: No  such file or directory"


I got this when I used sudo
> ------- sound initialization -------
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
32768 samples
   16 samplebits
    1 submission_chunk
22050 speed
0x0xb01fb000 dma buffer
No background file.
----------------------


so i think chaging the persmission of "/dev/dsp" would work?

---

### Post by losslesshead on 2005-10-24
Hi, I need some help.  ASAP!  I really want to play wolfenstein/TC-Elite but I am having a little problem...  Whenever I try to launch TC-Elite (or Wolfenstein for this matter) a black screen come up, and then it goes down, leaving me back where I started, Terminal.  This is what I got in Terminal:

> mav@ubuntu-basement:~$ sudo tc-elite
Password:
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/mav/.etwolf/tcetest
/usr/local/games/enemy-territory/tcetest/pak3.pk3 (89 files)
/usr/local/games/enemy-territory/tcetest/pak2.pk3 (934 files)
/usr/local/games/enemy-territory/tcetest/pak1.pk3 (526 files)
/usr/local/games/enemy-territory/tcetest/pak0.pk3 (1555 files)
/usr/local/games/enemy-territory/tcetest/mp_bin.pk3 (4 files)
/usr/local/games/enemy-territory/tcetest
/home/mav/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
6871 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 800x600
Using 8/8/8 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect


***********************************************************
 You are using software Mesa (no hardware acceleration)!
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Received signal 11, exiting...

COULD SOMEONE PLEASE TRY AND EXPLAIN WHAT'S HAPPENING!  I really want to play these games, but I need someone to help me fix this error!

---

### Post by jeffreyvergara.NET on 2005-10-25
have you installed your Video card driver correctly? it seems you hardware acceleration is off

---

### Post by rimmer on 2005-10-25
This is the problem 
>  You are using software Mesa (no hardware acceleration)!
Driver DLL used: libGL.so.1
If this is intentional, add
"+set r_allowSoftwareGL 1"
to the command line when starting the game.

As jeffreyvergara.NET has already written from the output it seams you are not 
using the correct drivers for your video card.

---

### Post by losslesshead on 2005-10-25
Ok.  Thanks.  I am not sure at the moment what video card the computer has, because it is really old (and was also given to me a couple days ago), and I don't know the model number.  I am going to open it up, and find what company makes the video card it has, and then look for drivers.  Thanks!

---

### Post by jeffreyvergara.NET on 2005-10-26
now TC-Elite wont have a sound even i run as sudo, root, root+sudo 

> 
------- sound initialization -------
[B]/dev/dsp: Invalid argument
Could not open /dev/dsp[/B]
------------------------------------
Sound memory manager started
Sys_LoadDll(/root/.etwolf/tcetest/ui.mp.i386.so)...
Sys_LoadDll(/root/.etwolf/tcetest/ui.mp.i386.so) failed:
"/root/.etwolf/tcetest/ui.mp.i386.so: cannot open shared object file: No such fi le or directory"
Sys_LoadDll(/usr/local/games/enemy-territory/tcetest/ui.mp.i386.so)... ok
Sys_LoadDll(ui) found **vmMain** at  0xae685cc0
Sys_LoadDll(ui) succeeded!
WARNING: reused image ui/assets/fadebox.tga with mixed glWrapClampMode parm
Found high quality video and fast CPU
--- Common Initialization Complete ---


---

### Post by Elmorulz on 2005-10-26
[QUOTE=rimmer]To uninstall TC:E and ET all youv'e got to do is delete the files from the relevant directories.[/QUOTE]

But how do I know if I deleted all files???

---

### Post by jeffreyvergara.NET on 2005-10-28
open up terminal > sudo nautilus
then browse to > usr/local/games/enemy-teritory 
then execute "uninstall.sh" (double click the choose run)

the only thing It does not delete is the shortcut icons under Application>Other
so I open up Applications Menu Editor then uncheck ET and TC-Elite so it wont show up.

I have a sound issue in ET + TC-Elite, when I use the shortcut under Application > Other > TC-Elite, sound won't work, but when I add the shortcut to my desktop, the sound work... it's really weird.

---

### Post by GazaM on 2005-10-28
jeffreyvergara.NET: The reason for having no sound when you use the menu item is that when you click it a sound plays through esd... since ET uses OSS and esd blocks OSS from the sound device for a few seconds after playing that sound ET cannot use sound. Desktop icons do not make sounds when clicked, which is the reason for sound working in that case. (In my own experience)

---

### Post by jeffreyvergara.NET on 2005-10-29
Ah I see... so there's no fix for this?

---

### Post by GazaM on 2005-10-29
The only fix I know of is to turn of the 'Sounds for Events' option in System>Preferences>Sound but this will disable all of the usual sytem sounds like the sounds when you open a folder etc. Hopefully the next release will use ALSA directly for sound events, I have heard talk of this in the Gnome 2.14 thread in the Dapper Drake Development forum, at least I think that's where I heard it :P

---

### Post by jeffreyvergara.NET on 2005-10-29
that would be great news... I installed again TC:E I just made a shortcut on my desktop so everything is fine.. lol

---

### Post by iluciv on 2005-11-04
I've got the sound to work through the command in the root terminal (thanks heaps btw :)).
 But I can't seem to connect to any online servers. Have I missed something or am I supposed to oopen a port on my router that isn't currently open. 

When I click on a server to join the game doesn't download any updates it tries to but nothing is downloaded. 

Thanks in advance

---

### Post by jeffreyvergara.NET on 2005-11-08
[QUOTE=iluciv]I've got the sound to work through the command in the root terminal (thanks heaps btw :)).
 But I can't seem to connect to any online servers. Have I missed something or am I supposed to oopen a port on my router that isn't currently open. 

When I click on a server to join the game doesn't download any updates it tries to but nothing is downloaded. 

Thanks in advance[/QUOTE]

I used the HowTos in ubuntu's wiki site, just look for EnemyTerritory (sorry forgot the link, im too lazy to search.. ehheehe)

there's something there that i think "chown /.etwolf" i think.

---

### Post by mulperi on 2005-11-08
This is great game!!!

How can I get fullscreen?

---

### Post by jeffreyvergara.NET on 2005-11-08
mine is set to fullscreen by default.

alt+enter might work

---

### Post by iluciv on 2005-11-08
jeffreyvergara.NET: choice! thanks :) the command for anyone else is:
           sudo chown -R user:user ~/.etwolf/ 

Thanks heaps

---

### Post by windowmaker on 2005-12-16
i have recently install RTCW: ET, and i followed the guide at [http://ubuntuguide.org/#configuresoundproperly](http://ubuntuguide.org/#configuresoundproperly) and the sound worked perfectly, however when i turned my PC on this morning the sound for RTCW: ET had stopped working, and i am stumped on how to get it working again =(

---

### Post by Arktis on 2005-12-19
This game is pretty decent, especially for something that hasn't gotten out of beta yet.  It's got its pluses and minuses.  But overall I think it's more realistic than CS:S.

I like the way the targeting works, it makes it much much more realistic, but the player movement needs work.  Sniping is very difficult because it's hard to keep the scope steady and there is major recoil.  This is a very good thing IMHO.  It means sniping takes a lot more skill than in CS:S.  All in all a pretty good game.  I killed several hours on it directly after installing.

[quote=lbuntu_52]I think the game has to run in root I'm not sure tho anyways type[/quote]
Don't install this with sudo, people.  Just do it as a regular user and install it to somewhere in your home directory.  You don't need root to play TC:E.

Thanks for the infor about this great game.

---

### Post by soonindallas on 2006-02-09
so, if I interpret the answer rightly, you just delete the directory inwhich you placed the files, and all is well ?  it's like uninstalled ?

---

### Post by chattanoga on 2006-02-09
I downloaded and installed Enemy Territory as suggested by "Ibuntu 52", with
#sudo sh /home/yourusername/et-linux-2.60.x86.run


Without installing the true combat mod I started the game and to my amazement it looks (and sounds!) just super. Starting the game I was able to connect to a server and join a game as a spectator.

Since this is my first attempt on FPS gaming I have a couple of beginner questions:


Q1: What is a Mod?
Enemy Territory looks great by itself, does the "True combat mod" add functionallity or is it a whole new game?

Q2: What do I have to do to join a game?
I randomly entered a server in ET, but ended up as a spectator (which was quite entertaining in it self, but not what I was expecting).

Q3: Is there a single player mode? 
Since this is the first try at this kind of game I really need to get aquainted with the controls before starting. 

Q4: Can I play as an individual against all other players or do I have to join a team?

---

### Post by Harleen on 2006-02-09
1) A mod is an abbreviation for modification, which does - as the name says - modify a game. The amount of changes differs for the mods.
The True Combat Mod hasn't much in common with the original game. It changes graphics, sound, and drastically modifies gameplay. Treat it just like a complete different game, that for some reasons needs ET installed before.
I don't like ET much, but I do like the True Combart mod.

2) I haven't played that game for a while. Out of my memories you have to choose a side (Axis or Allie) and a role (soldier, medic, engineer). You will then be deployed after a short delay (about 10 seconds).

3) No, unfortunally not. It was planned, but wasn't finished. If it would have been finished, ID wouldn't have released that game for free. So there is at least one good thing on the missing single player mode.
But whithout practicing you will end as cannon fodder in your first games. I have never got out of this phase...
I also wouldn't recommend this game as the first 1st-person-shooter. It's too hard to stay alive even for mediocre players. But since it's free there's no risk in trying it out.
The TC mod isn't really easier, but it's slower and the enemies are easier to identify.

4) It's a team game only. If you just want to shoot anything that moves, you should rather try out Quake or Unreal Tournament, or if it has to be free Nexuiz.

---

### Post by chattanoga on 2006-02-10
Thanks.

I figured out how to join a game and ended up as cannon fodder directly (hope I did not spoil the game for the other players). :-)

As I understand it ET (and thus True Combat) is based on the Quake3 game engine?
Are there other free games "out there" using this engine?

---

### Post by handy on 2006-02-10
You should find plenty of interest on the following link:

[http://doc.gwos.org/index.php/Native_Games](http://doc.gwos.org/index.php/Native_Games)

:KS

---

### Post by crankcaller on 2006-02-10
>>I figured out how to join a game and ended up as cannon fodder

He-He.  Me too.  I even got booted from the server for killing my team mates...
Gonna install the TC mod tonight when i finish work.

My pal and i went onto an empty server and learned to control/shoot etc as I hadn't really played fps before.

*hmmm* i changed that last sentence from "learned to play with each other" ;)

---

### Post by drgeorgec on 2006-02-17
I have downloaded and installed the game according to the excellent Ibuntus_52 Guide. I have sound and everything, i can adjust my resolution to 1280x1024 fine but my problem is quite similar to yours. I connect to the servers and when it starts downloading the maps etc. (actually it does not download them its just connecting) i get an error: file.... etc. not found which i suppose are maps, models etc. Why it does not download theese files from the server like counter strike does? Has anybody else had this problem and if you know how to resolve it it will be much appreciated if you tell me too :)

---

### Post by drgeorgec on 2006-02-17
I found it! You have to verify that the directory that it downloads maps to is chmoded for access by your user! If you do not do this, you'll be unable to download and install the maps & other files you need to join games!
Type in the console:

sudo chown -R user:user ~/.etwolf/

and replace user:user with your ubuntu user name eg:  
sudo chown -R george ~/.etwolf/

or george:your user group if you have one.

A very good guide is here [https://wiki.ubuntu.com/EnemyTerritory](https://wiki.ubuntu.com/EnemyTerritory)

---

### Post by hans796 on 2006-04-18
Thanks for the autostart fix. Nice man!

---

### Post by Ob1 on 2006-04-18
Could someone post some screenshots of this mod?

---

### Post by lg3 on 2006-04-19
Help...I get this message when I try to install it using the terminal session:

Verifying archive integrity...Error in MD5 checksums: 5f710f3326e06461b7803717b7a6a163 is different from b8b59bc515d86cc845fb52f5d2c14423

---

### Post by Ob1 on 2006-04-19
Know of any other download server for Enemy territory? none of those mirrors worked.

---

### Post by aktiwers on 2006-04-20
I cant get the sound to work? Even though I open with sudo.
Not even when I use the code to get sound working.

Any ideas?

---

### Post by MLevin on 2006-07-13
Hello,

Have installed the TC:E on ubuntu, and found that it lags the response to the mouse movements :( Double-booted into XP, used the same config file and map and server, runs flawless!

In ubuntu, disabled OpenGL; helped just a bit, still lagging the move reaction, got killed everytime :)

Any known fixes for that? beside running in 320x200... :(

---

### Post by Polygon on 2006-07-13
here is a torrent for people who do not want to wait 5 hours for http to download it:

[http://bittorrent.com/detail.html?infohash=243223AE5A39909DB07A338980F00DD868251F05&per_page=10&search=linux&index=2](http://bittorrent.com/detail.html?infohash=243223AE5A39909DB07A338980F00DD868251F05&per_page=10&search=linux&index=2)

i would just download the patch from the site in the first post

---

### Post by tux-gamer on 2006-10-11
I Have problem with TC-E 0.49, i have this errror:
> ERROR: GRegisterPlayerClasses: failed to load character file 
 'characters/temperate/axis/soldier.char' for axis soldier
 when Host Game.

and How to change resolution ( option -> system), to "normal resolution", i don't like "letter box", "wide screen 6:9" and "wide screen 6:10"?

and can i use **Bot** like **Bobot** or **Omnibot** whith this TC-Elite, if can, how to do that?

I start the game whith this commandline:
$./et.x86 +set fs_game tcetest
I can play Et,and i have no sound problem too. 
(my soundcard nforce2 have hardware mixing)
My VGA is Geforce 6200 AGP8x 128MB using NVIDIA-8774 driver.

thanks before.

nb: sory for my bad english.

---

