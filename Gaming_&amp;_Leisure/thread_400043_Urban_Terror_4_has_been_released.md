---
title: "Urban Terror 4 has been released"
date: 2007-04-03
forum: Gaming &amp; Leisure
---

### Post by bvanaerde on 2007-04-03
They announced that it would be released on April the first... so I wasn't sure if they were joking or not.
The files can be downloaded at the homepage: [http://www.urbanterror.net](http://www.urbanterror.net)

For information about how to install it in Linux, visit the [forums]("http://www.forums.urbanterror.net/index.php/topic,2496.0.html").

---

### Post by Mateo on 2007-04-03
thanks, i think i'll give it a shot.

---

### Post by Mateo on 2007-04-03
those instructions assume you own quake 3... what if you don't?  on the site it says it works if you don't have quake 3.  not sure how to set everything up...

---

### Post by bvanaerde on 2007-04-03
> **Mateo said:**
> those instructions assume you own quake 3... what if you don't?  on the site it says it works if you don't have quake 3.  not sure how to set everything up...

You need to install ioUrbanTerror first, which can be found on the [homepage.]("http://www.urbanterror.net/news.php") (the first two sentences on the website describe what you have to do)
Just pick a zip to download... the Linux files are inside ;-)

---

### Post by Mateo on 2007-04-03
yeah, but it doesn't tell you where to place the files in the zip.  that's what i'm unsure of.

---

### Post by Mateo on 2007-04-03
I got it.  for those who don't have quake 3 do this.

```
sudo mkdir /usr/local/games/UrbanTerror
```

then unzip the contents of the Linux folder in the iourbanterror-whatever.zip package here.   just the contents of the linux folder, you don't need the rest.  then after you get the big file, unzip it to the same /usr/local/games/UrbanTerror folder.  Keep the qtut4 directory, don't ditch it.  Then do:

```
sudo chmod +x /usr/local/games/UrbanTerror/ioUrbanTerror.i386
```

to make it executable. then create a launcher for that file.

---

### Post by fordp on 2007-04-04
Can this not go into the repo's ??

Who do we have to ask to get it into Universe or whatever ?

The Ubuntu need to embrace and encourage  projects like [http://www.ioquake3.org/](http://www.ioquake3.org/).

I will have a go at getting this game working over easter.

I used to play it when it was just a mod ;)

---

### Post by Mateo on 2007-04-04
> **fordp said:**
> Can this not go into the repo's ??

Who do we have to ask to get it into Universe or whatever ?

i would like to know this as well.  there aren't very many games in the Repos.  I'd help out if I knew how to get them there.

---

### Post by racoq on 2007-04-04
Finally my favorite FPS arrived to Linux. Now i can play it natively on Ubuntu. This is a great addition to Linux community. People should spread this, in my opinion, now we can run natively one of the best FPS that exists (IMO).
America's army, ActionCube and others don't even come close to Urban terror. That's a shame that the guys of Counter Strike, don't develop a native version for linux. We then would could say that we have best FPS running natively on Linux, and people could easily switch to Linux. Although with this release of Urban Terror, we will see our community of gamers grow, because of this. I strongly advise any MOTU to take responsibility on maintaining this game in the repository's. 
Really we all will benefit from this release.

---

### Post by redsp1der on 2007-04-04
I can't extract the Linux folder to the UrbanTerror folder I get this error

Extraction not performed

You don't have the right permissions to extract archives in the folder "/usr/local/games/UrbanTerror"

how do I get the right permissions?
and while Im asking newbie questions what is a launcher and how do I create one?

---

### Post by Mateo on 2007-04-04
> **redsp1der said:**
> I can't extract the Linux folder to the UrbanTerror folder I get this error

Extraction not performed

You don't have the right permissions to extract archives in the folder "/usr/local/games/UrbanTerror"

how do I get the right permissions?
and while Im asking newbie questions what is a launcher and how do I create one?

assuming you are using Archive Manager, use sudo.  Do this:

```
sudo file-roller
```

then find the zip file, wherever you put it.  then you should be able to extract to that directory.

let me know if you have any more problems.

---

### Post by redsp1der on 2007-04-04
that really didn't work.
after I enter "sudo file-roller" I get the archive manager window but almost everything is grayed out 

and as soon as I click on anything i get this error in the terminal:

(file-roller:8583): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.


man I just wanted to play a cool linux game why does installing have to be so complex?
I can't get this one to install and I just tried Padman and I can't figure out how to install it either.

