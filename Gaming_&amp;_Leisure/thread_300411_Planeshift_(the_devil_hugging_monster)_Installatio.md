---
title: "Planeshift (the devil hugging monster) Installation &amp; Uninstillation issues"
date: 2006-11-15
forum: Gaming &amp; Leisure
---

### Post by TommyMann on 2006-11-15
I heard about this game planeshift, and since moving to linux I was a little depressed about losing all my games, so I decided to give it a shot.

This has been a nightmare. First off their website doesn't have the bin on it up ever. I finally got the Linux torrent to download, and what do I get? a .exe file. Sweet! Not. So I search all around torrentville until I come upon a .bin file, it's for 3.015 instead of 3.016 and I say what the hell, I'll just run the updater.

I finally get it on my computer to install it, and I do, and everything is looking fine until I click on the menu to launch it. Crap, my menus don't work I think to myself.

I go to open up the folder to launch it; lo and behold it's locked. I try to go into konsole and use what I think sounds like a good name for the launcher, psupdate and psclient. Nothing.

So I spend a little time chmod -r 755ing the directory. I finally get it to unlock. I click on the one that entitled "up". I get the same reaction as from my menu. A half second of bouncing gear and then nothing. Then I try clicking the psc. I infer that's the client. I get the same reaction.

I open up my buddy the terminal again, and lo and behold I get an error. It needs libXaw.so.8, fine apt-get install libXaw.so.8, the terminal tells me that we ain't got no libXaws.

So I say, you're too much trouble. I fire up the uninstaller. It goes through the motions tells me it's complete, and yet all the damnable files still linger mocking me. Ok, then, I open up the unscript.sh, I type sudo and paste the code.

Permission Denied.

First and foremost, can anyone tell me how to get this devil hugging monster off my computer?

Then can anyone suggest some good linux games that have at least a little more ease of install and what what.

---

### Post by MaximB on 2006-11-15
I didn't get it...you installed the windows version or the Linux ?

I just downloaded the Linux .bin from the site [www.planeshift.it](www.planeshift.it)
made it exectable and run it in the Terminal...no problems at all
works great.

---

