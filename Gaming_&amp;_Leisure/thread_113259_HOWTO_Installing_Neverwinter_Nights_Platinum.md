---
title: "HOWTO: Installing Neverwinter Nights Platinum"
date: 2006-01-06
forum: Gaming &amp; Leisure
---

### Post by leech on 2006-01-06
Easy Howto.

**1:** Enable the Universe repository; Open up Synaptic Package Manager, System -> Administration -> Synaptic Package Manager. Enter in your Password. Click on Settings, and select Repositories. Click Add. Then put check marks in the box for Community maintained (Universe) and while you're at it, may as well put one in Non-free (Multiverse)

**2:** After clicking OK on both dialogs, click Search and type in unshield. It will show three packages, just double click on unshield and it will ask you if you also want to mark libunshield, which is required. Click Mark. Click Search again and type in msttcorefonts.  Double click it to queue the package and click Apply.  This will download and install both Unshield and the fonts required by Nevewinter Nights.  Unshield is required by the installer.

**3:** Download the script **(attached)**.  Extract it, then right click on the script in the File Manager and select properties. Then select the Permissions tab. On the Owner line, put a check in Execute. Click close.

**4:** Double click on the install-nwn.sh and select Run in Terminal.  
[COLOR="Red"]Note for Edgy Eft users![/COLOR] You must first change the /bin/sh symbolic link.  To do this simply run ```
sudo dpkg-reconfigure dash
``` Select No, and it'll change your shell to bash.  After installing the game, you'll probably want to switch back to using dash, as to not mess up any advantages of speed that dash may provide.  Run the command again and select Yes.

**5:** A terminal window will open, asking if you're installing the Platinum or Diamond edition.  Then it will ask for CD or DVD version. Select the proper one, then enter. Then it asks for the cdrom path. On Ubuntu, this will be /media/cdrom for the first drive. Next is the install directory. By default this is /usr/local/games/nwn. Change this if you'd like. If you're going to install there, you will need to use sudo. If you don't have multiple people using your computer, then just put it in /home/<username>/nwn. Next it asks for the current patch version that is located in the users home directory (1.66 is the newest patch.  There is a 1.67beta4, but the installer doesn't directly support that yet).  

Important: When the script asks "Do you wish for the script to mount the CD (Y/n)" you'll want to choose NO. This is because Ubuntu will automatically mount the CDs for you when you insert them. For the group, it is safe enough to just hit enter (since you should already be in the users group.)  If you'd like, you can also change group to games.  If you do this, then only users in the games group can play it.  This of course could be useful if you have children with their own accounts on your computer, and you ground them from games.  Just make sure that you add yourself the the group games.

Last but not least, start inserting the CDs. It starts off with disk 2. (Hint: You'll know when to hit enter on the script, because Nautilus will open up a window showing what is on the CD/DVD you just inserted. This shows that it is mounted and the script can do it's thing) To eject a CD/DVD, right click on the icon on the desktop and select eject.

6: There is no step number 6

**7:** After installation, if you want an icon either on the desktop or on the menu you will need to edit the nwn start up script. Just ```
gedit ~/nwn/nwn
``` and add a line ```
cd /home/<username>/nwn
```

Mine looks like this;

```
#!/bin/sh

# This script runs Neverwinter Nights from current directory

cd /home/leech/nwn
export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0

# If you do not wish to use the SDL library included in the package, remove ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=./lib:./miles:$LD_LIBRARY_PATH
export LD_PRELOAD=./nwmovies.so
./nwmain $@
```

**7a**: For a desktop Icon, simply right click on the desktop, and select Create Launcher. Enter the Name (Neverwinter Nights), You don't really need Generic name or Comment. For the command you can either Browse to /home/<username>/nwn and select the nwn file. For the Icon, you can click on the button that says No Icon, and then browse to /home/<username>/nwn and select nwn.ico.

**7b:** For a menu entry. Select Applications -> System Toos -> Applications Menu Editor. Then in the left hand column, select Games. Then press the New Entry button. The rest is exactly like installing the desktop Launcher above. Then quit the Menu Editor and you will have a Neverwinter Nights menu entry under Applications -> Games.

**8:** Now load the game up. After the initial boot screen, you will be asked for the CD-Keys. They are printed inside the front cover of your manual. You will have to enter the key for the Original Neverwinter Nights twice. I have no idea why, but it asks for it twice. The others are only required once.

***Please note that this is for the Platinum or Diamond Editions of Neverwinter Nights.  For the Original, Gold, Shadows of Undertide or Hordes of the Underdark there is a graphical installer located at [http://icculus.org/~ravage/nwn/](http://icculus.org/~ravage/nwn/)***

**Update:**Now supports Diamond edition and 1.67 patch.  Thanks go to the creator of the Install Script.

**Neverwinter Nights with Movies!**

Get the latest version [**here.**]("http://home.roadrunner.com/~nwmovies/")

Bink video player is [**here.**]("http://www.radgametools.com/down/Bink/BinkLinuxPlayer.zip")

1) Copy nwmovies-latest.tar.gz into your nwn directory and untar it with 'tar xfvzp nwmovies-latest.tar.gz' 

2) Install development packages for SDL and ELF, also you'll need gcc, etc.  ```
sudo apt-get install build-essential libelfg0-dev libsdl1.2-dev libsdl-gfx1.2-4 libsdl-gfx1.2-dev libsdl-mixer1.2
```

3) Run the nwmovies_install.pl with './nwmovies_install.pl /usr/lib/libSDL-1.2.so.0'  (as a side note, if you installed nwn to /usr/local/games/nwn with sudo, you'll also need to run the script with sudo.)

4) Edit the nwn script.  Put the line 'export LD_PRELOAD=./nwmovies.so' right above the line that says './nwmain $@'

5) Copy BinkPlayer.zip into your nwn folder and unzip it with 'unzip BinkPlayer.zip'  then run 'chmod +x BinkPlayer'

Now run nwn as you normally would, the first time that you run it, will create a cache for your movies, as the text instructs, just run it a second time and you should have movies within the game!

*Additional Note:* You do not need to remove the ./lib from the nwn script as it says.  As a user has discovered, that will break the movies.  Not sure why this is, since we specified to use the System SDL library, but there must be some incompatibilities.

Hope this is helpful.

Leech

P.S.  This was originally posted in [http://ubuntuforums.org/showthread.php?t=77466&page=3&highlight=neverwinter]("http://ubuntuforums.org/showthread.php?t=77466&page=3&highlight=neverwinter") I created a new thread for it since it's been asked about a few times and this is easier to find.

Update:  Placed the fix for Edgy users in a more obvious place.

---

### Post by FizDev on 2006-01-06
Wow, this seems much less complicated than what Bioware was saying to do... I'll go and try right away! =)

I've tried and it works perfectly! It runs as smoothly as in Windows... maybe even more. Thanks for this howto.

---

### Post by leech on 2006-01-06
Not a problem :D

Leech

---

### Post by J-B on 2006-01-06
Well this would have been nice to know yesterday!  Lol, I followed the instructions in the Bioware forums which forces you to decompress each cd manually, and install everything manually.  I spent about eight hours and several tries on it total before I got it working.   Oh well, good tutorial, hope it helps some people out there.  

fizdev-  NWN actually does run more smoothly under Ubuntu, at least for me.  I've noticed a marked difference from my windows install.

---

### Post by leech on 2006-01-06
Maybe we should either have this as a sticky or entered into the Ubuntu Games list.  This howto has been in this forum for quite some time but it was buried in that other thread.  That hurts that it took 8 hours.  This way doesn't take much time at all.

Leech

---

### Post by J-B on 2006-01-06
[QUOTE=leech]Maybe we should either have this as a sticky or entered into the Ubuntu Games list.  This howto has been in this forum for quite some time but it was buried in that other thread.  That hurts that it took 8 hours.  This way doesn't take much time at all.

Leech[/QUOTE]

Agreed.  Sticky this, it's a great tutorial.

---

### Post by Zodiac on 2006-01-06
Would this be the same for the Diamond edition as well???

---

### Post by leech on 2006-01-06
I'm not sure.  The diamond edition is the same as the platinum, except it has the Kingmaker module.  Does it have a separate CD for that?

Leech

---

### Post by Zodiac on 2006-01-06
Not sure... it arrives tomorrow ;)... 

I was under the impression however that it was all on one DVD...

---

### Post by leech on 2006-01-06
[http://nwn.bioware.com/forums/viewtopic.html?topic=461746&forum=72](http://nwn.bioware.com/forums/viewtopic.html?topic=461746&forum=72)

I think this thread pretty much sums up the current situation.  Hopefully Bioware will figure out a way around this.  To think I probably would have bought the Kingmaker CD, except that I haven't even had time to complete the original campaign, let alone Shadows of Undertide and Hordes of the Underdark.

Leech

---

### Post by Maelgwyn on 2006-01-10
I tried this, and got as far as the script, but when I got to the point where I needed to define the cdrom path, when I entered the info and pressed **enter**, it just closed the script.

---

### Post by leech on 2006-01-11
Did it give you any sort of error?  

> INVALID DEVICE! Please check the device and try again

That's what it gave me if I entered the wrong device.  I have /media/cdrom0 and put in /media/cdrom which gave me the error.

Could also be that the creator of this script has changed it from the one I have, somehow breaking it.  

I posted it at [http://thefnords.org/install-nwn.sh](http://thefnords.org/install-nwn.sh).  

Leech

---

### Post by Maelgwyn on 2006-01-11
nope, no error :S It just closed...

---

### Post by leech on 2006-01-11
Try the one from my website, it works here without problems.  

Leech

---

### Post by Maelgwyn on 2006-01-11
[quote=leech]Try the one from my website, it works here without problems.[/quote]

that's [http://thefnords.org/install-nwn.sh]("http://thefnords.org/install-nwn.sh")  ?

---

### Post by leech on 2006-01-11
That's the one.  Hosted by your's truely.

Leech

---

### Post by blacklantern on 2006-01-11
*laughs* I knew I'd manage to screw it up. When I get past step 6, the terminal window closes, and after I insert the DVD, nothing happens other than the contents of the CD being shown in the file browser. the directory /usr/<username>/games/nwn doesn't exist. Does the script create it, or should I do it beforehand?

edit:

Nevermind. Reading is fundamental. :P

---

### Post by leech on 2006-01-12
Now the big question is, for everyone who has it working...  when are we going to play?  :D  My server is currently running the Pool of Radiance module, which is great for 3-6 players.  In essence you start out in town and the town council has several jobs that you go do.  Pretty good module, based off the old Advanced Dungeons and Dragons one.  

Of course if you have any other suggestions for a module, I'd be glad to serve it up.  I was thinking that we could get groups to sign up for a particular game of it, and have the time set up, so that we could play that module weakly or whatever.  I could probably have a saved session afterwards and so host several different games at different times.

What does everyone think of that?  

Leech

---

### Post by Sandlst on 2006-01-12
I just wanted to drop by and say Thanks Leech for the great guide! I havent gotten it working yet because I think my cdrom is dying-a lot of the time it shows only the title of the cd being loaded but no data on it unfortunatly :P. I also wanted to add that, for the above posters who say the terminal exits with no error, you could try to open up a new terminal, click edit, then current profile, and under the 'title and command' tab, at the very bottom you can set the terminal to stay open when it normally would close, and thus hopefully display an error you can see to solve when you try again.

EDIT: just in case someone else has the above cd-reading problem, it sometimes works to unmount the cd manually (I have mine setup to auto-eject with the button) and re-enter it.

---

### Post by leech on 2006-01-13
Not a problem, though maybe you should save the thanks until it's working :D  Fortunately for you, new DVD/CD-ROMS aren't all that expensive.  

That's really very strange that people are having the terminal actually closing on them.  Thanks for the advice for that.

Leech

---

### Post by mr_mop on 2006-01-13
Yes thanks for the guide, not tried it yet, but will be shortly.

I recommend this brand new custom module.  It only requires NWN, the 2 expansions and CEP.  You don't need any other downloads.
[http://www.ferhan.org/](http://www.ferhan.org/)

They also run their own Nordock server which I frequent and its quite fun.  Quite a bit of DM interaction.
[http://nordock.ntfm.org/](http://nordock.ntfm.org/)

---

### Post by chronusdark on 2006-01-13
excellent how to im installing now 

this really simplifys the whole process

---

### Post by leech on 2006-01-14
[QUOTE=mr_mop]Yes thanks for the guide, not tried it yet, but will be shortly.

I recommend this brand new custom module.  It only requires NWN, the 2 expansions and CEP.  You don't need any other downloads.
[http://www.ferhan.org/](http://www.ferhan.org/)

They also run their own Nordock server which I frequent and its quite fun.  Quite a bit of DM interaction.
[http://nordock.ntfm.org/](http://nordock.ntfm.org/)[/QUOTE]

The Ferhan website isn't exactly friendly to Firefox is it?  I just tried giving it a look over and it wasn't usable at all (could be because I'm using the Dapper Firefox, but who knows.)

Leech

---

### Post by chronusdark on 2006-01-14
alright leech i ordered the diamond compliation should be here tuesday.

we should organize some offical ubuntuforums nwn games what do ya say?

---

### Post by chronusdark on 2006-01-14
[QUOTE=leech]The Ferhan website isn't exactly friendly to Firefox is it?  I just tried giving it a look over and it wasn't usable at all (could be because I'm using the Dapper Firefox, but who knows.)

Leech[/QUOTE]
 right click on the middle section of the page and select this frame only 
and you can read it alright

---

### Post by mr_mop on 2006-01-14
[QUOTE=leech]The Ferhan website isn't exactly friendly to Firefox is it?  I just tried giving it a look over and it wasn't usable at all (could be because I'm using the Dapper Firefox, but who knows.)

Leech[/QUOTE]

I'm looking at it now, on Windows firefox and seems Ok.  Breezy firefox is also Ok.  I wonder what's different in Dapper?
Anyway, its the module thats more important right :)

---

### Post by leech on 2006-01-14
[QUOTE=chronusdark]alright leech i ordered the diamond compliation should be here tuesday.

we should organize some offical ubuntuforums nwn games what do ya say?[/QUOTE]

I agree.  I don't know how many have tried logging into my server, but it's been running solid since I set it up.  

Leech

---

### Post by leech on 2006-01-14
[QUOTE=chronusdark]right click on the middle section of the page and select this frame only 
and you can read it alright[/QUOTE]

That worked, though not exactly a good solution...  So this is a Persistent World?  

We could all join up on this, if that's what everyone would prefer.  I was thinking more along the lines of a group just going through modules, but this works too.

The problem with the page could be due to Firefox 1.5, Dapper, or my own screwed up set up.  Not sure.  Works fine in Konqueror too.  Go figure.

Leech

---

### Post by chronusdark on 2006-01-15
hey im up for just going through modules do we want to have a DM or just play regular?

while the persistant world idea is really cool i play neverwinter nights to avoid the persistant world type games (world of warcraft)

---

### Post by leech on 2006-01-16
[QUOTE=chronusdark]hey im up for just going through modules do we want to have a DM or just play regular?

while the persistant world idea is really cool i play neverwinter nights to avoid the persistant world type games (world of warcraft)[/QUOTE]

I agree with you on this, I prefer just the modules.  The one I'm running right now doesn't require a DM, but we could put up a poll on what modules people would like to play.  I wouldn't mind doing the Dragon Lance Adventures.  Though back when I first tried it out they felt very amatuerish, since the Dialogs were just horrible.  But I think in the updates of the modules, a lot of that was fixed.

Leech

---

### Post by Elvish Legion on 2006-01-20
Check out [http://dreunoctem.com/](http://dreunoctem.com/)

I used to play there a bit

---

### Post by Elvish Legion on 2006-01-20
How do I change the resolution? It tries to resize my screen and I get mode not supported...is it in the config.ini?

---

### Post by leech on 2006-01-21
It is in nwn.ini.  It is line 8 and 9.

Leech

---

### Post by sir_cheats_a_lot on 2006-01-26
I'm having problems with this method.   at the end of install process i get the following message:  
"Testing for ImageMagick convert
convert not found!
convert is a part of the Image Magick tools, used here to make the nwn.iso a Linux friendly nwn.xps
Skipping image conversion"

i get it with both the diamond edition(when it works) and the platinum edition.   when i load neverwinter nights, i just get prompted for my keys, and it never gets any farther.  it just keeps prompting for the keys over and over again.    any suggestions?

---

### Post by leech on 2006-01-27
Have you tried installing Imagemagick?  I always thought it was installed by default.  'sudo apt-get install imagemagick'

Leech

---

### Post by sir_cheats_a_lot on 2006-01-28
no didn't install Imagemagick, but in anycase i got Neverwinter nights installed and working, but it runs kinda slow. my previous problem was i just installed it in the default location which for some reason you don't have permissions to edit files, so i just changed the install location.  also text on the game seems to be kinda mis-aligned...do you think Imagemagick would correct this or would this be a problem caused by my graphics card(ati 9200 128MB AGP)?
*note*
I am in the process of migrating from windows, so please be patient with me.

---

### Post by leech on 2006-01-28
Well, I would install imagemagick anyhow, since it's used by a lot of things.

As far as the text goes, I don't know, I don't have an ATI card, though I do know if you don't have certain fonts installed, you will get no text at all.  Make sure you have msttcorefonts installed.

( sudo apt-get install msttcorefonts )

Leech

---

### Post by Jedeye on 2006-01-31
Worked great until I got to the part where it needed the cd key... apparently I lost the manual but was able to hold onto the box/cd fold out book. perhaps it will turn up around the same time I find where I backed up my old characters...

---

### Post by RaiSuli on 2006-02-02
I'm getting this error message when the script tries to access disk 2 on my cdrom drive:

Cannot read "/media/cdrom/disk2.zip".
Please check that disk 2 is in /media/cdrom
Press Enter to continue.

I've got two dvd/cd drives, I've tried changing the path to cdrom0 and cdrom1, doesn't work. Nautilus displays the contents, but that's just it. :-| 

Any ideas?

---

### Post by impact201 on 2006-02-13
Does anyone have the install script saved that they could mirror for me?  It seems the install-nwn.sh has been removed from the host, and I need to reextract the game :-|  For some reason, installing from the Bioware download pack isn't working for me, but the script worked great last time I did it.  Hopefully someone kept it around...

Thanks!

---

### Post by leech on 2006-02-14
I still have it, and I just tried the link in the first post and it still works.  Try [http://thefnords.org/install-nwn.sh](http://thefnords.org/install-nwn.sh)

Leech

---

### Post by psychosushi on 2006-02-22
For me for some reason fonts don't work at all. I can open the game, but when I see the window, none of the buttons have any test in them. Also, it requires me to enter the cd-key every time I get into the game. The cd-key works, but I can't stay in the game.

---

### Post by leech on 2006-02-22
For the fonts, it is due to lack of the msttcorefonts package.  Make sure you have this installed.

In fact, I should smack myself for not including that in the howto.  I just added that in, so hopefully anyone else with this problem will know how to fix it.

For the CD-Key issue, I have a guess.  Check to make sure that your nwn is writable by the user that you loaded the game with.  It saves the keys themselves in nwncdkey.ini.  This is the file that will need to have write permissions.  If you have multiple users that all use this same game yet have different accounts, I would make the file and save directories be part of the games group, and make sure that the people you want playing the game to be in the games group.  If you need help with that, I will explain it later on.

Leech

---

### Post by leech on 2006-02-22
[QUOTE=RaiSuli]I'm getting this error message when the script tries to access disk 2 on my cdrom drive:

Cannot read "/media/cdrom/disk2.zip".
Please check that disk 2 is in /media/cdrom
Press Enter to continue.

I've got two dvd/cd drives, I've tried changing the path to cdrom0 and cdrom1, doesn't work. Nautilus displays the contents, but that's just it. :-| 

Any ideas?[/QUOTE]

My first question would be, do you have the DVD or CD version?  I only have the CD version myself, so I'm not sure exactly how different the DVD version is.  disk2.zip is on my Disk 2 of the game for the CD version.  You could try checking all the CDs and see if for some reason you were unlucky and your disks are just mislabled.  

Leech

---

### Post by psychosushi on 2006-02-22
actually, I have the msttcorefonts package installed, that doesn't help. Interestingly, verything, including the fonts worked when I installed neverwinter in my home directory instead of /usr/local/games. I don't know why that would fix the fonts problem, but anyway, everything works now.

Sasha

---

### Post by leech on 2006-02-22
Not quite sure why the fonts would not work, but as I said before, everything will work if you have the proper permissions.  I should add to the HOWTO information on if you have a multi-user system, though I don't know if nwn is even programmed to work that way, since it just uses the one saves folder, and I think that is what would be most imporant as far as a multi-user setup.

Leech

P.S. According to this site [http://icculus.org/~dolson/mdkxp/](http://icculus.org/~dolson/mdkxp/) you can use a script for multi-user set ups.

---

### Post by sir_cheats_a_lot on 2006-02-23
it was a permissions issue...i had the same problem with missing fonts and having to enter keys over and over again.   as soon as i installed it into a folder that i had the permissions to write in the problem was solved.   however, i do wounder why it was even allowed to install in a folder that the user couldn't write to. :-k

---

### Post by drgreborn on 2006-02-28
I have a problem. I can't seem to run the game. I did everything as stated yet it still can't boot.

---

### Post by Coelocanth on 2006-03-05
I don't have Platinum, but I have the original NWN and both SoU and HotU (all bought when they were released). Any reason this wouldn't work to get them installed?

Thanks for any answers you can provide.

(Forgive me if this is a dumb question, but I'm a noob at Linux).

---

### Post by leech on 2006-03-06
I think the installers you want for those would be at [http://icculus.org/~ravage/nwn](http://icculus.org/~ravage/nwn)

Leech

---

### Post by sharperguy on 2006-03-07
ok, i didn't follow the instructions here because i wasn't sure if it would work phor seperate bought disks. I installed via a windows install.

Anyway when i try to play the whole system freezes and im not usre if it my graphics card or the game.

I am using Radeon 8500.

Not sure how compatible it is with linux.

---

### Post by leech on 2006-03-08
[QUOTE=sharperguy]ok, i didn't follow the instructions here because i wasn't sure if it would work phor seperate bought disks. I installed via a windows install.

Anyway when i try to play the whole system freezes and im not usre if it my graphics card or the game.

I am using Radeon 8500.

Not sure how compatible it is with linux.[/QUOTE]

Could be your video drivers.  The 8500 should be covered by the radeon or ati driver that is built into X.org.  Sorry, but my experience with ATI cards under linux is very limited.  Someone else hopefully will know.  I know Nwn even worked on the Matrox Parhelia's first openGL drivers for linux, so it should work with the ATI DRI driver that has been in the making for many years.

Leech

---

### Post by sharperguy on 2006-03-09
well i followed the instructions for installing the ATI drivers. After which i could not play it at all! Though now (not sure what i did) it works w/o crashing but _very_ slowly and stuttery.

---

### Post by leech on 2006-03-09
Run from a terminal.  ```
glxinfo |grep direct
```  It should say "direct rendering: yes"  If not, that would be your problem.  

So does this mean you're using the fglrx drivers?  I wish someone else with that card would speak up here.  It's much harder to trouble shoot something when you don't have that hardware, especially since ATI's driver situation is a mess.

Leech

---

### Post by sharperguy on 2006-03-09
your right it was no

any idea how i wol enable it?

ok: 

when i run sudo dpkg-reconfigure xserver-xorg and select ati the game opens but very stuttery

however

if i select fglrx it says "failed to initialise graphics"

hmm...

---

### Post by sharperguy on 2006-03-10
can anyone help me then?

Dont ask how but i got it working :) 

so whens the next game?

---

### Post by leech on 2006-03-11
Glad to hear you got it working.  Maybe someone should set up a page that lists when games will be played.

Leech

---

### Post by Bokonon on 2006-03-14
I got the diamond version working (less kingmaker) by following the directions on the neverwinter forums (linked above).&#12288;&#12288;Now I just need some free time to play it.

Thanks for the posts here--everything helped.

EDIT: Got Kingmaker working easily by following the same guide (on Bioware's forum, linux general support).  One more nail in Window's coffin!

---

### Post by ~KoN~ on 2006-04-03
Used your install guide Leech, its brilliant. The first guide that actually worked for me! :-D

Except, that i can't see any text. Yes, i installed the font as you instructed, but i don't know if it worked. Seeing as its not displaying the text i figure something went wrong somewhere, any advice on how to fix it up?

btw, just in case it makes a difference, my graphics card is a GeForce FX 5200 and as far as i can tell i installed the graphics drivers correctly.

Anyway, thanks to anyone for any help i get.

~KoN~

---

### Post by psychosushi on 2006-04-04
To get the fonts working in NWN install it in your home directory and not in /usr or /usr/local. There appear to be some premissions issues.

Sasha

---

### Post by Bokonon on 2006-04-04
[QUOTE=psychosushi]To get the fonts working in NWN install it in your home directory and not in /usr or /usr/local. There appear to be some premissions issues.

Sasha[/QUOTE]

I got it working in /usr/local/games/nwn but I had to chmod -R everything.  Probably easier just to install it in your home directory.  Since I am the only user on my machine, that is exactly what I plan to do next time.

NWN2 comming soon?  ](*,)

---

### Post by glotz on 2006-04-04
[QUOTE=J-B]Agreed.  Sticky this, it's a great tutorial.[/QUOTE]

Now it's stickied, how aboyt wicky it? [https://wiki.ubuntu.com/Games](https://wiki.ubuntu.com/Games)

Don't have an account there myself. That's where it needs to be.

---

### Post by ~KoN~ on 2006-04-04
[QUOTE=Bokonon]but I had to chmod -R everything[/QUOTE]
How do i do that? I assume its quicker than a re-install . . . :-k 

[QUOTE=psychosushi]To get the fonts working in NWN install it in your home directory[/QUOTE]
I'll give this a go if no-one explains chmod to me.

Also, is there a CEP linux install script for the CEP installer (which i have downloaded (also re-installing NWN on Windows incase i need to copy)) or do i just copy over the CEP files? The update, well i can just do the same as for the CEP.

~KoN~

---

### Post by psychosushi on 2006-04-05
[QUOTE=~KoN~]How do i do that? I assume its quicker than a re-install . . . :-k 


I'll give this a go if no-one explains chmod to me.

Also, is there a CEP linux install script for the CEP installer (which i have downloaded (also re-installing NWN on Windows incase i need to copy)) or do i just copy over the CEP files? The update, well i can just do the same as for the CEP.

~KoN~[/QUOTE]
 
cd /path-to-nwn-directory/nwn
sudo chmod -R *

Sasha

---

### Post by franklee on 2006-04-06
Guys and Gals, my Laptop is an Acer Aspire with a Turion 64bit chip and 512meg of ddr....my problem is that my graphics are run by onboard SIS....up to 128 meg of ram can be designated to my graphics output. This has led to Ubuntu installing in the default VESA mode available at 1024-768 resolution. Im wondering if installing NWN is worth the time, with only onboard graphics. It runs ok in Lamedoze but I REFUSE to use M$.

So...err....any opinions?

---

### Post by leech on 2006-04-06
Which Sis chip is it?  Firstly, edit your xorg.conf ```
sudo gedit /etc/X11/xorg.conf
```  Do a search for vesa and change ```
Driver     "vesa"
``` into ```
Driver     "sis"
```

That will at least give you better 2D desktop.  The problem is, most Sis chipsets don't have 3D support.  If you go to this page, [http://www.winischhofer.at/linuxsisvga.shtml](http://www.winischhofer.at/linuxsisvga.shtml) it'll explain everything you need to know about Sis chipsets under Linux (and probably a lot of stuff you didn't need to know :D )

Leech

---

### Post by leech on 2006-04-06
[QUOTE=glotz]Now it's stickied, how aboyt wicky it? [https://wiki.ubuntu.com/Games](https://wiki.ubuntu.com/Games)

Don't have an account there myself. That's where it needs to be.[/QUOTE]

It doesn't look like it's stickied.  I need to update it soon.  I'll add NWMovies to it, and installing the CEP to it as well.  

Maybe what I need to do is change it so that installs in /usr/local/games/nwn, which is where it should be.  

Though that means I have to re-install it again...  guess that's not too bad.  

Leech

---

### Post by leech on 2006-04-06
[QUOTE=~KoN~]How do i do that? I assume its quicker than a re-install . . . :-k 


I'll give this a go if no-one explains chmod to me.

Also, is there a CEP linux install script for the CEP installer (which i have downloaded (also re-installing NWN on Windows incase i need to copy)) or do i just copy over the CEP files? The update, well i can just do the same as for the CEP.

~KoN~[/QUOTE]

There is, it's located at [http://liflg.org/?catid=6&gameid=65](http://liflg.org/?catid=6&gameid=65)  I think I need to add this to the HOWTO as well as the Movies and Hardware Cursor.  Just haven't had the time to do so.  

Leech

---

### Post by franklee on 2006-04-08
Cheers Ears.

I gedit the xorg.conf and discover there isnt one....haha how weird is that??

---

### Post by K.Mandla on 2006-04-09
Just a quick thank-you to the OPer. This was far easier to install than the Bioware instructions, and call me crazy, but I do think the Linux version runs faster than the Windows version.

I should mention that I didn't have any luck with the automatic download and install of the client and update. I ended up downloading them separately and putting them into a nearby directory, and that did the trick. But aside from that slight detour, everything installed exactly as you described.

Thanks again!

---

### Post by l0c0dantes on 2006-04-14
How Do you update the gold version?

---

### Post by Mookawaka on 2006-04-15
Are there any known issues for running NWN in Ubuntu online with custom HAK packs and override files?

---

### Post by l0c0dantes on 2006-04-15
W00t, I got it all patched up

Anyone know of any good noob friendly online servers?

And I have no Idea mookwaka

---

### Post by leech on 2006-04-17
[QUOTE=Mookawaka]Are there any known issues for running NWN in Ubuntu online with custom HAK packs and override files?[/QUOTE]

None that I know of.  You just install the hak packs just like you would in Windows.  The folders are all laid out the same, as far as I recall.

Leech

---

### Post by leech on 2006-04-17
[QUOTE=l0c0dantes]How Do you update the gold version?[/QUOTE]

If I recall, the Gold Edition is just Neverwinter Nights + Shadows of Undertide.  Whereas the Platinum Edition is Neverwinter Nights + Shadows of Undertide + Hordes of the Underdark.

You'd basically have to get a copy of Hordes of the Underdark and then run the installer from [http://www.liflg.org](http://www.liflg.org)

Leech

---

### Post by leech on 2006-04-17
[QUOTE=K.Mandla]Just a quick thank-you to the OPer. This was far easier to install than the Bioware instructions, and call me crazy, but I do think the Linux version runs faster than the Windows version.

I should mention that I didn't have any luck with the automatic download and install of the client and update. I ended up downloading them separately and putting them into a nearby directory, and that did the trick. But aside from that slight detour, everything installed exactly as you described.

Thanks again![/QUOTE]

I think I may know the problem behind that one.  I attempted to install it via sudo and it did the same thing.  The problem was that it downloads it to ~/ which is the variable for the user's home directory.  So if you run it with sudo, then ~/ is actually /root/.  If you run it as your normal user it'll be /home/<username>/ where it looks for the patch.  It doesn't always download it to where it then looks for it.  

Leech

---

### Post by timHEMIwalker on 2006-04-17
I tried this HOWTO for neverwinter nights gold edition, and it worked pretty sweet until disk 2 where i had a problem with some language .zip file or something. in any case, i hopped over and tried the bioware walkthrough and i got the game running, but my issue is that when i enter my CD key at the opening of the game. it says that it is incorrect, or invalid or some nonsense like that. and i can be a simpleton at times, but i am sure that i entered it correctly. i mean really, i checked, double checked, and triple checked. i got it right from the inside of my manual, and i don't understand why it isn't working. is it maybe looking in the wrong place to verify my CD key? do i have any idea what i'm talking about? the answer the the latter question is probably not. actually no. i'm brand spankin new to linux, but i'm giving it a shot. help me out? thanks a bunch.

---

### Post by zgerrz on 2006-04-19
What is the exact name of the file/script used to run the game after installation? I installed the game in /home/user/nwn, but when I open that folder, I can't find anything that looks like a startup script for the game. I used the DVD install option as well.

---

### Post by leech on 2006-04-19
[QUOTE=timHEMIwalker]I tried this HOWTO for neverwinter nights gold edition, and it worked pretty sweet until disk 2 where i had a problem with some language .zip file or something. in any case, i hopped over and tried the bioware walkthrough and i got the game running, but my issue is that when i enter my CD key at the opening of the game. it says that it is incorrect, or invalid or some nonsense like that. and i can be a simpleton at times, but i am sure that i entered it correctly. i mean really, i checked, double checked, and triple checked. i got it right from the inside of my manual, and i don't understand why it isn't working. is it maybe looking in the wrong place to verify my CD key? do i have any idea what i'm talking about? the answer the the latter question is probably not. actually no. i'm brand spankin new to linux, but i'm giving it a shot. help me out? thanks a bunch.[/QUOTE]

This howto is specifically for the Platinum Edition.  For the Gold edition what you'll want to do is download the installer (graphical even!) from [http://icculus.org/~ravage/nwn/](http://icculus.org/~ravage/nwn/)

I'll put this on the original post, since I think you're not the only one to ask this.  That page also includes installers for the original, and the two expansion packs.  So even if you have the Gold Edition (which is the Original and Shadows of Undertide) you can still use the installer for Hordes of the Underdark if you have that Expansion Pack as well.

Leech

---

### Post by leech on 2006-04-19
[QUOTE=zgerrz]What is the exact name of the file/script used to run the game after installation? I installed the game in /home/user/nwn, but when I open that folder, I can't find anything that looks like a startup script for the game. I used the DVD install option as well.[/QUOTE]

Step #7 states that it is simply 'nwn'  I do need to clean it up a bit.  So in your case, it will be /home/user/nwn/nwn.

Leech

---

### Post by zgerrz on 2006-04-19
```
zgerrz@ubuntu:~$ /home/zgerrz/nwn/nwn
bash: /home/zgerrz/nwn/nwn: No such file or directory