---

### Post by Mateo on 2007-04-04
did that error message prevent you from doing anything?  sometimes you get error message in the terminal but you can usually ignore them.

try this instead:

```
sudo tar -cf whatever.zip /usr/local/games/UrbanTerror
```

don't get frustrated, you are really close to having this game and then you'll be able to enjoy it.

---

### Post by redsp1der on 2007-04-05
> redsp1der@redsp1der-desktop:~$ sudo tar -cf ioUrbanTerror_1.0 .zip /usr/local/games/UrbanTerror
Password:
tar: .zip: Cannot stat: No such file or directory
tar: Removing leading `/' from member names
tar: Error exit delayed from previous errors
redsp1der@redsp1der-desktop:~$ sudo file-roller

(file-roller:4966): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.
redsp1der@redsp1der-desktop:~$ 


still no luck.
I don't understand how it was so easy for you and why my system doesn't work the same.

---

### Post by Mateo on 2007-04-05
it's not any different really. It's just hard to communicate what to do over this.  do you happen to have any type of instant messager?  I could walk you through it easier that way.

I have no idea why file roller will not open with sudo for you.

I messed up on that other command, sorry!  It should be:

```
sudo unzip ioUrbanTerror_1.0.zip
```

this should create a new folder.  get into it by typing

```
cd WHATEVER-THE-FOLDER-IS-CALLED
```

then type

```
ls
```

which should show you a few more folders, one for linux, windows, and mac.  you want the linux one of course.  type:

```
cd WHATEVER-THE-LINUX-FOLDER-IS-CALLED
```

then you just need to move the files.  like this:

```
sudo mv * /usr/local/games/UrbanTerror
```

---

### Post by daverave999 on 2007-04-08
I didn't realise there was a thread about UrT-I have to add my 2p in and say this is probably my favourite game of all time. I've played since 2.6 IIRC and am ecstatic that the standalone version has brought more people back into it.

I would urge anyone who likes FPS games to give this a try because it is excellent, and so far I have seen no difference between running it on Windows and running it on Linux.

Anyone got any pointers how to set up XQF to find servers for this? I'm doing fine using the in-game browser but I'd like to try XQF to see if it's any good.

---

### Post by FoolsGold on 2007-04-08
This has got to be the most fun FPS I've played in fricking AGES. Congrats to the UT team for making it function not only as a standalone game, but also making it work perfectly in Linux.

And it's all free!

---

### Post by RotoGrip on 2007-04-08
I can not log into servers. The game loads then cuts out saying "failed to load battle eye client" Even though in the setup screen it shows being active.

Using Ubuntu 6.10

---

### Post by daverave999 on 2007-04-08
> **RotoGrip said:**
> I can not log into servers. The game loads then cuts out saying "failed to load battle eye client" Even though in the setup screen it shows being active.

Using Ubuntu 6.10[This thread]("http://www.forums.urbanterror.net/index.php/topic,7393.0.html") might help?

---

### Post by sgardne on 2007-04-09
You can get it via torrent from gameupdates.org: [http://www.gameupdates.org/index.php?search=urban+terror](http://www.gameupdates.org/index.php?search=urban+terror)

Also, you can get lots of other legal game torrents here. It's by far the best way to get patches or whatever for games.

-s

---

### Post by MadMan2k on 2007-04-09
great game! Tremulous shares now the linux FPS throne with it :)

---

### Post by RotoGrip on 2007-04-09
If i were to get a server for this game would there be enough of an intrest? I can get a good price for a server. Also i see alot of servers online but they come with high ping to boot. Id be willing to get a dedicated server if people were going to use it. Im really enjoying this game.

---

### Post by afljafa on 2007-04-10
Being a somewhat antisocial git when it comes to gaming - is there a single player option to this game?

---

### Post by FoolsGold on 2007-04-10
> **afljafa said:**
> Being a somewhat antisocial git when it comes to gaming - is there a single player option to this game?

Start Urban Terror, bring down the console (~ key), type in

/bot_enable 1

Close console, click Start Server, setup whatever options you like but make sure the map you play is "Abbey", otherwise the bots will be totally useless due to lack of waypoints. When ready, start the server.

Select your team and join, bring down the console, type in

/addbot chicken

Repeat command for any many times as bots you want added. Their skill varies, sometimes they're great, sometimes they'll tk you without mercy. Official bot support was dropped, but the commands remain in case you really want them.

---

### Post by Cirdan7 on 2007-04-10
edit: Didn't realize this thread was 3 pages :P...

You can do...

"sudo chmod 777 /usr/local/games/UrbanTerror"

....but that is a hackish way of doing it.

---

### Post by bvanaerde on 2007-04-11
> **afljafa said:**
> Being a somewhat antisocial git when it comes to gaming - is there a single player option to this game?

Not really, no.
There is a little bit of bot support, as mentioned above me, but there are no real single player missions.
Fragging somebody is better when you know it's a *real* person :D

---

### Post by paparappa on 2007-04-12
I don't get it, when i've extracted the files from the zip 
ioUrbanTerror what do I do then? Do I chmod  ioUrbanTerror.i386 and then make a launcher on the desktop? But i have to download the other ZIP as well right? I mean the  zip with size of 550 mb. 
When I've chmodded ioUrbanTerror.i386 and i doubleclick it it happens nothing. No reaction. Is there a detailed HOWTO SomewherE?

---

### Post by paparappa on 2007-04-12
I solved it... For anyone else this is what to do:

- make a dir called 'urt' or any other name
- put in 'urt' the 'q3ut4' dir from UrbanTerror40_full.zip
- put in 'urt' what is inside the Linux dir from ioUrbanTerror_1.0.zip
- put in 'urt' the 'BattlEye' dir from ioUrbanTerror_1.0.zip
- "chmox +x ioUrbanTerror.i386" in 'urt' to make it executable

Make a launcher on the desktop :)

---

### Post by mrazster on 2007-04-12
[SIZE="6"]OR..!!![/SIZE]you can just do it as the guys says in this post: *_[http://ubuntuforums.org/showpost.php?p=2426024&postcount=4](http://ubuntuforums.org/showpost.php?p=2426024&postcount=4)*_

Works perfectly for me...really love this game..:guitar:

---

### Post by paparappa on 2007-04-13
I get this error where it sais "Can't load BattlEye Client" and in Urban Terror forums it told me to

sudo chcon -t texrel_shlib_t /home/drew/Linux-i386/BattlEye/*.so

in terminal well then i get an error message that look like this:

"chcon: can't apply partial context to unlabeled file"

What the heck is unlabeled file!? And how do i label?

---

### Post by dannyxxx69 on 2007-04-13
I'm new to Linux and don't understand hot to do the  last two steps:

* chmod +x ioUrbanTerror.i386
* ./ioUrbanTerror.i386 

how do I do the chmod thing?

---

### Post by sgardne on 2007-04-13
> **dannyxxx69 said:**
> I'm new to Linux and don't understand hot to do the  last two steps:

* chmod +x ioUrbanTerror.i386
* ./ioUrbanTerror.i386 

how do I do the chmod thing?
These are console commands. Make sure you're in the same directory as the file indicated. Then type the commands into the terminal followed by the [enter] key.

---

### Post by dannyxxx69 on 2007-04-13
I tried that and i get this:
chmod: missing operand after `+/usr/local/games/UrbanTerror/ioUrbanTerror/Linux-i386/ioUrbanTerror.i386'
Try `chmod --help' for more information.
:(

---

### Post by sgardne on 2007-04-13
> **dannyxxx69 said:**
> I tried that and i get this:
chmod: missing operand after `+/usr/local/games/UrbanTerror/ioUrbanTerror/Linux-i386/ioUrbanTerror.i386'
Try `chmod --help' for more information.
:(
Are you putting a space between the +x and the filename? so it would be 

chmod [space] +x [space] filename [enter]

---

### Post by dannyxxx69 on 2007-04-13
I typed that but nothing is happening in the terminal and nothing has changed in the folder.

---

### Post by sgardne on 2007-04-13
> **dannyxxx69 said:**
> I typed that but nothing is happening in the terminal and nothing has changed in the folder.
Linux doesn't give you confirmation if the command was successful. Sounds like it worked. You should be able to start the game now by typing ./ioUrbanTerror.i386

---

### Post by mrazster on 2007-04-13
> **dannyxxx69 said:**
> I tried that and i get this:
chmod: missing operand after `+/usr/local/games/UrbanTerror/ioUrbanTerror/Linux-i386/ioUrbanTerror.i386'
Try `chmod --help' for more information.
:(

**Dany:** go to your file location / right click / properties / permissions / and click "Allow this file to run as a program" / close and doubble click on the file....and geeeet reeady to ruuuuumble...!!!

---

### Post by dannyxxx69 on 2007-04-15
:D  thanks you guys rock, i'm getting around 30fps with a AMD 1GHz  with 640 mb RAM and a Nvidia 6200.:D

---

### Post by fakie_flip on 2007-04-17
> **redsp1der said:**
> that really didn't work.
after I enter "sudo file-roller" I get the archive manager window but almost everything is grayed out 

and as soon as I click on anything i get this error in the terminal:

(file-roller:8583): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.


man I just wanted to play a cool linux game why does installing have to be so complex?
I can't get this one to install and I just tried Padman and I can't figure out how to install it either.


use gksu with gui apps not sudo

gksu file-roller

---

### Post by fakie_flip on 2007-04-17
What other good games are there for Linux? So far I have these.

Wolfenstein Enemy Territory and RTCW
Sauerbraten
Frozen Bubble
Armagetronad
Neverball
Unreal Tournament 2004

---

### Post by sgardne on 2007-04-17
> **fakie_flip said:**
> What other good games are there for Linux? So far I have these.

Wolfenstein Enemy Territory and RTCW
Sauerbraten
Frozen Bubble
Armagetronad
Neverball
Unreal Tournament 2004
America's Army

---

### Post by noerrorsfound on 2007-04-17
> **fakie_flip said:**
> What other good games are there for Linux? So far I have these.

Wolfenstein Enemy Territory and RTCW
Sauerbraten
Frozen Bubble
Armagetronad
Neverball
Unreal Tournament 2004
[http://warsow.net/](http://warsow.net/)
I was trying to think of a good description of Warsow but ended up just taking this from Wikipedia:
> The very competitive gameplay of War§ow focuses heavily on movement and trickjumping. Players use many tricks/bugs found in the Quake engine including strafe-jumping, double jumping and rocket jumping. There are also tricks like the wall jump and dash that were available in the Unreal series. The various movements all combine to add an extra dimension to the gameplay; as the player's proficiency at moving increases, they will be able to collect health, armour and weapons more quickly, more effectively overpower enemies with their speed, and of course compete on the various Race maps that the game offers. While it is possible to play a good game without knowing how the physics work, it will severely impede one's ability to play against seasoned veterans.

The learning curve is higher because of the tricks you have to learn, but there are various guides and also a wiki:
[http://warsow.net/wiki/index.php?title=Movement](http://warsow.net/wiki/index.php?title=Movement)

Tricks in the game:
[list][*]Dash
[*]Wall Jump
[*]Strafejump
[*]Air Strafe / Bunny hopping
[*]Ramp Slide
[*]Double Jump
[*]Double Dash Jump
[*]Rocketjump
[*]Rocket Walljump
[*]Plasma Climb
[*]Plasma Slide
[*]Circle Jump
[*]Circle Dash Combo
[*]Ramp Jumping
[*]Surfing[/list]

---

### Post by Perfect Storm on 2007-04-18
Installation guide for Urban Terror: [http://gaming.gwos.org/e107_plugins/content/content.php?content.68](http://gaming.gwos.org/e107_plugins/content/content.php?content.68)

---

### Post by Mateo on 2007-04-18
> **paparappa said:**
> I get this error where it sais "Can't load BattlEye Client" and in Urban Terror forums it told me to

sudo chcon -t texrel_shlib_t /home/drew/Linux-i386/BattlEye/*.so

in terminal well then i get an error message that look like this:

"chcon: can't apply partial context to unlabeled file"

What the heck is unlabeled file!? And how do i label?

did you (or anyone else) ever figure this out?

---

### Post by scotty2hott2k on 2007-04-18
world of padman is another must game for linux imo.

---

### Post by fakie_flip on 2007-04-18
> [QUOTE]Quote:
Originally Posted by paparappa  
I get this error where it sais "Can't load BattlEye Client" and in Urban Terror forums it told me to

sudo chcon -t texrel_shlib_t /home/drew/Linux-i386/BattlEye/*.so

in terminal well then i get an error message that look like this:

"chcon: can't apply partial context to unlabeled file"

What the heck is unlabeled file!? And how do i label? 

> did you (or anyone else) ever figure this out?[/QUOTE]

You don't need to do that command. Infact, that command is not included with Ubuntu because Ubuntu does not have SELinux (Security Enhanced Linux). What you need to do is replace two files that are patched. Read and download them here.

[http://www.urbanterror.net/news.php?item.142.3](http://www.urbanterror.net/news.php?item.142.3)

Let me know if this helps

---

### Post by fakie_flip on 2007-04-18
What other good games are there besides first person shooters? I think I have 10 or more FPS games in Ubuntu now, and I'd like to get some other types of games. These are the games I have already.

Frozen Bubble
Armagetron Advanced
Planet Penguin Racer
Neverball

_FPS games_
Unreal Tournament 2004
Sauerbraten and Cube
Wolfenstein Enemy Territory
Return to the Castle Wolfenstein
Alien Arena 2007 (downloading)
World of Padman
Nexuiz
Urban Terror
and I downloaded a few others that were mentioned in this thread, but haven't tried them yet.

---

### Post by fakie_flip on 2007-04-18
> **sgardne said:**
> America's Army

I read that America's Army was discontinued for Linux. There are newer version, but they are available for Windows and not Linux. I could get an old version of America's Army possibly. I played it a while back. Do you have any other suggestions?

---

### Post by daverave999 on 2007-04-21
Regarding XQF (game browser), people may find [this]("http://www.forums.urbanterror.net/index.php/topic,7710.0.html") useful.

---

### Post by noerrorsfound on 2007-04-21
> **fakie_flip said:**
> I read that America's Army was discontinued for Linux. There are newer version, but they are available for Windows and not Linux. I could get an old version of America's Army possibly. I played it a while back. Do you have any other suggestions?
The latest version they released for GNU/Linux is 2.5. I've heard that many people still play it but for some reason it always says my internet connection may be down so I can't log in.

---

### Post by rcatman on 2007-04-22
I've been experiencing a problem connecting to servers and starting my own server.

I've finally isolated the problem.

Everything works fine if I execute the program from the command line.

But when I use a launcher I made from the desktop, i get a 'failed to start BattlEye' error. I can't connect to a game or launch a server. Should I pass the program an argument in the launcher so it knows where to look for BattleEye? 

GREAT game by the way. I love it. It's just like counter strike. I get a great frame rate too! I run an athlon amd xp 2000+ with 512mb ram and a Geforce3 Titanium 200 vid card.

---

### Post by bvanaerde on 2007-04-22
> **rcatman said:**
> Everything works fine if I execute the program from the command line.

But when I use a launcher I made from the desktop, i get a 'failed to start BattlEye' error. I can't connect to a game or launch a server. Should I pass the program an argument in the launcher so it knows where to look for BattleEye? 

It seems to be a known bug...
When scrolling down on [this page]("http://urbanterror.net/e107_plugins/content/content.php?content.5") to the "errors" section, you see this:
> "Couldn't load default.cfg", "invalid gamefolder", "Failed to load BattlEye" or going to q3 menu instead of Urban Terror
    In case of ioUrbanTerror: Your q3ut4-folder, BattlEye-folder and ioUrbanTerror.exe are not in the same folder. BattlEye error can also be caused by having win2k/winME/win98 and not yet having updated the .dll's (see UrT mainpage). In linux, it could be that your server is missing a certain package. In a terminal go to the BE folder and type 'ldd BEServer_i386.so' and see if it outputs something missing. Then install that :)

    In case of Q3A: Your q3ut4-folder, PB-folder and quake3.exe are not in the same folder or you are not starting with +set fs_game q3ut4 (explained at bottom).
On the forums, there's [a thread]("http://www.forums.urbanterror.net/index.php/topic,7453.msg97698.html") about a similar problem, but on Win2K.
It may be relevant though.

**EDIT**: on the [urbanterror homepage]("http://urbanterror.net/news.php"), scroll down to "Windows 98/Me/2000 & Linux users: Critical update for BattlEye".
Hope this will help :)
There are some files you need to overwrite, in order to solve the problem.

---

### Post by bravemosquito on 2007-04-22
I have a problem with running UrT4. The game starts normally in full-screen, menus and navigating through them are ok but when I start server with a random level the game closes itself, drops to desktop (GNOME) and changes my resolution to lower + the mouse cursor is not moving :confused:

---

### Post by rcatman on 2007-04-23
Hey bvanaerde,
I went to the Urban Terror homepage  and downloaded BEClient_i386.so and BEServer_i396.so thenmoved them over the old copies in the BattlEye folder. That appears to have fixed the 'failed to start BattlEye' problem I was having earlier. I just got done playing on a server. Thanks for the tip/news.

---

### Post by fakie_flip on 2007-04-23
> **bravemosquito said:**
> I have a problem with running UrT4. The game starts normally in full-screen, menus and navigating through them are ok but when I start server with a random level the game closes itself, drops to desktop (GNOME) and changes my resolution to lower + the mouse cursor is not moving :confused:

How are you running the game? You should be running it from the same directory the binary is in. Have you tried reinstalling it?

---

### Post by bravemosquito on 2007-04-23
> **fakie_flip said:**
> How are you running the game? You should be running it from the same directory the binary is in. Have you tried reinstalling it?

Installed using FAQ from the site. Downloaded UrbanTerror40_full.zip, extracted to Quake 3 dir and ran with this command line for launcher:
**/usr/local/games/quake3/quake3 +set fs_game q3ut4**

where q3ut4 is Urban Terror's dir.

Sometimes game runs fine only one map and after change crashes. Sometimes crashes when loading the map

---

### Post by Mateo on 2007-04-24
> **bvanaerde said:**
> It seems to be a known bug...
When scrolling down on [this page]("http://urbanterror.net/e107_plugins/content/content.php?content.5") to the "errors" section, you see this:

On the forums, there's [a thread]("http://www.forums.urbanterror.net/index.php/topic,7453.msg97698.html") about a similar problem, but on Win2K.
It may be relevant though.

**EDIT**: on the [urbanterror homepage]("http://urbanterror.net/news.php"), scroll down to "Windows 98/Me/2000 & Linux users: Critical update for BattlEye".
Hope this will help :)
There are some files you need to overwrite, in order to solve the problem.


This doesn't work for me.  Same error.  I even tried making them executable.  No difference whatsoever.

---

### Post by psoulocybe on 2007-04-24
I got everything installed and it works.... however I can only get around 25 fps.
Tried lowering settings and nothing changed.

i get around 6000 fps on glxgears

Fiesty 64bit
A64 3000+
512 mb memory
Nvidia 5500

i run steam in windows w/ around 70fps in most mp games, and would like to fix this

---

### Post by Phalanx747 on 2007-06-20
In my case the gameplay is choppy. The ping is ok (under 30) and the fps is at about 50/60. I don't recall what the fps was before, but up to about a week ago the gameplay was fine (i.e. completely smooth and not choppy). I have no idea what happened to change that, though. I didn't install anything, let alone any drivers of some sort.

I tried to reinstall the ATI videocard drivers, but this didn't really work since apt-get said it already was installed. I removed urban terror's installation *and* the configuration files (~/.q3a) and reinstalled. To no avail, it would seem. I even lowered all of the graphic settings. This helped a little, but it still works worse than it did a week ago.

Any thoughts on this matter?

---

### Post by bvanaerde on 2007-06-20
That's weird...
Maybe something big is running in the background... type "top" in the CLI, and check if there's something that's eating your CPU.

---

### Post by tolstoybikeboy on 2007-06-21
i'd like to know the same answer...i follow your steps..but it says i don't have permission to extract to this directory... :( i'm a newb...could you please help

---

### Post by Phalanx747 on 2007-06-23
Well, the problem seems to have dissipated after a reboot. Which is wierd, since I had previously rebooted several times. Maybe one of the updates fixed it or something. I dunno, but it works again! :P

---

### Post by bvanaerde on 2007-09-08
I noticed that somebody made an install script for Urban Terror.
Check this topic at the UrT forums:
[http://www.forums.urbanterror.net/index.php/topic,8165.0.html](http://www.forums.urbanterror.net/index.php/topic,8165.0.html)

It couldn't be simpler:
[LIST]
[*]Download the install script
[*]Make it executable *(chmod +x urt40-linux-installer.sh)*
[*]Run the script *(./urt40-linux-installer.sh)*
[/LIST]

---

### Post by Depressed Man on 2007-10-27
The script seems to error out with some message about gnome-nautilus.

---

### Post by fatbuttlarry on 2009-06-12
These instructions say to use "sudo" in Ubuntu to install this game.  I simply extracted it to a folder in my home directory.

Then I right-clicked on **ioUrbanTerror.i386** and made it Executable.  Game ran first try.

If game servers don't list you haven't done anything wrong, it's a bug.  To get game servers to list just close and re-open the game.  Click "Play Online" and then "Get New List" just once and the servers should show up.

Cool game, I recommend it for any CounterStrike fans or Ubuntu users that want to try new games.

-Tres

---

