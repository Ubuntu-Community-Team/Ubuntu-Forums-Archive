---
title: "World of Padman Out Now! (new free game :P)"
date: 2007-04-01
forum: Gaming &amp; Leisure
---

### Post by hikaricore on 2007-04-01
Download: [http://padworld.chillerlan.net/index.php?files=main](http://padworld.chillerlan.net/index.php?files=main)
Trailer: [http://www.youtube.com/watch?v=IeOoKrqK2F8](http://www.youtube.com/watch?v=IeOoKrqK2F8)
Homepage: [http://www.worldofpadman.com/](http://www.worldofpadman.com/)

This game looks awesome, and all I can think at this moment is that if this is a 550mb
april fools joke, I'm going to kill someone's dog.  :)

Borrowed from linux-gamers.net:

> Its finally done!! The WoP team released the standalone version of this great game today. The installer file is about 550 MB, several download locations are available for the linux version, so take a closer look at their Homepage. There you will aswell find a list of public game servers.

---

### Post by Bekker on 2007-04-01
Finished downloading and played it moments ago, first impression: :shock: :-D This game rocks and it's free!
So start downloading and install with
```
sudo sh worldofpadman.run
```

---

### Post by finferflu on 2007-04-01
I'm downloading it right now. The trailer looks awesome, I hope the game does as well. Is it open source?

---

### Post by DirtDawg on 2007-04-01
I can't find the minimum requirements. Anyone know?

---

### Post by Bekker on 2007-04-01
I wouldn't know where to find them either, but it works on my sytem with all settings high and a resolution of 1280x1024
my system: Dapper Drake on an AMD Athlon 2000xp+ with a NVidia Geforce 6600GT and 756mb of memory.

---

### Post by Perfect Storm on 2007-04-01
Looks cool, gonna examin that game a bit further.

---

### Post by DirtDawg on 2007-04-01
> **Bekker said:**
> I wouldn't know where to find them either, but it works on my sytem with all settings high and a resolution of 1280x1024
my system: Dapper Drake on an AMD Athlon 2000xp+ with a NVidia Geforce 6600GT and 756mb of memory.

Hmm, I have el-crappo Intel 64M video, so it's always iffy with the 3D.

---

### Post by Perfect Storm on 2007-04-01
Read somewhere it uses Quake 3 engine so you might check the req. for quake 3.

---

### Post by Perfect Storm on 2007-04-01
Found the minimum req. for Quake 3 on tuxgames;

Operating System	2.2.9 or better Linux kernel with glibc-2.x and X-Windows
Processor	266 MHz x86 Processor
Memory	64 MB
Disc Space	200 MB
CD Rom	4 x CD Rom
Graphics Card	Graphics card with 4 MB video memory
Sound Card	OSS Compatible

By the way I have added World of Padman to UGA's news.

---

### Post by DirtDawg on 2007-04-01
Cool, thx :KS

---

### Post by plb on 2007-04-01
Anyone try it out yet?

---

### Post by Perfect Storm on 2007-04-01
Still downloading, 20min for ~550MB.
I'll report back.

---

### Post by yabbadabbadont on 2007-04-01
The screenshots look really cool.  I like the cartoony style.  In case it wasn't obvious, I'm a big Sam & Max fan too.  :D

---

### Post by Perfect Storm on 2007-04-01
Okay....downloaded and installed. Just be aware if you installed it globally (with sudo priveledge) to exit the installer (don't push the launch World of Padman button) or you'll mess up the permission of WoP.
Nice intro ^_^...alot of option to tweak the game itself, but the singleplayer option havn't been implemented yet. So if you are singleplayer dude you have to wait a bit more...

---

### Post by DirtDawg on 2007-04-01
All the download links are giving me a page of code rather than a download, except for exp.de, which I cannot read. Anyone else have luck with this?

---

### Post by Perfect Storm on 2007-04-01
Right click on the link and choose download link as. Or copy the link and use D4x.

---

### Post by hikaricore on 2007-04-01
I love this game, i feel like i'm playing MicroMachines lol.  Except with cartoons and guns.

---

### Post by Ruthenium on 2007-04-01
Nice game, I love the intro and all the artwork, the game feels great too, thanks for the link.:)

---

### Post by plb on 2007-04-01
So it's multiplayer only?

---

### Post by DirtDawg on 2007-04-01
> **Artificial Intelligence said:**
> Right click on the link and choose download link as. Or copy the link and use D4x.

Of course! Geez, thanks again.

---

### Post by hikaricore on 2007-04-01
> **plb said:**
> So it's multiplayer only?

At the moment yes.  I think the rushed the release out of
frustration of the game taking so long to complete.  The
faq and other sections of their site mention single player
mode alot so it's probably not far off.  They might have
even forgot to enable it in their haste.

---

### Post by Bekker on 2007-04-01
I still love this game, one of the first games on linux I feel I can really get addicted to. But I noticed that every time I start the game it forgets the changes I made to the settings. Kinda annoying.
Does anybody know how to solve this? It probarly has to do with that I installed it using sudo...

---

### Post by Bekker on 2007-04-01
While typing my last post I thought of a solution, and it worked!
So here's the answer to my own question in case somebody else has the same problem.
Not a pretty solution, I know, but run the game once as root (sudo wop) and set everything to your liking and quit. Now if you run it as some user it'll use root's settings you just set.

---

### Post by .oops on 2007-04-01
Can I expect better perfomance than in, lets say, Enemy Territory?

---

### Post by hikaricore on 2007-04-01
> **Bekker said:**
> I still love this game, one of the first games on linux I feel I can really get addicted to. But I noticed that every time I start the game it forgets the changes I made to the settings. Kinda annoying.
Does anybody know how to solve this? It probarly has to do with that I installed it using sudo...

I'm guessing you lanched the game for the first time from the installer, which would have root owned your ~/.WoPadman/ directory.

```
sudo chown username:username -R ~/.WoPadman/
```

Replacing username with your user's name.  :)  Hopefully this works.

---

### Post by DirtDawg on 2007-04-01
I got it working pretty smoothy on the "fastest" setting, but boy it's dark. I've turned the gamma all the way up, but it doesn't seem to have had an effect. Anyone else had/solved this problem?

EDIT: Nevermind. There's an option called "Ignore HW Gamma?" that's defgaulted 'on'. Turning that off solved the issue quick-like. Cool.

---

### Post by compiledkernel on 2007-04-01
Dudes, that game is so cartoony and fun, I havent played a game that made me laugh THAT HARD in a long time. 

Post us your favorite servers, and Ill be sure they get put on the UGA Server list, also post your callnames.

---

### Post by hikaricore on 2007-04-02
> **compiledkernel said:**
> Dudes, that game is so cartoony and fun, I havent played a game that made me laugh THAT HARD in a long time. 

Post us your favorite servers, and Ill be sure they get put on the UGA Server list, also post your callnames.

Havn't really picked a favorite server much, but if you see me on any, I'll be: hikaricore

Imagine that eh?  :P

---

### Post by 2dere on 2007-04-02
WoW screenshots and vid look awesome. Never been a FPS (this is more because of how much I suck at them) but I really want to play this too bad I won't be up till the weekend.

---

### Post by Perfect Storm on 2007-04-02
Howto added for those who needs it: [http://gaming.gwos.org/e107_plugins/content/content.php?content.63](http://gaming.gwos.org/e107_plugins/content/content.php?content.63)

---

### Post by Bekker on 2007-04-02
> **hikaricore said:**
> I'm guessing you lanched the game for the first time from the installer, which would have root owned your ~/.WoPadman/ directory.

```
sudo chown username:username -R ~/.WoPadman/
```

Replacing username with your user's name.  :)  Hopefully this works.

That did the trick :-) I was so excited to play the game when I installed it so I launched it from the installer right away the first time.

---

### Post by JunySan on 2007-04-02
Thanks to Artificial Intelligence for the "HowTo" , it worked perfectly.:) 

Great Game!

---

### Post by scotty2hott2k on 2007-04-02
absolutely cracking game.

---

### Post by darksong on 2007-04-02
Is there a way i can change the resolution the app boots in - it wont boot under the res i set =(

---

### Post by PhatStreet on 2007-04-02
This is pretty fun. Fast-paced, free, and it has a unique style. I just wish there were more servers, although I may not have queried the server correctly.

---

### Post by techstop on 2007-04-02
I'm getting 500 Internal serer errors when trying to download or go to the homepage. :cry:  I found the file on my ISP's mirror though.

But the trailer looks awesome! This is a Quake3 mod right? Might see you guys online soon! :mrgreen: :mrgreen:

---

### Post by argie on 2007-04-03
For those wondering about Minimum Requirements:
It runs on my Intel Pentium IV 2.9 Ghz with 256 MB RAM and onboard VIA graphics with 32 MB shared. This doesn't play Nexuiz at all, but WoP works just fine at 640x480.

It's a pretty damn neat game. I'm liking it.

---

### Post by darksong on 2007-04-03
It breaks way to easily - i tried changing my graphic settings to how i want them and it broke - they need to improve on this, apps should be able to run no matter the Resolution.

---

### Post by hikaricore on 2007-04-03
> **darksong said:**
> It breaks way to easily - i tried changing my graphic settings to how i want them and it broke - they need to improve on this, apps should be able to run no matter the Resolution.

```
rm -R ~/.WoP
```

From a terminal should fix it.

I don't think you can honestly expect as much from a free game as you seem to be.

If you break it, you need to take personal reponsibility and fix it.

---

### Post by hobieone on 2007-04-03
i just down loaded it the game and i agree it rocks. i hope they come out with a level editor and and a few more maps and game modes like tossee capture the flag.

---

### Post by Mateo on 2007-04-03
Mine is showing that there are no servers.  anyone else have this problem?

---

### Post by argie on 2007-04-03
> **hobieone said:**
> i just down loaded it the game and i agree it rocks. i hope they come out with a level editor and and a few more maps and game modes like tossee capture the flag.

It seems to be based on the quake3 engine. I'm willing to bet the quake3 map editor can make maps.

---

### Post by Mateo on 2007-04-03
it is based on the quake3 engine.

by the way, if you aren't finding any servers, make sure to change from 'local' to 'internet'.

---

### Post by Velociraptor on 2007-04-04
This game is amazing, I never ever thought I would see such slick graphics in a game on Linux! My mind boggles how much work the developers put into this. 

I have it running at 1280x1024 on my old nvidia 6600 gt, and smoooth (well once I turned compiz off). And the download includes x86_64 binaries too!

I just need to read the manual to figure out how I increase my score from zero!

Oh, and the installer states that they intend to release under the GPL!

---

### Post by Mateo on 2007-04-04
it is a tad difficult. the combination of so much open space and slow-moving projectiles makes it hard to do anything but jump and shoot randomly.

---

### Post by Gorthus on 2007-04-04
We should all get into a game... Call it "Ubuntu gamers FTW!" :D

---

### Post by compiledkernel on 2007-04-04
> **Gorthus said:**
> We should all get into a game... Call it "Ubuntu gamers FTW!" :D


UGA will support this.  [http://gaming.gwos.org](http://gaming.gwos.org) 

Reference this thread as well. 

[http://ubuntuforums.org/showthread.php?t=400963](http://ubuntuforums.org/showthread.php?t=400963)

---

### Post by Gorthus on 2007-04-04
Hm... I just downloaded... When I am trying to install It says please choose components to install and there are 4 options...

all 4 are checked but I need to uncheck one. How do I do that?

---

### Post by TravisNewman on 2007-04-04
I love this game. Quake 3 lends itself well to total conversions. I can't wait for the SP to get finished.

---

### Post by Perfect Storm on 2007-04-04
> **Gorthus said:**
> Hm... I just downloaded... When I am trying to install It says please choose components to install and there are 4 options...

all 4 are checked but I need to uncheck one. How do I do that?

What's your options?

---

### Post by Gorthus on 2007-04-04
Nevermind... I got in...


I don't really like the game... To fast pased... I'm more into WWII games with snipers...

---

### Post by EdThaSlayer on 2007-04-04
Great trailer. This game looks very unique and models look great. Thats why *clicks on some link* I'm downloading it.

---

### Post by Mateo on 2007-04-04
> **Gorthus said:**
> Nevermind... I got in...


I don't really like the game... To fast pased... I'm more into WWII games with snipers...

not WWII, but you should check out this game if you like "realistic" shooters:

[http://ubuntuforums.org/showthread.php?t=400043](http://ubuntuforums.org/showthread.php?t=400043)

---

### Post by techstop on 2007-04-09
My screen is very dark when running this game. Any pointers on how to change brightness or gamma from the console for instance?

---

### Post by Perfect Storm on 2007-04-09
Go into the game option, I think it's under display, and set gamma to off

---

### Post by techstop on 2007-04-09
> **Artificial Intelligence said:**
> Go into the game option, I think it's under display, and set gamma to off

No, there is no ingame option for gamma, that's why I asked. ;-) 

However, I did just find the answer. Being based on Quake III, there is a cfg file located here;

~/.WoPadman/wop/wop_config.cfg

There is an option in there called;

seta r_ignorehwgamma "1"

Change the variable to "0" (ie off) and my gamma was back to normal. Hope this helps someone, I've seen a few people asking about it in the game chat...

---

### Post by Perfect Storm on 2007-04-09
Well, it should be there (it's in mine), so you don't have to edit the fil config file.

---

### Post by techstop on 2007-04-09
> **Artificial Intelligence said:**
> Well, it should be there (it's in mine), so you don't have to edit the fil config file.

My apologies, I just found it after having another look.... :oops: 

I swear I looked over and over and over and ....

Well, you get the point, all sorted now. Cheers!

---

### Post by EdThaSlayer on 2007-04-09
I keep getting  this error. :confused: 
> edwin@edwin-desktop:~/MyDownloads$ sudo sh worldofpadman.run
Verifying archive integrity...Error in MD5 checksums: 61afb0087c4fbb1489d66f4466d2696a is different from 1fb54282c982a07232b553eeeeb6c654


I also don't know how to fix this. :(

---

### Post by Swimerdude on 2007-04-09
try uninstalling it then reinstalling it?

---

### Post by EdThaSlayer on 2007-04-09
> **Swimerdude said:**
> try uninstalling it then reinstalling it?

I'm trying to install it. :( 
This is the first step to install the app. :(

---

### Post by Perfect Storm on 2007-04-09
Looks like a bad download when the checksum doesn't match.
A new download is a good idea.

---

### Post by EdThaSlayer on 2007-04-09
> **Artificial Intelligence said:**
> Looks like a bad download when the checksum doesn't match.
A new download is a good idea.

Alright :( 
(Prepares for another 9-10 hour download)

---

### Post by Perfect Storm on 2007-04-09
Ah, you are on dialup I guess :-/
Try see if you can find a torrent instead, more reliable. Otherwise use D4X alot saver than normal download.

---

### Post by 2dere on 2007-04-14
I installed Padman but only clicked on one of the options at the end ( I think it was 'add to list of something' ) I and dont' know how to start up the game. Sorry for sounding like a complete nub (I am but I'm trying to learn so I put off asking this earlier trying to find out how to start games from a terminal or something but couldn't figure it out) 
Thanks guys

---

### Post by Bekker on 2007-04-14
It should be in your taskbar menu ---> games
But apparently you changed some of the settings in that 'add to list of something'  so it's not there.

Hopefully you know how to execute commands from the commandline, 'cause the command to start world of Padman is wop.

If it works correctly and you like to play it more often you can also try and make an icon for it on your desktop. I don't know how to do that using Gnome (I'm on KDE), but you should be able to work it out yourself :)

---

### Post by 2dere on 2007-04-14
hmm I dunno what I changed nothing was selected to begin with. I thought I selected the logical choice that would put it in that list but I guess not. I can't do the command line thing I haven't learnt yet so your wop comment is lost on me. Cheers for the 'almost helpful' post

---

### Post by Bekker on 2007-04-14
o dear, well you can execute commands from the commandline in the terminal. To be found at the menu ---> Accessories--->Terminal
A new window should open stating something like
```
Username@Computername:~$
```
with a blinking cursor waiting for your commands!
Just type wop and press enter, this should execute world of Padman

I suggest you learn a bit more about linux, there are loads of tutorials on the internet. And also don't be afraid to ask stuff, there's an absolute beginners talk section on this forum.

A bit more info about the (ubuntu) command line: [gwos command line]("http://doc.gwos.org/index.php/CommandLineBeginners")
It gives more information then you need now but just glimpse through it to get an idea of the possibilities.

---

### Post by 2dere on 2007-04-14
Sorry for sounding like an **** Bekker, I'm tired and it got to me (perhaps deciding not to sleep till I got the game working wasn't a good idea.) I reinstalled the game (over the current version for some reason their uninstall did nothing???) and the same thing happened quoting the readme > After installation an icon should appear in the game folder of the start
menu. You can also start wop manually by simply entering "wop" in the
console.
Which made click into what you were saying, sadly both these things hasn't come true. sadly the other readme informs me how to play the game so that didn't really help. The files are where they said they'd be so far thats the only thing they've said is right. I think I will go to bed and try again later and don't worry I am trying to learn from the tutorials out there

---

### Post by Bekker on 2007-04-14
No problem at all. You get some good night's sleep and when your all fresh again maybe this helps:
Have you been able to enter "wop" on the commandline (console/terminal, it's all about the same)? If you did, what happenend? Did your screen flicker, did you get any output on the commandline (post here please)?

I haven't felt the urge to uninstall this game so no experience with not working uninstall scripts...

Sleep tight ;)

---

### Post by User_Program on 2007-04-14
This game looks amazing !     downloading now.

Does anyone know if this is a new engine or a Q3 engine.  If so would making maps be the same as Q3 ? If not does anyone have any info for map making.. There forums seem to be down or I would have gone there.

Thanks!

---

### Post by Mateo on 2007-04-14
the game is fun, but a bit too hard.  all you can do is really randomly shoot.  players run really fast and the guns shoot really slow. so hitting someone seems like more luck than skill.

---

### Post by hikaricore on 2007-04-14
> **Mateo said:**
> the game is fun, but a bit too hard.  all you can do is really randomly shoot.  players run really fast and the guns shoot really slow. so hitting someone seems like more luck than skill.

So it's exactly like 75% of all other FPS games ever created?  :P

---

### Post by Perfect Storm on 2007-04-14
> **hikaricore said:**
> So it's exactly like 75% of all other FPS games ever created?  :P

Wish I could say the same for the RPG and Strategy genre....

---

### Post by jorgerosa on 2007-04-15
Im impressed too. I even post a thread about this game (Link: [http://ubuntuforums.org/showthread.php?t=409939](http://ubuntuforums.org/showthread.php?t=409939))
Because i never saw this one.
"This game looks awesome, and all I can think at this moment is that if this is a 550mb
april fools joke, I'm going to kill someone's dog. " - All credits for posting in Ubuntu forums, goes to: hikaricore.
BTW, Im also starting to love it...

Hi, **Bekker**, I'm playing under the name "ONE-FROM-PT". Cya.
Couldn´t  post answer there, because some *artificial intelligence* closed the theread ;) np

**Mateo:** ..."so hitting someone seems like more luck than skill" - **Thats WHY i love this game... ** \\:D/ 8-[ ... i stay alive, stay alive, stay alive, aaah, aaah, aaaaaaaah... ;)

---

### Post by Mighty Pete on 2007-04-15
I'm glad you guys are enjoying the game. Feedback is good. Yes there is no single player yet. If we make one it will not be quick chances are. You can always play against the bots, They are very good. This is using a custom version of the Q3 engine. It should work on any computer that Quake 3 would work on though. Just like any other game if it does not work properly just turn down the eye candy a bit. Remember you can edit the config file to set any resolution with in reason. Quake 3 engine has some quarlks with some sizes.  There is also a panel inside where you can set things via a GUI but not all options are changeable there.

Lets the games begin :popcorn:

Your Pal

The Mighty Pete

---

### Post by jorgerosa on 2007-04-15
Yep, Mighty Pete, ive already played against Bots and they are better than me, so... I´ll NOT buy the game :-\" 
**Congratulations to all your team**, the game is just FANTASTIC, much better than commercial games around, all fits GREAT in the game: Multiplayer, design, graphics, maps (A MUST!), sounds, playbility, price... 5 STARS!!! Just one note: You could make the game less "for kids" type. *(Did i wrote it right?)* [-o< 
=D> =D> =D> =D> =D>
Comes in a good time: Many people run out from linux because: "Linux has no good games". (This has been someway true because software houses have $$$ interests.)

---

### Post by Mighty Pete on 2007-04-15
"Less of a kids game" 

Ya but I helped make it for my kids. There are lots of ultra violent / Adult only  games out there already. We are trying to make a fun game, not a violent game. Remember if we made it more adult chances are you could not download it or play it in Germany. They have some odd laws there, and since most of the guys on the team live there you can see why the game is what it is. 

Hopefully this is a breath of fresh air. 

Have fun.

Your Pal

The Mighty Pete

---

### Post by jorgerosa on 2007-04-15
Received!
*"Hopefully this is a breath of fresh air. Have fun."* - It sure is a breath of fresh air, 100% Original idea!
**Have fun??? Sure im having it. Lots of fun, man! Thx to you all.**
*"make it for my kids"* - Why do you have kids?!  ;-) 
*"There are lots of ultra violent / Adult only games out there already"* - Seriously: I also agree.

---

### Post by Kittens on 2007-04-15
I click on it from my applications list, but nothing happens.

:confused:

EDIT: The screen blinks, but that's it.

---

### Post by hikaricore on 2007-04-15
> **Kittens said:**
> I click on it from my applications list, but nothing happens.

:confused:

EDIT: The screen blinks, but that's it.

You may want to try running the game from a terminal window then post any error output that it gives.

Also check for direct rendering:

```
glxinfo | grep rendering
```

And letting us know what type of video hardware do you have might help too :)

---

### Post by brennydoogles on 2007-04-15
> **hikaricore said:**
> You may want to try running the game from a terminal window then post any error output that it gives.

Also check for direct rendering:

```
glxinfo | grep rendering
```

And letting us know what type of video hardware do you have might help too :)

I just tried to run the game in terminal with the WOP command, and when I did, the screen blinked a few times, my resolution went all crazy, and I could only see the top corner of my terminal window. I couldn't move my mouse, (otherwise I would have copied the output of my terminal), and I ended up having to Ctrl C and then restart X in order to get my compy back. I have an older Nvidia GeForce Titanium video card, and the output from 
```
glxinfo | grep rendering
```
is 
```
direct rendering: No
```
Any Advice??

---

### Post by hikaricore on 2007-04-15
Without direct rendering enabled, there is no chance of running WoP.
But there may be an easy fix for ya.

Your best bet would be to install and run envy for you Nvidia card:

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

It should automatically detect if your card is supported by any of the drivers availible for linux and install them for you.

---

### Post by brennydoogles on 2007-04-15
> **hikaricore said:**
> Without direct rendering enabled, there is no chance of running WoP.
But there may be an easy fix for ya.

Your best bet would be to install and run envy for you Nvidia card:

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

It should automatically detect if your card is supported by any of the drivers availible for linux and install them for you.

Thanks for the superfast reply... I am attempting to run envy now, i will post back with any changes!!

---

### Post by ceedubu on 2007-04-16
I seem to be having a bit of trouble getting this game to run.

It looks as if it installs correctly but when I try to run it (typing "wop" in the console) i get this error:

```
  ./wop-engine.i386: error while loading shared libraries: libvorbisfile.so.3: cannot open shared object file: No such file or directory 
```

I checked synaptic and it looks like libvorbisfile3 is installed on my system.

Oh yeah... my computer... a few specs:
[LIST]
[*]AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
[*]dual GeForce 7800 gtx - (SLI) - with the latest drivers.
[*]2 gigs ram
[*]Ubuntu Edgy Eft 64 bit version.
[/LIST]

Anyone else had this prob? Any info would be most appreciated as this game looks like it could be quite fun.

Thanks
C

---

### Post by hikaricore on 2007-04-16
```
ls -la /usr/lib/libvorbisfile*
```

should return something like this:

> 
-rw-r--r-- 1 root root 21400 2006-07-23 06:49 /usr/lib/libvorbisfile.a
-rw-r--r-- 1 root root   896 2006-07-23 06:49 /usr/lib/libvorbisfile.la
lrwxrwxrwx 1 root root    22 2006-11-23 03:37 /usr/lib/libvorbisfile.so -> libvorbisfile.so.3.1.1
_lrwxrwxrwx 1 root root    22 2006-11-23 03:37 /usr/lib/libvorbisfile.so.3 -> libvorbisfile.so.3.1.1_
-rw-r--r-- 1 root root 24864 2006-07-23 06:49 /usr/lib/libvorbisfile.so.3.1.1


If for some reason the softlink I underlined is missing, you can make it manually, but at your own risk.

**Note I may have a different version of libvorbis installed than you do.

---

### Post by ceedubu on 2007-04-16
i ran the command in the console and got these results. They are a bit different than yours.

> lrwxrwxrwx 1 root root    22 2007-04-13 23:51 /usr/lib/libvorbisfile.so.3 -> libvorbisfile.so.3.1.1
-rw-r--r-- 1 root root 27376 2006-06-30 13:35 /usr/lib/libvorbisfile.so.3.1.1

im not really sure what all that means...

Thanks for the quick response.

---

### Post by hikaricore on 2007-04-16
this line is a soft link to the main file:
lrwxrwxrwx 1 root root 22 2007-04-13 23:51 _/usr/lib/libvorbisfile.so.3_ -> libvorbisfile.so.3.1.1

this is the main library file. 
-rw-r--r-- 1 root root 27376 2006-06-30 13:35 /usr/lib/libvorbisfile.so.3.1.1

Due to the changing versions and names of some libraries, soft links are put in place to simplify the process
of programs looking for these libraries.  Without soft links, every time you updated any libraries, you would
need to recompile any software that needed them and change the calls in the source to the correct libraries.  :)

Anyway, sadly it looks like you have everything in place where it's needed.  I'm going to guess
the issue you're having is due to the nature of running 32 bit software in a 64 bit environment,
there are workarounds for this type of thing but I have 0 experience in said field.  >.<

Sorry, hopefully someone can come up with something more concrete for your issue.

---

### Post by brennydoogles on 2007-04-16
works great now!!

---

### Post by StarscreamD on 2007-04-16
I just tried this game. It was impressive for being free, but it ran horribly. The choppiness was almost unbearable. Or does it run like that for everyone? When I run Quake 3 or Unreal on my system with the graphics all the way up, it runs circles around this game when the graphics are down. I actually really dig the "Micro Machines" feel, and if I could get this to run better, I'd be stoked.

---

### Post by hikaricore on 2007-04-16
> **StarscreamD said:**
> I just tried this game. It was impressive for being free, but it ran horribly. The choppiness was almost unbearable. Or does it run like that for everyone? When I run Quake 3 or Unreal on my system with the graphics all the way up, it runs circles around this game when the graphics are down. I actually really dig the "Micro Machines" feel, and if I could get this to run better, I'd be stoked.

No it doesn't run like this for everyone.
This is probably an issue with your video card/drivers not being setup properly or at all.
Or it could be a cpu or memory issue.  You'll need to be a little more specific.

---

### Post by cyrsan on 2007-04-16
try tweaking setup -> system -> graphics to disable some eye candy in favor of performance. also, some linux users have problems with the map "kais trashmap" so check if other maps have the same performance issues for you.


@all: since the ubuntu forum discusses the game nearly as much as its own forum does, i'll crosspost my request here:

> let's assume there would be a mod in development, focusing on competitive players and league games, like osp/cpma for quake3. what features would you like to see in such a mod? (enemy models, referee commands, gameplay changes, etc..)
any opinion and feedback is welcome.

---

### Post by fruitsofherwomb on 2007-04-16
I love the art style to this game. I'm pretty impressed.

---

### Post by StarscreamD on 2007-04-16
Yeah for some reason now it's working better! Thanks guys.

---

### Post by Istonian on 2007-04-17
I love this game. When I switched to Ubuntu I was aorrying about gaming. So far either my games are native or are supproted by Wine or crossover linux.

---

### Post by Flaringo on 2007-04-27
I downloaded this game just now, but at once something in 3D is displayed (like the preview in the player setup screen), the game runs horrible. About 15 fps max, I'd say. I've tried re-installing it, I've set EVERYTHING possible to the lowest setting possible, and I see no noticable improvement. :(

Here is my glxinfo:
```
flaringo@flaringo:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 7800 GT/PCI/SSE2/3DNOW!
OpenGL version string: 2.1.0 NVIDIA 96.31
OpenGL extensions:
    GL_ARB_color_buffer_float, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_gpu_program_parameters, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_depth_stencil, GL_EXT_packed_pixels, 
    GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod, GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_sRGB, GL_EXT_timer_query, 
    GL_EXT_vertex_array, GL_HP_occlusion_test, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square, 
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fence, 
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program, 
    GL_NV_fragment_program_option, GL_NV_fragment_program2, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_filter_hint, 
    GL_NV_occlusion_query, GL_NV_packed_depth_stencil, GL_NV_pixel_data_range, 
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_texgen_reflection, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle, 
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3, 
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, 
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 
    GL_SGIX_depth_texture, GL_SGIX_shadow, GL_SUN_slice_accum

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x30 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x31 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x34 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x35 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x36 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x37 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x39 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x3b 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x3c 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x3d 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x3e 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x3f 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x41 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x43 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x44 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x45 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x46 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x47 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x48 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x49 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x4a 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x51 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x52 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x59 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x5a 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x5c 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x5e 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x5f 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x60 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x61 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x62 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x63 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x64 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x65 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x66 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x67 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x68 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x69 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x6a 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x6b 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x6c 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x6d 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x6e 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x6f 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x70 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x71 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x23 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x72 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x73 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x74 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x75 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x76 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x77 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x78 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x79 32 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x7a 32 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x7b 32 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x7c 32 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x7d 32 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x7e 32 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x7f 32 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x80 32 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x81 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x82 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x83 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x84 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x85 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x86 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x87 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 Ncon
0x88 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 Ncon
0x89 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x8a 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x8b 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x8c 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x8d 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x8e 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x8f 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 Ncon
0x90 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 Ncon
0x91 32 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x92 32 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x93 32 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x94 32 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x95 32 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x96 32 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon
0x97 32 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 Ncon
0x98 32 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 Ncon

```

Here's what glxgears prints out:
```
flaringo@flaringo:~$ glxgears
19976 frames in 5.0 seconds = 3990.460 FPS
22326 frames in 5.0 seconds = 4465.126 FPS
22256 frames in 5.0 seconds = 4450.591 FPS
X connection to :0.0 broken (explicit kill or server shutdown).

```

Is there anyone who knows of a possibe solution?

EDIT: Snap. Doesn't look like the native opengl games likes compiz. :(

---

### Post by StarscreamD on 2007-04-27
> **Flaringo said:**
> ...Doesn't look like the native opengl games likes compiz...
or Beryl.

---

### Post by hikaricore on 2007-04-27
Using beryl or compiz while trying to run other 3d applications has been mentioned before as problematic for most.  It's not impossible but it honestly just depends on your hardware.  Using the tools availible with both of these window managers it's very easy to enable and disable them in about 2 seconds.  I also mentioned this in my "Advice" sticky in this very forum.  :)

---

### Post by Flaringo on 2007-04-27
Weird thing is, other games like GLtron, ppracer, cube3d etc. runs perfectly fine in Compiz. Hmm, oh well.

---

### Post by Josey on 2007-04-28
nice game... played for hours tonight

---

### Post by justin whitaker on 2007-04-28
Just played this last night. 

First impressions: Battling around a kitchen is a bunch of very silly fun.
Second impressions: Wait, I'm dead already?

:) 

Put in a single player mode and more maps, box it, ship it!

---

### Post by 2dere on 2007-06-14
Okay, I downloaded this game around the first week the game was released and couldn't get the game to work. It'd go through the install fine but when it came to actually running the game I'd get nothing. Wasn't added to the app list, no shortcut, and equally nothing typing 'wop' in a terminal. I posted in this thread earlier and the attempted help didn't work. I downloaded this game again today because I really want to play it and the same thing has happened again. I'm guessing its got something to do with my computer but is there any reason I'd get no response after installing the game? I've followed all the advice in this thread and a couple of others, had all the settings that were needed that I've come across but I can't get a pulse for this game. Any ideas/help? Please?

---

### Post by hikaricore on 2007-06-14
> **2dere said:**
> Okay, I downloaded this game around the first week the game was released and couldn't get the game to work. It'd go through the install fine but when it came to actually running the game I'd get nothing. Wasn't added to the app list, no shortcut, and equally nothing typing 'wop' in a terminal. I posted in this thread earlier and the attempted help didn't work. I downloaded this game again today because I really want to play it and the same thing has happened again. I'm guessing its got something to do with my computer but is there any reason I'd get no response after installing the game? I've followed all the advice in this thread and a couple of others, had all the settings that were needed that I've come across but I can't get a pulse for this game. Any ideas/help? Please?

Honestly, **wop** from a terminal should work.  >.<

The only thing I can thing of is that you didn't run the installer with sudo.

```
sudo ./nameofinstaller.sh
```

So it wasn't able to make the symlinks to the game properly.

Do you get any errors from terminal when you try and run it with **wop**?

Also what type of hardware do you have, video drivers installed properly?

Can you run other 3d games?

---

### Post by johnny4north on 2007-06-14
the "world of Padman" finally has new maps for the little blue guys :D - [http://padworld.myexp.de/index.php?files=maps](http://padworld.myexp.de/index.php?files=maps)

---

### Post by 2dere on 2007-06-15
> **hikaricore said:**
> Honestly, **wop** from a terminal should work.  >.<

The only thing I can thing of is that you didn't run the installer with sudo.

```
sudo ./nameofinstaller.sh
```

So it wasn't able to make the symlinks to the game properly.

Do you get any errors from terminal when you try and run it with **wop**?

Also what type of hardware do you have, video drivers installed properly?

Can you run other 3d games?

Well I'm glad to see that it doesn't sound like a common problem. I did install via superuser, I don't get any errors expect being told that 'wop' could not be found. 
I'm sure I have my drivers installed properly because I can get Beryl going and as for other games, I can't tell you because this is the only gave I've tried installing on linux.

---

### Post by AndyCinDallas on 2007-07-26
Same problem here, although I didn't see anything on the WOP forum about using "sudo" when installing - just "sh installer.run" which worked - now I can't for the life of me get the game started. No links under Applications -> Games

When I do "wop" in the console I get "bash: wop: command not found"

Any way to create the symlinks manually, short of downloading the 550+ Mb file again? I'm almost a total newbie to Linux.

---

### Post by spekterx on 2007-07-26
> **AndyCinDallas said:**
> Same problem here, although I didn't see anything on the WOP forum about using "sudo" when installing - just "sh installer.run" which worked - now I can't for the life of me get the game started. No links under Applications -> Games

When I do "wop" in the console I get "bash: wop: command not found"

Any way to create the symlinks manually, short of downloading the 550+ Mb file again? I'm almost a total newbie to Linux.

sudo is usually used for installing things because not all directories can be accessed or written to/read from with just a normal user. sooo you'd be able to install something, but not fully.

also, downloading now, weeeeeee im excited :D

---

### Post by dmn_clown on 2007-07-27
> **hikaricore said:**
> Without direct rendering enabled, there is no chance of running WoP.
But there may be an easy fix for ya.

Your best bet would be to install and run envy for you Nvidia card:

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

It should automatically detect if your card is supported by any of the drivers availible for linux and install them for you.

or you can just start the game like ```
./wop-engine.i386 +set r_allowSoftwareGL 1
```

Just like any other q3 or ioq3 based game to allow the use of the free drivers.

---

### Post by Sayers on 2007-07-27
It seems the site is down ...

---

### Post by NewJack on 2007-07-27
Downloaded this last night.  Thanks to AI for his quick howto, worked without a fault.  

One problem I have is the game is not seeing any servers.  What am I doing wrong?  Do I have to manually open a port for this to happen, if so how do I do that?  I am a linux multiplayer noob, so go easy on me :).

---

### Post by AndyCinDallas on 2007-07-27
> **spekterx said:**
> sudo is usually used for installing things because not all directories can be accessed or written to/read from with just a normal user. sooo you'd be able to install something, but not fully.

also, downloading now, weeeeeee im excited :D
Ahhhh, I see - ok, I reinstalled it (using the sudo command) and now the shortcut shows up under Games. Woo :D

---

### Post by BigSilly on 2007-07-28
I've just downloaded this for my Ubuntu and installed it using the sudo sh command as described - WOW! Amazing stuff, and it's free! It's an incredibly accomplished piece of gaming, and I'd like to extend my thanks to the coders for this tremendous game, and also for bringing it to Linux. It runs so sweet on my fairly simple Ubuntu setup. :D

Can I ask though, is there an easy way to play this on your own rather than playing online straight away? I'm not that great at online shooters, and I'd really like to practice a bit offline before I take the plunge into the arena! I want to get good at this, and I don't fancy the utter ridicule I'm bound to face at the hands of the experts!

Thanks for your help.

---

### Post by burt_57 on 2007-07-28
Ok I am downloading it now........ will see what the hype is all about.
it is downloading at @365 KB/sec.
Will let you know what I think of it soon.
Ok done in 25 or so minutes.
Now looking to how to install.

---

### Post by BigSilly on 2007-07-28
> **BigSilly said:**
>  Can I ask though, is there an easy way to play this on your own rather than playing online straight away? I'm not that great at online shooters, and I'd really like to practice a bit offline before I take the plunge into the arena! I want to get good at this, and I don't fancy the utter ridicule I'm bound to face at the hands of the experts!

Sorry to bump this question up, but if anyone can help I'd be most grateful. Also, when I do eventually get good at this game, what's the etiquette for joining a battle? Can I just join any map and get shooting, or do the players have to approve you before you can play? I'm pretty sure these are daft questions, but I'm just not versed in online playing. I'm used to solo-play on games consoles.

Thanks again.

---

### Post by AndyCinDallas on 2007-07-28
When you start the game, hit "Multi" in the menu, which will take you to the server screen. Click "Create" at the bottom to create your own server - then select a map. Once you've selected the map, look at the right - there's an option to select bots. Add as many as you like, along with their respective skill-level, click "Back" and start the game.

Alternatively, once the game starts, hit "Esc" which brings up a menu and add a few bots ;)

Online games - dunno yet, as I'm playing solo first to get used to it.

---

### Post by BigSilly on 2007-07-28
Thanks for that Andy. Done and done. Now I can start to explore the controls. I expect I might be a while!

Thanks. :)

---

### Post by AndyCinDallas on 2007-07-28
My first time successfully helping someone - yay :D

---

### Post by Duck2006 on 2007-09-18
> **hikaricore said:**
> Download: [http://padworld.chillerlan.net/index.php?files=main](http://padworld.chillerlan.net/index.php?files=main)
Trailer: [http://www.youtube.com/watch?v=IeOoKrqK2F8](http://www.youtube.com/watch?v=IeOoKrqK2F8)
Homepage: [http://www.worldofpadman.com/](http://www.worldofpadman.com/)

This game looks awesome, and all I can think at this moment is that if this is a 550mb
april fools joke, I'm going to kill someone's dog.  :)

Borrowed from linux-gamers.net:

Thanks will try that gram out

---

