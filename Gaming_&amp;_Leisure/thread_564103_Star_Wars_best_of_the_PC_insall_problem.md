---
title: "Star Wars best of the PC insall problem"
date: 2007-09-30
forum: Gaming &amp; Leisure
---

### Post by andnobodyslept on 2007-09-30
I just went out and bout star wars the best of the PC, why not, 5 games 40 dollars American, plus I really wanted to play KotOR.

So here is the deal, I go to install the game, which now there are two games on the disk (star wars galaxies and kotor), 
I run```
wine /media/cdrom0/LaunchBOPC1.exe
```

first a box pops up and tells me that wine needs to install an add on...no problem I let wine do its thing. Then a window pops up that I know is supposed to let me choose which game I want to install (tried installing it on my windows partition), except that it is just white with the little, a picture is supposed to be here icon in the upper left.

Using wine 0.9.44 set to windows XP (also tried windows 2000)
P4 3.0 Ghz
Nvidia drivers through the restricted driver menu
and a gig of ram

Any ideas?

---

### Post by Lord Illidan on 2007-09-30
Why don't you try navigating to their specific directories and seeing if there is a setup.exe there?

---

### Post by andnobodyslept on 2007-09-30
I tried that, there were two .exe's in the KOTOR folder
setup.exe got me as far as install shield starting up and having me hit next, then wine said there was a DLL function call crashed and it had to stop
the other LaunchKOTOR.exe just led me to the same white screen.

Don't know if this makes any difference, but I tried going into the empire at war folder and installing that through the setup.exe and there it at least let me enter the key before shutting down...

---

### Post by andnobodyslept on 2007-09-30
I was looking over at the wine site, looks like this is a bug that is affecting all of the best of the pc pack...
[http://appdb.winehq.org/viewbugs.php?bug_id=8722]("http://appdb.winehq.org/viewbugs.php?bug_id=8722")
too bad if you ask me since it's a great deal...well I keep playing around with it for a while, until then, I guess I'll have to hold on to my windows partion...damn I was planning on getting rid of it when gusty came out.

---

### Post by dorath on 2007-09-30
It reallly is a great deal, and some of those games are supposed to run great under WINE too!

The very first thing I check after each new version of WINE is if the Best of the PC games will install.  :-(

If you haven't voted for that bug, please do.  You can do so here: [http://bugs.winehq.org/show_bug.cgi?id=8722](http://bugs.winehq.org/show_bug.cgi?id=8722)

---

### Post by andnobodyslept on 2007-09-30
Just voted, hopefully this will get fix soon. If it's anything I noticed with I didn't let directx control the mouse the installation just froze, didn't even spit out any error messages.

---

### Post by shad0w_walker on 2007-10-01
Have you thought about the old install in windows and then copy the installed files to your Linux drive. Thats why i keep Virtual box around with a a copy of XP loaded on it.

---

### Post by cogadh on 2007-10-01
Virtual Box can't run 3D games effectively, it doesn't have the necessary hardware access.

---

### Post by shad0w_walker on 2007-10-01
Might want to re-read my post. I said I use Virtualbox to install the games, then copy the installed files to my Linux drive.

---

### Post by cogadh on 2007-10-01
Ah, my bad, that makes much more sense. However, many modern games do require certain registry entries that are only written during the install process in order to work correctly. While the copy from a Windows install method will work sometimes, it won't work all the time.

---

### Post by shad0w_walker on 2007-10-01
Thats true, however this is talking about older games so its not as much of a common issue (From my experience), and there are some ways of getting the entries out.

---

### Post by Hooloovooloo on 2007-10-01
Woah! I started playing KoTOR II again yesterday! :D
Couldn't get it to run in Wine though. I tried the latest version, but no luck :/
Had to run it in W*****s.

Sorry i can't help you with your problem btw. :(

---

### Post by andnobodyslept on 2007-10-01
shad0w_walker, I'll have to give your idea a go, worst case I'm back to where I am now, best case I have another game I can play without having to boot into windows...Thanks for idea

---

### Post by andnobodyslept on 2007-10-01
Well cedega was able to find a work around for the problem
[http://cedegawiki.sweetleafstudios.com/wiki/Knights_of_the_Old_Republic]("http://cedegawiki.sweetleafstudios.com/wiki/Knights_of_the_Old_Republic")
I tried their work around with wine, no luck. I guess I could try compiling cedega from the cvs or just subscribing to cedega...but I like a challenge, I'll try compiling it later. Anyone know the latest version of cedega to be released to cvs or from source?

---

### Post by dorath on 2007-10-01
> **shad0w_walker said:**
> Have you thought about the old install in windows and then copy the installed files to your Linux drive.

I believe I'll give this a go.  :-)

---

### Post by dorath on 2007-10-01
Copied over the JK II and KotOR folders from my XP install.

Tried JK II first, no luck.  :-(

Tried KotOR (using swkotor.exe), much better!  The game started up fine and looked to be running great, then I noticed that I couldn't see the mouse.  I can use it to click stuff, just can't see the mouse itself.  Tried launching the game with LaunchKOTOR.exe, didn't work, same as JK II.  Hmm.

By unchecking 'Hardware Mouse' from in swkotor.exe or from in launcher.exe, I was able to get the mouse to appear.  Also, the game ran much smoother without 'use software sound' checked.

Decided to try JK II again.  This time I went into the GameData folder and launched the game using jk2sp.exe, it works!  Wants the CD though.

That's enough for me tonight, Heroes comes on in a bit.  ;-)

---

### Post by andnobodyslept on 2007-10-01
Great update, I'll have to give that a try.. Right now I'm compiling cedegacvs hopefully this might work, if not at least I know that the other trick worked.

---

### Post by andnobodyslept on 2007-10-03
well I gave up on cvscedega and getting it to install with wine. I copied it over from my windows partition, everything seems to be working just fine, except once I choose to run the game, I lose all sound. When I first run the launcher.exe everything seems fine, but when I click play, I lose sound...Any ideas?


EDIT: Used swkotor.exe Now everything seems to work

---

