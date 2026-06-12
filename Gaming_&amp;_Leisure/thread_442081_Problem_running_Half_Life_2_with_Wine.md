---
title: "Problem running Half Life 2 with Wine"
date: 2007-05-13
forum: Gaming &amp; Leisure
---

### Post by catinabox on 2007-05-13
I'm having a problem with Half-Life 2. When it loads it shows the blurry background of the main menu for a few seconds, then turns black and crashes. I used [this](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games) guide to install Steam and HL2, and use this as my startup script:
```
#!/bin/bash
WINEDEBUG=fixme-all wine C:/Program\ Files/Steam/Steam.exe -fullscreen \
    -width 1280 -height 1024 -applaunch 220 \
    -heapsize 512000 -console -novid -gl "$@"
```

This is the output from the terminal when I run the script:

```
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for context 0x1
err:systray:delete_icon invalid tray icon ID specified: 1d
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:mshtml:nsIOService_NewURI Could not get nsIWineURI: 80004002
err:mshtml:nsIOService_NewURI Could not get nsIWineURI: 80004002
err:mshtml:nsIOService_NewURI Could not get nsIWineURI: 80004002
err:mshtml:nsIOService_NewURI Could not get nsIWineURI: 80004002
```
I am running the 64-bit version of Feisty Fawn, also I have installed the driver documented [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") which made Enemy Territory, a native linux game, run fine, however HL2 is a much newer game so it's possible that it is a graphics card problem. I've only been using linux for a few days now so I'm pretty clueless.

---

### Post by aoanla on 2007-05-14
I've been having a similar problem with HL2 in 64bit Feisty, so it's possible we can go some way to diagnosing a problem together.

I find that omitting the "-console" switch from the Steam commandline enables me to get to the menu screen without the crash that you describe. With the "-console" switch, I get the same problem as you, although sometimes by pressing the ~, I can apparently bring down an "invisible console" on the black screen (only apparent from the change of my mouse cursor when I move over it) before I crash out.

However, on starting a new game, I manage to watch all of the G-man's initial monologue before the game crashes with a different DirectX error. If I specify "-dxlevel 80" to turn off DirectX 9 stuff, I manage to play about 30 seconds to a minute of game before the same crash happens. 

I'm using an ATI X1950 Pro with the latest fglrx drivers. I thought that they might be the problem, so I'm interested to know what graphics card you're using...

---

### Post by catinabox on 2007-05-15
My card is a X1300, but I'm thinking of getting a new one soon. I will try removing -console and setting the DirectX to version 8, and tell you how it goes.

---

### Post by ChaosNipples on 2007-07-23
What I would do is go into my bios and raise the AGP voltage a tad or get a better cooling system because when a game crashes  while playing that is usually a hardware or driver problem.

---

