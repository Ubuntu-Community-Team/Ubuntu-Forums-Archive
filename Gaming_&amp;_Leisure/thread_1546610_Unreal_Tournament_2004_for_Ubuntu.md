---
title: "Unreal Tournament 2004 for Ubuntu"
date: 2010-08-05
forum: Gaming &amp; Leisure
---

### Post by Joseph Schwenker on 2010-08-05
Hey all!  I just found Unreal Tournament 2004 on Newegg, and it says in the requirements that it supports Linux.  However, that's the only place it says.  I did some research, and apparently, this version of the game includes both the Linux and Windows version.  However, I noticed in the comments on this game that the second disc is missing in this version, which is reported to have some videos on it.  I'm worried that the Linux content might be on the second disc.  I can't find this game anywhere else for the $10 price for Linux, but the game has a replace-only policy, so I won't  be able to get a refund if only the Windows version is present.  Can someone confirm that the native Linux version will be present if I buy the game?

[http://www.newegg.com/Product/Product.aspx?Item=N82E16832129122](http://www.newegg.com/Product/Product.aspx?Item=N82E16832129122)

---

### Post by Rustybolts on 2010-08-05
My version of Unreal Tournament which I bought before I had installed Linux contains linux installer on first CD. Even if it doesn't (which I doubt it ) there is  a Linux installer available from this website [http://www.liflg.org/?catid=6&gameid=17](http://www.liflg.org/?catid=6&gameid=17)

---

### Post by Joseph Schwenker on 2010-08-05
Thanks a bunch!  I'll buy it.

---

### Post by Joseph Schwenker on 2010-08-05
I just ordered it.  Can't wait to play it!  I hope it doesn't need the CD in the drive to play.

---

### Post by Rustybolts on 2010-08-05
Once installed cd is not needed

---

### Post by Technophobia on 2010-08-05
You will likely run into the issue where the game asks your for libstdc++5 package. You can find it here

[http://packages.ubuntu.com/en/jaunty/libstdc++5](http://packages.ubuntu.com/en/jaunty/libstdc++5)

---

### Post by Joseph Schwenker on 2010-08-06
Funny, I didn't get that error when I played the demo... wait, oh yeah!  I already installed libstdc++5.so for Grid Wars.  I personally like the Windows version of Grid Wars better; the Linux version uses SDL (can't adjust volume, alt tab, etc) and the music doesn't work.  If only Grid Wars were open source or still being developed...
Sad that all of these games have to use SDL, and that SDL has to be so crappy in Linux.  Who ever heard of a system where you can't turn down the volume while in a game?

---

### Post by slooksterpsv on 2010-08-06
A bit more information, I'm running Lucid 64-bit, and I install UT2004 now the installation was strange on my computer so here's how I had to do it:
1. Copy the install-sh.sh file from Disc 1 onto your desktop
2. Open a Terminal and run the install-sh.sh file you copied from Disc 1 (we're not running it from Disc 1 though).
3. It immediately checks Disc 1 then asks for Disc 2
4. I had problems with mounting the CDs so I had to manually mount them by, lets say Disc 3 won't mount automatically, I believe the first CD is UT2004_1 (we follow that same naming pattern):
```

sudo mkdir /media/UT2004_3
sudo mount /dev/sr0 /media/UT2004_3

```
then click on Retry. After it's finished with CD 3, go into Terminal and type the following to unmount and remove it:
```

sudo umount /media/UT2004_3
sudo rm -R /media/UT2004_3

```

And continue step 4 till it's installed.

Now after it's installed, you have to install the patch first (its on the UT2004 web site), then install the libstdc++5 file.

If you're running the 64-bit version of Ubuntu, you have to do more changes by editing this file:
**/usr/local/games/ut2004/ut2004**
and replace all instances where it says:
**ut2004-bin**
with
**ut2004-bin-linux-amd64**

Next you run ut2004 and voila - I think I may have had another issue, but a quick google search fixed it.

Let me know if you run into any problems.

---

### Post by Joseph Schwenker on 2010-08-10
The game should be here tomorrow or the day after.  I've noticed some things in the demo, though.  The microphone does not work.  I have it properly configured in Sound.  I used [these instructions]("http://icculus.org/~warp/ut2004/") and put the two files into my UT2K4 directory, then created .openalrc with the settings recommended.  I am still unable to use the microphone, or so I think.  I have been unable to test it that well, as I am unable to connect to a lot of the servers.  I  can't connect to listen servers at all (I get a black screen that is either blank, with a line on it, or with a line and an IP address on it), and can't connect to some regular servers, either.  It doesn't matter if they're using the standard demo maps or not, I can't connect to them.  I have gotten by playing on one server that actually has players on it (there was another server listed in deathmatch that I could connect to, but the foreign admin randomly kept kicking me for no reason, so I kept connecting, and he banned me, which I thought was not possible in the demo).  I have forwarded 7777-7778 and the two others ones necessary for hosting listen servers.  Can anyone explain why I can't connect to most of the servers, and also help me get the microphone working?  I hope that these issues will be fixed in the full version, though if I want to play with my friends who don't own the game, I'll need the demo version, and would really like to not have these problems.  Thanks!

---

### Post by handy on 2010-08-10
> **Joseph Schwenker said:**
> I just ordered it.  Can't wait to play it!  I hope it doesn't need the CD in the drive to play.

Depending on the version of the game you buy (I don't know if they produced any with the upgrades or not?) You may have to upgrade the game to become free of the need for the CD. You won't have trouble finding the upgrades & other great expansions on the net.

Have fun it is such a great game. :)

---

### Post by wingnux on 2010-08-10
Too many troubles with outdated libraries but installing (and updating) the windows version via wine works like a charm! 
I installed it yesterday.

---

### Post by Joseph Schwenker on 2010-08-11
Outdated libraries?  I haven't had any problems with the demo yet (other than those ones I mentioned above, which were minor, and affect only the demo).  I already had libstdc++5.so installed (for Grid Wars), and it worked great.  
The Windows version has the extremely annoying issue with dinput.dll.  The mouse isn't warped, and can either be confined or escape from the window.  If you force mouse warping, the mouse can still escape if you move it fast enough, and then you can't use the menus.  Wine also reduces the performance of ANY application running under it, so you're better to use the native version.  The microphone is the only major problem (other than the weird server problem in the demo).
Can anyone figure out how to get the microphone working, or why I can't connect to most of the demo servers, especially listen servers?

---

### Post by handy on 2010-08-11
The updates I refer to come from Epic (or whoever gives themselves credit for creating the game).

You won't have ANY problems using them, the game is better for it. Apart from Epic taking away the need for the CD in the drive in the first of the updates from memory.

---

### Post by Joseph Schwenker on 2010-08-11
> **handy said:**
> The updates I refer to come from Epic (or whoever gives themselves credit for creating the game).


Could you provide a link to these updates?

---

### Post by slooksterpsv on 2010-08-11
> **Joseph Schwenker said:**
> Could you provide a link to these updates?
[http://www.gamershell.com/download_11755.shtml](http://www.gamershell.com/download_11755.shtml)

---

### Post by Joseph Schwenker on 2010-08-11
> **slooksterpsv said:**
> [http://www.gamershell.com/download_11755.shtml](http://www.gamershell.com/download_11755.shtml)

Is that that only patch I need to install, or were there multiple updates released that need to be installed?

---

### Post by Perfect Storm on 2010-08-11
Get the megapack instead. It contains the latest patch + bonus stuff

---

### Post by Joseph Schwenker on 2010-08-11
> **Artificial Intelligence said:**
> Get the megapack instead. It contains the latest patch + bonus stuff

Can you give me a download link to the Megapack patch?

---

### Post by Perfect Storm on 2010-08-11
[http://www.gamershell.com/download_11937.shtml](http://www.gamershell.com/download_11937.shtml)

---

### Post by Joseph Schwenker on 2010-08-11
Thanks for all of these patches!  I noticed that on the mega pack page, it said that it contains "9 new and updated maps".  If I install the unupdated version of UT2K4 and play on a server just to test it out (without installing the patch), could I be banned for "cheating", since the maps I'm using aren't the same ones that the server has?

---

### Post by Perfect Storm on 2010-08-11
The megapack is an official release. So the answer is no.

---

### Post by Joseph Schwenker on 2010-08-11
If I install the **un**updated version of UT2K4 and play on a server just to test it out (**without** installing the patch)...

In other words, is it mandatory that I apply this update, or will I be able to play the game without it?  It doesn't really matter, I'll probably just install the patch immediately, though I'm just a bit curious.

---

### Post by Perfect Storm on 2010-08-11
AFAIK the patch fixes some serious performance/running issues. I highly doubt it can run on a modern Linux system without the patches.

---

### Post by Joseph Schwenker on 2010-08-11
Alright.  I'll be sure to install it immediately after installing the base UT2K4.  Does the patch fix the VOIP chat issue?

---

### Post by Perfect Storm on 2010-08-11
No idea. I don't use VOIP.

---

### Post by handy on 2010-08-11
> **Joseph Schwenker said:**
> Thanks for all of these patches!  I noticed that on the mega pack page, it said that it contains "9 new and updated maps".  If I install the unupdated version of UT2K4 and play on a server just to test it out (without installing the patch), could I be banned for "cheating", since the maps I'm using aren't the same ones that the server has?

All you really need to know about that question is that everyone you will be playing against will already have these patches installed. :D

---

### Post by Joseph Schwenker on 2010-08-11
Thanks.  It came in the mail today, so I'll be installing it today.  I contacted Ryan Gordon to ask if his VOIP patch still worked, and he said that I could just install the two files and it should work.  I replied and asked him if I need the ~/.openalrc file, and if there was a way to test VOIP offline.  Hopefully the problem isn't that my microphone is in my USB webcam.

---

### Post by Joseph Schwenker on 2010-08-11
Low and behold, my game doesn't have the Linux installer in it.  I tried using the [Linux installer]("http://www.liflg.org/?catid=6&gameid=17") linked to earlier in the forum, but as soon as I enter my CD key, the window freezes and stops working.  I really need to get this installed!  Can anyone help?

---

### Post by Joseph Schwenker on 2010-08-11
I am now using [this guide]("http://forums.epicgames.com/showthread.php?t=558146") to install it.

---

### Post by Joseph Schwenker on 2010-08-11
I had a bit of trouble getting a launcher to work, but I eventually succeeded by pointing the launcher to a script that I made.

```
#!/bin/sh
cd "/usr/local/games/ut2004/System/"
./ut2004-bin
```

Copy and paste that into gedit, save it, mark it as executable, then point the launcher to it.  Thanks for all of your help, everyone!

---

### Post by handy on 2010-08-11
I have a vague recollection that it was best to copy the installer file onto the desktop & run it from there. Though you have got past the problem now anyway.

I had an email conversation with Iculus in the past. I was impressed by his humility & humour. :)

---

### Post by Joseph Schwenker on 2010-08-11
> **handy said:**
> I have a vague recollection that it was best to copy the installer file onto the desktop & run it from there. 

There was no Linux installer included.  I'll have to mention that on Newegg, as Newegg said listed Linux under supported operating systems.

---

### Post by slooksterpsv on 2010-08-11
> **Joseph Schwenker said:**
> There was no Linux installer included.  I'll have to mention that on Newegg, as Newegg said listed Linux under supported operating systems.

There should be, on the root of disc 1, linux-installer.sh

You don't have that on disc 1? Does the box say about it and Linux?

---

### Post by Joseph Schwenker on 2010-08-11
Contrary to what Newegg said, the game includes no Linux installer.  It is the Midway DVD version.  Newegg said that it included the editor's choice and mega bonus pack, though all of the reviews on Newegg said that this was not so.
There is no Linux installer.  I looked in all of the directories. The person who wrote the guide also said so.  I downloaded the Loki Linux Installer, but it froze after I entered my serial code.  The back of the game does not list Linux in the requirements.

---

### Post by handy on 2010-08-11
My multiple CD set holds the installer on the 2nd CD.

& marketroids can rarely be trusted, as by their nature they are a selfish breed who profit from the exploitation of others. A lot like meat eaters come to think of it. hmm...

---

### Post by Brebs on 2010-08-12
> **Joseph Schwenker said:**
> the Midway DVD version
Yeah, that one [was tricky](http://bugs.gentoo.org/show_bug.cgi?id=159164).

---

### Post by Joseph Schwenker on 2010-08-12
Can anyone help me set /usr/local/games/ut2004/System/ut2004-bin as the command "ut2004"?  "ut2004demo" is already set, but "ut2004" is not.

---

### Post by Joseph Schwenker on 2010-08-12
After that, can someone help me install the Killing Floor UT2004 mod natively?
I found a link to the mod installer, but it's for Windows.  I ran it, and it created the standard Animations, Textures, etc.  I tried dragging those files into ut2004, but it wanted to replace a whole bunch of content, so I cancelled and undid the move operation.  Additionally, I'm not entirely sure how to execute the mod.  There is a bat file, very similar to a Linux executable for a mod, but I can't figure out how to make it into a bash script.  I read on another thread that the command to execute Killing Floor is "ut2004 -mod-KF".

---

### Post by Technophobia on 2010-08-12
Install KF into your .ut2004 dirctory with Wine. Then start it with "ut2004 -mod=KFMod20" in the terminal.

---

### Post by Joseph Schwenker on 2010-08-12
> **Technophobia said:**
> Install KF into your .ut2004 dirctory with Wine. Then start it with "ut2004 -mod=KFMod20" in the terminal.

Thanks, I'll try that.  I thought that you installed mods into your UT2004 install directory (/usr/local/games/ut2004).  That's what I did for Alien Swarm, and it worked.

---

### Post by Joseph Schwenker on 2010-08-12
Wait!  If I install it into ~/.ut2004, then it will replace any directories with the same name, like System.  Should I install it into a new directory: ~/.ut2004/KillingFloor?

---

### Post by Joseph Schwenker on 2010-08-12
I'd really like to play some mods NOW.  I already waited several days for the game, and I shouldn't have to wait any longer.  PLEASE help me do the things I mentioned above.  I'd really like to start playing now.

---

### Post by Joseph Schwenker on 2010-08-12
> **Technophobia said:**
> Install KF into your .ut2004 dirctory with Wine. Then start it with "ut2004 -mod=KFMod20" in the terminal.

I am unable to do either of those things; as I mentioned in one of my previous posts, I need help setting "/usr/local/games/ut2004/System/ut2004-bin" as "ut2004".  Also, if I install the game to ~/.ut2004, it will overwrite my System directory, which I assume contains all of Unreal Tournament 2004's settings.

---

### Post by Joseph Schwenker on 2010-08-13
bump

---

### Post by Joseph Schwenker on 2010-08-15
bump
I am now getting random clicking noises whenever the sound is quiet.  My microphone does not work.  I cannot play mods.  I cannot launch the game with "ut2004".  I cannot connect to any listen servers.  I am sick of this.  I've been waiting for two days for a reply, and I'd just like to actually PLAY my game.    PLEASE SOLVE THIS NOW.

---

### Post by Joseph Schwenker on 2010-08-15
I just looked at a guide on how to get the microphone to work, and I joined Public and Team, but no one could hear me.  I looked for the meter that indicates how loudly you are speaking, but it was nowhere on the screen.  The volume went down when I pressed F to talk, though.  I tried running the game with pasuspender and padsp.  Here's the output of the game with padsp, it was interesting because I heard the clicking  for a few seconds after I quit the game, then it stopped, and the console updated.  After the clicking stopped, the console updated itself with pause_audiodevice stubbed for 0x3.  Here's the entire output.

```
joseph@joseph:~$ cd /usr/local/games
joseph@joseph:/usr/local/games$ cd ut2004
joseph@joseph:/usr/local/games/ut2004$ cd System/
joseph@joseph:/usr/local/games/ut2004/System$ padsp ./ut2004-bin
WARNING: ALC_EXT_capture is subject to change!
Defaulting to false
Defaulting to false
Resolved ut2004master2.epicgames.com -> 216.27.56.6
Resolved ut2004master1.epicgames.com -> 24.199.192.15
Connection established.
Resolved ut2004master2.epicgames.com -> 216.27.56.6
Resolved ut2004master2.epicgames.com -> 216.27.56.6
Resolved ut2004master2.epicgames.com -> 216.27.56.6
Resolved ut2004master1.epicgames.com -> 24.199.192.15
Connection established.
RecvFrom returned SOCKET_ERROR 111
RecvFrom returned SOCKET_ERROR 111
RecvFrom returned SOCKET_ERROR 111
Defaulting to false
pause_audiodevice stubbed for 0x3
pause_audiodevice stubbed for 0x3
joseph@joseph:/usr/local/games/ut2004/System$ 

```

---

### Post by Joseph Schwenker on 2010-08-15
I solved one of my problems by myself.  I found where UT2K4's demo symbolic link was stored (/usr/local/bin), then copied my launcher script for UT2K4 into /usr/local/games/ut2004/, then created a symbolic link to it in /usr/local/bin by typing 

```
sudo ln -s /usr/local/games/ut2004/ut2004 /usr/local/bin/ut2004
```

Be sure to mark the script as executable, as well as the symbolic link!  This is the script: 

```
#!/bin/sh
cd "/usr/local/games/ut2004/System/"
./ut2004-bin
```

Save that file as ut2004 and put it in /usr/local/games/ut2004/.

---

### Post by Joseph Schwenker on 2010-08-15
I still need help with:

A) Getting the microphone to work
B) Stopping the weird clicking noises at loading screens
C) Installing mods (ones that, unlike Alien Swarm, want to replace core UT2K4 content)

---

### Post by Joseph Schwenker on 2010-08-16
Ok, I fixed the weird clicking noises, and found out how to install mods.  I looked in the guide for Out of Hell, and I found that you are supposed to take the directory above the standard mod folders and put that into /usr/local/ut2004 (the UT2004 folder, NOT the configuration folder in ~/.ut2004.  Thus, the hierarchy would go like this:

MOD:

Out_Of_Hell
-Animations
-Textures
-Maps
-System
-Models
-Sounds
-Music

and then drag Out_Of_Hell into /usr/local/games/ut2004.  UT2004 now looks like this: 

ut2004
-AlienSwarm
-Animations
-Textures
-Maps
-Out_Of_Hell

Now, running the mod is a bit more difficult.  This may change from mod to mod, but for Out of Hell, I hate to write a script/use the terminal.  
If you are using the terminal: cd to /usr/local/games/ut2004/System
then type: padsp ./ut2004-bin -mod=Out_Of_Hell
and the mod should start.

For a script: 

```
#!/bin/sh
cd "/usr/local/games/ut2004/System/"
padsp ./ut2004-bin -mod=Out_Of_Hell
```

You notice the "padsp" command.  I saw this on the Out Of Hell forum, and it solved my issue with the random noise in UT2004.  Just put padsp before ./ut2004-bin (if you're using my script or the terminal) or ut2004 (if you have set up the symbolic link, as described above).
Also, this will allow you to run Chrom/ium and UT2004 at the same time; Chrome's ALSA plugin stops UT2004 from having sound.
You could also use pasuspender, though I haven't tested it as much.  It probably works, though.

Ryan Gordon does not have an answer for the mic, but he says that someone should fix it.

---

### Post by Joseph Schwenker on 2010-08-16
Another problem has sprung up, this time with text-to-speech.  I cannot get it to work.  I looked [here]("http://icculus.org/lgfaq/#ut2k4tts"), and it says that I need to install two programs, start a program, and change a configuration.  I installed festival, but could not find any program with the exact name "speechd".  I found "python-speechd", which I thought would work.  I then modified the file to set the TTS to /dev/speech.  I reread the isntructions, and it said that I needed to launch speechd.  I typed speechd, but nothing happened.  I tried again, and was given two options that started with "speechd": speechd-server-spawn and speechd-up.
Neither command starts speechd, and I do not have TTS in-game.

---

### Post by Joseph Schwenker on 2010-08-16
bump

---

### Post by handy on 2010-08-16
> **Joseph Schwenker said:**
> bump

I know you are very impatient having had to work hard over days in an effort to get UT2K4 to function the way you want it to on Ubuntu. & you have had a lot of success. :)

It would be nice if you wrote a how-to after you have solved all of the current problems, it would help others in the future, saving them from what you have had to go through.

If any of us who are following your thread knew the answers to your questions we would have posted them.

Just a tip that you probably don't know - it is considered to be bad etiquette to bump inside of a 24 hour period here.

I hope your solution manifests soon. :)

---

### Post by Joseph Schwenker on 2010-08-16
> **handy said:**
> I know you are very impatient having had to work hard over days in an effort to get UT2K4 to function the way you want it to on Ubuntu. & you have had a lot of success. :)

It would be nice if you wrote a how-to after you have solved all of the current problems, it would help others in the future, saving them from what you have had to go through.

If any of us who are following your thread knew the answers to your questions we would have posted them.

Just a tip that you probably don't know - it is considered to be bad etiquette to bump inside of a 24 hour period here.

I hope your solution manifests soon. :)

