---
title: "How To: play Unreal Tournament GOTY in Edgy"
date: 2006-10-31
forum: Gaming &amp; Leisure
---

### Post by BLTicklemonster on 2006-10-31
Okay, things appear to have changed a bit in edgy, or the loki installer has changed, one or the other. (This works in Gutsy, too. I have no idea about Hardy, because it's unstabler than a 19 year old Alabama 3rd grader in a dui tank)

So if you are like me, and think Unreal Tournament is the best game ever made, and have to have it playable on any machine, and freaked when you tried it in Edgy, here's how you do it.


Well, first off, make sure it's installed:

Get this download: [http://www.liflg.org/?catid=6&gameid=51](http://www.liflg.org/?catid=6&gameid=51) (actually, chose which one, depending on if you have ut or utgoty) I put it in my /home/myname/ to run it. Go ahead and put cd one in right now so it will be mounted. 

If you put the file anywhere other than /home/yourname/, the open terminal, and cd /tothedirectoryouputitin. (good practice: always put stuff in /home/you/ when you have to install them. delete them later. Terminal defaults to that directory, so it's easier that way)

Type 
```

sh unreal.tournament_436-multilanguage.goty.run 
```

and then install ut. 


Now you will notice, once all is done, that 

```
cd /home/myfolder/ut
```
then
```
ut
```

won't work.

Thanks to DarkSim, we have a neat solution to this.

From the terminal, type

```
cd /home/yourname/ut
```

then

```
gedit playut
```
press enter

paste this into it, and save:

```
#!/bin/sh

cd /home/bill/ut

bash ut
```

now close gedit, and in the terminal, type:

```
chmod 755 playut
```

Now you can use that file to launch ut.

Click on your launch bar on your desktop, and create a link to it (there's a ut icon in ~/ut to use).

Here's how to make a ut cleaner:

Open text editor, and copy and paste the following in to it:

```
#!/bin/bash
cd ~/Cache || exit 1 # change this to your UT user dir
if [ -f cache.ini ] ; then
{
export utdir="/home/[COLOR="Red"]bill[/COLOR]/.loki/" # change this to your main UT folder
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

Notice this: /home/[COLOR="Red"]bill[/COLOR]/.loki/ . Change according to your personal set up.

Save in /home/you/ as utcleaner. Notice all the pretty colors that the text changed to? This means something important, but I am a total noob, so it's above my pay grade, therefore there's no telling what it means.

Open terminal, and type this:

```
chmod +x utcleaner
```

(or chmod 755 utcleaner if +x doesn't work for you)

The file utcleaner is now executable.

To run it, from terminal, type

```
./utcleaner
```

Better yet, put that baby in your ~/ut folder, then create a launcher for it.

Thanks to tjotser for telling me about ut-bin.

anyone know how to make a launcher for this, please share...


Edit:

a recap, install it all, put the utcleaner file in /home/yourname/ut then to play, just 

cd /home/yourname/ut
bash ut

once the game's over, then

./utcleaner

and your cache is moved.

anybody figure out how to make a launcher for this that works?

---

### Post by BLTicklemonster on 2006-11-05
And if you want to install umods, use this program: [http://ut.abfackeln.com/asu.html?page=install](http://ut.abfackeln.com/asu.html?page=install)

---

### Post by Fsngruv on 2006-11-09
will this work for dapper too

---

### Post by BLTicklemonster on 2006-11-09
Yeah, sorry, it works in Breezy, also, come to think of it. 

Hey, I noticed you were having problems, I guess you got it working?

If you did and want to check out some really insane stuff, come to our server at 67.19.84.40 some time. We have a lot of different mods on there. Map vote shows them in the center of the window. Choose the ZarkArms/BatWings on a large out door map if you want to see something that will blow you away. To fly, just jump, and press crouch (for an added boost, doubletap, then press crouch).

If you see me in there holler!

---

### Post by Fsngruv on 2006-11-16
yeah, i got it working but when I installed the glx-compiz and updated to the 686 kernel is started crashing on me and when I tried to reinstall it won't do it anymore, but when I get it going, i'll swing by your server and check it out

---

### Post by BLTicklemonster on 2006-11-18
I don't know about any of you, but UT in Edgy won't start the normal way. I used to could go to /home/me/ut and there was a file named ut that I could double click on, and the game would launch. 

Not in Edgy. Now I have to go to /home/bill/ut/System and find the file ut-bin. 

How to correct this? 

In the terminal

```
gedit /home/me/ut/ut
```

Then in gedit, you can click on search>replace, then where it says, "_S_earch for:" type in ./loki then click on "Replace _A_ll" save it, and now you can double click on that and start the game. 

One less folder to navigate to, and it's easier to write a launcher for that than it is for ut-bin. And this is how you do that for a desktop launcher:

Right click on your desktop, and go to Create Launcher, go to Name and put Unreal Tournament (or Best Game Evar) then go to Command: and type in 

```
sh -c /home/bill/ut/ut
```

then click close. A new icon will appear on your desktop (which can be changed, of course, see the attached thumbnail for the one I use). You can now double click that to launch UT. (Save that icon to perhaps /home/me then click on icon in the create launcher window, and navigate to the /home/me folder and use that picture if you like it. I think just about any .png file will work. I don't think size is that big a deal, either as the image is resized when it is used as an icon, so play around with some stuff in gimp and perhaps you can use Xan's head as a ut launch icon!

---

### Post by hysterik on 2006-11-19
I have a step for step walk through posted on my clan forum website, which is specific to Ubuntu 64bit.  I'm also using the accelerated UTGLR GL library.  The game runs as smooth as I've ever seen it, and with the UTGLR piece the graphics can be made a bit brighter too.  Thanks for the cache collecting script, I'll make some use of that.  I don't play Zark, but I do a lot of 155/55 LGI.

Now, does anyone know how to set up a UT99 or UT2004 server on a linksys slug (NSLU2)?  Probably not possible?

[http://www.goodbull.com/phpbb2/viewtopic.php?t=52](http://www.goodbull.com/phpbb2/viewtopic.php?t=52)

---

### Post by BLTicklemonster on 2006-11-19
By slug, I take it you mean a router? I've gotten our router set up one time to allow UT to be played online, but it refuses to let me use my computer. Rather my son's has to be used on another connection. [www.unrealadmin.org](www.unrealadmin.org) I think that's the link... you can go there. They have a linux specific forum for server admins.

So ah, the ogl thing you speak of sounds good. I'll have to go check that one out. Thanks for the link. I guess you're from beyond unreal, right?

*edit:

Sweet renderer, thanks!

---

### Post by User_Program on 2006-11-19
I also ran into alot of other older games that didn't work due to edgy's sh being  linked to dash instead of bash.

I got sick of it so I 

> sudo dpkg-reconfigure dash


and selected "no" and everything is working great. This also worked with some packages that were failing to compile too. I haven't run into any problems with it yet.  The only thing I have heard about the switch in sh link, is dash runs faster.  But I don't know enough about it to give any insight.

But thanks for the alternative!

---

### Post by BLTicklemonster on 2006-11-19
Well, you see what you did is what one would do if one know wtf they were doing, see. What I did is what one would do if one were to muddle about all willy nilly trying to do what one can do with little useful kn- bah, lmao. I wondered when someone would come along and say something helpful! Nothing like reinventing the wheel to get people to show you a BMW. Thanks!

---

### Post by esaym on 2006-12-20
Im running dapper but perhaps one of you all will be able to help me.  I just got the game installed and I am having horrible mouse lag and the games runs fast and then slows way down randomly.  From what I have read it would seem like vsync is on but I don't think it is and I don't know how to tell.  I also did everything here: [http://www.goodbull.com/phpbb2/viewtopic.php?t=52](http://www.goodbull.com/phpbb2/viewtopic.php?t=52)  (great site btw!)and still no fix.  I am running on my desktop with an ati 9700pro.  I am starting to think that it is the card causing the trouble.  My 1ghz laptop with a geforce 2go runs the game better....

---

### Post by BLTicklemonster on 2006-12-20
Sorry bro, but ati cards and linux don't jive well when it comes to ut. There's a fix, I just don't know what it is. It isn't in the game settings either. Sorry, wish I could help. Someone ought to be along with an answer.

---

### Post by esaym on 2006-12-20
> **BLTicklemonster said:**
> Sorry bro, but ati cards and linux don't jive well when it comes to ut. There's a fix, I just don't know what it is. It isn't in the game settings either. Sorry, wish I could help. Someone ought to be along with an answer.

Hey thats exactly what I wanted to hear seeing how I got me a 6800 in the mail right now:mrgreen:

Thanks for the speedy response though.  Most of my threads the last week have been going unanswered :(

---

### Post by BLTicklemonster on 2006-12-30
> **User_Program said:**
> I also ran into alot of other older games that didn't work due to edgy's sh being  linked to dash instead of bash.

I got sick of it so I 



and selected "no" and everything is working great. This also worked with some packages that were failing to compile too. I haven't run into any problems with it yet.  The only thing I have heard about the switch in sh link, is dash runs faster.  But I don't know enough about it to give any insight.

But thanks for the alternative!


Excellent, thank you for that. it works great now, /home/bill/ut/ut and it's running.

---

### Post by esaym on 2007-01-03
> **esaym said:**
> Hey thats exactly what I wanted to hear seeing how I got me a 6800 in the mail right now:mrgreen:

Thanks for the speedy response though.  Most of my threads the last week have been going unanswered :(

Ok my new 6800 fixed all my problems in linux.:mrgreen:   Now just a quick question.  I have the goty edition.  I see there are warnings about playing the goty edition online?  Before I install the extra textures I just want to now if anyone has had any problems?

---

### Post by 8ABagel on 2007-01-03
I'm new to linux. I have ubuntu 6.10 installed and wanted to get UT running. I followed the directions in your post, however I got this error after running the first command.

bagel@Arcturus:~$ sh unreal.tournament_436-multilanguage.run
Verifying archive integrity... All good.
Uncompressing Unreal Tournament 436-multilanguage Installer...................................................................................
/home/bagel/.setup8797: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

Any suggestions would be appreciated. Thanks.

---

### Post by NTolerance on 2007-01-04
> **8ABagel said:**
> I'm new to linux. I have ubuntu 6.10 installed and wanted to get UT running. I followed the directions in your post, however I got this error after running the first command.

bagel@Arcturus:~$ sh unreal.tournament_436-multilanguage.run
Verifying archive integrity... All good.
Uncompressing Unreal Tournament 436-multilanguage Installer...................................................................................
/home/bagel/.setup8797: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

Any suggestions would be appreciated. Thanks.

```
sudo apt-get install libgtk1.2
```

---

### Post by BLTicklemonster on 2007-01-04
> **NTolerance said:**
> ```
sudo apt-get install libgtk1.2
```

:) WHAT HE SAID :)

---

### Post by esaym on 2007-01-05
Ok I got the goty version installed and plus I did all the updates from here [http://www.goodbull.com/phpbb2/viewtopic.php?t=52](http://www.goodbull.com/phpbb2/viewtopic.php?t=52)

Amazing enough anti aliasing is working!  It never worked in windows with my ati card.  Not sure if it is an ati problem or what.  Either way seeing UT at 16aa&af is freaking amazing!

---

### Post by 8ABagel on 2007-01-06
Thanks!

---

### Post by esaym on 2007-01-06
Oh yea one more thing.  How do I take screenshots?

---

### Post by druss316 on 2007-01-06
Hi. I got UT non GOTY installed..  And follow your directions step by step.  but when I run ut-bin it does nothing. I then tried the one on goodbull.com. It still didn't run..  Any idea?

I am running on edgy.

---

### Post by BLTicklemonster on 2007-01-06
Hmmm.  Oh yeah, this is what I did:

[http://www.ubuntuforums.org/showpost.php?p=1780929&postcount=9](http://www.ubuntuforums.org/showpost.php?p=1780929&postcount=9)

---

### Post by druss316 on 2007-01-06
ok.. I did that and now I get ut-bin: cannot execute binary file.
 
I got no idea what is going on.. this is very weird...

---

### Post by BLTicklemonster on 2007-01-06
$ cd /home/you/ut/
$ sh ut

see what happens

---

### Post by BLTicklemonster on 2007-01-06
Renderer:
[http://forums.beyondunreal.com/showthread.php?t=161177](http://forums.beyondunreal.com/showthread.php?t=161177)

---

### Post by druss316 on 2007-01-06
ok I did what U said.. now I come up with ./ut-bin: No such file or directory.. :[

ok I have UT installed in /usr/local/games/ut

when I run sudo sh ut. It tells me can't find System and ut-bin

but I goto /home/me I see a folder created called ut with sub directory System..  So something with the UT script is doing that instead of going to the correct location..

So when I move everything from /usr/local/games/ut to /home/me/ut.  I get the following error

ut: line 75: ./ut-bin: No such file or directory

---

### Post by BLTicklemonster on 2007-01-07
it's saying that because the script says it's in another place. When you installed, it gave you an option on where to install. Mine always defaults to my /home/me directory. 

do you have a .loki directory in your /home/you directory? 

Open nautilus or thunar or whatever, and go to your home directory, then press ctrl and h and look for .loki and see if it has a folder called UT, with a System folder in it. Is there a UT-bin file there?

I'm not sure what your problem is, but I'd guess put the files back in the original directory, and try starting it like this

cd /usr/local/games/ut

then 

sh ut

or is that what you did originally?

Sorry for the mixup. I didn't know UT hadn't installed in your home directory.

---

### Post by BLTicklemonster on 2007-01-07
> **esaym said:**
> Oh yea one more thing.  How do I take screenshots?


F9 and look in ~/.loki/ut/System

Now where did UT install for you? Was it in your home directory? loki ought to be /home/you/.loki regardless, I'm pretty sure of it.

---

### Post by druss316 on 2007-01-07
Hi, No I don't have a .loki folder..  I'm thinking it cause I'm running the x86_64 of ubuntu. But not sure.  I was able to get UT2004 install and working.

---

### Post by druss316 on 2007-01-07
Yea.. I did the sh ut. and it had problems finding ut-bin.

---

### Post by esaym on 2007-01-21
Ok I just noticed I have a problem.  The first time I installed ut I just did the basic install using the regular installer.  This timeb I installed the goty edition with the extra textures and I used the installer from this thread.  Now I have noticed that when connecting to a server every file that is sent to me I download really slow.  Like 5-10kBs.  So I really can't play on servers with lots of mods because of the slow downloading.  I didn't have this problem when I installed the non goty.

Anyone experience this before or know a fix?  I played with the netspeed but it didn't do anything.

](*,)

---

### Post by Xenix on 2007-01-22
I installed Unreal, but I am unable to start it.  When I open "ut-bin" under the "System" directory in the Unreal installation, it doesn't start.  No error messages or anything.

EDIT - Nevermind, I fixed it.  Just note to everyone with the GOTY of Unreal - you MUST use the GOTY installer if you have the GOTY version.  I tried using the other installer for the orginal version, and that is why it wouldn't run.

---

### Post by Ender777 on 2007-02-08
hey i just installed ubuntu 6.10 edgy, and i need UT:goty to work. I'm also kinda new to linux in general, but i'm kinda getting it down. I dled that file, but when i ran it this is the error i got: 

ender@jane:~$ sh unreal.tournament_436-multilanguage.goty.run
Verifying archive integrity... All good.
Uncompressing Unreal Tournament 436-multilanguage.goty Installer....................................................................................
/home/ender/.setup31658: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory

what should i do?

EDIT: Nvm now i just cant figure out how to get it off OpenGL :( it runs all choppy...

---

### Post by esaym on 2007-02-22
> **esaym said:**
> Ok I just noticed I have a problem.  The first time I installed ut I just did the basic install using the regular installer.  This time I installed the goty edition with the extra textures and I used the installer from this thread.  Now I have noticed that when connecting to a server every file that is sent to me I download really slow.  Like 5-10kBs.  So I really can't play on servers with lots of mods because of the slow downloading.  I didn't have this problem when I installed the non goty.

Anyone experience this before or know a fix?  I played with the netspeed but it didn't do anything.

](*,)

Ok I can verify that this problem is in both the 440 patch and the 451 patch.  I guess I will just be sticking with the official 436...
:(

---

### Post by BLTicklemonster on 2007-02-22
Good point, never install anything higher than 436 on your computer. There's nothing there to benefit you as a client on later releases, it's all server side stuff.

---

### Post by Hewure on 2007-03-15
Greetings from Perth, Western Australia, it's my 1st post, so go easy one me!!!

I'm new to Linux in general, and am reading through this thread to try and get UT GOTY running.

I'm a big fan of the game & will be completely converted to Ubuntu if I can get it running OK - I love the Beryl Interface...


Anyway, for anyone experiencing the game running too fast, or fast/slow, type this into the UT .ini file (located in UT System folder) in whatever  Renderer you use - 
FrameRateLimit=180

Here it is in my Open GL (from my Windows {sorry to swear} install)

[OpenGLDrv.OpenGLRenderDevice]
[COLOR="Red"]FrameRateLimit=180[/COLOR]
Translucency=True
VolumetricLighting=True
ShinySurfaces=True
Coronas=True
HighDetailActors=True
DetailTextures=True
Description=NVIDIA GeForce 6600 GT

The game doesn't like running at extreme framerates, so this just caps it. You can mess with the number, but 180FPS is pretty playable - LOL.

Hope this helps someone.

Regards, Steve ](*,)

---

### Post by BLTicklemonster on 2007-03-15
Thanks for the tip, Steve! Glad to see some folks down under know a great game when they see it!

---

### Post by Hewure on 2007-03-15
HA! 

UT is still pretty popular here, 2 ISP's run dedicated Servers, plus lots of private ones.

My brother, a few mates and myself often have a LAN on the Weekend - one guy is REALLY good, so we make sure his drink is never empty... "Another Beer, Paul? Fancy a Bourbon?" LOL

I managed to install it OK, running the "UT" didn't do a thing, so I tried your "UT BIN", but still no joy. Nothing happens whatsoever. I must admit I've only been skimming the thread. I might get rid of the install, start again, and go through all the advice step by step.

I'll have a look at your server once I'm up & running, though my ping will probably be woeful.

Thanks

---

### Post by BLTicklemonster on 2007-03-16
> **esaym said:**
> Ok I just noticed I have a problem.  

Well, I noticed the other night that you didn't seem to have any problems any more!!!

Nice to finally see someone from these forums on a server!

GGs!

---

### Post by Lystrodom on 2007-03-16
Ok, so, when I try to install this, it gets to a certain point, then says "Failure to read GenEarth.utx from disc" or something similar. I'm guessing it's just the disc, as it's pretty scratchy, anyone else have any ideas of what could cause that?

---

### Post by AJB2K3 on 2007-03-16
> **Hewure said:**
> HA! 

I managed to install it OK, running the "UT" didn't do a thing, so I tried your "UT BIN", but still no joy. Nothing happens whatsoever. 

Thanks
cd to the System folder and use

```
./ut-bin
```
Exactly as i printed because ubuntu is case sensitive and ut is tempermental on starting up.

---

### Post by BLTicklemonster on 2007-03-16
> **Lystrodom said:**
> Ok, so, when I try to install this, it gets to a certain point, then says "Failure to read GenEarth.utx from disc" or something similar. I'm guessing it's just the disc, as it's pretty scratchy, anyone else have any ideas of what could cause that?

I have not tried this in linux, but in windows you can install the demo, then turn around and install the 436 patch and have a fully functional game. If you can find the demo installer, if there is such a thing, perhaps you can try this instead? 

Also, see if you can copy the ut disk to another disk. I have found that some cds that are not usable for installation can be copied and work fine. Not always, but perhaps you can get away with this. See if this works before chasing down the demo. :)


AJ, I used an ati card, and ut was no where near as good as it is under nvidia. I had problems after problems. Hopefully there are better drivers now than there were back in the fall.

---

### Post by esaym on 2007-03-16
> **BLTicklemonster said:**
> F9 and look in ~/.loki/ut/System

Now where did UT install for you? Was it in your home directory? loki ought to be /home/you/.loki regardless, I'm pretty sure of it.

Yea lets see some screenies!

[[img]http://la.gg/thmb/Shot0019.png[/img]]("http://la.gg/upl/Shot0019.png")

[[img]http://la.gg/thmb/Shot0020.png[/img]]("http://la.gg/upl/Shot0020.png")

[[img]http://la.gg/thmb/Shot0021.png[/img]]("http://la.gg/upl/Shot0021.png")

[[img]http://la.gg/thmb/Shot0024.png[/img]]("http://la.gg/upl/Shot0024.png")

[[img]http://la.gg/thmb/Shot0025.png[/img]]("http://la.gg/upl/Shot0025.png")

[[img]http://la.gg/thmb/Shot0027.png[/img]]("http://la.gg/upl/Shot0027.png")


16x AA and AF :KS

---

### Post by BLTicklemonster on 2007-03-16
Okay, now that looks excellent! Great to see UT looking so great in linux, aint it?

---

### Post by AJB2K3 on 2007-03-16
Is this 2k3/4 or classic and is there some difference between the 6.06/6.10 installers?
or is it the UAnthology issue?
i ask because im still running Ubuntu 6.06 and my install runs of the hd not the cd's.

---

### Post by Lystrodom on 2007-03-16
It's the game of the year edition. [Here](http://pc.ign.com/objects/015/015579.html) it is on IGN.

Anyway, I tried copying the disc to my HD, but it failed at one point. I guess it's just too scratched.

I'll look into that demo-patch thing.

---

### Post by esaym on 2007-03-16
I don't know why yall are having so much trouble.  All I had to do was put the cd in and run one of the installer scripts: [http://www.liflg.org/?catid=6&gameid=51](http://www.liflg.org/?catid=6&gameid=51)

It doesn't matter what distro you have, all the installer does is copy the files from the cd rom and make the home directory.

---

### Post by AJB2K3 on 2007-03-17
> **esaym said:**
> I don't know why yall are having so much trouble.  All I had to do was put the cd in and run one of the installer scripts: [http://www.liflg.org/?catid=6&gameid=51](http://www.liflg.org/?catid=6&gameid=51)

It doesn't matter what distro you have, all the installer does is copy the files from the cd rom and make the home directory.
Mine worked fine except for the map extraction bug.

---

### Post by Hewure on 2007-03-18
[COLOR=Red]Alright![/COLOR] I got it working - and from the ut, not the utbin !?!?, so I just put a shortcut on the desktop.

**What Renderers are you guys using?** It looks OK, but is running about 1 1/2 times normal speed. Using NVidia Drivers, 6600GT, 1280x1024, SDLGLRenderDevice

The FramerateFix I posted earlier seems to make no difference with the SDLGLRenderDevice {Works a treat in [SIZE=1]Windows[/SIZE]), and normal OpenGL doesn't seem to work - got all the sound etc, no Display:mad:. (Installed UTGLR32).

Linux has been a pretty steep learning curve, but I'm enjoying messing it up so far.

[FONT=Comic Sans MS]Cheers, Steve[/FONT]

---

### Post by BLTicklemonster on 2007-03-18
From another forum:

> **G-Lite said:**
> If anyone is still around here... ;)
I managed to compile Chris Dohnal's OpenGLDrv for Linux.

I unfortunatly had to disable SSE support, UT for linux is compiled with and older version of gcc that doesn't support it, so I had to stick to that.

Besides that, I disabled some debugging code, which probably won't concern any of you. Basically all the problems Chris describes at the bottom of [his page](http://cwdohnal.home.mindspring.com/utglr/).

You can find it **[here](http://g-lite.kochen.nl/misc/OpenGLDrv.so)**.

For reference, my OpenGLDrv section looks like this:
(You can find a description for these also at Chris' [settings page](http://cwdohnal.home.mindspring.com/utglr/settings.html))
```
[OpenGLDrv.OpenGLRenderDevice]
UseGammaExtension=True
UseModulatedGamma=True
MinDepthBits=16
ShareLists=False
Translucency=True
VolumetricLighting=True
ShinySurfaces=True
Coronas=True
HighDetailActors=True
UseTrilinear=True
AlwaysMipmap=False
AutoGenerateMipmaps=False
NoFiltering=False
MaxAnisotropy=8
UseS3TC=True
NoMaskedS3TC=False
Use16BitTextures=False
UseBGRATextures=True
LODBias=0.000000
UseTNT=False
TexDXT1ToDXT3=False
UseMultiTexture=True
UsePrecache=True
MaxTMUnits=0
UsePalette=True
UseAlphaPalette=True
MaskedTextureHack=True
GammaOffset=0.500000
GammaCorrectScreenshots=True
GammaOffsetRed=0.000000
GammaOffsetGreen=0.000000
GammaOffsetBlue=0.000000
OneXBlending=False
RequestHighResolutionZ=True
RefreshRate=0
SwapInterval=1
FrameRateLimit=0
UseAA=True
NumAASamples=4
AAFilterHint=0
UseZTrick=False
MaxLogUOverV=8
MaxLogVOverU=8
MinLogTextureSize=0
MaxLogTextureSize=8
UseCVA=False
UseMultidrawArrays=True
BufferClippedActorTris=True
BufferTileQuads=False
UseSSE=True
UseVertexProgram=False
UseTexIdPool=True
UseTexPool=True
DynamicTexIdRecycleLevel=100
DetailTextures=True
UseDetailAlpha=True
DetailClipping=True
DetailMax=2
SinglePassDetail=False
SinglePassFog=False
ColorizeDetailTextures=False
```

[edit] "BufferTileQuads=True" - seems to cause artifacts all over the place here, just FYI; switched it off above. :)

---

### Post by CrazyCraz on 2007-05-28
Ok.. Im attempting this for like the 18th time, but I want to install GOTY without installing DISK 2.  I know some have done it, but with these installers, it asks to mount CD2 and if you say "NO" it goes to another window and says Click Exit to exit the program and erase all temporary files.  Obviously you can tell what happens next.  Everything gets deleted and nothing is remaining.  Is there a fix to this, because I DO NOT want to install the second CD.

---

### Post by BLTicklemonster on 2007-05-28
What are the chances that you can take the ut folder and the .loki folders that are created and when it asks for the second cd, copy those folders to the desktop, then allow the installer to kill progress when you say no, then put the moved folders back where they were and see if they work?

I'm sorry, but I have no idea how to get it to allow no second cd. But if someone knows, I hope they post here!

---

### Post by CrazyCraz on 2007-05-28
Well.. good thing is.. cut and paste worked for this.

Bad thing is, there is no ut-bin file in the ut/system folder.  In the /home/me/ut folder, there is a ucc and a ut.  I double click on either of those and nothing happens.

Oh.. one last thing... I love this game more than you !!!

---

### Post by CrazyCraz on 2007-05-28
Also, there is no hidden folder called loki ??

---

### Post by BLTicklemonster on 2007-05-28
There ought to be a ut file in the /ut folder.

have you tried crtl+h while in your /home/you directory to see if any .* directories show up?

If not, create one, then go 

/home/yourname/ut/ut

and see what happens.

Heck, if nothing else, I can copy and paste the file here and let you edit it to your settings. 

```
#!/bin/sh
###############################################################################
#
## LIFLG Startup Script
#
###############################################################################
#
# The game binary
GAME_BINARY="ut-bin"

# Subdirectory
SUBDIR="System"

# Additional commandline options for mods etc.
CMD_ARGS=""

# don't use US keyboard layout
#NOUSLAYOUT="true"


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

LANG=POSIX
export LANG
script=$0
count=0
while [ -L "$script" ]  
do
    script=$(readlink "$script")
    count=`expr $count + 1`
    if [ $count -gt 100 ]  
    then
        echo "Too many symbolic links"
        exit 1
    fi
done
GAME_DIR=`dirname $script`

if [ ! -d ${HOME}/.loki/ut/System ]
then
    mkdir -p ${HOME}/.loki/ut/System
fi

# Remove passwords from UnrealTournament.ini
if [ -r ${HOME}/.loki/ut/System/UnrealTournament.ini ]
then
	sed 's/\(SavedPasswords\[[0-9]*\]=\).*/\1/g' ${HOME}/.loki/ut/System/UnrealTournament.ini >  ${HOME}/.loki/ut/System/UnrealTournament.tmp
	sed 's/\(PasswordHistory\[[0-9]*\]=\).*/\1/g' ${HOME}/.loki/ut/System/UnrealTournament.tmp >  ${HOME}/.loki/ut/System/UnrealTournament.ini
fi

trap "setxkbmap" EXIT

# games run better with US keyboard layout
test $NOUSLAYOUT && setxkbmap -symbols 'us(pc101)'

cd $GAME_DIR
cd $SUBDIR

LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:$PWD
export LD_LIBRARY_PATH

# start the game
./$GAME_BINARY "$CMD_ARGS" "$@"
EXITCODE="$?"

# reset kb layout
setxkbmap

exit $EXITCODE
```

change bill to your name, and create a .loki directory in /home/yourname.

Save that up there as ut.bin in your /home/yourname/ut directory. Then open terminal, and 

cd /home/yourname/ut

then

sudo chmod 755 ut

and see if it works then.

---

### Post by esaym on 2007-05-29
This should be fine for the single cd version.  It is text based: [http://www.3ddownloads.com/beyondunreal/official/ut/ut-install-436.run](http://www.3ddownloads.com/beyondunreal/official/ut/ut-install-436.run)

Insert cd and then run "bash ut-install-436.run"

---

### Post by CrazyCraz on 2007-05-29
Cool beans.. im getting...

Can't find file for package 'Engine'.. now

the .u is in the system folder, so Im not sure what its trying to do.  I got a bit more tinkering to do.  I have UT working by using WineHQ to install it, but I want to learn this .loki way of installing it.

The only last thing I have to work on is getting into UTDC servers since UTDC does not like Linux.  I host 3 servers now (2-SLV servers and 1-INSTAGIB).  I set the UTDC.ini to not worry about OS's, but I guess im not getting something tweaked out right.  Still freaking kicking me due to the UTDC check.

I will figure that one out.  If you all like SLV or INSTAGIB, look for the PSK clan server (for SLV) and the HNC clan server (for INSTAGIB).  Great pings for East Coasters...  

KEEP UT ALIVE !!!

---

### Post by BLTicklemonster on 2007-05-29
If it's the new utdc, then the setting for os-s is backwards from what you'd expect. I think it's called

OSCare=True

is what it should be set to.

We run a linux server, and I put the latest utdc on it, and the os setting had to be differernt from what I thought it should be.

And for some reason, we had to drop that version. I can't remember why.


Hey Esaym, thanks for that post!!!


(btw, vehicles are beta testing on our server, look for maps with "manta" in the name. (Well, there is a DOM map I did, called DOM-UTV-bravehart that has vehicles in it, check it out)  And Onslaught for UT is in server beta test one. Local testing on a server at the house, but it's really cool. We shoud be putting it on our server before long)

---

### Post by CrazyCraz on 2007-05-29
Yea.. its set to true... still kicking me out.  Prolly gonna drop the server back to UTDC 1.7b rather than this 1.8 and see what happens.  Either way, Im still messing with this .loki installation wizard.

---

### Post by CrazyCraz on 2007-05-29
Yea.. its set to true... still kicking me out.  Prolly gonna drop the server back to UTDC 1.7b rather than this 1.8 and see what happens.  Either way, Im still messing with this .loki installation wizard.

I get these errors now...

craz@ChillOutCrew2-Linux:~$ ut
Unreal engine initialized
Bound to SDLDRV.so
Joystick [0] : Unknown Joystick
SDLClient initialized.
Bound to Render.so
Failed to load 'Engine': Can't find file for package 'Engine'
Signal: SIGSEGV [segmentation fault]
Aborting.
Exiting.
Name subsystem shut down
Allocation checking disabled
Segmentation fault (core dumped)
craz@ChillOutCrew2-Linux:~$

Engine.u is in the system folder also.  Not sure what else to expect with this error.

---

### Post by CrazyCraz on 2007-06-01
Any idea about the above error ??

I get these errors now...
 
 craz@ChillOutCrew2-Linux:~$ ut
 Unreal engine initialized
 Bound to SDLDRV.so
 Joystick [0] : Unknown Joystick
 SDLClient initialized.
 Bound to Render.so
 Failed to load 'Engine': Can't find file for package 'Engine'
 Signal: SIGSEGV [segmentation fault]
 Aborting.
 Exiting.
 Name subsystem shut down
 Allocation checking disabled
 Segmentation fault (core dumped)
 craz@ChillOutCrew2-Linux:~$
 
 Engine.u is in the system folder also. Not sure what else to expect with this error.

---

### Post by BLTicklemonster on 2007-06-01
Sorry, that's beyond me.

Can you get the errors from the unrealtournament.log file in /home/yourname/.loki/ut/system and post them here?

---

### Post by HeavyAl on 2007-06-20
Looks like an old thread but I thought I'd mention that this still occurs in Feisty. You have to run ut-bin in the System dir. 

Also, for those with frame rate problems, ie:FR is WAAAYY too fast to play, this is often caused by the cpu scaling tool 'powernowd' .. to disable it temporarily you can go to a shell and type 'sudo killall powernowd' which will stop it from messing with your game for the short term. Alternately you can disable it from System/Administration/Services .. some people have said they remove the package altogether but that seems a little overboard for my tastes.

Anyway, happy fraggin!

---

### Post by BLTicklemonster on 2007-06-20
Thanks for the input, Rafe! :popcorn:

---

### Post by UT1rulz on 2007-07-21
I installed UT GOTY on Ubuntu 7.04 32-bit using this guide but now Im having a problem with the sound in the game. The sound crackles horribly.
I just formatted my Ubuntu partition a few hours ago (had some other problems) and reinstalled everything, including UT. Before that the sound crackled only in multiplayer, in single player it was fine but the game ran extremely fast (the CPU speed is constant, Cool and Quiet is turned off in BIOS), in multiplayer the speed was normal but there was this horrible crackling. After installing UT I now also installed the bonus packs (didnt have them installed before) and now the speed is normal everywhere, but the crackling is also everywhere, so it seems like the speed problem and the sound problem are somehow connected.
Also I am unable to take screenshots in the game. Print screen button doesnt work, typing shot in the console doesnt work.
My computer is: Athlon 64 X2 4200+ dualcore CPU, 2GB DDR2, Geforce 7900 GTO.

Any ideas?

---

### Post by BLTicklemonster on 2007-07-21
64 bit cpu problems aren't my forte, but F9 is the screenshot button.

The sound... Well, there's an old fix for sound problems that may or may not work in your case...

But first off, what are you sound settings? (Esc, options, preferences,  audio)

Try different settings.

/home/yourname/.loki/ut/System/ open unrealtournament.ini

Look in 

[Audio.GenericAudioSubsystem]

UseFilter=True

UseSurround=False

UseStereo=True

UseCDMusic=False

UseDigitalMusic=True

UseSpatial=False

UseReverb=False

Use3dHardware=False

LowSoundQuality=False

ReverseStereo=False

**Latency=40     <-----------------------------this right here**

OutputRate=22050Hz

Channels=16

MusicVolume=192

SoundVolume=192

AmbientFactor=0.700000

DopplerSpeed=0.000000

Try changing the latency to 20 (?).


Now how messed up is that, I thought I had my sound set to surround sound... lol

---

### Post by UT1rulz on 2007-07-21
F9 was the first thing I tried when I wanted to take a screenshot :P
In Windows the screenshots are saved in the UT system folder, it should be same in Ubuntu, right?

Anyway, changing the latency to 20 didnt help.
My sound settings are:
Autotaunt off
Message beep on
Sound quality high (cant change it to low, when I close the window and come back its set to high again, even when I restart UT)
Music volume about 80%, sound volume 100% (changing the volume didnt help either)
Play voice messages all
No mature taunts off
Announcer volume about 80%
Use HW 3D/surround sound both off.

My ut.ini settings are:
[Audio.GenericAudioSubsystem]
UseFilter=True
UseSurround=False
UseStereo=True
UseCDMusic=False
UseDigitalMusic=True
UseSpatial=False
UseReverb=False
Use3dHardware=False
LowSoundQuality=False   <- tried setting it to "True" but in the game I still couldnt set the quality to low
ReverseStereo=False
Latency=20
OutputRate=22050Hz
Channels=16
MusicVolume=192
SoundVolume=192
AmbientFactor=0.700000
DopplerSpeed=0.000000

---

### Post by BLTicklemonster on 2007-07-21
See if there's a /.loki directory in your /home directory. You'll have to press CTRL+H to see hidden folders. 

If there is, you should have a ut/system in it. Stuff that affects ut are in it along with screenshots.

---

### Post by UT1rulz on 2007-07-21
No, there isnt. My UT system folder is located at /home/allan/ut/System, but there are no screenshots. I also recorded a demo and now I cant find that either.

Any more ideas about the sound issue?

---

### Post by fago on 2007-07-25
hm, I have the sound issue too. Any solutions?

---

### Post by UT1rulz on 2007-07-28
What is your computer configuration?

---

### Post by io1io2 on 2007-09-01
Just so other people don't have similar problems.....

to run ut on AMD64 you require the 32bit library packages (lib32) installed using

sudo apt-get install ia32-libs-sdl libc6-i386 lib32ncurses5 ia32-libs

symptoms are ut-bin pretending not to exist...

---

### Post by krizzze on 2007-09-07
hello all
recently, like 3 days ago, i started with ubuntu, and i gotta say i love it.
Today i configured wine etc
and i tried to install ut99 through the methods you all described above.
although nothing worked, tried ./ut.bin and many other commands but just nothing comes up, folowed by some error messages in the terminal.

```
krizzze@krizzze-desktop:~/ut99/System$ ./ut-bin
Signal: SIGIOT [iot trap]
Aborting.

```

and

```
krizzze@krizzze-desktop:~$ sh ucc

dirname: missing operand
Try `dirname --help' for more information.
Couldn't run ucc (ucc-bin). Is UT_DATA_PATH set?
```

then i tried to install the game through wine, which was succsful, btu when trying to load the game it says:

```

krizzze@krizzze-desktop:~$ wine "/home/krizzze/.wine/drive_c/UnrealTournament99/System/UnrealTournament.exe"
fixme:vxd:VXD_Open Unknown/unsupported VxD L"sice.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"siwvid.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:vxd:VXD_Open Unknown/unsupported VxD L"ntice.vxd". Try setting Windows version to 'nt40' or 'win31'.
wine: Unhandled page fault on read access to 0x00000000 at address 0x42d392 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x0042d392).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0042d392 ESP:0033da8c EBP:0033dad8 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:c03c5000 EBX:00000001 ECX:0033db00 EDX:00000000
 ESI:00000000 EDI:00400000
Stack dump:
0x0033da8c:  00400000 7b87a0f0 0033dad8 0033daac
0x0033da9c:  00000001 00000000 0033db00 00001010
0x0033daac:  00400000 7b87a0f0 00000001 00001010
0x0033dabc:  00000073 fcf32555 500007ff 0000c03c
0x0033dacc:  00000000 fcf30935 00000002 0033db9c
0x0033dadc:  0042d58f 00001010 0033db00 00400000
Backtrace:
=>1 0x0042d392 in unrealtournament (+0x2d392) (0x0033dad8)
  2 0x0042d58f in unrealtournament (+0x2d58f) (0x0033db9c)
  3 0x00428274 in unrealtournament (+0x28274) (0x0033dc4c)
  4 0x00426b9a in unrealtournament (+0x26b9a) (0x0033dc6c)
  5 0x004257ee in unrealtournament (+0x257ee) (0x0033dcb0)
  6 0x00425052 in unrealtournament (+0x25052) (0x0033fd0c)
  7 0x00424bc6 in unrealtournament (+0x24bc6) (0x0033fd64)
  8 0x0042761a in unrealtournament (+0x2761a) (0x0033fd9c)
  9 0x00410a99 in unrealtournament (+0x10a99) (0x0033fe7c)
  10 0x0041ace2 in unrealtournament (+0x1ace2) (0x0033ff08)
  11 0x7b87221e in kernel32 (+0x5221e) (0x0033ffe8)
  12 0xb7ec7897 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x0042d392: movl        0x0(%esi),%edi
Modules:
Module  Address                 Debug info      Name (47 modules)
PE      400000-44b000   Export          unrealtournament
ELF     7b800000-7b926000       Export          kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bc97000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7e754000-7e759000       Deferred        libxfixes.so.3
ELF     7e759000-7e762000       Deferred        libxcursor.so.1
ELF     7e762000-7e76a000       Deferred        libxrender.so.1
ELF     7e76a000-7e787000       Deferred        imm32<elf>
  \-PE  7e770000-7e787000       \               imm32
ELF     7e787000-7e78a000       Deferred        libxinerama.so.1
ELF     7e78a000-7e82a000       Deferred        libgl.so.1
ELF     7e82a000-7e82f000       Deferred        libxdmcp.so.6
ELF     7e82f000-7e832000       Deferred        libxau.so.6
ELF     7e832000-7e923000       Deferred        libx11.so.6
ELF     7e923000-7e931000       Deferred        libxext.so.6
ELF     7e931000-7e936000       Deferred        libxxf86vm.so.1
ELF     7e936000-7e94e000       Deferred        libice.so.6
ELF     7e94e000-7e957000       Deferred        libsm.so.6
ELF     7e957000-7e9e5000       Deferred        winex11<elf>
  \-PE  7e970000-7e9e5000       \               winex11
ELF     7ea55000-7ea75000       Deferred        libexpat.so.1
ELF     7ea75000-7eaa0000       Deferred        libfontconfig.so.1
ELF     7eaa0000-7eab4000       Deferred        libz.so.1
ELF     7eab4000-7eb1f000       Deferred        libfreetype.so.6
ELF     7eb1f000-7eb33000       Deferred        lz32<elf>
  \-PE  7eb30000-7eb33000       \               lz32
ELF     7eb33000-7eb4c000       Deferred        version<elf>
  \-PE  7eb40000-7eb4c000       \               version
ELF     7eb4c000-7eb92000       Deferred        advapi32<elf>
  \-PE  7eb60000-7eb92000       \               advapi32
ELF     7eb92000-7eb9e000       Deferred        libgcc_s.so.1
ELF     7ec95000-7ed52000       Deferred        gdi32<elf>
  \-PE  7ecb0000-7ed52000       \               gdi32
ELF     7ed52000-7ee8e000       Deferred        user32<elf>
  \-PE  7ed70000-7ee8e000       \               user32
ELF     7efa0000-7efab000       Deferred        libnss_files.so.2
ELF     7efab000-7efb5000       Deferred        libnss_nis.so.2
ELF     7efb5000-7efcc000       Deferred        libnsl.so.1
ELF     7efcc000-7eff3000       Deferred        libm.so.6
ELF     7eff7000-7f000000       Deferred        libnss_compat.so.2
ELF     b7d56000-b7d5a000       Deferred        libdl.so.2
ELF     b7d5a000-b7e9b000       Deferred        libc.so.6
ELF     b7e9c000-b7eb3000       Deferred        libpthread.so.0
ELF     b7ec0000-b7fd1000       Export          libwine.so.1
ELF     b7fd3000-b7fee000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\UnrealTournament99\System\UnrealTournament.exe
        00000009    0 <==


```

I have no idea where this comes from, anybody got any ideas for fixing one of these problems? 

THX you very much :-)


found another cd of ut and set the video settings to something with software instead of hardware.
and then it worked, but i change it ingae back to some higher settings and now it gives some "out of virtual memory errors".
some further digging is needed

but does anybody know what i did wrong with the "normal" installation?
i used .run files from here and that completed all succesfully

---

### Post by ZMEZman on 2007-09-13
> **BLTicklemonster said:**
> See if there's a /.loki directory in your /home directory. You'll have to press CTRL+H to see hidden folders. 

If there is, you should have a ut/system in it. Stuff that affects ut are in it along with screenshots.

Hey a Black Legion player wassup!!! TickleMonster...OK I've been using ubuntu now for about a week...and I find the compiz-fusion a nice feature...
But my question was I can't get UT to run I downloaded the first item BLTickleMonster put in here and I got this message:



2001@2001-desktop:~$ sh unreal.tournament_436-multilanguage.goty.run
Verifying archive integrity... All good.
Uncompressing Unreal Tournament 436-multilanguage.goty Installer....................................................................................
/home/2001/.setup9157: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory 
2001@2001-desktop:~$ 
   

And I don't know what to do now...
I'm kinda new to Linux...I used it back in 95 I think but haven't since...


I'm going to look through the forums more....

sudo apt-get install libgtkl.2    tried that also and got this: 

  Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libgtkl.2


 running Fiesty Fawn

---

### Post by tjotser on 2007-09-13
In terminal , type :

sudo apt-get install libgtk1.2

then try the installer again, should work :guitar:

* FINAL EDIT * , you typed it wrong , the "i" is a "1" as in one

---

### Post by BLTicklemonster on 2007-09-13
I see the Mercs are finally very well represented here! Glad to see you EZMan! 

Try what tjotser posted, but try

sudo aptitude install instead of apt-get. I remember reading exactly why it's better than apt-get, but I don't remember what all it was about, but that's what I do nowadays. 

Oh, and Krizze, I have no idea how to help you with your wine installation. Try the installer so you don't have to use Wine, and see how that does for you.

---

### Post by Tiago Cruz on 2007-11-08
> **fago said:**
> hm, I have the sound issue too. Any solutions?

I have problem with sound too.

I'm using one Dell Optiplex 745, with this audio controller:
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)


The sound works, but with 'echo' very bad....
What can I do? :(

---

### Post by Jiiprah on 2007-12-08
Here is a UT99 Icon and a UT Cleaner icon.

---

### Post by BLTicklemonster on 2008-01-05
Just a note for anyone installing using the native installer (not wine)

cd /home/yourname/ut 

then 

bash ut

should get the game playing.

Now if anyone knows how to get 


cd /home/bill/ut bash ut

to work in a shortcut or a launcher, please tell me, lol.


Anyone ever get the sound problems fixed? Can you share how it was done?


AND, has anyone ever had any luck getting UT to play smooth with ATI cards? I have an onboard xpress200, and UT is really choppy. Framerates hover around 30, and the screen is really dark. Using opengl, and the tweaks I posted earlier.

---

### Post by gijoe3k on 2008-01-08
Hi BLTicklemonster

I just wanted to thank you for your post for the " bash ut". I had all sort of problems w/ get utgoty working on the latest ubuntu, your suggestion made it work flawlessly. 

Also you asked about get ATI cards working correctly with UT/ubuntu. The post below is from a guy named MMatt. He fixed my issue with my Radeon 7500 card(thinkpad t30). I used to get really bad frame rates, downloading a program called "driconf" and enabling "hyper z performance" made my card jump from 750fps to 1700fps(I know that its nothing to brag about but it works!).

Anyway, if you have any questions let me know. Thanks dog!

> Originally Posted by mmatt  View Post
Ok, managed to make some serious performance increase in glxgears (~1700). Still haven't got Blender working!

Here's what I did:

1) Changed device section of /etc/X11/xorg.conf
Section "Device"
Identifier "ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
Driver "ati"
BusID "PCI:1:0:0"
Option "AGPMode" "4"
Option "EnablePageFlip" "true"
Option "AGPFastWrite" "true"
Option "EnableDepthMoves" "true"
Option "GARTSize" "64"
Option "AGPSize" "64"
Option "backingstore" "on"
Option "UseInternalAGPGART" "no"
EndSection

2) downloaded driconf (sudo apt-get install driconf). Enable HyperZ (Big improvement)

3) changed the default colour depth to 16 (another big difference, not noticeable in quality):
Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
Monitor "Generic Monitor"
DefaultDepth 16
.
.etc

