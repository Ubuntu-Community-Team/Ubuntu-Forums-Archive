---
title: "display directory in terminal tab"
date: 2013-03-19
forum: Desktop Environments
---

### Post by rawlins02 on 2013-03-19
Trying enable the display of current directory at top of terminal in each open tab. Something like: 

~/Documents

Have installed xtitle package. At command line:

> xtitle Test

works. I've seen some post which talk about placing commands in .bashrc.  I use tcsh, so thinking .cshrc. What is the setting to get directory to show each time I change directory or open a new tab?

---

### Post by cortman on 2013-03-19
[This]("http://askubuntu.com/questions/22413/how-to-change-gnome-terminal-title") might be of help.

---

### Post by rawlins02 on 2013-03-19
> **cortman said:**
> [This]("http://askubuntu.com/questions/22413/how-to-change-gnome-terminal-title") might be of help.

Looks like the simple way is to edit the default profile.

Terminal -> Edit -> Title and Command

in the Initial Tile field. A colleague who uses another window system just had success by placing "%D" in that field. That doesn't work for GNOME. Still looking, as I'm unable to translate the bash commands in that tutorial into tcsh style.

---

### Post by cortman on 2013-03-20
Well, [here's a post]("http://apple.stackexchange.com/questions/21383/showing-current-directory-in-terminals-title-using-tcsh") on doing it with tcsh- I dont' use tcsh so I can't say if it'll work or not- it's for OSX...

---

### Post by rawlins02 on 2013-03-23
I chopped out the echo and sed commands from 

alias cwdcmd 'printf "\033]1;%s\007\033]2;%s\007" "$cwd:t" "$HOST echo $cwd | sed s-$HOME-~-" '

and placed in .cshrc. When I do a cd command I'm getting the computer name. Want something like:

~/Documents

which is /home/smith/Documents

---

