---
title: "Exult: What Do I Need?"
date: 2007-06-16
forum: Gaming &amp; Leisure
---

### Post by plinydogg on 2007-06-16
Hi everyone,

I'm glad to learn that Exult (the Ultima 7 emulator), which I had on Windows, is also available for Linux. I'm a newbie to Linux and I can't figure out what I need to download in order to install it. The link is here:

[http://exult.sourceforge.net/](http://exult.sourceforge.net/)

What do I need to download from this site? And then what do I need to do with it?

Any help would be much appreciated. Thanks in advance!

---

### Post by cogadh on 2007-06-16
No, you don't need to download it from there, it is available in the Games and Amusements (multiverse) repository.

---

### Post by plinydogg on 2007-06-16
cogadh: Thanks! See, I'm such a newbie that I haven't yet learned to accept how easy things can be with Ubuntu :)

---

### Post by plinydogg on 2007-06-16
Okay. Another stupid question: I installed Exult and copied my Ultima 7 (original Black Gate version) files to my home directory (I don't know where else to put them). So, they're here:

/home/ben/Ultima7

I went to edit the exult.cfg file to let Exult know what the path to the files was and wrote the following:

[HTML]<blackgate>
    <title>
    blackgate
    </title>
    <path>
    /home/ben/Ultima7  
    </path>
   </blackgate>
   <serpentisle>
    <title>
    serpentisle
    </title>
    <path>[/HTML]

But when I try to run Exult it can't find the files. What am I missing?

Thanks in advance (again)!

---

### Post by plinydogg on 2007-06-17
Okay, I got it working. For others with the same question, make sure that you are editing the exult.cfg file that is in your home directory (not the one in the etc directory). 

Edit the exult.cfg file by inserting between the <path></path> tags this:

/home/yourname/.exult/blackgate

repalce "yourname" with your name. 

Put the Ultima 7 files in the .exult/blackgate subdirectory of your home directory (you may have to View-->show hidden files first).

---

### Post by Nossie on 2007-06-22
I bought the game a while ago...  I think it was the EA classics double cd box... the same with strike commander..

Sadly, although I know the box exists somewhere in my room I've no idea where it is!

I have however downloaded the software again from abandonia.com ... but I'm not having much luck setting it up... can anyone tell me where the files go? I've been trying to follow the 'guide' posted here but all I have are some files and a 'static' folder... what stuff goes in the exult 'blackgate/gamedat' folder ?


ty for any help

---

### Post by Gen2ly on 2007-12-21
Good question.  I have Ultima 7 but now I own PPC so I am not able to install Ultima 7 through wine.  If anyone has this installed, please give a file listing.

---

### Post by Khar on 2008-04-18
I got it working after some fiddling.

First, install Exult through Synaptic. Then copy the STATIC folder and the following files into /home/YOURNAME/.exult/blackgate: install.exe, endgame.exe, install.prm, intro.exe, mainmenu.exe, u7.cfg, u7.exe, ultima7.com

Next, edit the Exult.cfg file by typing:
sudo gedit ~/.exult.cfg in a terminal window, and edit the path parameters so they read as follows:

    <path>
    /home/YOURNAME/.exult/blackgate
    </path>

Add the following under the  </savegame_path> line

    <music_path>
    /usr/share/games/exult/music
    </music_path>

Next, go to [http://exult.sourceforge.net/download.php](http://exult.sourceforge.net/download.php) and download 'Sound Pack for Black Gate', 'Ogg encoded Music files for Exult Part 1' and 'Ogg encoded Music files for Exult Part 1'.

Extract the oggs to 'music' folder on your desktop, and extract the jmsfx.flx file to your desktop.

Then type the following in a terminal window:
cd ~/Desktop 
sudo cp jmsfx.flx  /usr/share/games/exult/
cd music
sudo mkdir /usr/share/games/exult/music
sudo cp *.* /usr/share/games/exult/music

Then run Exult, start a new game and press Esc to bring up the options menu. Go into the audio options and change the driver to digital. Now the game, music and sound effects should all be working!

---

### Post by cbreaker on 2009-10-22
Okay so I am running Jaunty 9.04 and I can't for the life of me get this working.   It always says data files not found.

I am using the same copies of U7 BG and SI that I did on Windows.

I've tried editing the config files in both /etc/exult.cfg and ~/.exult.cfg with no avail.

When I run exult from the console I see this:

```
Exult version 1.4.05cvs
Built at: Oct  1 2008 20:22:47
Compile-time options: USE_TIMIDITY_MIDI, USE_FMOPL_MIDI, USE_EXULTSTUDIO, HAVE_ZIP_SUPPORT
Compiler: gcc, version: 4.3.2

Platform: Linux version 2.6.28-15-generic 
Exult path settings:
Data          : /usr/share/games/exult
Digital music : /usr/share/games/exult/music

Black Gate   : not found (<BLACKGATE_STATIC>/)
Forge of Virtue   : not found (<FORGEOFVIRTUE_STATIC>/)
Serpent Isle   : not found (<SERPENTISLE_STATIC>/)
Silver Seed   : not found (<SILVERSEED_STATIC>/)
OGG Vorbis Digital Music: Disabled
Trying: `Timidity'
timidity.cfg: No such file or directory
Failed to initialize midi player (code: 1)
Failed!
Trying: `UnixSeqDevice'
UnixSeqDevice: opening device: /dev/sequencer
Success!
Midi Output: Enabled

```

Note that I installed version 1.4cvs from ppa to see if anything changed.   Same exact results.

For the love of all things holy, why is this so hard?   Is there any way for me to find out what exactly where exult is looking?

Thanks..

---

### Post by Perfect Storm on 2009-10-22
> Data          : /usr/share/games/exult
Digital music : /usr/share/games/exult/music

It is still looking in this places. How's the config exult file looks like in your $home?
But you could move the data files to the "default" places instead.

---

### Post by cbreaker on 2009-10-22
Okay so I got it to work - the exult.cfg file that came with the package was all sorts of broken.    I cleaned it up and now it works.

yay!

---

### Post by fijau on 2010-01-11
Another question:
Where can I find the file storing key bindings? On Exult website I found this name: 'bgdefaultkeys.txt' but it doesn't exist on my computer!
And I'm trying to find it, because it seems to me, that one of the keys doesn't work. Well, it's highly probable I'm mistaken, but still, where can I change default key command?

I'm using Ubuntu 9.10 and Exult 1.2-13.

Thanks.

---

### Post by fleischkuchen on 2010-12-27
> **cbreaker said:**
> 

...
When I run exult from the console I see this:
...




i am having the same problems getting ultima ii started. how do you 'run' exult on console. i am a nb as well and tried commands like exec/display/show/prompt to see the console-screen you posted (i am using ubuntu maverick).

Many thanks in advance

---

