---
title: "Again!  No sound..just at boot up not in Desktop"
date: 2006-03-18
forum: Desktop Environments
---

### Post by KiLLeR_WoMBaT on 2006-03-18
Okay everyone....how about some help here.  I've tried EVERY thing in a million threads and how-to's.  I've posted like five different threads and I can't get an answer or solution on any of them.  When I first installed (and re-installed) Breezy, my sound worked.  Now I only hear it at the login screen.  It has gone from the simple default login screen sound to double (kind of an echo of the sound) to now I hear the login sound four times!!!

Of course once I'm logged in...no sound.  The only thing I have done to this fresh install is run Automatix.  Nothing else.  And yes, the sound went away before I ran automatix; that is why I ran it.  I was trying to fix the sound issue.

I have an onboard sound chip...lspci gives this:

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

Here are some screenshots of the dialog boxes I'm given when trying to test sound and run xmms and bmp:

---

### Post by blkno1 on 2006-03-18
Something similar happened to me, turned out after upgrading some sound drivers that my volume muted somehow.  I went like two months with no sound and all it was was muted.

---

### Post by KiLLeR_WoMBaT on 2006-03-18
I checked that first off with alsamixer.  Not muted.

---

### Post by stalefries on 2006-03-18
Try this:
Go to System>Administration>User and Groups
Go to the Groups tab
Find "audio", select it and click Properties...
Make sure you are included in that group.

---

### Post by KiLLeR_WoMBaT on 2006-03-18
I tried that and there is no "audio" group listed.    How do you add an audio group and what would the settings be?  Here is a screenshot:

---

### Post by Sendervictorius on 2006-03-19
[QUOTE=KiLLeR_WoMBaT]I tried that and there is no "audio" group listed.    How do you add an audio group and what would the settings be?  Here is a screenshot:[/QUOTE]
You need to have the "show all users and groups" box checked!

---

### Post by KiLLeR_WoMBaT on 2006-03-19
Okay, thank you.  I see the audio group now and my user account is the only one in it.  I guess this is another dead end?

How can I get rid of EVERYTHING that has ANYTHING to do with audio and start over without reinstalling (like I have already done)?  Just after installing the sound works.  It's just when I start trying to add functionality like plugins, ATI driver, Java and such the sound dies.

Is their any log or something I need to look at or post so we can figure this out?

---

### Post by KiLLeR_WoMBaT on 2006-03-19
Bump...any help out there?

---

### Post by KiLLeR_WoMBaT on 2006-03-19
Nothing?  No One?  Come on.

---

### Post by KiLLeR_WoMBaT on 2006-03-20
Any help out there?

---

### Post by arnieboy on 2006-03-20
try running xmms with the OSS output driver. That might solve your problem.

---

### Post by RavenOfOdin on 2006-03-20
Is ESD running? :confused:

---

### Post by KiLLeR_WoMBaT on 2006-03-21
[QUOTE=arnieboy]try running xmms with the OSS output driver. That might solve your problem.[/QUOTE]

xmms comes up but will not play a song with ANY output driver.  No sound.

Again, I do get sound upon boot up at the login screen.  Of course now it is a quadruple drum beat instead of the single.  Kind of like it's playing the sound file four times in a row in quick succession.

---

### Post by KiLLeR_WoMBaT on 2006-03-21
[QUOTE=RavenOfOdin]Is ESD running? :confused:[/QUOTE]

How would I tell if it is running?

This is what I get when I killall esd:

daniel@WoMBaT-Laptop:~$ sudo killall esd
Password:
esd: no process killed
daniel@WoMBaT-Laptop:~$

---

### Post by arnieboy on 2006-03-21
try doing the following.. go to system --> preferences--> sound and **uncheck** "Sound for events". Now try restarting your computer..

---

### Post by RavenOfOdin on 2006-03-21
[QUOTE=KiLLeR_WoMBaT]How would I tell if it is running?

This is what I get when I killall esd:

daniel@WoMBaT-Laptop:~$ sudo killall esd
Password:
esd: no process killed
daniel@WoMBaT-Laptop:~$[/QUOTE]

If its not running, then that means you have to start it.
Type in:

esd&

---

### Post by KiLLeR_WoMBaT on 2006-03-21
[QUOTE=arnieboy]try doing the following.. go to system --> preferences--> sound and **uncheck** "Sound for events". Now try restarting your computer..[/QUOTE]

That is unchecked.  I did that way back when trying the different "How-To" posts.  What should I be looking at to try and find out what is causing it?  A certain log or something?

---

### Post by KiLLeR_WoMBaT on 2006-03-21
[QUOTE=RavenOfOdin]If its not running, then that means you have to start it.
Type in:

esd&[/QUOTE]

This is what I get:

daniel@WoMBaT-Laptop:~$ esd&
[1] 24400
daniel@WoMBaT-Laptop:~$ ALSA lib pcm_dmix.c:773:(snd_pcm_dmix_open) unable to cr eate IPC semaphore
daniel@WoMBaT-Laptop:~$

---

### Post by KiLLeR_WoMBaT on 2006-03-22
Still no sound.  However, it seems it is something to do with Automatix.  The sound only goes away after using it to install stuff.

I guess my ONLY recourse is to reinstall Breezy and DON'T use Automatix.  That means the headache of doing all that stuff manually.  Or use Automatix and install one thing at a time and see where the break is.  I only wish there was a better way to diagnose this problem without those extremes.

I'm still taking any help or solutions!

---

### Post by kaput on 2006-03-22
I've been having problems with the new -19 release of the kernel in Dapper. I've been having to boot to the -18 release to have working sound.

---

### Post by KiLLeR_WoMBaT on 2006-03-23
Screw dapper!  I'm still having problems with Breezy!!!

---

### Post by KiLLeR_WoMBaT on 2006-03-25
Okay, saw this on a different thread.

daniel@WoMBaT-Laptop:~$ cat /proc/asound/cards
0 [ICH5           ]: ICH4 - Intel ICH5
                     Intel ICH5 with ALC650F at 0xe8000c00, irq 17


Does this help anyone diagnose my problem?

---

### Post by linux_owns on 2006-03-26
What up dog,
Just to make sure its not something simple.
put your mouse in the right top over the sound emblem. Whats it say? I had a similar problem and it turns out all i had to do was right-click then pref. and scroll down to front instead of headphones or whatever it was on.

---

### Post by KiLLeR_WoMBaT on 2006-03-26
[QUOTE=linux_owns]What up dog,
Just to make sure its not something simple.
put your mouse in the right top over the sound emblem. Whats it say? I had a similar problem and it turns out all i had to do was right-click then pref. and scroll down to front instead of headphones or whatever it was on.[/QUOTE]

It says Master:100 percent

---

