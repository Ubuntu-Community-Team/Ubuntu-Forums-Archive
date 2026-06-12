---
title: "Script to start multiple instances of same program"
date: 2009-05-12
forum: General Help
---

### Post by XCan on 2009-05-12
I'm quite new to the whole shell scripting part in *nix system and has so far mostly just written very trivial scripts. However, recently I've come to need a simple way to start up 3-4 instances of the same program. The problem is that these instances preferably should not run in the background but occupy one bash screen each. 

Since I've grown very attached to the feature in Ubuntu where multiple tabs can be launched within the "same" terminal window, I'm wondering if anyone could point me in the right direction as to how to write a script that would do the following:

```
start an instance -> create new tab -> start instance -> create new tab -> start instance and so forth. 
```

Thanks in advance!

---

### Post by XCan on 2009-05-13
*bump*

---

### Post by geirha on 2009-05-13
Put this in a file:
```

hardstatus alwayslastline "%{=b}%{b}%w %=%{G}%c %d. %M %Y "

screen irssi                       # Start irssi irc client in first window
screen w3m http://help.ubuntu.com  # Start web browser in second window
screen                             # Start a shell in the third window

```

Call the file whatever you like. I'll just assume you called it "myscreenrc"

Run screen with that configuration file
```
screen -c myscreenrc
```

Now you have three windows in one terminal. To switch between them, you can use C-a <number>. That is press and hold Ctrl, hit a, release Ctrl, hit 0 (or 1 or 2).
There's also 
C-a n - next window
C-a p - previous window
C-a C-a - last viewed window (Hold Ctrl, hit a, hit a, release Ctrl)
C-a c - create window

Lastly, the really nice thing about screen is that you can detach and reattach to it.
Hit C-a d to detach. The programs you have started in the screen will keep running in the background. Then later you can open a terminal and run ```
screen -r
``` to reatach to it.

You can also display the same screen in two terminals at once, by running "screen -x" in the second terminal.

---

### Post by StuartN on 2009-05-13
It does not work. There are bug reports [https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/157266](https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/157266)

You are supposed to be able to add options to the terminal command (see "man gnome-terminal") to open as many tabs or windows as you like and pass commands into them.

For instance this should run "ls" in the first tab and "which" in the second, but only partially completes:

```
gnome-terminal --tab-with-profile Default --command "ls -a" --tab-with-profile Default --command "which ls"
```

The outcome is unpredictable if more than one command is included. Without commands the tabbing works correctly.

Also, before running gnome-terminal you must open a terminal and edit the Default profile settings under "Title and Command" to set "Hold window open" when command exits (otherwise the command runs and all trace disappears before you see anything).

---

### Post by XCan on 2009-05-13
Thank you guys! I tried StuartN's approach and it's working perfectly!

---