```

I don't know why there's nothing there. Is the installer script supposed to close itself when it's done without any warning? I thought it was strange that after installing for awhile the script just closed without saying that it was finished installing. Just wondering if that might explain something.

---

### Post by leech on 2006-04-20
The end of the script should state > PASSED: ambient directory exists
PASSED: data directory exists
PASSED: music directory exists
FAILED: override directory missing
Add "cd /home/leech/nwn" to "/home/leech/nwn/nwn" to be able to run Neverwinter Nights from anywhere. You may also want to add a symbolic link to it from a bin directory, or somewhere else in your PATH.
Enjoy!
Testing for ImageMagick convert...
Making nwn.xpm...

Though I think the last message on the check where it says FAILED: override directory missing, is due to a bug in the installer, it said that it couldn't find the patch that I had it download.  I'll figure out a workaround for that.  

Leech

---

### Post by leech on 2006-04-20
Ok, apparently there is a problem with the script.  I'm not sure how exactly he has it set up, but you basically have to download the patch, then tell it where it is, otherwise the patch will not be applied, and it will give an error saying that it cannot find it.  I emailed the author of the script so hopefully we can get this problem fixed.  Hell, I wish I could program, I'd take the loki installer and update it so that it worked with the Platinum Edition, and maybe even the Diamond Edition as well.

Leech

---

### Post by zgerrz on 2006-04-21
Yeah, if we get this problem sorted out that would be great.

I was wondering where the hell the installer is downloading all these patches to on my hard disk?

---

### Post by martzgfx on 2006-04-21
Hello guys,
just tried (many, many times) to install and run Neverwinter Platinum religiously following instructions as per Leech's HOW-TO guide, to no avail.

Installation goes fine, but when I try to run the game (bash# ./nwn), I get that same error all the time:

./nwn: line 12: ./nwmain: cannot execute binary file

I did add the extra line "cd /home/*user*/nwn" in nwn with pico, also did the ./fixinstall, well I tried them all. Even tried Bioware Linux resource files and patches! :sad: 

I have Ubuntu Breezy (5.10) installed on a Powermac G4 AGP - and I have been using NWN Platinum on DVD (WIN version). Could something be missing, or I simply cannot install it on a PPC architecture?  :confused: 

Thanks in advance!

**::: martzgfx :::**

---

### Post by leech on 2006-04-22
It's because you're on the PPC architecture.  The binary would have to be completely different for it to run on a PPC.  

Leech

---

### Post by leech on 2006-04-22
[QUOTE=zgerrz]Yeah, if we get this problem sorted out that would be great.

I was wondering where the hell the installer is downloading all these patches to on my hard disk?[/QUOTE]

It should just download it to wherever you ran the script from.  I ran mine from my /home/leech directory, and that is where the patch is located.  I know that the auto-download of the patch works, it's just looking for it in the wrong area, because it always says that the file does not exist, unless you run the script a second time, then tell it to not download it, and then tell it to find the patch in ~/ and it will work.  

The problem really lies in the script itself not knowing where it downloaded the patch to.  I haven't received a reply from the author of the script yet.  Here's hoping that this can be worked out.

Leech

---

### Post by zgerrz on 2006-04-22
[QUOTE=leech]It should just download it to wherever you ran the script from.  I ran mine from my /home/leech directory, and that is where the patch is located.  I know that the auto-download of the patch works, it's just looking for it in the wrong area, because it always says that the file does not exist, unless you run the script a second time, then tell it to not download it, and then tell it to find the patch in ~/ and it will work.  

The problem really lies in the script itself not knowing where it downloaded the patch to.  I haven't received a reply from the author of the script yet.  Here's hoping that this can be worked out.

Leech[/QUOTE]
Well I figured out a way around the installer's error. I searched my computer to find where the patches were installed, and they actually ended up in my /tmp folder. So, I copied them to three different places. The folder where I ran the script from, the folder where I installed the game (/home/zgerrz/nwn), and the patch folder within the nwn folder (/home/zgerrz/nwn/patch).

I don't know which folder helped the installer find the patches more easily, but  it worked! One of these areas helped the installer complete the installation, and now everything runs beautifully. If the installer can't be fixed soon, at least it should be noted that copying over these patches to these directories has fixed the problem for me.

---

### Post by leech on 2006-04-24
I did make a change stating that you had to download the patch first, before running the script to fix the problem with the auto-download.  The problem is, the new script was created with makeself, so it's not just plain text.  Otherwise I could probably modify the script to look for the patch in the right place myself.  I am looking into changing the old script to support both the 1.66 patch, perhaps the 1.67b4 patch as well.  So that it will auto-download and install.

My other thoughts were to create a Loki installer for it.  The only problem is my programming skills suck (I can do Hello World, and that's about it!)

Leech

---

### Post by leech on 2006-04-28
I've now contacted Brian Whisler, who created the installation script that is now in the Howto.  He's working on a Universal installer, so that it should support all variations of Neverwinter Nights.  He's also working on getting the installer to set up the Movies and Hard ware mouse as well.  

Maybe we can get a debian package made, one that just has Unshield as a dependency, then runs the install script, plus installs everything to compile the movies library, etc.  

Leech

---

### Post by Nikusan on 2006-04-29
[QUOTE=leech]If I recall, the Gold Edition is just Neverwinter Nights + Shadows of Undertide.  Whereas the Platinum Edition is Neverwinter Nights + Shadows of Undertide + Hordes of the Underdark.

You'd basically have to get a copy of Hordes of the Underdark and then run the installer from [http://www.liflg.org](http://www.liflg.org)

Leech[/QUOTE]

I've got the plain old versions of nwn, sod and hotu. Should I install with the graphical installers at [http://icculus.org/~ravage/nwn/](http://icculus.org/~ravage/nwn/) ? After they are installed what is the best way to update them? Will the updaters at [http://www.liflg.org/?catid=6&gameid=65](http://www.liflg.org/?catid=6&gameid=65) work for me? :confused:

---

### Post by leech on 2006-04-29
[QUOTE=Nikusan]I've got the plain old versions of nwn, sod and hotu. Should I install with the graphical installers at [http://icculus.org/~ravage/nwn/](http://icculus.org/~ravage/nwn/) ? After they are installed what is the best way to update them? Will the updaters at [http://www.liflg.org/?catid=6&gameid=65](http://www.liflg.org/?catid=6&gameid=65) work for me? :confused:[/QUOTE]

Yeah, that's exactly what you should use :D  

Leech

---

### Post by Nikusan on 2006-04-30
[QUOTE=leech]Yeah, that's exactly what you should use :D  

Leech[/QUOTE]

Awesome! I'm up and running with 1.67 + the fix from the bioware forum. Quick question: I'm trying to install the module [Tale of a Mage]("http://nwvault.ign.com/View.php?view=Modules.Detail&id=4129").
I created the ~/nwn/tlk dir for ToM_2.tlk but when I try to load the module in game it complains about a missing required custom tlk file. Is this a problem with my install or with the module?

---

### Post by leech on 2006-04-30
I recall at one point in time that it's an issue with case sensitivity, and looking into the logs, I am right.  What you'll have to do is take all the files that this module requires, and make all capital letters lower case. 

Unfortunately it requires the CEP 1.52 package, which apparently it's been a while since  installed any new modules, because I still have an older version of CEP installed in linux.  But once you change the filenames to all lower case, it should run fine.

Leech

---

### Post by Nikusan on 2006-04-30
[QUOTE=leech]I recall at one point in time that it's an issue with case sensitivity, and looking into the logs, I am right.  What you'll have to do is take all the files that this module requires, and make all capital letters lower case. 

Unfortunately it requires the CEP 1.52 package, which apparently it's been a while since  installed any new modules, because I still have an older version of CEP installed in linux.  But once you change the filenames to all lower case, it should run fine.

Leech[/QUOTE]

I had a feeling that could be it! Keep on rocking :)

---

### Post by Fallom on 2006-06-13
I have the Diamond DVD placed in the drive /media/dvdrecorder but when I give that location to the script it says "INVALID DEVICE!"

What's the deal?

---

### Post by weasel fierce on 2006-06-21
I tried using the script, but when mounting the cd as it appears in the filesystem (/media/cdrom0) it doesnt find the CD. I tried the alternate drive as well, after pointing it to cdrom1 but no cookie there either.

---

### Post by userundefine on 2006-06-23
[QUOTE=blacklantern]*laughs* I knew I'd manage to screw it up. When I get past step 6, the terminal window closes, and after I insert the DVD, nothing happens other than the contents of the CD being shown in the file browser. the directory /usr/<username>/games/nwn doesn't exist. Does the script create it, or should I do it beforehand?

edit:

Nevermind. Reading is fundamental. :P[/QUOTE]
Ok, maybe *I'm* thick, but how did you get past this?  I enter all the information, hit enter after the Groups question and it just exits.  Doesn't do anything.  I've read the steps several times, I don't see the magic I'm missing.

?

Edit: Nevermind.  I used [this howto]("http://nwn.bioware.com/forums/viewtopic.html?topic=469853&forum=72") instead and installed it quickly.

---

### Post by ~KoN~ on 2006-06-29
[EDIT]Fixed my problems, but i have the wrong install script and the link provided is screwing up. The install script install's my platinum as just the first expansion pack. If someone has the script and can provide a link that'd be great.

~KoN~[\EDIT]

---

### Post by vem0m on 2006-07-22
links for main script DEAD

---

### Post by vem0m on 2006-07-22
nevermind found it but its not working found it last one  found wasn't the right one [http://www.paradoxinc.net/files/install-nwn.sh](http://www.paradoxinc.net/files/install-nwn.sh) there it is

---

### Post by ~KoN~ on 2006-07-22
Thanks for the new link vem0m.

:-D 

~KoN~

---

### Post by mlind on 2006-08-10
There's very neat patch available for libsdl package that allows you to toggle NWN to fullscreen/windowed mode [http://home.woh.rr.com/nwmovies/libsdl.html](http://home.woh.rr.com/nwmovies/libsdl.html)

I just tried it and it works perfectly. You can put patched libSDL soname on NWN's lib/ folder and just change the symlink to that file.
I'll attach patched libSDL **alsa version** (for Dapper). Alt+Enter toggles the window state.

---

### Post by leech on 2006-08-10
> **vem0m said:**
> nevermind found it but its not working found it last one  found wasn't the right one [http://www.paradoxinc.net/files/install-nwn.sh](http://www.paradoxinc.net/files/install-nwn.sh) there it is

The horrible thing is, I could have sworn I changed that link one day.  I wonder if it was reverted at some point because the forums had gone down.  I'll fix it on the first page (Again).

Leech

---

### Post by leech on 2006-08-10
Oops, my bad again.  This is actually not the same script I was using before.  I talked to the guy who made the original one on there some time ago, but apparently his hosted site has disappeared.  I'll tar.gz it up and post it here.

Leech

---

### Post by joecomstock on 2006-08-13
Thanx for the How-To, I have installed NWN diamond off the BioWare setup.  This was much easier.  Anyhow thanx for you work.

---

### Post by nso on 2006-08-17
Umm I have similar problems as everyone else except my terminal exits out as soon as I answer which release I'm installing. Can I get some help?

---

### Post by leech on 2006-08-22
> **nso said:**
> Umm I have similar problems as everyone else except my terminal exits out as soon as I answer which release I'm installing. Can I get some help?

Which script did you use?  The one I posted not too long ago works quite nicely here.  I've tried it on Dapper Drake, Debian Sid, and Edgy Eft.  With the exception of Edgy Eft (which I made a note of on the bottom) it works fine with no modifications.  With Edgy, as stated, you need to revert the link for /bin/sh back to /bin/bash (since in Edgy it uses /bin/dash instead.)

Leech

---

### Post by illu45 on 2006-08-27
> **nso said:**
> Umm I have similar problems as everyone else except my terminal exits out as soon as I answer which release I'm installing. Can I get some help?

Make sure that you've installed unshield and libunshield, as they are required for the installer. I know it sounds silly, but I missed it the first time I tried. ](*,)

I'm having a bit of a problem myself. I've installed the game and the install went fine. However, everytime I launch the game, it goes into a black screen which I cannot seem to get out of without doing a hard reboot. The rest of the system works fine (I can still hear my music playing) but I cannot see anything.

Any ideas?
-illu45

EDIT: If it helps any, I also cannot seem to disable FullScreen mode (by editing the nwn.ini file)

EDIT: I played around with some of the SDL files and installed the patch that allows for fullscreen/windowed mode switching. The game now launches and I everything looks fine, however, after about 30-60 seconds, my computer freezes :(

EDIT (probably last one for now): I updated my video card drivers and it seems to have solved the crashing problem. No sound, though... May try updating sound card drivers later.

EDIT: It was going to my integrated sound card, fixed that by disabling it in BIOS :)... 

So, when's the next game?

---

### Post by bplus on 2006-09-04
anyone know if this method works with the NWN delux collection. (Bought in the UK).

---

### Post by leech on 2006-09-04
What does the deluxe edition come with?

Leech

---

### Post by leech on 2006-09-04
Edit: Double Post. 

Leech

---

### Post by bplus on 2006-09-04
it comes with nvn, hordes of the underdark, shadows of the undrentide.

See thing is I ve got installed on unbuntu by using the 1 gig resources file on the bioware site. I followed the instructions on installing it and it worked fine. (and patched up to latest versions)

I just haven't got a clue how to get the videos working, so was thinking of trying your method.

thanks.

---

### Post by SentientFluid on 2006-09-06
I ran through the How-to and NWN successfully brought me to the screen to enter my serial, however there was no text at all.  I checked and I have msttcorefonts installed, AND I told the script to install to ~/Games/nwn.  I, of course, have full access to everything in there.

So I renamed ~/Games/nwn to ~/Games/nwn_old and ran through the How-to again (this time with .  Now, no matter where I try to run the nwn script from (new folder, old folder, launcher on desktop or in menu) nothing happens at all.

If I go into Terminal and cd to either the nwn_old or nwn folder and run the nwn script I get this message:

```
mcop warning: user defined signal handler found for SIG_PIPE, overriding
Creating link /home/geoff/.kde/socket-ubuntu64.
can't create mcop directory
```

So my question is... what did I do and how can I fix it? :D

---

### Post by leech on 2006-09-07
I think the mcop error is something from KDE, not sure if you run that or not, or quite possibly you have a KDE daemon running somewhere.  Shouldn't be really relevant though to Neverwinter Nights.

The installer that is attached in the How To should set your permissions properly for the fonts, etc.  I do know that the issue of the fonts not showing up is a permissions issue.  

For now, try to run 'chmod 755 -R ~/Games/nwn' and make sure the nwn script itself points to the right directory.

Leech

---

### Post by beeldings on 2006-09-08
I recently reinstalled Dapper and had to reinstall NWN Platinum as result. I noticed that after configuring the game to play the movies, it runs very slow. Prior to installing the movies patch, the game ran full speed at 1280x1024, but when I run it with the movies enabled, the mouse lags on the menu screen with everything either turned off or set to run at the lowest settings. Is there a way I can remove the movies without having to reinstall NWN? My system runs Dapper 32 on an AMD Athlon 64 2.2 Ghz, 2 GB DDR RAM, and the video card is an XFX GeForce 6800XT 512 MB AGP (with latest drivers through envy).

---

### Post by daemoncat on 2006-09-12
Well, downloaded all the patches, etc. looked over the script, setup directories, and ran the shell ... pretty purple messages says:
Cannot read "/media/cdrom0/disk2.zip" ... well, wazzup? I checked that the path was correct, it was. so ... ls -l /mount/cdrom0 gives me ... disk2.bzf ... BZF?:confused: ? WTM$ crap is this??? so ... after googling and finding some obscure reference to it beinga texture and info file ... nothing on the bioware forums ... nothing here. Is my set of disks the ONLY one ever made with this silliness? :frown: So ... is there any way to get the .bzf file to behave? Thanks.

---

### Post by daemoncat on 2006-09-12
Well, downloaded all the patches, etc. looked over the script, setup directories, and ran the shell ... pretty purple messages says:
[COLOR="DarkOrchid"]Cannot read "/media/cdrom0/disk2.zip"[/COLOR] ... well, wazzup? :confused: I checked that the path was correct, it was. so ... ls -l /mount/cdrom0 gives me ... disk2.bzf ... BZF? :confused: ? WTM$ is this??? :shock: so ... after googling and finding some obscure reference to it being a texture and info file ... I find a solution ... biounzip! :biggrin: 
... but biounzip segfaults before it can do anythinguseful! :( The make output was full of [COLOR="DarkRed"]incompatible implicit declaration of built in function 'exit'[/COLOR] errors :frown: So ... is there any way to get the .bzf file to behave? ](*,) Thanks.

---

### Post by Perfect Storm on 2006-09-13
Well I just put everything down from CD to harddrive. Easy solution.

---

### Post by leech on 2006-09-13
> **beeldings said:**
> I recently reinstalled Dapper and had to reinstall NWN Platinum as result. I noticed that after configuring the game to play the movies, it runs very slow. Prior to installing the movies patch, the game ran full speed at 1280x1024, but when I run it with the movies enabled, the mouse lags on the menu screen with everything either turned off or set to run at the lowest settings. Is there a way I can remove the movies without having to reinstall NWN? My system runs Dapper 32 on an AMD Athlon 64 2.2 Ghz, 2 GB DDR RAM, and the video card is an XFX GeForce 6800XT 512 MB AGP (with latest drivers through envy).

That's quite odd, I have a 6800GT and don't suffer that problem.  At least that I can recall, I haven't played it in a while though.

It's easy enough to disable movies without uninstalling.  Simply put a # in front of the line for exporting the nwmovies.so in your nwn start up script.

Leech

---

### Post by bplus on 2006-09-13
I m having problems with movies bit of your guide leech:
I installed nwn using the 1 gig resource file from bioware. Then I installed Shadows if undrentide and hordes of the underdark.

I ve got everything up to date with most recent patch. (one with the cloaks). Everything seemed to work.

I followed the bit of your guide about getting the movies to work.

The movies bit in the menu isn't greyed out any more and the movies play, except they have no sound! Also all the in game music doesn't play at all either now!

The movies do play with sound however outside the game e.g:
```

./BinkPlayer /home/bbyrne/nwn/movies/XP2_Intro.bik

```
works fine.

Any ideas?


Im thinking of trying to install everything using the cds and your guide if I cant figure this out. Thanks for making for making the guide in the first place!

---

### Post by beeldings on 2006-09-13
> **leech said:**
> That's quite odd, I have a 6800GT and don't suffer that problem.  At least that I can recall, I haven't played it in a while though.

It's easy enough to disable movies without uninstalling.  Simply put a # in front of the line for exporting the nwmovies.so in your nwn start up script.

Leech

What's really strange is that after I disabled the movies, the game still ran extremely slow. This was under GNOME, so I tried something different and ran the game under XFCE. With XFCE, the game ran flawlessly, with and without movies. I reinstalled Dapper AGAIN so now I'm going to attempt another installation of NWN. I'll report back when it's finished.

---

### Post by On. Clarkii on 2006-09-14
Ok, so I got through the installation and go to my nwn directory and sh nwn.  I get this in response:


mcop warning: user defined signal handler found for SIG_PIPE, overriding
Creating link /home/darren/.kde/socket-Hobbiton.
can't create mcop directory

any ideas what this is all about?  I have an Nvidia card and all else is good--running dapper.

---

### Post by duncan128 on 2006-09-15
On. Clarkii

All you have to is create the directory yourself, i.e.

mkdir /home/darren/.kde/socket-Hobbiton

This has happened to me twice (with GAIM and NWN) when I installed KDE once and then removed it.

---

### Post by daemoncat on 2006-09-15
> **Artificial Intelligence said:**
> Well I just put everything down from CD to harddrive. Easy solution.

:confused: and it just ran after that? :? Silly me! I thought it would be harder than that. I'll give that a try. Thanks! :lol:

---

### Post by Carbon Based on 2006-09-16
I installed NWN Diamond using this HOWTO, and it works great for me so far. The only problem is that, as I installed it in /usr/local/games, I have to run it using gksudo, otherwise I get an error when I try to create a character ("unable to load module"). I've done "chmod 777 -R *" in the nwn directory, that made fonts actually show up, but still the module error. Other than that it runs great using gksudo, there was only some strange flickering in the textures of characters that I fixed by tweaking the video settings in the game. Thanks for this great HOWTO.

---

### Post by bob3000 on 2006-09-16
I tried installing it this way, but it didnt work 4 me. I installed it with wine, and it installed great! One problem... I opened nwn, pressed play, and a message popped up saying "insert nwn disk" the disk was inserted. what do I do!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!](*,) ](*,) ](*,) ](*,) ](*,) 

BTW what is a no-cd crack, and would it help? if so, where do I get one?

I am new to linux.:-\"

---

### Post by leech on 2006-09-17
I'll try to answer what I can in one post...

@ bplus;

The sound problem could be related to the version of libsdl you have, make sure you're running the alsa version.  Or 'sudo apt-get install alsa-oss' may also help.  That's kind of an odd issue that the music worked before but doesn't after putting in the movies.

@ Carbon Based;

Strange, usually that'll work.  I generally just install nwn in the home directory, it isn't really programmed for multi-user set ups anyhow.  There is a hack for setting it up with multi-users, but I've never attempted it myself.

@ bob3000;

What exactly does not work with the method put forth in my how to?  You'll be better off running the native version, and not through Wine.  A No-CD crack is in essence something that removes a CD check that most games have.  Unfortunately Wine itself doesn't really provide the wrapper for this sort of software, due to copyright and IP issues.  The Native version of Neverwinter Nights has never asked for the CD to be inserted.

Leech

---

### Post by bplus on 2006-09-17
firstly thanks for the response leech!

Howeve I ve just switched to 64 bit ubuntu. Again Im trying to get the movies in working in neverwinter, but now I cant even get bink player working!
if I ./BinkPlayer <some nwn movie file> I get the following error:

> 
./BinkPlayer: error while loading shared libraries: libvorbisfile.so.3: cannot open shared object file: No such file or directory


also when I run nwmovies_install.pl these errors appear at the end:
> 
nwmovies/nwmovies_link.S:17: Error: `pusha' is not supported in 64-bit mode
nwmovies/nwmovies_link.S:19: Error: `popa' is not supported in 64-bit mode


then when running the actual games (./nwn) i get:

> 
ERROR: ld.so: object './nwmovies.so' from LD_PRELOAD cannot be preloaded: ignored.


is there a way to get nwmovies working on ubuntu 64?

thanks in advance!

---

### Post by Perfect Storm on 2006-09-17
> **Carbon Based said:**
> I installed NWN Diamond using this HOWTO, and it works great for me so far. The only problem is that, as I installed it in /usr/local/games, I have to run it using gksudo, otherwise I get an error when I try to create a character ("unable to load module"). I've done "chmod 777 -R *" in the nwn directory, that made fonts actually show up, but still the module error. Other than that it runs great using gksudo, there was only some strange flickering in the textures of characters that I fixed by tweaking the video settings in the game. Thanks for this great HOWTO.

You can't install as root (well you can, but then you'll taking a security risk if you play nwn with sudo).
Instead install in your home folder.
I usually installs game in /home/<username>/.Games (hidden) and makes shortcut to them.

---

### Post by bob3000 on 2006-09-17
Leech: my problem with the installer...  I downloaded patch 1.65 from the script, but it doesn't recognize it. how do i manually install it?
also, there is no writing in the window that asks for the key, and no matter how many times i enter it, nothing happens.
I use Dapper.


BTW has anyone gotten "the battle for middle earth" (1 NOT II) to work on their machine?
It

---

### Post by leech on 2006-09-18
> **bplus said:**
> firstly thanks for the response leech!

Howeve I ve just switched to 64 bit ubuntu. Again Im trying to get the movies in working in neverwinter, but now I cant even get bink player working!
if I ./BinkPlayer <some nwn movie file> I get the following error:



also when I run nwmovies_install.pl these errors appear at the end:


then when running the actual games (./nwn) i get:



is there a way to get nwmovies working on ubuntu 64?

thanks in advance!

Try installing libvorbisfile3 first, that's what package the libvorbis.so.3 file is in.

Leech

---

### Post by leech on 2006-09-18
> **bob3000 said:**
> Leech: my problem with the installer...  I downloaded patch 1.65 from the script, but it doesn't recognize it. how do i manually install it?
also, there is no writing in the window that asks for the key, and no matter how many times i enter it, nothing happens.
I use Dapper.


BTW has anyone gotten "the battle for middle earth" (1 NOT II) to work on their machine?
It

Firstly, why the 1.65?  The newest installer that is on the page now supports 1.67 (the 1.68 is out now, but it's just a matter of extracting that on top of your nwn directory to get it to work).  You may have the older version of the script which did have that problem of automatically downloading the patches.  The one that is currently on there should work just fine.

Leech

---

### Post by bob3000 on 2006-09-26
in the windows version, there is a bar called "tools" on the start menu. how do I get this?

I am using 1.67

---

### Post by leech on 2006-09-26
It's been a long time since I played it on Windows, so I could be wrong about this.  But I think the TOOLS option is for the Aurora toolset, which is not ported to Linux.  [http://neveredit.sourceforge.net/cgi-bin/moin.cgi](http://neveredit.sourceforge.net/cgi-bin/moin.cgi) is what you'll want to look at.

Leech

---

### Post by bob3000 on 2006-09-30
sorry, but being the linux noob i am, how do i get neveredit running?](*,) 
i use dapper

---

### Post by leech on 2006-09-30
No clue :D  I tried it myself quite a while ago and it still needed some work.  Not sure how good it is now.  If I recall it uses Python and you just need to run the script.

Leech

---

### Post by glenn45 on 2006-10-01
Hi! Is this HOWTO good for 64bit ubuntu? 
Thanks in advance.

---

### Post by leech on 2006-10-01
Give it a shot and let us all know if it works in 64bit linux.  I haven't tried it myself, but I don't see why it wouldn't work.

Leech

---

### Post by glenn45 on 2006-10-03
> **leech said:**
> Give it a shot and let us all know if it works in 64bit linux.  I haven't tried it myself, but I don't see why it wouldn't work.

Leech

Okey. I'll try tonight. hehehe:)

---

### Post by TheFlamingBush on 2006-10-04
Hi Leech!....ive just read through your entire thread and have to say ive been impressed with the thought youve put into this. Well done mate! :)

Ok i have NWN, SOU, and HOU, all bought at various times in the last few years. No diamond or gold or whatever editions. I have been wanting to try it out on Linux, even if it is just to play it a bit....probably with CEP added so that it can be played on a server.

Ive run into a bit of a problem though...._EDIT!_ 

**I fixed it i think!**

---

### Post by leech on 2006-10-05
You know what the really funny thing is?  I've basically become Ubuntu Tech Support for Neverwinter Nights.  Yet, I haven't even played the game in ages!  I want to get back into it, but just haven't found the time.  

Leech

---

### Post by dolphinsonar on 2006-10-05
I forbit the use of the text "LOL" unless acompanied by an audio file of you actually laughing out loud, that must be directly downloadable in a non-proprietary format from the text "[LOL]("http://pardubice.misto.cz/_MAIL_/Motorola_MPx200/Tones/lyde/laughing.wav")" when you type it.

Thank you for your cooperation.


> **J-B said:**
> Well this would have been nice to know yesterday!  Lol, I followed the instructions in the Bioware forums which forces you to decompress each cd manually, and install everything manually.  I spent about eight hours and several tries on it total before I got it working.   Oh well, good tutorial, hope it helps some people out there.  

fizdev-  NWN actually does run more smoothly under Ubuntu, at least for me.  I've noticed a marked difference from my windows install.

---

### Post by leech on 2006-10-05
> **dolphinsonar said:**
> I forbit the use of the text "LOL" unless acompanied by an audio file of you actually laughing out loud, that must be directly downloadable in a non-proprietary format from the text "[LOL]("http://pardubice.misto.cz/_MAIL_/Motorola_MPx200/Tones/lyde/laughing.wav")" when you type it.

Thank you for your cooperation.

I agree!  The most annoying thing in the world right now to me (well as far as computers go, people themselves will always be the worst...) is that when talking to someone who uses MSN Messenger on Windows does a LOL or Yup or even something like They and it puts this huge YUP or makes a laughing guy and a huge LOL, even worse on They because it makes it say tHEY, with the HEY flashing.  Is there any possible way to turn that crap off?

Leech

---

### Post by TheFlamingBush on 2006-10-05
> **leech said:**
> I agree!  The most annoying thing in the world right now to me (well as far as computers go, people themselves will always be the worst...) is that when talking to someone who uses MSN Messenger on Windows does a LOL or Yup or even something like They and it puts this huge YUP or makes a laughing guy and a huge LOL, even worse on They because it makes it say tHEY, with the HEY flashing.  Is there any possible way to turn that crap off?

Leech

Leech, i used the Auto download for my individual packages. I also went through step 1 and 2 in your origional article. I then downloaded 1.68 update for linux, and installed that to the letter, however i cant seem to get the game to run at all!

In fact i cant find the NWN main, its in the NWN directory of course but it looks like an executable text file.

Theres **NWMain**, which is an *application/x-executable*, and then there is the **NWN** file that is a *application/x-shellscript*. Neither of these open the game. The best i get is whether i want to run in terminal, display, run etc....when i start up the shell script. The other file, which i suspect is the file i need simply doesnt respond at all...nothing, nada, nix!

Im a bit flumoxed!..... 3 gigs on the disk and nothing at all. 

I tried using the HOTU cd to start the game but that doesnt seem to work either, although i get sound and a small pic if i press install, so at least i know there is potential! ;)....

have i failed to do something script wise? I have  msttcorefonts installed, and unshield which of course allowed me to use the auto install.

Drat!....i was actually looking forward to seeing how this working in Linux. Although to be honest i was more interested in building some mods in my spare time, so the tool set will be required, and i gather it isnt working or available in Linux?

---

### Post by leech on 2006-10-06
It's just the nwn shell script that you need to run.  Open a terminal, cd into your nwn directory, then simply type ```
./nwn
``` and it should work.

Leech

---

### Post by leech on 2006-10-06
That was rather annoying.  I just tried to load up Neverwinter Nights, and the sound played, but there was no video.  Then it totally crashed my X after I tried to go to the console and kill it.

Figured it was Beryl's fault (I'm running Edgy with Beryl and all it's 3D goodness), but then upon rebooting, I tried it with Metacity.  Worked fine, then I enabled Beryl again, and it worked fine.  So chalk that up as a random crash.  

Leech

---

### Post by TheFlamingBush on 2006-10-06
thanks lEECH.....BUT i tried that also last night and the reply i got back was that it was a directory, and thats it...nothing more!...:-/

i dumped the game, and will reinstall today and see if it works, if not i'll use it on my XP partition, and download falconsnest for my Linux partition.

shame!.....still lets give it one more go! ;)

oh and i guess this might have been asked before. But if i install it on the middle fat32 share partition i have, for sharing stuff between Ubuntu and XP, can i just play it through wine in Ubuntu.....or doesnt that work?

---

### Post by leech on 2006-10-06
Wine is so overrated, when it works natively.

Sounds like the problem you're having is that instead of going into the nwn directory, then running ./nwn you're running it from your home directory.

So let's say your user name is flamingbush.  If you installed it in your home directory, it'd be /home/flamingbush/nwn.  What you'd want to do is then open up a terminal, which will automatically be in your home directory, then type ```
cd nwn
```

So then the line would look something like ```
flamingbush@ubuntu:~/nwn$
```

Then all you would need to type is ./nwn

The confusion here is that both the execution script and the folder is named 'nwn'  You could conceivably just use /home/<user>/NeverwinterNights/ when you install it to save yourself from this confusion.  I do also talk about how to create an icon in your menu for launching the game (at least I did in one of my drafts, it's been so long now that I forgot if it's still on the full post.)

As far as running it on a fat32 partition.  I'd shy away from that, Fat32 pretty much sucks anymore.  You could always try the ntfs3g driver, but again, that would probably be a bit on the complicated side to set up.  I say forget Windows and play it natively!

Leech

---

### Post by MrBlond83 on 2006-10-17
I tried the part for NWN movies. Without it, my NWN worked perfectly, but once I add "export LD_PRELOAD=./nwmovies.so", the movies work, but the background music stops working!

The funny thing is that sound effects like when clicking on buttons work, it's just the music that doesn't! and also no music or sound in the movies at all.

When I remove that line it all goes back to normal, what's up with that?

EDIT: The problem seems even weirder - the music inside the game works, the music in the main menu after going back to it works, the only time music doesn't work is while playing the movies, and while being in the menu for the first time after playing the movies.

Strangely, when playing movies directly using Bink from the command line, their sound works fine.

Has anyone found a solution to this yet?

---

### Post by mage2 on 2006-10-17
I installed NWN diamond once everything was great. 
My kbuntu died a horrible death, so like any geek I reinstall and reinstall NWN using the same setup and the same hardware. And following the same instructions. 
Now I do not have any text when I start the game in the field where it should ask for the key, all the fields are empty. I have uninstalled the msttfontcores and the unshield and the libunshield. I also removed the /usr/local/games/nwn directory and started over. Still nothing. 
I am trying yet again. 
Does anyone have any ideas?

---

### Post by MrBlond83 on 2006-10-18
Where is leech I heard he is the undisputable master of NWN in linux.

Who can summon him :)

---

### Post by leech on 2006-10-19
Sorry, been busy working on some of my own issues :D

As far as the fonts not showing up, that's a permissions issue.  As stated in the How To, it's easier just to install Neverwinter Nights in your home directory.  The installer should take care of your file permissions, so the text should work right away.

With the movies not playing music?  This is just me hazarding a guess, but do you have libesd-alsa0 installed?  Also the other one you could try to make sure you have is libsdl1.2debian-alsa.

Leech

---

### Post by MrBlond83 on 2006-10-19
I have libesd-alsa0 and libsdl1.2debian-all installed.

What puzzles me is that playing movies using BinkPlayer directly works perfectly, but when played through the game in the exact same manner there is no sound.

Very strange.

---

### Post by Uuranor on 2006-10-21
Uh, maybe someone can help me.
I've recently re-installed NWN on my linux box (edgy), and now it is really slow. In Windows XP it runs without any problem, and so on my old installation of NWN (in dapper).

My glxgear -printfps give me this output:
7070 frames in 5.0 seconds = 1413.983 FPS
7047 frames in 5.0 seconds = 1409.251 FPS
7047 frames in 5.0 seconds = 1409.353 FPS
7048 frames in 5.0 seconds = 1409.588 FPS
7047 frames in 5.0 seconds = 1409.317 FPS
7047 frames in 5.0 seconds = 1409.353 FPS

... but the command "cat /proc/driver/nvidia/agp/status" give me:
Status:          Disabled

AGP initialization failed, please check the ouput  
of the 'dmesg' command and/or your system log file 
for additional information on this problem.


Someone has any hint to make NWN speedy?

---

### Post by factotum218 on 2006-10-21
Here here!
I dont have the platinum edition or any of the expansion packs atm, but after getting the game a few years back, running through it and moving on...
Installing it on ubuntu and following the walkthrough on the bioware site; it's a breath of new life into this game! Runs so much smoother than I recall on my old win2k setup.

Im crossing my fingers that NWN 2 will at the very very least have wine support. I haven't seen anything regarding a native port yet.
Anyone know differently?

---

### Post by factotum218 on 2006-10-21
Here are the factors I see.
1> Running Edgy.
Really this probably isn't the problem but you never know.
2> The xorg.conf might be off.
What is you graphics card model? I think even if its something like a recent onboard intel it should be usable. Look into enabling AGP in your xorg.conf. I always had to manually set this up when I was running Slackware, its not difficult. Plenty of documentation around to get it done, especially in this ever-growing Ubuntu community.

---

### Post by Uuranor on 2006-10-22
> **factotum218 said:**
> Here are the factors I see.
1> Running Edgy.
Really this probably isn't the problem but you never know.
2> The xorg.conf might be off.
What is you graphics card model? I think even if its something like a recent onboard intel it should be usable. Look into enabling AGP in your xorg.conf. I always had to manually set this up when I was running Slackware, its not difficult. Plenty of documentation around to get it done, especially in this ever-growing Ubuntu community.

Ok, I've modified xorg.conf by changing NvAGP from "1" to "3", and now the status doesn't have any problem. BTW the game is still not smoother like my old installation of Ubuntu, or WinXP :(

---

### Post by leech on 2006-10-22
First off, I would run [code]glxinfo |grep direct[\code] though it does sound by your glxgears like you should have direct rendering.  Secondly, I would check to make sure your resolution settings aren't too high.  I can honestly say that it's been a long time since I have actually played the game, I did try it though in Edgy along with AIGLX and the new nvidia beta driver and Beryl loaded and it actually still worked!  

I'll run some more tests though, since as I said, I didn't play it long, just long enough to load up my character.

Oh and to the poster who had just the original version, I would suggest next time you have to re-install to use the installer at http://www.liflg.org where they have a native loki installer for Neverwinter Nights and the CEP

Leech

---

### Post by theplatypus on 2006-10-26
I've followed the instructions found here to get movies working, but upon running the game I get the following error. The game works fine , but I still don't have the movies. Any ideas?

```
ERROR: ld.so: object './nwmovies.so' from LD_PRELOAD cannot be preloaded: ignored.

