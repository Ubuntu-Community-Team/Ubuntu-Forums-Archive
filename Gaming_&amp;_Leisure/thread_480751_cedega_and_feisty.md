---
title: "cedega and feisty"
date: 2007-06-21
forum: Gaming &amp; Leisure
---

### Post by myname on 2007-06-21
Hello all,

I just signed up to cedega for 3 months to give it a shot, and so far, my luck isn't that great. I installed it, and to be honest, the interface is quite confusing.  I've used wine in the past, but wanted to give cedega a try based on some reviews.

I grabbed the latest file (version 6.xx) from transgamings website, and installed it on Ubuntu Feisty.  I also noticed that it recommended specific python files.  With a standard install of Ubunutu do I need to do this?

When I tried to install Enemy Territory: Quake Wars, I get the following:

Open a terminal and type in the following:

> 
~/download/games/etqw$ cedega ETQuakeWarsBetaSetup.exe
/usr/lib/transgaming_cedega/gddb.py:24: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
  import gddb_parser
~/.cedega/.winex_ver/winex-6.0.2/winex/bin/wine: can't exec 'ETQuakeWarsBetaSetup.exe': error=21


any ideas?

--kevin

---

### Post by myname on 2007-06-22
Been trying to solve this, and it appears that I need to disable exec-shield.  Does Feisty have exec-shield enabled?

--kevin

---

### Post by hikaricore on 2007-06-23
I'm not really sure, I do know that there have been Python issues in Cedega for many users since Feisty
went stable release.  I've seen several threads about this but haven't been able to locate any with a resolution.

Just thought I'd chime in, sorry I couldn't be of more assistance.

On another note, I thought there was to be a linux client for QuakeWars?  

[http://linux.strangegamer.com/index.php?title=Enemy_Territory:_Quake_Wars](http://linux.strangegamer.com/index.php?title=Enemy_Territory:_Quake_Wars)

---

### Post by myname on 2007-06-23
Appreciate the input.  I too thought there would be a native linux client, and also could not find a resolution for the python errors.

However, as a update, I unzipped the .exe file to a directory, then ran the setup within that, I get further, but not much.

In the terminal, after unzipping the directory, I execute the setup program:

~/temp$ cedega Setup.exe
/usr/lib/transgaming_cedega/gddb.py:24: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
import gddb_parser
Created not existing system directory 'C:\Application Data'
Created not existing system directory 'C:\WINDOWS\Favorites'
Created not existing system directory 'C:\WINDOWS\NetHood'
Created not existing system directory 'C:\WINDOWS\PrintHood'
Created not existing system directory 'C:\WINDOWS\Recent'
Created not existing system directory 'C:\WINDOWS\SendTo'
Created not existing system directory 'C:\WINDOWS\ShellNew'
Created not existing system directory 'C:\Documents and Settings\All Users\Application Data'
Created not existing system directory 'C:\Local Settings\Application Data'
Created not existing system directory 'C:\My Documents\My Pictures'
Created not existing system directory 'C:\WINDOWS\Start Menu\Programs\Administrative Tools'
Created not existing system directory 'C:\WINDOWS\Start Menu\Programs\Administrative Tools'
kevinp@dugr:~/temp$ cedega Setup.exe
/usr/lib/transgaming_cedega/gddb.py:24: RuntimeWarning: Python C API version mismatch for module gddb_parser: This Python has API version 1013, module gddb_parser has version 1012.
import gddb_parser
Created not existing system directory 'C:\WINDOWS\Start Menu\Programs\Administrative Tools'

It starts to install, then I get a popup that says:

1628 Failed to Complete Windows Installation

getting closer.... so close I can almost taste it.

Any ideas? 

--Kevin

---

### Post by hikaricore on 2007-06-23
I think it may be better to wait a week or so until they release the linux version of the beta client.  (just a guess)

This game is _JUST_ being released.  There's no guarantee that it will even work with WINE or Cedega.
So my suggestion remains unless you know of people already running it like this, it may not even work.
Not all ***dows software runs under WINE/WINEX you should be aware of this, check cedega's supported game
list and the [wine application database]("http://appdb.winehq.org") for more info on what runs and how well it runs.

Aside from that, dealing with your main Cedega issue is probably best suited for their support, as we generally recommend WINE around these parts.  ^_^

---

### Post by UK-Wobbie on 2007-06-23
> **myname said:**
> Hello all,

I just signed up to cedega for 3 months to give it a shot, and so far, my luck isn't that great. I installed it, and to be honest, the interface is quite confusing.  I've used wine in the past, but wanted to give cedega a try based on some reviews.

I grabbed the latest file (version 6.xx) from transgamings website, and installed it on Ubuntu Feisty.  I also noticed that it recommended specific python files.  With a standard install of Ubunutu do I need to do this?

When I tried to install Enemy Territory: Quake Wars, I get the following:

Open a terminal and type in the following:



any ideas?

--kevin




I been useing wine and i got to say it is better then useing Cedega! 
My games like doom3 or American McGeen's Alice do not install in Cedega! Doom3 do not load and McGeen's Alice do not load in the setup :(
I no wine can not play doom3 or American McGeen's Alice! But alot of games what i got do not work in Cedega and work in wine.

I say wine is a lot better then Cedega, If i am you i be better keeping to wine :p

---

### Post by myname on 2007-06-23
Thanx for the info.  Wasn't really looking for a resolution for ETQW yet, as it is just beta, and not released, just trying to see if anyone has see this behavior in another game.

Do you guys think wine is better than cedega?  better as in better support?  I've read up here how people prefer open source (free, ie. wine) versus non; crossover office and cedega.  The best would be if developers would do native ports to linux, especially since linux has gotten more mainstream press recently.  Maybe the powers to be with the big distros could approach game developers to port some good games to linux.

--Kevin

---

