---
title: "Difficulty getting games to install"
date: 2010-04-18
forum: Gaming &amp; Leisure
---

### Post by keljaden on 2010-04-18
I am well aware that AI (and many others) have written a plethora of guides on how to install the opensource linux games.  For me though, I do not want to have to follow a 3 page guide full of terminal commands just to play a mid grade FPS game.  Right now I am going back to my Linux/Win7 dual boot up because I am upset at how much work it takes to get a simple game to install.  For example; I would go to ubuntu's software manager and install open arena.  I try to go online, no one is there.  Turns out there is a MASSIVE update on for the game on their website.  Its not even just a bunch of nice packaged .deb files.  I am not sure why each game doesn't have its own repo that I can just add so it will stay up to date.  Another problem I have had is with regnum online; no matter what I click to download I have only every received the download link to a 64 or 32 bit windows installer.  I am not sure who I need to contact about this, but for me at least, I do not feel comfortable using an OS that requires so much work for just a simple game.
As far as WINE and Crossover, I can post a problem and it will have not a single reply for weeks.  Without any reasonable amount of support I am just going to be gaming in Windows for the moment. and getdeb site doesn't seem to agree with my Linux Mint 8 64 bit install either.
I will continue to use linux as an OS on my laptop as it can suite my needs as an OS for school.  But I would really like some work to be done as far as getting a game to run without having to follow a complex guide.

(and playdeb doesn't seem to work with KDE very well which is RIDICULOUS because gnome is ugly)

---

### Post by HHx66 on 2010-04-18
PlayDeb works fine on my x64 Kubuntu (Though I have Synaptic Installed over the watered-down "package manager" Kubuntu comes with by default). The basic fact is, as of right now, if I were looking for serious gaming I'd either dual-boot with Windows for games or buy a console, Linux is far behind as far as gaming goes, but still not too bad for the occasional game, but you're not going to get anywhere near the ease of Windows for gaming at this point.

I do have one suggestion though, have you tried djl? [http://en.djl-linux.org/](http://en.djl-linux.org/) - it's a Linux game manager, it auto downloads and installs the games from repo's.

---

### Post by keljaden on 2010-04-18
Thank you for the fast reply.
I will give it a go.  I am not as upset at the quality of the games, just how difficult they are to install.  Like I can go to synaptic and grab it, but its normally an old outdated version.  And I am afraid of kubuntu...it gave 9.10 a try and crashed left and right, thats why I was using Linux Mint 8 x64 KDE.
I am still a big fan of Ubuntu and Mint and think they are wonderful OS's but I hope after 10.04, it would be nice if people started focusing on making a few more solid games.  Just like ONE really good, FPS, RTS, and a RPG (like fable) that are free and easy to install.  Personally I feel that would bring a lot of gamers over.  As long as I have one game for each of those three genre's I'd be set.  (and yes I know UT is for linux, but they need to make a good RTS like starcraft, and a good RPG).
Are there any good single player RPG's for linux?

---

### Post by HHx66 on 2010-04-19
Not sure about that, I know theres a lot of diablo-esque RPG's on Linux, but I'm not much of an RPG fan myself, I spend a lot of my linux gaming time on emulators to be honest.

---

### Post by myromance123 on 2010-04-19
Hmmm, regarding Regnum Online I find it very hard to believe you've actually checked the site in the past year at least.

 Go here:[http://www.regnumonline.com.ar/index.php?sec=6&l=1]("http://www.regnumonline.com.ar/index.php?sec=6&l=1")
Still don't see those links to a Linux 32-bit and 64 bit download? What about that large download link in the middle of the page?
 Check the image attached below if you still can't see it.

The file is a .BIN. Its a standard installer and its *for* Linux.

Also, Playdeb is not at fault, Kpackagekit is. I suggest a change to Synaptic.

There is a native client for Neverwinter Nights if you're still unsatisfied. Or if you've ever played Dota, we have a HoN client for Linux. Don't forget to check out the Penumbra series. These are NOT cheap, low quality games, so do check them out.

---

### Post by keljaden on 2010-04-19
@myromance123, yes I went there just before then.  I click to download the linux one and for reasons I cannot fathom the .exe downloads.  I am specifically clicking the linux 64 installer (I have tried on multiple machines of different distributions).

I liked the manager, though, It doesn't download the lastest versions (or ones with players on it).  I have open arena a go, went straight to multi player and no servers were found.  I am really at a loss here.

and with my dual boot I just put ubuntu 9.10 on and I remember another reason I hated gnome...It has the worst mouse options ever.  I can't ever get the speed slow enough while keep my DPI at 2000.

---

### Post by tommcd on 2010-04-20
For many games like: Nexuiz, Sauerbraten, World of Padman, and Open Arena, you can just download the game directly from the developer's site. This assures that you are always using the latest version. Also, Nexuiz, Sauerbraten, Blood Frontier, and Open Arena do not even have to be installed. You just download them, unzip or extract them, then cd into the game's directory and run their executable right from the terminal. This involves running only one command, not "a 3 page guide full of terminal commands" to play the game. You can also easily place a launcher for the game's executable on your desktop if you wish. Alternatively, you can move the game's directory to /usr/local/games and have it available for all users on the system. Here is how to do that for Open Arena:
[http://openarena.wikia.com/wiki/LinuxInstall](http://openarena.wikia.com/wiki/LinuxInstall)
(See the section: "Other linux distributions / alternative installation").
For other games, like World of Padman for example, you just run the game's install script and it installs to /usr/local/games (or wherever you may want it. I prefer /usr/local/games, so I can keep these games separate from all the Ubuntu apps in /usr). You then just run the command to start the game from the terminal. Again, this involves only one command.
Removing these games only involves deleting the game's directory from /usr/local/games. Some games also place a symlink to the games executable in /usr/bin or /usr/local/bin.
When you run some of these games you may get an error that you are missing some lib file or something like that. If that happens you can just install the required dependency for the game from the Ubuntu repos.
For what it is worth, I don't think I have ever encountered a game that required 3 pages of terminal commands to install.

---

### Post by keljaden on 2010-04-21
thanks tommcd I will give it a go.

---