```

---

### Post by MrBlond83 on 2006-10-26
Can you see the nwmovies.so file in your main NWN directory?

If not, then maybe you extracted the nwmovies some place else by mistake. The newmovies archive includes several files (which are actually symbolic links) that should be in your main NWN directory, plus an "nwmovies" directory.

This happened to me when first installing it as I put the archive file in the NWN directory and extracted it to "nwmovies" directory, which resulted the files that should be in the main NWN directory being in "NWN/nwmovies", and the directory of nwmovies being in "NWN/nwmovies/nwmovies"...

So that would be my guess :)

---

### Post by theplatypus on 2006-10-27
> **MrBlond83 said:**
> Can you see the nwmovies.so file in your main NWN directory?

If not, then maybe you extracted the nwmovies some place else by mistake. The newmovies archive includes several files (which are actually symbolic links) that should be in your main NWN directory, plus an "nwmovies" directory.

This happened to me when first installing it as I put the archive file in the NWN directory and extracted it to "nwmovies" directory, which resulted the files that should be in the main NWN directory being in "NWN/nwmovies", and the directory of nwmovies being in "NWN/nwmovies/nwmovies"...

So that would be my guess :)

This is what is listed in my main NWN directory.  If I understand you correctly it is incorrect. How do I go about fixing this mess?                    localvault                    nwnplayer.ini
..                   logs                          NWNv129.txt
ambient              miles                         nwserver
BinkLinuxPlayer.zip  modules                       override
BinkPlayer           movies-OC.txt                 patch.key
chitin.key           .mssdebug.log                 portraits
data                 music                         readme.linuxserver.txt
dialog.tlk           nwclient129.tar.gz            readme-SDL.txt
dmclient             nwm                           readme.txt
dmvault              nwmain                        saves
docs                 nwmovies-latest.tar.gz        servervault
EULA.txt             nwmovies-latest.tar.gz_FILES  tempclient
fixinstall           nwn                           texturepacks
hak                  nwncdkey.ini
lib                  nwn.ini

---

### Post by God Of Atheism on 2006-10-27
First I did not manage to run the game in Dapper, although the install did seem to work, now in Edgy I run into other troubles.
When running the script I get:

-en Enter the install directory. (/usr/local/games/nwn): 
/media/sdb2/nwn
[: 64: ==: unexpected operator
-e Possible write error
-e Please try a different folder or change permissions on /media/sdb2/nwn

The -e at the start, or -en in most cases, appears on the preceding screens as well, something seems to be wrong with the character encoding of the script, the locale is not recognized (when opening it as a textfile) and this might be a possible cause of the error, although I'm not sure. In addition, I noticed that the Edgy install did change some thing in /etc/fstab (see below), which might be the cause of the write error above. I did change permissions on /media/sdb2/nwn, but was not able to change the group, so instead created the listed group and added myself as a member of that group, but the error message remains unchanged

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2 -- converted during upgrade to edgy
UUID=<long identifier> / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=<long identifier> /home ext3 defaults 0 2
# /dev/sda1 -- converted during upgrade to edgy
UUID=<medium identifier> /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda3 -- converted during upgrade to edgy
UUID=<medium identifier> /media/sda3 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sdb2 -- converted during upgrade to edgy
UUID=<short identifier> /media/sdb2 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sdb3 -- converted during upgrade to edgy
UUID=<long identifier> none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Where <long/medium/short identifier> is a hexadecimal number in the long case interrupted by several dashes, in the short case by one dash and in the medium case by none and having 32/16/8 hexadigit length.

Any ideas as to how to solve this problem?

---

### Post by d3v1ant_0n3 on 2006-10-27
Randomly found this thread the other day. Found my NVW disc today, got all excited. And my dvd drive decided to take its ball and go home ](*,) I hate this machine sometimes. 

SO I'm presently being pleasantly suprised by the download speeds from Biowares site for the resources tar. 

And dammit, I WILL complete it this time (never made it past the first few chapters before, kept getting distracted by HL2 on PC.).

---

### Post by leech on 2006-10-28
> **d3v1ant_0n3 said:**
> Randomly found this thread the other day. Found my NVW disc today, got all excited. And my dvd drive decided to take its ball and go home ](*,) I hate this machine sometimes. 

SO I'm presently being pleasantly suprised by the download speeds from Biowares site for the resources tar. 

And dammit, I WILL complete it this time (never made it past the first few chapters before, kept getting distracted by HL2 on PC.).

Sounds like my week!  I was putting together a computer for a friend.  It was  built around the Core 2 Duo, an Asus P5B-E motherboard, etc.  Anyhow, without going into too many details, Ubuntu was being a pain in the butt to install, so I pulled out my SATA dvd burner, popped it in there to try to install again, and then when I put it back in my main system, everything seemed to blow up (lost all my data on my main windows drive, had to re-create my grub, etc.)  

I also never passed the original campaign, mainly because of getting to a point where it pissed me off, then stopping, then picking it up a year later, then stopping, then maybe a year later again starting again...  It's a HUGE game, plus the two expansions, plus all the free modules out there.  You could basically play the game forever and not have to buy another one ever.

Leech

---

### Post by leech on 2006-10-28
> **God Of Atheism said:**
> First I did not manage to run the game in Dapper, although the install did seem to work, now in Edgy I run into other troubles.
When running the script I get:

-en Enter the install directory. (/usr/local/games/nwn): 
/media/sdb2/nwn
[: 64: ==: unexpected operator
-e Possible write error
-e Please try a different folder or change permissions on /media/sdb2/nwn

The -e at the start, or -en in most cases, appears on the preceding screens as well, something seems to be wrong with the character encoding of the script, the locale is not recognized (when opening it as a textfile) and this might be a possible cause of the error, although I'm not sure. In addition, I noticed that the Edgy install did change some thing in /etc/fstab (see below), which might be the cause of the write error above. I did change permissions on /media/sdb2/nwn, but was not able to change the group, so instead created the listed group and added myself as a member of that group, but the error message remains unchanged

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2 -- converted during upgrade to edgy
UUID=<long identifier> / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=<long identifier> /home ext3 defaults 0 2
# /dev/sda1 -- converted during upgrade to edgy
UUID=<medium identifier> /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda3 -- converted during upgrade to edgy
UUID=<medium identifier> /media/sda3 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sdb2 -- converted during upgrade to edgy
UUID=<short identifier> /media/sdb2 vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sdb3 -- converted during upgrade to edgy
UUID=<long identifier> none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Where <long/medium/short identifier> is a hexadecimal number in the long case interrupted by several dashes, in the short case by one dash and in the medium case by none and having 32/16/8 hexadigit length.

Any ideas as to how to solve this problem?

Just a shot in the dark, firstly.  What filesystem is on /media/sdb2?  By my guess it's either a SCSI drive or an SATA one.  But either way, it's not your home directory, I would make sure that you indeed do have write permissions on it (for example, if it's NTFS, you need the ntfs-3g packages plus change the /etc/fstab to ntfs-3g.

It looks like it's a vfat drive, but vfat is really not a good idea to install Neverwinter Nights on.  Remember, Linux is case sensitive, and so is Neverwinter Nights for Linux.  For example, you have to change the case on a lot of player made modules before they'll work.  

Leech

---

### Post by d3v1ant_0n3 on 2006-10-28
Well I only have the main campaign installed, but that will more than do me for now! And it was really painless. Download. Unzip. Unzip another tar. Patch (By, yep, unzipping another tar). Run.

Only thing I had issues with was changing the resolution up to 1024*768(native for this screen)- It made the screen go black. This might have been due to the fact I was running it over Beryl tho. Performance wasn't bad for this box either. Hurrah!

EVen tho I blatantly haven't used this guide, thanks for the inspiration to make me play Neverwinter again:D

---

### Post by _francis on 2006-10-28
installed nwn diamond today on a brand new edgy took the files from a windows installation and followed the guide at [URL="http://nwn.bioware.com/downloads/linuxclient.html"] i updated to 1.68 and game is running smoothly. but after trying to enable the movies (it worked without a problem under dapper) i got the following outpput at the command line:

ERROR: ld.so: object './nwmovies.so' from LD_PRELOAD cannot be preloaded: ignored.
libGL warning: 3D driver claims to not support visual 0x4b

anyone got an idea?

as long as the game is running it's not a big problem but i really would like to see the movies without starting bink in a terminal...

---

### Post by MrBlond83 on 2006-10-29
leech, my problem is even weirder now. Last time I reported not being able to hear sound in movies playing inside nwn, despite being able to hear sounds just fine when they were played directly using nwmovies.pl or binkplayer.

Well, yesterday I decided to get to the bottom of another problem I was having, which was alsa streaming sound through the analog port of my soundcard and not the digital one (I was able to make gstreamer stream to the digital output simply by selecting IEC958 in the sound preferences, but that did not affect alsa of course). So I started reading on, and eventually realized all it takes was a small change to /etc/asound.conf - replace "hw:0,0" with "hw:0,2" (which was the address for the IEC958).

Since the main reason I wanted to fix this was so I can listen to Pandora music through my 5.1 system and not through headphones (which i keep connected to the analog output), I went on happily with my day. But then when I started NWN I was suprised to find out that now sound in movies does indeed work! The music in the main menu still did not work when first entering the menu (it worked before installing nwmovies, and it works when coming back to the menu after loading a game), so that leads me to think that it is unrelated (it was also reported by other users and is pretty marginal so who cares). But what really puzzles me is how come sound in movies inside nwn refuses to play through hw:0,0...

Anyway, I have no real solution, just thought I would share this and maybe someone will see in it more than I do :)

---

### Post by techstop on 2006-10-30
I had a quick look in the thread, I don't think this has been answered....

I had this working fine on Dapper, and I did a clean install to Edgy (from scratch, formatted drive etc). I made a backup of my nwn directory to DVD first though. What is involved in getting this to work again? Do I have to do the whole install process again, or can I just copy the nwn folder back to my Edgy installation? Cheers.

---

### Post by hirumono on 2006-10-31
> **Uuranor said:**
> Uh, maybe someone can help me.
I've recently re-installed NWN on my linux box (edgy), and now it is really slow. In Windows XP it runs without any problem, and so on my old installation of NWN (in dapper).


Hi, I had just the same problem when I switched from Breezy to Edgy. Nwn was outstandingly smooth and fast before, and then it stuttered sadly, together with the mouse which moved at "steps".
Finally I looked into Synaptic and found that Edgy had installed nVidia modules for a 64-bit platform (???); when I switched to 386 binaries (and the system reloaded my kernel, too), nwn ran just as smooth and fast as before.
Maybe your problem is the same?

Cheers!

---

### Post by daedalusman on 2006-10-31
In edgy I am getting this error even though I have set both user and group permissions to allow both file and directory creation and read write...

```
-en Enter the install directory. (/usr/local/games/nwn): 
/home/tyrion/nwn/
[: 64: ==: unexpected operator
-e Possible write error
-e Please try a different folder or change permissions on /home/tyrion/nwn/
```

Can some one help me out here, I really would like to finally be able to play a descent rpg in linux since I no longer have windows installed at all. This really annoying. Thanks for any help.

---

### Post by leech on 2006-11-01
> **daedalusman said:**
> In edgy I am getting this error even though I have set both user and group permissions to allow both file and directory creation and read write...

```
-en Enter the install directory. (/usr/local/games/nwn): 
/home/tyrion/nwn/
[: 64: ==: unexpected operator
-e Possible write error
-e Please try a different folder or change permissions on /home/tyrion/nwn/
```

Can some one help me out here, I really would like to finally be able to play a descent rpg in linux since I no longer have windows installed at all. This really annoying. Thanks for any help.

Here is the answer to this one..... lousy Edgy and it's usage of DASH!

What you'll need to do is temporarily (or permanently) change sh to point to bash.  This is actually rather easy, at least.

```
sudo rm /bin/sh
sudo ln -s /bin/bash /bin/sh
``` then you can run the install script.  Note that it no longer has the funky -en and that it now will actually download the patch etc.

To return to using dash, just simply ```
sudo rm /bin/sh
sudo ln -s /bin/dash /bin/sh
```

Leech

---

### Post by leech on 2006-11-01
> **techstop said:**
> I had a quick look in the thread, I don't think this has been answered....

I had this working fine on Dapper, and I did a clean install to Edgy (from scratch, formatted drive etc). I made a backup of my nwn directory to DVD first though. What is involved in getting this to work again? Do I have to do the whole install process again, or can I just copy the nwn folder back to my Edgy installation? Cheers.

You should be able to just copy your nwn folder back to your Edgy installation, the only problem I've seen so far from running it on Edgy is the installation script was broken due to the move to using Dash over Bash.

Leech

---

### Post by leech on 2006-11-01
So I worked on this a bit more and cleaned things up a bit, organized here and there and added the fix for Edgy Eft.  

There probably is still more work to do on it, but who cares as long as it gets people going on playing the game 100% natively :D

Leech

---

### Post by daedalusman on 2006-11-01
Thanks leech for the info and help. I actually ended up just installing in manually last night with a tutorial from the bioware nwn forums and got it working that way. But it works 100% natively and I'm now happy. Again thanks and keep up the good work.

edit
Also maybe a better way to change from dash to bash would be to use dpkg-reconfigure dash. Also note that in needs to be run by root and that answering no will change to bash. Just thought you would like to know. Thanks

---

### Post by techstop on 2006-11-01
> **leech said:**
> You should be able to just copy your nwn folder back to your Edgy installation, the only problem I've seen so far from running it on Edgy is the installation script was broken due to the move to using Dash over Bash.

Leech

OK, I had a fair bit of trouble with this, but it's working now. I kept getting errors like this;

> barney@edgy:~/nwn$ ./nwn
./nwmain: error while loading shared libraries: libmss.so.6: cannot open shared object file: No such file or directory

Here's what I did;


1. Copy /nwn/miles to /usr/lib (this was recommended in a few threads on these forums, see link below) and run ldconfig. Others also advised to change the export path in the nwn script. By itself, these steps didn't work.

2. Add symlinks as found in this post;

[http://nwn.bioware.com/forums/viewtopic.html?topic=347606&forum=72](http://nwn.bioware.com/forums/viewtopic.html?topic=347606&forum=72)

Scroll down a bit till you come to this section;

> These files should also have the following symbolic links:

    * ./lib/libSDL-1.2.so.0 -> libSDL-1.2.so.0.0.5
    * ./miles/libmss.so -> libmss.so.6
    * ./miles/libmss.so.6 -> libmss.so.6.5.2


If these links are missing, you should create them yourself using these commands:

user @ host nwn $ cd lib
user @ host lib $ ln -s libSDL-1.2.so.0.0.5 libSDL-1.2.so.0
user @ host lib $ cd ..
user @ host nwn $ cd miles
user @ host miles $ ln -s libmss.so.6.5.2 libmss.so.6
user @ host miles $ ln -s libmss.so.6 libmss.so
user @ host miles $ cd ..

So, I made those symlinks, and all is working again! I don't know if this helps anyone, but it looks like others have the same problem;

[http://www.ubuntuforums.org/showthread.php?t=188755](http://www.ubuntuforums.org/showthread.php?t=188755)

---

### Post by leech on 2006-11-01
> **daedalusman said:**
> Thanks leech for the info and help. I actually ended up just installing in manually last night with a tutorial from the bioware nwn forums and got it working that way. But it works 100% natively and I'm now happy. Again thanks and keep up the good work.

edit
Also maybe a better way to change from dash to bash would be to use dpkg-reconfigure dash. Also note that in needs to be run by root and that answering no will change to bash. Just thought you would like to know. Thanks

Thanks, unfortunately I did all this early in the morning.  I should have remembered dpkg-reconfigure for this.  Big Duh on my part :D  I'll fix it.

Leech

---

### Post by silthenru on 2006-11-03
Hey...  after struggling and struggling with Bioware's linux install manual, I happily found this one (I'm not the best with technical aspects of linux).

So... I've got to step 4/5 on your list.... where I right click "install-nwn.sh" and open with terminal.

It says "opening install-nwn.sh" in the window list for a while... but then it goes away and nothing has opened.  that's all.  Can I be helped?

I'm trying to load NWN Plat onto Dapper Drake.  I can't figure out what's wrong.

Thanks.



NEVER MIND.  I think I figured it out by opening terminal then typing "exec ./Desktop/install-nwn.sh"

---

### Post by leech on 2006-11-06
Yeah, that'll work too.  I just tried to explain it using the graphical method, since some people are scared of the terminal.  You can just start it with going into the directory where it is and just using ./install-nwn.sh.  

Leech

---

### Post by hobieone on 2006-11-09
as popular that this game is this thread need to be stickied:-D 
recently had to redo my system and had to dig thru the forums to find this thread again it definatly easier that biowares way

---

### Post by daedalusman on 2006-11-09
> **leech said:**
> Thanks, unfortunately I did all this early in the morning.  I should have remembered dpkg-reconfigure for this.  Big Duh on my part :D  I'll fix it.

Leech

Hey no worries, I only mentioned it as I just saw it on the dash wiki page and thought I would mention it here.

---

### Post by djprotoss on 2006-11-28
mostly a FYI since I haven't had a chance to sit down and look at the code.
Short version: nwmovies doesn't compile on amd64.
Lots of warnings about casting to pointer from integer of different size, and finishes up with:
nwmovies/nwmovies_link.S: Assembler messages:
nwmovies/nwmovies_link.S:13: Error: suffix or operands invalid for `push'
nwmovies/nwmovies_link.S:14: Warning: 4294967272 shortened to 232
nwmovies/nwmovies_link.S:15: Error: suffix or operands invalid for `push'
nwmovies/nwmovies_link.S:17: Error: `pusha' is not supported in 64-bit mode
nwmovies/nwmovies_link.S:19: Error: `popa' is not supported in 64-bit mode

now the operand stuff I can cope with fairly easily, but the pusha might be more fun. May post a followup once I've had a chance to investigate.

---

### Post by thedude98 on 2006-12-01
I ran thru all of the instructions at the start of this thread.  After inserting the dvd into the drive I'm not sure how to start the install.  Should the script notice the disk??  Most seem to get it so sorry for my thickhead.  I have the Diamond edition...

---

### Post by techstop on 2006-12-01
> **thedude98 said:**
> I ran thru all of the instructions at the start of this thread.  After inserting the dvd into the drive I'm not sure how to start the install.  Should the script notice the disk??  Most seem to get it so sorry for my thickhead.  I have the Diamond edition...

So in Step 4 you have executed "install-nwn.sh" to launch the installer and it has asked you to insert the disc? Then what happens?

---

### Post by thedude98 on 2006-12-03
I run this script ([http://www.paradoxinc.net/files/install-nwn.sh)](http://www.paradoxinc.net/files/install-nwn.sh)), answer all of the questions and after I press enter to accept the default (user) group, the window closes.  My guess is that's when I should be prompted to load the dvd.

---

### Post by ceno-byte on 2006-12-20
first off i must say this is a great HOWTO guid for installing Neverwinter Nights thnxs very much Leech. I followed it but i ran into a problem when i tried to install the movies i followed everything in the guide but when i go to run NWN from the terminal i get this error " ERROR: ld.so: object './nwmovies.so' from LD_PRELOAD cannot be preloaded: ignored. "

here is my nwn script :

#!/bin/sh

# This script runs Neverwinter Nights from the current directory

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=./lib:./miles:$LD_LIBRARY_PATH
export LD_PRELOAD=./nwmovies.so
./nwmain $@

is there something i did wrong im not really sure what to do from here if it helps im running ubuntu 6.10 

besides this little snag everything else works perfectly :)

---

### Post by PacShady on 2006-12-22
Hey, having trouble with trying to get the movies working.

Firstly, I've got the same problem mentioned previously about having no background music. As for the movies, they're not playing at all. The 'Movies' button on the main menu is clickable, but none of the movies in there play either, nor do the startup movies etc.

Here's the details that come up in the terminal when I run 'sudo ./nwn' in my /opt/games/nwn directory (I install most of my non-deb programs here for easy finding):

```
NOTICE: NWMovies: Version: 20060113.161108
NOTICE: SDL Library determined to be: ./lib/libSDL-1.2.so.0
NOTICE: NWMovies: Patch 0 Address: 0x08076939
NOTICE: NWMovies: Patch 1 Address: 0x0807694d
NOTICE: NWMovies: Patch 2 Address: 0x0815973c
NOTICE: NWMovies: Patch 3 Address: 0x08159756
NOTICE: NWMovies: Patch 4 Address: 0x0807680b
NOTICE: NWMovies: Patch 5 Address: 0x08204e41
NOTICE: NWMovies: Patch 6 Address: 0x08204e64
NOTICE: NWMovies: PrePatch0: 8b 80 48 02 00 00 5d c3
NOTICE: NWMovies: PrePatch1: 8b 80 4c 02 00 00 5d c3
NOTICE: NWMovies: PrePatch2: e8 bf d2 f1 ff 83 ec 08
NOTICE: NWMovies: PrePatch3: eb 58 83 ec
NOTICE: NWMovies: PostPatch0: b8 00 00 00 00 90 5d c3
NOTICE: NWMovies: PostPatch1: b8 00 00 00 00 90 5d c3
NOTICE: NWMovies: PostPatch2: 90 90 90 90 90 83 ec 08
NOTICE: NWMovies: PostPatch3: 90 90 83 ec
NOTICE: NWMovies: PrePatch4: 56 8d 5d e8 53
NOTICE: NWMovies: PostPatch4: e9 80 d5 ea af
NOTICE: NWMovies: MoviesPrePatch: 6a 00 53 bf 00 00 00 3f e8 ae fd 29 00 8b 43 60 8b 10 c7 04 24 00 00 80 3f 57 57 57 50 ff 52 44 83 c4 1c
NOTICE: NWMovies: MoviesPostPatch: 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90
NOTICE: NWMovies: SDL_WM_GrabInput() address: b7d08900
NOTICE: NWMovies: (Calculated) SDL_WM_GrabInputRaw() address: b7d08864
NOTICE: NWMovies: Initialized.

```

I'm running NWN Vanilla with SOU and HOTU as expansions (ie. NOT as Diamond/Gold/Platinum/etc). I installed NWN using the Ravage installer, then installed SOU and HOTU manually (the Ravage installers wouldn't play nice with me for the expansions). I then patched the game up to 1.68. I'm running an AMD AthlonXP 2.0GHz with 768MB RAM and an Ati Raedon 9550 with propriety drivers installed onto Kubuntu Dapper. The game runs fine normally (sans movies), and the movies are playable using the BinkPlayer executable in the NWN directory. Any ideas?

'Shady


EDIT: Seems nwmovies thinks it IS playing movies when it isn't. Here's the contents of a fresh log file:

```
./nwmovies.pl AtariLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: AtariLogo: Fri Dec 22 21:48:33 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/AtariLogo.bik
1166788113.586763: BinkLib: SDL_PRELOAD Initialized
NOTICE: NWMovies.pl finished playing: AtariLogo: Fri Dec 22 21:48:33 2006
./nwmovies.pl BiowareLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: BiowareLogo: Fri Dec 22 21:48:33 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/BiowareLogo.bik
1166788113.820340: BinkLib: SDL_PRELOAD Initialized
NOTICE: NWMovies.pl finished playing: BiowareLogo: Fri Dec 22 21:48:33 2006
./nwmovies.pl WotcLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: WotcLogo: Fri Dec 22 21:48:34 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/WOTCLogo.bik
1166788114.028571: BinkLib: SDL_PRELOAD Initialized
NOTICE: NWMovies.pl finished playing: WotcLogo: Fri Dec 22 21:48:34 2006
./nwmovies.pl fge_logo_black >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: fge_logo_black: Fri Dec 22 21:48:34 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/fge_logo_black.bik
1166788114.309309: BinkLib: SDL_PRELOAD Initialized
NOTICE: NWMovies.pl finished playing: fge_logo_black: Fri Dec 22 21:48:34 2006
./nwmovies.pl NWNIntro >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: NWNIntro: Fri Dec 22 21:48:34 2006
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/NWNintro.bik
1166788114.519343: BinkLib: SDL_PRELOAD Initialized
NOTICE: NWMovies.pl finished playing: NWNIntro: Fri Dec 22 21:48:34 2006

```

---

### Post by leech on 2006-12-23
I would suggest posting in the nwn.bioware.com forums.  The person who wrote the nwmovies script is zzqzzq_zzq  and he helps people out there.

Of course you could also always email him, his email address  is easily found by just doing a search for nwmovies on google.

Leech

---

### Post by aleska on 2006-12-29
Leech - first off, many many thanks.  
I went through the how-to (seemingly without a hitch).  But, I am having the problems with no text appearing.  I read through the entire thread, and it appears that the answer to text not appearing is one of permissions; but I'm confused.

I'm running Edgy.  I checked to see if msttcorefonts is installed, and indeed it is.  Also, I installed nwn to a folder under my home directory /home/aleska/nwn rather than under /usr.  I thought that by installing to a folder under my home directory I shouldn't run into any permissions issues.  Right?

So, I'm not sure what to try next.  I'm optimistic as I can get through the splash screen and to the main menu...however, without the text there I'm pretty much dead. 

So, any suggestions are greatly appreciated.  

ps - I can't wait to start playing this again...since converting from windows 6 months ago I thought I had to kiss NWN goodbye...until I came across this how-to.  I've only played the single player campaign before, so also looking forward to trying out multi-player with some of you.  thx

---

### Post by leech on 2006-12-29
You can just right-click on the nwn folder in Nautilus and tell it to allow your user to read and write all then click the "Apply to all enclosed files" that should work.

Leech

---

### Post by aleska on 2006-12-29
Thanks again Leech!
Well, you know, I tried that...even made it read write executable for anyone.
I actually have all files and directories in nwn as rwxrwxrwx...so, I'm thinking it isn't a permission thing (at least that's my understanding...I am only 6 months new to linux).

Before I got your reply, I posted a similar inquiry on nwn.bioware.com/forums

zzqzzq_zzq had this to say:
> dialog.tlk is missing/unreadable/corrupt.

Check your installation and try again.

David

Possibly confirming this response, I searched my nwn directory, and sure enough, there is no dialog.tlk file.  

But, I'm not sure what this means.  So, I don't have it for some reason.  Where in the nwn's directory structure should it be located (i.e. what folder)?  Should this be a file that is on one of the four install disks?  If so, would I be able to find it on the cds and copy and paste into an appropriate directory and be good to go?  Or would something like this require a reinstallation? 

Upon fixing the issue, I'll be sure to post what steps I needed to take to fix.  But, for now, still need a little hand holding.

TIA!

---

### Post by rstreeks on 2006-12-30
I am running Dapper on a AMD64 when I tried to run the BinkPlayer I found out that there where some libraries missing.
see ldd output:
[FONT="Courier New"]/usr/local/games/nwn$ ldd BinkPlayer
        linux-gate.so.1 =>  (0xffffe000)
        libSDL-1.2.so.0 => /usr/lib32/libSDL-1.2.so.0 (0x5557d000)
        libpthread.so.0 => /lib32/libpthread.so.0 (0x55605000)
        libSDL_mixer-1.2.so.0 => /usr/lib32/libSDL_mixer-1.2.so.0 (0x55618000)
        libstdc++.so.5 => /usr/lib32/libstdc++.so.5 (0x55686000)
        libm.so.6 => /lib32/libm.so.6 (0x55740000)
        libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0x55762000)
        libc.so.6 => /lib32/libc.so.6 (0x5576d000)
        libasound.so.2 => /usr/lib32/libasound.so.2 (0x5589c000)
        libdl.so.2 => /lib32/libdl.so.2 (0x55959000)
        libX11.so.6 => /usr/lib32/libX11.so.6 (0x5595c000)
        libXext.so.6 => /usr/lib32/libXext.so.6 (0x55a42000)
        /lib/ld-linux.so.2 (0x55555000)
        libvorbisfile.so.3 => not found
        libvorbis.so.0 => /usr/lib32/libvorbis.so.0 (0x55a4f000)
        libogg.so.0 => /usr/lib32/libogg.so.0 (0x55a78000)
        libsmpeg-0.4.so.0 => not found
        libXau.so.6 => /usr/lib32/libXau.so.6 (0x55ad6000)
        libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0x55ad9000)[/FONT]

I am also running gentoo from this distribution I have copied the libraries that where missing.
The missing libraries where  copied in to the following directory: /emul/ia32-linux/usr/lib according to the debian/ubuntu documentation this is the place to put them. The following libraries I have copied and created the same symbolic links as in my gentoo distribution. All the files you see here are used by either NWN extensions nwmouse, nwmovies etc or for the BinkPlayer. 

[FONT="Courier New"]/emul/ia32-linux/usr/lib$ ls -l
total 396
lrwxrwxrwx 1 root root     11 2006-12-27 15:26 libelf.so -> libelf.so.1
-rwxr-xr-x 1 root root  76260 2006-12-27 15:25 libelf.so.1
lrwxrwxrwx 1 root root     21 2006-12-29 10:22 libsmpeg-0.4.so.0 -> libsmpeg-0.4.so.0.1.3
-rwxr-xr-x 1 root root 250144 2006-12-29 10:14 libsmpeg-0.4.so.0.1.3
lrwxrwxrwx 1 root root     22 2006-12-29 10:21 libvorbisfile.so -> libvorbisfile.so.3.1.0
lrwxrwxrwx 1 root root     22 2006-12-29 10:21 libvorbisfile.so.3 -> libvorbisfile.so.3.1.0
-r-xr-xr-x 1 root root  25564 2006-12-29 10:13 libvorbisfile.so.3.1.0
lrwxrwxrwx 1 root root     19 2006-12-27 15:49 libXcursor.so -> libXcursor.so.1.0.2
lrwxrwxrwx 1 root root     19 2006-12-27 15:49 libXcursor.so.1 -> libXcursor.so.1.0.2
-rwxr-xr-x 1 root root  34336 2006-12-27 15:48 libXcursor.so.1.0.2[/FONT]

I edited/created the configuration file for ldconfig: /etc/ld.so.conf
and add the following two lines into it.
/emul/ia32-linux/lib
/emul/ia32-linux/usr/lib

Then I ran ldconfig which recreates the ld.so.cache

From this point onwards I could run the *.bik files by the BinkPlayer.

I had downloaded the latests beta release off the nwmovies, nwlogging, nwmouse and nwuser from: [URL="http://home.woh.rr.com/nwmovies/nwlinux-beta.tar.bz2"]http://home.woh.rr.com/nwmovies/nwlinux-beta.tar.bz2
[/URL] and followed his instructions.

I am still using the original SDL libary from the game. My next step will be to create my own upgraded SDL library that has the SDL_WM_GrabInputRaw visible.

I know I have cheated by getting the missing libraries from my gentoo distribution. If any one can explain where to get those libraries from a regular source or how to compile them. I would be much happier.

---

### Post by aleska on 2006-12-30
So, after doing an md5checksum from the bioware guys, it was apparent that not only were three files missing or unreadable, but another 11 failed to match.  So, I decided to try a complete reinstall, this time using patch 167 in the script.

Install seemed to go smoothly...

I created a desktop launcher...and then, it doesn't launch, rather I get this error message.

> Details: Failed to execute child process "/home/aleska/nwn" (Permission denied)

Any ideas?

---

### Post by aleska on 2006-12-30
FYI - got it working...

Following the technical questions sticky thread at bioware [http://nwn.bioware.com/forums/myviewtopic.html?topic=347606&forum=72](http://nwn.bioware.com/forums/myviewtopic.html?topic=347606&forum=72) the first piece of advice is to make sure permissions are set correctly.  

> root @ host nwn # chown -R user:group .
root @ host nwn # chmod -R ugo=rX,ug+w .

So, I followed the above, using sudo and now everything seems to work properly.  

I found the keycode entries to be quirky.  If anyone was problems with that, let me know, I can at least tell you what I had to do to make them work.

Now, gameplay seems to be fine...however, sound is choppy.  I'll search this thread again to see if this issue was raised and resolved.  Otherwise, if anyone can tell me the quick fix for getting sound to be normal and not choppy, I'd be grateful.

Thanks!  Looking forward to playing with some of you.  Is there anyone who is interested?

---

### Post by aleska on 2006-12-30
...and once again the bioware forums gave me the simple answer.  In the nwn script, I just needed to remove ./lib from the ld_library_path (as is explicitly commented in the file).  Apparently, this uses the ubuntu distro's libSDL as opposed to the one that comes with nwn.  Simple enough.

I'm sure this wasn't news to any of you, but just in case, thought I'd restate it for purpose of solving choppy sound issue.

I've been playing for a half hour now with no problems whatsoever!  W00t!  Thanks to all!

Again, anybody interested in some multiplayer action, please let me know.

---

### Post by leech on 2007-01-11
> **rstreeks said:**
> 

[FONT="Courier New"]/emul/ia32-linux/usr/lib$ ls -l
total 396
lrwxrwxrwx 1 root root     11 2006-12-27 15:26 libelf.so -> libelf.so.1
-rwxr-xr-x 1 root root  76260 2006-12-27 15:25 libelf.so.1
lrwxrwxrwx 1 root root     21 2006-12-29 10:22 libsmpeg-0.4.so.0 -> libsmpeg-0.4.so.0.1.3
-rwxr-xr-x 1 root root 250144 2006-12-29 10:14 libsmpeg-0.4.so.0.1.3
lrwxrwxrwx 1 root root     22 2006-12-29 10:21 libvorbisfile.so -> libvorbisfile.so.3.1.0
lrwxrwxrwx 1 root root     22 2006-12-29 10:21 libvorbisfile.so.3 -> libvorbisfile.so.3.1.0
-r-xr-xr-x 1 root root  25564 2006-12-29 10:13 libvorbisfile.so.3.1.0
lrwxrwxrwx 1 root root     19 2006-12-27 15:49 libXcursor.so -> libXcursor.so.1.0.2
lrwxrwxrwx 1 root root     19 2006-12-27 15:49 libXcursor.so.1 -> libXcursor.so.1.0.2
-rwxr-xr-x 1 root root  34336 2006-12-27 15:48 libXcursor.so.1.0.2[/FONT]

I edited/created the configuration file for ldconfig: /etc/ld.so.conf
and add the following two lines into it.
/emul/ia32-linux/lib
/emul/ia32-linux/usr/lib

Then I ran ldconfig which recreates the ld.so.cache

From this point onwards I could run the *.bik files by the BinkPlayer.

I had downloaded the latests beta release off the nwmovies, nwlogging, nwmouse and nwuser from: [URL="http://home.woh.rr.com/nwmovies/nwlinux-beta.tar.bz2"]http://home.woh.rr.com/nwmovies/nwlinux-beta.tar.bz2
[/URL] and followed his instructions.

I am still using the original SDL libary from the game. My next step will be to create my own upgraded SDL library that has the SDL_WM_GrabInputRaw visible.

I know I have cheated by getting the missing libraries from my gentoo distribution. If any one can explain where to get those libraries from a regular source or how to compile them. I would be much happier.

I believe in my revisions to the HOW TO for the movies, I listed the packages required.  But here's a little hint on Debian and Ubuntu.  If there is a particular library that you need installed, and you don't know which package it is in, go to [http://packages.debian.org](http://packages.debian.org) (for Debian) or [http://packages.ubuntu.com](http://packages.ubuntu.com) (for Ubuntu.)

Then scroll down to where it says "Search for Contents of Packages".  Just cut and paste or type in the library (for example libXcursor.so.1.0.2) then select the distribution you are using and hit the search button.  Then you'll have what package(s) have that file in them.  In the case of libXcursor.so.1.0.2, the packages are libxcursor1 and libxcursor1-dbg.

Leech

---

### Post by leech on 2007-01-11
> **aleska said:**
> ...and once again the bioware forums gave me the simple answer.  In the nwn script, I just needed to remove ./lib from the ld_library_path (as is explicitly commented in the file).  Apparently, this uses the ubuntu distro's libSDL as opposed to the one that comes with nwn.  Simple enough.

I'm sure this wasn't news to any of you, but just in case, thought I'd restate it for purpose of solving choppy sound issue.

I've been playing for a half hour now with no problems whatsoever!  W00t!  Thanks to all!

Again, anybody interested in some multiplayer action, please let me know.

Glad to hear you've got it working.  The weird thing is, if I comment out the ./lib from the nwn script, my movies don't work.  Another poster had the same problem.  Glad to hear it's working.  I think the main reason the sound was chopping for you was that the SDL that comes with nwn is probably not compiled with the proper alsa compatibility.

Leech

---

### Post by mistermax on 2007-01-18
The version I've got is the "Best of Atari" one, I don't know if this is the same as the platinum or whatever?

Bascially, I've now tried the Linux client install from the icculus site and it seemed to have worked, however, when I run the nwn launcher, the screen goes dark and it crashes out...

If I run it from the shell, I see this:

max@ghengis:~/nwn$ ./nwn
mcop warning: user defined signal handler found for SIG_PIPE, overriding
Link points to "/tmp/ksocket-max"
can't create mcop directory


Sorry if I'm going over old questions, but I've not found out what I'm doing wrong yet.

Cheers guys (and guy-ettes)

---

### Post by parradux on 2007-01-22
I have the platinum edition of this game. I have fully followed this guide and when I try to run this game I get this error: 


Fatal signal: Segmentation Fault (SDL Parachute Deployed)


I have no idea what is the problem.

---

### Post by leech on 2007-01-22
I think there is a program called fixinstall in the nwn directory.

Try running that with ./fixinstall and then load up nwn.  

Leech

---

### Post by parradux on 2007-01-22
Checking for required files

PASSED: ambient directory exists
PASSED: data directory exists
PASSED: music directory exists
PASSED: override directory exists
PASSED: miles directory exists
PASSED: nwm directory exists
FAILED: chitin.key missing

Its been missing the key ever since I've updated. 

I still get the same error.

---

### Post by leech on 2007-01-22
I have a chitin.key file here, it's 943.4KB.  Look for it on your CD.  If you can't find it, I'll try to attach it in the morning after I get back from work.

Leech

---

### Post by parradux on 2007-01-22
I dont think thats the problem, because i've tried to run the game without updating it, and there was the same problem.

Any case please post the file.

---

### Post by mistermax on 2007-01-23
I get the same thing - missing chitin.key?

I've searched the 3 discs and can't find it. But these discs are the UK issue "Best of Atari", possibly a bit different?

I've got my serial inside it. But no chitin key....

---

### Post by parradux on 2007-01-23
Ok i've fixed mostly everything. No more SDL dumps or whatsoever. 

What I get now is this: 

Aborted (core dumped) 

And then nothing. 

Can someone help me?

---

### Post by leech on 2007-01-24
Do your log files show anything?  I'm not sure if attaching my chitin.key file is going to help, but I'll do so. 

According to [http://nwn.bioware.com/forums/viewtopic.html?topic=463726&forum=74](http://nwn.bioware.com/forums/viewtopic.html?topic=463726&forum=74) a re-install is about all that is going to help.

Leech

---

### Post by mmafterme on 2007-01-24
Does the install script from the first post support the 1.68 patch? Or do I need to download the 1.66 first and then manually update it to 1.68?

I couldn't find a definititive answer.

---

### Post by podfish on 2007-01-24
No Joy.  Using the uberscript under Edgy, fresh install, with some Automatix additions, NWN Platinum DVD, 1.67 patch, I am unable to:

1)  Start the game in under 2 minutes
2)  Start any module, including the basic Neverwinter Nights module.
3)  Save any settings whatsoever.
4)  1280x1024 doesn't work.  1280x960 and below does.  Defaults to 800x600, and, again, can't save settings.

I have done the following to attempt to fix this.

1)  sudo chown -R root:users /usr/local/games/nwn/
2)  sudo chmod -R 755 /usr/local/games/nwn
3)  Changed from the pre-installed nwn sdl libs to the ubuntu by changing the line in nwn.ini.
4)  prayed to Jebus to save my machine.
5)  wondered why this isn't a .deb.
6)  checked and rechecked the configs.
7)  reinstalled imagemagick.
8)  reinstalled libsdl
9)  reinstalled video drivers
10)  re-added myself to the /etc/group users entry
11)  added myself to /etc/group -- games entry, even though nothing is owned by games, see Item 1.
12)  whinged and cried and complained that, for some reason, ubuntu and apt appear to be giving me more trouble than gentoo and portage ever did.
13)  scoured google, the ubuntu forums, and other distro forums for similar threads, and solutions that didn't include only "chown and chmod", or "just install it as a user, not root."  That's not a solution that works for me--multiple users on the machine should be able to use this installation--and i'm not symlinking to my /home/steve from another user's homedir.  That's ugly as heck.

Gonna run off to forums.gentoo.org to see if i can find my posts on a manual install.  Meantime, any suggestions or questions as to what configs you might want posted would be appreciated!  thread looks pretty active, so, I'm hoping I get a response.

Thanks for supporting linux games on ubuntu--still a good distro, even if I'm too dumb to get it to work.  :-P :guitar: 

Podfish

---

### Post by mmafterme on 2007-01-24
> **mmafterme said:**
> Does the install script from the first post support the 1.68 patch? Or do I need to download the 1.66 first and then manually update it to 1.68?

I couldn't find a definititive answer.

After trying it out, the install script works fine with the 1.68 patch.

I went further and set up nwmovies only to find out there was no sound while watching the movies from the client, but they played fine with binkplayer. So, I did a little searching on the bioware forums and someone suggested to add the following line in ./nwn

```
export SDL_AUDIODRIVER=esd
```

It works perfectly, I get full sound everywhere, except when I first load into the menu.

---

### Post by podfish on 2007-01-25
OK.  Did something else, and I can get the game to work, with fonts, etc, keys installed, and the game runs without any major problems at low resolutions.

To get that to happen, I did a 

```

sudo chmod -R 770 /usr/local/games/nwn/

```
I still, however, get this error when I set a resolution higher than 1024x768:
```
steve@monolith:~$ nwn
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  135 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x187
  Serial number of failed request:  133
  Current serial number in output stream:  135

```
This happens whether I run as root or as myself.
I tried installing the newest nVidia drivers from nVidia.  No problems making that install happen, but still no joy.  If you want to see my xorg.conf, it is posted here as well:
```
Section "ServerLayout" 
 Identifier "X.org Configured" 
 Screen "Screen0" 0 0 
 InputDevice "Mouse1" "CorePointer" 
 InputDevice "Keyboard1" "CoreKeyboard" 
 EndSection 

Section "Module"

# This loads the DBE extension module.

    Load        "dbe"   # Double buffer extension

# This loads the miscellaneous extensions module, and disables
# initialisation of the XFree86-DGA extension within that module.
    SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection

# This loads the Type1 and FreeType font modules
    Load        "type1"
#    Load        "speedo"
    Load        "freetype"
#    Load        "xtt"

# This loads the GLX module
    Load       "glx"
# This loads the DRI module
#    Load       "dri"

EndSection

Section "ServerFlags"
#Option "Xinerama" "on"
EndSection 

Section "Files"

# The location of the RGB database.  Note, this is the name of the
# file minus the extension (like ".txt" or ".db").  There is normally
# no need to change the default.


# Multiple FontPath entries are allowed (which are concatenated together),
# as well as specifying multiple comma-separated entries in one FontPath
# command (or a combination of both methods)
#
#

    FontPath   "/usr/share/fonts/misc/"
    FontPath   "/usr/share/fonts/TTF/"
    FontPath   "/usr/share/fonts/Speedo/"
    FontPath   "/usr/share/fonts/Type1/"
    FontPath   "/usr/share/fonts/CID/"
    FontPath   "/usr/share/fonts/75dpi/"
    FontPath   "/usr/share/fonts/100dpi/"
    FontPath   "/usr/share/fonts/local/"
    FontPath   "/usr/share/fonts/TrueType/"
    FontPath   "/usr/share/fonts/freefont/"
    FontPath "/usr/share/fonts/corefonts"
# The module search path.  The default path is shown here.


EndSection



Section "Extensions"
        Option "Composite" "Enable"
        Option "RENDER" "Enable"
EndSection


Section "InputDevice"

    Identifier  "Keyboard1"
#    Driver      "kbd"
    Driver      "keyboard"
    Option "XkbModel"   "logiaccess"
    Option "XkbLayout"  "us"
    Option "XkbVariant" "basic"
EndSection

Section "InputDevice"

# Identifier and driver

    Identifier  "Mouse1"
    Driver      "mouse"
    Option "Protocol"    "Auto"
    Option "Device"      "/dev/input/mice"
    Option "ZAxis Mapping"  "4 5"
    Option "Buttons"    "7"
EndSection


Section "Monitor"

    Identifier  "Monitor0"
    HorizSync   30.0-107.0
    VertRefresh 48 - 160

EndSection

#Section "Monitor"
#        Identifier "Monitor1"
#        HorizSync 30.0-80.0
#        VertRefresh 50-100
#EndSection


Section "Device"
    Identifier  "card0"
    Driver      "nvidia"
    VideoRam    131072
    Option      "TwinView"      "True"
    Option      "RenderAccel" "true"
    Option "UseEdidFreqs"       "True"
    Option "MetaModes" "1280x1024,1280x1024;1280x1024,NULL;1280x960,1280x960;1280x960,NULL;1024x768,NULL;1024x768,1024x768;800x600,800x600;800x600,NULL;640x480,640x480;640x480,NULL;1600x1200,NULL"
    Option      "HWCursor"   "On"
    Option      "AllowGLXWithComposite" "true"
    Option      "NvAGP"  "2"
    Option     "TwinView" "true"
    Option      "SecondMonitorHorizSync" "30-64"
    Option     "Second MonitorVertRefresh" "50-100"
    Option     "TwinViewOrientation" "RightOf"
#    Option      "Xinerama" "on"
    Screen      0
# Insert Clocks lines here if appropriate
EndSection


Section "Screen" 
 Identifier "Screen0" 
 Device "Card0" 
 Monitor "Monitor0" 
 DefaultDepth 24 
 Option  "AddARGBGLXVisuals" "True"

 SubSection "Display" 
        Viewport 0 0 
        Depth 1 
        Modes "2560x1024" "1280x1024" "2560x960" "1280x960" "1024x768" "2048x768" "1600x600" "800x600" "1280x480" "640x480" "1600x1200"
 EndSubSection 

 SubSection "Display" 
        Viewport 0 0 
        Depth 4 
        Modes "2560x1024" "1280x1024" "2560x960" "1280x960" "1024x768" "2048x768" "1600x600" "800x600" "1280x480" "640x480" "1600x1200"
 EndSubSection 

 SubSection "Display" 
        Viewport 0 0 
        Depth 8 
        Modes "2560x1024" "1280x1024" "2560x960" "1280x960" "1024x768" "2048x768" "1600x600" "800x600" "1280x480" "640x480" "1600x1200"
 EndSubSection 

 SubSection "Display" 
        Viewport 0 0 
        Depth 16 
        Modes "2560x1024" "1280x1024" "2560x960" "1280x960" "1024x768" "2048x768" "1600x600" "800x600" "1280x480" "640x480" "1600x1200"
 EndSubSection 

 SubSection "Display" 
        Viewport 0 0 
        Depth 24 
        Modes "2560x1024" "1280x1024" "2560x960" "1280x960" "1024x768" "2048x768" "1600x600" "800x600" "1280x480" "640x480" "1600x1200"
 EndSubSection 

 EndSection 
```

I'm really having a hard time figuring out what I'm doing wrong; and I'm stymied by the fact that this was easier under another distribution, and permissions aren't causing this.  The only 2 things I can think of are the "ARGBGLXVISUALS" argument in xorg (I'll check that in a sec) and perhaps that the "latest" ubuntu version of the sdl libraries just aren't supporting what I'm wanting to do, which I've run into in the past.  Could the nvidia "twinview" xinerama implementation be causing this problem?  I'll try running with a backup xorg without twinview enabled, and see what happens...

---

### Post by leech on 2007-01-26
My guess is that it is due to the TwinView.  I did have it working across three screens with my Matrox Parhelia, but maybe it has problems either with nVidia's OpenGL itself, or with not finding the right resolution.

Though I don't remember exactly, but I think you might have to just manually change the nwn.ini to the resolution you want.

Give that a try.

Leech

---

### Post by podfish on 2007-01-26
Pretty sure it was twinview.  I de-installed the newer nvidia drivers because it was wreaking havoc with the "restricted-module" for my wireless card, which I also need, and causing actual driver conflicts between atheros and emu10k1 (audigy) under alsa, if you can believe that noise.  Anyhow it's all working now, except the other monitor.  I'll probably keep twinview, and just run NWN on another display.

Anyhow, if you get rid of twinview, it seems to work a lot better--although, i'm going to say it again, didn't have a problem under (ahem) gentoo.  My guess is the stock ubuntu libsdl package isn't compiled with xinerama support.

by the way, if anyone tries the "new" driver, it's full of cool whiz-bang features, like gui-level twinview setup in nvidia-settings, auto resolution capability detection (if supported by the monitor) and all kinds of neato stuff.  However, you'll probably break other things inadvertantly; so when you decide to revert back and wait for the cool driver to show up, or find a bleeding-edge repository, you can run the nvidiaxxxxxxx.run script with the --uninstall option.  You may find after re-installing apt's nvidia-glx that things are broken.  This is because the nvidia installer steps all over ubuntu's symlinks in the x config directories.  To fix, all you have to do is reinstall xserver-xorg-core, and reinstall your linux-restricted-modules packages, and nvidia-kernel-common and nvidia-glx for good measure.  reboot, and you should be good to go.

Again, thanks for being here with support.  This is probably the 2nd best support environment i've seen around the OSS community...and you're definitely gaining on 1st place.  keep up the good work, and you'll get guys like me to poke my nose around and help (or more likely hinder) once in a while!

By the way, anyone know what directories the save-files and character backups live in?  I'd kind of like to copy my old files over, since I'm near to finishing the original module, and don't want to start over.  Also, somone wanna point me to a good server/servers?  Are the ones mentioned earlier in the thread still OK?

The Podfish

---

### Post by podfish on 2007-01-26
Game looks great, movies work awesome, never seen them before, so kind of cool.  Little bit choppy at my resolution--tested it by 1600x1200, and it worked surprisingly well.  Much better at 1280x960... :0)

saves live in ..../nwn/saves (go figure.)  Was able to continue campaign where I left off, so way cool.

Thanks again for the great howto.

---

### Post by MaximB on 2007-01-27
Thanks for your great guide, it did helped me installing NWN although I didn't use your script but managed to combine my windows installation with the bioware Linux client files.
I have a small problem , I've followed your guide but I still can't run the game movies.
I use edgy and I did made "sudo dpkg-reconfigure dash".

My nwmovies.log :

```
./nwmovies.pl AtariLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: AtariLogo: Sat Jan 27 13:02:56 2007
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/AtariLogo.bik
NOTICE: ZoomSurface functions unavailable. The error was: libSDL_gfx.so: cannot open shared object file: No such file or directory
1169895776.493422: BinkLib: SDL_PRELOAD Initialized
*** glibc detected *** ./BinkPlayer: double free or corruption (out): 0x0809f8b0 ***

```

thanks in advance !
P.S - my movie files are in the /home/maxim/maxddark/games/nwn/movies I do NOT run this game from the CD/DVD.

---

### Post by leech on 2007-01-27
Damn!  I thought I had added that a long time ago!  

You need to install libsdl-gfx1.2-dev

I'll fix the HOW TO.

Leech

---

### Post by MaximB on 2007-01-28
I did it but the movies are still not running.
maybe I did something wrong in the process ?
 here is my movies installation :

```
maxim@maxim:~/maxddark/games/nwn$ ./nwmovies_install.pl /usr/lib/libSDL-1.2.so.0 
NOTICE: NWMovies: Executing: gcc -Wall -Inwmovies/libdis -g -fPIC -shared -Wl,-soname,libdisasm.so nwmovies/libdis/libdis.c nwmovies/libdis/i386.c -o nwmovies/libdis/libdisasm.so
NOTICE: NWMovies: Executing: gcc -Wall -shared -g -Wl,-soname,binklib.so nwmovies/binklib.c -o nwmovies/binklib.so /usr/lib/libSDL-1.2.so.0 -ldl -lelf  -lm
NOTICE: NWMovies: Executing: gcc -Wall -shared -g -DSDLLIB=\"/usr/lib/libSDL-1.2.so.0\" -I/usr/include/libelf -Inwmovies/libdis -o nwmovies/nwmovies.so nwmovies/nwmovies.c nwmovies/nwmovies_lookup.c nwmovies/nwmovies_cookie.c nwmovies/nwmovies_crumb.c nwmovies/nwmovies_link.S /usr/lib/libSDL-1.2.so.0 -ldl -lelf 
NOTICE: NWMovies: Please check for errors above
NOTICE: NWMovies: nwmovies executable built. Please modify your nwn startup command to
NOTICE: NWMovies: set LD_PRELOAD to 'nwmovies.so', before executing nwmain.

```

is everything fine ? was is wrong then ?

---

### Post by leech on 2007-01-28
Looks good to me.  I don't see why that wouldn't work.  Again after installing the libsdl-gfx1.2-dev package, post up your nwmovies.log and we'll see if it's missing something else.

Leech

---

### Post by MaximB on 2007-01-28
ok, here is it :

```
./nwmovies.pl AtariLogo >> nwmovies.log 2>&1
NOTICE: NWMovies.pl playing: AtariLogo: Sun Jan 28 17:24:02 2007
NOTICE: NWMovies: Executing: ./BinkPlayer ./movies/AtariLogo.bik
1169997842.786819: BinkLib: SDL_PRELOAD Initialized
*** glibc detected *** ./BinkPlayer: double free or corruption (out): 0x0809f5c8 ***
```

---

### Post by leech on 2007-01-30
Try this.

Open a Terminal, cd into your nwn directory and then run ```
./BinkPlayer movies/AtariLogo.bik
```

That should run the movie, if it does not, than BinkPlayer has an issue, which is what I expect is the issue.  Looks like it's having an issue with glibc.

Leech

---

### Post by MaximB on 2007-01-30
strange - it RUNS well in the Terminal
but NOT in the game.
what could it be...?

---

### Post by mistermax on 2007-01-30
Okay- I contacted Atari support and they say that the UK released Best of Atari is the same as the "Gold" edition.

So I went and got the icculus gold installer.

The only thing the installer keeps asking me to insert disc 2. Even when it is in... I've tried exporting the setup path as suggested in the icculus FAQ, but to no avail.

I feel like I'm getting closer here, but not quite...

Any suggestions?

---

### Post by leech on 2007-01-30
So does it only have the first expansion, Shadows of Undertide?  That's what the Gold edition is.

Breaking it down, from what I can recall.  You have the Original, then Gold Edition comes with the first expansion, Platinum comes with both expansions (Shadows of Undertide and Hordes of the Underdark) and Diamond comes with the both expansions and the Kingmaker module.

Leech

---

### Post by leech on 2007-01-30
> **MAXDDARK said:**
> strange - it RUNS well in the Terminal
but NOT in the game.
what could it be...?

I'm not entirely sure, but I would try running the script with the libSDL that Neverwinter Nights comes with.  I usually have better luck with that.

```
./nwmovies_install.pl lib/libSDL-1.2.so.0
``` from your nwn directory.

Leech

---

### Post by kmwatts on 2007-01-31
I have NWN working from a terminal, all is fine and well. But when I try to create a desktop launcher pointing it to the nwn file in the games directory. I get a flash of terminal opening then returns to my desktop. Any Ideas?

---

### Post by techstop on 2007-01-31
> **kmwatts said:**
> I have NWN working from a terminal, all is fine and well. But when I try to create a desktop launcher pointing it to the nwn file in the games directory. I get a flash of terminal opening then returns to my desktop. Any Ideas?

You need to give the full path to the executable, eg.

```
/home/techstop/nwn/nwn
```

I have also unticked the box that says "run command in a terminal". HTH.

---

### Post by kmwatts on 2007-01-31
I have tried it, as a application, application in terminal,and as file. I right click then create launcher, fill in name, browse to the script file. Which is in /home/kmwatts/nw/nwn , select a icon save/ok. Pops up on the desktop, double click on it and poof. Get a flash of terminal if I have it set up to run in one. Then nothing. I have also tried creating script file to change to that directory then execute nwn but that too just pops up terminal then returns to the desktop. Could this be a permission issue?
Ken

---

### Post by techstop on 2007-01-31
Here is my nwn script if that helps;

```
#!/bin/sh

# This script runs Neverwinter Nights from the current directory

cd /home/techstop/nwn

export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=./usr/lib:./miles:$LD_LIBRARY_PATH

./nwmain $@


```

The permissions of nwn and nwmain are 777.

---

### Post by kmwatts on 2007-01-31
Think I found it. My script file wasn't set up to change to the directory.....to many installs today...:D  thanks for the help.
Ken

---

### Post by mistermax on 2007-01-31
> **leech said:**
> So does it only have the first expansion, Shadows of Undertide?  That's what the Gold edition is.

Breaking it down, from what I can recall.  You have the Original, then Gold Edition comes with the first expansion, Platinum comes with both expansions (Shadows of Undertide and Hordes of the Underdark) and Diamond comes with the both expansions and the Kingmaker module.

Leech

Aaaah right- then in that case it's the original as it has no expansion pack on it.

So basically so far I've tried using the Diamon/Platinum installer and the Gold installer, both for the wrong purpose.

So is there a simple way to install the Original Version? Or even some comprehensive instructions?

---

### Post by leech on 2007-02-01
[http://www.liflg.org/?catid=6&gameid=65](http://www.liflg.org/?catid=6&gameid=65)

Try there for the 1.29 installer along with patches.  Actually Ravage has one as well, though I think this one supports all languages instead of individual language patches.

Leech

---

### Post by MaximB on 2007-02-01
> **leech said:**
> I'm not entirely sure, but I would try running the script with the libSDL that Neverwinter Nights comes with.  I usually have better luck with that.

```
./nwmovies_install.pl lib/libSDL-1.2.so.0
``` from your nwn directory.

Leech

sorry - no luck with the in-game movies :(

---

### Post by mistermax on 2007-02-01
I ran the installer and got this:

Fatal signal: Segmentation Fault (SDL Parachute Deployed)

---

### Post by Chachee on 2007-02-04
Thanks for the how-to.
  Just had a few questions - 

1.  Does the script account for the new 1.68 update?
2.  How does the script handle the Expansions?  Seems that's what gave most people a hard time on the official forums.
3.  What is the script written in?  I would like to look at it to get some ideas and all that since I'm still new to it.  If I try GEdit or cat it nothing/junk is displayed.

Again thanks for the how to!

JT

---

### Post by techstop on 2007-02-04
> **Chachee said:**
> Thanks for the how-to.
  Just had a few questions - 

1.  Does the script account for the new 1.68 update?
2.  How does the script handle the Expansions?  Seems that's what gave most people a hard time on the official forums.
3.  What is the script written in?  I would like to look at it to get some ideas and all that since I'm still new to it.  If I try GEdit or cat it nothing/junk is displayed.

Again thanks for the how to!

JT

1. I guess you want to know if you use the latest patch from step 5? I'm not sure. I installed a while ago with 1.67, then updated when 1.68 came out. You may have to do it that way too to be sure.
2. Expansions? This HOWTO is for the Platinum edition which contains SoU and HotU. Do you mean Premium Modules such as Kingmaker, Witches Wake etc? No idea, I don't have them.
3. It's a shell script as indicated by the sh extension. Not sure why it doesn't open in gedit, but you can have a look at the contents with;
```

grep |less install-nwn.sh
```

or even use vi.

---

### Post by leech on 2007-02-05
Talk about a royal pain in the butt!

Ok, basically the install-nwn.sh is compressed using makeself.  Unfortunately unmakeself is NO WHERE on the net for Linux, it's a FreeBSD program!  I tried compiling it in Ubuntu, but finally gave up, downloaded PC-BSD Vmware file and then installed it with that and extracted the install-nwn.sh file.  It contains several files, and I will attach it here for anyone who wants to hack away at this installer and add new features (NWMovies, Patches, et?)

While we're at it, how about making unmakeself available in the repositories, makeself is already.

Leech

---

### Post by Chachee on 2007-02-05
Techstop,
  I was talking about the premium content, but it seems they kinda have that figured out in the forums over at bioware, so I'll check there.

  I'll check the patch when I install and let you all know here if it worked well.

FYI here's the link for bioware's install for reference.  Don't remember if it's been posted already.

[http://nwn.bioware.com/forums/viewtopic.html?topic=469853&forum=72](http://nwn.bioware.com/forums/viewtopic.html?topic=469853&forum=72)

Leech,
  thanks for posting the script!  Sorry it was such a hassel.  I've converted almost completely to Linux at this point and figured it was time to start learning scripting.  I'm sure this will help.

JT

JT

---

### Post by leech on 2007-02-05
Not a problem, you know the funny thing is, I haven't played Neverwinter Nights in a long time now.  Usually I play it in cycles, get to a point where I'm stuck, then stop for a long time, then pick it up again :D  Probably time I pick it up again.

I will say that PC-BSD looks mighty smooth, though I'm usually not a KDE guy.  But at least I was able to use it for unmakeself.

Hopefully now someone can upgrade the script, I still don't know what happened to the original creator of it, all his websites have disappeared.

Leech

---

### Post by Chachee on 2007-02-06
I'm going to have to get another box working here soon.  So I'll destroy this script and see if I can get it working.  I'll have to read up on unshield and all that too.

JT

---

### Post by Daergeth on 2007-02-06
I just bought and got NWN in the mail, and its only 3 discs, and theyre not in zip format, but are .bzf. Anyone know how to install this? :(

---

### Post by daemoncat on 2007-02-07
I ran into EXACTLY the same thing, see page 12 of this forum, posts #117 & #118 for all the stuff I tried. After running down several false leads, it turns out that "bzf" stands for "Boiware Zip Format", and the format doesn't seem to be recognized by gzip. As far as I know, there is no working fix. I never got NWN installed, and I still haven't been able to figure out that "incompatible implicit declaration of built in function 'exit'" error nonsense for the only bzf Linux tool I found. 

I'm not a coder at all. This is past me, I suppose that it's possible to install via Windows and move the files to Linux, or maybe "unzip" the .bzf's in Windows, but as the file format seems so obscure, I doubt there's any Linux tool for it that works under Ubuntu. I'd be interested in any ideas. I sort of let it die. :(

---

### Post by leech on 2007-02-08
That's messed up.  My copy of Neverwinter Nights Platinum just uses 4 CDs and are all in the disk1.zip, disk2.zip, etc.  

I wonder how many editions of Neverwinter Nights are out there?  Where did you order this one from, I'd return it and tell them that you wanted it for running in Linux, but the edition they sold you wasn't compatible.

Worse thing that could happen is that they deny you, and you can then just download the original game from Bioware, using your CD-Key.  The problem though is that I don't know if you can download the resource files for the expansion packs.  You could also try emailing Bioware or Atari.

Leech

---

### Post by Chachee on 2007-02-09
Ok,
  Just got the Diamond DVD and ran through the script and install and here's how it went.  Everything installed, but the premium content.  No KingMaker got installed.  

  It ran through the wine part, I saw the Kingmaker screen, but it disappeared quickly and I saw all kinds of stuff scroll in the terminal.  However, when I load the game and go to preimum content there is nothing to select.

  Otherwise everything else went fine for diamond edition.

EDIT - Also, how would I load other modules and the CEP?

  Any clue as to where to start looking for problems/fix?

JT

---

### Post by leech on 2007-02-09
I don't currently own the Diamond edition, nor the Kingmaker premium module.

For the CEP stuff, all you have to do is download the .hak and .mod files that come with it and extract them into the appropriate folders.  Or you can go to [www.liflg.org](www.liflg.org) and download the CEP installer that uses the Loki installer.

Leech

---

### Post by Chachee on 2007-02-10
Hmm..

Well, it started to install Kingmaker and said it backed up my wine configs.  I'll have another look at the script and see if I can figure out what it did, and bounce it off the 'official' guide at bioware.

JT

---

### Post by daemoncat on 2007-02-10
Thanks for the ideas! I don't think I can use the "wanted Linux version". In little teeny tiny type it said on the box under "system requirements": "Windows". :-| 
As I never played online, the download using cd-keys option never occurred to me! Thanks for that tip. I'm working on that one now. FWIW, picked up the game at Wal-Mart. Didn't look any different than any of the other versions I'd seen anywhere else. Maybe it was a very old copy? Who knows.
In any case, I have something to work on for this. Thanks again.

---

### Post by leech on 2007-02-11
[http://mandrivausers.org/lofiversion/index.php/t31601.html](http://mandrivausers.org/lofiversion/index.php/t31601.html)

Found this while looking for solutions to the bzf and neverwinter nights issue.

Maybe this is the answer you seek?

Leech

---

### Post by daemoncat on 2007-02-11
Wow! I changed the CD-RW for a CD-ROM awhile back, and I just assumed that Edubuntu would follow the change and automagically update the fstab, symlinks, etc.. It didn't, so the NWN scripts couldn't find the files, and they usually just fail silently, unless one is watching the terminal window! Well, I got that sorted out and downloaded Ravage's plain NWN installer. 

But ... the terminal showed an "Extraction successful" for disk 1, then nothing after "Extracting Install Disc2", even though the gui asked for the 3 discs by name, and in order, and gave me a successful install when finished. ... so had the Loki and other installers I tried.

Odd things: 
1.) No apparent activity in the gui when disc 2 is worked on ... no "extracting file: xxx.xxx" messages or change in the "install progress" bar.
2.) Empty "portraits" directory. Maybe it is in a fresh install. I don't know, but it seems odd.
3.) Finally, after it's all done, this message when I try to run the "nwn" script to start the game:
[i]dad@server:~/nwn$ ./nwn
mcop warning: user defined signal handler found for SIG_PIPE, overriding
Creating link /home/daddykins/.kde/socket-renoir.
can't create mcop directory[/i]
Permissions are all set to my user.  :confused: 

Whew! It's educational, I guess. :|

---

### Post by daemoncat on 2007-02-11
Well, DOH! It's now the simple "export the correct sound drive" error! Maybe it'll work now ... ;-)

---

### Post by leech on 2007-02-12
Well, as far as portraits go, I wouldn't worry, I don't even have a portraits directory!

Congratulations.  I hope it's working.  I haven't really played it in KDE (since I use GNOME)

Let us all know how it goes.

Leech

---

### Post by daemoncat on 2007-02-28
:mrgreen:  Oh yeah! After using bits and pieces from the Bioware site, etc. It RUNS! \\:D/ 

Now, on to the CEP ... 

Thanks for all the help! :biggrin:

---

### Post by DarkW0lf on 2007-03-02
Does Diamond come in both CD and DVD's ?
Is Kingmaker only on the DVD ?
What about Auroa ? Any news on that or NWNedit ?

How many people got Diamond install with using this howto ? For a little while I considered if I wanted NWN or NWN2 but I think I want all the content that has been made for NWN instead.

Like leech said, "you could play it for years".

---

### Post by leech on 2007-03-03
According to Atari's website, the Diamond edition comes in DVD only.  I know the Platinum comes with both and a thick Manual, that's why in many stores I've seen the Diamond edition at a lower price than the Platinum, even though Platinum edition is missing the Kingmaker module.

Leech

---

### Post by gldvxx on 2007-03-11
this install process worked really great for me and made things a lot easier!  i had one issue though.  after in installed amarok i was getting an "mcop" error when i tried to run nwn from the terminal.  i found the fix in this forum:

[http://ubuntuforums.org/showthread.php?t=61511](http://ubuntuforums.org/showthread.php?t=61511)

which was to have it only use the ./miles library path:

export LD_LIBRARY_PATH=:./miles:$LD_LIBRARY_PATH

is this something that should be specified as part of a default install or only if you get the "mcop" error?  (btw i'm running gnome, not kde)

---

### Post by lindoran on 2007-03-18
you may want to mention to everybody who uses this script... you need wine installed to run it... i downgraded my install to i386 just cause i didn't want to bother with runing 32bit wine on 64bit ... just a thought.

---

### Post by techstop on 2007-03-18
> **lindoran said:**
> you may want to mention to everybody who uses this script... you need wine installed to run it... i downgraded my install to i386 just cause i didn't want to bother with runing 32bit wine on 64bit ... just a thought.

Which script? :confused: The howto in the first post absolutely does not need wine. NWN is a native linux client, no need for wine whatsoever.... :-k

---

### Post by leech on 2007-03-19
Yeah, it doesn't use wine at all.  It uses unshield to get the files out of the archive files on the DVD / CD, and that's it.  I never had to use wine.

Some of the other installers I've seen do.  But that was before unshield was written, I think most of those installers have disappeared.

There actually was a patch to be able to make wine compile cleanly for 64bit that I saw in the Debian package bug reports, but I'm not sure if it ever made it into the Ubuntu package.

[http://packages.debian.org/unstable/otherosfs/wine](http://packages.debian.org/unstable/otherosfs/wine)

Here is an actual package of wine for amd64!  Oddly enough they haven't put this into Feisty yet.  Though the version in Feisty is newer.  The debian package is 0.9.30, and the Ubuntu package is 0.9.32.

I haven't ran 64bit in a long time, 'cause every time I do there are certain things that I couldn't get working right, so I gave up until Debian gets proper multi-architecture working (which unfortunately won't happen until after Etch, which keeps getting pushed back).

Leech

---

### Post by zenrox on 2007-03-23
:popcorn: 
i have the diamond edition 
works just fine following the how to
just one sugestion
update the script to use the latest patch 1.29
and just for some functinality
add an option for extracting the zips(linuxver) for infinitedungons,wyverncrown,piratesoftheswordcoast
other wise all and all worked great
Ps
on the nwmovies part
dont forget to add chmod +x Blinkplayer

---

### Post by psynaps3 on 2007-03-23
In case anyone has problems with movies not playing within the game (but working if invoked directly via BinkPlayer), download libSDL 1.2.9 and try with it. I have been unable to get the movies to play ingame with anything newer than 1.2.9.

Many thanks to 'leech' for this wondeful howto 	:-({|=

---

### Post by JMO707 on 2007-03-24
Question: The script will work with 1.68 patch?

---

### Post by mmafterme on 2007-03-27
> **JMO707 said:**
> Question: The script will work with 1.68 patch?

Yes it will.

---

### Post by b3rx on 2007-03-29
i dont seem to be able to make the movies to work. but i was able to run the nwmovies.pl /usr/lib/ thing.. ./BinkPlayer /path/to/nwn/movies works in the console but in the game it doesn't..

please advice.

---

### Post by leech on 2007-04-01
> **zenrox said:**
> :popcorn: 
i have the diamond edition 
works just fine following the how to
just one sugestion
update the script to use the latest patch 1.29
and just for some functinality
add an option for extracting the zips(linuxver) for infinitedungons,wyverncrown,piratesoftheswordcoast
other wise all and all worked great
Ps
on the nwmovies part
dont forget to add chmod +x Blinkplayer

Fixed.  Can't believe I missed that.  Though you know there are always those things that a long time Linux user does automatically and just forgets to mention for new users :D

Leech

---

### Post by cjl2301 on 2007-04-02
Ok - before I run this, patch 1.29 seems way out of date.  Can the script be updated to use the latest patch?

Or can I autoupdate after installing via the script?

---

### Post by leech on 2007-04-02
It will download and install the 1.67 patch, then you can just extract the 1.68 on top of it.  So it's not horribly out of date.

Leech

---

### Post by cjl2301 on 2007-04-02
> **leech said:**
> It will download and install the 1.67 patch, then you can just extract the 1.68 on top of it.  So it's not horribly out of date.

Leech

Great, thanks!

---

### Post by jbumgar on 2007-04-05
What is this script you are referring to?  Do I have to download it from somewhere?  If I do where?

---

### Post by cjl2301 on 2007-04-08
> **leech said:**
> It will download and install the 1.67 patch, then you can just extract the 1.68 on top of it.  So it's not horribly out of date.

Leech

When I run the script - it auto downloads the 1.65 patch, not the 1.67 patch.  Do I have the correct script?

---

### Post by cjl2301 on 2007-04-09
> **cjl2301 said:**
> When I run the script - it auto downloads the 1.65 patch, not the 1.67 patch.  Do I have the correct script?

Nevermind - I grabbed the archive from topic #1 in this post and I got everything installed and working!

The only issue I had was that I originally installed as root into usr/local/games and when I started up NWN I saw the screen to enter my cd key, but there was no text on the screen.  That is, the buttons and controls were there but no text was on them.

So I removed that install and installed into my home dir.   I then copied my cdkey.ini that I had saved into the dir and everything worked fine.

Thanks for making this script!

---

### Post by leech on 2007-04-10
I didn't actually write the script, just the How To.  Unfortunately I've lost contact with the one who did write it.  He was going to create an updated script that supported movies, etc. 

Leech

---

### Post by inigo_jones on 2007-05-04
First off thanks for all the work thats gone into these resources/thread already....

I JUST got the diamond dvd edition of NWN. (for 25cents at a garage sale. sweet!) i found this thread, followed the instructions, and installed to my home directory.  the game seems to have installed fine. says everything is ready and i can run Neverwinter nights, then when i try to run ( ./nwn) the screen blacks, as it starts to run, then i crash back to my desktop with error -

Fatal signal: Segmentation Fault (SDL Paracute Deployed)

i ran ./fixinstall and everything cheack out fine...

i tried copying miles/ files to /usr/lib and ldconfig with no luck.

i thought the problem was running mergedfb dual monitor with my ati card, so i launched a single screen server layout with mergedfb diasbled, but still a Segmentation fault...

EDIT/UPDATE

deleting everything and reinstalling fixed it... dont know why but whatever - not complaining! oh, and it runs fine with the radeon driver with mergedfb enabled on ati radeon9200.

---

### Post by suso on 2007-05-07
> **techstop said:**
> Which script? :confused: The howto in the first post absolutely does not need wine. NWN is a native linux client, no need for wine whatsoever.... :-k

Actually, going only by what is in this howto and the script I downloaded today for use with the Diamond edition, I end up with the following error when I run through the script:

```
-e Testing for wine...
-e wine not found!
-e wine can be downloaded from [www.winehq.com/](www.winehq.com/)
-e Try again after installing
```


Then it gives me my prompt back.  So there is something trying to use wine.  Its not the install-nwn.sh script as there is no mention of wine in there.

---

### Post by leech on 2007-05-13
If you're using the script from the first page, it shouldn't ask for wine.  Though I noticed you had the -e in the front of that, which is an issue with using Dash instead of bash.  

Very strange that it would look for wine.  I know it tests if you have Unshield.

Leech

---

### Post by ashnazg on 2007-05-13
I got NWN installed and working on my AMD64 last night.  Here are the extra issues I dealt with when following the instructions on the first post of this thread:
- it DID require me to have WINE installed, which I could never find in any of the repositories...  I eventually found a new repository at winehq to add, which then allowed me to install it
- I installed it system-wide as root (well, sudo), and discovered when trying to play it as non-root that it complained of being unable to load modules (i.e. unzip stuff).  I eventually changed everything in the installation to me:games ownership, rather than the root:root it installed with.  Also, the default Feisty install does NOT have a "games" group already created (at least it my case it didn't).
- the nwmovies part won't compile on my box... aside from a slew of warnings, I get these errors:
   - nwmovies/nwmovies_link.S: Assembler messages:
   - nwmovies/nwmovies_link.S:13: Error: suffix or operands invalid for `push'
   - nwmovies/nwmovies_link.S:14: Warning: 4294967272 shortened to 232
   - nwmovies/nwmovies_link.S:15: Error: suffix or operands invalid for `push'
   - nwmovies/nwmovies_link.S:17: Error: `pusha' is not supported in 64-bit mode
   - nwmovies/nwmovies_link.S:19: Error: `popa' is not supported in 64-bit mode

In short, I'm playing it at the beginning tutorial stage, and playing as a non-root user... so I consider it a success.  I just wanted to point out the extra steps I did deal with (wine) and the issue with movies (64bit).

Thanks tor the original post with these instructions... they made a world of difference in my first Ubuntu installation of NWN.  I could NEVER get it running on Gentoo, thought I tried and tried.

---

### Post by phibonoacci on 2007-05-18
ok i got done with the install and made the icon... but it does nothing... it IS executable, 

phi@phi:~/NWN$ ./nwn
./nwn: line 5: cd: /home/phi/NWN/NWN: No such file or directory
mcop warning: user defined signal handler found for SIG_PIPE, overriding
Creating link /home/phi/.kde/socket-phi.
can't create mcop directory
phi@phi:~/NWN$ 


please help me i'm newesh to the down and dirty stuff here

philos

---

### Post by Daiimus on 2007-05-19
Hey, I recently added nwmovies to my version of NWN...and it ran perfectly...until I tried to play NWN in-game. I get alot of "lag" now, even when I turn my resolution and other graphics setting to the lowest of the low. Its not a big deal, I copied my entire nwn folder but I figured I should let you know. 

I'm pretty fresh at linux, I've been using ubuntu for almost a year but its been an uphill battle. If you want specs and such lemme know what output from what commands you need...

But for the most part I run an AMD Mobile 1.6, 5123MB RAM, ATI Radeon 9550. I got drivers going for the graphics card and everything. So I had the old version of nwn running real smooth.

NWmovies is definetly slick though and your install guide was AWESOME. My pc just doesn't dig on it.

---

### Post by Mazehero55 on 2007-05-19
um when I try to put in a directory to install in it puts out this:

/home/rave/library/games/nwn
[: 64: ==: unexpected operator
-e Possible write error
-e Please try a different folder or change permissions on /home/rave/library/games/nwn

can anybody help me?

---

### Post by Mazehero55 on 2007-05-21
okay I figured out how to install. I have Diamond edition so I found a great howto [here]("http://nwn.bioware.com/forums/viewtopic.html?topic=469853&forum=72") for the Diamond folks. But know that the patch listed there is out of date, so you need to get the new one.

Then on a side note I can't get the movies to play... The button isn't grayed out now and I can click on them but it does nothing...

any help

---

### Post by NJDubois on 2007-05-30
Alright, this is an odd, and strange question.  I 100% own nwn platinum.  Cd keys and all, loved the game under windows and now that i am windows free, I'm trying to install nwn with out wine.  The only problem is, I don't have the linux_data.zip file and its killing me.  I'm damn sure that this site, like all others doesn't even want to talk about torrents and what not but i really wanted that file so i tryed downloading it thinking hell, may be mine's just old and i can grab that one file and be ok.  but it didn't have it either.  I don't know what to do and I refuse to buy the game again just so i can get the one file I need.  I thought about sending a message to bioware, but ths ubuntu community is great.  ....i own all of you much thanks for helping me on my way to being windows free.....

Any ideas?  should i message bioware?  Is there somewhere i can download that one damned file so i can play nwn?

Thanks again, all of you.  It wont be long before the average joe that knows nothing about linux or computers will be able to say bye bye billy!

-Nick

---

### Post by wuzzeb on 2007-06-25
Here is a small howto to be able to switch back to your desktop while playing Neverwinter Nights, without having to deal with patching libSDL with fullscreen, compiling etc.

Note: I am going to assume nwn was installed in /opt/nwn, if you installed somewhere else you will just need to modify the paths slightly

1) Create a file  /opt/nwn/startnwn (for example, using gedit), and put the following into it
```

#!/bin/sh

display=:1
nwn=/opt/nwn/nwn
user=john

xinit /usr/bin/env DISPLAY=$display /bin/su -c $nwn $user -- $display

```

2) Modify the nwn= line to contain the path to the nwn script (the script you normally run)
3) Modify the user= to contain your login user name
4) If you don't understand what display is, leave it at :1,  otherwise set to whatever you want.

5) Test the script by running sudo /opt/nwn/startnwn  (The startnwn script must be run as root).  You can switch back and forth by using Ctl-Alt-F7 and Ctl-Alt-F8

6) Now you have two options

6.a) Type the password in every time you run nwn.  For this, edit the desktop launcher and/or menu icon to run the command "gksudo /opt/nwn/startnwn"  This will prompt for a password, then run the startnwn script

6.b) In a console, run "sudo visudo"  then add a line on the bottom

```

<username>   ALL = NOPASSWD: /opt/nwn/startnwn

```

modifying the <username> and path to startnwn.  sudo will now run the startnwn script without a password, so in the desktop launcher and/or menu icon command can be set to "sudo /opt/nwn/startnwn"


As I mentioned before, you can then switch back and forth using Ctl-Alt-F7 (desktop) and Ctl-Alt-F8 (nwn)

---

### Post by DarkW0lf on 2007-07-07
My question are for the DIamond DVD (that what's in the stores around here).

What files are downloaded by the script ?
I am dialup and if the downloaded patches are rather large (say over 15 MB) I'd rather go to the local college or some other place with hispeed connection and download them to my USB stick.

If I do that do I need both 1.67 and 1.68 or can I tell the script only to use 1.68 ?
What is CEP ? If there are some other files I might need I'll put them on the USB stick too.

---

### Post by DarkW0lf on 2007-07-07
Can't we just replace #! /bin/sh at the start of the script with #! /bin/bash if we want to use bash instead of dash and avoid the whole issue altogether ?

Whenever you get an error for WINE it might be for Kingmaker.
WINE isn't needed for nwn but it is for the Kingmaker installer (it is windows only).

I looked over quickly the forum for Diamond at Bioware's site and apparantly you need to map the nwn directory as a drive in WINE, run Kingmaker and then you can unmap nwn. ( not sure why there is a registry edit or why it's not a straight map ??? )

[http://nwn.bioware.com/forums/viewtopic.html?topic=469853&forum=72](http://nwn.bioware.com/forums/viewtopic.html?topic=469853&forum=72)

First post outlines this. I bet we could run our script and only need to follow the steps for Kingmaker after that.

From bioware's forum Wolfram's post:

Steps 1-3 involve installing WINE and making a config file
(You should already have this)

Link drive letter to nwn directory (must be current working directory).
ln -s $PWD $HOME/.wine/dosdevices/n\:

# Create registry patch.
cat << EOF > nwn.reg
[HKEY_LOCAL_MACHINE\Software\BioWare\NWN\Neverwinter]
"Location"="n:\\\"
EOF

Apply registry patch.
regedit nwn.reg

Link (or copy) KingmakerSetup.exe to nwn directory.
ln -s $NW_DIAMOND/KingmakerSetup.exe .

Run KingmakerSetup.exe to install the Premium Modules.
wine KingmakerSetup.exe

Remove obsolete files.
rm -f KingmakerSetup.exe nwn.reg 'premium/uninst Neverwinter Nights(TM) Kingmaker.exe'

---

### Post by Miss Kudos on 2007-07-16
I just wanted to thank Leech for posting the how-to.  I got NWN Diamond working.  Its smoother than butter on a baby's butt.  Except for the sound and music.  Its more like chopped garlic on a baby's butt.  I just now pulled myself away from the game long enough to post this.  I'll be seeing if I  can fix it later.

---

### Post by ChaOConnor on 2007-07-18
Whenever I try running the script I get to the part about where to install.  I created a NWN folder in my user directory but I get the following error:

-en Enter the install directory. (/usr/local/games/nwn): 
/home/cha/Games/NWN
[: 64: ==: unexpected operator
-e Possible write error
-e Please try a different folder or change permissions on /home/cha/Games/NWN

Please help, thanks!!!

---

### Post by ChaOConnor on 2007-07-18
Alright, so I'm at a complete loss.  (See post above this for my last attempt w/ the script).

Then I read the installation instructions on the BioWare page... no dice.

If I have the Platinum DVD, what is the best way to install?  Should I download the linux client from Bioware?  Do I extract the .CAB files from the DVD?  I'm so confused b/c it seems like there are various methods but each is suggesting different things.  

I still can't get the script to work w/ that weird error I listed above, but if all else fails, how do I install it manually?  I tried editing the script to see what steps it takes, but it kept saying it couldn't recognize the characters.

Thanks for reading this and taking the time to consider my question.

---

### Post by ChaOConnor on 2007-07-19
Okay, so the script wasn't working for me (See posts above).  I reverted to trying the official Bioware instructinos round here: [http://nwn.bioware.com/downloads/linuxclient.html](http://nwn.bioware.com/downloads/linuxclient.html)
If all I install is NWN Client, I can get in.  When I put the update in like the instructions say, I get the SDL error.  I have NWN Platinum on DVD, but at no point during the Bioware instructions is my DVD called for.  

I'm really at my wits end, I've tried 3 seperate methods to install this darn game and I can't get it to work. :confused:

Anyone... someone?  Please help!! Thank you!

---

### Post by DarkW0lf on 2007-07-20
I used a combination of bioware's instructions and the instructions from the forum.
I don't have broadband so I had to do a manual install like what is in the forums (bioware's forum I mean).
Game works for me but I can't get the movies to play, compile the so file okay and the game built the cache but nothing is playing in the game (Bink works manually). I would like an entry in the main menu but can't figure out how to get it to run the nwn script in stead of looking for another directory.

Movies and a slow mouse are the only game issues I have and I can partially live with the slow mouse. The game isn't really all that slow but it is noticeable when I try to move the mouse across the screen.

---

### Post by DarkW0lf on 2007-07-21
Okay I got the menu entry working. Reread the thread and saw the post regarding adding the cd command.
Though that oddly seems wierd when you tell it the exact path.

Doesn't the game also have an update function ?
I don't see in the gui where I would download updates. I took a screenshot of the game menu. Doesn't matter I manually put in 1.68 but I thought it was possible to update through the game. Oh well, guess I'll have to manually update in the future.

---

### Post by Nachowarrior on 2007-07-26
ok... I'm running amd 64 version of ubuntu.. latest. and i get this error on step five when entering the install path....   


[: 64: ==: unexpected operator
-e Possible write error
-e Please try a different folder or change permissions on /home/nachowarrior/Desktop/nwn


i tried owning the folder, i tried sudo... can't get past this step... I installed nwn fine just using the standard steps from their official site... but then i get this

Segmentation Fault (SDL Parachute Deployed)

after it changes my resoloution and looks like it's going to open... anyway. any ideas?

---

### Post by rweinreis on 2007-07-26
Great howto trying it now!

---

### Post by Elvish Legion on 2007-08-06
Nevermind forgot to do sudo dpkg-reconfigure dash

didnt relize even on fiesty you had to

---

### Post by cameran on 2007-08-13
Will this script also install version 1.68 (the latest version) or only 1.67 which is what the original post says?

any advice on how to install 1.68 patch if it is not supported?

thanks!

cameran

---

### Post by cameran on 2007-08-13
ok still digging through the thread and saw that the script downloads 1.67 and then you can install 1.68 over that.  i hope it works!  my copy should be arriving this week - i got it for $10 from gogamer.com :-)

i'll update with success/problems

cameran

---

### Post by mmafterme on 2007-08-15
> **cameran said:**
> ok still digging through the thread and saw that the script downloads 1.67 and then you can install 1.68 over that.  i hope it works!  my copy should be arriving this week - i got it for $10 from gogamer.com :-)

i'll update with success/problems

cameran

You can, in fact, just use the 1.68 patch. The script will ask which patch you are trying to install, where you can tell it to use 1.68 and it will work without any problems. Don't waste your time downloading two patches.

---

### Post by DarkW0lf on 2007-08-19
I am still not getting movies to play in game but will play in Bink.
Videos were cached and they are highlighted in the movies menu but won't play.

---

### Post by jasay on 2007-08-21
> **DarkW0lf said:**
> I am still not getting movies to play in game but will play in Bink.
Videos were cached and they are highlighted in the movies menu but won't play.
I was having trouble too until I tried ignoring this part of the howto:
> Additional Note: You do not need to remove the ./lib from the nwn script as it says. As a user has discovered, that will break the movies. Not sure why this is, since we specified to use the System SDL library, but there must be some incompatibilities.I renamed the folder and it recached the movies then ran with movies.  I'm not at all sure why it appears to work one way for some and another way for others.

I decided I didn't like waiting through the advertising movies at startup so I renamed all the files in the movies folder that had "logo" in them.  Startup is much faster and movies in game still work fine.

P.S.  A big thanks to leech for the howto that has made my first Neverwinter Nights experience fairly simple and fun.

---

### Post by DarkW0lf on 2007-08-24
What do you mean you renamed them ? Are they the wrong case ?

---

### Post by cogadh on 2007-08-30
Alright, now I'm totally confused. I've seen so many different versions of how to fix movie problems, I'm completely lost.

I have the problem where movies work, but have no sound in the game. They do work with sound if played outside the game with the Bink player. Does anyone have a clear answer on how to correct this problem?

---

### Post by th3rmos on 2007-09-01
I know this is an OOOOOLLLLLDDDDD Post, but I am having trouble getting this to install. The script will not complete. I get to the install directory, and it will not let me install this ANYWHERE! It says them when I try to install into a directory in my uses home directory. What am I doing wrong?

```
-en Enter the install directory. (/usr/local/games/nwn): 
/home/thermos/games/nwn
[: 64: ==: unexpected operator
-e Possible write error
-e Please try a different folder or change permissions on /home/thermos/games/nw
```

```
thermos@ubuntu-desktop:~$ cat /etc/lsb-releaseDISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.04
DISTRIB_CODENAME=feisty
DISTRIB_DESCRIPTION="Ubuntu 7.04"
thermos@ubuntu-desktop:~$ 

```

---

### Post by th3rmos on 2007-09-01
I missed a page reading through the thread, and found the answer. Thanks anyway.

---

### Post by Pheonix86 on 2007-09-30
Hey!

I just came across this post and thought I would give it a try!

I have Neverwinter Nights Deluxe Edition.
I installed the game using different installers than the one you suggested because my CDs came as individual game disks.
(nwn, HOU, SOU)

But, I followed your HOW TO on installing the movies, because this was the one thing that I really missed about playing the game!

So, I installed as you instructed, and the movies played, but there was no sound. More research led me to installing "libsdl debian ALL" and adding a line like "export (something) lib=esd" (sorry I can't remember what it was, but I found this in the bioware site, it has been mentioned in this post too, p23 I think.)

And there I had it, NWN with perfect sound and WORKING movies! :)

THEN... I soon found out that after playing the game for about 10 - 20 minutes, the sound would become so crackly to the point of not being able to play the game.

Restarting the game would put the sound back to perfect, but then again after another 10 - 20 minutes, the sound would become really bad again.

Has anyone else had this issue, and have you been able to fix it?

Any help would be appreciated!

Thanks!

Mikey

---

### Post by Bupert1 on 2007-10-10
Ok to everyone out there I am totaly new to linux period. I want to run my dimond dvd I read the first couple of pages and am totaly confused I dont know what a universe repository is or how to access it is there a cut and past full explination so I dont have to have a phd in programing or know how to write comand lines.
Robert

---

### Post by cogadh on 2007-10-10
Perhaps you should familiarize your self with Ubuntu a little bit more, before you try tackling a non-standard application install.

Ubuntu uses several server repositories for software packages. the "Universe" and "Multiverse" repositories contain mostly unsupported software packages (unsupported as in no tech support is provided). For more details and instructions on how to add the Universe repository, go here:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by Naegling23 on 2007-10-10
cool, I used this guide to install nwn a while (about a year?) ago.  It worked great, but I never bothered with the video.  Just decided to try again, took me all of 5 minutes.  Thanks for the guide!

---

### Post by Bupert1 on 2007-10-15
Ok got it all worked out this site got it installed smooth of silk now though when I try to save or load a created charecter nwn crashes any Ideas
Robert

---

### Post by cogadh on 2007-10-16
FYI - Upgrading to Gutsy broke the sound completely in NWN. Removing the "export SDL_AUDIODRIVER=esd" line I added to the nwn script to get sound in movies working restored the game sounds, but brought me back to movies with no sound. After some poking around, I found that I had to re-install the "esound" package (it was removed by the upgrade?), then I could put the line back in and movie sounds would work again. However, it does not work consistently at all (it appears to only work on every other movie played in sequence) and it sounds very crackly when it does work. If anyone has any ideas on how to get around this, it would be appreciated.

EDIT - I found an potential workaround for the sound problems with Gutsy. I just did a clean install of Gutsy and this time instead of installing the "esound" package, I installed the "pulseaudio" and "pulseaudio-esound-compat" packages, which allow the PulseAudio sound server act as a direct replacement for Esound. So far, it seems to work much better than regular Esound. I don't have the consistency problems I had before, and it appears that the sound is a lot less "crackly" than it was before. I only played for about 10 minutes, so I don't know if the sound will get completely garbled after 20 minutes of play like it used to, but I'll keep testing.

---

### Post by mmafterme on 2007-10-19
I've done a clean install of 7.10, and installed Neverwinter Nights and the movies, but when the movies play, they play on a semi transparent image of the previous menu. IE: if I start a new game, the chapter selection screen stay on screen while the movie plays. Also, the sound does not play when the movies are showing, but the sound works fine in game.

-EDIT-

After installing the pluseaudio and pulseaudio-esound-compat packages the sound plays fine, but I still have the problem with the movie being played on top of the previous menu item.

-EDIT 2-
After using Envy to install the 96.43.01 drivers, the movies play fine.

-EDIT 3-
Adding the line "export XLIB_SKIP_ARGB_VISUALS=1" to the nwn script with the latest nVidia drivers made everything work.

---

### Post by romana on 2007-10-21
Hey, may have missed this, but can't seem to find a solution in the thread so far.

I have a sweet little laptop with no cdrom/dvd drive. I usually grab stuff off of my main server, so it is not an issue. So I copied the Diamond edition onto my server, and then into my hdd. But the script spits at it not being a valid device. (It isn't, of course, it is a folder:)  )

Any suggestions? :confused:

---

### Post by zenrox on 2007-10-21
> **romana said:**
> Hey, may have missed this, but can't seem to find a solution in the thread so far.

I have a sweet little laptop with no cdrom/dvd drive. I usually grab stuff off of my main server, so it is not an issue. So I copied the Diamond edition onto my server, and then into my hdd. But the script spits at it not being a valid device. (It isn't, of course, it is a folder:)  )

Any suggestions? :confused:

try mounting the copyd folder to a dvd/cd mount point

---

### Post by linuxlizard on 2007-10-21
I'm having this problem on gutsy:
ERROR: ld.so: object './nwmovies.so' from LD_PRELOAD cannot be preloaded: ignored.

Also, the first thing that comes up I think is the cd key request. It shows the boxes, but no text explaining which cd key and there are two boxes beneath the cd key boxes - supposed to click on one but without the text I can't tell which one?

Any idea why I would have no text?

Also- for sound- I used gedit to make .openalrc in my home directory with this text:
(define devices '(native))

And that seems to work fine to eliminate sound crackling in this and other games.

---

### Post by romana on 2007-10-21
> **zenrox said:**
> try mounting the copyd folder to a dvd/cd mount point

Tried that, it had same error message.

---

### Post by mmafterme on 2007-10-21
> **linuxlizard said:**
> I'm having this problem on gutsy:
ERROR: ld.so: object './nwmovies.so' from LD_PRELOAD cannot be preloaded: ignored.

Also, the first thing that comes up I think is the cd key request. It shows the boxes, but no text explaining which cd key and there are two boxes beneath the cd key boxes - supposed to click on one but without the text I can't tell which one?

Any idea why I would have no text?

Also- for sound- I used gedit to make .openalrc in my home directory with this text:
(define devices '(native))

And that seems to work fine to eliminate sound crackling in this and other games.

For the text, you need to download msttcorefonts from the repositories. Did you follow the directions for installing nwmovies correctly?

---

### Post by linuxlizard on 2007-10-22
> you need to download msttcorefonts from the repositorie

Synaptic tells me they are already installed

> Did you follow the directions for installing nwmovies correctly?

I'll go back and check again, but I thought I followed the instructions step by step carefully.

---

### Post by Bupert1 on 2007-10-22
Hi well I figured it out after uninstall and reinstall many times it works perfectly so long as I dont add a portraits folder and try to use custom portraits if anyone knows a fix cool if not I will just use the ones that come with game.
Robert

---

### Post by mmafterme on 2007-10-22
> **linuxlizard said:**
> Synaptic tells me they are already installed



I'll go back and check again, but I thought I followed the instructions step by step carefully.

Strange....

Where did you install nwn to?

---

### Post by linuxlizard on 2007-10-22
/usr/local/games/nwn

---

### Post by cogadh on 2007-10-22
Install it in your home folder, that way you don't have problems with read/write permissions when doing the movie install/config.

---

### Post by linuxlizard on 2007-10-24
OK, I've gone back and re-installed in my home folder. The game now works perfectly- fonts working and so forth. BUT- no movies work. The movies menu is "unlocked"- you can click on it and click on the first movie but when you do nothing happens...

---

### Post by safetydan on 2007-10-28
Make sure you've run

```
chmod +x /usr/local/games/nwn/BinkPlayer
```

which should make your movies work for you. Assuming you've followed the other instructions.

---

### Post by zaniness on 2007-11-02
I've been looking for this for a long time.Thank you so much leech.It works great now.:):):KS By the way,sorry..but what's Kingmaker module?:confused:
__________________
[Engineers Beneficial Association](http://www.newsback.com/meba.html)

---

### Post by cogadh on 2007-11-02
An expansion pack that came with the Diamond edition of the game. It includes the Kingmaker, ShadowGuard and Witch's Wake modules, which I think you can get separately from the NWN store on BioWare's website.

---

### Post by mivo on 2007-11-05
Has someone tried the instructions on how to install the NWN movies on a 64-but Gutsy system? I'm a bit uneasy about adding the building tools, wondering if they will somehow mess up my installation?

By the way, I installed NWN without using any of the other scripts. Just followed the steps in [this post]("http://nwn.bioware.com/forums/viewtopic.html?topic=417536&forum=72"). (I already had the 32-bit libs from installing a 32-bit browser and Skype.)

---

### Post by thrice_loved on 2007-11-17
I am now running Neverwinter Nights Gold and Hordes of the Underdark. I followed the instructions here:
[http://nwn.bioware.com/downloads/linuxclient.html]("http://nwn.bioware.com/downloads/linuxclient.html")
They're long, but they work. :)

This computer used to run neverwinter nights on XP now all Ubuntu and (dare I say it) I think it runs more smoothly under Ubuntu.

Kudos to Bioware for releasing this to Linux :D

---

### Post by DarkW0lf on 2007-12-08
I still cannot get the movies to play.

I have the latest client running on Ubuntu Gutsy.
I compiled the movies as listed in the instructions and built the cache.
Tried this with ./lib in the path of the nwn script and without.

Movies play fine with the stand alone Bink player, in the game menu the screen goes dark for a second and there is a beep. But that's it and  I am right back at the menu again and movies won't play during the game.

---

### Post by Slingshot on 2007-12-19
Hi all, just wanted to check if anyone has something similar happen to them with Neverwinter Nights. Install went fine except for movies (Thanks Leech for the script). Following zzqzzq_zzq over at the Bioware forums I built a patched SDL. None of above made movies work in NWN, so I gave up trying to get them working.

Recently I decide to enable the compizfusion desktop and when I ran NWN, the movies flashed on screen, disappeared with the sound still playing. A little missing around found it worked in windowed mode and changing the NWN resolution from 1280x800 to 1024x768 it all came good. 

Anyone know how to disable the intro movies? there starting to bore me now. :)

---

### Post by DarkW0lf on 2007-12-22
Someone earlier said to rename them and that kept the intros from playing.

What did you do with compiz to get movies working ?

---

### Post by Slingshot on 2007-12-24
> Someone earlier said to rename them and that kept the intros from playing.

What did you do with compiz to get movies working ?

Nothing out of the ordinary. Enabled effects. Installed Emerald. Installed AWN. I must have spent countless hours trying to get them to work before, my bottom jaw hit the keyboard when the movies flashed up after enabling Compiz. If i disable the effects, it goes back to the skipping right past the movies.

---

### Post by Dwiman89 on 2007-12-25
IM very confused. I have Neverwinter Nights Diamond. It says for windows on the box. Does following the instructions get mine to work? I didn't see anything mentioned about wine or anything like it. Do I have to go out and buy a linux version of the game???????

---

### Post by mivo on 2007-12-25
Bioware offers a client for Linux for NWN, which can be downloaded for free. The CDs or the DVD you have are fine -- you need the data from them (graphics, sound, etc.). No need for Wine, it runs natively in Linux.

---

### Post by Perfect Storm on 2007-12-25
I wrote a installation guide for download installation of NWN for Ubuntu: [http://gaming.gwos.org/doku.php/guides:64bit:nwn](http://gaming.gwos.org/doku.php/guides:64bit:nwn)

just ignore the installaion of ia32-libs if you're not using 64-bit

---

### Post by 08runner on 2008-01-14
This might help those eager to get movies working in NWN.

I had the same problem which was amazingly solved by setting my desktop back to pure gnome (removing all KDE libraries). Suddenly I could see all movies in NWN!

As soon as I installed a single KDE library movies were gone...:confused:

---

### Post by diebydesire on 2008-01-26
i have everything up and running thanks leech... my issue is my gamespy connection keeps timing out. would that have anything to do with having to forward any ports or anything

---

### Post by Zuuswa on 2008-01-26
you shouldnt have any disconnect errors, no ports need to be opened up for the client.  It might be that your ISP is throttling the traffic through those known ports.  NAT translation may be to blame as well, if you have a single IP and are sharing it via a router.  If you plug your computer to the modem directly or turn off NAT translation, make sure you have sufficient security on your box.

---

### Post by ronin69hof on 2008-01-29
Hey,

did anyone get PRC31e and CEPv2 with the merge hack to work?  If so can someone post instructions on how to do it.

thanks

ronin

---

### Post by chochem on 2008-02-06
This is probably going to drown in the torrent of posts but I think that a link to the "just-copy-your-darn-windows-nwn-install-and-be-done-with-it-(almost)" guide supplied by bioware would save a lot of people a lot of trouble - presuming that you have a windows install somewhere (or one you can borrow). It doesn't contain as many steps as this one and it doesn't get outdated as easily (where do i find the linux 1.67 patch?):

[http://nwn.bioware.com/downloads/linuxclient.html#wininstall](http://nwn.bioware.com/downloads/linuxclient.html#wininstall)

Basically it's copy some NWN data folders into a linux NWN folder, download and extract a set of linux binaries into same folder, same for linux specific patch, run a simple script (no options) and you're done. Just a recommendation.

---

### Post by chochem on 2008-02-07
BTW Does anyone know if there is a way to switch workspaces while it's running so I can use Firefox as a reference? Ctrl+Alt+arrowkeys doesn't register....

---

### Post by mauser on 2008-02-11
Hello Folks,

I dual boot (for now).
So I just copied my entire NwN folder from my Win partition, then did the ./fixinstall

---

### Post by jdunn on 2008-02-13
I know its old but thanks for the good How-To, Leech.  I have the original NWN, SoU and HotU CDs which I've installed on Linux before.  However,  I always wanted to have the movies so I recently read through your How-To for that...No Problems.  \\:D/

---

### Post by mmafterme on 2008-02-23
> **chochem said:**
> BTW Does anyone know if there is a way to switch workspaces while it's running so I can use Firefox as a reference? Ctrl+Alt+arrowkeys doesn't register....

Try this post.

[http://ubuntuforums.org/showpost.php?p=2912904&postcount=280](http://ubuntuforums.org/showpost.php?p=2912904&postcount=280)

---

### Post by Alterax on 2008-03-04
> **wuzzeb said:**
> Here is a small howto to be able to switch back to your desktop while playing Neverwinter Nights, without having to deal with patching libSDL with fullscreen, compiling etc.

Note: I am going to assume nwn was installed in /opt/nwn, if you installed somewhere else you will just need to modify the paths slightly

1) Create a file  /opt/nwn/startnwn (for example, using gedit), and put the following into it
```

#!/bin/sh

display=:1
nwn=/opt/nwn/nwn
user=john

xinit /usr/bin/env DISPLAY=$display /bin/su -c $nwn $user -- $display

```

2) Modify the nwn= line to contain the path to the nwn script (the script you normally run)
3) Modify the user= to contain your login user name
4) If you don't understand what display is, leave it at :1,  otherwise set to whatever you want.

5) Test the script by running sudo /opt/nwn/startnwn  (The startnwn script must be run as root).  You can switch back and forth by using Ctl-Alt-F7 and Ctl-Alt-F8

6) Now you have two options

6.a) Type the password in every time you run nwn.  For this, edit the desktop launcher and/or menu icon to run the command "gksudo /opt/nwn/startnwn"  This will prompt for a password, then run the startnwn script

6.b) In a console, run "sudo visudo"  then add a line on the bottom

```

<username>   ALL = NOPASSWD: /opt/nwn/startnwn

```

modifying the <username> and path to startnwn.  sudo will now run the startnwn script without a password, so in the desktop launcher and/or menu icon command can be set to "sudo /opt/nwn/startnwn"


As I mentioned before, you can then switch back and forth using Ctl-Alt-F7 (desktop) and Ctl-Alt-F8 (nwn)

Sounds good to me, but there's one minor change I would make.  Once you have created and tested the /opt/nwn/startnwn script, it's still a PITA to drop to the terminal and sudo it.  So instead, just set the sticky bit.  Then, regardless of who runs it, the script will run as if root had executed it:

First, set the owner of the script to root:

**sudo chown root:root /opt/nwn/startnwn**

Next, set the permissions as follows:

**sudo chmod 1755 /opt/nwn/startnwn**

Finally, make a symbolic link from it to the /usr/bin directory so you don't have to navigate to it every time:

**sudo ln -s /opt/nwn/startnwn /usr/bin/.**

Now all you have to do is execute that file (which can be built into a launcher icon), and it will run without taking extra steps later.

(A word of caution.  Go easy on the sticky bits unless you know that the program is safe to begin with, otherwise you can accidentally screw something up later.)

--Alterax

---

### Post by Xenoc on 2008-03-20
ok I've been trying all morning to get my cd version of platinum edition installed; but every time I try to get it installed i get the fallowing error. I always get this error at the installation path step.

```
/home/xenoc/nwn 
[: 64: ==: unexpected operator
-e Possible write error
-e Please try a different folder or change permissions on /home/xenoc/nwn

```

Can anyone help me with this?  I really want to play.

---

### Post by rjb26 on 2008-03-20
> **bplus said:**
> anyone know if this method works with the NWN delux collection. (Bought in the UK).


I think it does.

---

### Post by kidux on 2008-03-20
> **Xenoc said:**
> ok I've been trying all morning to get my cd version of platinum edition installed; but every time I try to get it installed i get the fallowing error. I always get this error at the installation path step.

```
/home/xenoc/nwn 
[: 64: ==: unexpected operator
-e Possible write error
-e Please try a different folder or change permissions on /home/xenoc/nwn

```

Can anyone help me with this?  I really want to play.

I am getting this same error with my DVD version of platinum. Doesn't matter what folder I tell it to install to, I either get this message or one telling me permission is denied.

---

### Post by kidux on 2008-03-21
> **chochem said:**
> This is probably going to drown in the torrent of posts but I think that a link to the "just-copy-your-darn-windows-nwn-install-and-be-done-with-it-(almost)" guide supplied by bioware would save a lot of people a lot of trouble - presuming that you have a windows install somewhere (or one you can borrow). It doesn't contain as many steps as this one and it doesn't get outdated as easily (where do i find the linux 1.67 patch?):

[http://nwn.bioware.com/downloads/linuxclient.html#wininstall](http://nwn.bioware.com/downloads/linuxclient.html#wininstall)

Basically it's copy some NWN data folders into a linux NWN folder, download and extract a set of linux binaries into same folder, same for linux specific patch, run a simple script (no options) and you're done. Just a recommendation.

Thanks, this was the simplest way of going about getting NWN installed and running. Thank god for VirtualBox, lol!. :KS

---

### Post by chochem on 2008-03-21
> **kidux said:**
> Thanks, this was the simplest way of going about getting NWN installed and running. Thank god for VirtualBox, lol!. :KS

You're welcome :) I actually wrote I script to automate the process but never got round to polishing it off - and I guess I only really needed to use ot once....

---

### Post by Danijel Snajder on 2008-03-26
> **Xenoc said:**
> ok I've been trying all morning to get my cd version of platinum edition installed; but every time I try to get it installed i get the fallowing error. I always get this error at the installation path step.

```
/home/xenoc/nwn 
[: 64: ==: unexpected operator
-e Possible write error
-e Please try a different folder or change permissions on /home/xenoc/nwn

```

Can anyone help me with this?  I really want to play.

> **kidux said:**
> I am getting this same error with my DVD version of platinum. Doesn't matter what folder I tell it to install to, I either get this message or one telling me permission is denied.

Me too, same problem, anyone?

---

### Post by Danijel Snajder on 2008-03-26
> **leech said:**
> Here is the answer to this one..... lousy Edgy and it's usage of DASH!

What you'll need to do is temporarily (or permanently) change sh to point to bash.  This is actually rather easy, at least.

```
sudo rm /bin/sh
sudo ln -s /bin/bash /bin/sh
``` then you can run the install script.  Note that it no longer has the funky -en and that it now will actually download the patch etc.

To return to using dash, just simply ```
sudo rm /bin/sh
sudo ln -s /bin/dash /bin/sh
```

Leech

Think this is the answer ! On page 18.

---

### Post by iSplicer on 2008-03-26
Will this work with gutsy?

---

### Post by Danijel Snajder on 2008-03-27
> **iSplicer said:**
> Will this work with gutsy?

Yes. The best and easiest method to install PLATINUM NWN with 1.68 patch and to work with feisty, gutsy, hardy... is to:

1) download script from:

[http://www.paradoxinc.net/linux/neverwinter-nights-platinum-editon-script-update/](http://www.paradoxinc.net/linux/neverwinter-nights-platinum-editon-script-update/)

2) and client and patch from

[http://nwn.bioware.com/downloads/linuxclient.html](http://nwn.bioware.com/downloads/linuxclient.html)
[http://nwn.bioware.com/support/patch_linuxhotu168.html](http://nwn.bioware.com/support/patch_linuxhotu168.html)

3) install packets from ubuntu repository: unshield, libunshield, and maybe msttcorefonts

4) then just run script and answer few questions. Cant be easiest.

P.S. Script on first page, i dont recomend, and if you have separate versions then use installers from [http://icculus.org/~ravage/nwn/](http://icculus.org/~ravage/nwn/)

---

### Post by real_deal_caulfield on 2008-03-27
Thanks for this very useful script.

---

### Post by Danijel Snajder on 2008-04-02
Also, i saw that people having problems with sound and nwn. Well I was not exception, i have **no sound at all.**
So i figured that patch overwrited files in /miles directory with windows files. And the solution is to:

[B]Manualy extract from linux client "/miles" directory and then overwrite with this files "/miles" directory in instalation directory.
[/B]


And if you have **bad sound** this is because game uses their older libaries, so you want use ubuntu´s new libaries. And the solution is to:

Open nwn file (the one with you run game) with text editor and in line

```
export LD_LIBRARY_PATH=./lib:./miles:$LD_LIBRARY_PATH
```
delete word ./lib: so that looks like this

```
 export LD_LIBRARY_PATH=./miles:$LD_LIBRARY_PATH
```

Enjoy...

---

### Post by DarkSim on 2008-04-02
I got an updated the movie script recently [3-08-08]. Now I got the movies to run great. The only problem is you have to play in windowed mode since the Bink player runs the movies in a separate window and you can't skip them.

So what you need to do is open up the nwn.ini and add the line 'AllowWindowedMode=1' in the Display options section. You also need to change the 'Fullscreen=1' to 'Fullscreen=0'. You should also bump down the resolution a notch so the window fits. You can do this in Height and Width. For 1280*1024 monitor I set them to 864 and 1152 respectively.


I didn't notice any degradation of sound after a half hour like the old movies script did to me so hopefully it will work out for all of you.

---

### Post by Taleman on 2008-04-09
Okay I did the install the way mentioned in the Bioware forums. Then I followed the steps here to get the movies working and it worked perfectly except if i dont remove the ./lib the I get no sound at all not even in the movies, however if I do remove it the game crashes on startup. is there anyway to solve this

---

### Post by Virgilius on 2008-04-13
This might be a really silly question, but does this guide work for Gutsy users as well?

---

### Post by arcanistherogue on 2008-04-14
> **Virgilius said:**
> This might be a really silly question, but does this guide work for Gutsy users as well?

Yes, I got this working on Gutsy through this guide.

---

### Post by martin saint martin on 2008-04-17
when following this how to i get to step 5 then nothing.  the terminal opens and asks for which version i have.  i'll enter 6(diamond dvd) hit enter and the terminal says "testing for wine..." and then closes.  i don't have wine, heard it was only for 32bit, also it looks like this how to is a wine free way to play.  i do have the unshield and libunshield installed.  what am i missing to move deeper into my nwn install?  is there something different i need to do for ubuntu 7.10 amd64?

---

### Post by mrgibson on 2008-04-24
Something that may help somes, if your nwn segfault just after running the executable, try removing nwn.ini first (the game will create a new one) 

It worked for me :) (Using both 1.68 and 1.69b6)

---

### Post by techstop on 2008-04-25
> **Danijel Snajder said:**
> Yes. The best and easiest method to install PLATINUM NWN with 1.68 patch and to work with feisty, gutsy, hardy... is to:

1) download script from:

<SNIP

Hmmm, I went to the link and the page got blocked by FF3 as being malware. More info here;

[http://www.stopbadware.org/reports/container?source=Firefox&version=3.0b5&reportname=http://www.paradoxinc.net/linux/neverwinter-nights-platinum-editon-script-update/](http://www.stopbadware.org/reports/container?source=Firefox&version=3.0b5&reportname=http://www.paradoxinc.net/linux/neverwinter-nights-platinum-editon-script-update/)

Beware!

EDIT: maybe it's the paradoxinc.net domain that is being blocked, not suggesting that the actual script is dodgy. Anyway, the original script seems to be working in hardy once you change to bash as suggested for edgy

---

### Post by Danijel Snajder on 2008-04-25
Dont know what happened to that site then,
but install script is worth downloading...

here´s then direct link to the script

[http://www.paradoxinc.net/files/icarus/scripts/install-nwn.sh](http://www.paradoxinc.net/files/icarus/scripts/install-nwn.sh)

or better here in attachment if this site goes down

---

### Post by kforum on 2008-05-11
thank you daniel i got it installed but cant seem to run it... the sh script seems to load and...nothing?
any hint on how to run the game?

---

### Post by kforum on 2008-05-12
i have tried teh whole 'remove ./lib idead, but i still can run it. it executes the program, then crashes immediately. o.O

---

### Post by Kymus on 2008-05-12
I followed the given directions and experienced no problems, but, when I try to run NWN, nothing happens... it just sits there :confused:

---

### Post by Aeroclub on 2008-05-31
Hey guys, NWN launches without a problem for me, however I can't get a movie thing to work...THis is what I get after typing './nwmovies_install.pl /usr/lib/libSDL-1.2.so.0' :

NOTICE: NWMovies: Executing: gcc -m32  -I/emul/ia32-linux/usr/include -L/emul/ia32-linux/usr/lib -L/emul/ia32-linux/lib -L/lib32 -L/usr/lib32 -Wall -Inwmovies/libdis -g -fPIC -shared -Wl,-soname,libdisasm.so nwmovies/libdis/libdis.c nwmovies/libdis/i386.c -o nwmovies/libdis/libdisasm.so
NOTICE: NWMovies: Executing: gcc -m32  -I/emul/ia32-linux/usr/include -L/emul/ia32-linux/usr/lib -L/emul/ia32-linux/lib -L/lib32 -L/usr/lib32 -Wall -shared -g -Wl,-soname,binklib.so nwmovies/binklib.c -o nwmovies/binklib.so /usr/lib/libSDL-1.2.so.0  -ldl -lelf -lm
/usr/lib/libSDL-1.2.so.0: could not read symbols: File in wrong format
collect2: ld returned 1 exit status
NOTICE: NWMovies: Executing: gcc -m32  -I/emul/ia32-linux/usr/include -L/emul/ia32-linux/usr/lib -L/emul/ia32-linux/lib -L/lib32 -L/usr/lib32 -Wall -shared -g -DSDLLIB=\"/usr/lib/libSDL-1.2.so.0\" -I/usr/include/libelf -Inwmovies/libdis -o nwmovies/nwmovies.so nwmovies/nwmovies.c nwmovies/nwmovies_lookup.c nwmovies/nwmovies_cookie.c nwmovies/nwmovies_crumb.c nwmovies/nwmovies_link.S /usr/lib/libSDL-1.2.so.0  -ldl -lelf
/usr/lib/libSDL-1.2.so.0: could not read symbols: File in wrong format
collect2: ld returned 1 exit status
NOTICE: NWMovies: Please check for errors above
NOTICE: NWMovies: nwmovies executable built. Please modify your nwn startup command to
NOTICE: NWMovies: set LD_PRELOAD to 'nwmovies.so', before executing nwmain.

I use 64bit, though it might be a problem, since nwmovies manual says to install "appropriate packages" if I use 64bit, but it didn't specify which...
Any ideas?

---

### Post by kforum on 2008-05-31
how did u manage to get it working/runing?

edit: could u also post ur startup script

---

### Post by Aeroclub on 2008-06-01
Unpacked it all, launched "fixinstall" and edited a script as instructed here. Actually, the script works either way: by deleting "./lib" or by addind a custom line of resources location.

---

### Post by kforum on 2008-06-01
here:
u need these files...

belfg0
libelfg0_dev
libsdl1.2_debian
libsdl1.2_dev
libsdl-mixer1.2
libsdl-gfx1.2-4
libsdl-gfx1.2-dev
libsdl1.2debian-all --not needed...maybe...

after searching a lot i found that info, though i havent been able to get the game to run yet, so.. good luck

also, dont forget this, afterwards...
export SDL_AUDIODRIVER=alsa, esd, or whatever u use.
for me it was '=alsa'.

hope my synthax makes sence

also, try the new nwnmovies4 patch:[http://home.woh.rr.com/nwmovies/nwmovies-v4-public.20080512.v4rc1.tar.gz](http://home.woh.rr.com/nwmovies/nwmovies-v4-public.20080512.v4rc1.tar.gz)

or look here:[http://nwn.bioware.com/forums/viewtopic.html?topic=629464&forum=72&sp=0](http://nwn.bioware.com/forums/viewtopic.html?topic=629464&forum=72&sp=0)

gluck

---

### Post by buntunub on 2008-06-06
Hey, using [this]("http://nwn.bioware.com/forums/viewtopic.html?topic=469853&forum=72&sp=0") thread I was able to get the Diamond Edition installed minus the Premium content. I get stuck on the KingmakerSetup.exe part though. Everytime I try to run that symlink he has me create it runs and then I get a popup message about not being able to find the game, etc. Anyone know the fix for this?

---

### Post by bardic on 2008-06-08
Hey all. Have a rather annoying issue here. Had this working on gusty and then did a clean installation of hardy and now I can't install NWN. 

The problem araises when I try to copy ANY file from the cd. It throws me errors like :


```
bardic@ubuntu:~/Games/nwn$ unzip /media/cdrom_/Data_linux.zip
Archive:  /media/cdrom_/Data_linux.zip
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
note:  /media/cdrom_/Data_linux.zip may be a plain executable, not an archive
unzip:  cannot find zipfile directory in one of /media/cdrom_/Data_linux.zip or
        /media/cdrom_/Data_linux.zip.zip, and cannot find /media/cdrom_/Data_linux.zip.ZIP, period.

```

or 

```
bardic@ubuntu:~/Games/nwn$ unzip -o /media/cdrom_/data/XP1.zip
Archive:  /media/cdrom_/data/XP1.zip
file #1:  bad zipfile offset (lseek):  0
file #2:  bad zipfile offset (local header sig):  38
  inflating: ambient/al_mg_x0rui2.wav  error:  zipfile read error

```

Any idea's why this is happening? I'd love to play NWN again.

---

### Post by Skifreak on 2008-06-08
First of all, excellent guide! I was able to install NWN with ease. Now, the main problem I am having is the fonts are not visible. I installed the ms core fonts and restarted, ran the script and I get the main screen with all of the buttons but no text inside?
Also, when I was entering the cd keys it only took me as far as the SOU key and never asked me for the hordes key. Finally, I did not download any patches as I was hoping to use the auto updater but this was a mistake I think. Any suggestions as to how I can update to the 1.68 patch now after the install? 
Sorry for all of the questions, I am really enjoying Kubuntu and if I can get this to work it may be the end of having to have a dual boot machine!

Thanks 

Skifreak

---

### Post by Fristi on 2008-06-16
Hiya
Firstly, thanks for the guide, it helped me a lot.

After some problems here and there I finally managed to install the game, the diamond edition that is.

I continued to follow the guide, created a desktop icon, installed the movie thing and than made the necessary adjustements.

When I tried to run the game it starst, as in my screen goes black and then I just go back to desktop, nothing crashes/gets stuck, no error warnings or so, just, black screen and than back...

Hope someone can help me fix this, really love to get this up and running again :-)

---

### Post by bardic on 2008-06-16
I'd like to post the fix to the problem I was having. It was rather simple too. My dvd rom was on the fritz. So on another pc I made an ISO and mounted it, and presto! It works.

---

### Post by Fristi on 2008-06-16
Me again, just a small update..If i Install according to the bioware site and then try to run the game i do get an error:

nwmain: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
./nwn: line 12: 20167 Aborted                 ./nwmain $@


I have absolutely no clue what to do with it..

edit:
Fixed it, as in, I removed the ./lib from the nwn file and the game started, just have to enter the cd codes now..fingers crossed!

---

### Post by MaximB on 2008-06-17
OK.
A BIG suggestion for ALL of you who want to play NWN or any other big game that works Nativity on GNU/Linux. 
When you do manage to install this game (with the help of this 38 pages long thread) please burn it as it is on 2 DVD's (just split the game directory in half so it can fit on 2 DVD's) , and the next time you want to install it just copy it from those DVD's.
It works for me and saved much time and nerves.

remember it's GNU/Linux, you don't HAVE to install every game every time.
After installation you can just burn and copy it, it's not Windows thus it doesn't need to mess up with your registry to work.

---

### Post by Xodarap on 2008-06-23
I am getting a segfault when running this - I think I have followed all the instructions, so I'm not sure why:

ben@ben-desktop:/usr/local/games/nwn$ ./nwn
Segmentation fault
ben@ben-desktop:/usr/local/games/nwn$ 

I put the last 1,000 lines of the stack trace here: [http://paste.ubuntu.com/22398/](http://paste.ubuntu.com/22398/)

I can put the entire log up if that is helpful, but it is 23 mb and it seems like the last 300 or so lines are all that matter.

If I don't remove the ./lib from the script I get the other error about XGetXCBBuffer, rather than a segfault.

Thanks!

EDIT: I installed patch 10 beta, and now it waits until I attempt to load a game to segfault.

---

### Post by DarkW0lf on 2008-06-28
I had been playing in Edgy and Feisty but now I can't get the game to run in Hardy.

Ran nwn in terminal to see why the game would just quit at start, though I don't know what it means if anything. (full output attached.)

I haven't played in a while and wanted to get back to it.
If I had already installed it form before what would be the packages I need to get it running again ?

```

#13 ./nwmain(SDL_SetVideoMode+0x45f) [0x804fb57]
#14 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7bdc450]
#15 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
nwmain: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Aborted

```

---

### Post by strifejordan on 2008-07-01
I made the icon but when i double click it to open the game it gives this message

There was an error launching the application.

Details: Failed to execute child process "/home/jordan/nwn" (Permission denied)

---

### Post by DarkW0lf on 2008-07-04
nwn is a script make sure it is set to execute and not display as text.

You can right click it and use the permissions tab.

---

### Post by JoneYee on 2008-07-29
> **Fristi said:**
> If i Install according to the bioware site and then try to run the game i do get an error:

nwmain: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
./nwn: line 12: 20167 Aborted                 ./nwmain $@


I am getting this if I install via the Bioware site's instructions, or if I follow the instructions and use the installer in the first post in this thread.  

I have not tried removing the lib reference from the nwn file yet (after 4 hours I was very tired).

1. Are there updated instructions, or an updated installer for installing on an 8.04 release or the 1.69 final patch?

2. Would anyone be willing to give me some serious assistance (spent two hours in IRC last night and no one would even acknowledge my questions).

---

### Post by JoneYee on 2008-07-29
SOLUTION:

gedit nwn

remove the ./lib from the path as the file suggests:

```
# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=:./miles:$LD_LIBRARY_PATH

./nwmain $@
```

---

### Post by Pastito on 2008-07-30
Thanks, I had the same problem and the solution works for me to.

---

### Post by Ostien on 2008-07-30
unfortunately I'm not having any luck with this solution.  I'm having the same problem but removing the ./lib line does not work.

---

### Post by JoneYee on 2008-07-30
> **Ostien said:**
> unfortunately I'm not having any luck with this solution.  I'm having the same problem but removing the ./lib line does not work.

Remove the Entire Line then.  Let me know what happens.

---

### Post by Ostien on 2008-07-31
Tried that but then decided to try installing again with a fresh file and remove ./lib and it worked.

strange, but hey now it works.

---

### Post by JoneYee on 2008-07-31
> **Ostien said:**
> Tried that but then decided to try installing again with a fresh file and remove ./lib and it worked.

strange, but hey now it works.

Cool,  I think the removal of .lib is an 8.04 fix.

---

### Post by DarkW0lf on 2008-08-01
I can't get the program to run with or without the ./lib in the line.

I have 8.04 installed but what version of the client are we talking about ?
( I think mine is still 1.68 maybe )

Oh are there other dependencies with 8.04 (do I need to rebuild anything ?)

---

### Post by JoneYee on 2008-08-04
> **DarkW0lf said:**
> I can't get the program to run with or without the ./lib in the line.

I have 8.04 installed but what version of the client are we talking about ?
( I think mine is still 1.68 maybe )

Oh are there other dependencies with 8.04 (do I need to rebuild anything ?)

Sorry, was out of town all weekend.  I am on the 1.65 distro.  I have not upgraded to 1.68/1.69.

I following the instructions in the initial post completely (minus to video portion) and then removed the lib line.  I am also running 8.04

---

### Post by Frasc0 on 2008-08-19
> **Danijel Snajder said:**
> Dont know what happened to that site then,
but install script is worth downloading...

here´s then direct link to the script

[http://www.paradoxinc.net/files/icarus/scripts/install-nwn.sh](http://www.paradoxinc.net/files/icarus/scripts/install-nwn.sh)

or better here in attachment if this site goes down

Hi. Got several of problems people here got. Game installed correctly using script on quoted post #359 by Danijel.

BTW... Using Hardy.

Thanks people.

---

### Post by DarkW0lf on 2008-08-23
Okay got the .lib stuff taken care of but this is my current error:
Also updated to current client and rebuilt movies:

Without ./lib:
```

~/nwn$ ./nwn
NOTICE: NWMovies: Version: 20080308.192336
NOTICE: SDL Library determined to be: /usr/lib/libSDL-1.2.so.0
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
NOTICE: NWMovies: PostPatch4: e9 2c cf e9 af 
NOTICE: NWMovies: MoviesPrePatch: 6a 00 53 bf 00 00 00 3f e8 72 4f 2a 00 8b 43 60 8b 10 c7 04 24 00 00 80 3f 57 57 57 50 ff 52 44 83 c4 1c 
NOTICE: NWMovies: MoviesPostPatch: 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 
NOTICE: NWMovies: SDL_WM_GrabInput() address: b7d07460
NOTICE: NWMovies: (Calculated) SDL_WM_GrabInputRaw() address: b7d073a0
NOTICE: NWMovies: Initialized.
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  134 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x71
  Serial number of failed request:  129
  Current serial number in output stream:  131

```

With ./lib:
```

~/nwn$ ./nwn
NOTICE: NWMovies: Version: 20080308.192336
NOTICE: SDL Library determined to be: ./lib/libSDL-1.2.so.0
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
NOTICE: NWMovies: PostPatch4: e9 2c ef f0 af 
NOTICE: NWMovies: MoviesPrePatch: 6a 00 53 bf 00 00 00 3f e8 72 4f 2a 00 8b 43 60 8b 10 c7 04 24 00 00 80 3f 57 57 57 50 ff 52 44 83 c4 1c 
NOTICE: NWMovies: MoviesPostPatch: 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 
NOTICE: NWMovies: SDL_WM_GrabInput() address: b7d93900
NOTICE: NWMovies: (Calculated) SDL_WM_GrabInputRaw() address: b7d93864
NOTICE: NWMovies: Initialized.
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb79f2767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb79f28b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb7b591bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7d9e53d]
#4 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x164) [0xb7d9978c]
#5 ./lib/libSDL-1.2.so.0 [0xb7d9b457]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d90f66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d737de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d738dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7c2e450]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb79f2767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb79f281e]
#2 /usr/lib/libX11.so.6 [0xb7b58518]
#3 /usr/lib/libX11.so.6(XMatchVisualInfo+0x40) [0xb7b4ef70]
#4 ./lib/libSDL-1.2.so.0 [0xb7d9951a]
#5 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x408) [0xb7d99a30]
#6 ./lib/libSDL-1.2.so.0 [0xb7d9b457]
#7 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d90f66]
#8 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d737de]
#9 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d738dc]
#10 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7c2e450]
#12 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb79f2767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb79f28b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb7b591bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XineramaIsActive+0x76) [0xb7da4b1a]
#4 ./lib/libSDL-1.2.so.0(X11_GetVideoModes+0x673) [0xb7d99c9b]
#5 ./lib/libSDL-1.2.so.0 [0xb7d9b457]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d90f66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d737de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d738dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7c2e450]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb79f2767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb79f281e]
#2 /usr/lib/libX11.so.6 [0xb7b58518]
#3 /usr/lib/libX11.so.6(XCreateColormap+0x26) [0xb7b2ee76]
#4 ./lib/libSDL-1.2.so.0 [0xb7d9b584]
#5 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d90f66]
#6 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d737de]
#7 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d738dc]
#8 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#9 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7c2e450]
#10 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb79f2767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb79f28b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb7b591bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeGetGamma+0x9a) [0xb7d9e80e]
#4 ./lib/libSDL-1.2.so.0 [0xb7d97a89]
#5 ./lib/libSDL-1.2.so.0(X11_SaveVidModeGamma+0x36) [0xb7d97b3a]
#6 ./lib/libSDL-1.2.so.0 [0xb7d9b60f]
#7 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d90f66]
#8 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d737de]
#9 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d738dc]
#10 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#11 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7c2e450]
#12 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb79f2767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb79f281e]
#2 /usr/lib/libX11.so.6 [0xb7b58518]
#3 /usr/lib/libX11.so.6(XCreateWindow+0x26) [0xb7b4f616]
#4 ./lib/libSDL-1.2.so.0 [0xb7d9aff3]
#5 ./lib/libSDL-1.2.so.0 [0xb7d9b635]
#6 ./lib/libSDL-1.2.so.0(SDL_VideoInit+0x2b2) [0xb7d90f66]
#7 ./lib/libSDL-1.2.so.0(SDL_InitSubSystem+0x4a) [0xb7d737de]
#8 ./lib/libSDL-1.2.so.0(SDL_Init+0x24) [0xb7d738dc]
#9 ./nwmain(SDL_SetVideoMode+0x293) [0x804f98b]
#10 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7c2e450]
#11 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb79f2767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb79f28b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb7b591bd]
#3 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeQueryVersion+0x8d) [0xb7d9e53d]
#4 ./lib/libSDL-1.2.so.0(SDL_XF86VidModeGetModeLine+0x5b) [0xb7d9e8e7]
#5 ./lib/libSDL-1.2.so.0 [0xb7d99368]
#6 ./lib/libSDL-1.2.so.0(X11_EnterFullScreen+0x72) [0xb7d9a092]
#7 ./lib/libSDL-1.2.so.0 [0xb7d9c375]
#8 ./lib/libSDL-1.2.so.0 [0xb7d9c52b]
#9 ./lib/libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7d917df]
#10 ./nwmain [0x84d970d]
#11 ./nwmain(strftime+0x1dfd) [0x80508b5]
#12 ./nwmain [0x805d896]
#13 ./nwmain [0x805adc0]
#14 ./nwmain [0x8059ae5]
#15 ./nwmain(SDL_SetVideoMode+0x45f) [0x804fb57]
#16 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7c2e450]
#17 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb79f2767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb79f281e]
#2 /usr/lib/libX11.so.6 [0xb7b58518]
#3 /usr/lib/libX11.so.6(XMoveResizeWindow+0x25) [0xb7b2e165]
#4 ./lib/libSDL-1.2.so.0(X11_EnterFullScreen+0xd4) [0xb7d9a0f4]
#5 ./lib/libSDL-1.2.so.0 [0xb7d9c375]
#6 ./lib/libSDL-1.2.so.0 [0xb7d9c52b]
#7 ./lib/libSDL-1.2.so.0(SDL_SetVideoMode+0x1b3) [0xb7d917df]
#8 ./nwmain [0x84d970d]
#9 ./nwmain(strftime+0x1dfd) [0x80508b5]
#10 ./nwmain [0x805d896]
#11 ./nwmain [0x805adc0]
#12 ./nwmain [0x8059ae5]
#13 ./nwmain(SDL_SetVideoMode+0x45f) [0x804fb57]
#14 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7c2e450]
#15 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
nwmain: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
./nwn: line 15:  8856 Aborted                 ./nwmain $@

```
Anyone know ?

---

### Post by justgrant2009 on 2008-09-09
I'm having trouble installing it, on the step where it asks me where i want to install it to, I tell it /home/<my user name>/nwn  and it tells me "please try a different folder or change permissions on '/home/<my user name>/nwn'  I have tried that though, i've chmod 777 -R'ed everything (from / down the chain).  What's going on?

Unfortunately, i just noticed now that when i log in, it tells me that there is a problem with my permissions on my home folder saying that it shouldn't bee 777 that it needs to be 644 and when i try and change it back... it won't let me now... help there too please if you can?

---

### Post by oldrocker99 on 2008-09-23
[also posted in the 64-bit group]

I tried three different install-nwn.sh scripts and finally went to BioWare's site and followed the instructions to the letter. One small edit of the nwn file (I made a copy of the original line and pasted it in the line following, then edited that copied line. Comment out whichever one doesn't work, and you can get back to the other one quickly if need be) and I was up and running. No movies :(, but everything else is just as delightful as it was 'way back in '02. 

Neverwinter Nights Diamond is, imho, the best commercial game available for Linux, and it is definitely the most gaming goodness you can get for $20. You can literally get years of enjoyment (all for free download) from this gaming masterpiece.

A big thumb's up to BioWare who had a Linux version that would take a purchased copy's serial numbers and run without a disk in the drive. 

Gaming does live on Linux!

:guitar:

---

### Post by oldrocker99 on 2008-09-23
PS--I installed in /home/nwn, for what it's worth. No permissions problems.

---

### Post by edveal on 2008-10-22
Will these instruction still work using Ubunty 8.04 and the NWN Dimand DVD?

---

### Post by luvinit on 2008-11-10
I am using hardy heron and for me NWN wouldn't work without installing the following package in synaptic

libsdl1.2debian-all

i also couldn't get sound untilI put this line in the nwn script

export SDL_AUDIODRIVER=esd

---

### Post by second.exodous on 2008-11-12
I'm not sure if this thread is still alive, but I'm having trouble.  I got all the way to step 7 where it asks me to edit the nwn file.  The installer didn't put a file named nwn.

I have the Diamond eddition, with the latest patch, 1.69.

Here is what is in the directory:

ambient     logs           NWNv169.txt                   scripttemplates
chitin.key  modules        nwn.xpm                       servervault
data        movies         nwserver                      source
dialog.tlk  music          nwtoolset.ini                 temp
dmvault     nwm            override                      tempclient
docs        nwmain         patch                         texturepacks
hak         nwn.ico        readme.linuxclientupdate.txt  xp2patch.key
localvault  nwnplayer.ini  saves

I tried to edit all the files I though it could be, but none of them had what was in leech's.

Any ideas or do I need to post more information?

Thanx,
Stan

---

### Post by Mark Sasak on 2008-11-14
I have read most of the thread and I still get an error following leech's directions.  I installed the game as sudo in /usr/local/games/nwn and edited the nwn file.  I also installed the movies and everything seemed to go fine.  But I get the error when I execute the nwn as sudo or user:

#15 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
nwmain: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Aborted

I am running 8.10 on an IBM Thinkpad T30
It opens a terminal window and then disappears.  I've added the login to the users group and chgrp -R users but it does exactly the same error.

Any help is greatly appreciated.  As soon as I get this working, on to loading it on a Dell D620.

Mark

---

### Post by DarkSoul1984 on 2008-11-23
Hi guys,

I'm hoping you can help me out. I'm still getting the hang of Ubuntu, and in an effort not to migrate back to Windows, I'm trying to install Neverwinter Nights Diamond edition.

I've been following the directions, and the problem I run into when I execute the script is in choosing the install directoy. I forever get this:

-e Please try a different folder or change permissions on /usr/local/games/nwn

This happens no matter what install directory I choose.

Anyone know what I'm doing wrong? I am all ears, or eyes in this case.

---

### Post by Perfect Storm on 2008-11-23
My suggestion is that you don't use [sudo] and install the game locally (on your home directory).

---

### Post by DarkSoul1984 on 2008-11-23
It happens even at the root terminal.

---

### Post by Perfect Storm on 2008-11-23
It's never a good idea to run stuff with sudo - only if it's to change/maintaining something in the system.

> Please try a different folder or change permissions on /usr/local/games/nwn

This means that you don't own/have permission for the folder and what's in it. To start changing the permission of files and folders in the system is a very very bad idea.
Nwn can't be installed system-wide like most other games without compromizing security.

---

### Post by DarkSoul1984 on 2008-11-23
Here's my basic procedure.

I went through steps 1 & 2 with no issues. I downloaded the install script and extracted it to my desktop. I chose to run it in terminal (as per the instructions), went through the first few options, and then received the same message when choosing the install directory no matter which directory I choose.

What am I doing wrong?

---

### Post by PioneerSkies on 2008-11-23
> **JoneYee said:**
> SOLUTION:

gedit nwn

remove the ./lib from the path as the file suggests:

```
# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=:./miles:$LD_LIBRARY_PATH

./nwmain $@
```

This has fixed this error
```
nwmain: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
```
for me on Ubuntu8.10 and nwn client v1.68. Just for statistics.

Thanks for the trick! :)

---

### Post by Mark Sasak on 2008-12-04
I followed leech' directions and I am still having a problem.  I'm loading it on an IBM T30 2Ghz and Ubuntu 8.10.  
I removed the lib from nwn.  I keep getting a seg fault.  Everything looks good.  The ini was created but the seg fault still happens.  This is from the terminal when executing.

laptop:~/nwn$ nwn
NOTICE: NWMovies: Version: 20080308.192336
NOTICE: SDL Library determined to be: /usr/lib/libSDL-1.2.so.0
NOTICE: NWMovies: Patch 0 Address: 0x0807513d
NOTICE: NWMovies: Patch 1 Address: 0x08075151
NOTICE: NWMovies: Patch 2 Address: 0x0814fc94
NOTICE: NWMovies: Patch 3 Address: 0x0814fcae
NOTICE: NWMovies: Patch 4 Address: 0x0807500f
NOTICE: NWMovies: Patch 5 Address: 0x081f41ad
NOTICE: NWMovies: Patch 6 Address: 0x081f41d0
NOTICE: NWMovies: PrePatch0: 8b 80 48 02 00 00 5d c3 
NOTICE: NWMovies: PrePatch1: 8b 80 4c 02 00 00 5d c3 
NOTICE: NWMovies: PrePatch2: e8 6b 55 f2 ff 83 ec 08 
NOTICE: NWMovies: PrePatch3: 168-: eb 58 83 ec 
NOTICE: NWMovies: PostPatch0: b8 00 00 00 00 90 5d c3 
NOTICE: NWMovies: PostPatch1: b8 00 00 00 00 90 5d c3 
NOTICE: NWMovies: PostPatch2: 90 90 90 90 90 83 ec 08 
NOTICE: NWMovies: PostPatch3: 168-: 90 90 83 ec 
NOTICE: NWMovies: PrePatch4: 56 8d 5d e8 53 
NOTICE: NWMovies: PostPatch4: e9 78 78 01 b0 
NOTICE: NWMovies: MoviesPrePatch: 6a 00 53 bf 00 00 00 3f e8 3e ff 27 00 8b 43 60 8b 10 c7 04 24 00 00 80 3f 57 57 57 50 ff 52 44 83 c4 1c 
NOTICE: NWMovies: MoviesPostPatch: 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 90 
NOTICE: NWMovies: SDL_WM_GrabInput() address: b7e84fd0
NOTICE: NWMovies: (Calculated) SDL_WM_GrabInputRaw() address: b7e84f20
NOTICE: NWMovies: Initialized.
Segmentation fault

Any help is extremely apreciated.

---

### Post by countzyx on 2008-12-14
Does anyone know where I can get a copy of the latest nwmovies? It seems that [http://home.woh.rr.com/nwmovies/](http://home.woh.rr.com/nwmovies/) is no more.

---

### Post by oldrocker99 on 2008-12-14
Once again, I'll say that none of the scripts on this thread worked for me, but following EXACTLY the instructions on Bioware's Linux forum (the top sticky) worked perfectly for me. An edit of the nwn file was necessary, and I still don't have the movies :mad:, but I can play the game and use ANY downloaded module.

BTW, if you get an error message that a HAK file wasn't found, look at the logfile and change the case (usually to lower) of that filename. Windows isn't case-sensitive, and Linux is.

:guitar:

---

### Post by vinnie1 on 2008-12-16
Hi

 I would like to get movies working in this game.

 I have installed BinkPlayer and tested it, works good.

 Now I need to know what are the next steps, to get it working in the game.

 it seems [http://home.woh.rr.com/nwmovies/](http://home.woh.rr.com/nwmovies/) is down/gone.

---

### Post by DarkW0lf on 2008-12-20
run ./fixinstall should take care of any case issues with filenames.

I currently have a problem getting the game running again. Both gutsy and hardy are having problems. Best I can find is that there is an issue with the kernel modules for video. I have found posts that have similar log entries to the ones I posted previously but they were having issues with nVidia cards (mine is an onboard Intel i845).

Any clues ??

(it seems to not like the widescreen resolution my Acer AL1916W uses, I swear I used this in earlier ubuntu's)

---

### Post by hena on 2008-12-28
I just installed a neverwinter nights to my comp and after solving the problems with sounds (copied ./miles dirs stuff again and set 'export SDL_AUDIODRIVER=alsa' in nwn) it works now. Yey!

However I would like to see the movie segments as well. However the link in first post doesn't have the latest tarball anymore. Where could I find that thing currently? Considering that this has been asked multiple times over several weeks without answers, I'm not very confident that I'll get one either ...

As far as the graphics go. you need to make sure that you have drivers which support direct rendering. Check command: ```
glxinfo |grep 'direct rendering'
```

Edit:
Hahaa! I found the site which now holds the nwmovies binaries.
[http://home.roadrunner.com/~nwmovies/](http://home.roadrunner.com/~nwmovies/)

---

### Post by DarkW0lf on 2009-01-09
Here is the error and glxinfo, my video card is an Intel 845G
The driver for which is xserver-xorg-video-i810 I think.

error:
NOTICE: NWMovies: Initialized.
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  135 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x71
  Serial number of failed request:  129
  Current serial number in output stream:  131

glxinfo:
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer, 
    GLX_OML_swap_method, GLX_SGI_make_current_read, GLX_SGI_swap_control, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_OML_sync_control, 
    GLX_SGI_make_current_read, GLX_SGI_swap_control, GLX_SGI_video_sync, 
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGIX_visual_select_group, GLX_EXT_texture_from_pixmap
GLX version: 1.2
GLX extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_import_context, 
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_allocate_memory, 
    GLX_MESA_copy_sub_buffer, GLX_MESA_swap_control, 
    GLX_MESA_swap_frame_usage, GLX_OML_swap_method, GLX_SGI_make_current_read, 
    GLX_SGI_swap_control, GLX_SGI_video_sync, GLX_SGIS_multisample, 
    GLX_SGIX_fbconfig, GLX_SGIX_visual_select_group
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 845G 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 7.0.3-rc2
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multisample, GL_ARB_multitexture, 
    GL_ARB_point_parameters, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_rectangle, 
    GL_ARB_transpose_matrix, GL_ARB_vertex_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_window_pos, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_equation_separate, 
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_clip_volume_hint, GL_EXT_cull_vertex, GL_EXT_compiled_vertex_array, 
    GL_EXT_convolution, GL_EXT_copy_texture, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_histogram, GL_EXT_multi_draw_arrays, 
    GL_EXT_packed_pixels, GL_EXT_point_parameters, GL_EXT_polygon_offset, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_stencil_wrap, GL_EXT_subtexture, 
    GL_EXT_texture, GL_EXT_texture3D, GL_EXT_texture_edge_clamp, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_object, GL_EXT_texture_rectangle, 
    GL_EXT_vertex_array, GL_3DFX_texture_compression_FXT1, 
    GL_APPLE_client_storage, GL_APPLE_packed_pixels, 
    GL_ATI_blend_equation_separate, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate, 
    GL_MESA_pack_invert, GL_MESA_ycbcr_texture, GL_MESA_window_pos, 
    GL_NV_blend_square, GL_NV_light_max_exponent, GL_NV_texture_rectangle, 
    GL_NV_texgen_reflection, GL_NV_vertex_program, GL_NV_vertex_program1_1, 
    GL_OES_read_format, GL_SGI_color_matrix, GL_SGI_color_table, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

---

### Post by plytheman on 2009-01-20
WOWZERS!!  I probably spent 4 hours this afternoon trying to get it to work.  What finally ended up working for me was a 2 step proccess.  First I followed [THIS guide for the DIAMOND edition]("http://nwn.bioware.com/forums/viewtopic.html?topic=469853&forum=72&sp=0").  After that it gave me an error when trying to launch that looked like this:
```
#12 ./nwmain [0x8059ae5]
#13 ./nwmain(SDL_SetVideoMode+0x45f) [0x804fb57]
#14 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7b81450]
#15 ./nwmain(AIL_WAV_info+0x39) [0x804f851]
nwmain: ../../src/xcb_lock.c:77: _XGetXCBBuffer: Assertion `((int) ((xcb_req) - (dpy->request)) >= 0)' failed.
Aborted
```

So then I just used gedit to fix up the launcher and removed "./lib:" as is explained [here.]("http://ubuntuforums.org/showthread.php?t=392766")

I'm sure both of these solutions have been brought up in this thread, but with it being as long as it is I figured I'd post it again.  Thanks to everyone that posted on these forums and all the nice folk in the irc channel (esp ichbinesderelch who helped me find some other installers).

Also, I have some serious clipping issues when I do get in there, so if you find yourself in the same problem there's a thread [here]("http://nwn.bioware.com/forums/viewtopic.html?topic=405580&forum=72&sp=0") that has some fixes I haven't had a chance to try yet.

EDIT: solved the choppy video problems with a tool that simply disables compiz.  Found it on this blog: [http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch).  Everything seems to be running peachy now!  Three step proccess and its all done (I hope).  Also haven't tried to get movies, but I'll deal with that another day...

Thanks and good luck!

---

### Post by tnt533 on 2009-02-21
Should have read the thread to the end.

*forget it*

---

### Post by Monkey_Magic on 2009-03-08
This is a great guide, thanks! 
I've run into a problem, though. (I'm new to linux!)

When it comes to the "Enter the install directory. (/usr/local/games/nwn):" and I enter my /home/username/nwn directory, it hits me with:

```
[: 64: ==: unexpected operator
-e Possible write error
-e Please try a different folder or change permissions on /usr/local/games/nwn
```

I've been trying everything to try and mess with the permissions, but I can't see what I need to do. Can anyone help?

---

### Post by mmafterme on 2009-03-13
> **leech said:**
> [COLOR="Red"]Note for Edgy Eft users![/COLOR] You must first change the /bin/sh symbolic link.  To do this simply run ```
sudo dpkg-reconfigure dash
``` Select No, and it'll change your shell to bash.  After installing the game, you'll probably want to switch back to using dash, as to not mess up any advantages of speed that dash may provide.  Run the command again and select Yes.

This is true for anything from 6.10 onwards.

---

### Post by DarkW0lf on 2009-03-22
DarkSim's post (#352)

Works for me to use windowed mode instead of full screen.
I don't like the movies in a separate window but I never had movies during play before and the game wouldn't run in Widescreen resolutions at all.

Don't know if it's the client or the video module but I hope someone gets that fixed.

---

### Post by Tahakki on 2009-03-23
Thanks for the HowTo. I tried your solution for getting movies to work, but it doesn't work. The 'Movies' option is no longer greyed out, but when I click on a movie, or when it gets to a place where a movie should play, the screen just flickers and nothing happens.

EDIT: Fixed. Turns out I didn't have the Movies folder as I followed BioWare's instructions. :P

---

### Post by Trogdor Burninator on 2009-03-24
OK Im a noobie to Ubuntu. I'm having problems when I come to "On Ubuntu, this will be /media/cdrom for the first drive." I type in /media/cdrom and I did /media/cdrom0 and the terminal still closes as soon as I hit enter.

I'm running Intrepid and nvidia 8400m graphics card if it helps at all

---

### Post by mediax on 2009-03-27
Any chance of this (or just the HOWTO portion) being stickied?

Or alternatively, another sub-forum being set up for game installation guides?

These guides are a great resource.

---

### Post by Perfect Storm on 2009-03-28
> **mediax said:**
> Any chance of this (or just the HOWTO portion) being stickied?

Or alternatively, another sub-forum being set up for game installation guides?

These guides are a great resource.

Nope.

---

### Post by mediax on 2009-03-28
> **Artificial Intelligence said:**
> Nope.

Well, thank you for that helpful reply.  Such a complete explanation is always appreciated.

---

### Post by Perfect Storm on 2009-03-28
> **mediax said:**
> Well, thank you for that helpful reply.  Such a complete explanation is always appreciated.

You want an explaination. It won't be accepted by the Council, it's them who say yea or ney. Many have requested many diffrent guides/howto to get stickied, but it won't happen. It will bloated the board too much. 

Search is the best way and the guide/howto makers have to tag the thread which will make it easier to find with the search/tag engine.


By the way, please drop the sarcasm. Just ask nice if I want to explain why.

---

### Post by mediax on 2009-03-28
I appreciate the problem - it's just a shame that nuggets of valuable information like this can't be made more easily available.

> **Artificial Intelligence said:**
> By the way, please drop the sarcasm. Just ask nice if I want to explain why.

IMHO your original answer was almost worse than no reply at all, hence my reaction.  Let's make a deal - you be a little less dismissive and I'll drop the sarcasm.  Fair enough?

---

### Post by brendanisevil on 2009-04-03
i have tried what you suggested but it stalls at step 5 for me. it tells me that permission is denied and that the directory does not exist. i created the directory and looked at the permissions and it still does not work. help me?

---

### Post by brigadoon on 2009-04-19
In the event this helps anyone...

I have recently loaded Ubuntu 8.10 onto a Sony Vaio as a dual boot with Vista. I have to have nwn loaded. I always use this script by Leech. Its a life saver. However, I always have issues related to either the system or the version of Ubuntu I am using. I had the similar issues as described in the last few posts.

Could not install the script...

Could not get the game to start...

Once the game started, the menus would blank out or become distorted...

The first issue ***Could not install the script*** was fixed by changing the shell command from dash to bash. Dash has permission issues on my system. Don't know why but switching to bash lets me install programs thru shells. I've noticed this with several other install scripts which is why I am documenting this here. Just remember when running the command...

sudo dpkg-reconfigure dash

**_ANSWER NO_** This changes the shell to bash.

The second issue ***Could not get the game to start*** was fixed by playing with the nwn file in GEDIT. My file looks as follows...

#!/bin/sh

# This script runs Neverwinter Nights from the current directory

cd /home/brigadoon/nwn
export SDL_MOUSE_RELATIVE=0
export SDL_VIDEO_X11_DGAMOUSE=0

# If you do not wish to use the SDL library included in the package, remove
# ./lib from LD_LIBRARY_PATH
export LD_LIBRARY_PATH=:./miles:$LD_LIBRARY_PATH
# export LD_LIBRARY_PATH=./lib:./miles:$LD_LIBRARY_PATH
# export LD_PRELOAD=./nwmovies.so
./nwmain $@

As you can see in my script above I don't bother with the movies. Nice to have but I want to move into game play fast. I can toggle them on when I need them.

The third issue ***Once the game started, the menus would blank out or become distorted*** was a result of a few items. 

The first was that the linux client didn't load. I believe it was a permissions issue at this point. This is a Ubuntu 8.10 recurring issue for me. I didn't have shell permission issues in earlier versions. The clients were in the directory already but didn't load. I had to load them manually.

The second was installing the patches. They were in the directory but didn't load. I manually installed them moving the patch to my nwn folder and running the command ***tar  -xzf  English_linuxclient169_xp2.tar.gz*** to extract the data. When running the script I tried loading the 167 patch without any luck. I manually loaded in the 169.

The third step was to change the folder and file permissions in my nwn game folder. I typed in ***sudo chown -R brigadoon.brigadoon nwn*** in my home folder location.

The fourth was to run the fixinstall script in the nwn game folder. I did have to change the file properties to make the fixinstall an executable.

The fifth step was to repeat the third step again.

With the exception of the fifth step the same thing would happen after each step. The game would start, text would appear, menus would go blank and then the graphics would get distorted. It seems that after installing or changing anything in the nwn game folder I have to reset permissions.

Prior to re-setting permissions running the game through a terminal window worked for me as well. The trick was to start the game using the sudo command. In a terminal window change directory to the Neverwinter Nights folder. Then type ***sudo ./nwn*** to start the game.

Good script, good game, good operating system. Ubuntu beats Vista any day.

---

### Post by brigadoon on 2009-04-19
> **brendanisevil said:**
> i have tried what you suggested but it stalls at step 5 for me. it tells me that permission is denied and that the directory does not exist. i created the directory and looked at the permissions and it still does not work. help me?

In my post just previous to this one I let the script make the nwn folder. I had the same issue as you did with permission issues. My roundabout solution got me through it and I'm up and running.

---

### Post by K.Mandla on 2009-04-27
Hi. I just used the script on a clean installation of 9.04 and ran into no problems. I have the Medibuntu repositories enabled and the ubuntu-restricted packages installed. 

Everything works with no adjustments on my part, after installing to my home directory. I even gave the script the 169 as the version number and it downloaded it and applied it automatically. 

Thanks once again for this. ;)

---

### Post by brendanisevil on 2009-05-13
Ok.... 

the install worked like a dream but it crashes when i want to start a new game and i have no writing on the buttoons in the game menu.. help me please

---

### Post by oldrocker99 on 2009-05-14
> **brendanisevil said:**
> Ok.... 

the install worked like a dream but it crashes when i want to start a new game and i have no writing on the buttoons in the game menu.. help me please

Did you run ./fixinstall in the terminal?

:guitar:

---

### Post by brendanisevil on 2009-05-15
yes i did and i still have the same problem

---

### Post by tcpage on 2009-05-16
Hi. I've only been using Ubuntu for about a week, and I'm having trouble setting nwn up. I'm running 9.04, and I followed the instructions above.

Everything seems to work fine until I go to "New Game" on the main menu. Instead of loading it gives me a message that says "pre_campaign: Gui layout file not found." 

Can anyone please tell me what I may have missed?

---

### Post by Elvish Legion on 2009-05-20
I have a slight problem. my NWN discs were damaged, and the only solution I had was iso from platinum (I think it was platinum at least) its 5 isos.


Anyway when I run the script I try to give it the 'drive' I mount my isos to (/mnt/disk) but it does not work, when I enter that it gives me an error saying invalid drive

Any work around or am I stuck trying to track down a nwn dvd in iraq?

---

### Post by brendanisevil on 2009-05-21
So I re-installed the game and manually installed the 169 patch instead of the 166/167 patch i was trying to use before. Followed everything that Brig suggested and now the game works spectacularly. Thanks for all the help. You guys rock!!

---

### Post by oldrocker99 on 2009-05-21
When all else fails, the top sticky in Bioware's Linux Neverwinter Nights forums is the only installation method that actually worked for me.

If only other companies would do Linux ports... ](*,)

:guitar:

---

### Post by dyingsun on 2009-05-22
**[COLOR="Red"]Segmentation Fault[/COLOR]**

Gday all, seems this is the GoTo thread for Linux NWN!

I've just about got the NWN working on my system, I can create new characters, begin loading old saved games from Windows, all that stuff, but when I start a new game, or try to load a saved one, I get the usual loading bar and then, just as I should appear in the bedroom of the Neverwinter Academy, I get dumped back to terminal with the extremely helpful output of "Segmentation Fault". followed by my command prompt. Doesnt say anything about parachutes or the like that I've seen on other NWN issues.

I've changed all the perms of the files in the nwn directories (recursive chown)
(also tried running as sudo)
fixinstalled
updated
nutted out the various other problems, and I'm hoping this will be the last problem!
I've searched and searched, just can't find the answer.
I did see something on bioware, saying that if you execute "glxinfo | grep render" it should return "Direct Rendering: Yes". That doesn't happen for me. Instead I get this:

```
GeForce 6150SE nForce 430/PCI/SSE2
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 

```

It doesn't say what it means if I dont have Direct Rendering, Would this be related to the problem?

I've also removed the ./lib - I couldnt get anything to load until I did that.

So close....yet so far!

So if anyone can give me a clue as to how to deal with this Segmentation Fault, I'd be over the moon. What causes segmentation faults anyway? I googled it but its a wee bit too teckie-nickle for me.


TIA
Damien

---

### Post by sparkmandrill on 2009-05-22
I'm trying to use the script on 9.04 and I'm getting:

[: 64: 0: unexpected operator
-e Possible write error
-e Please try a different folder or change permissions on /home/username/nwn

when promted to specify the destination folder. I tried several folders on different harddrives.

I've read about this error in this thread before, but I can't seem to find any solution.
Any ideas?

---

### Post by brendanisevil on 2009-05-22
sparkmandrill,
you need to log in to your machine as root to change the permissions for those folders (at least in 9.04 which i am running). Once that is done you can log back into your computer as yourself and try running the script again. also try changing the terminal layout to bash **sudo dpkg-reconfigure dash** and select "no". run the script and you should be fine. If that fails, have a look at Brigadoon's first post on page 43 of this thread for more help. If that doesn't work just ask and I will see what else i can come up with

---

### Post by tcpage on 2009-05-22
As a follow up, I sorted out the issue I was having: 

Turns out, 9.04 didn't support my ATI Graphics Card, and the only thing I could do about it was downgrade to Intrepid Ibex, where it runs perfectly.

---

### Post by sparkmandrill on 2009-05-23
Thanks brendanisevil. The dash reconfigure did the job. Installed well i think.

Now the Problem is: It crashes on the "unpacking module" screen. No errors whatsoever. The program just closes.

---

### Post by Naegling23 on 2009-07-27
hmm, this ran great in hardy, now in jaunty, Im getting this error:

NOTICE: NWMovies(./nwmain): Version: 20080430.v4rc1
NOTICE: Looking up symbols in libSDL.....
ERROR: sdl_wm_grabinput_ptr == NULL: (null)
Aborted

any help?

---

### Post by Naegling23 on 2009-07-27
hmm, removing:

export LD_PRELOAD=./nwmovies.so

from the nwn launch script solves the problem, it must be an issue with the movie player.  Any idea what could have caused the problem?  It would be nice to have the movies playing again.

---

### Post by akira777 on 2009-08-29
Install seems to work for me and I was playing in game as well.  But what happen frequently is that sometimes I load a map in a story or even online my session somehow automatically log out of ubuntu and I have to log back in again and I have to start the program again.  It seems like X just restart or something.  This occur in NWN Platnium version  I'm not sure if this is a video issue or not but I didn't make any change to the driver since it came default with 9.04 Jaunty x64. My specs are:

laptop with:

Pentium Dual-Core CPU T4200 2.00GHz
2.00 GB Ram
Mobile Intel 4 series Express chipset family display

---

### Post by oldrocker99 on 2009-08-29
> **tcpage said:**
> As a follow up, I sorted out the issue I was having: 

Turns out, 9.04 didn't support my ATI Graphics Card, and the only thing I could do about it was downgrade to Intrepid Ibex, where it runs perfectly.

That's exactly what I did and why I did it.

:guitar:

---

### Post by DarkW0lf on 2010-01-12
I have been playing this faithully in an x386 box.
My laptop has a better graphics card but is a AMD64 (dual-core)

ia32libs are installed but when trying to run the script (the nwn script not the install one) it says that it can't open libelf.so (which is not in the /lib32 directory or anywhere under /usr that I could find).

Would this be because I just copied the existing NWN directory.
I didn't see anything in the gwos.org site about 64bit that isn't similar to what I did.

The site just has you unpack archives from the discs, considering I already did that, is anyone else with a 64bit system getting an error about libelf.so ?

---

### Post by DarkW0lf on 2010-01-20
I found some sites/forums where they were having problems with nwmovies on amd64. So I removed that from the nwn script and now the game runs but there is no sound. And it does not seem to detect my soundcard (NVIDIA HD Audio on-board).

So I know I have to rebuild the nwmovies.so but why would it not detect my soundcard ?

---

### Post by DarkW0lf on 2010-02-06
Yeh, figured it out.
Removed ./lib from export line in script (not sure why it was put back in)

All works on 64bit now and sound devices are detected.
(Would still need to recompile the nwmovies.so but they neer played in-game anyway so I may not bother.)

---

### Post by ViorelB on 2010-03-13
What should i do at this step?

---

### Post by oldrocker99 on 2010-03-13
Did you get that while installing, or trying to play? A Linux installation of NWN doesn't even ask for the disk when you start it, unlike the Windows version.

:guitar:

---

### Post by ViorelB on 2010-03-14
I get it when trying to install

---

### Post by Toffeeapple on 2010-03-14
> **ViorelB said:**
> What should i do at this step?

It means it can't find Data_Shared.zip so my guess would be either the file is corrupt or it isn't where the installer thinks it is... make sure you are writing the correct paths.. 

CD to your game dirctory...  for me that would be

```
cd ~/.Games/nwn
```

and then..

```
unzip -o /media/cdrom/Data_Shared.zip
```

where '/media/cdrom/' is the path to where ever it is your nwn cd is mounted

I'm assuming you have been [here]("http://nwn.bioware.com/downloads/linuxclient.html#nwngoldinstall")

Don't forget linux is case sensitive when it comes to file names and paths.

Hope that helps, good luck.

---

### Post by ekkaal on 2010-05-11
Hello there !

EDIT : I've fixed my problem by installing Wine. Sorry for that !

I have a fresh install of "Lucid Lynx" (Ubuntu 10.04) and I'm trying to install NWN Diamond Edition.

I've followed the guide but was not able to find the Msttcorefonts. I assumed it was included by now with "Lucid Lynx". 

I've downloaded the script. Change the Terminal for Bash and executed it. The script load perfectly well in a Terminal. Thoug upon selecting Dimaond, the window disappeared and I can't go further.

Any idea ?

Thanks in advance

---

### Post by brigadoon on 2010-05-11
> **ekkaal said:**
> Hello there !

EDIT : I've fixed my problem by installing Wine. Sorry for that !

I have a fresh install of "Lucid Lynx" (Ubuntu 10.04) and I'm trying to install NWN Diamond Edition.

I've followed the guide but was not able to find the Msttcorefonts. I assumed it was included by now with "Lucid Lynx". 

I've downloaded the script. Change the Terminal for Bash and executed it. The script load perfectly well in a Terminal. Thoug upon selecting Dimaond, the window disappeared and I can't go further.

Any idea ?

Thanks in advance

Goto Synaptic Package Manager and search for ttf-mscorefonts-installer. This should take care of it once loaded. Also get ttf-liberation for Times, Ariel and Courier.

---

### Post by sniperblade on 2010-06-01
> **wuzzeb said:**
> Here is a small howto to be able to switch back to your desktop while playing Neverwinter Nights, without having to deal with patching libSDL with fullscreen, compiling etc.

Note: I am going to assume nwn was installed in /opt/nwn, if you installed somewhere else you will just need to modify the paths slightly

1) Create a file  /opt/nwn/startnwn (for example, using gedit), and put the following into it
```

#!/bin/sh

display=:1
nwn=/opt/nwn/nwn
user=john

xinit /usr/bin/env DISPLAY=$display /bin/su -c $nwn $user -- $display

```

2) Modify the nwn= line to contain the path to the nwn script (the script you normally run)
3) Modify the user= to contain your login user name
4) If you don't understand what display is, leave it at :1,  otherwise set to whatever you want.

