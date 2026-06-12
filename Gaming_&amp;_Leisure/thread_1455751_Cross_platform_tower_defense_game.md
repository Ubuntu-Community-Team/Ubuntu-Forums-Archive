---
title: "Cross platform tower defense game"
date: 2010-04-16
forum: Gaming &amp; Leisure
---

### Post by OgreProgrammer on 2010-04-16
This is my friends Tower defense game called Target Defense. Needless to say its free.

You can play it in your browser or download an executable file for linux, OSX or windows. 

Here is the link. [http://www.targetdefense.com/](http://www.targetdefense.com/)

If you have any thing to say(nice I hope) to him, his email is at the bottom of the targetdefense.com page, or leave it here and I will pass it on.

---

### Post by myromance123 on 2010-04-16
Hey it looks interesting, really neat how you have a Linux version too.

 I'm downloading it now :)
I'll let you know how it goes~

EDIT: Hmm can't get it running ...
Here's what the terminal says:
```
ismail@ismail-desktop:~/Desktop/TargetDefense$ ./TargetDefense
FullScreen API: Warning, OPENGL Support is experimental! 
Keep checking http://www.superduper.org/processing/fullscreen_api/ for updates!

```

---

### Post by OgreProgrammer on 2010-04-16
Thanks for trying it myromance123. 

Were you unable to play it in your browser as well? It should work equally well(haha, hopefully better) there.

---

### Post by myromance123 on 2010-04-17
Hmm well I had to install the sun-java6-plugin from synaptic before it would load on any of my browsers. When it did load it would just have a blue P logo on the top left and everything else was white.
 Now today it says there is an error since I installed this java console add-on for Firefox.

 Here's what the console says:
```
----------------------------------------------------
c:   clear console window
f:   finalize objects on finalization queue
g:   garbage collect
h:   display this help message
l:   dump classloader list
m:   print memory usage
o:   trigger logging
q:   hide console
r:   reload policy configuration
s:   dump system and deployment properties
t:   dump thread list
v:   dump thread stack
x:   clear classloader cache
0-5: set trace level to <n>
----------------------------------------------------


java.lang.NullPointerException
	at com.sun.opengl.util.JOGLAppletLauncher.start(JOGLAppletLauncher.java:404)
	at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1639)
	at java.lang.Thread.run(Thread.java:619)
Exception: java.lang.NullPointerException
java.lang.NullPointerException
	at com.sun.opengl.util.JOGLAppletLauncher.start(JOGLAppletLauncher.java:404)
	at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1639)
	at java.lang.Thread.run(Thread.java:619)
Exception: java.lang.NullPointerException
```

Basically, its still just stuck at the P logo. Let me know if there is a fix yeah, I'm really itching to play it :)

PS: I'm using Ubuntu 10.04 Beta 2

---

### Post by Aped on 2010-04-17
I downloaded it on my laptop (Karmic) with some pretty unstellar specs and it runs decently. Spits out a few errors, I can paste those if you want. 

Main complaint is that it's HARD. I can't get past level 10, personally.

---

### Post by OgreProgrammer on 2010-04-17
> **myromance123 said:**
> 
PS: I'm using Ubuntu 10.04 Beta 2

Ok, I am going to to install 10.04 beta. Downloading it now.

I'm still running 9.10 and it worked for me, though I needed a 64 bit version outside the browser. You are using 32 or 64 bit?

I asked him to give me the source and I compiled a 64 bit version which you can get here:
[http://dl.dropbox.com/u/3735901/Target%20Defense-linux-64bit.tar.bz2]("http://dl.dropbox.com/u/3735901/Target%20Defense-linux-64bit.tar.bz2")

---

### Post by OgreProgrammer on 2010-04-17
> **Aped said:**
> I downloaded it on my laptop (Karmic) with some pretty unstellar specs and it runs decently. Spits out a few errors, I can paste those if you want. 

Main complaint is that it's HARD. I can't get past level 10, personally.

Thanks for trying it Aped. Its a little hard at first, but you have to micromanage your towers more than most tower defense games. 

I'll pass on the errors if you post them.

---

### Post by myromance123 on 2010-04-17
I'm running a 32-bit system. All my systems are sadly 32-bit..
 
 Really can't wait to play it, let me know how it goes for you :)
Thanks for getting back

---

### Post by OgreProgrammer on 2010-04-17
I finally got 10.04 installed, though I did 64 bit. I need to set some more stuff up however, but I havent forgotten you.

---

### Post by OgreProgrammer on 2010-04-17
DST, the author is having openGL problems too now. It seems there is a problem with the libraries he is using. So that might be the source of it.

---

### Post by myromance123 on 2010-04-18
Thanks for getting back to me, if there is a fix or new version just let me know yeah :)
 
 I'll check back often.

---

### Post by OgreProgrammer on 2010-04-18
> **myromance123 said:**
> Thanks for getting back to me, if there is a fix or new version just let me know yeah :)
 
 I'll check back often.

You are welcome. I think I recognise your avatar from the LA Vida thread here at ubuntu forums. You are watching that too, right?

