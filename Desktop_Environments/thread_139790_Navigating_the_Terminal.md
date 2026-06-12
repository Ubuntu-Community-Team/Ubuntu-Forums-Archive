---
title: "Navigating the Terminal"
date: 2006-03-04
forum: Desktop Environments
---

### Post by phargarten on 2006-03-04
I am fairly good with Windows command but brand new to Unix as of yesterday when I did my first Linux install. I am loving it but having an issue with the "cd" command. I am sure this is idiotic but here's my question:

here is a snapshot of my navigation

peter@ubuntu2:/$ dir
usr (and the rest are listed)
peter@ubuntu2:/$ cd usr
peter@ubuntu2:/usr/$ dir
bin games (and the rest are also listed)
peter@ubuntu2:/usr$ cd /games
bash: cd: /games: No Such File or Directory

I feel like an idiot but I cant see why this wouldnt navigate similar to windows command. Thanks for any help

---

### Post by o_fortuna on 2006-03-04
[QUOTE=phargarten]I am fairly good with Windows command but brand new to Unix as of yesterday when I did my first Linux install. I am loving it but having an issue with the "cd" command. I am sure this is idiotic but here's my question:

here is a snapshot of my navigation

peter@ubuntu2:/$ dir
usr (and the rest are listed)
peter@ubuntu2:/$ cd usr
peter@ubuntu2:/usr/$ dir
bin games (and the rest are also listed)
peter@ubuntu2:/usr$ cd /games
bash: cd: /games: No Such File or Directory

I feel like an idiot but I cant see why this wouldnt navigate similar to windows command. Thanks for any help[/QUOTE]
Since "/" is the name of the root filesystem (like C:\\ is in Windows), you shouldn't use it before games. For example, when you did this:
```
cd usr
```
You told the console to switch to a directory relative to your current directory (/), and when you did this
```
cd /games
```
You told the console to switch to the directory at "/games" (/ being the root directory, games being a folder within that directory) which doesn't exist.

Basically, putting the / before it makes it an absolute directory change (relative to the root filesystem, /), but not putting the / before it makes it a relative change. What you should have done was:
```
cd /usr
cd games
```
The slash before usr so that it switches to /usr, which is where you want to go (in case you're in a different folder). There is no slash between "cd" and "games" because you are going to a folder that is in in the current directory. (i.e, it says peter@ubuntu2:/usr$ so the /usr is where you currently are).

Another excellent article from the [Ubuntu Wiki]("https://wiki.ubuntu.com"): [TerminalHowTo]("https://wiki.ubuntu.com/BasicCommands?action=show"). Check it out.

---

### Post by pestilence4hr on 2006-03-04
Try `cd games`.  The full path to the directory you are trying to get to is /usr/games, not /games.  `cd /usr/games` will work too.  And you should probably get acquainted with "ls" instead of "dir".  See "man ls" for documentation.

---

### Post by aysiu on 2006-03-04
If you're in /home/phargarten and want to get to /home/phargarten/games, you would type ```
cd games
```

If you're in /home/billyjimbob and want to get to /home/phargarten/games, you would type ```
cd /home/phargarten/games
```

Unless you have a folder called /games at the top level (with /usr, /bin, /lib, /boot, and /etc), doing ```
cd /games
``` won't get you anywhere.

---

