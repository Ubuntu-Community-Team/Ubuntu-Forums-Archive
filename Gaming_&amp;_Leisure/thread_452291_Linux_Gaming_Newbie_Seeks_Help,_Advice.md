---
title: "Linux Gaming Newbie Seeks Help, Advice"
date: 2007-05-23
forum: Gaming &amp; Leisure
---

### Post by Gazimoff on 2007-05-23
Hi al,

Well, I've had Ubuntu 7.04 up and running for a week or two now and I'm now looking at migrating across some of my Windows games to Linux. I'm completely new to this side of things, with my only previous experience being setting up LAMP servers. Any advice, suggestions etc that you can make would be greatly appreciated.

I'm using the AMD64 version of Ubuntu FF. I've also grabbed the 64-bit version of wine. I'm using the NVidia restricted driver.

Hardware specs in case you need them are:
Intel Core 2 Duo 6600
Gigabyte GA-965-DS3P motherboard.
2GB Crucial Balistix Tracer PC6400 DDR SDRam (running in dual channel mode)
NVidia GeForce 7900 with 256MB on board RAM
250GB Seagate SATA HDD. Linux has a 50GB slice of that.

I'd be looking to run the following games on this system. I have them on CD/DVD, installed on Windows
Doom 3
Quake 4
Stalker
World of Warcraft (including expansion)

If anyone has any suggestions or advice on setting this up, that would be great. Additionally, if anyone has any recommendations on 3D benchmarking tools, demos or screensavers that run on Linux I'd be really keen to see them. I know how this machine performs on Windows and I'd like to get a feel for performance on Linux.

Many thanks for your time and any help/advice/suggestions you can offer!

---

