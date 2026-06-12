---
title: "znes problems"
date: 2007-10-09
forum: Gaming &amp; Leisure
---

### Post by ljonesj on 2007-10-09
ok i start znes it comes up to a black screen and then goes off right after that

---

### Post by acoustibop on 2007-10-09
So, which version of ZSNES is this, ljonesj, and how did you install it?

---

### Post by ljonesj on 2007-10-10
from the repositores and it was apt-get install and it was from gutsy gibson beta too

---

### Post by acoustibop on 2007-10-10
So, which version is it?  I'm not using the Gutsy repositories yet.

---

### Post by disturbedite on 2007-10-10
version in gutsy is 1.510-1.

try launching from command line and post the result.

---

### Post by ljonesj on 2007-10-12
what is the command for command line i use sudo znes no dice

---

### Post by FranMichaels on 2007-10-12
> **ljonesj said:**
> what is the command for command line i use sudo znes no dice

zsnes! :razz:

```
zsnes
```

I don't mean to pick on you for the spelling, it is just that it matters when it is the command to launch it too...
Also, if you had the older version before, you might need to remove the config files, which would be in
~/.zsnes 
Don't delete the whole directory though, the .srm and .zs* have all your saves in there.

:)

---

### Post by antmangaka on 2007-10-12
hello, i also have a problem with zsnes
I installed yesterday it and was playing fine
but today
```
minyie@minyie-desktop:~/Installers/pcsx2$ zsnes
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
Could not set 1280x960-GL video mode.
minyie@minyie-desktop:~/Installers/pcsx2$ sudo zsnes
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
ManyMouse: 2 mice detected.
Using ManyMouse for:
Mouse 0: USB Mouse
Mouse 1: Macintosh mouse button emulation
Could not set 512x448 video mode: No available video device
minyie@minyie-desktop:~/Installers/pcsx2$ 

```

---

### Post by FranMichaels on 2007-10-12
> **antmangaka said:**
> hello, i also have a problem with zsnes
...

Hello, okay don't run zsnes with sudo, doesn't need root permission. The error is regarding video output.

```
gedit ~/.zsnes/zsnesl.cfg
```
or nano if your prefer to edit in the terminal

Find Video, and specifically change 
cvidmode=somevalue

If you like you can remove the file or rename it, and zsnes will make fresh settings for the video output. 

Did you change video drivers or something, since it seems that you had used opengl settings before... 
Which I do too... So something outside of zsnes must have changed I think...

Good luck :)

---

### Post by antmangaka on 2007-10-12
nope, haven changed the drivers :(

---

### Post by ljonesj on 2007-10-13
well i just installed the release canidate of gutsy and zsnes works fine now. something must have been wrong in the beta

---

### Post by sochbat on 2007-10-19
ZSNES is STILL not working for me.  What the deuce.

I've tried uninstalling it, and reinstalling via Synaptic, but still, no dice.

This also came up.

> ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
Creating link /home/sochbat/.kde/socket-SochBAT.
can't create mcop directory


---

### Post by Massive Brain on 2007-10-19
Try using SDL audio output. Works for me.

---

### Post by dfreer on 2007-10-19
> can't create mcop directory

Sounds like a permissions issue in your home directory. Have you by any chance backed up/restored your home directory? It may be that you didn't copy things correctly, unfortunately I'm not sure how to resolve this issue. Your home folder should have 755 permissions.

---

### Post by Depressed Man on 2007-10-19
Manually create the directories, seems to work for me.

---

### Post by chriswyatt on 2007-10-21
Where is this mcop directory supposed to be placed?  I tried placing it in .zsnes to no avail.

p.s. I freshly installed ZSNES onto a clean installation of Gutsy (final version)

This is my output:

```
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event9. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event8. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.
Creating link /home/chrisw/.kde/socket-chrisw-laptop.
can't create mcop directory
```

---

### Post by chriswyatt on 2007-10-21
Fixed all those polling errors by allowing read permissions :) , ZSNES still won't run though.

EDIT: It seems that if you run a KDE app before starting ZSNES it works!  I'm not yet sure if this is permanent, but I'm guessing it probably is :) .

---

### Post by dfreer on 2007-10-21
> **chriswyatt said:**
> Fixed all those polling errors by allowing read permissions :) , ZSNES still won't run though.

EDIT: It seems that if you run a KDE app before starting ZSNES it works!  I'm not yet sure if this is permanent, but I'm guessing it probably is :) .

Hmmm, I haven't had this issue when testing my packages before, maybe it's a issue specific to using the official debian package? Oh well, at least it's working for you guys!

EDIT: Yeah, the polling errors won't cause the emulator to crash, it's not that big of an issue unless you can't get your joystick to work.

---

### Post by kingmob on 2007-10-22
Hmm, i have the exact same problem. Has only appeared since I upgraded to gutsy. The polling error was easily fixed, but i cannot find out what the "mcop" error is.

---

### Post by FranMichaels on 2007-10-22
Okay, I just ran into this error on my sisters laptop. Doing as Depressed man says make the directory manually.

So for chrisw

```
mkdir /home/chrisw/.kde/socket-chrisw-laptop
```

Using my meager bash skills, this command should work for everybody. :razz:

**```
mkdir ~/.kde/socket-`hostname`
```**

---

### Post by BigSilly on 2007-10-22
I have this problem too. It's been filed as a bug from what I can tell, so hopefully there'll be some sort of fix coming shortly. The above commands didn't work for me unfortunately. :(

---

