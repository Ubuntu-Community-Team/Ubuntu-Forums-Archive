---
title: "Unreal Tournament Tips!"
date: 2005-10-27
forum: Gaming &amp; Leisure
---

### Post by NiceGuy on 2005-10-27
Hi all, well after a bit of messing around I've managed to get UT GOTY Edition up and running mainly by referring to this guide: [http://www.princessleia.com/UT.html]("http://www.princessleia.com/UT.html") 
and this post: [http://www.ubuntuforums.org/showthread.php?t=8053]("http://www.ubuntuforums.org/showthread.php?t=8053")

However I did run in to some problems, so I thought I'd post my fix's here and (hopefully) save you all some time and frustration!

So anyway, 

Step 1. Follow the guide: [http://www.princessleia.com/UT.html]("http://www.princessleia.com/UT.html") 

Step 2. You will need to extract the maps, but before you do - try typing ```
ut
``` into the terminal; if you get the error: ```
 dirname: too few arguments
Try `dirname --help' for more information.
Couldn't run Unreal Tournament (ut-bin). Is UT_DATA_PATH set?
``` Then we need to a little more 'setting up' (if not skip to Step 3). 

Type: ```
 sudo gedit /usr/bin/ut
``` in the terminal and then add the line ```
UT_DATA_PATH="/usr/games/ut/System"
``` into the file (I put it under the 'UT_PREFS=...' line) - *note* if your install directory is different, then enter that location instead! 

now in order to avoid [THIS]("http://www.ubuntuforums.org/showpost.php?p=226219&postcount=9") we will have to add the same line to the file ucc: ```
sudo gedit /usr/bin/ucc

``` and again add the line ```
UT_DATA_PATH="/usr/games/ut/System"
``` under the 'UT_PREFS=...' line.

Step 3. Make a new document in your home directory containing the following: ```
#!/bin/sh
# Change this to YOUR install-dir of UT
#
INSTALLDIR=/usr/games/ut

cd $INSTALLDIR/System

for i in `ls ../Maps/*.unr.uz`
	do
	ucc decompress ../Maps/$i -nohomedir
	done

rm ../Maps/*unr.uz
mv *.unr ../Maps

echo "..:: Done! ::.." 

``` make it executable and then 'sudo' run it from a terminal. If your maps get deleted copy them back to the maps directory (/usr/games/ut/maps) from the install CD's and read Step 2 above ;)

Step 4. Now try typing, ```
ut
``` into the terminal again - all being well you should be up and running! But don't stop reading just yet!!!

Step 5. So then, hows your sound? Can you hear the in game sounds? Yes? Good, now try running the game by going to Applications>Games>Unreal Tournament

*note* if the icon isn't there you may need to [ refresh the gnome panel]("http://ubuntuguide.org/#refreshgnomepanel")

Sound still working? If yes then good for you, if no read on...

First I recommend you follow the directions given here: [http://ubuntuguide.org/#configuresoundproperly]("http://ubuntuguide.org/#configuresoundproperly") 

The reason it doesn't work is because the Enlightened Sound Daemon is running, stopping the UT sound (I think that right, if not please feel free to correct :p ).

There are 2 ways to get around this; one you can do what the [guide]("http://ubuntuguide.org/#configuresoundproperly") says and disable the system sounds or if you like the 'clunks' when you start apps (as I do! :D ) you can do the following;

Open a terminal and type ```
sudo gedit /usr/bin/ut
```

and add the line ```
sleep 5
``` above the line which says '# The user preferences directory'

This will cause UT to wait 5 seconds before starting which should allow enough time for the Daemon to shut down. 

*note* if you followed the [guide]("http://ubuntuguide.org/#configuresoundproperly") then you can probably reduce this value from 5 to 2 seconds - play around and see what works!

Right well that's about it! Any problems, errors etc. feel free to post, sorry if its a bit long and disorganised but its been a long day - happy gaming!

---

### Post by wil on 2005-10-28
Also see [http://www.utpg.org/](http://www.utpg.org/) for some unofficial updates
[http://icculus.org/lgfaq/](http://icculus.org/lgfaq/) was also handy - just search for unreal
fixed my openGL problem which now works better than the SDLGL renderer

---

### Post by niels on 2005-11-24
I have followed all your steps till this one. In step one, when I tryed to install the umodpack, it wasn't there, but in another thread, I read, that I just had to convert the maps with the script in step 3.

> **NiceGuy]

Step 3. Make a new document in your home directory containing the following: ```
#!/bin/sh
# Change this to YOUR install-dir of UT
#
INSTALLDIR=/usr/games/ut

cd $INSTALLDIR/System

for i in `ls ../Maps/*.unr.uz`
	do
	ucc decompress ../Maps/$i -nohomedir
	done

rm ../Maps/*unr.uz
mv *.unr ../Maps

echo "..:: Done! ::.." 

``` make it executable and then 'sudo' run it from a terminal. If your maps get deleted copy them back to the maps directory (/usr/games/ut/maps) from the install CD's and read Step 2 above  said:**
> 

I have copyed the script to a file I called 'utconvert'. I didn't know how to run it, so I copyed it to/usr/bin. Then it was possible for me to run it, but I get this errormessages (I have only copyed the ending, caus it repeats the start a lot of times).
[QUOTE]
WARNING: Not using preference directory
MisingIni

History:

Exiting due to error
WARNING: Not using preference directory
MisingIni

History:

Exiting due to error
WARNING: Not using preference directory
MisingIni

History:

Exiting due to error
mv: kan ikke udføre stat() '*.unr': Ingen sådan fil eller filkatalog
..:: Done! ::..
niels@nielslaptop:~$


(some of the last part is danish, it says something like; mv: can't run stat() '*.unr': No such file or directory)

I have done step 2.

What's wrong???

Please anser me, I'm dying to play UT!

---

### Post by NiceGuy on 2005-11-24
Hurm... well, ok lets look at this bit by bit

the last bit (in danish?!?! - don't know why that is!?) is saying that there are no .unr files in the ut maps directory (normally /usr/games/ut/system). So the first thing I'd do is see what is in maps directory. 

If there is nothing in there then your going to have to copy the maps back again from the maps folder on your ut cd. 

As we seem to be having problems it might be worth deleting the line 

"rm ../Maps/*unr.uz"

from the utconvert script so you don't have to copy them back again.

On a side note in order to run the script utconvert, right click on it and go to properties>permissions and check the tick box which says "excute" on the owner line. Then open a console window and type: sudo and then litteraly drag the file from your desktop to the console window, then press enter to run it. 

Now as for the  "WARNING: Not using preference directory" bit - I wouldn't worry about that as I get that message too, the confusing bit is

"MisingIni

History:

Exiting due to error"

I guess its asking for a .ini file which is... well... missing - shame it doesn't say which one :P

try just typing ucc in to a console and seeing if it will run on its own and post back what it says.


oh and while your at it could you check that the files /.loki/ut/System/UnrealTournament.ini
/.loki/ut/System/User.ini
/.loki/ut/System/ChaosUT.ini

are in your home directory (you'll have to go to View>show hidden files to look at them) 
and the files
/usr/games/ut/System/UnrealTournament.ini
/usr/games/ut/System/UnrealTournament.ini.PATCH
/usr/games/ut/System/User.ini

are also present.

---

### Post by niels on 2005-11-24
Thanks.

I have copyed the maps from the cd's, deleted "rm ../Maps/*unr.uz" from the 'utconvert' script and ran it as you explained, but I still gets the same error (now it just don't delete the maps)?

[QUOTE=NiceGuy]
I guess its asking for a .ini file which is... well... missing - shame it doesn't say which one :P
[/QUOTE]
Please read on...

[QUOTE=NiceGuy]
try just typing ucc in to a console and seeing if it will run on its own and post back what it says.
[/QUOTE]

Done:
> 
niels@nielslaptop:~$ ucc
MisingIni

History:

Exiting due to error
niels@nielslaptop:~$


But when I try to run 'ut' nothing happens!?

[QUOTE=NiceGuy]
oh and while your at it could you check that the files /.loki/ut/System/UnrealTournament.ini
/.loki/ut/System/User.ini
/.loki/ut/System/ChaosUT.ini
[/QUOTE]
None of these files are there, only one called UnrealTurnament.log

[QUOTE=NiceGuy]
and the files
/usr/games/ut/System/UnrealTournament.ini
/usr/games/ut/System/UnrealTournament.ini.PATCH
/usr/games/ut/System/User.ini
[/QUOTE]
These files are present.

PS.
[QUOTE=NiceGuy]
(in danish?!?! - don't know why that is!?)
[/QUOTE]
I am danish!

---

### Post by NiceGuy on 2005-11-24
> I am danish!

Ah I see, that would explain it! LOL

But about the missing ini file...

Could you post the log file, you never know it might shead some light as to which ini file you are missing...

Oh and could you post the ucc.log file if you can find one - look in your home directory /.loki/ut/System/ucc.log and in the UT directory /usr/games/ut/system/ucc.log

PS. you said that you couldn't do "apt-get install umodpack". So I assume that you didn't try to install any mod packs form the UT website (I never did this either so it should work anyway). The reason I ask is that I have read that installing a dodgy mod pack can cause this error.

PPS. Have you tried reinstalling it? I can't imagine why, but maybe something went wrong the first time.

---

### Post by niels on 2005-11-25
[QUOTE=NiceGuy]
Could you post the log file, you never know it might shead some light as to which ini file you are missing...
[/QUOTE]
What log-file are you thinking of (the once below?)

[QUOTE=NiceGuy]
Oh and could you post the ucc.log file if you can find one - look in your home directory /.loki/ut/System/ucc.log and in the UT directory /usr/games/ut/system/ucc.log
[/QUOTE]
The /.loki/ut/System/UnrealTournament.log file is empty, but /.loki/ut/System/ucc.log says this:
> 
Log: Log file open, Thu Nov 24 22:47:39 2005
Init: Name subsystem initialized
Init: Version: 436
Init: Compiled: Oct 30 2000 11:53:24
Init: Command line: 
Init: Base directory: 
Init: Character set: ANSI
Critical: appError called:
Critical: MisingIni
Exit: Exiting.
Uninitialized: Name subsystem shut down
Uninitialized: Log file closed, Thu Nov 24 22:47:39 2005

/usr/games/ut/System/ucc.log says:
> 
Log: Log file open, Thu Nov 24 22:55:13 2005
Init: Name subsystem initialized
Init: Version: 436
Init: Compiled: Oct 30 2000 11:53:24
Init: Command line: ../Maps/../Maps/UTCredits.unr.uz -nohomedir
Init: Base directory: 
Init: Character set: ANSI
Critical: appError called:
Critical: MisingIni
Exit: Exiting.
Uninitialized: Name subsystem shut down
Uninitialized: Log file closed, Thu Nov 24 22:55:13 2005


[QUOTE=NiceGuy]
PS. you said that you couldn't do "apt-get install umodpack". So I assume that you didn't try to install any mod packs form the UT website (I never did this either so it should work anyway). The reason I ask is that I have read that installing a dodgy mod pack can cause this error.
[/QUOTE]
No, I havn't tryed to install any packeges from the website.
(I can't download Bonus Packs, it asks for my email and birthdate and then sends me to another page, where I can's find the Bonus Packs!?)

[QUOTE=NiceGuy]
PPS. Have you tried reinstalling it? I can't imagine why, but maybe something went wrong the first time.[/QUOTE]
Ok, i tryed this. First I cheked if I had chmod'ed the install script, and it seemed that I had forgotten this part. After chmod'ing, I ran the script again, and this time a graphical installer showed up!?!
I noticed, that I might have said no to both OpenGL and Glide for rendering (what's the difference?).
But I couldn't complet the installation. The 'Begin Install' is inactive with a 'No write permissions on the install directory' message!?

Thanks again for your fast help - this community rules! :D

---

### Post by NiceGuy on 2005-11-27
Sorry for the lateness of this reply (I've been busy this weekend).

So am I right in thinking that the first time you ran the script there was no graphical installer?!? If so that might explain where you went wrong...

I recommend you try installing it again (third time lucky). I've just installed it myself on a new machine and this is exactly what I did so 'hopefully' it should work for you! :D

1. Download the installer [http://www.princessleia.com/tools//ut/ut-install-436-GOTY.run]("http://www.princessleia.com/tools//ut/ut-install-436-GOTY.run") and place it in your 'home' directory.

2. Open a console window and type```
xhost +
``` you'll get a message which says: ```
access control disabled, clients can connect from any host
```

3. Next type ```
sudo su
``` and enter your password. This will make you 'root'

4. Then type ```
export DISPLAY=:0.0
```

5. Then type ```
chmod 755 ut-install-436-GOTY.run
```

6. Finally type ```
bash ut-install-436-GOTY.run
``` which should launch the graphical installer.

7.
The install path should be /usr/games/ut
The link path should be /usr/bin
The option 'Binary Files' should be selected and the default renderer should be OpenGL
The option 'Data Files' should be selected
The option 'Desktop menu items' should be selected

Click 'Begin Install'

8. Half way through the installation it will as you for the second disk and if you only have one cdrom (like I do) then you will have to eject the first cd. To do this you may need to right click on the cd icon on your desktop and click 'eject' 

9. When the installation is finished, just click exit. Then in the console type ```
exit
``` and then follow the instructions from my first post (step 2 onwards).

Hope this works for you - let me know how you get on!

---

### Post by niels on 2005-11-27
> **NiceGuy]Sorry for the lateness of this reply (I've been busy this weekend).
[/QUOTE]
Me too, so there is no problem  said:**
> 
6. Finally type ```
bash ut-install-436-GOTY.run
``` which should launch the graphical installer.

This time it launches the graphical installer, but it says that i have 'No write permission on the install directory', and the 'Begin Install' is inactive!?!
Do I have to delete what it installed the first time? If so, what exactly should I delete (/usr/games/ut/*, /usr/bin/ut, /usr/bin/ccu, /home/niels/.loki/ut/*?)

Thanks for your help again!

---

### Post by NiceGuy on 2005-11-27
Well to be on the safe side I'd delete the /usr/games/ut directory.

As for the 'No write permission on the install directory' bit... hurm...

are you sure your running the install script as root, ie. by typing ```
sudo su
``` and then typing ```
bash ut-install-436-GOTY.run
```

---

### Post by niels on 2005-11-27
OK, now the installation was a success. Everything went smooth! I think the problem was, that I forgot a different thing each time. Sorry...

But now I have a new problem. When I run ut, I get the following error:
> 
...
Input system initialized for SDLViewport0
Opening SDL viewport.
Bound to GlideDrv.so
Loaded render device class.
Initializing Glide...
Found Glide: 2.60.00.0415
gd error (glide): Can't find or access Banshee/V3 board
grSstQueryHardware failed
No localization: SDLDrv.Errors.Failed3D (int)
<?int?SDLDrv.Errors.Failed3D?>
Signal: SIGSEGV [segmentation fault]
Aborting.
Exiting.
Name subsystem shut down
Allocation checking disabled
Lagersegmentfejl
niels@nielslaptop:~$

(The second last line is danish and says something like 'Storringerror')

I know that I don't have a 3D graphic-card, but at [the official UT site]("http://unrealtournament.com/utgoty/specs.php") it says, that it's not a must.

Is there any way I can make it work???

---

### Post by NiceGuy on 2005-11-27
Thou shall play UT yet! (I hope!)

That error message is telling you that you are trying to play unreal Tournament using the Glide renderer - but don't have a graphics card which supports it.

Now you say you don't have a 3D card so hardware rendering isn't an option so we are going to have to tell it to use 'software rendering'.

There are two files we are going to need to edit (one if you are the only user on the pc)

1. Open a console window and type:
```
 gedit .loki/ut/System/UnrealTournament.ini
```

2. Scroll down the file until we come to a bit which says [Engine.Engine]. The next three lines are the one we will be considering. At the moment they should say:
```

[Engine.Engine]
GameRenderDevice=GlideDrv.GlideRenderDevice
WindowedRenderDevice=GlideDrv.GlideRenderDevice
RenderDevice=GlideDrv.GlideRenderDevice

```
which is telling UT to use Glide rendering

3. Because we are wanting to use software rendering we are going to have to  replace these lines with the following:
```

[Engine.Engine]
GameRenderDevice=SDLSoftDrv.SDLSoftwareRenderDevice
WindowedRenderDevice=SDLSoftDrv.SDLSoftwareRenderDevice
RenderDevice=SDLSoftDrv.SDLSoftwareRenderDevice

```
Now you want to save the file and exit, then type UT into a console window and cross your fingers!


Now, if in the future you get a 3d graphics card and you want to use hardware rendering then either use the following if you want to use Glide rendering (which I think is mainly for 3Dfx cards - 3dfx Banshee etc):
```

[Engine.Engine]
GameRenderDevice=GlideDrv.GlideRenderDevice
WindowedRenderDevice=GlideDrv.GlideRenderDevice
RenderDevice=GlideDrv.GlideRenderDevice

```
or use
```

[Engine.Engine]
GameRenderDevice=SDLGLDrv.SDLGLRenderDevice
WindowedRenderDevice=SDLGLDrv.SDLGLRenderDevice
RenderDevice=SDLGLDrv.SDLGLRenderDevice

```
to use OpenGL rendering.



Hopefully UT is working now [-o< and if you are the only user on your PC we can stop there, if not you are going to need to do the same thing to the file located in the installation folder.

Open up a console and type:

```
sudo gedit /usr/games/ut/System/UnrealTournament.ini
```

and edit that file in the same way.


NB. Just to give credit where credit is due all that info was shamelessly lifted from [http://osgaming.net/Downloads/Linux/Installers/README-GOTY]("http://osgaming.net/Downloads/Linux/Installers/README-GOTY")

---

### Post by niels on 2005-11-28
YES! It worked!!! Thanks a LOT! Now I know wat to do all night long - my girlfriend is gonna hate you ;)

I'm really greatfull! Thank's NiceGuy!

---

### Post by NiceGuy on 2005-11-28
Glad to help! 

(and to niels girlfriend - "sorry :oops: please don't be mad [-o< )

---

### Post by Sp@z on 2005-12-22
HI  well I installed UT99 today and when I did, I installed it to /home/bill/ut folder. Problem is I cannot delete it because I don't have write permissions to my home folder? I installed it as root as per these directions.....[http://www.princessleia.com/UT.php](http://www.princessleia.com/UT.php)

The reason I want to delete it is because following this thread............[http://www.ubuntuforums.org/showthre...eal+Tournament](http://www.ubuntuforums.org/showthre...eal+Tournament)
says I have to make the changes to the UT data path, which I cannot do. Because I get blank gedits when trying the path noted or changing the path to /home/bill/ut and trying to edit said file. I just assume install it to the directory in the howto for sake of ease. I am open to fixing the install I currently have but not sure how. I tried I failed. I just don't want two installs on my system and reinstalling it also leaves me with only the option to install it in /home/bill/ut ....not /usr/bin ut (Default location I believe).

However........if I double click the sh ut file within the folder and click run the game loads and I can play it. If I move it or create a launcher, it is a NO GO...Any help here? Thanx in advance!




PS I prefer it in my Home folder with write permissions since I can easliy modify those files within..........but I want it to run correctly.

I posted this in another thread and since the post I am no longer able to click on the sh ut file, it doesn't run anymore. I would be HAPPY just to learn to remove or uninstall this and start over, but when I run sh uninstall I get a "Componant not found issue" 

Thanks!



Edit..I got it all fixed now. :)

---

### Post by JonGibbins on 2005-12-26
Hi there, Mr NiceGuy!
Thanks for such a good guide.... HOWEVER! ;)

When I'm running the installer ut-install-436-GOTY.run , When told to insert the UT CD, the installer is looking at my floppy drive instead of looking at the CD drive! I have no idea quite why it's doing this, all my usual CD and FDD access is fine.
Any idea how to give the installer a slap and point it to my CD drive?

---

### Post by BLTicklemonster on 2005-12-26
I don't see why you are all having so many problems, have you tried this: [http://ubuntuforums.org/showthread.php?t=74623](http://ubuntuforums.org/showthread.php?t=74623) ?

It works flawlessly for me. There's also how to make a cache cleaner on that, too.

---

### Post by Sp@z on 2005-12-26
[QUOTE=BLTicklemonster]I don't see why you are all having so many problems[/QUOTE]
Thanks for the link, I am sure it will be useful for other ppl as well. Although I got UT to run, working through a terminal window is so ALIEN and FORIEGN to me, it actually INTIMIDATED me, I am sure that is why I had a problem. I can't speak for others but please remember you were n00b at linux one day too. I appreciate all the help I can get but I read your post as you being frustrated, I certtainly don't want to contribute to someones frustration, but if we need help I thought this was the place to go?

Edit is this the same ticklemonster from Unreal Admins page? I bet you are! YOu helped me ALOT over there too KUDOS to you!!!!!

---

### Post by BLTicklemonster on 2005-12-26
Sorry, that didn't come out right. What I should have said was that it is far easier to install UT than what is being done, and to try the way shown in the link.

I didn't think before I posted that. I will try every way I know to help someone, and am totally embarassed that I posted that without thinking about it beforehand.

---

### Post by joelito on 2005-12-28
Hello everyone

OK the info looks usefull but my problem is slightly diferent(Posting here for not creating a new topic)

The thing is that I downloaded the Linux demo version wich only supports 3dfx and I'm using a Radeon. I need to know where to Download the files I need to enable SDLGLDrv

---

### Post by BLTicklemonster on 2005-12-29
Here's a reply that I got on unrealadmins.org when I asked about ogl renderers:

> **Rush]Hmm, not really, but according to the author of UTGLR it might be possible to compile most of its code on Linux however it would be quite tricky and nobody has even tried ... and I'm not gonna try it either, it would require installing GCC 2.9 which is quite an antiq. 

However, there are two things which you can improve, as you probably noticed UT is using SDL for all the input stuff and also there's an SDL renderer, you can make UT use a newer SDL than the standard one distributed with UT, just look at my libSDL in UT/System:
```

unimatrix System # ls -al /opt/unreal-tournament/System/libSDL*
lrwxr-xr-x  1 root root 24 Nov  6 13:59 /opt/unreal-tournament/System/libSDL-1.1.so.0 -> /usr/lib/libSDL-1.2.so.0

```
Do you catch it ? You can just delete the old libSDL-1.1.so.0 and make symbolic link or just copy a recent version to match the old name, it works :P

Second, edit you ~/.loki/ut/System/UnrealTournament.ini and look for [SDLGLDrv.SDLGLRenderDevice], there's an OpenGLLibName setting, you can point it to the recent Nvidia's OpenGL lib, like I have:
```

[SDLGLDrv.SDLGLRenderDevice]
....
OpenGLLibName=/usr/lib/libGL.so

```


OpenGL works much better on Linux than on Windows :P[/QUOTE]
(I have no idea what any of that means, so be careful if you attempt it)


And here's a link I got from Skullkrusher that has a new ogl so file, and ini settings: [http://forums.beyondunreal.com/showthread.php?t=161177](http://forums.beyondunreal.com/showthread.php?t=161177)

In case you missed it, here's how to make a cache cleaner for UT:

[QUOTE={BL}Ticklemonster]Assuming you used one of these [http://www.liflg.org/?catid=6&gameid=51](http://www.liflg.org/?catid=6&gameid=51) to install ut in ubuntu....

Here's how to make a cache cleaner for UT. It takes the files that you download from servers from a temporary folder ( /.loki/ut/Cache) and puts them in the proper places where they belong according to extension, i.e. .utx, .uax, etc.


Go to synaptic package manager, download gawk (just a thingy that is used by cache cleaner. I would tell you exactly what gawk is and what it does, but it's so freaking technical it would make your head explode gelatinous material about the place, rendering your keyboard useless for replying "OMGOMGOMG1337" to this thread when you're done).

Open text editor, and copy and paste the following in to it:

```
#!/bin/bash
cd ~/.loki/ut/Cache || exit 1 # change this to your UT user dir
if [ -f cache.ini ]  said:**
> bill[/COLOR]/ut/" # change this to your main UT folder
gawk -F= ' 
utdir = "${utdir}"
function moveit(targ)
{
print "mv -v "$1".uxx" " " utdir targ substr($2, 1, length($2)-1) | "sh";
}
{
if(match($2,".unr")) moveit("Maps/");
else if(match($2,".utx")) moveit("Textures/");
else if(match($2,".uax")) moveit("Sounds/");
else if(match($2,".umx")) moveit("Music/");
else if(match($2,".u")) moveit("System/");
}
END { close("sh") }' cache.ini
rm *.uxx cache.ini
}
fi;
if [ -f $utdir"System/De.u" ]; then rm $utdir"System/De.u" ;fi  
if [ -f $utdir"System/de.u" ]; then rm $utdir"System/de.u" ;fi
# end script
```

Notice this: /home/[COLOR="Red"]bill[/COLOR]/ut/ . Change according to your personal set up.

Save in /home/you/ as utcleaner. Notice all the pretty colors that the text changed to? This means something important, but I am a total noob, so it's above my pay grade, therefore there's no telling what it means.

Open terminal, and type this:

```
chmod +x utcleaner
```

The file utcleaner is now executable.

To run it, from terminal, type

```
./utcleaner
```

Now to make things cooler, how about a desktop launcher?

Right click on the desktop, click create launcher, name it UTCleaner, go down to where it says command: and put ./utcleaner and check where it says run in terminal (I tried it without running in terminal, and for some reason all it does is delete uxx files, so click on run in terminal for sure). If you want an icon, go ahead and use one. [You can create custom icons, too, if you want to.](http://www.ubuntuforums.org/showthread.php?t=92393). Click OK. 

Now you can double click and clean all your .uxx files. 

Nifty, huh?

THANKS TO ~V~ AT UNREALADMINS.ORG (Who's motto is "There's no place like 127.0.0.1" ) FOR THIS.


I think that covers the basics.

---

### Post by BLTicklemonster on 2005-12-29
Here's a reply that I got on unrealadmins.org when I asked about ogl renderers:

> **Rush]Hmm, not really, but according to the author of UTGLR it might be possible to compile most of its code on Linux however it would be quite tricky and nobody has even tried ... and I'm not gonna try it either, it would require installing GCC 2.9 which is quite an antiq. 

However, there are two things which you can improve, as you probably noticed UT is using SDL for all the input stuff and also there's an SDL renderer, you can make UT use a newer SDL than the standard one distributed with UT, just look at my libSDL in UT/System:
```

unimatrix System # ls -al /opt/unreal-tournament/System/libSDL*
lrwxr-xr-x  1 root root 24 Nov  6 13:59 /opt/unreal-tournament/System/libSDL-1.1.so.0 -> /usr/lib/libSDL-1.2.so.0

```
Do you catch it ? You can just delete the old libSDL-1.1.so.0 and make symbolic link or just copy a recent version to match the old name, it works :P

Second, edit you ~/.loki/ut/System/UnrealTournament.ini and look for [SDLGLDrv.SDLGLRenderDevice], there's an OpenGLLibName setting, you can point it to the recent Nvidia's OpenGL lib, like I have:
```

[SDLGLDrv.SDLGLRenderDevice]
....
OpenGLLibName=/usr/lib/libGL.so

```


OpenGL works much better on Linux than on Windows :P[/QUOTE]
(I have no idea what any of that means, so be careful if you attempt it)


And here's a link I got from Skullkrusher that has a new ogl so file, and ini settings. It's what I'm using now, and at least the colors are a lot better: [http://forums.beyondunreal.com/showthread.php?t=161177](http://forums.beyondunreal.com/showthread.php?t=161177)

In case you missed it, here's how to make a cache cleaner for UT:

[QUOTE={BL}Ticklemonster]Assuming you used one of these [http://www.liflg.org/?catid=6&gameid=51](http://www.liflg.org/?catid=6&gameid=51) to install ut in ubuntu....

Here's how to make a cache cleaner for UT. It takes the files that you download from servers from a temporary folder ( /.loki/ut/Cache) and puts them in the proper places where they belong according to extension, i.e. .utx, .uax, etc.


Go to synaptic package manager, download gawk (just a thingy that is used by cache cleaner. I would tell you exactly what gawk is and what it does, but it's so freaking technical it would make your head explode gelatinous material about the place, rendering your keyboard useless for replying "OMGOMGOMG1337" to this thread when you're done).

Open text editor, and copy and paste the following in to it:

```
#!/bin/bash
cd ~/.loki/ut/Cache || exit 1 # change this to your UT user dir
if [ -f cache.ini ]  said:**
> bill[/COLOR]/ut/" # change this to your main UT folder
gawk -F= ' 
utdir = "${utdir}"
function moveit(targ)
{
print "mv -v "$1".uxx" " " utdir targ substr($2, 1, length($2)-1) | "sh";
}
{
if(match($2,".unr")) moveit("Maps/");
else if(match($2,".utx")) moveit("Textures/");
else if(match($2,".uax")) moveit("Sounds/");
else if(match($2,".umx")) moveit("Music/");
else if(match($2,".u")) moveit("System/");
}
END { close("sh") }' cache.ini
rm *.uxx cache.ini
}
fi;
if [ -f $utdir"System/De.u" ]; then rm $utdir"System/De.u" ;fi  
if [ -f $utdir"System/de.u" ]; then rm $utdir"System/de.u" ;fi
# end script
```

Notice this: /home/[COLOR="Red"]bill[/COLOR]/ut/ . Change according to your personal set up.

Save in /home/you/ as utcleaner. Notice all the pretty colors that the text changed to? This means something important, but I am a total noob, so it's above my pay grade, therefore there's no telling what it means.

Open terminal, and type this:

```
chmod +x utcleaner
```

The file utcleaner is now executable.

To run it, from terminal, type

```
./utcleaner
```

Now to make things cooler, how about a desktop launcher?

Right click on the desktop, click create launcher, name it UTCleaner, go down to where it says command: and put ./utcleaner and check where it says run in terminal (I tried it without running in terminal, and for some reason all it does is delete uxx files, so click on run in terminal for sure). If you want an icon, go ahead and use one. [You can create custom icons, too, if you want to.](http://www.ubuntuforums.org/showthread.php?t=92393). Click OK. 

Now you can double click and clean all your .uxx files. 

Nifty, huh?

THANKS TO ~V~ AT UNREALADMINS.ORG (Who's motto is "There's no place like 127.0.0.1" ) FOR THIS.


I think that covers the basics.

---

### Post by BLTicklemonster on 2006-11-05
Eeek double post up there.

here's a umod extractor if anyone wants it.

[http://ut.abfackeln.com/asu.html?page=install](http://ut.abfackeln.com/asu.html?page=install)

---

### Post by weise on 2007-01-25
Hi,

I installed Ubuntu 6.10 x86_64.

I installed ia32-libs, ia32-libs-gtk, ia32-libs-openoffice.org, ia32-libs-sdl, ia32-sun-java5-bin, lib32asound2, lib32gcc1 , lib32ncurses5, lib32stdc++6, lib32z1.

I installed UT99 with sucess.

When I run ut, I get the following error:

> 
jurandy@weise:/usr/local/games/ut/System$ linux32 ./ut
Unreal engine initialized
Bound to SDLDrv.so
Joystick [0] : Unknown Joystick
SDLClient initialized.
Bound to Render.so
Lighting subsystem initialized
Rendering initialized
LoadMap: Entry
Bound to Fire.so
Case-insensitive search: Botpack -> ..\System\BotPack.u
Bound to IpDrv.so
appError called:
Class Actor Member Owner problem: Script=48 C++=52
Executing UObject::StaticShutdownAfterError
Executing USDLClient::ShutdownAfterError
Signal: SIGIOT [iot trap]
Aborting.
Exiting.
Name subsystem shut down


Is there any way I can make it work???

Weise

---

### Post by weise on 2007-01-26
I resolved the problem.

The [www.liflg.org](www.liflg.org) create a new ut99 installer with 64bit support.

I downloaded [http://www.liflg.org/?what=dl&catid=6&gameid=51&filename=unreal.tournament_436-multilanguage.run]("http://www.liflg.org/?what=dl&catid=6&gameid=51&filename=unreal.tournament_436-multilanguage.run")
and installed ut99.

When I ran the game I got the following error:

> "/usr/local/bin/ut: 29: Syntax error: Bad substitution"

I applied this patch:

> --- ut.tmp      2007-01-26 11:28:00.000000000 -0200
+++ ut  2007-01-26 11:54:57.000000000 -0200
@@ -26,7 +26,7 @@
     
     if [ -L "$path" ]; then
         ll="$(LC_ALL=C ls -l "$path" 2> /dev/null)" &&
-       echo "${ll/* -> }"
+       echo "$ll" | sed -e "s/.* -> //" | sed -e "s/\*//"
     else
        return 1
     fi


And the game ran with sucess.

Weise

---

### Post by BLTicklemonster on 2007-01-26
EXCELLENT! Thanks for posting back with the fix.

Now come visit us sometime!!!

Tell them the Ticklemonster sent you, lol.

8.6.74.123

Best time to catch us is Wed about 10 PM eastern time, though we do have people in there around that time a lot of times during the week.

---

### Post by gummo on 2007-05-11
I just followed this guide and the game runs like a charm now, thanx alot man.

---

### Post by BLTicklemonster on 2007-05-12
Good thing! Glad it works.


Hey everyone, if you ever played ut2k4 and didn't like the vehicles, perhaps you'll like what we have over at the Black Legion. 

Come play, and look in our mapvote for maps with the word 

manta

in them. 

The vehicles are more fun than 2k4 vehicles, and are much more intuitive. Beta versions, still a bug or two, but they are the first of their kind to be used in UT. 

Press fire to get in one, press alt fire to fly of "hop" then, and to leave, press crouch.

for a different type of fun, try the bat wings mod that you see in the mutator section of the mapvote.

Either way, it's stuff you don't normally see elsewhere.

and if you like them, come by and say hello at [www.theblacklegion.clanservers.com/index.php](www.theblacklegion.clanservers.com/index.php)

and yes, the vehicles are based on work initiatied by HenryHouse back a few years ago. We have BlackCheetah to thank for the replication work done on these. (15 year old kid over in the UK)

Come frag with us!!!


(the server ip address is in a post above here, btw)

---

### Post by dshuck on 2007-07-20
> **weise said:**
> I resolved the problem.

The [www.liflg.org](www.liflg.org) create a new ut99 installer with 64bit support.

I downloaded [http://www.liflg.org/?what=dl&catid=6&gameid=51&filename=unreal.tournament_436-multilanguage.run]("http://www.liflg.org/?what=dl&catid=6&gameid=51&filename=unreal.tournament_436-multilanguage.run")
and installed ut99.

When I ran the game I got the following error:



I applied this patch:



And the game ran with sucess.

Weise


I realize this was a long time ago that you did this, but do you remember what you did to apply this patch?  It seems like that block would replace the code in the "ut" file around Line 29, where your (and my!) error occurred.   I did so, but am still getting the same error.  Any idea?

---

### Post by Shpongled303 on 2007-07-21
> **weise said:**
> I resolved the problem.

When I ran the game I got the following error:

I applied this patch:

And the game ran with sucess.

Weise

I also get the error:
ut: 29: Syntax error: Bad substitution

Where and how did you apply that handy patch that you have?

---

### Post by BLTicklemonster on 2007-07-21
In terminal:

sudo gedit /usr/local/bin/ut

enter your password.

Now immediately save this file as oldut.

Then find this:

```
###############################################################################
## DO NOT EDIT BELOW THIS LINE
###############################################################################
readlink() {
    local path=$1 ll
    
    if [ -L "$path" ]; then
        ll="$(LC_ALL=C ls -l "$path" 2> /dev/null)" &&
	echo "${ll/* -> }"
    else
	return 1
    fi
}
```

and replace it with

```
###############################################################################
## DO NOT EDIT BELOW THIS LINE
###############################################################################
readlink() {
    local path=$1 ll
    

if [ -L "$path" ]; then
ll="$(LC_ALL=C ls -l "$path" 2> /dev/null)" &&
- echo "${ll/* -> }"
+ echo "$ll" | sed -e "s/.* -> //" | sed -e "s/\*//"
else
return 1
fi
}
```

and now save as ut (MAKE SURE YOU DON'T SAVE IT AS OLDUT)

and see if that does the trick.

If not, then go back and 

sudo gedit /usr/local/bin/oldut

and save as ut, then wait for an answer, lol. Sorry, but that's the best help I can give.

(yeah, I know, this isn't the proscribed way to back up files, but I find it easier by far to do this this way instead of the other way)

---

### Post by BLTicklemonster on 2007-07-21
?? who the heck was leo0o_m3ssi ?

---

### Post by Shpongled303 on 2007-07-22
Hey BLTicklemonster,

Appreciate the help, but we ended up finding a solution from a different forum -- the Loki Installers forum.

The problem was:

Ubuntu uses "dash" as the default shell instead of "bash."
So we just opened the "ut" script in the installed Unreal Tournament directory,
and changed "#!/bin/sh" to "#1/bin/bash"

Then it worked. :) Runs great! :KS

---

### Post by BLTicklemonster on 2007-07-22
Same as this?

[http://ubuntuforums.org/showpost.php?p=1780929&postcount=9](http://ubuntuforums.org/showpost.php?p=1780929&postcount=9)

Glad you got it going. I forgot all about that.

---

### Post by hikaricore on 2007-07-22
> **BLTicklemonster said:**
> ?? who the heck was leo0o_m3ssi ?

A spammer.  The matter has been dealt with.  :guitar:

---

### Post by BLTicklemonster on 2007-07-22
:) We have image verification on our server, yet we constantly have new spammers trying to join. They can't get in until one of us admins allow them. Most are obvious by their emal address or name (just had OFFLEASE-RU and VIAGRA ONLINE try to join), and I just ban them right off the bat.

Gets tiring after a while. I think I need to see about getting the two dudes who do the php to find a better image verification system if these bots can get around them.

---

### Post by blackswamper on 2008-08-26
I've come across this issue twice now. (on two completely different installs in a row)
When I install and run UT (and I don't run into any issues) I can play for a couple minutes...
then my controls start "sticking". Randomly as I move in directions my controls will get stuck. I will have to hold "S" to stand still instead of not pressing a button to move forward (which isn't what I have it bound to anyway), things like that, I can't wait for it to get stuck switching weapons with a full load out, but that's just silly.
Yeah, what's up with that? Any ideas?

---

### Post by wmatthews on 2009-03-26
Great tutorial worked perfectly.  I haven't played this game in years. :guitar:

---