5) Test the script by running sudo /opt/nwn/startnwn  (The startnwn script must be run as root).  You can switch back and forth by using Ctl-Alt-F7 and Ctl-Alt-F8

6) Now you have two options

6.a) Type the password in every time you run nwn.  For this, edit the desktop launcher and/or menu icon to run the command "gksudo /opt/nwn/startnwn"  This will prompt for a password, then run the startnwn script

6.b) In a console, run "sudo visudo"  then add a line on the bottom

```

<username>   ALL = NOPASSWD: /opt/nwn/startnwn

```

modifying the <username> and path to startnwn.  sudo will now run the startnwn script without a password, so in the desktop launcher and/or menu icon command can be set to "sudo /opt/nwn/startnwn"


As I mentioned before, you can then switch back and forth using Ctl-Alt-F7 (desktop) and Ctl-Alt-F8 (nwn)

Hey guys. This is Snipe. I'm new to the forums ^^ hows everyone doing? hope yer all well!!! :)

So, regarding the post i am quoting. I have installed NWN Platinum and i am trying a way to minimize the game/ switch to desktop while playing. Compiling libSDL is a bit too diff for me since i've been using Ubuntu for half a year only, so i just saw this post and thought i'd give it a try. But it gives me an error:

```
sniperblade@sniperblade-desktop:~/nwnv169$ sudo /home/sniperblade/nwnv169/startnwn

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux sniperblade-desktop 2.6.31-21-generic-pae #59-Ubuntu SMP Wed Mar 24 08:47:55 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-21-generic-pae root=UUID=2e57855f-7eda-491b-b7c7-ee45a432139e ro quiet splash
Build Date: 06 May 2010  09:30:46PM
xorg-server 2:1.6.4-2ubuntu4.3 (buildd@) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Tue Jun  1 14:26:47 2010
(==) Using config file: "/etc/X11/xorg.conf"

(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:17:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:18:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:19:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:0) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:1) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:2) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:3) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:4) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@0:20:5) found
(WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found

































Backtrace:
0: X(xorg_backtrace+0x3b) [0x8133d6b]
1: X(xf86SigHandler+0x55) [0x80c7d35]
2: [0xb7773400]
3: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0xb6df84e0]
4: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PHM_DispatchTable+0x114) [0xb6dbb094]
5: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PHM_SetPowerStateDeferrable+0x60) [0xb6db8e30]
6: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0xb6e0a836]
7: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PSM_AdjustPowerState+0x2ee) [0xb6e09bde]
8: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PEM_Task_AdjustPowerState+0x42) [0xb6de4902]
9: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PEM_ExcuteEventChain+0x77) [0xb6de2c37]
10: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PEM_HandleEvent_Unlocked+0x45) [0xb6de0df5]
11: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PEM_HandleEvent+0x39) [0xb6de0ed9]
12: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PEM_Initialize+0x199) [0xb6de11a9]
13: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0xb6db70ed]
14: /usr/lib/xorg/modules/drivers//fglrx_drv.so(PP_Initialize+0x4a) [0xb6db6c4a]
15: /usr/lib/xorg/modules/drivers//fglrx_drv.so(swlPPLibInitializePowerPlay+0xaf) [0xb6d7205f]
16: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxPPLibInit+0x5a) [0xb6d2c70a]
17: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0xb6d78f4e]
18: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0xb6d76e31]
19: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxDisplayMapAddNode+0x141) [0xb6d77031]
20: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxDisplayAdaptorCreate+0xb2) [0xb6d77bd2]
21: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxDisplayPreInit+0x41a) [0xb6d75d2a]
22: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxPreInit+0x1178) [0xb6d2d8b8]
23: X(InitOutput+0x4e9) [0x80b05b9]
24: X(main+0x1cb) [0x807234b]
25: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0xb7461b56]
26: X [0x80719c1]
Saw signal 8.  Server aborting.

 ddxSigGiveUp: Closing log
 ddxSigGiveUp: re-raising 8
giving up.
xinit:  Connection refused (errno 111):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
sniperblade@sniperblade-desktop:~/nwnv169$ 
sniperblade@sniperblade-desktop:~/nwnv169$ 
sniperblade@sniperblade-desktop:~/nwnv169$ 
sniperblade@sniperblade-desktop:~/nwnv169$ 
sniperblade@sniperblade-desktop:~/nwnv169$ 
sniperblade@sniperblade-desktop:~/nwnv169$ 
sniperblade@sniperblade-desktop:~/nwnv169$ 
sniperblade@sniperblade-desktop:~/nwnv169$ 
sniperblade@sniperblade-desktop:~/nwnv169$ 
sniperblade@sniperblade-desktop:~/nwnv169$ 
sniperblade@sniperblade-desktop:~/nwnv169$ 
sniperblade@sniperblade-desktop:~/nwnv169$ 
sniperblade@sniperblade-desktop:~/nwnv169$ 
sniperblade@sniperblade-desktop:~/nwnv169$ 
sniperblade@sniperblade-desktop:~/nwnv169$ 
sniperblade@sniperblade-desktop:~/nwnv169$ 
sniperblade@sniperblade-desktop:~/nwnv169$ 
sniperblade@sniperblade-desktop:~/nwnv169$ 
sniperblade@sniperblade-desktop:~/nwnv169$ 
sniperblade@sniperblade-desktop:~/nwnv169$ 
sniperblade@sniperblade-desktop:~/nwnv169$ 
sniperblade@sniperblade-desktop:~/nwnv169$ 
sniperblade@sniperblade-desktop:~/nwnv169$ 
sniperblade@sniperblade-desktop:~/nwnv169$ 
sniperblade@sniperblade-desktop:~/nwnv169$ 
sniperblade@sniperblade-desktop:~/nwnv169$ 
sniperblade@sniperblade-desktop:~/nwnv169$ 
sniperblade@sniperblade-desktop:~/nwnv169$ 
sniperblade@sniperblade-desktop:~/nwnv169$ 
sniperblade@sniperblade-desktop:~/nwnv169$ 
sniperblade@sniperblade-desktop:~/nwnv169$ 
sniperblade@sniperblade-desktop:~/nwnv169$ 
sniperblade@sniperblade-desktop:~/nwnv169$ 
sniperblade@sniperblade-desktop:~/nwnv169$ 
```

