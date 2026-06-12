---
title: "Valve Source games display problem"
date: 2008-12-29
forum: Desktop Environments
---

### Post by sgtrock on 2008-12-29
I'm hoping someone can help me figure this problem out.  It's been bugginng me for quite a while.  First, basic specs:

8.04 Kubuntu
x86 64 bit system.
Nvidia 9600 GT video card
2GB RAM

Wine version 1.1.10

I've been running wine for several years, so it's distinctly possible that I've got some leftover configuration information that's messing me up.  I've tried uninstalling and reinstalling to see if that would help.  No luck.

With that background, the symptoms:

1) Open Steam.
2) Log in normally.  All Steam displays, with the exception of the Flash based content on the Store tab, looks fine.
3) Select the "My Games" tab.  All content displayed properly.
4) Choose a game and launch.  Launching the game works correctly.

5a) Team Fortress 2:
5a1) Choose a server to connect.  Connects normally.
5a2) The introduction display, which I believe is simple HTML, shows a black rectangle instead of the content.
5a3) Hit 'Continue'.  Game loads normally.

5b) Left 4 Dead:
5b1) While the game launches normally and runs the intro movie correctly, something odd occurs when it finally gets to the menu display.  I see the moving background of zombies.  I hear all the sounds correctly.  The odd part is that while I see and hear all this stuff, I can't see the menu!

It gets a bit stranger.  If I just move the mouse pointer around the screen, I get the little click as I pass over approximately where the various menu items should be.  I think I have even managed to select one or two because the configuration of buttons sometimes seems to change.

Both of these games are ones that others have reported on AppDB at WineHQ as working with hardware configurations that are similar to mine.  My current tentative working hypothesis is that I've got a HTML rendering problem that is affecting both games.  

I thought I'd found the solution when I realized that wine-gecko was not installed.  Installing the latest version has not resolved the issue.

Does anyone know if I'm on the right track?  If so, what should I try?

If you think I may be off base, do you have any advice as to what steps I should take too investigate the problem?

TIA

---

