---
title: "Trying to install UT:GOTY"
date: 2005-03-06
forum: Gaming &amp; Leisure
---

### Post by HungSquirrel on 2005-03-06
...and the installer version 436 crashes and burns.  Anyone know what this error means and how to get around it?

```
# ./ut-install-436.run
Verifying archive integrity...OK
Uncompressing Unreal Tournament version 436 Linux installtrap: usage: trap [-lp] [arg signal_spec ...]
```

---

### Post by mike998 on 2005-03-06
I have installed that myself - didn't get any errors and it works for me.
I got my version of the help from here
[http://www.princessleia.com/UT.html](http://www.princessleia.com/UT.html)
That's about all I can do to help

---

### Post by Ironi on 2005-03-06
Run it with the --keep option, which won't remove the /tmp/selfgz* dir after it's done (and also won't trigger that broken trap condition). You could also edit the file manually if you felt like it; it's just a "shell archive" with a shell script preceding a .tar.gz archive.

---

### Post by jdodson on 2005-03-06
ok i just successfully installed this on my ubuntu machine.  so basically follow the princess leia tut for debian here:

[http://www.princessleia.com/tools/ut/2.README.Debian](http://www.princessleia.com/tools/ut/2.README.Debian)

when it says apt-get install umodpack, skip that because that is not in ubuntu universe.

but you still need to convert the maps after you install the game.  by default they are in some weird windows format.  snag this script to convert all the maps for you:

```

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

``` 

run that as root or sudo and it will convert all your map files.  now finally i was getting an error because the game did not know where the game files were.  so what i did was create the following script to run the game:

```

#! /bin/sh

export UT_DATA_PATH=/usr/games/ut/System
ut
``` 

so basically it sets the path and then runs unreal goty.  

i will post more when i figure out howto install GOTY cd2 and maybe how to get the umodpack on ubuntu.

---

### Post by HungSquirrel on 2005-03-07
> **Ironi]Run it with the --keep option, which won't remove the /tmp/selfgz* dir after it's done (and also won't trigger that broken trap condition). You could also edit the file manually if you felt like it said:**
> 
 That did the trick to get the installer to run, but when I run the game, I get the following:

```
Unreal engine initialized
Bound to SDLDrv.so
Joystick [0] : Unknown Joystick
SDLClient initialized.
Bound to Render.so
Lighting subsystem initialized
Rendering initialized
LoadMap: Entry
Failed to load 'Entry': Can't find file 'Entry'
Failed to load 'Level None.MyLevel': Can't find file 'Entry'
appError called:
Failed to enter Entry: Can't find file 'Entry'
Executing UObject::StaticShutdownAfterError
Executing USDLClient::ShutdownAfterError
Signal: SIGIOT [iot trap]
Aborting.
Exiting.
Name subsystem shut down
```

And this is with my maps already in the correct *.unr format.


[quote]run that as root or sudo and it will convert all your map files. now finally i was getting an error because the game did not know where the game files were. so what i did was create the following script to run the game
I got the error you speak of.  There's a 'better' way to fix it, in that it will work for all users.  Under sudo, open the ut script (mine's /usr/bin/ut, yours may vary).  Comment out the following lines:

```
# Set the home if not already set.
#if [ "${UT_DATA_PATH}" = "" ]; then
#    UT_DATA_PATH="`FindPath $0`/System"
#fi
```
And add:
```
UT_DATA_PATH="/path/to/ut/System"
```

---

### Post by jdodson on 2005-03-07
start a google search with the error results, i found this:

[http://www.netsys.com/suse-linux-e/2001/05/msg02217.html](http://www.netsys.com/suse-linux-e/2001/05/msg02217.html)

---

### Post by linuxNewb on 2005-05-30
[QUOTE=mike998]I have installed that myself - didn't get any errors and it works for me.
I got my version of the help from here
[http://www.princessleia.com/UT.html](http://www.princessleia.com/UT.html)
That's about all I can do to help[/QUOTE]

During the install I keep getting a window telling me to mount CD 1, but it is mounted. What's wrong?

---

### Post by mike998 on 2005-05-30
Check that error message - It may be that the installer wants you to unmount CD1 and mount CD2.

---

### Post by Chaos5lw on 2005-06-23
[QUOTE=jdodson]```

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

```[/QUOTE]

mmm, that script nicely deleted all my .unr.uz maps and left me with two .unr maps... i take it that that isnt supposed to happen.

---

### Post by BLTicklemonster on 2006-01-05
Decompression: [http://nic-nac-project.de/~lowey/cgi-bin/igc.cgi?igc=31](http://nic-nac-project.de/~lowey/cgi-bin/igc.cgi?igc=31)

Thanks to {BL}Hawkwind for finding this nice little tool.

---

### Post by keggy on 2006-10-02
Hi I read this post only now and I can't find the installer at [http://www.princessleia.com/UT.html](http://www.princessleia.com/UT.html) how can I do? Can ypu give another URL to find it? :-k 

Bye

Francesco

---

### Post by BLTicklemonster on 2006-10-02
[http://ubuntuforums.org/showthread.php?t=74623](http://ubuntuforums.org/showthread.php?t=74623)

mind you that's for utgoty, if you just have ut, then get 

unreal.tournament_436-multilanguage.run

and to install it

sh unreal.tournament_436-multilanguage.run

then get over to 67.19.84.40 and say hi.

don't forget to 

> **BLTicklemonster said:**
> Here's how to make a cache cleaner for UT. It takes the files that you download from servers from a temporary folder ( /.loki/ut/Cache) and puts them in the proper places where they belong according to extension, i.e. .utx, .uax, etc.


Go to synaptic package manager, download gawk (just a thingy that is used by cache cleaner. I would tell you exactly what gawk is and what it does, but it's so freaking technical it would make your head explode gelatinous material about the place, rendering your keyboard useless for replying "OMGOMGOMG1337" to this thread when you're done).

Open text editor, and copy and paste the following in to it:

```
#!/bin/bash
cd ~/.loki/ut/Cache || exit 1 # change this to your UT user dir
if [ -f cache.ini ] ; then
{
export utdir="/home/[COLOR="Red"]bill[/COLOR]/ut/" # change this to your main UT folder
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

so you clean your cache folder!!!

Happy Fragging!

---

### Post by curly_nostrill on 2006-10-04
lol, @ ticklemonster...

and thanks

curly aka Poop_Finger

---

### Post by BLTicklemonster on 2006-10-05
Okay, kids, have you noticed that ut doesn't quite look the same in linux as it does in Windows? If so, here's a link that may interest you.

[http://forums.beyondunreal.com/showthread.php?t=161177](http://forums.beyondunreal.com/showthread.php?t=161177)

Go to your /home/yourname/ut/system folder and rename the file

OpenGLDrv.so to oldOpenGLDrv.so and then download the file from the link above, and put it in your ut/system folder. 

(SAVE A COPY OF YOUR UNREALTOURNAMENT.INI FILE SOMEWHERE SAFE!)
(you can get to it by going to your home directory, then press ctrl+h to unhide folders, then it's in the .loki folder, in the ut system folder)

In your unrealtournament.ini file, in the 

[Engine.Engine]

section, you'll want to replace each 

*.*RenderDevice ( I think it's SDL something by default )

with

OpenGLDrv.OpenGLRenderDevice

(I think there's three intances in there, and they are the first lines under engine.engine)

I copied and pasted G-Lite's settings, but his gamma was way out of whack on my system, so I changed the value

GammaOffset=0.500000

to

GammaOffset=0.100000

and it was fine.

Way more like what I was used to in windows, and pressing ~ and typing 

timedemo 1

showed me getting anywhere from  60 to 80+ fps, which is reasonable.

Hope this is helpful to all you hard core UT fanatics.

---

### Post by curly_nostrill on 2006-10-06
Thanks BLT! You're Da Bomb!

I just hope I can remember where to find this when/if ever I catch up to the bleeding edge tech of three years ago...:mrgreen:

btw... [this guys iso_mounter script ( http://rob.pectol.com/myscripts/ )]("http://rob.pectol.com/myscripts/") is also Da Bomb 2.  I just hope it works for installing UT from the mounted .nrg's I have.  I've just been using the same install folder across all my reinstalls of windows but it seems I have to start afresh now for Ubuntu/Linux...?

---

### Post by AJB2K3 on 2007-03-04
This will sound stupid but 
what do i save the script as?

---

### Post by BLTicklemonster on 2007-03-04
save it as .sh

like when you download it, I think you can be safe in just renaming it and drop the .txt at the end. Then run it as you normally would run an .sh file.

---

### Post by AJB2K3 on 2007-03-05
Im now getting the usuall whatnot iot error due to the un compressed files but i cant get eather of the scripts here to work.
The latest one (closest to this post )  crashes with this line
```
cd ~/.loki/ut/Cache || exit 1 # change this to your UT user dir
```
I dont have a cahe file anyware what do i do now?
Nevermind i just riped of my win install and used the data files from that.

---

### Post by BLTicklemonster on 2007-03-05
Congrats! Now come visit us at the Black Legion

8.6.74.123

and have some fun~!

---

### Post by AJB2K3 on 2007-03-06
> **BLTicklemonster said:**
> Congrats! Now come visit us at the Black Legion

8.6.74.123

and have some fun~!
HUH?
BTW how do i get the path to usr/local/games/ut/system in to the path tree?
Anyone unreal to work through ut yet?
Anyone got chaos ut to work?

---

### Post by AJB2K3 on 2007-03-07
> **BLTicklemonster said:**
> Congrats! Now come visit us at the Black Legion

8.6.74.123

and have some fun~!
Whats with all the bots?

---

### Post by BLTicklemonster on 2007-03-07
Something to keep people busy til someone shows up. Shouldn't be more than a few, though. Don't tell me there's 24 again!!!

---

### Post by AJB2K3 on 2007-03-08
> **BLTicklemonster said:**
> Something to keep people busy til someone shows up. Shouldn't be more than a few, though. Don't tell me there's 24 again!!!
no 10/20, 50 % of the plaer lsit.

---

### Post by BLTicklemonster on 2007-03-08
I'll drop that down tonight, not sure how it got that way.

---

### Post by AJB2K3 on 2007-03-08
When conneting with XP i get intro version mismatch but it worked fine on ubuntu.

---

### Post by rennen01 on 2007-03-08
UT: GOTY edition that came out around 2000? People still play that? I really don't like the new UTs these days.

---

### Post by AJB2K3 on 2007-03-09
> **rennen01 said:**
> UT: GOTY edition that came out around 2000? People still play that? I really don't like the new UTs these days.
yes and playing in on ubuntu wiyhout wine.
from what i se there are quite a few that dont like the new UT's

---

### Post by rennen01 on 2007-03-09
Did any of you guys ever play that Tactical Mod? It is called Tactical Ops.  Counterstrike gameplay that played on the UT Engine.

---

### Post by BLTicklemonster on 2007-03-09
Heck yes, people still play UT!!! People come and go when new games come around, but the newness of the new games wears off, and people keep coming back saying they don't know why they ever left. I don't like the new versions. None of them have the same level of raw intensity and "magical" game play that set UT apart from everything else. AND I don't like games that push you to have cutting edge equipment to play them. Companies these days seem to sell out to hardware manufacturers, and forget that a truly good game is what they should be making, not a truly beautiful bling bling infested monutment to rendering and shading. 2K4 has such high detail texturing that my limited vision loses players. I JUST CANT MAKE OUT THE WIDDLE BIDDY ENEMIES AGAINST ALL THE GARBAGE IN THE MAPS. 

So I stick with UT. Best game epic ever made, bar none.


Plus, we have talented scriptors working on some cool stuff at the BL. If you ever get a chance, come check out the Bat Wings, or if you are insane and want to try something totally absurd, check out the Zark Cow Weeee. It's the redeemer on lysurgic acid diethylamide or however you spell lsd. A rapid fire redeemer that has zoom, that fires nuclear nali war cows with flames coming out their bums. mooomooomooomooo. Senseless fun and hilarity. HINT: spawn with alt fire, not fire, or you fricase yourself.

We try to get in there around 9 to 10 est us, so maybe we'll see some of you Ubuntu folks? 

(and if you run into any problems, let me know. I still need to drop the bot count, btw)

---

### Post by rennen01 on 2007-03-09
Definitely gonna give this a shot.

BLTickemaster, the links in your sig are very helpful.

Thank you.

---

### Post by BLTicklemonster on 2007-03-09
> **rennen01 said:**
> Definitely gonna give this a shot.

BLTickemaster, the links in your sig are very helpful.

Thank you.

lmao, thanks. I was sitting staring at feisty wondering how to automount the partitions the other night... heh heh, now I remember... :blush:

---

### Post by AJB2K3 on 2007-03-10
whats 9-10 us in uk time?
Any experts know how to put Chaos ut in or how to get a model from blender into ut ?
Got a Seburo CX model dying to be used.

---

### Post by BLTicklemonster on 2007-03-10
Wow. I've never been able to do anything but distort a cube or sphere into some indistinguishable shape in any 3d editor (though I can make all kinds of stuff in unrealed... why can't they make 3d editors that are as simple as unrealed?), so I never tried the next logical step. Beyondunreal forums could be a place to seek help, and chimeric might have something. (google those words)

---

### Post by AJB2K3 on 2007-03-10
> **BLTicklemonster said:**
> Wow. I've never been able to do anything but distort a cube or sphere into some indistinguishable shape in any 3d editor (though I can make all kinds of stuff in unrealed... why can't they make 3d editors that are as simple as unrealed?), so I never tried the next logical step. Beyondunreal forums could be a place to seek help, and chimeric might have something. (google those words)
I know the two very well but haven't visited in 3 years, supprised they were still around.

GACK getting the sigserv sigmentation falt with ucc.

---

### Post by AJB2K3 on 2007-03-11
How do i launch it from the start menu?

---

### Post by BLTicklemonster on 2007-03-11
It depends on which installer you used, for one thing. Some put it in /home/you/ut, others put it elsewhere, but if you can find where it is, I'll try to remember where it is that you add stuff to start up. Otherwise you can right click on the desktop and create a launcher in the meantime.


I used ATI for a while, and it was just bothersome compared to nvidia is all.

---

### Post by AJB2K3 on 2007-03-11
Mine is installed to usr/local/games/ut with a link to usr/local/games/ut/System/ut-bin
now
```
usr/local/games/ut/System/ut-bin
```does nothing
```
./usr/local/games/ut/System/ut-bin
``` bring up unable to launch child process.
the only way i can run it is from the console cd ing to```
usr/local/games/ut/System/
```
then running ut-bin. nothing else works.

---