---

### Post by myromance123 on 2010-04-19
I'm participating in that :D

 I helped design the new website, although it is very basic :P

---

### Post by Aped on 2010-04-20
```
FullScreen API: Warning, OPENGL Support is experimental! 
Keep checking http://www.superduper.org/processing/fullscreen_api/ for updates!
==== JavaSound Minim Error ====
==== Don't know the ID3 code TSSE

do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.
==== JavaSound Minim Error ====
==== Don't know the ID3 code TSSE

==== JavaSound Minim Error ====
==== Couldn't rewind using reset (Resetting to invalid mark), will try reloading the file.

==== JavaSound Minim Error ====
==== Don't know the ID3 code TSSE

==== JavaSound Minim Error ====
==== Don't know the ID3 code TSSE

==== JavaSound Minim Error ====
==== Don't know the ID3 code TSSE

==== JavaSound Minim Error ====
==== Don't know the ID3 code TSSE

==== JavaSound Minim Error ====
==== Couldn't rewind using reset (Resetting to invalid mark), will try reloading the file.

```

Almost all the same thing.

---

### Post by OgreProgrammer on 2010-04-23
Thats very strange to see the full screen error message. I uncommented my copy of the source and got an error informing me that I didnt have that library installed. So its strange that it comes up.

However, that did not fix things for the minim library error. I went to find an update for that library but it seems I have the most recent. 

Currently the game runs for me with no problems through the IDE, though I see a singular error

==== JavaSound Minim Error ====[FONT=monospace]
[/FONT]==== Don't know the ID3 code TSSE

as well as a log file which reports:

# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0xebaa447f, pid=3691, tid=3956308848
#
# JRE version: 6.0_16-b01
# Java VM: Java HotSpot(TM) Client VM (14.2-b01 mixed mode linux-x86 )
# Problematic frame:
# C  [libGL.so.1+0x6947f]
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.

So the bug is likely upstream in java or openGL This leaves me at a loss for what to do.

---

### Post by myromance123 on 2010-04-23
I just retried playing the game on the site itself after updating Ubuntu Beta 2 and its awesome!

 The only things I think that are lacking are:
1. Boss Levels
2. Sounds for destructions
3. Laser beam sounds of sorts

 If there are Boss Levels, I couldn't tell. There was one level with an enlarged "creep" but I wasn't sure if it was a boss.
I managed to reach Wave 37 :D
 That was really fun, I hope this game continues to progress and mature :)

Also, I was unable to upgrade my damage towers. Not sure why. The maximum level of towers being at 6 is kind of low too.

---

### Post by OgreProgrammer on 2010-04-23
I'm very happy you got it working. :)

1. Those big creeps at the beginning of every 5th level are bosses. They will actually heal if you are not attacking them. You'll get a bonus for eliminating them, and you can select +3% on your cash multiplier, or a bonus to remaining lives. 

2. Thats right! There are no destruction sounds. I dont know why I didnt notice before. I'll mention that.

3. I think he had beam sounds at one point, but there gets to be so many lasers that it overflows the buffer, making it hard to sync the sounds. I'll ask about that too. Hes improved his skills a lot, so maybe he has worked out a way to provide that.

wave 37 is the end. I think he needs better win and lose screens myself.  I'd like more levels too. 

The damage towers only have a single level as they provide a multiplier to towers in their range. Since two(or more) can affect a tower, it gets insanely powerful, so I think that is the reasoning for a single level on them. I'd like to see more tower levels too. Upgrades in tower defense games never go far enough.

I'll pass word on about your review. I'm sure it will put a grin on his face. Thanks again, and I'll come back with more information.

---

### Post by myromance123 on 2010-04-24
Wow! I had no idea I had won the game :P
 I'm glad I could have contributed a review :D

Hope things go well and smoothly, I'll keep checking back ;)

---

### Post by OgreProgrammer on 2010-04-24
How many towers did you need to get to 37?

---

### Post by doorknob60 on 2010-04-24
It froze mt whole browser as soon as I clicked the link! I blame Java though, since Java always does crap like that :P

EDIT: Tried it again and then it was fine. Why is Java so messed up on Linux? It freezes randomly, sound has problems, and Runescape HD doesn't work right :P

---

### Post by myromance123 on 2010-04-24
If I remember correctly, I used about 6-8 towers. Except for two, all were at the center to maximize range usefullness.

---

### Post by OgreProgrammer on 2010-04-24
Do you make use of the targeting types for individual towers?

---

### Post by Aped on 2010-04-25
Went back and replayed this, got to 37 quite easily. I hadn't realized just how potent upgrades were, and hadn't been using them (except the frost towers, for the range). 

Played challenge mode too and ended up with 300 or so lives left... got tough at the end, I think if I were to do it again it'd be all linked lasers and dmg boosters and a few frost tower things. 

All in all, pretty cool game. I don't know what those words (Strong Weak Far etc) mean or why you can click below them to light **** up, or why you can't upgrade damage booster towers, but it was still fun.

---