### Post by FranMichaels on 2007-10-22
Okay let me try again.

```

mkdir ~/.kde/socket-`hostname`
chown -hR `id -n -g` ~/.kde
chmod 755 -R ~/.kde 

```

How about that?

I didn't actually test this on my box, no .kde folder... Anyway, I've used the commands before. :biggrin:

Ideally, it will make the dir zsnes looks for. Make sure it's owned by your username, and that its permissions match those of the home folder.

:razz:

---

### Post by chriswyatt on 2007-10-24
Thanks, problem sorted now :) .  Seems that my suggestion was only a temporary fix.

---

### Post by mysticmatrix on 2007-10-25
> **chriswyatt said:**
> Fixed all those polling errors by allowing read permissions :) , ZSNES still won't run though.

EDIT: It seems that if you run a KDE app before starting ZSNES it works!  I'm not yet sure if this is permanent, but I'm guessing it probably is :) .

Works for me. I start SMplayer b4 starting ZSNES

---

### Post by BigSilly on 2007-10-27
> **FranMichaels said:**
> Okay let me try again.

```

mkdir ~/.kde/socket-`hostname`
chown -hR `id -n -g` ~/.kde
chmod 755 -R ~/.kde 

```

How about that?

I didn't actually test this on my box, no .kde folder... Anyway, I've used the commands before. :biggrin:

Ideally, it will make the dir zsnes looks for. Make sure it's owned by your username, and that its permissions match those of the home folder.

:razz:

Ah haah! This worked for me! Thanks very much! It's a silly thing to go wrong though isn't it?

But nevertheless, cheers for the lesson in bash.

:)

---

### Post by FranMichaels on 2007-10-27
> **BigSilly said:**
> Ah haah! This worked for me! Thanks very much! It's a silly thing to go wrong though isn't it?

But nevertheless, cheers for the lesson in bash.

:)

Hey, I am very glad it worked :) 

It was a learning experience for me too. 

As for the nature of bugs, of all the things to go wrong with emulating hardware, directory permissions? Very unrelated indeed :razz:

P.S. I will submit this as an UbuntuForums How-To. Thank you for letting me know that it works! :)

---

### Post by herrdoktor330 on 2007-11-30
Since this thread is still rather live, I want to post an issue I'm having.

I can get zsnes to load on 7.04 feisty with zsnes  1.51. But when the program loads, it detects my controller, a mayflash PS2 control to USB adapter, without any hat controls. I'm using the Gnome Joystick configuration utility and it detects the hat switch and analog sticks fine. Any idea how to fix this? 

Here's my terminal readout:

```

ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check http://www.zsnes.com/ for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
Unable to poll /dev/input/event7. Make sure you have read permissions to it.
Unable to poll /dev/input/event6. Make sure you have read permissions to it.
Unable to poll /dev/input/event2. Make sure you have read permissions to it.
Unable to poll /dev/input/event5. Make sure you have read permissions to it.
Unable to poll /dev/input/event4. Make sure you have read permissions to it.
Unable to poll /dev/input/event1. Make sure you have read permissions to it.
Unable to poll /dev/input/event3. Make sure you have read permissions to it.
Unable to poll /dev/input/event0. Make sure you have read permissions to it.
ManyMouse: 0 mice detected.

Audio Opened.
Driver: Advanced Linux Sound Architecture (ALSA) output
Channels: 2
Rate: 32000

Device 0 WiseGroup.,Ltd MP-8866 Dual USB Joypad
  6 axis, 12 buttons, 0 hats, 0 balls


```

And as always... thanks to all for any help on this one.

---

### Post by acoustibop on 2007-11-30
"I'm using the Gnome Joystick configuration utility," herrdoktor330?  AFAIK there isn't a joystick configuration utility included in Gnome.  My guess is you've installed jscalibrator, which is likely the cause of your problem.  It seems to disable the directional controls of controllers, while reporting that they're working perfectly.

I'd suggest removing jscalibrator completely, including its configuration.  You may have to restart X as well, or even reboot, to make sure your controller is properly re-detected.

---

### Post by 2manydrugsago on 2008-01-22
When I first installed zsnes with add/remove programs it came up fine in windowed mode. Inside that window I changed it to go full screen(don't remember how) Now it opens the screen goas black for half a second and then it closes. I have uninstalled it with A/R and then reinstalled it, same result. I read on the forums about video output so I  did the      gedit ~/.zsnes/zsnesl.cfg     and changed the video values to very low settings and it does the same thing.
Anyone help me?
I am using a old gateway 700 with 128 of ram and a vodoo 3 3000 vid card with 16 megs of ram on it.

---

### Post by FranMichaels on 2008-01-23
Try running zsnes from terminal. If it shows anything with the word mcop in it, look at the link in my sig for the solution.

If it's a configuration problem, make sure the video options you chose in zsnesl.cfg don't have full (if fullscreen mode is really the problem... I don't think so though...) next to them.

If neither of the above work, then rename or delete zsnesl.cfg 
Zsnes will have a fresh start.

:)

---

### Post by mastahkillah666 on 2008-02-10
For those of you who are stuck with the 'mcop' problem, instead of creating a directory you can create a link of the socket to the /tmp directory and pointing it to null by typing in a terminal  8)  :

```
lnusertemp socket >/dev/null
```You can also create such "links" not only for kde resource sockets, but also for its resource cache (lnusertemp cache >/dev/null) and its tmp (lnusertemp tmp >/dev/null).

Hope it 'helps' (even if the problem is indeed resolved with mkdir)  ;)  .

---