Thanks.  I have already explained clearly the solutions to the problems that I have solved.  Thus, I probably won't need a separate how-to thread.
I know that it is bad etiquette to bump twice within a 24-hour time period, though I have tried not to do so.  I don't believe that I have intentionally done so yet.
This is a difficult problem, and if I need to bump the post often to get an answer, I will do so.  Forum etiquette always seems pointless to me.  

"You do realize this thread is five years old..."
"Yeah, that means that you were too stupid to solve it five years ago, and I'm bringing up the fact that this problem has not been solved in five years!  No, I'm not starting a new thread-- this thread is already here!  Maybe when people look at the date they'll realize that this has been going on for a long time."

Chances are, my problem will not soon be solved.  Getting the microphone to work is a bit complex.

---

### Post by handy on 2010-08-16
Someone else might go to the trouble for you then. :)

---

### Post by Brebs on 2010-08-17
> **Joseph Schwenker said:**
> /dev/speech
speechd provides /dev/speech - so you *need* to be running speechd.

---

### Post by Joseph Schwenker on 2010-08-17
> In order to use Speech Dispatcher with Festival (which is recommended), you
must have installed this package (or the packages it depends on) and the
Festival server started.  To achieve the latter, you must start the server
either by hand such as running

  festival --server

on a command line or in some script, or you must comment out the

  exit 0

