---
title: "gfceu : Can't configure keyboard settings + Dragon Warrior IV runs bad"
date: 2008-07-16
forum: Gaming &amp; Leisure
---

### Post by Ishimaru Chiaki on 2008-07-16
Hello everyone.  I'm new to this forum, but I installed Ubuntu on my PC two months ago, and up to now, I used to go to the French Ubuntu forum for support since French is my mother tongue.  But today, I have some problems I couldn't solve on the French side, so I come here to seek help from you.

As an old school RPG gamer, I used to play NES game with NESticle when I had my previous PC (a Pentium 120 with win95) and I really loved this emu since it used to run Dragon warrior IV fine.  Then I had to change PC four years ago (system crash after 7 years of use) for my current one who came with winXP and then, Nesticle couldn't run correctly (black screen whatever the resolution).

Now I am on Ubuntu since May 15 and I recently installed gfce ultra, but I have two problems.

- First and major problem : I don't have any joystick, so I want to use my keyboard to play games, but whatever the "Gamepad" button I click, I have this : [View screenshot]("http://img.photobucket.com/albums/v381/ladykatt/bug-gfceu.png")

Then, the program is freezed and I have to use the **kill -9 <process number>** command in order to close this blank window and come back to gfceu's interface.

Does anyone who doesn't have any joystick has the problem ?

- Second and more minor problem : It doesn't run Dragon Warrior IV well, the graphics are distorted and I can't distinguish anything, while I don't have this problem with the three previous Dragon Warrior games.  The same DW4 ROM used to run well on NESticle.

I didn't test other NES emulators for Linux, since gfceu is the only one available in .deb packages, and I hesitate to test other emulators without knowing if they run DW4 fine.

Thanks in advance.

Ishimaru

---

### Post by eragon100 on 2008-07-16
try ZSNES from add/remove applications

It's a great NES emulator with tons of features! :wink:

---

### Post by dfreer on 2008-07-16
> **eragon100 said:**
> try ZSNES from add/remove applications

It's a great NES emulator with tons of features! :wink:

...Except it's not a NES emulator :( Honestly... *shakes head*

Also, IIRC GFCEU had a bug where you had to input the key multiple times before it would let you move on to the next one. When configuring your gamepad and that window pops up, try pressing the key you want to map to the "A" button a couple of times. It should move on to configure the next button.

If that doesn't work, try running gfceu from the Terminal, and then configure your gamepad to see if it gives you any meaningful error messages.

---

### Post by Ishimaru Chiaki on 2008-07-16
uh... I didn't notice the texts in the terminal when I tried to set the gamepad...

Now, when I try to set the keys, I have an error message at the end.

Here's what I have in the terminal (note : I launched via the terminal, but I used the GUI to go to Input, then in "Gamepad#1")
I tried several times because I'm not quite used to this way of setting.
```
caroline@caroline-desktop:~$ gfceu
gfceu message:  Using: /usr/games/fceu
gp1_button
gfceu message:  Command: /usr/bin/aoss /usr/games/fceu -sound 1 -fs 0 -opengl 0  -inputcfg gamepad1 /dev/null

Starting FCE Ultra 0.98.12...
GamePad #1: A (1)
GamePad #1: A (2)
GamePad #1: A (3)
GamePad #1: B (1)
GamePad #1: B (2)
GamePad #1: SELECT (1)
GamePad #1: SELECT (2)
GamePad #1: SELECT (3)
GamePad #1: START (1)
GamePad #1: START (2)
GamePad #1: UP (1)
GamePad #1: UP (2)
GamePad #1: DOWN (1)
GamePad #1: DOWN (2)
GamePad #1: LEFT (1)
GamePad #1: LEFT (2)
GamePad #1: RIGHT (1)
GamePad #1: RIGHT (2)
GamePad #1: Rapid A (1)
GamePad #1: Rapid A (2)
GamePad #1: Rapid B (1)
GamePad #1: Rapid B (2)
Loading /dev/null...

An error occurred while loading the file.
   gp1_button
gfceu message:  Command: /usr/bin/aoss /usr/games/fceu -sound 1 -fs 0 -opengl 0  -inputcfg gamepad1 /dev/null

Starting FCE Ultra 0.98.12...
GamePad #1: A (1)
GamePad #1: A (2)
GamePad #1: B (1)
GamePad #1: B (2)
GamePad #1: SELECT (1)
GamePad #1: SELECT (2)
GamePad #1: START (1)
GamePad #1: START (2)
GamePad #1: UP (1)
GamePad #1: UP (2)
GamePad #1: DOWN (1)
GamePad #1: DOWN (2)
GamePad #1: LEFT (1)
GamePad #1: LEFT (2)
GamePad #1: RIGHT (1)
GamePad #1: RIGHT (2)
GamePad #1: Rapid A (1)
GamePad #1: Rapid A (2)
GamePad #1: Rapid B (1)
GamePad #1: Rapid B (2)
Loading /dev/null...

An error occurred while loading the file.



```