This is the exact output of the console. Any ideas what's wrong? :/
Thanks in advance for your help.
-Snipe-

---

### Post by The Big Head One on 2011-02-08
So, I've installed the game following the BioWare site tips and I was trying to "install" the movies, when I try to 
"**3) Run the nwmovies_install.pl with './nwmovies_install.pl  /usr/lib/libSDL-1.2.so.0'**", this problem happens:
 
NOTICE: Examining sound configuration for some clues...
NOTICE: Take this output with a grain of salt..

NOTICE: It appears none of your PCM playback devices supports
NOTICE: more than one simultaneous channel.
NOTICE: You may need to look into software mixing, via dmix, or ESD/ARTSD.

What should I do?

Thank you.

---------Edit-----------
So, even with these problems, I continued to "install" the movies, apparently everything was apparently perfect. When I used the "./nwn" to run the game the Atari "movie" appeared (with no sound) then the screen went black and nothing happened after that, I tried to use "alt+tab" to switch the windows, but every window was black (The console window, the NWN window and the Bink Player window).

---------Edit2-----------
So I deleted the ./lib of the **nwn** script and now the initial movies work, but when I try to see the campaign movies, the screen frozen and I hear the only sounds of the campaign movies but I can't see them :/ 
What should I do?

---

### Post by ChipDSnow on 2011-07-11
"On Ubuntu, this will be /media/cdrom for the first drive."

