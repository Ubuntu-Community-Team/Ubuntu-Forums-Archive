---
title: "steam dual monitor suport and using existing game content"
date: 2012-12-16
forum: Gaming &amp; Leisure
---

### Post by milesnorth on 2012-12-16
I'm a non-beta tester and decided to install the steam client on a 12.04 kubuntu mythtv home theatre with monitor and projector this morning.  

question 1:
I copied a steam windows Trine 2 subdirectory to ~/.steam/steam/SteamApps/common and the linux steam client still downloaded the entire Trine 2 content.  How do I copy existing windows steam content to linux or otherwise use existing steam content on a dual boot linux/win8 machine.

Question 2:
Trine 2 only starts on display 0 and not display 1.  What steam or shell launch options will get the games to launch on the projector screen.  I tried first launching the steam client on display 1 and starting Trine 2 from the client.  And then tried the following script.  Both started Trine 2 on display 0.
```
#!/bin/sh
# Run Trine 2 game on display :0.1

# put the mouse to display 1.
`xwit $ARGS -root -warp 520 1080`

export DISPLAY=:0.1
steam steam://rungameid/35720

# put the mouse back.
`xwit $ARGS -root -warp 520 540`
```Thanks for any advice,
Kurt

---

### Post by holastickboy on 2012-12-17
I was under the impression you couldn't copy the windows installations to Linux, and vice versa,  and that you had to do a fresh install? 

Question 2: What is the graphics card and driver that you are using?  I know in Nvidia and AMD control panels you can set the "main" monitor for x output with games.  Failing that, you could always run in windowed fullscreen mode and just drag it to the other monitor.  I have never used the game config to actually play around with what renders on the monitor, always used the driver settings.  Furthermore, I tend to use dual x servers (which means i cant drag windows to each monitor, but I can run games in full screen on a specific monitor without having it stretched over both monitors).

---

### Post by milesnorth on 2012-12-19
> **holastickboy said:**
> Furthermore, I tend to use dual x servers  (which means i cant drag windows to each monitor, but I can run games in  full screen on a specific monitor without having it stretched over both  monitors).
I set dual x servers in the nvidia x server frontend.  Over the last  several days I cleaned up my script tweaked both this script and the   trine2_bin_starter.sh file.  Also started the steam client on display 1   and fired up trine from the client.  Looked for launch options for  trine in the steam  client. Looked in the options.txt file for trine.   Nothing gives me any  indication of how to start trine or steam games on  display 1.  I might  have to just live with my ignorance for awhile and  see what comes along.   Hope Steam can work on this frustration factor  for HTPC systems.

---

