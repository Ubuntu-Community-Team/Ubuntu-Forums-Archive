---
title: "Tremulous freezing!"
date: 2008-01-06
forum: Gaming &amp; Leisure
---

### Post by Chamelion on 2008-01-06
We have 2 computers with Ubuntu. Ubuntu Feisty and the other Edubuntu Gutsy.
both of them keep on freezing in the middle of Tremulous game play. Gutsy can at least be re started with alt, controll back. I have to turn of Feisty with power button.
 This seems to be some sort of bug. Does anybody know a fix? It still is playable but very annoying. Thanx in advance.

---

### Post by BreathEasy on 2008-01-06
Both computers? Well that sucks. Do they both use similiar graphics cards? Is Compiz Fusion running on both? What version of Tremulous are you running, the latest (1.1)?

There must be some similiarity between the two machines for such freezing to occur on seperate computers, and since I've played Tremulous and not had freezing, I'm not sure sure it's a bug.

---

### Post by Chamelion on 2008-01-06
Gutsy is Nvidia GT8500 (256mb). Intel C2duo, 1.8 Gig.  Ram 1Gig 
Feisty:Nvidia GT8500 512mb Intel C2duo 3Gig. Ram 4Gig

---

### Post by hikaricore on 2008-01-06
How exactly did you install your video drivers?

Is there any strange terminal output before/when the game crashes?
(this can be seen by running the game from a terminal in non-fullscreen mode)

---

### Post by Chamelion on 2008-01-06
I used Envy. Yes I did forget to mention that the game is reduced to a small screen in the corner. I can see my desktop with the game in the corner. On Gutsy the actual game is still going. I can see everybody else still running around except that everything else is frozen.

---

### Post by BreathEasy on 2008-01-06
Arg, envy.

Envy installs the absolute latest drivers, although I've heard some problems with the newer NVIDIA drivers. I'd recommend clearing out the Envy-installed drivers if you can (hopefully Envy's uninstallation option still works), and then afterwards, use Ubuntu's restricted drivers manager in the System menu -> Administration -> Restricted Drivers Manager to install the known, stable and functional drivers.

---

### Post by stzasnail on 2008-01-06
Also, disable any desktop effects. I have had loads of trouble with Compiz/Beryl/Compiz Fusion and games(especially Tremulous). Including the problem you are describing. 

If you do not have them enabled, try using older Nvidia drivers(as earlier mentioned)

---

### Post by Chamelion on 2008-01-16
> I have had loads of trouble with Compiz/Beryl/Compiz Fusion and games(especially Tremulous). Including the problem you are describing.
Sorry about the late answer to this. That could explain the problems we have. We also are running Sabayon. Also lots of problems with some games. Including Sauerbraten on occasion. I run into problems disabling Compiz in Feisty and then enabling it again.
Are there any difficulties in Gutsy?

---

### Post by doug-M on 2008-01-16
I'm having exactly the same problem. The game ends up in a window in the upper left corner of the screen, mouse doesn't work, most keyboard input doesn't work. The game seems to be continuing but I can't control it.

Sorry no solution but I do have an easier way to recover.

Hit ctrl-alt-f1
You should end up at a text console login.
Login then do this command:
ps -ef | grep tremulous
The first number is the process id (pid), such as 29734, so kill that process with this command:
kill 29734

Then use ctrl-alt-f7 to get back to your normal desktop.

---

### Post by Chamelion on 2008-01-16
If this is a bug, how and where could this be reported? I was just getting some hope for games in Linux. I still reserve a small part of a hard drive for XP just for playing games. I liked the few games I could find for Linux.
This sort of thing is a setback for Linux.:(

---

### Post by Cappy on 2008-01-16
> **doug-M said:**
> I'm having exactly the same problem. The game ends up in a window in the upper left corner of the screen, mouse doesn't work, most keyboard input doesn't work. The game seems to be continuing but I can't control it.

Sorry no solution but I do have an easier way to recover.

Hit ctrl-alt-f1
You should end up at a text console login.
Login then do this command:
ps -ef | grep tremulous
The first number is the process id (pid), such as 29734, so kill that process with this command:
kill 29734

Then use ctrl-alt-f7 to get back to your normal desktop.

You should try this: [http://ubuntuforums.org/showthread.php?t=656720](http://ubuntuforums.org/showthread.php?t=656720)
or possibly turning off compiz by using ```
metacity --replace
```

---

### Post by gsiliceo on 2008-01-18
If you disable your screensaver, the problem goes.

---

