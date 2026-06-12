---
title: "America's Army 2 Special Forces - Need Some Help Completing the Installation"
date: 2010-12-17
forum: Gaming &amp; Leisure
---

### Post by marl30 on 2010-12-17
I ran the file:** armyops250linux.run** in terminal, midway through the installation I see this: **Please enter the installation path [/usr/local/games/armyops] . **This where I'm stuck because I don't know what enter there. I need some help to complete this installation.

---

### Post by marl30 on 2010-12-17
So I got it to install by using sudo sh armyops250linux.run. It installed successfully and starts, but no sound, plus it did not install any icons to launch the game. I had to launch it from it's path:/usr/local/games/armyops

Installing some of these Linux games is just a pain. :(

Anybody want to checkout this game and see if you can get it to work properly, here is the site: [http://www.filefront.com/4310823/AASF-Direct-Action-v2.5-Linux-Full-Install/#](http://www.filefront.com/4310823/AASF-Direct-Action-v2.5-Linux-Full-Install/#)

---

### Post by tommcd on 2010-12-17
> **marl30 said:**
> So I got it to install by using sudo sh armyops250linux.run. It installed successfully and starts, but no sound, plus it did not install any icons to launch the game. I had to launch it from it's path:/usr/local/games/armyops
Try running **armyops** from the terminal. It should have created a symlink for launching the game in /usr/bin/, which should be in your PATH.
If you want an icon on your desktop, just go to /usr/local/games/armyops and right-click on the launcher for the game, and choose to create a desktop shortcut for it. For sound, check if the game is using OSS instead of alsa. If it is, then make sure no other apps are using your sound card when you launch the game. Or set the game to use alsa if you can.
> **marl30 said:**
> 
Installing some of these Linux games is just a pain. :(
It helps to read the documentation first, assuming there is any for this game.
> **marl30 said:**
> 
Anybody want to checkout this game and see if you can get it to work properly, here is the site: [http://www.filefront.com/4310823/AASF-Direct-Action-v2.5-Linux-Full-Install/#](http://www.filefront.com/4310823/AASF-Direct-Action-v2.5-Linux-Full-Install/#)
I am downloading the game now to try it on Slackware.

---

### Post by tommcd on 2010-12-17
The game runs just fine for me on Slackware 13.1 32bit. It does create a symlink in /usr/bin, so you should be able to launch it just by running *armyops* in the terminal like I did.
 The sound is set to OpenAL, and that is the only choice the game gives you. The weird thing is, I don't even have OpenAL installed on Slackware and I got sound in this game.
Try installing *libopenal1* on Ubuntu, and see if that gives you sound in armyops. And make sure no other apps are using your sound card when you launch armyops.
[http://packages.ubuntu.com/maverick/libopenal1](http://packages.ubuntu.com/maverick/libopenal1)
There does not seem to be a package in the Maverick repos just named OpenAL.

---

### Post by marl30 on 2010-12-18
> **tommcd said:**
> The game runs just fine for me on Slackware 13.1 32bit. It does create a symlink in /usr/bin, so you should be able to launch it just by running *armyops* in the terminal like I did.
 The sound is set to OpenAL, and that is the only choice the game gives you. The weird thing is, I don't even have OpenAL installed on Slackware and I got sound in this game.
Try installing *libopenal1* on Ubuntu, and see if that gives you sound in armyops. And make sure no other apps are using your sound card when you launch armyops.
[http://packages.ubuntu.com/maverick/libopenal1](http://packages.ubuntu.com/maverick/libopenal1)
There does not seem to be a package in the Maverick repos just named OpenAL.

libopenal1 seems to already be installed. When I opened the game a second time and checked on the sound configuration, I saw an option to set to software instead of Openal. I set it to that and the game crashed. It has not been able to start since. I wonder if because I'm using 64 bit has anything to do with it?

---

### Post by tommcd on 2010-12-18
> **marl30 said:**
>  When I opened the game a second time and checked on the sound configuration, I saw an option to set to software instead of Openal. I set it to that and the game crashed. It has not been able to start since.
I don't even get the option for software under audio. The only option I have is OpenAL. The game seems to be using OSS instead of alsa as near as I can tell. I tried running the AA game today and the sound worked. But after quitting the game I could not get sound in any other app until I closed the terminal that I ran the game from. This is characteristic of OSS, where only one app at a time can use the sound card.
> **marl30 said:**
> 
 I wonder if because I'm using 64 bit has anything to do with it?
I think there may be some problems with AA and that evil scourge pulseaudio that Ubuntu uses. See this:
[http://forums.linuxmint.com/viewtopic.php?f=49&t=60553&p=346352](http://forums.linuxmint.com/viewtopic.php?f=49&t=60553&p=346352)
Also, the game does not seem to be very well supported in linux:
[http://ubuntuforums.org/showthread.php?t=1530344](http://ubuntuforums.org/showthread.php?t=1530344)

---

### Post by marl30 on 2010-12-18
> **tommcd said:**
> I don't even get the option for software under audio. The only option I have is OpenAL. The game seems to be using OSS instead of alsa as near as I can tell. I tried running the AA game today and the sound worked. But after quitting the game I could not get sound in any other app until I closed the terminal that I ran the game from. This is characteristic of OSS, where only one app at a time can use the sound card.

I think there may be some problems with AA and that evil scourge pulseaudio that Ubuntu uses. See this:
[http://forums.linuxmint.com/viewtopic.php?f=49&t=60553&p=346352](http://forums.linuxmint.com/viewtopic.php?f=49&t=60553&p=346352)
Also, the game does not seem to be very well supported in linux:
[http://ubuntuforums.org/showthread.php?t=1530344](http://ubuntuforums.org/showthread.php?t=1530344)

I don't think I'll be fighting to get this game working. I'm sure I'll find other great free games. If that means running them order Wine, I don't mind. How do I uninstall it?

---

### Post by tommcd on 2010-12-19
> **marl30 said:**
> I don't think I'll be fighting to get this game working. I'm sure I'll find other great free games. If that means running them order Wine, I don't mind. How do I uninstall it?
First please understand that this is not a *linux* problem. It is the AA developers lack of sufficient support for linux that is the problem. Games that are well supperted on linux like Nexuiz, Sauerbraten, World of Padman, Doom3, Quake4, Alien Arena, Cold War, etc, etc, work about as well on linux as they do on  Windows.

If you want to have a go at starting the game again, just rename the *.armyops* directory in your home directory to *.armyops.bak*. Then restart the game. This will create a new pristine *.armyops* directory in your home directory with the default settings that should allow you to launch the game again. 
You may also want to try running *gstreamer-properties* in the terminal and set everything to alsa, so as to remove pulseaudio from the picture. Note that this will not remove pulseaudio. It will just set all (or most anyway) of your sound apps to alsa, where they should be!!!
 Or better yet, remove  pulseaudio by removing  **pulseaudio** and **gstreamer0.10-pulseaudio** with apt-get or synaptic. Then run 
**gstreamer-properties** and set everything to alsa.

If you are hell bent on removing AA (like I did, since it seemed rather uninspired and poorly supported on best), then just do this:
```

sudo rm -r /usr/local/games/armyops
sudo rm /usr/local/bin/armyops
rm ~/.armyops

```
And this will remove the game from your system.
*NOTE: Be very careful with those **rm**commands. Use TAB autocompletion * to be sure you have the correct file or directory before you confirm by hitting enter.
Remember, files deleted from the terminal are banished for good! They do not go to the trash for easy retrieval.
There is little to fear if you run the commands as written. It also helps to make a not of where these source code apps install their wares.
Most of the time with linux games, the game will bo to: /usr/local/games/
And the executable will go to /usr/local/bin.
There are exceptions to this though. Just watch the installer as the game installs, or consult their documentation if their is any.
Write back if you need more help.
All in all, this game is rather disappointing for the linux enthusiast.

Oh, and don't use Wine if you can avoid it. There are many linux games, like the ones I mentioned in my last post, plus many more besides, that work *really, really* well in linux. If you need more help with this, then ask away to find the BEST!!!!! linux games.
Many of the ones I have menrioned

---

### Post by marl30 on 2010-12-20
> **tommcd said:**
> First please understand that this is not a *linux* problem. It is the AA developers lack of sufficient support for linux that is the problem. Games that are well supperted on linux like Nexuiz, Sauerbraten, World of Padman, Doom3, Quake4, Alien Arena, Cold War, etc, etc, work about as well on linux as they do on  Windows.

If you want to have a go at starting the game again, just rename the *.armyops* directory in your home directory to *.armyops.bak*. Then restart the game. This will create a new pristine *.armyops* directory in your home directory with the default settings that should allow you to launch the game again. 
You may also want to try running *gstreamer-properties* in the terminal and set everything to alsa, so as to remove pulseaudio from the picture. Note that this will not remove pulseaudio. It will just set all (or most anyway) of your sound apps to alsa, where they should be!!!
 Or better yet, remove  pulseaudio by removing  **pulseaudio** and **gstreamer0.10-pulseaudio** with apt-get or synaptic. Then run 
**gstreamer-properties** and set everything to alsa.

If you are hell bent on removing AA (like I did, since it seemed rather uninspired and poorly supported on best), then just do this:
```

sudo rm -r /usr/local/games/armyops
sudo rm /usr/local/bin/armyops
rm ~/.armyops

```And this will remove the game from your system.
*NOTE: Be very careful with those **rm**commands. Use TAB autocompletion * to be sure you have the correct file or directory before you confirm by hitting enter.
Remember, files deleted from the terminal are banished for good! They do not go to the trash for easy retrieval.
There is little to fear if you run the commands as written. It also helps to make a not of where these source code apps install their wares.
Most of the time with linux games, the game will bo to: /usr/local/games/
And the executable will go to /usr/local/bin.
There are exceptions to this though. Just watch the installer as the game installs, or consult their documentation if their is any.
Write back if you need more help.
All in all, this game is rather disappointing for the linux enthusiast.

Oh, and don't use Wine if you can avoid it. There are many linux games, like the ones I mentioned in my last post, plus many more besides, that work *really, really* well in linux. If you need more help with this, then ask away to find the BEST!!!!! linux games.
Many of the ones I have menrioned

Hey, thanks a lot for your help. I went ahead and deleted it with the command you provided. I didn't want to mess around with the sound since I use Jackd with some of the Ubuntu Studio softwares, though the sound was already set to alsa.  As for Linux games, I'll be heading over Debgames when I get the chance to see what else they have over there. I got Urban Terror from there a few weeks ago, and it is my favourite Linux game so far. Love it! I'll also check out those you mentioned. 

As for Wine... I'm one of those who can't ditch certain Windows software and games just yet due to learning MS Office Applications at school. I need Wine to run them. I also need it to play my favourite game, Fifa 08. I also play San Andreas online a lot. They both work perfectly in Wine. I rather use Wine than dual boot. Wine has even limit how often I need to use Virtual Box.   

Thanks again. :)

---

### Post by Jack Brown on 2011-01-26
Had installed AA and works perfectly on ubuntu 10.04.  But it's been quite some time that im not sure what the detailed steps are.

something close to:

used the armyops250linux run file, (filefront or other links on americas army site)

?then libstdc++5 (edit: available in repository)

pbsetup for linux from evenbalance.com (punkbuster anti cheat)

no need for wine.

still a great game, it has aged well :)  There's still several servers out there.  at least 2 that are active.  others have no people but are up.

and don't forget Tremulous on your list of first person shooters, quite an experience.

(2nd edit, remembering) shortcut might not appear in applications, but i think you can find it when you right click on Applications in the panel and click 'edit menu'...   it should be in the 'Others' section.

---

### Post by marl30 on 2011-01-26
> **Jack Brown said:**
> Had installed AA and works perfectly on ubuntu 10.04.  But it's been quite some time that im not sure what the detailed steps are.

something close to:

used the armyops250linux run file, (filefront or other links on americas army site)

?then libstdc++5 (edit: available in repository)

pbsetup for linux from evenbalance.com (punkbuster anti cheat)

no need for wine.

still a great game, it has aged well :)  There's still several servers out there.  at least 2 that are active.  others have no people but are up.

and don't forget Tremulous on your list of first person shooters, quite an experience.

(2nd edit, remembering) shortcut might not appear in applications, but i think you can find it when you right click on Applications in the panel and click 'edit menu'...   it should be in the 'Others' section.

I doubt I'll ever attempt to install that game again any time soon. For now I'll continue to enjoy Urban Terror. 

Tremulous seems to only be in 32 bit, I'm running 64 bit.  But thanks for the response.

---

### Post by 0N3 on 2011-01-26
Run this in a terminal see if it gives you sound during play

padsp /usr/local/games/armyops/armyops

It should create a menu entry in your menu using it so you will have only to press a button to get it running with sound.

---

### Post by dudetime on 2011-01-28
America's Army 2 is a great game but just try this 
[http://aa25assist.sourceforge.net/](http://aa25assist.sourceforge.net/)

---

### Post by buttrunks101 on 2011-02-10
[http://aa25assist.sourceforge.net/download.php](http://aa25assist.sourceforge.net/download.php)
i just installed today with this but it seems that not many servers are up. anyone else play or have more servers? or play another game?... i am only 31 honor from 2nd account but dont want to lose it lol.

---

### Post by marl30 on 2011-03-03
> **buttrunks101 said:**
> [http://aa25assist.sourceforge.net/download.php](http://aa25assist.sourceforge.net/download.php)
i just installed today with this but it seems that not many servers are up. anyone else play or have more servers? or play another game?... i am only 31 honor from 2nd account but dont want to lose it lol.

If you want to play a real competitive, great online first person shooter, go for Urban Terror. Hit me up if you're ready for a challenge. I'll own anyone on the servers I like to play on, which is mostly capture the flag. :D

---

