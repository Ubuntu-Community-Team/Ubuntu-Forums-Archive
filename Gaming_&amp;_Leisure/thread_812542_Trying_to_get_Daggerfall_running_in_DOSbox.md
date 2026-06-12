---
title: "Trying to get Daggerfall running in DOSbox"
date: 2008-05-30
forum: Gaming &amp; Leisure
---

### Post by n0th1n on 2008-05-30
Can anyone help me get Daggerfall running in DOSbox? I've been looking around for a while and haven't found anything to get it working. I installed the game, I even did a Huge install to my dosgames folder mounted as C, and set the sound, and everything seemed fine. 

When I try running the game by running "DAGGER" like it says, I get an error saying it can't find the right CD and to try inserting the correct CD again. The CD is in there, and the cd is mounted as a cdrom, which is what I installed the game from in the first place, but its giving me that error and I don't know why or what to do about it.

Anyone know how to get this running or what the problem might be?

---

### Post by OpposingForce on 2008-05-30
I just got Daggerfall running in DOSbox last night after fixing an issue with a black screen.

You can just bypass the CD check since you have the big install.  It wouldn't detect my CD either, so I just did this fix. I think you might need the v213 patch for this, so get that if you haven't already.  Now just go to your Z.CFG for dosbox and look at these lines, your "pathcd" should be set to the same as your "path".  something like this (mines in the wine directory b/c I used wine to run the Windows XP installer for the game)

```

path c:\dagger\arena2\
pathcd c:\dagger\arena2\

```

Then make a empty file, name it dag.bat (NOT dagger.bat) and put it in the Dagger main directory.

put this in it

```

@echo off
set dos4gvm=@dagger.vmc
fall.exe z.cfg

```

I googled, and some users get a black screen after doing the no cd fix.  To fix it, check your Dagger.bat file, make sure it looks something like this

```

mount c c:\
c:
cd dagger
dag.bat

```

Again, change the directories to match yours.  The black screen is a result of the game not finding the files because C:/ is not mounted to the right drive.  I had to mount to my actual C:/ drive, NOT the C:/Dagger.  You mount it as the C:/ drive, then change directory to C:/Dagger and the black screen disappeared for me.

If you want to make a launcher for the game, try this 

```
dosbox -c "mount C: /home/cory/.wine/drive_c" -c "c:" -c "cd dagger" -c "dag.bat"
```

again, change your paths as necessary

---

### Post by n0th1n on 2008-05-31
Thanks, its running now.

I hadn't tried running under wine, just ran in DOSbox alone. Has it worked well for you in wine? I've now been having the problem of the game crashing alot, but I've seen elsewhere that its typical for Daggerfall to crash, but it really is doing it alot (every 5 minutes, sometimes less) And this is just in the opening dungeon. 

Have you or anyone else had this same problem and is there a way to make it run better, or is it something everyone just has to live with?

---

### Post by OpposingForce on 2008-05-31
Glad to hear you got it working, but I just have the game files installed in the wine directory (because I ran the windows xp installer through wine), I'm running it through the linux client of Dosbox, so the game is running natively, but just mounted to the wine directory where the files are located.  And I actually haven't even crashed once yet *knocks on wood*.  Did you install the v213 patch? Definitely give the patch a try if you haven't because it fixes **loads** of bugs from the 1.0 version of the game.

[http://www.fileplanet.com/51562/50000/fileinfo/Daggerfall-v2.13-Patch](http://www.fileplanet.com/51562/50000/fileinfo/Daggerfall-v2.13-Patch)

---

### Post by lawentzel on 2009-08-13
Thanks for the help.  I loved this game, now I am able to play it again. Was having the same problem with the game not recognizing the CDRom.  It almost appeared as if it wasn't recognizing the label.  I say this because, when you typically type DIR it will show you the name of the drive, if there is one at the time of the directory.  Doesn't matter... Game is working.  Thanks.

---

### Post by loyd2323 on 2009-08-26
> Dagger.bat file do you mean the file that you just made?

---

### Post by loyd2323 on 2009-08-26
nevermind found the solution somewhere else

[http://www.bethsoft.com/bgsforums/index.php?showtopic=860924&hl=black](http://www.bethsoft.com/bgsforums/index.php?showtopic=860924&hl=black)

---

### Post by Crunchy the Headcrab on 2009-08-26
I love the Elder Scrolls games.  Morrowind is still my favorite.  I find Daggerfall unplayable due to the archaic controls.  That's the problem I have with most retro games.  I can deal with old school graphics and sound but controls kill it for me.

---