### Post by Rhubarb on 2007-05-23
Doom 3 and Quake 4 both have native linux installers.  They're on id's website somewhere (id's ftp servers are really slow, so try and download them off a mirror somewhere).

I haven't had any experience with doom 3, but I know for sure you can get quake 4 running on 64 bit Feisty fine.

To get quake 4 running, download "quake4-linux-1.3-2.x86.run" (I can't remember where I download it from, but it's free on the 'net somewhere).
Make some directories in your home:  ~/quake4/q4base
Copy all the *.pk4 off your quake4 DVD / CDs (in the q4base directory) over to ~/quake4/q4base.
Execute the quake4-linux-1.3-2.x86.run binary (./quake4-linux-1.3-2.x86.run), and tell it to install to ~/quake4

That's it!
You don't even need the quake4 DVD / CD in the drive to play the game (in fact, you don't even need the quake 4 DVD / CD to install the game either - make up an .iso of it if need be).
You will need to enter in your serial number once the game has started up.
(The Serial is kept in ~/.quake4/q4base/quake4key).
If need be it's quite easy to manually set the resolution if you have an odd resolution monitor (like mine here is 1680 x 1050)
~/.quake4/q4base/Quake4Config.cfg  :-
```
seta r_customHeight "1050"
seta r_customWidth "1680"
seta r_mode "-1"
```

I've seen posts here of people succesfully getting WoW working (with wine I think)

---

### Post by Gazimoff on 2007-05-23
OK, I've copied the files from the DVD and downloaded the .run file, but how do I execute it? Every time I double-click on it, it opens up a text editor.

---

### Post by Nesnej Trick on 2007-05-23
> **Gazimoff said:**
> OK, I've copied the files from the DVD and downloaded the .run file, but how do I execute it? Every time I double-click on it, it opens up a text editor.
You'll need to give yourself run permissions first. Just right-click the file, go into "properties", select the "permissions" tab and tick the box "run" for the appropriate users.

---

### Post by Iarwain ben-adar on 2007-05-23
> **Gazimoff said:**
> OK, I've copied the files from the DVD and downloaded the .run file, but how do I execute it? Every time I double-click on it, it opens up a text editor.

Hiya there,

There is a program called [wine](http://winehq.org/) to run Windows programs (and games aswell) in Linux.

Try to install it by following these instructions => [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Then go to your terminal, and move to the dir you copied your files to.
```
cd game_dir/
```

Use wine to launch the program when you are in the right dir
```
 wine program_name
```

This will bring up a screen of your program, allowing you to install stuff etc.


Iarwain

---

### Post by rajeev1204 on 2007-05-23
> **Gazimoff said:**
> OK, I've copied the files from the DVD and downloaded the .run file, but how do I execute it? Every time I double-click on it, it opens up a text editor.


Type in terminal  sudo sh filename.run

this will run it .


Quake 4 and doom3 run fine on ubuntu . 

If u have sound issues , at the beginning run the game(after u have finished install) from terminal like this : quake4 +set s_driver oss.

Do this only if u have sound issues .

---

### Post by tribunal on 2007-05-23
And you should divide native games and other games, not native
Doom3 and Quake IV have native installers and native binaries, so we can call them native games
Installing them and running them is not very difficult to do usually
If you want to run windows-games, not native, you have to use some kind of emulator
Usually it is WINE or CEDEGA
WINE is free and Cedega is not, but Cedega is better for some games, cause they are specialized in running games
There are a lot of articles about running WoW in Linux, using wine or cedega
And S.T.A.L.K.E.R. can be started using Wine and this patch:
[http://bugs.winehq.org/attachment.cgi?id=5641&action=view]("http://bugs.winehq.org/attachment.cgi?id=5641&action=view")
I can tell you more, if you want to use wine

---

### Post by Bagnaj97 on 2007-05-23
I'm fairly certain that the 64bit verison of wine currently only runs 64bit windows applications as there is no wine implementation of the wow64 (windows on windows64) library. If this is the case you will need the 32bit version of wine, which might not work with 64bit Ubuntu. There are some details on [this page(http://wiki.winehq.org/WineOn64bit)]("http://wiki.winehq.org/WineOn64bit") which might be helpful.

---

### Post by Cappy on 2007-05-23
64-bit wine only runs 32-bit windows applications. 64-bit Windows applications cannot be run on either 32-bit or 64-bit.
Also, don't follow the instructions for installing WINE from that link above.
Ubuntu has a MUCH simpler way. Just follow this:
[http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

I'll copy and paste the commands to install WINE here for simplicity.
```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update
sudo apt-get upgrade

```

---

### Post by Gazimoff on 2007-05-23
OK, Doom3 runs without problems, although when it exits Gnome doesn't seem to do a screen redraw. I'll try and screenshot it to show you what I mean.

Quake4 seems to install fine (I had to sudo install it), but does not run. It says it failed writing a file to .quake4/q4base/ It's strange, as I couldn't see a .quake4 folder.

---

### Post by misfitpierce on 2007-05-23
I use Cedega but it charges. I find it worth it though. :)

---

### Post by The Squig on 2007-05-23
wow on linux [http://www.wowwiki.com/Linux/Wine](http://www.wowwiki.com/Linux/Wine).


I just download wine and ran the game with the -opengl switch. ex wine wow.exe -opengl . Should work with the launcher also. if you run into trouble you could try the guide.

---

### Post by Pikestaff on 2007-05-23
Here's another great guide for getting WoW working with Linux: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

I personally have had very little problems with WoW and Wine, Blizz games are typically fairly easy to run on Linux even if they aren't available natively.  There is a weird thing going on with the latest patch right now (causing the program to freeze on exit, among other things) but this seems to be happening to a lot of people and not just with Linux so I'm assuming there will be a fix available soon.

---

### Post by Cappy on 2007-05-23
I forgot the most import step earlier:
```
sudo apt-get install wine
```
^^

---

### Post by Gazimoff on 2007-05-24
An improvement in Quake4 - it installs and runs now, but all I get is a black screen with the game sounds playing. Doom 3 is running natively though, performing better than it did under Windows too!

---

### Post by lou1998 on 2007-05-24
I initially installed 64 bit Ubuntu and had problems getting wine to work, so I decided to go with 32 bit Ubuntu.  Right now I run Ubuntu 6.06 and  have been able to successfully run WoW (with TBC Xpac), Doom 3 and Neverwinter Nights. 
I haven't tried Quake 4 yet.  
The how-to articles on this forum are fairly detailed and allowed me to get things up and running without knowing much about Linux.

---