Okay, so I'm a total noob when it comes to Linux, and I pray that you all will forgive me.  But I get to this step, and now I'm totally confuzzled (wife made up word, it means to be confused and puzzled at the same time).  

I get this error:  INVALID DEVICE! Please check the device and try again

Now, I've tried _DVD, dvd0, dvd1, cdrom, cdrom0, cdrom 1 and nothing works.

Grr!!

Any help, thanks in advance!!

Chip

---

### Post by MichelMatos on 2011-07-26
Can any good soul update the installation process?

Due the Bioware old foruns arent working, I cant reach any other help to install Neverwinter Nights on Ubuntu 11.04.

Thnx in advance!

---

### Post by MichelMatos on 2011-07-26
Ok, just managed to install all files following a post from Fernando Scherer.

My issue now is the hardware mouse...

---

### Post by crunchy_chicken on 2011-11-29
This is the best that I can do to help you guys, I found this after 6 hrs of searching. Anyways, hope it helps you as well as it did me. 

I couldnt post the actual link, but go to the social section and forums on bioware's official page. its not that hard to find

---

### Post by culinaryforge on 2011-12-11
It warms my heart to see that this thread is still active!

So, I made the big switch from xp to Ubuntu Lucid a couple weeks ago and I couldn't be happier seeing my PC being productive for me instead of being productive for MS.

