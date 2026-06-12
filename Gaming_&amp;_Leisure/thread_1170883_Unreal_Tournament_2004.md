---
title: "Unreal Tournament 2004"
date: 2009-05-26
forum: Gaming &amp; Leisure
---

### Post by Jguy on 2009-05-26
So I've been able to get to where it's installing, and it tells me to 'mount the Unreal Tournament 2004 CDROM', and I'm running the DVDROM edition. The thing couldn't get any more mounted than it already is. Any suggestions?

---

### Post by racerraul on 2009-05-26
That was funny...

Can you elaborate a bit?
There is an installer file on the DVD to install it on Linux, did you run that and are getting that error?

Once you put in the cd it should have auto mounted... you should be able to change to that directory and run the linux-install.sh file from a terminal window...

---

### Post by CharmyBee on 2009-05-26
The problem with the linux install script for ut2004 is that it's for the multi-CD version that has like 10 discs to go through. It's not compatible with the DVD version nor is it even included in it.

The only alternative I can think of is trying to copy the folders manually then making the 'cdkey'/'ut2004key' file or so (don't remember the name) in the System folder with your CD-KEY to start. I never tried this method myself though so I can not guarantee success.

---

### Post by racerraul on 2009-05-27
Hope this help... 
32bit
[http://gwos.org/doku.php/guides:32bit:ut2004dvd?s](http://gwos.org/doku.php/guides:32bit:ut2004dvd?s)[]=unreal

64bit
[http://gwos.org/doku.php/guides:64bit:ut2004?s](http://gwos.org/doku.php/guides:64bit:ut2004?s)[]=unreal

I am pretty sure I used the 64bit instructions there and I have the DVD edition.

---

### Post by simeon87 on 2009-05-27
> **CharmyBee said:**
> The problem with the linux install script for ut2004 is that it's for the multi-CD version that has like 10 discs to go through. It's not compatible with the DVD version nor is it even included in it.

Actually, it is. I have the DVD version and I installed it on Linux using that script. I have the SE version though.

---

### Post by caravel on 2009-05-27
I've always done it this way: [http://utforums.epicgames.com/showthread.php?t=558146](http://utforums.epicgames.com/showthread.php?t=558146)

Though I do have the Anthology version.  The easiest way to install it is to copy the directories over, run the 3369 linux patch and then manually create the CDkey file and install any dependencies.  You may have some trouble with permissions.  I think I had to chown the whole UT2004 directory in order to get it working.  Obviously don't run the game as root.

---

### Post by Jguy on 2009-05-27
I apologize for the lack of information. Inserted the DVD, it auto-mounted to /media/UT2004_DVD. Opened up a terminal, typed cd /media/UT2004_DVD && sudo sh linux-installer.sh and the installer ran without a hitch. Entered the CD Key and I get to the error described above. I did notice that there were seperate folders for each CD should I have had that version, I will try the suggestion above. The link provided by racerraul was tried after I couldn't get it to work the first time through. (I came up with the same error, and found that tutorial thinking I had missed a step or something). Even by following that step by step, it still gave me the same error. Yes, libstdc is installed and up-to-date.


Thanks all.

---

### Post by Flash__Gordon on 2010-01-09
Did you ever get this to work? I am having the same issues. I have the DVD It has the installer on disc. I can go through the installation to the point were it asks to mount cd2. Very freak'n frustrating!

---

### Post by Perfect Storm on 2010-01-09
You need to use a specific version libstdc. libstdc++5; [http://ubuntuforums.org/showthread.php?t=1243005](http://ubuntuforums.org/showthread.php?t=1243005) if you're using 9.10

---

### Post by Flash__Gordon on 2010-01-09
> **Artificial Intelligence said:**
> You need to use a specific version libstdc. libstdc++5; [http://ubuntuforums.org/showthread.php?t=1243005](http://ubuntuforums.org/showthread.php?t=1243005) if you're using 9.10

I don't think this applies to the installer of DVD asking for play [COLOR="Magenta"]CD[/COLOR] but thanks for the link anyway. I am running 9.04 still at this time. I am waiting until 10.04.

just for the record I do have the most recent libstdc++5

---

### Post by Flash__Gordon on 2010-01-11
Ok here is what I ended up doing after trying everything listed on every other web site and nothing worked. 

 I created an .iso of the DVD and mounted it on my desktop with gmountiso.
then I copied the "linux-installer.sh" from the DVD to my desktop. Then in terminal 
cd Desktop
sudo sh linux-installer.sh

after entering pw it will begin the installation. just use the default locations for installation. (ok, ok, etc.)

After game is installed it asks if you want to start game. Go ahead and do this and set screen settings and such from the settings menu. Then test the game. Exit game (I know it is hard to stop)

Now download UT2004 megapack script. Can be downloaded from this link
[http://www.liflg.org/?what=dl&catid=6&gameid=17&filename=ut2004.megapack-english-3.run](http://www.liflg.org/?what=dl&catid=6&gameid=17&filename=ut2004.megapack-english-3.run)

copy (or download) it to your Desktop. In terminal enter:
cd Desktop
sudo sh ut2004.megapack-english-3.run

after entering your root pw it will begin to install. Then close when finished. 

It may not have placed shortcuts in your applications menu (mine didn't even though I said "yes" to this) If not just go to 'system' 'preferences' and 'main menu'. 
click on 'games' and then select "new item"

Where it says "command" type in /usr/local/games/ut2004/ut2004
(if you did not install to the default directory then you will have to change the above accordingly) Under "name" give it whatever name you want. I put UT2004. close the windows and go to Applications menu and then under games you should now see the shortcut you just made. 

If the game does not start with the shortcut above open Synaptic and in the search type in libstdc++5 and make sure you have it installed. (green square)

Enjoy (you don't need the disc in to play the game)

Flash_Gordon

---

