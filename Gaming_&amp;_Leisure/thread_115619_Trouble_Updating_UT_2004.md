---
title: "Trouble Updating UT 2004"
date: 2006-01-10
forum: Gaming &amp; Leisure
---

### Post by Gaming_Junkie on 2006-01-10
I am at a loss on how to update UT 2004.  All the files I've seen are in .tar.bz2 format, and I have no idea how to install them into the game.  I've tried simply extracting and overwriting them into the main directories, but when I loaded up the game afterward it didn't recognize the changes.

Has anyone successfully updated UT 2004?  Could someone please tell me step by step how they did it?

---

### Post by Curlydave on 2006-01-10
I'd like to know this as well. I've done it, but by doing it manually; Opening up a root browser and copying the contents of each folder. That's the only way I've found to work.

Whenever I try to extract it automatically, it goes through the process then at the end says "errors, can't overwrite this folder" for all of the folders, and nothing actually gets extracted. :(

---

### Post by Zeroedout on 2006-01-11
good lord, how do you people not know about loki installers for linux gamers! [http://www.liflg.org/](http://www.liflg.org/) This site will save you a BIG headache!!!!! [http://www.liflg.org/?catid=6&gameid=17](http://www.liflg.org/?catid=6&gameid=17) for the ut2004 section. Good luck, and MAKE SURE YOU UPDATE IN THE RIGHT ORDER! If you do not update in the right order, it's a minor headache :)

---

### Post by Curlydave on 2006-01-11
[QUOTE=Zeroedout]good lord, how do you people not know about loki installers for linux gamers! [http://www.liflg.org/](http://www.liflg.org/) This site will save you a BIG headache!!!!! [http://www.liflg.org/?catid=6&gameid=17](http://www.liflg.org/?catid=6&gameid=17) for the ut2004 section. Good luck, and MAKE SURE YOU UPDATE IN THE RIGHT ORDER! If you do not update in the right order, it's a minor headache :)[/QUOTE]

The order doesn't matter anymore. The patch and ECE have been made obsolete by the Megapack, which contains both as well as new content.

---

### Post by Divan Santana on 2006-01-11
how do you play unreal 2004 on linux??

Do you need a special linux version? Windows version? Where do I start? :D

---

### Post by Brynster on 2006-01-11
there is a native installer on the disc's (I think its on the last disc on the CD version)

---

### Post by Gaming_Junkie on 2006-01-12
I already tried getting the files from Loki, but the links were broken.  

I am going to try updating it manually, first with the ECE bonus pack, and then with the mega pack.  This is what BeyondUnreal recommended.

---

### Post by Gaming_Junkie on 2006-01-12
[QUOTE=Curlydave]I'd like to know this as well. I've done it, but by doing it manually; Opening up a root browser and copying the contents of each folder. That's the only way I've found to work.

Whenever I try to extract it automatically, it goes through the process then at the end says "errors, can't overwrite this folder" for all of the folders, and nothing actually gets extracted. :([/QUOTE]

It worked!  Thanks, Curlydave.

---

### Post by MacV on 2006-01-12
[QUOTE=Gaming_Junkie]I already tried getting the files from Loki, but the links were broken.  

I am going to try updating it manually, first with the ECE bonus pack, and then with the mega pack.  This is what BeyondUnreal recommended.[/QUOTE]

ACctually, the links are not broken. Well, kinda. You have to download the torrent links and get them that way, the direct download links are what's broken. I'm downloading some of the mods now actually.

---

### Post by professor_chaos on 2006-01-13
there a script at [http://www.linux-gamers.net/modules/wfsection/article.php?page=1&articleid=40](http://www.linux-gamers.net/modules/wfsection/article.php?page=1&articleid=40)
that will make the patching painless. Saved me lots of time with the ~4 patches I've installed.

---

### Post by Sp@z on 2006-01-13
I maunaully updated mine by downloading the patches from unrealadmin.org and then extracted them to the desktop and copied them over into the proper folders in my /home/bill/ut2004 folder. I wish I had known about the script though, owell I am sure kubuntu will crash soon and I will have to reinstall it and I will try the script. BTW the linux installer is on the FIRST disk on the CD version..........

---

### Post by handy on 2006-01-13
You will have the best game install experience if you copy the 

**linux-installer.sh** file onto your desktop & run it from there.

Also when given the option to run the installer in a terminal say no, you will get to see the pretty installer then! :D 

**As far as order, how to, & the like is concerned with the latest patch?**

***_Read on:_***

UT2004 for x86 and amd64 Linux patch 3369.2

3369.2 has a server exploit fixed for both architectures, and compiler optimizations reenabled for amd64 (they got turned off by accident in 3369.1).


UT2004 for x86 and amd64 Linux patch 3369.1

3369.1 is a "hotfix" patch to correct some issues in the 3369 patch.

Changes over stock 3369:

- Linux: Fixed large memory usage.
- x86 Linux: Reenabled Pixomatic renderer ("PixoDrv").
- Mac OS X: game will now run on Mac OS X 10.2.8 ("Jaguar") again.
- Mac OS X: 3D audio now correctly spatializes, other OpenAL fixes.

The Linux version can be applied as usual; it's the 3369 patch with updated binaries. The Mac version requires a 3369 install, so the whole ECE Bonus Pack doesn't need downloading again. There is no Win32 or Win64 3369.1, as these issues were specific to Linux/Mac.


UT2004 for x86 and amd64 Linux patch 3369

Please install the Editors' Choice bonus pack FIRST, and then 3369

Patch 3369 contains several important fixes, but Linux users might be most excited about the availability of render-to-texture support (detailed shadows, motion blur, headlights, the DM-Morpheus scoreboard, etc).

The package contains both the client and dedicated server, and x86 and amd64 binaries. This will only patch the retail version (either the original UT2004 or the Editors' Choice Edition), and not the demo.

To install: download, unpack, and copy the contents of the newly-created "UT2004-Patch" directory over your ut2004 installation, allowing it to overwrite files. That's all.

--icculus.

That should wrap it up... :rolleyes:

---

### Post by handy on 2006-01-13
Using Archive Manager to extract the update into the UT2k4 directory isn't too hard is it?

sudo file-roller

Cheers

---

### Post by nchase on 2006-01-13
WHenever I try to copy the ut2004-patch folder over into the directory the window closes like 25% of the way through. Anyone know why this may be happening?

edit: I have the ECE edition of the game, does this change which patches I should be installing?

---

### Post by Curlydave on 2006-01-14
Question: Can anyone explain the write errors when extracting directly into the directory with fileroller?

Also, in Windows, the Megapack replaces the ECE and patch, so it's all you need. Is that teh same in Linux?

---

### Post by handy on 2006-01-14
I don't get write errors when installing Patches or any other enhancements into the **UT2004** directory.

The info from the patch that I posted earlier today in this thread doesn't answer the overwrite question?

**[EDIT:]**

The Linux version can be applied as usual; it's the 3369 patch with updated binaries. The Mac version requires a 3369 install, **so the whole ECE Bonus Pack doesn't need downloading again**. There is no Win32 or Win64 3369.1, as these issues were specific to Linux/Mac.

---

### Post by Sp@z on 2006-01-15
I used the scripts from loki, but aafter it checks the integrity it tells me to install UT2K4 first..........I did, I installed it to the default folder UT2K4 wanted to use as well. I think that is the prob though............I even put the script in the system folder and still same message............odd.............updating the old fashioned way for now............copy paste. LOL

---

