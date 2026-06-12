---
title: "Launcher doesn't work"
date: 2006-07-24
forum: Desktop Environments
---

### Post by z00s on 2006-07-24
So I've created about a half dozen launchers and they all work fine. However, when I create a launcher for Neverwinter Nights at /usr/local/games/nwn/nwn it simply will not run. I click on the icon and nothing happens. Every other launcher I've done the exact same routine with and they all work fine.

When I run NWN from a command line using: /usr/local/games/nwn/nwn 

I receive the error: /usr/local/games/nwn/nwn: line 12: ./nwmain: No such file or directory

However, it works fine if I type: cd /usr/local/games/nwn
Followed by: ./nwn

One thing I have noticed, however, is that when I run another one of my games, Doom3 from the command line using: /usr/local/games/doom3/doom3 it runs fine and my Doom3 launcher runs just fine.

Thanks in advance.

---

### Post by dtfinch on 2006-07-25
That's odd. On similar occasions (some games under wine) I've just written a shell script to cd to the directory and run it.

#!/bin/sh
cd /usr/local/games/nwn
./nwn

Then mark the shell script as executable and point the launcher to it.

---

