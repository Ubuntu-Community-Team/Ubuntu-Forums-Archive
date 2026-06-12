---
title: "two problems running games using wine"
date: 2007-08-08
forum: Gaming &amp; Leisure
---

### Post by animeanonymous on 2007-08-08
Well, I'm a really new user and I am trying to figure out the ins and outs of wine in the context of gaming.  

I run the setup.exe file off of a cd using the "wine setup.exe" terminal command.  I go through the installation just fine.  It should create a new  installation directory in the drive_c virtual c drive.  But it does not.  We can't find the installation.  I was able to open the game(Blue Shift) once, but I can't find the installation.  I've tried nautilus and the terminal but I can't find it.  I've been able to install and run Dune 2000 and it hasn't given me this problem.  However, it did the same thing when I tried to run Oni.

Also, when I ran blue shift for the first time, I tried to start a new game and my computer froze.  I don't think it's a problem with wine not being able to handle it.  

Any ideas to rectify my two situations?

---

### Post by Montre on 2007-08-08
this probably won't help since I'm new to this whole thing as well. But I noticed when I installed WoW to the default location where it then goes through wine. I noticed that instead of it being 
~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/

it went into
~/.wine/drive_c/Program\ Files/Program\ Files/World\ of\ Warcraft/

So maybe your blueshift added an addition program file entry, so CDing into it is impossible, try to CD one directory at a time and then use "dir" to see if theres any extra folders.

Remember you won't be able to see the wine folder through a GUI because of the . infront of it, you'll have to go type the folder name into your addy bar

As for blue shift, it worked the second time? So I guess thats all good.

---

### Post by Diabolis on 2007-08-08
go to your home folder and press:

```
ctrl+h
```

that makes visible all the hidden directories. Wine directory is hidden, thats why you usually don't see it. Once you get there you can just look around for the files you need.

---

### Post by animeanonymous on 2007-08-08
Well, I just realized that there is a wine folder in my applications menu and that has access points for the games.  So they're on my hard drive somewhere.  Problem solved I suppose.

Now why do you think blue shift just crashes on me?

---

### Post by cogadh on 2007-08-08
> **animeanonymous said:**
> Now why do you think blue shift just crashes on me?
Wine is beta software, crashes are to be expected.

That being said, what version of Wine are you using? Also, try running the game from the terminal and see if any error messages pop up that explain the crash:
```
cd $HOME/.wine/drive_c/Program\ Files/*Blue Shift install directory*
wine game.exe
```
Obviously, adjust the cd command to match the actual install directory and change the "game.exe" to the correct executable name.

---

### Post by hikaricore on 2007-08-08
You may also want to check for your game here: [http://appdb.winehq.org/](http://appdb.winehq.org/)

To see if it's listed and advice other may have given on running it via WINE.

---