EDIT : It finally seemed to have worked, I am playing Dragon Warrior 3 right now and the keys I entered are working.

Now, all is left is the DW4 issue.

---

### Post by acoustibop on 2008-07-16
You could try [Mednafen]("http://mednafen.sourceforge.net/"), Ishimaru Chiaki - it emulates a number of platforms, including the NES and Sega Master System - the only emulator I've found for Linux that emulates SMS satisfactorily.

It's command line-only, but I don't find this a problem; just click on a game it can play and it opens the game automatically.

Best place to get it is the [CinnamonPirate]("http://repository.cinnamonpirate.com/") repository; they generally have the most up-to-date version.  I think it may also be in the Ubuntu repositories, but I think that's an old pre-SMS version.

---

### Post by Ishimaru Chiaki on 2008-07-16
I tested DW4 with Mednafen and the rendering is even worse, I have only big patches of colors while I was having clouds of small pixels under gfceu.

For those who would want to test by themselves, I'm available by PM for more details.

---

### Post by DoktorSeven on 2008-07-16
> **Ishimaru Chiaki said:**
> 
```
caroline@caroline-desktop:~$ gfceu
gfceu message:  Using: /usr/games/fceu
gp1_button
gfceu message:  Command: /usr/bin/aoss /usr/games/fceu -sound 1 -fs 0 -opengl 0  -inputcfg gamepad1 /dev/null

Starting FCE Ultra 0.98.12...
GamePad #1: A (1)
GamePad #1: A (2)
GamePad #1: A (3)
GamePad #1: B (1)
GamePad #1: B (2)
GamePad #1: SELECT (1)
GamePad #1: SELECT (2)
GamePad #1: SELECT (3)
GamePad #1: START (1)
GamePad #1: START (2)
GamePad #1: UP (1)
GamePad #1: UP (2)
GamePad #1: DOWN (1)
GamePad #1: DOWN (2)
GamePad #1: LEFT (1)
GamePad #1: LEFT (2)
GamePad #1: RIGHT (1)
GamePad #1: RIGHT (2)
GamePad #1: Rapid A (1)
GamePad #1: Rapid A (2)
GamePad #1: Rapid B (1)
GamePad #1: Rapid B (2)
Loading /dev/null...

An error occurred while loading the file.
   gp1_button
gfceu message:  Command: /usr/bin/aoss /usr/games/fceu -sound 1 -fs 0 -opengl 0  -inputcfg gamepad1 /dev/null



```

Just for reference for the future (and anyone else investigating this), this is normal behavior when you configure your controller.  For the frontend to configure your input separately from loading and running a game, it has to run FCEU with a dummy game since it expects at least something, so it uses /dev/null (a dummy file that is sort of like a black hole, nothing comes out, everything goes in and is lost forever), thus the "error" that it can't load the file.

This is normal behavior.

---

### Post by FranMichaels on 2008-07-21
> **Ishimaru Chiaki said:**
> I tested DW4 with Mednafen and the rendering is even worse, I have only big patches of colors while I was having clouds of small pixels under gfceu.

For those who would want to test by themselves, I'm available by PM for more details.

Rendering as far as I know it's not problematic in mednafen. If DW4 doesn't look like this, your ROM image is likely bad.

If I have misunderstood your issue, feel free to PM me.

---

### Post by The Avatar of Time on 2008-09-17
> **DoktorSeven said:**
> Just for reference for the future (and anyone else investigating this), this is normal behavior when you configure your controller.  For the frontend to configure your input separately from loading and running a game, it has to run FCEU with a dummy game since it expects at least something, so it uses /dev/null (a dummy file that is sort of like a black hole, nothing comes out, everything goes in and is lost forever), thus the "error" that it can't load the file.

This is normal behavior.

Thanks a million for this bit of advice. I have been trying for quite some time to configure my game pad on gfceu and kept getting the /dev/null message. I never even bothered to see if it worked, I took it as a failure and googled and tried repeatedly to reconfigure it. 

Sure enough, it had worked all along just as you say. I feel a bit simple minded now for not just testing to see if it worked... 

Anyhow, thank you kindly.


***I don't think it's really my place to say, but wouldn't it make a bit of sense to go ahead and have some sort of "It worked!" message to let you know the error was normal? Perhaps it's obvious to most, but just a thought.

***I suppose it doesn't matter but I don't seem to see a 'Thanks' icon anywhere on your post to use to thank you. In fact FranMichaels is the only poster with a 'Thanks' icon. Odd...

---