line in the /etc/init.d/festival file.

Please note all your local host names must be set in the /etc/festival.scm file
before starting the Festival server so that it is accessible.  For instance
line like the following should be present in your /etc/festival.scm:

  (set! server_access_list '(localhost your-alternate-host-name))

If Speech Dispatcher is started before the Festival server is started, you must
run

  invoke-rc.d speech-dispatcher reload

to allow Speech Dispatcher to figure out that the previously unavailable
Festival server is now running.

And finally, you must tell Speech Dispatcher to use Festival for its output.
Change the following configuration options in
/etc/speech-dispatcher/speechd.conf:

  DefaultModule festival
  LanguageDefaultModule "en" "festival"

 -- Milan Zamazal <pdm@debian.org>, Wed Nov 26 12:41:31 2003

I have encountered several problems with this:

/etc/init.d/festival does not exist.
/etc/festival.scm does not exist.

I installed speech-dispatcher-festival.  I ran festival --server from alt F2, I changed /etc/speech-dispatcher/speechd.conf as the README stated.  I was then unsure of what command to run, so I first tried speechd-server-spawn, then tried speech-dispatcher.  When I looked in System Monitor, speech-dispatcher and festival were both running.  I took a look in /dev, but did not see a speech folder or file.  I launched the game anyway, but I heard no text spoken.
Oh, and just out of curiosity, how can I make speech-dispatcher and festival say things I type?  In espeak, I could type "espeak "I do not want to go shopping with you", and it would say that phrase.
Thanks for the path to the README.

---

### Post by gnomeuser on 2010-08-17
for people like me who bought the gog.com edition here are instructions for how to go about getting a native install.

[http://www.gog.com/en/forum/unreal_series/unreal_tournament_2004_linux_version/perm=10/#p_b_10](http://www.gog.com/en/forum/unreal_series/unreal_tournament_2004_linux_version/perm=10/#p_b_10)

(you can use the link further down to get more mirrors for the patch)

This is an alternative approach to solving the need for openal libraries.

[http://ubuntuforums.org/showpost.php?p=3862601&postcount=9](http://ubuntuforums.org/showpost.php?p=3862601&postcount=9)

Also requires libstdc++5 so you need to install that as well.

I've only tested it so far as the getting the game to nearly start, but it dislikes my GLX so I haven't played it yet.

---

### Post by Joseph Schwenker on 2010-08-17
> **gnomeuser said:**
> for people like me who bought the gog.com edition here are instructions for how to go about getting a native install.

[http://www.gog.com/en/forum/unreal_series/unreal_tournament_2004_linux_version/perm=10/#p_b_10](http://www.gog.com/en/forum/unreal_series/unreal_tournament_2004_linux_version/perm=10/#p_b_10)

(you can use the link further down to get more mirrors for the patch)

This is an alternative approach to solving the need for openal libraries.

[http://ubuntuforums.org/showpost.php?p=3862601&postcount=9](http://ubuntuforums.org/showpost.php?p=3862601&postcount=9)

Also requires libstdc++5 so you need to install that as well.

I've only tested it so far as the getting the game to nearly start, but it dislikes my GLX so I haven't played it yet.

I bought the Midway DVD version, and already have it working natively.  I already have sound working (and without as many noise spikes, thanks to padsp).

---

### Post by Brebs on 2010-08-18
speech-dispatcher looks like a red herring - it doesn't create /dev/speech, which UT2004 needs for text-to-speech.

I've just got this working (in a different distro), using [speechd](http://www.speechio.org/) and [flite](http://cmuflite.org/). First, I [patched speechd](http://pastebin.com/tqKFtDzU) to add support for outputting to flite, then I patched flite to use a decent default voice:

```
sed -i -e 's:flite_voice_list = flite_set_voice_list();:flite_voice_list = flite_set_voice_list();\n    desired_voice = flite_voice_select("rms");:' main/flite_main.c
```

I'm quite surprised that speechd doesn't appear to be in Debian/Ubuntu.

---

### Post by Joseph Schwenker on 2010-08-18
I'll try what you suggested, Brebs.  I'm using [this guide]("http://icculus.org/lgfaq/#ut2k4tts"), and I'm only trying to use speechd because that's what it says to use.  Is it possible that I could use espeak instead if I can't get this to work?

---

### Post by Brebs on 2010-08-18
speechd provides **/dev/speech**, which you need. It then runs the speech-synthesis program - e.g. festival, flite, rsyth, viavoice.

If you want speechd to work with espeak, then you'll have to patch in support for it, just like in the patch I just showed you.

So, to be clear, you need speechd, plus a speech-synthesis program that's supported by speechd.

---

### Post by Joseph Schwenker on 2010-08-18
I'm confused.  I don't know how to compile anything; all I know is that it involves a lot of "make"s.  The link to the speechd website leads me to a page with an error.  The Flite website has only the sources, which, again, I do not know how to compile.  Could you provide me with an RPM or DEB?

---

### Post by Brebs on 2010-08-18
Yeah, the speechd website is a joke. In Firefox, click on the View menu, then "Page Source" - not that it's particularly enlightening.

To install speechd, log in as root (e.g. *sudo su*), then run these commands:

```
cd
umask -S 0022
wget http://download.lunar-linux.org/lunar/patches/speechd-0.56-add-flite-support.patch
wget http://www.speechio.org/dl/speechd-0.56.tar.gz
rm -rf speechd
tar -xf speechd-0.56.tar.gz
cd speechd
patch -Np0 -i ../speechd-0.56-add-flite-support.patch
sed -i -e "s:/usr/local:/usr:" Makefile
sed -i -e "s:festival:flite:" speechdrc
sed -i -e "s:MANDIR=man/man1:MANDIR=share/man/man1:" -e "s:INSTALL_MANDIR=/usr/man/man1:INSTALL_MANDIR=/usr/share/man/man1:" Makefile
make
make install

```

Then run "speechd" as root, and notice that you have /dev/speech. To stop speechd, run "killall speechd" - it doesn't remove /dev/speech, which is a bit confusing, because echoing text to /dev/speech when speechd is not running will just make the echo hang! Make sure you have exactly one instance of speechd running, because it doesn't check itself:

```
ps ax | grep /usr/bin/speechd
```

flite is [already in Ubuntu](http://packages.ubuntu.com/lucid/flite), thankfully.

Test it, by running as your normal user (rather than as root):
```
flite -t "would you like to play a nice game of chess?"
echo "would you like to play a nice game of chess?" > /dev/speech
```
When that echo command works, ut2004 will work.

You will probably want flite to use the "rms" voice, if you're running version 1.4 or later (run **flite -lv** to see the voices available), rather than the "kal" robot-sounding default, so change line 195 of /usr/bin/speechd to be:
```
    @cmd = qw(flite -voice rms -t);
```
Instead of:
```
    @cmd = qw(flite -t);
```

---

### Post by Joseph Schwenker on 2010-08-18
I copied and pasted all of the commands you said, but in the end, I heard nothing.  Here is everything I did:

```
joseph@joseph:~$ sudo su
[sudo] password for joseph: 
root@joseph:/home/joseph# cd
root@joseph:~# wget -O speechd-0.56-add-flite-support.patch http://pastebin.com/download.php?i=tqKFtDzU
--2010-08-18 16:05:35--  http://pastebin.com/download.php?i=tqKFtDzU
Resolving pastebin.com... 173.236.86.29
Connecting to pastebin.com|173.236.86.29|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3699 (3.6K) [application/download]
Saving to: `speechd-0.56-add-flite-support.patch'

100%[======================================>] 3,699       --.-K/s   in 0.02s   

2010-08-18 16:05:35 (160 KB/s) - `speechd-0.56-add-flite-support.patch' saved [3699/3699]

root@joseph:~# wget http://www.speechio.org/dl/speechd-0.56.tar.gz
--2010-08-18 16:05:41--  http://www.speechio.org/dl/speechd-0.56.tar.gz
Resolving www.speechio.org... 64.71.152.40
Connecting to www.speechio.org|64.71.152.40|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 23815 (23K) [application/x-gzip]
Saving to: `speechd-0.56.tar.gz'

100%[======================================>] 23,815       137K/s   in 0.2s    

2010-08-18 16:05:42 (137 KB/s) - `speechd-0.56.tar.gz' saved [23815/23815]

root@joseph:~# tar -xf speechd-0.56.tar.gz
root@joseph:~# cd speechd
root@joseph:~/speechd# patch -Np0 -i ../speechd-0.56-add-flite-support.patch
patching file speechd
Hunk #1 succeeded at 7 (offset -1 lines).
Hunk #2 succeeded at 64 (offset -1 lines).
Hunk #3 succeeded at 190 (offset -1 lines).
Hunk #4 succeeded at 212 (offset -1 lines).
Hunk #5 succeeded at 248 (offset -1 lines).
Hunk #6 succeeded at 307 (offset -1 lines).
Hunk #7 succeeded at 343 (offset -1 lines).
Hunk #8 succeeded at 501 (offset -1 lines).
patch unexpectedly ends in middle of line
Hunk #9 succeeded at 592 with fuzz 2 (offset -1 lines).
root@joseph:~/speechd# sed -i -e "s:/usr/local:/usr:" Makefile
root@joseph:~/speechd# sed -i -e "s:festival:flite:" speechdrc
root@joseph:~/speechd# make
mkdir -p man/man1
mkdir -p bin
pod2man speechd > man/man1/speechd.1
pod2man catspeech > man/man1/catspeech.1
echo '#!/usr/bin/perl -w' > bin/catspeech
cat catspeech >> bin/catspeech
echo '#!/usr/bin/perl -w' > bin/speechd
cat speechd >> bin/speechd
root@joseph:~/speechd# make install
pod2man speechd > man/man1/speechd.1
install --mode=755 --owner=root --group=root bin/catspeech \
		/usr/bin/catspeech
install --mode=755 --owner=root --group=root bin/speechd \
		/usr/bin/speechd
test -d /usr/man/man1 || /bin/mkdir /usr/man/man1
/bin/mkdir: cannot create directory `/usr/man/man1': No such file or directory
make: *** [install-man] Error 1
root@joseph:~/speechd# speechd
root@joseph:~/speechd# su joseph
joseph@joseph:/root/speechd$ cd
joseph@joseph:~$ flite -voice rms -t "would you like to play a nice game of chess?"
joseph@joseph:~$ echo "would you like to play a nice game of chess?" > /dev/speech

```

The final command did nothing; I heard nothing.  I ran the command after I had installed flite in synaptic.

---

### Post by Joseph Schwenker on 2010-08-18
I also got an error about being unable to find "rms".

---

### Post by Brebs on 2010-08-18
Remove /root/speechd and do the install again - notice I've added a sed command to fix the mandir, so speechd should complete its installation now - it had failed before it got around to installing /etc/speechdrc, which is what tells speechd to use flite rather than festival.

Read what I wrote - you are running Ubuntu's **old** version of flite, which doesn't have the "rms" voice. So don't set the voice.
```
flite -t "would you like to play a nice game of chess?"
```
If you still have problems, run speechd in debugging mode, so it will show what it is doing:
```
killall speechd
speechd -f -s flite
```

---

### Post by Joseph Schwenker on 2010-08-18
```
joseph@joseph:~$ cd /usr/bin/
joseph@joseph:/usr/bin$ sudo gedit speechd
speechd               speechd-server-spawn  speechd-up
joseph@joseph:/usr/bin$ sudo gedit speechd
speechd               speechd-server-spawn  speechd-up
joseph@joseph:/usr/bin$ sudo gedit speechd
[sudo] password for joseph: 

(gedit:7104): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed

(gedit:7104): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed

(gedit:7104): GLib-GObject-CRITICAL **: g_object_ref: assertion `object->ref_count > 0' failed
joseph@joseph:/usr/bin$ clear
joseph@joseph:/usr/bin$ flite -lv
failed to open file "-lv" for reading
joseph@joseph:/usr/bin$ su root
Password: 
su: Authentication failure
joseph@joseph:/usr/bin$ su root
Password: 
su: Authentication failure
joseph@joseph:/usr/bin$ sudo su root
root@joseph:/usr/bin# cd
root@joseph:~# ls
Desktop  speechd  speechd-0.56-add-flite-support.patch  speechd-0.56.tar.gz
root@joseph:~# rm -r speechd
root@joseph:~# ls
Desktop  speechd-0.56-add-flite-support.patch  speechd-0.56.tar.gz
root@joseph:~# cd
root@joseph:~# wget -O speechd-0.56-add-flite-support.patch http://pastebin.com/download.php?i=tqKFtDzU
--2010-08-18 16:52:28--  http://pastebin.com/download.php?i=tqKFtDzU
Resolving pastebin.com... 173.236.86.29
Connecting to pastebin.com|173.236.86.29|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3699 (3.6K) [application/download]
Saving to: `speechd-0.56-add-flite-support.patch'

100%[======================================>] 3,699       --.-K/s   in 0.02s   

2010-08-18 16:52:28 (149 KB/s) - `speechd-0.56-add-flite-support.patch' saved [3699/3699]

root@joseph:~# wget http://www.speechio.org/dl/speechd-0.56.tar.gz
--2010-08-18 16:52:32--  http://www.speechio.org/dl/speechd-0.56.tar.gz
Resolving www.speechio.org... 64.71.152.40
Connecting to www.speechio.org|64.71.152.40|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 23815 (23K) [application/x-gzip]
Saving to: `speechd-0.56.tar.gz.1'

100%[======================================>] 23,815       137K/s   in 0.2s    

2010-08-18 16:52:33 (137 KB/s) - `speechd-0.56.tar.gz.1' saved [23815/23815]

root@joseph:~# tar -xf speechd-0.56.tar.gz
root@joseph:~# cd speechd
root@joseph:~/speechd# patch -Np0 -i ../speechd-0.56-add-flite-support.patch
patching file speechd
Hunk #1 succeeded at 7 (offset -1 lines).
Hunk #2 succeeded at 64 (offset -1 lines).
Hunk #3 succeeded at 190 (offset -1 lines).
Hunk #4 succeeded at 212 (offset -1 lines).
Hunk #5 succeeded at 248 (offset -1 lines).
Hunk #6 succeeded at 307 (offset -1 lines).
Hunk #7 succeeded at 343 (offset -1 lines).
Hunk #8 succeeded at 501 (offset -1 lines).
patch unexpectedly ends in middle of line
Hunk #9 succeeded at 592 with fuzz 2 (offset -1 lines).
root@joseph:~/speechd# sed -i -e "s:/usr/local:/usr:" Makefile
root@joseph:~/speechd# sed -i -e "s:festival:flite:" speechdrc
root@joseph:~/speechd# sed -i -e "s:MANDIR=man/man1:MANDIR=share/man/man1:" -e "s:INSTALL_MANDIR=/usr/man/man1:INSTALL_MANDIR=/usr/share/man/man1:" Makefile
root@joseph:~/speechd# make
mkdir -p share/man/man1
mkdir -p bin
pod2man speechd > share/man/man1/speechd.1
pod2man catspeech > share/man/man1/catspeech.1
echo '#!/usr/bin/perl -w' > bin/catspeech
cat catspeech >> bin/catspeech
echo '#!/usr/bin/perl -w' > bin/speechd
cat speechd >> bin/speechd
root@joseph:~/speechd# make install
pod2man speechd > share/man/man1/speechd.1
install --mode=755 --owner=root --group=root bin/catspeech \
		/usr/bin/catspeech
install --mode=755 --owner=root --group=root bin/speechd \
		/usr/bin/speechd
test -d /usr/share/man/man1 || /bin/mkdir /usr/share/man/man1
install --mode=644 --owner=root --group=root share/man/man1/speechd.1 \
		/usr/share/man/man1/speechd.1
install --mode=644 --owner=root --group=root share/man/man1/catspeech.1 \
		/usr/share/man/man1/catspeech.1
install --mode=644 --owner=root --group=root speechdrc \
		/etc/speechdrc
install --mode=644 --owner=root --group=root speechd.sub \
		/etc/speechd.sub
root@joseph:~/speechd# speechd
root@joseph:~/speechd# ps ax | grep /usr/bin/speechd
 7207 ?        Ss     0:00 /usr/bin/perl -w /usr/bin/speechd
 7224 pts/1    S+     0:00 grep --color=auto /usr/bin/speechd
root@joseph:~/speechd# killall speechd
root@joseph:~/speechd# ps ax | grep /usr/bin/speechd
 7227 pts/1    S+     0:00 grep --color=auto /usr/bin/speechd
root@joseph:~/speechd# killall speechd
speechd: no process found
root@joseph:~/speechd# clear

root@joseph:~/speechd# speechd
root@joseph:~/speechd# ps ax | grep /usr/bin/speechd
 7241 ?        Ss     0:00 /usr/bin/perl -w /usr/bin/speechd
 7249 pts/1    R+     0:00 grep --color=auto /usr/bin/speechd
root@joseph:~/speechd# su joseph
joseph@joseph:/root/speechd$ cd
joseph@joseph:~$ flite -t "would you like to play a nice game of chess?"
joseph@joseph:~$ killall speechd
speechd(7241): Operation not permitted
speechd: no process found
joseph@joseph:~$ sudo su root
root@joseph:/home/joseph# killall speechd
root@joseph:/home/joseph# speechd -f -s flite
Loaded speechd.sub.
String substitutions: 222
Checking for /etc/speechdrc...loaded.
Checking for /root/.speechdrc...not found.
Speech synthesis system = "flite"
cmd = flite -t



```

I opened Gedit and set the voice back to the default from rms.  Then I compiled the thing, then I ran the ps ax thing, and noticed two instances.  I typed killall speechd, then restarted it, and there were still two instances.  Again, in the end, it didn't work.  I ran it in debug mode, if any of that makes any sense to you.

---

### Post by Joseph Schwenker on 2010-08-18
Whoa!  I just opened my home folder, and I saw a file called rms.  I opened it, and it played "Would you like to play a nice game of chess" in Totem!  I was expecting the terminal to speak the command to me real-time, like espeak.  I didn't know that I was supposed to look for an output.  I'm not sure which set of commands this instance of rms is from, either.

---

### Post by Brebs on 2010-08-18
> # ps ax | grep /usr/bin/speechd
 7241 ?        Ss     0:00 /usr/bin/perl -w /usr/bin/speechd
 7249 pts/1    R+     0:00 grep --color=auto /usr/bin/speechd
That is one instance of speechd running, and also showing the grep command that you're running. It is *not* 2 instances of speechd.

So, get the flite command working and producing sound, then get the echo command working.

That "rms file" is probably flite creating an audio *file*, instead of audio, because your old version of flite doesn't understand "-voice rms". You can see the program options:

```
flite --help
speechd -h
```

---

### Post by Joseph Schwenker on 2010-08-18
How should I go about getting those two working?  I ran the commands you said, and nothing happened.  I've never used either of these programs before.

---

### Post by Brebs on 2010-08-18
Strewth, flite 1.3 has a different command syntax to 1.4. From flite.texi:
> The second argument @code{OUTPUTTYPE} is the name of a file the output
is written to, or if it is @code{play} then it is played to the audio
device directly.  If it is @code{none} then the audio is created but
discarded, this is used for benchmarking.  If @code{OUTPUTTYPE} is
omitted, @code{play} is assumed.  You can also explicitly set the
outputtype with the @code{-o} flag
So your flite is creating the audio, then discarding it :lolflag:

What a ridiculous default behaviour. Anyway, it looks like you should change that line 195 (only needed for flite 1.3) to:
```
    @cmd = qw(flite -o play -t);
```
Then restart speechd.

---

### Post by Brebs on 2010-08-18
And here is how to install flite 1.4 - run as root:

```
apt-get remove flite
cd
umask -S 0022
wget http://www.speech.cs.cmu.edu/flite/packed/flite-1.4/flite-1.4-release.tar.bz2
rm -rf flite-1.4-release
tar -xf flite-1.4-release.tar.bz2
cd flite-1.4-release
sed -i -e 's:flite_voice_list = flite_set_voice_list();:flite_voice_list = flite_set_voice_list();\n    desired_voice = flite_voice_select("rms");:' main/flite_main.c
./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var --infodir=/usr/share/info --mandir=/usr/share/man --with-audio=alsa --enable-shared
make
make install
```

---

### Post by Joseph Schwenker on 2010-08-18
Excellent!  I followed all of your instructions, finally got output.  However, when I switched to my own user account from root, I got an error: 

```
root@joseph:/usr/bin# flite -t "hello world"
root@joseph:/usr/bin# su joseph
joseph@joseph:/usr/bin$ flite -t "hello world"
flite: error while loading shared libraries: libflite_cmu_us_kal.so.1: cannot open shared object file: No such file or directory
joseph@joseph:/usr/bin$ 

```

Is something owned by root that shouldn't be?

---

### Post by Brebs on 2010-08-18
Compare to my setup:

```
$ flite --version
  Carnegie Mellon University, Copyright (c) 1999-2009, all rights reserved
  version: flite-1.4-release December 2009 (http://cmuflite.org)

$ ls -l /usr/lib/libflite_cmu_us_kal.so.1*
lrwxrwxrwx 1 root root      26 Aug 19 02:32 /usr/lib/libflite_cmu_us_kal.so.1 -> libflite_cmu_us_kal.so.1.4
-rwxr-xr-x 1 root root 1977578 Aug 19 02:32 /usr/lib/libflite_cmu_us_kal.so.1.4

$ ldd /usr/bin/flite
	linux-gate.so.1 =>  (0xb7701000)
	libflite_cmu_us_kal.so.1 => /usr/lib/libflite_cmu_us_kal.so.1 (0xb7500000)
	libflite_cmu_time_awb.so.1 => /usr/lib/libflite_cmu_time_awb.so.1 (0xb7160000)
	libflite_cmu_us_kal16.so.1 => /usr/lib/libflite_cmu_us_kal16.so.1 (0xb6dd7000)
	libflite_cmu_us_awb.so.1 => /usr/lib/libflite_cmu_us_awb.so.1 (0xb6af2000)
	libflite_cmu_us_rms.so.1 => /usr/lib/libflite_cmu_us_rms.so.1 (0xb678e000)
	libflite_cmu_us_slt.so.1 => /usr/lib/libflite_cmu_us_slt.so.1 (0xb64a7000)
	libflite_usenglish.so.1 => /usr/lib/libflite_usenglish.so.1 (0xb6491000)
	libflite_cmulex.so.1 => /usr/lib/libflite_cmulex.so.1 (0xb6401000)
	libflite.so.1 => /usr/lib/libflite.so.1 (0xb63d9000)
	libm.so.6 => /lib/libm.so.6 (0xb63b2000)
	libasound.so.2 => /usr/lib/libasound.so.2 (0xb62ed000)
	libc.so.6 => /lib/libc.so.6 (0xb61a2000)
	/lib/ld-linux.so.2 (0xb7702000)
	libdl.so.2 => /lib/libdl.so.2 (0xb619e000)
	libpthread.so.0 => /lib/libpthread.so.0 (0xb6185000)
	librt.so.1 => /lib/librt.so.1 (0xb616f000)
```

---

### Post by Joseph Schwenker on 2010-08-18
```
joseph@joseph:~$ flite --version
flite: error while loading shared libraries: libflite_cmu_us_kal.so.1: cannot open shared object file: No such file or directory
joseph@joseph:~$ ls -l /usr/lib/libflite_cmu_us_kal.so.1*
lrwxrwxrwx 1 root root      26 2010-08-18 19:34 /usr/lib/libflite_cmu_us_kal.so.1 -> libflite_cmu_us_kal.so.1.4
-rw-r--r-- 1 root root 1975776 2010-04-24 09:31 /usr/lib/libflite_cmu_us_kal.so.1.3
-rwxr-x--- 1 root root 1987867 2010-08-18 19:33 /usr/lib/libflite_cmu_us_kal.so.1.4
joseph@joseph:~$ ldd /usr/bin/flite
	linux-gate.so.1 =>  (0xb781c000)
	libflite_cmu_us_kal.so.1 => not found
	libflite_cmu_time_awb.so.1 => not found
	libflite_cmu_us_kal16.so.1 => not found
	libflite_cmu_us_awb.so.1 => not found
	libflite_cmu_us_rms.so.1 => not found
	libflite_cmu_us_slt.so.1 => not found
	libflite_usenglish.so.1 => not found
	libflite_cmulex.so.1 => not found
	libflite.so.1 => not found
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb77db000)
	libasound.so.2 => /usr/lib/libasound.so.2 (0xb7713000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb75b9000)
	/lib/ld-linux.so.2 (0xb781d000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb75b4000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb759b000)
	librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0xb7592000)

```

---

### Post by Brebs on 2010-08-18
I don't see how you would have /usr/lib/libflite_cmu_us_kal.so.1.3 if you ran **apt-get remove flite**

I suggest you:

apt-get remove flite
rm -f /usr/lib/libflite*

Then reinstall flite 1.4 using the commands I showed earlier - note that the ./configure line is now tweaked - it may have been incomplete earlier.

Plus, an easy check:

```
$ which flite
/usr/bin/flite
```

Edit: Ah, your permissions are screwed up:

> -rw-r--r-- 1 root root 1975776 2010-04-24 09:31 /usr/lib/libflite_cmu_us_kal.so.1.3
-rwxr-x--- 1 root root 1987867 2010-08-18 19:33 /usr/lib/libflite_cmu_us_kal.so.1.4
Only root can read libflite_cmu_us_kal.so.1.4, which is wrong - did you change the permissions deliberately?

---

### Post by Joseph Schwenker on 2010-08-18
> **Brebs said:**
> Edit: Ah, your permissions are screwed up:


Only root can read libflite_cmu_us_kal.so.1.4, which is wrong - did you change the permissions deliberately?

No, I did as you said and used "sudo su root" to run the commands as root.  Most likely, since I was root, root created all of those files in its own name.  I tried to change the permissions of a folder that was only readable by root before; I wanted to change it so that it would still be owned by root, but could be read by others, but for some reason, it didn't work.  Should I just use a sudo chown -R joseph:joseph?

---

### Post by Joseph Schwenker on 2010-08-18
This is odd...
I just ran ```
flite -t "would you like to play a nice game of chess?"

```
and got the same error as usual, but when I ran ```
echo "would you like to play a nice game of chess?" > /dev/speech

```
I heard the voice speak.  I opened Unreal Tournament 2004, and heard the voice read the chat.  After I quit, I was unable to use the command again.  Unreal Tournament still reads the chat, but I cannot run that command.  Additionally, the voice that read the chat in UT2004 was really quiet, and not very clear.  RMS sounded a lot sharper; more like the espeak voice.  How can I change the default voice?

---

### Post by Brebs on 2010-08-18
Sounds like a umask issue. Check as the root user:
```
$ umask
0022
```
flite 1.4 has a main/Makefile containing:
```
cp -pd $(flite_LIBS_deps) $(INSTALLLIBDIR)
```
Which just copies the perms that the files already have - which is an unsafe method. It should use the "install" command, with -m755, just like it does 2 lines above:
```
$(INSTALL) -m 755 $(BINDIR)/flite_time $(INSTALLBINDIR)
```
So reinstall flite, using my revised commands which include umask. That will fix its file permissions.

Edit: Your "oddness" is caused by speechd running as root, which runs flite as root. And you currently have wrong perms on your flite libs, which only root can read.

You have to actually run what I tell you to run - I already include a sed command to change flite's default voice to rms.

Regarding volume, I dunno. Maybe pulseaudio's per-app volume control is kicking in.

---

### Post by Joseph Schwenker on 2010-08-18
Excellent!  I can use both flite and speechd now.  However, when I run "echo "would you like to play a nice game of chess?" > /dev/speech", the voice alternates between the default and a low-quality rms.
Okay, so remaining issues with this are:
-Setting the voice to a crisper, more understandable one (similar to espeak's sharp-sounding voice)

Also, what should I do in a new session if I want to use UT2004's TTS?  I am assuming that I need to just add speechd to my startup applications.

---

### Post by Brebs on 2010-08-18
Alternates? I suspect you're running more than one session of speechd - remember the "ps" command mentioned earlier, to check that, and the magical "killall speechd".

The only setup needed in future is to run speechd as root. You can run that automatically in a bootup script - e.g. in /etc/init.d/

---

### Post by Joseph Schwenker on 2010-08-19
Alright, it seems as if I have solved most of my problems.  However, is there a way to change the voice?  The default voice isn't very crisp at all.  It sounds very dull and bassy.
Also, think you could help me set up that startup script you spoke of?

---

### Post by Joseph Schwenker on 2010-08-19
For some reason, I didn't hear the text being parsed into speech when I played UT2004 just now.  When I closed the application, I heard some of the speech parsed.  There is a long delay between the text appearing and it being spoken.
This feature looked nice, but the delay and incomprehensibility (and the fact that it's not that reliable) makes me not want to use it.  If this feature worked ideally, it wouldn't take an expert to get it running, and it would be configured by default.  The voices would be comprehensible, and there wouldn't be such a long delay between messages.  
At the moment, this features isn't all that useful to me.  If I could get VOIP working in UT2004, then it would be a great feature, as all the players would "voice chat", and I wouldn't have to look at the chatbox ever.  Of course, since VOIP doesn't work, I am looking at the chatbox for replies, and, give this fact, as well as many of the other contributing factors, I have decided not to use this feature for now.  I DO appreciate your help, you have been very helpful, and I hope that your work will help future Linux gamers when they stumble across this thread (or a future HOWTO).  Thanks!

---

### Post by Brebs on 2010-08-19
Don't say "for some reason" - run **speechd -f** so you can SEE what's happening. None of this is magic.

Is everyone chatting, in your UT2004 games? They're supposed to be running and gunning, with little time for chit-chat :)

The funny thing is, flite is a lot *faster* than festival. If you have a single-core CPU, then maybe it's very busy servicing ut2004. You could increase its priority (look into the "nice" and "renice" commands, and /etc/security/limits.d/), but that would make ut2004 stutter.

Also, there's a deliberate "sleep 2" (pause for 2 seconds) between messages, in the speechd code - maybe that can be reduced or eliminated, I dunno.

This is only "expert stuff" because it hasn't been thrown into an installer. Look at these - [speechd](http://foo-projects.org/git/?p=lunar/moonbase.git;a=tree;f=zbeta/speechd) and [flite](http://foo-projects.org/git/?p=lunar/moonbase.git;a=tree;f=zbeta/flite). So with those, just enter "lin flite speechd" and the installation's done, configured with sensible defaults. This is because I've just taken the effort needed to package them up. Well, there's nothing stopping you or someone else from doing the Ubuntu equivalent.

---

### Post by Joseph Schwenker on 2010-08-19
I have a dual-core CPU, and speechd reads messages that I type, so it wasn't a problem creating a circumstance where speechd was supposed to read something.

I might try this again tomorrow, though I am a bit annoyed that even if I disable the text-to-speech option in UT2004's preferences, the game will hang on the startup screen if I am not running speechd.

Also, I have been having an issue for a long time with UT2004 and its mods.  They all have bad performance.  On Torlan, max settings on a GeForce 8800 GT 512MB, Intel Pentium D 2.66 Dual Core, I average around 30 fps, sometimes dipping below.  When I played Out of Hell, I noticed that at both the highest and lowest settings, I got 15 fps when looking at a character.  In Killing Floor, my CPU was screaming, and I was getting 12 fps at max settings, though that may have been the fault of the 8x AA, 16x Anisotrophic filtering and texture sharpening that I enabled in my nVidia preferences.  Still, my card supports 16x FSAA, and the game's requirements are very low.  I found someone who was having a very similar issue [here]("http://www.nvnews.net/vbulletin/showthread.php?t=99085").
Can anyone help perform the instructions mentioned in that thread?  I'd like to see if I can get more than 30 fps.  On Windows, I played Left 4 Dead with maximum settings, Unreal Tournament 3 Demo on maximum settings, and Mirrors Edge with fairly good settings.

---

### Post by Brebs on 2010-08-19
You're right - ut2004 hangs on the startup splash screen, if /dev/speech is present but speechd is not running. I ran it with **strace -e trace=file theexecutable**, and it hangs while accessing /dev/speech - kinda expected I suppose.

I think you're expecting too much of the video card - FSAA and AF really slow it down.

[Disable composite](http://ubuntuforums.org/showthread.php?t=1530118), and run the [handedness stutter fix](http://forums.gentoo.org/viewtopic-p-4173559.html#4173559).

---

### Post by handy on 2010-08-19
The FPS performance on my Athlon64 3500+/2GB RAM/AGP XFX 7950GT/512MB was better than those quoted a couple of posts up by the OP?

I ran UT2k4 with everything at max', on a 19" CRT. I was using mods as well.

---

### Post by Brebs on 2010-08-19
> **handy said:**
> 19" CRT
Irrelevant - what matters is the **screen resolution** the game was using - how many pixels the graphics card had to render.

I myself, a couple of years ago, had a 7950 card, then upgraded to an 8800. And was surprised when the 8800 turned out to be jerkier. [People have moaned about this a lot](http://www.google.com/search?hl=en&lr=&safe=off&as_qdr=all&q=ut2004+nvidia+8800+stutters&aq=f&aqi=&aql=&oq=&gs_rfai=), on Windows as well as Linux.

[Here ya go](http://forums.epicgames.com/showthread.php?t=575143):
> The common problems consist in the unexpected stuttering in a number of games, among which CoD 2 ( with volumetric lighting switch on ), Oblivion ( with HDR switch on ) , FEAR, S.T.A.L.K.E.R. The game, which demonstrates performance about 60 frames per second, can be unexpectedly slowed down to **15 FPS**.

No solution though :(

---

### Post by Joseph Schwenker on 2010-08-19
I'm not having a problem with stuttering; I'm having a problem with low fps and fps slowdowns.  When I look at intense action in ONS-Torlan, my fps go way down.  Of course, I can never top 30 fps.  I AM NOT expecting too much out of this card.  This is UNREAL TOURNAMENT we're talking about.  It was made in 2004.  I've played Half-Life 2 at maximum settings, I've played Half-Life 2: Deathmatch at maximum settings; both were made the same year.  Of course, I've also played Left 4 Dead at maximum settings.  Is some little game from 2004 "too much" for my graphics card?  What's more, is that even turning the settings down does not improve performance in Out of Hell.  30 tops, 15 for characters.  This rules out my graphics card being old.  Seriously, look at the requirements:
> Pentium III or AMD Athlon 1.0 GHz processor (Pentium® or AMD 1.2GHz or greater recommended) 
128MB RAM (256MB RAM or greater recommended) 
5.5GB HDD space REQUIRED 
8X CD-ROM or DVD 
Windows® compatible sound card 
32 MB video card required (64 MB NVIDIA or ATI hardware T&L card recommended) 
DirectX® version 9.0b (included on game disc) 
Internet (TCP/IP) and LAN (TCP/IP) play supported. Internet play requires a 33.6 kbps or faster modem (broadband recommended)

Well, let's see, I have a Pentium D Dual Core, which is greater than the recommended.  I have 2 GB of RAM.  I have an integrated sound card, which, as well all know, Ubuntu uses Pulseaudio for, which is problematic for old games, though I'm using padsp.  I have an 8 MB/PS connection, and this is not applicable as I got the 15 fps in Out of Hell (which is only single player).
Can anyone help me sort out that solution that I linked to above?

Oh, and I get the slowdowns even with AA, AF, and TS disabled.

---

### Post by slooksterpsv on 2010-08-19
[http://news.softpedia.com/news/Unreal-Tournament-2004-Tweaks-and-Unlockables-38536.shtml](http://news.softpedia.com/news/Unreal-Tournament-2004-Tweaks-and-Unlockables-38536.shtml)
That may help, but there's also other tweaks you can do in the ini file to improve performance.

Google Ut2004 ini tweaks or that to find more.

---

### Post by Brebs on 2010-08-19
Check that you're using the [performance governor](http://www.google.com/search?hl=en&lr=&safe=off&as_qdr=all&&sa=X&ei=tuVtTIz6LY2WvAPy_8D5DA&ved=0CBIQvwUoAQ&q=ut2004+linux+performance+governor+echo+cpu0&spell=1).

As root:
echo performance > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

---

### Post by Joseph Schwenker on 2010-08-19
bash: /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor: No such file or directory

Can anyone help me do the instructions that I linked to?  I'd really like that, rather than a whole bunch of unrelated stuff.  I linked to that page for a reason: the guy is having the same issue as me.  Could you help me use the instructions?  I'm not sure how to go about running two instances of Xorg and what not.  I linked to the page a few posts ago.

---

### Post by Joseph Schwenker on 2010-08-20
Oh, and I'd like to ask about an issue that I've been experiencing in all versions of UT2004, the demo and the full version.  For whatever reason, I cannot connect to listen servers.  I am stuck on the screen with their IP address, and if I choose to wait for several minutes, I get an error saying "Connection failed".  When I look at these servers in the server browser, they all have "N/A" listed as their ping.  This is for ALL listen servers.  Can anyone explain this?  I tried forwarding the ports necessary for hosting a listen server, but that didn't work.

---

### Post by Brebs on 2010-08-20
> **Joseph Schwenker said:**
> rather than a whole bunch of unrelated stuff
If you looked at the URLs that *we* provided, you would realize that they are *not* unrelated. And they most certainly are worth trying.

There's no need to start a 2nd instance of xorg - just do the necessary in your single instance of xorg. I just provided an URL to you about it! One of hundreds that are a simple googling away, because the question has been asked and answered countless times before - asking it again just increases the tedium.

Your blatant refusal to do any googling, and next to no investigative work yourself, is pretty disheartening.

For instance, do you even know if your Linux setup has any CPU power-saving in effect? Hint: Google it.

---

### Post by Joseph Schwenker on 2010-08-20
Maybe it wasn't all unrelated, though since I asked how to do a specific instruction and linked to it, I was a bit frustrated when I did not get help on it.  I tried that performance optimization that slook mentioned, but I didn't notice any dramatic performance increase.  Disabling Compiz also does very little.  I do not refuse to Google anything; I don't even know what to Google!  You linked me to a Google results page, on which the top result was THIS THREAD.  I don't even know what performance governor does, or is.  It seems that I don't have it installed, as the output of your command indicated.
The instructions I linked to:

> The composite extension is on by default now, to disable it you have to set it to false or 0, commenting it out does not do it, also the NvAGP "0" slows down the bus (and will probably make it slower too), so comment that out

I had the same problems as you with UT, basically if you enable the stuff that compiz wants then 3d is slow, so start X twice with two separate config files, one with all the options for compiz (if you use that), and then the other with most of the options turned off for games (it changed my fps from about <20 to 60+, and i only have a 6800 and play at 1680x1050 with everything max)

> I've followed your instructions and additionaly turned off cool'n'quiet and it's much better, ranging from 40 to 160 FPS. Thanks!

Can anyone help me do this?

---

### Post by Joseph Schwenker on 2010-08-21
bumpity bumpity bump

---

### Post by Joseph Schwenker on 2010-08-23
bump with a cherry on top

---

### Post by Joseph Schwenker on 2010-10-04
Gotta love the fact that everyone just boycotted this thread.  Do you expect every single person to know every single thing?  Do you expect every single user to know every single command and part of their computer?  No.  I just wanted to play Unreal Tournament, and after I asked you a specific question, you just dodged it.  Gotta love the Ubuntu sassiness.

---

### Post by slooksterpsv on 2010-10-04
> **Joseph Schwenker said:**
> Gotta love the fact that everyone just boycotted this thread.  Do you expect every single person to know every single thing?  Do you expect every single user to know every single command and part of their computer?  No.  I just wanted to play Unreal Tournament, and after I asked you a specific question, you just dodged it.  Gotta love the Ubuntu sassiness.

I'm not boycotting the thread, I just don't know the answer. Sorry :( wish I could help.

---

### Post by Joseph Schwenker on 2010-10-04
> **slooksterpsv said:**
> I'm not boycotting the thread, I just don't know the answer. Sorry :( wish I could help.

Thanks for acknowledging me.  It's more Brebs that's boycotting it due to my so-called "incompetence".  I got a new CPU, and I am now getting a lot more FPS.  However, this game is way under-optimized, so performance is a lot less than what it might be on Windows.  The microphone does not work, and the lack of PulseAudio support is really annoying.

---

### Post by uRock on 2010-10-04
People here are volunteers who help when they can. If no body has an answer, then they aren't going to post.

Hopefully someone will come along with an answer for you.

---

### Post by Joseph Schwenker on 2010-10-08
Recently, I've been noticing that the microphone has been picking up sound (the meter is moving when I speak), and people say that they are able to hear me.  I'm not entirely sure what caused it (people on the servers were being rather idiotic and some said they could hear me while others could not).  I just made some changes today, and I found that another person with a microphone was able to hear me.  Most likely, it's the fact that I'm launching the game with padsp ut2004, though I could be wrong, as padsp did nothing until recently.
Anyway, I found a great post that will help a lot of users out.  It improved my fps a bit, and made some great improvements to the game!

> Full, dynamic shadows are available for UT2004 for Linux! Icculus seemingly made a mistake in the latest patch (3369.2) for UT2004, in both the Linux and Mac versions. Follow these instructions for full shadows and note, you'll need that patch (3369.2) for this:


First of all, ensure that UT2004 isn't running.

Go to the .ut2004 directory in Home, by opening the file manager and pressing Ctrl + H. .ut2004 will appear. Then navigate to the System directory.

Edit the UT2004.ini file - in the [OpenGLDrv.OpenGLRenderDevice] section, ensure that 'UseRenderTargets=True'.

Then edit the User.ini file - in the [UnrealGame.UnrealPawn] section, ensure that 'bPlayerShadows=True' and 'bBlobShadow=False'; and ensure that in the [Engine.Vehicle] section, 'bVehicleShadows=True'.

With these changes, you can now run UT2004. Edit any of the in-game settings as you wish, however, and this is quite important, DO NOT edit the Shadow settings. You'll see that it is a menu list with nothing in it, where it would say 'None, Blob', originally. Just leave it as it is - empty. Then run your favourite map, press F4 for third-person view.... 

Et voila! Full shadows are now yours! People, cars and even Static Meshes all cast shadows!

EDIT:
Find a screenshot below presenting full dynamic shadows in UT2004 for Linux! Also, according to the Linux Questions wiki, the UT2004 client for Linux is incapable of 'rendering-to-texture', leaving car license plates, among other (more important) things, un-rendered and blank. Well, not if you set UseRenderTargets to True, as above - see below! Enjoy.





Furthermore, for extra quality in OpenGL rendering, assuming your computer is capable of handling it, edit these settings in the aforementioned UT2004.ini file:

[Engine.Engine]
DetectedVideoMemory=(Number in MB, usually set to 0 by default)

[Engine.GameEngine]
CacheSizeMegs=(Number in MB, usually set to 64. Set higher for better performance)

[OpenGLDrv.OpenGLRenderDevice]
UseVSync=True (Set False by default. 'True' provides a more consistent framerate.)
UseVBO=True (Gives access to the OpenGL VBO. Set True for performance gain.)
UseVSync=True (This appears twice in the settings, for some reason. Set this to True as well.)
UsePixelShaders=True (Set to False by default. Gives access to, well, pixel shaders.)
Last edited by Lathilde; November 25th, 2008 at 08:27 PM.. Reason: Adding screenshots for reference purposes, as well as tips for OpenGL performance and quality improvement in-game.

The original post is in [this thread]("http://ubuntuforums.org/showthread.php?t=528209").

However, after turning on all of those options in both files, I am finding these weird, transparent green pentagons in some areas in Torlan.  I think they may be shaders rendering incorrectly.  Since SDL (gotta love the incompetent developers) does not support alt tab, volume adjustment, or anything besides ctrl alt F1, I was unable to take a screenshot of this.  If there's a key to do so in-game, then please tell me.
Using the options mentioned, I was able to enable full, dynamic shadows, shaders, vertical synchronization, increase the cache size, and enable dynamic license plates.  It also looks like there is an option for anisotrophy levels in there;  does anyone know how I should use that option?
Hope this helps my fellow competitors in the tournament!

---

### Post by Protocol84 on 2010-11-10
Any time I run UT2004 on nix I log into Openbox to run it, I see about a 30% increase in most games but I do not know exactly the improvement in UT, but I notice it loads faster and runs smoother.

On a side note, as this it the most recent active thread on UT2004, I am trying to get an "uncache" script for levels downloaded from play servers working. It worked splendidly the first time but now fails.

More info here :
[http://ubuntuforums.org/showthread.php?p=10098459#post10098459](http://ubuntuforums.org/showthread.php?p=10098459#post10098459)

Any help would be greatly appreciated!

---

