---
title: "what gives?  None of these games I find for linux work."
date: 2007-07-26
forum: Gaming &amp; Leisure
---

### Post by xl_cheese on 2007-07-26
I've tried installing about a dozen games today.    No success.

Some won't build.  Some will build but make install does nothing.

Others attempt to run but hose my screen.  I have to do "cnrl alt backspace" to get out.  Then Ubuntu will refuse to log me back in.  It hangs.  gotta reboot.

I found one game that has worked- amenance.  However, I didnt' have to compile it.  Just clicked a file and it ran.  

Argh.

---

### Post by tgm4883 on 2007-07-26
It would help if you said what games these were and where you got them

---

### Post by xl_cheese on 2007-07-26
one example.  I got the deb file from here:
[http://www.parallelrealities.co.uk/starfighter.php](http://www.parallelrealities.co.uk/starfighter.php)

I installed it, but can't figure out how to launch it.  there was no icon or any readme files.


 I found the same game in the repo,  starfighter,  installed it and when I click the menu icon to launch nothing happens....

maelstrom from the repo
irrlamb
poopmup
nimbus
stp
formido

and others I have already removed from my trash.

---

### Post by xl_cheese on 2007-07-26
openarena from the repo:  Screen when black after clicking the menu icon.

---

### Post by DoktorSeven on 2007-07-26
Regarding Starfighter, do you have a PowerPC based PC?  That's the only Debian package I saw on the page you linked.  If you don't have a PPC computer then the Debian package shouldn't install, or if it did, shouldn't run.  The RPM for x86 might work if you have a standard Intel/AMD PC; you can run it through alien (**sudo apt-get install alien** then **sudo alien starfighter-1.1-1.i586.rpm** from wherever you downloaded it, and **dpkg -i *filename***, filename being the file Alien created), providing you have all the requirements.  **starfighter** from a terminal prompt should launch the game.

Some things do require a bit of trickery or knowledge like this to install -- not all games for Linux are as easy to install as Windows games, but you do get used to it.

---

### Post by DoktorSeven on 2007-07-26
> **xl_cheese said:**
> openarena from the repo:  Screen when black after clicking the menu icon.

Do you have 3d drivers enabled? (Go to a terminal and type: **glxinfo | grep direct**; it should come back "direct rendering: Yes".  If it says "No" then you'll have to enable 3d drivers; search the forums, the Ubuntu wiki, or Google for information on how to do that with your card.)

---

### Post by xl_cheese on 2007-07-26
> **DoktorSeven said:**
> Do you have 3d drivers enabled? (Go to a terminal and type: **glxinfo | grep direct**; it should come back "direct rendering: Yes".  If it says "No" then you'll have to enable 3d drivers; search the forums, the Ubuntu wiki, or Google for information on how to do that with your card.)

Thanks for the help.  It shows I do have direct rendering enabled.

---

### Post by xl_cheese on 2007-07-26
nexuiz from the repo:  able to launch to a screen that does nothing but say loading...

---

### Post by xl_cheese on 2007-07-26
tremoulous from the repo:  Nothing but a black screen.

Once again after having to cntrl alt backspace I get to my login screen, but the system freezes on login.  I notice there is no sound when arriving at the login prompt.

---

### Post by xl_cheese on 2007-07-26
frozen bubble from the repo:  Nothing happens after clicking the menu icon.

Can someone else confirm whether these games work or not?  Is it my system?

---

### Post by Steveway on 2007-07-26
They all work here.
Post your System-Specs.

---

### Post by xl_cheese on 2007-07-26
dell e521
amd X2 2.2GHz
2Gb memory
8600 gt video card.

I don't think my system should have trouble playing them.

---

### Post by xl_cheese on 2007-07-26
Maybe these are related issues on my system?

[http://ubuntuforums.org/showthread.php?t=509715](http://ubuntuforums.org/showthread.php?t=509715)

What a pain in the neck!

---

### Post by DoktorSeven on 2007-07-26
The best thing is to try running the games from the terminal and paste any relevant output here to diagnose the problem.  You can look at the menu editor to see what command launches each (as a help, **frozen-bubble** lanuches Frozen Bubble).

---

### Post by azraelck on 2007-07-26
What is your system? I have Nexiuz, Frozen Bubble, Tremulous, and OpenArena, and all of them work fine on my system. I don't know about the others, as I haven't got them installed. 

Have you tried to run them in the terminal, and see what messages if any it gives out?

---

### Post by xl_cheese on 2007-07-27
I ran barrage from the command line.

```
wes@Dork-Ubuntu:~$ barrage
BARRAGE v1.0.2
Copyright 2003-2005 Michael Speck (http://lgames.sf.net)
Released under Gnu GPL
---
main loop delay: 0 ms

```

Nothing happened.  The process exists tho.

```
7942 pts/3    00:00:00 barrage
```

Thanks for the help.

---

### Post by azraelck on 2007-07-27
Is that a dual core or 64bit processor? Maybe there's some lingering issues in those games with that processor setup. It could be your video card isn't yet properly supported (I don't know, since I have the older 7600GT).

---

### Post by BigSilly on 2007-07-27
I don't think your video card is supported yet. A mate of mine had all sorts of problems just trying to install Ubuntu on his brand new PC with a 8800GTS card, and he ended up abandoning it until the next release. I'm sure I read here somewhere that the developers will be supporting these cards with the next release.

For my part I can confirm that many of the games you list work fine on my PC. I have OpenArena, Frozen Bubble, Alien Arena, Glest and an absolute ton more, all working great.

---

### Post by cogadh on 2007-07-27
What video driver are you actually using for that card? The default "nv" driver does have some limited direct rendering support (it will report "direct rendering: yes"), but it generally does not work well for games. You should install the nvidia-glx driver or probably the nvidia-glx-new driver to get games running properly.

---

### Post by darksidedude on 2007-07-27
well it depends on you card, even if direct render is on, some games wont run,

i think the code for the gears test is this , but not shure give it a shot:confused:

```
 glxgears -info 
```

---