Anyone getting better than ~1700 fps in glxgears (I know it's not a great benchmark but it does give an indication).

More importantly, has anyone got Blender to work in ubuntu feisty with this driver?

Matt

Edit: dropping to depth 16 made some SDL games (namely Neverwinter Nights) unplayable. Don't let glxgears be the only reference!]

---

### Post by BLTicklemonster on 2008-01-08
Sorry it took me this long to post it! I've been using it for a few months.

Bad timing, but thanks for the tip on using ATI, I think it will certainly come in handy here. I spent hours getting a Geforce fx 5200 to work in this computer. The problem was that ubuntu was looking for the card to be something like 

pci:1:5:0

but it was 2:4:0

and it took me forever to notice that and correct it in dpkg-reconfigure xserver-xorg. Heck, I can't even use a live cd without having to do that before I can get to the desktop! What a mess!

Anyway, thanks, I may try it out on another computer some day, and it's nice to know.

GL HF

---

### Post by MAXimator on 2008-01-12
hi ticklemonster

i'm totaly stuck on the installer.

i tell the installer to put the files on /opt/ut, symbolic links no, base install, standard textures, no start menu entries, and then the installer wants to mount the ut-cd, but i uploaded the files through ftp because i have no option to put the cd in, the server is too far away from me. 

if i choose '**no**' the installer quits :(

can you or anybody please help me out?

p.s.: i played ut 8 years ago, now it would be a pleasure to me to setup a classic server.

---

### Post by MAXimator on 2008-01-12
now i have a solution for my problem.
[this hint](http://www.liflg.org/?catid=2) helped me.

> The installer does not find the cd.
First try to export the CD-ROM environment variable: (Especially for auto/supermount users e.g. Mandrake).
export SETUP_CDROM=/path/to/your/mounted/cdrom
FreeBSD users: setenv SETUP_CDROM /path/to/your/mounted/cdrom


i typed 
[I][B]export SETUP_CDROM=/path/to/your/mounted/cdrom
[/B][/I]
and it worked:)!

---

### Post by BLTicklemonster on 2008-01-12
Glad you got it working, Max!

---

### Post by BertP on 2008-02-16
`I used to love playing the original UT,,,  If there is still an active online community I can dig out my old GOTY cd which should be somewhere in the closet  and install it under Wine but is there anyplace I can find the native Linux version?   and if do obtain  the Linux Cd's, will your instruction still work for Gutsy?

---

### Post by BLTicklemonster on 2008-02-16
I play all the time. 

Just when you get it set up, do this:


cd /home/yourname/ut

bash ut

and you're ready to rock.

Our clan has a Zark sniper server with some other weapon mods, and a fun bat wing mod by Henry House that's a trip. We even have some UT vehicle ctf maps, too.

[www.theblacklegion.clanservers.com/index.php](www.theblacklegion.clanservers.com/index.php)


As a matter of fact, for those of you who like to use teamspeak, it's in the repos:

sudo aptitude install teamspeak-client

then it's in applications, internet.

teamspeak-server is, also.

:)


What part of Alabama, Bert? I'm in Rome, Ga, up in the northwest corner of the state.

---

### Post by DarkSim on 2008-02-16
> **BLTicklemonster said:**
> Just a note for anyone installing using the native installer (not wine)

cd /home/yourname/ut 

then 

bash ut

should get the game playing.

Now if anyone knows how to get 


cd /home/bill/ut bash ut

to work in a shortcut or a launcher, please tell me, lol.


Anyone ever get the sound problems fixed? Can you share how it was done?


AND, has anyone ever had any luck getting UT to play smooth with ATI cards? I have an onboard xpress200, and UT is really choppy. Framerates hover around 30, and the screen is really dark. Using opengl, and the tweaks I posted earlier.

I don't know if this will work but its worth a shot.

1.)On your desktop make a text document that is executable.
2.)Write the following on the document and save:
```

#!/bin/sh

cd /home/bill/ut

./ut
```
3.)Double-Click on the Document and it should ask what you want to do. Hit Run and get a bunch of Head Shots with a Ripper

If you don't know how to change the document to being executable Right-Click on Properties and its on the Permission tab. You can also change the icon on the Basic Properties Tab from a piece of paper to the Unreal Logo.

I did something similar to this for my NWN installation and it works great.

---

### Post by BLTicklemonster on 2008-02-16
Thanks, DarkSim. I had to put 

bash ut

instead of 

./ut

 but it works great. Thanks!

---

### Post by BertP on 2008-02-17
Thanks for the help!   For the first time in at least 5 years I played  the original version of UT..... and this time  natively on Ubuntu!!

I still have a problem with the audio;   the sounds are recognizable  but they are somewhat garbled.   Do you have any ideas about how to fix this?


By the way, I live in central Alabama just south of Birmingham

Bert

---

### Post by BLTicklemonster on 2008-02-17
I'm lucky to not have had any sound issues, sorry, I don't know how to help with that. 

Try looking here:
[http://www.google.com/search?q=garbled+sound+unreal+tournament+site%3Bubuntuforums.org&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.com/search?q=garbled+sound+unreal+tournament+site%3Bubuntuforums.org&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

---

### Post by BLTicklemonster on 2008-02-18
By the way, there's this guy in our clan called Black Cheetah who is a freaking genius at ut stuff, and he's taken the models from UT2k4, and converted them to UT.

[http://skincity.beyondunreal.com/?section=models&action=show_infos&id=668](http://skincity.beyondunreal.com/?section=models&action=show_infos&id=668)

[IMG]http://skincity.beyondunreal.com/src/img_models/pic2_id668.jpg[/IMG]

---

### Post by DarkSim on 2008-02-19
That looks bad***. I'll go download it and give it a run. Time to start Mr. Crow's assault on the ladder. :D

---

### Post by GSF1200S on 2008-02-19
You know, id love to install this game as a native install. Unfortunately, none of the discs I can find contain the linux version. cant find it online either...

The GOTY version works fantastic with wine .46 (in gutsy repos), so im content for now. But if someone knows where the native linux version is, that would be great.

It really sucks because none of the mods work on the wine install of it... (cant get them loaded).

---

### Post by BLTicklemonster on 2008-03-11
Oooh, I missed your post. Sorry. Look back over the first of the thread. You download a linux installer to use with your disk, and it installs the game so it plays in linux.

I have been using an Nvidia geforce fx5200 video card, but I just decided to try out the ati card that's built onto the mother board. As far as renderers is concerned, I was using a version listed in this thread based on Chris Donhal's ogl renderer, but antchecker kept kicking me, so I went to unrealadmin.org and clicked on downloads, unrealtournament, patches, linux, and downloaded the utpatch 451, and extracted just the ogl .so and int files and was using them in linux, but now with the ati onboard graphics, I use the sdlgld files, and it is pretty good. Graphics aren't as "normal" and speed isn't what I was used to, but it's smooth enough to play for now without any tweaks.

In case anyone wants ideas on renderers to use...

---

### Post by esaym on 2008-10-15
An update for some people.  Many people are effected by the problem of UT99 running too fast: [http://icculus.org/lgfaq/#runeutfast](http://icculus.org/lgfaq/#runeutfast) Basically if you have a newer style cpu with frequency scaling you will be effected.

The original fix was to spam the CPU with random mathematics to get the cpu up to max speed before the game started.  However this only works if the cpu stays loaded up enough during game play to keep the frequency at max.  With today's high power cpu's UT99 will not tax the cpu enough to hold it at max speed.  The result is the cpu speed will sometimes change from max to min during gameplay causing game speed craziness.

I have found the fix to be editing the ut start up script to set the scaling governor to performance before the game starts.  This will stop and cpu speed changes while in game play.  Conveniently the start up script stays running in the background until you exit UT.  This also made it easy to set the scaling governor back to ondemand (or what ever) when the game exits.


So to do this, you first need to find the UT start up script, it is labeled "ut".  Mine is located in /usr/games/ut/ut

Open the script and find where it executes "ut-bin" and added this above it:
echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
and then add this below it:
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

Here is a sample of mine:

```
LD_LIBRARY_PATH=${LD_LIBRARY_PATH}:$PWD
export LD_LIBRARY_PATH

echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

# start the game
./$GAME_BINARY "$CMD_ARGS" "$@"
EXITCODE="$?"

echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

# reset kb layout
setxkbmap

exit $EXITCODE

```

So as you can see, we set the cpu to max speed before ut-bin is run.  Then once you exit UT, ut-bin is killed and the script continues and the next step is to set the governor back to ondemand and then the script terminates.

Works great!  

Also note that for a regular system user to be able to adjust the cpu governors, you need to set the permissions on /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor.

You can do this automatically at startup by adding:
chmod 777 /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

to /etc/rc.local

:KS

Modified original UT start up script:

---

### Post by BLTicklemonster on 2008-10-15
Fascinating. And seeing as how UTDC won't scan what's going on with a linux box, this will not give a false reading as a speed hack? Can this be used on older machines as a speed hack? If so, the security implications are somewhat touchy. I'd hate to see admins locking linux players out of their servers. At present, they have to allow us in the first place depending on the security they use. BUT, that there is one kick a** fix, bro.

---

### Post by esaym on 2008-10-16
> **BLTicklemonster said:**
> Fascinating. And seeing as how UTDC won't scan what's going on with a linux box, this will not give a false reading as a speed hack? Can this be used on older machines as a speed hack? If so, the security implications are somewhat touchy. I'd hate to see admins locking linux players out of their servers. At present, they have to allow us in the first place depending on the security they use. BUT, that there is one kick a** fix, bro.

I don't know what UTDC is, one of those things that checks for aim bots or something?

But no, this is all very low level stuff with the cpu, out of the reach of normal software, UT doesn't care what your cpu speed is, it just change change once it has loaded.  
Back in the era of 1998, cpu's didn't change their speed on the fly to "save power"  When ut-bin is first loaded it grabs the cpu speed apparently.  Then once the game gets going and the cpu starts to work, the motherboard (or software drivers) can bump the cpu speed up from it's standard powersave mode of ~1000mhz to what ever the max speed it is rated for.  (Mine idles at 1000mhz and under load it changes to 2900mhz).  UT does not know how to coupe with this.  In a single player game it causes the gameplay to be faster than humanly playable.  In an online environment, it causes massive stuttering.  None of this could be used to an advantage.


Only certain cpu's with supported motherboards can change their speed on the fly, mainly any laptop since 2002 and any motherboard/cpu combo supporting AMD cool 'n quit technology or Intel speedstep:
[http://www.amd.com/us-en/Processors/ProductInformation/0,,30_118_9485_9487%5E10272,00.html](http://www.amd.com/us-en/Processors/ProductInformation/0,,30_118_9485_9487%5E10272,00.html)
[http://www.intel.com/cd/channel/reseller/asmo-na/eng/203838.htm](http://www.intel.com/cd/channel/reseller/asmo-na/eng/203838.htm)

---

### Post by Sir_Brizz on 2009-06-18
So nobody ever figured out the sound latency issues? I have the game installed and it runs great, but the sound lags up to a second behind what is going on on-screen. Also, I have a measly P4 3.0ghz laptop I'm running it on, so I don't think it's a speed issue.

---

### Post by NTolerance on 2009-06-19
> **Sir_Brizz said:**
> So nobody ever figured out the sound latency issues? I have the game installed and it runs great, but the sound lags up to a second behind what is going on on-screen. Also, I have a measly P4 3.0ghz laptop I'm running it on, so I don't think it's a speed issue.

I also have the sound latency problem.  Something has been fixed since Feisty that stops the distorted sound issue, but now this latency problem is there.  I have experimented with all values in the sound section of the UnrealTournament.ini file with no success.  I've tried both OpenAL and Generic sound configs in the ini file.  I have to run UT with aoss to prevent sound distortion.  Could this be related to pulseaudio?

---

### Post by NTolerance on 2009-07-03
SUCCESS!

Let me start by laying out some of the UT sound problems as they've progressed over the last couple of years.  On systems with Intel HDA audio, Feisty, Gutsy, and possibly others had issues with crackling audio.  From what I can tell, something may have happened with ALSA around the time of Hardy/Intrepid/Jaunty that fixed this problem.  One down.  

Now, most guides recommend using the "aoss" command to get clear audio in Jaunty.  This is one of the factors that causes the remaining latency issues where sound effects are about a full second behind actual game events.  The "padsp" command seems to make things go, possibly in combination with other settings.  I'll also add that while "aoss" prevents background applications such as Rhythmbox from playing music mixed in with the game sounds, this works fine with "padsp", which I'm quite pleased with.

So without further ado, here's the combination of settings that give perfect audio on my Jaunty system with an Intel HDA chip:

1.  Set audio system in ~/.loki/System/UnrealTournament.ini to AudioDevice=Audio.GenericAudioSubsystem.
2.  Use custom startup script from [this site](http://fingel.com/ut/howtos/utonlinux.html) to start UT at the correct speed.
3.  Use "padsp" command in front of the custom startup script to get audio working properly with no latency:
```
padsp /usr/local/games/ut/utcustom.sh
```

On a side note, I've had further success getting all the buttons on my Logitech MX518 mouse working in UT.  Those using this mouse may know that the +/- buttons change the sensitivity of the mouse.  I don't really like this feature and much prefer to use those buttons as functions in games.  Also, UT can't recognize more than 3 mouse buttons.  I prefer to use the "back" button as alt-fire, but UT won't recognize it.  In short, I used two programs, lomoco and evrouter, to get all buttons working and recognized in UT.  For the buttons that UT can't detect, I used evrouter to set them to keyboard events.  I can't go into further detail right now, but I may make a guide in the future if there's interest.  Maybe we can collaborate and make the definitive UT sound/mouse guide that puts all info on one page.

On a second side note, has anyone tried switching from fullscreen UT to a virtual terminal and back again?  I'd like to do this so I can control Rhythmbox while playing the game, but when I switch back to UT a mouse cursor is placed in the center of the screen and kinda ruins the experience.  Anyone know how to fix this?

Edit:  With regards to the mouse cursor problem, [this xorg.conf](http://ubuntuforums.org/showpost.php?p=7123231&postcount=12) fix appears to work for me.  But I wonder about the implications of "SWCursor".  Any disadvantages to using it?

---

### Post by BLTicklemonster on 2011-03-08
On Karmic, no sound. The post above didn't help, and now my game crashes. :(

---

