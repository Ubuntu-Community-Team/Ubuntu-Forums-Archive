---
title: "Little perfomance issue"
date: 2021-06-05
forum: Gaming &amp; Leisure
---

### Post by jcvardy on 2021-06-05
Hello there. I am currently using Ubuntu Studio, and everything's great so far, games on steam even run better than on windows (I don't have a gaming pc, so it is easy to notice on some games), but whenever I close a game and want to continue doing something else, I get an issue where it seems my pc is running at the usual speed, but my "screen" is actually choppy, or laggy. The FPS drops really, really low. Haven't tested if it is running exactly as fast as before opening the game besides the FPS, but I think it also does get some overall performance drop. Only solution I've found is rebooting the system. Again, it is Studio I'm using. Any ideas on why this might be happening?

---

### Post by TheFu on 2021-06-07
Have you tried logging out and logging in again?  That should re-initialize the GUI. No need to reboot.
Is it for all games or just specific one?
Is it for games only from steam or locally installed APT packaged games too?
Are these WINE or native Linux games?

I probably cannot help, since I only play Sudoku and similar games.

---

### Post by jcvardy on 2021-06-07
Well, Haven't tried reinitializing the GUI alone. Didn't know you could do that, heh. It's only steam games, both native and non-native (running with proton), since those are the only games I've tried. Less demanding application like KDEnlive, all the audio software don't generate the same issue. I have a game which runs worse in linux, much worse, even tho' it's native, than in windows. The rest tend to have a slightly better performance while in game.

---

### Post by mastablasta on 2021-06-08
> **jcvardy said:**
> . Less demanding application like KDEnlive, ...
:lolflag: this one can eat your CPU and ram for breakfast.

anyway check the processes running in the background. sometimes certain games would crash and continue to run in the background. usually this happens with wine. kill the process and you should get back to normal.

some native Linux games are bad ports and indeed do run much slower than they do on windows.

some windows games run noticeably better on linux. in my case that was Far cry 2.

with Steam make sure it is installed well and that it doesn't do any strange logging. it ate up whole disk by creating huge log file (few hundred GB) on my kids pc. we didn't notice it since we were away and he left the PC on. anyway we removed it, updated steam and it hasn't happened since.

---

### Post by jcvardy on 2021-06-09
I'll check steams logs. Just had to reinstall it due to a bug, and I'm still having the same issue when exiting a game. Fun fact is, once I re-enter the game, it works fine, no choppines. Also, rebooting KDE didn't solve the issue :(

---

### Post by mastablasta on 2021-06-10
did you install steam from repos or via deb (using .deb file)?

---

### Post by Perfect Storm on 2021-06-11
Have you tried set your system in gamemode?

---

### Post by jcvardy on 2021-06-15
Think I installed it by repo, and tried gamemode. Turned out most of my issues were related to the KDE compositor. Found out running LXQt in parallel and executing the games there. Went smooth as hell, which pointed to the DE. Anyways, thank for the help guys, really appreciated!

---

### Post by mastablasta on 2021-06-16
KDE has a choice of different OpenGL to be used for drawing the windows. when i used old PC as well as now with the upgraded CPU i keep it low. it looks a bit more flat, not so nice, but is much faster as a result. you can also turn off various special desktop effects.

you can find these in:
> [COLOR=#202124][FONT=arial]'System Settings' > 'Display and Monitor' > 'Compositor'[/FONT][/COLOR]

KDE also has a setting for a while now where you can turn off desktop effects when full screen applications (e.g. games) are running. 

you can slo disable enable compositor with shortcut: Alt+Shift+F12

finally there is also Feral's Gamemode. which officially supports only some titles, but can also be used with other. more here: [https://www.omgubuntu.co.uk/2019/08/feral-gamemode-ubuntu](https://www.omgubuntu.co.uk/2019/08/feral-gamemode-ubuntu)

---