### Post by myromance123 on 2010-04-25
> I don't know what those words (Strong Weak Far etc) mean or why you can click below them to light **** up,
Yeah, at first I thought they are for the creeps but clicking them does nothing(yet).

> Do you make use of the targeting types for individual towers?
Sorry I don't understand what you're asking, targeting types?

Also note, I only used 1 of each tower except for the basic tower. I had 2 of those.

---

### Post by OgreProgrammer on 2010-04-25
Arg. Those button labels are a weak point in the design. 

Each tower stores a setting referring to its preferred target type.

Weakest/strongest means attack the creep within range that is weakest(in health) or strongest. Likewise near/far means to attack whoever is at that range. Note that far means whoever is farthest down the path. New/old picks a target based on the age of the creep. Each step they take increments an age counter. I never use those two as they closely correspond to near/far.

Click a tower(or have it selected) and then select an attack scheme from those. If no tower is selected, clicking those options will set the default for new towers. 

I think it would be better to have an indicator on each tower showing its targeting style.

---

### Post by OgreProgrammer on 2010-04-25
DST showed me the sprites for new creeps, so hes got something planned. If you have ideas for improvement, nows the time to say.

New towers too, with more upgrades.

---

### Post by Aped on 2010-04-25
Knowing this about the different 'preferences' I've been playing around and noticed that when set to Weak, turrets will simply not attack if all enemies in range have the same (full) hp.

---

### Post by myromance123 on 2010-04-26
I just played it again and this time I tried the challenge mode. Wow that was hard. I survived with 322 lives. Lost the most on the last level.

 I was forced to use the 'weak' setting for the towers at the bottom because they were letting the destroyable creeps with little health through. I was amazed though, even with more than 20 linked lasers and power towers in the middle of them those towers did less than the other towers. The final damage was about 8k. Great for the first 6 levels, not so afterwards.
:)

 Maybe for Boss levels a text could appear on screen informing the gamer: "BOSS LEVEL".

---

### Post by ProDigit on 2010-05-19
Target Defense freezes after finishing a level or being dead.
It goes back to the main screen.
From there I can't do anything.
Killing the process in System Monitor (in Ubuntu 10.4) does make it disappear out of the processes list, but the window is still present.

Any tips on how to close the game without rebooting?

Thanks!


Edit:
It seems Java stays active, and I needed to kill Java to close the windows.
I have Azureus Vuze running on the background which might have used Java too; perhaps that is the reason of the java window not closing?

---

### Post by jpkotta on 2010-11-22
I have a 64-bit system, and I downloaded TargetDefenseLin64.tar.bz2.  There's a bunch of .so's in there, but they're all 32-bit.  Trying to run the game gives "UnsatisfiedLinkError: wrong ELF class: ELFCLASS32".  I installed the libjogl-jni package and copied libgluegen-rt.so, libjogl.so, and libjogl_awt.so to the TargetDefense directory, and it worked.

---

### Post by hiruko on 2011-10-31
> **jpkotta said:**
> I have a 64-bit system, and I downloaded TargetDefenseLin64.tar.bz2.  There's a bunch of .so's in there, but they're all 32-bit.  Trying to run the game gives "UnsatisfiedLinkError: wrong ELF class: ELFCLASS32".  I installed the libjogl-jni package and copied libgluegen-rt.so, libjogl.so, and libjogl_awt.so to the TargetDefense directory, and it worked.

Whith that worked for me ( Ubuntu 11.10 amd64)
Thanks

---

### Post by scatcat1 on 2012-02-06
started up first try with no issues. im on fairly old computer too. awesome game, nice graphics. easy to learn hard to master. the key is upgrade, upgrade, upgrade. 2 things i would improve is the buy tower and tower control menus they should auto hide and not just go opaque. also 8x is not fast enough what about 12 or 16x. level editor is nice touch. all in all worth the download id give it 3.5 of 5.

---

### Post by kriltos on 2012-02-08
Hi there i just downloaded the TargetDefence MX 32bit version for linux, i'm stuck on how to install it. any idea what the terminal commands i need to input are?

P.s: i'm on Ubuntu 11.10 if that makes any difference.

---

### Post by Spartanis on 2012-02-19
> **kriltos said:**
> Hi there i just downloaded the TargetDefence MX 32bit version for linux, i'm stuck on how to install it. any idea what the terminal commands i need to input are?

P.s: i'm on Ubuntu 11.10 if that makes any difference.

Open the downloaded .zip file, copy the folder wihtin it to anywhere.. Go to that folder and locate the file "TARGETDEFENSEMX" 

right click it.. and select PROPERTIES

Select PERMISSIONS tab and check ALLOW EXECUTING FILE AS PROGRAM

Click CLOSE button

Double click the same file.. HIT RUN button.. 

Hope this helps :)

---

### Post by Dlambert on 2012-02-19
Looks very nice!

---

### Post by neuman1812 on 2012-04-28
Just Started playing this after doing a google search for "Tower Defense Linux"   This thread was the first result.  Great Game


Quick question: Im running Ubuntu 10.04 64bit with TDMX 64bit.   Does it have a full screen mode?

---

