---
title: "Pso:bb"
date: 2007-01-25
forum: Gaming &amp; Leisure
---

### Post by Pobega on 2007-01-25
I've been trying to get PSOBB working under Xubuntu, but it's giving me some trouble.

I know Wine and Cedega have trouble with nProtect, so I tried using an exe that disables it. That didn't seem to want to run. I ran it with wine using> wine _PsoBB.exe 1095189843That skipped right past Gameguard and seemed to work, the game flickered in and then out. So I figured if I could get this to work in Cedega the way it works in Wine I may be able to play PSO!

So I ran> cedega _PsoBB.exe 1095189843, but I noticed that it just doesn't do anything. It sits at the terminal and doesn't exit until I press Ctrl+C.

The exe I'm running is a modded exe, so I can't run it from within the Transgaming GUI (I am not sure how to put my own exes in the games list), and cedega won't run through the termina. Does anyone have any ideas what I can run in the terminal to get the executable running? (The 1095189843 is the runtime parameter for the executable)

---

### Post by jural on 2007-02-07
The exe that disables GG for PSOBB needs Dotnet 2.0 installed.
Tried to install dotnet, but needed windows installer and that needs ie 5.1 or greater. trying to install ie 6 or 5.1 says a newer version is already installed.

---