My problem lies in the execution of the install-nwn.sh script:

Previously I installed all the dependencies to run NWN and copied over from an existing xp install, then added the requisite nwclient129.tar.gz; nwresources129.tar.gz; and English_linuxclient169_xp2.tar.gz. Ran ./fixinstall and I actually had it running up to the choose ' single/lan/internet' game screen so I know that much is there. The game would crash/exit/do nothing when I tried to advance to the multiplayer selection.

I removed /games/nwn/ to start again to see if I had a bad install and started from scratch.

Running install-nwn.sh goes fine up untill it looks for the disks and no matter where I tell it to look, it comes back INVALID DEVICE. I've tried everything in /media/;/dev/; and hdd directories where both install data and data from the cds was copied to but still I get INVALID DEVICE.

Could I be missing some dependency for the script to operate properly? Am I missing something obvious?

cul

---

### Post by mefistofiel on 2011-12-29
here's my story how I made NWN work on linux.

I've tried two methods of instaling NWN on linux, none of them worked. first method was from this site:
[http://robotbutler.org/article/13](http://robotbutler.org/article/13)
I encountered some "no gui found" message and the game freezed. Second method is at the beginning of this thread. However I always got "invalid device" message, no matter what i did (i've got ISO image). so I tried something else. I installed my NWN (diamond edt) by wine. then copied game folder from .wine to where i wanted my linux-NWN to be installed. then I followed steps from Robot Butler's site. everything works fine, apart from movies, which are not being played at all (haven't tried to fix it yet). anyway I thought that native NWN would be faster than wine. It isn't, and the game works fine under wine.

---

### Post by Spuddigger on 2011-12-29
So, being completely new to Ubuntu, I hope I'm not asking a dead end question here.  I recently installed Ubuntu, and shortly thereafter got the itch to play NWN.  However, I don't have it on CD's, I have the downloadable version via Good Old Games.  This version downloads as an .exe file, and two .bin files.  Is there any way to get these working in Ubuntu, or is it strictly limited to Windows?

---

### Post by maria_e_andersson on 2011-12-30
**NWN on Ubuntu 11.10**

To begin with, I have no real experience with Ubuntu or Linux. I just happen to be part of a teacher group where we learn about different kind of computer support where Linux/Ubuntu and Edubuntu was used. I just fell in love with Ubuntu. 

I really want to be able to play NWN and didn't know how to do it in Ubuntu, or if it even was possible. NWN is really the only reason why I should continue to cling to my Windows 7 system. All my other needs are covered by Ubuntu in a nicer way than in Windows. I made an inquiry here:
[http://www.amiaworld.net/phpBB3/viewtopic.php?f=2&t=62939](http://www.amiaworld.net/phpBB3/viewtopic.php?f=2&t=62939) 
and it sounded so good so I thought I'll give it a shot and write down what's easy or hard for a Linux newbie as me to do.

**Technical stuff**
I use a 64 bit packard Bell laptop, bought this year.
Ram: 3,9 GiB
Proc: AMD Athlon(tm) II Dual-Core M320 × 2 
Graphic: VESA: M96 (ATI card) with proprietary drives

**Software and scripts**
Ubuntu 11.10, in my case it's 11.04 64 bit updated to 11.10 and with Swedish language installed inside Windows with the Wubi installer, if it's any difference.

A working 3D  environment. I downloaded and installed the free 3D car game “Vdrift” before so I knew that 3D games are possible to play on the computer.

The english platinum/diamond DVD with all three Cd's on.
* (If you just want to try this out, this DVD can be found as a torrent file in a multitude of places on the Internet)*

1.69 script for Linux found here:
files.bioware.com/neverwinternights/updates/linux/169/English_linuxclient169_xp2.tar.gz (483 MB)

Linux install script here:
[http://ubuntuforums.org/attachment.php?attachmentid=14107&d=1155247716](http://ubuntuforums.org/attachment.php?attachmentid=14107&d=1155247716) (36 kb, but you must be a member of the forum)

You must install the “Unshield” program, do it through the Ubuntu program central (paperbag icon at the left edge of the screen)

nwclienthotu can be found here (37.8 MB):
[http://nwdownloads.bioware.com/neverwinternights/linux/161/nwclienthotu.tar.gz](http://nwdownloads.bioware.com/neverwinternights/linux/161/nwclienthotu.tar.gz)
download it to your home directory unpacked.

Linux client 1.29 can be found here (5.2 MB)
[http://www.fileplanet.com/121474/120000/fileinfo/Neverwinter-Nights-Linux-Client-1.29](http://www.fileplanet.com/121474/120000/fileinfo/Neverwinter-Nights-Linux-Client-1.29)
download it to your home directory unpacked.

**Extra**
I Installed Gmount-iso to mount the DVD iso-file. Maybe you don't have to if you know Linux better than I.

**References**
As I said, I don't have anyone that can help me with this, so I have used information from Internet, mainly this page:
[http://kmandla.wordpress.com/2010/03/23/install-neverwinter-nights-in-ubuntu/](http://kmandla.wordpress.com/2010/03/23/install-neverwinter-nights-in-ubuntu/)
Here is a HOW-TO that I followed too, but gave up. I took the install script from this page though.
[http://ubuntuforums.org/showthread.php?t=113259](http://ubuntuforums.org/showthread.php?t=113259)
For those with just different CD:s
[http://robotbutler.org/article/13](http://robotbutler.org/article/13)


**Begin (09.15 am)**
*I started to download the 1.69 patch for Linux, but here the first problem arose. I have only used the APT package handler before, but the script was submitted in another format called gz. I just opened it with the standard program suggested by Ubuntu. It took me 7 minutes to bring it home.
*I got a list of files and folders, I placed myself in my home directory and extracted all. Maybe that wasn't too smart, but so it was written in the guide. Now I have a mess of files in my home directory instead.
*It says “Enable the Universe repository; Open up Synaptic Package Manager, System -> Administration -> Synaptic Package Manager. Enter in your Password. Click on Settings, and select Repositories. Click Add. Then put check marks in the box for Community maintained (Universe) and while you're at it, may as well put one in Non-free (Multiverse)” 
But here I'm stuck. Universe or Multiverse can't be found. At all. I assume I check “Updates without official support (sourcecode)”  and “Independent (sourcecode)” instead.

Next step says: “After clicking OK on both dialogs, click Search and type in unshield. It will show three packages, just double click on unshield and it will ask you if you also want to mark libunshield, which is required. Click Mark. Click Search again and type in msttcorefonts. Double click it to queue the package and click Apply. This will download and install both Unshield and the fonts required by Nevewinter Nights. Unshield is required by the installer”, so I do as it says. I search for unshield but to no avail. So here I'm stuck for good and the time is 09.46 am.

**Step 2**
*I decide to go with just the script. 
[http://ubuntuforums.org/attachment.php?attachmentid=14107&d=1155247716](http://ubuntuforums.org/attachment.php?attachmentid=14107&d=1155247716)
But here is next problem, I can't get it without being member of the Ubuntu forum. How stupid isn't that? After I have filled in the membership registration, I got the script: install-nwn.sh.tar.gz in my home directory, unpacked it to install-nwn.sh
*By default Ubuntu uses dash as a shell, but the script relies on bash to run properly. So to change it, you start a terminal (CTRL+ALT+T) and write:
[FONT=Courier New]sudo dpkg-reconfigure dash[/FONT]
And answer No if you want it to be permanent (which you don't). After installing the game, you'll probably want to switch back to using dash, as to not mess up any advantages of speed that dash may provide. Run the command again and select Yes.
*You'll probably need Microsoft TTF fonts in the game too, so you install them with:
sudo aptitude install -y unshield cabextract ttf-mscorefonts-installer
But that doesn't work sighs it says that aptitude is an unknown command. Why? I don't know, it's 10.08 am and I take a coffee break to calm down. 
Tries: [FONT=Courier New]sudo apt-get install -y unshield cabextract ttf-mscorefonts-installer[/FONT]
and it works just fine. But it turns out that I already have all fonts needed and the command does nothing.

**Mounting the DVD**
I'm not a Linux geek and I don't know how to mount stuff. So I just put the DVD in the lap top and let Ubuntu read it. It seems to work just as fine as in Windows with a DVD icon in the left task bar which I can read by just double click on it.

**Create install directory**
Use the same terminal window and write:
[FONT=Courier New]mkdir -p ~/games/nwn[/FONT]
It creates a new directory called games and under that a directory called nwn in your home directory.

**Install the script**
So, the old script from the ubuntu forum is downloaded and ready to run, let's try to use the terminal window and write:
[FONT=Courier New]./install-nwn.sh[/FONT]
Bugger “file doesn't exist” it says. Checking again, the file is not extracted, instead it's in the download folder but it is greyed out and I don't know why. I right click on the archive, choose “Extract here” which seems to work and after that I move the file to my home directory and try again:


**Platinum or Diamond?**
The script start and I have a choice, do I have the platinum or the diamond edition? How am I supposed to know when it's not written on the outside? Diamond edition has three extra premium modules, if you don't have those three extra modules, you have a platinum edition, or De Luxe edition as it is called in Europe.
[FONT=Courier New]./install-nwn.sh[/FONT]
Next error comes here; the script ends with a halt since it wants “unshield”. Unshield isn't installed, but can be found here according to the terminal window message:
[http://synce.sourceforge.net/synce/unshield.php](http://synce.sourceforge.net/synce/unshield.php)
To bad, it goes to a 404 page. Sighs
I use the Ubuntu Program Central instead (icon at left side of screen that looks like a paper bag) and types in “Unshield”. And there I got a hit.

I try the script again after installing Unshield:
[FONT=Courier New]./install-nwn.sh[/FONT]
and now it's working just fine

**CD or DVD**
I'm using a DVD so I choose that.

**Client files**
I know I have downloaded 1.69, but not the rest. Now it complains that nwclient129.tar.gz and nwclienthotu.tar.gz can't be found. I better download them now then....
Version 1.29 can't be found where the instruction page has a link, it's dead. I have to search for nwclient129.tar.gz in some other way. Gooogle showed a lot of option and I choose this place:
[http://www.fileplanet.com/121474/120000/fileinfo/Neverwinter-Nights-Linux-Client-1.29](http://www.fileplanet.com/121474/120000/fileinfo/Neverwinter-Nights-Linux-Client-1.29)
Nwclienthotu.tar.gz could be found here:
[http://nwdownloads.bioware.com/neverwinternights/linux/161/nwclienthotu.tar.gz](http://nwdownloads.bioware.com/neverwinternights/linux/161/nwclienthotu.tar.gz)

After I have downloaded both and copied the unpacked archives to my home directory, I try to just hit yes I have the files in my hoe folder and hit enter.

Next problem “Patch file could not be found in home folder” what the … does that mean? I hit Y for yes and try to download it. Next question, what patch do I want to use? 1.67 is the highest, but I use 1.69. Hmm. According to the guide, I can just write in “169” and then choose “english” as language. 1.67 was the highest patch number when the script was written, but with 169 it searches for the right script. Let's try it:
169 and then ENG for English works just fine, but after that it can't find the DVD!? It looks for it in /media/dvd but as the noob I am, I have no clue about where it is to be found or how to make Ubuntu find it. When I check it graphically in the explorer window, it seems to be /media/_DVD but trying that I just get the answer that /media/_DVD is a folder. So, here I'm stuck. I have to mount that DVD anyway

**Mounting a DVD**
Open a terminal window and write:
[FONT=Courier New]sudo mount _DVD.iso /media/floppy0 -t iso9660 -o loop[/FONT]
Error; the file or catalog doesn't exist. 
I try:
[FONT=Courier New]sudo mount _DVD.iso /media/isoimage/ -t iso9660 -o loop [/FONT]
Doesn't work either

So here I am, totally stuck and the silly thing is that I can open any file in the /media/_DVD folder where the DVD disc for NWN is to be found, I just can't start the install script for it. The problem is that I don't know if the error message say that it  can't find the source DVD or if it can't find the destination folder.

On Internet, I found a link to a small program called Gmount-iso which can be used to mount ISO files in Ubuntu. I Install it through the program central.  

It turns out that it is nigh impossible to mount the files. The programs are looking for an ISO file but can't find it, only the files on the DVD. To be able to install NWN I have to copy the DVD to an ISO file to be able to mount it. Silly? Yes, I think I'm doing something wrong but it seems to be the only way to do it. It's 2.3 GB in size. I do hope Wubi can manage such large file.

The time is 11.20 am and I'm utterly frustrated.

I use the terminal in the media folder and create a new folder named floppy0:
[FONT=Courier New]sudo mkdir floppy0[/FONT]
And after that I went to my home directory and wrote:
[FONT=Courier New]sudo mount _DVD.iso /media/floppy0 -t iso9660 -o loop[/FONT]
And it worked.... I copied the DVD ISO to no avail, the problem was that it had no folder named floppy0 to mount at. I get a warning that it's read only, but I assume it's ok since it's a DVD disc.

**Try 3 from the beginning:**
Run script:
[FONT=Courier New]./install-nwn.sh[/FONT]
Choose 5 (= platinum edition for me)
finds Unshield => hit enter
Choose DVD => Enter
Finds both client files => Enter
Asks for patch file => Hit Y and Enter
169 => Enter
ENG => Enter

And now, enter the path to the mounted DVD
/media/floppy0
[I]Error, invalid Device
bash: /media/floppy0: is a folder[/I]
 (sighs heavy)....

I try to mount the copied ISO to floppy0 by using Gmount-iso, but I just get the error message that floppy0 isn't empty (of course not since it connects to the DVD). Stuck again.


**Try 4**
I create a new folder in media and name it cdrom. Use chmod777 to make it usable by all.
[FONT=Courier New]Sudo chmod777 cdrom[/FONT]

After that, I use Gmount-iso to mount my copied ISO-file. Same error again:
[I]An error occured 
 /media/cdrom seems to be mounted read-only[/I]
But it is an ISO from a disc so that shouldn't be a problem.

Go back to home folder and run all scripts again:
But with the same error:
*INVALID DEVICE! Please check the device and try again*

When I try to unmount it, I get this error:
*umount: /media/cdrom is not in fstab*

So, right now its 12.38 pm and I'm giving up. Are there anyone else who can help me by telling me how to mount that ISO so the installation might go on?

//Maria

---

### Post by tsagas on 2012-01-12
> **maria_e_andersson said:**
> **NWN on Ubuntu 11.10**

When I try to unmount it, I get this error:
*umount: /media/cdrom is not in fstab*

So, right now its 12.38 pm and I'm giving up. Are there anyone else who can help me by telling me how to mount that ISO so the installation might go on?

//Maria

Maria, try this:

```
sudo mkdir /mnt/iso
sudo nano /etc/fstab
```

add this to /etc/fstab (replace my_nwn_dvd.iso with the full path to your iso file):

```
my_nwn_dvd.iso    /mnt/iso    iso9660    noauto,loop,ro    0 0
```

Now: 

mount (full path to iso)

when the script asks for dvd path, give '/mnt/iso'

After installation, remove that entry from your /etc/fstab, or comment it out.

---

### Post by Einder on 2012-01-12
The script isn't working for me at all. I get to the cdrom path, and since I'm using ubuntu 11.10 I figured it would be /media/cdrom however it keeps closing out the script when I enter that and hit enter. Any advice on how to fix it?

EDIT: Found that I was getting an INVALID DEVICE error, am looking for the solution...will post it if I find it.

---

### Post by AggieDan on 2012-02-09
Okay, I'm running into some problems, too.  I used to use linux a lot.  Mind you, used to.  So, now that I have a newish laptop (Dell Latitude E5400 - integrated Intel video and sound) to play with I have been trying to get nwn to work in Ubuntu to currently no avail.  Actually, it works, but just with no sound.

To remove any chance that I've mucked things up by trying to get expansion packs installed, I've done the bare minimum to get a 1.29 install to work.

in my home directory...

mkdir ./nwn
tar -xvjf ../nwresources129.tar.gz
cd ~/nwn
tar -xvjf ../Downloads/nwclient129.tar.gz

When I type ./nwn I'm able to launch the game, but there is no audio and the audio options screen does not have any sound providers under advanced sound options.  Additionally, the only speaker configurations available are 5.1 and 7.1.  When choosing either of these, the game crashes.

---

### Post by AggieDan on 2012-02-10
Amazing what search will do.

Added the libsdl1.2debian-esd package and then added the following to my nwn script :

```
export SDL_AUDIODRIVER=esd
```

---

### Post by AfterBerner on 2012-04-25
Hey All,

I've been trying to install this on 11.10 with no success.  I've got everything up to the "INVALID DEVICE! Please check the device and try again".  We got around this on 10.04 by unpacking the ISO into the media file directly and in 10.04 it worked.  In 11.10....it does not.  I've also tried various file folders created into the media folder with names matching the /media/dvd that the installation program calls for as well as various NWN or NW_DIAMOND names.  No luck/joy.  Anyone familiar with the installation program "install-nwn.sh" might be able to help, but my linux programming is non-existant.  Please help.  This is a wonderful game and I'd like to be able to use it under Linux/Ubuntu.

:(

---

### Post by ergo-proxy on 2012-04-26
> **AfterBerner said:**
> Hey All,
 
I've been trying to install this on 11.10 with no success. I've got everything up to the "INVALID DEVICE! Please check the device and try again". We got around this on 10.04 by unpacking the ISO into the media file directly and in 10.04 it worked. In 11.10....it does not. I've also tried various file folders created into the media folder with names matching the /media/dvd that the installation program calls for as well as various NWN or NW_DIAMOND names. No luck/joy. Anyone familiar with the installation program "install-nwn.sh" might be able to help, but my linux programming is non-existant. Please help. This is a wonderful game and I'd like to be able to use it under Linux/Ubuntu.
 
:(
 
It's waste of time, run it on wine it's far more stable.

---

### Post by oldrocker99 on 2012-04-26
> **ergo-proxy said:**
> It's waste of time, run it on wine it's far more stable.

Hmmm...I have been running Neverwinter Nights with the Linux client for over four years. I have not had to reinstall it in quite a while (my /home directory is on a separate drive), but here's a post from the GOG.com forums (where they sell the Platinum Edition for a measly $10):
[http://www.gog.com/en/forum/neverwinter_nights_diamond/linux_playability/page1](http://www.gog.com/en/forum/neverwinter_nights_diamond/linux_playability/page1)

This may help ya out.

---

### Post by vanquishedangel on 2012-05-03
> **ergo-proxy said:**
> It's waste of time, run it on wine it's far more stable.

Actually I have not found that so on this attempt to install it. Installing in wine gives me crashes with no error reported from both main.exe and nwn.exe. But it did work beautifully before.

I did get it to work however following this guide: 

[http://www.google.com/url?sa=t&rct=j&q=install%20nwn%20ubuntu&source=web&cd=6&ved=0CFMQFjAF&url=http%3A%2F%2Fsocial.bioware.com%2Fforum%2F1%2Ftopic%2F187%2Findex%2F4643217%2F1&ei=-3WiT7HPFYGs8QSAvZ3hCA&usg=AFQjCNGmKipu-fvIXw9sHqvBYJjBOpfxvQ](http://www.google.com/url?sa=t&rct=j&q=install%20nwn%20ubuntu&source=web&cd=6&ved=0CFMQFjAF&url=http%3A%2F%2Fsocial.bioware.com%2Fforum%2F1%2Ftopic%2F187%2Findex%2F4643217%2F1&ei=-3WiT7HPFYGs8QSAvZ3hCA&usg=AFQjCNGmKipu-fvIXw9sHqvBYJjBOpfxvQ)
I cannot get kingmaker working or any of the premium modules but I read somewhere that that could be because they have to authenticate and they no longer can, so I didn't install them this time. (wish I would have read that before wasting time trying) Also I cant seem to get the movies working either.

---

### Post by Colsta on 2013-04-04
Has anyone got a precomiled version of nwmouse.so they can post up for me to try?
I've spent two days searching and downloading various libraries trying to compile this for myself but have hit a brick wall trying to bring in libsdl1.2-dev:386 since when I try to do so, apt wants to uninstall half my OS (seriously)!  I'm currently on Ubuntu 12.04 LTS (not that I can amend my original profile to add that - whoever made the decision to retrospectively add a policy of 25 posts before that can be done needs their bumps felt).

---

### Post by tsagas on 2013-04-04
> **Colsta said:**
> Has anyone got a precomiled version of nwmouse.so they can post up for me to try?

There you go.

---

### Post by Colsta on 2013-04-05
You sir are a gentleman for posting that so quickly - you have my thanks.  It's all working splendidly now.

Having spent no more than about 20 minutes installing NWN on linux natively (thanks to Leech and other helpful souls both here and in the Bioware forums), I spent two long days playing the library shuffle trying to get this last aspect working only to get stymied when the end was in sight.  (Incidentally I see I'm not alone having problems importing libsdl1.2-dev:386 as there's a similar bug in launchpad.)

---

