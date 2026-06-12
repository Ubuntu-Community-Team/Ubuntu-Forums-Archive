---
title: "Terminal apps: limiting depth of folder name shown"
date: 2005-03-28
forum: Desktop Environments
---

### Post by panabar on 2005-03-28
I'm trying to limit the depth of folders shown on the

```

panabar@ubuntuTez:~/Documents/prc/cross/crosslinux/cutoff-10 $

```

line to show only one folder depth (for Gnome terminal app or Xterm or Eterm) something like this:

```

panabar@ubuntuTez: cutoff-10 $

```


But so far I haven't found clue on how to limiting depth and it gets more annoying the deeper I go into the folders.


Any help would be greatly appreciated.


Thank You

---

### Post by swhit on 2005-03-28
In the .bashrc file in your home directory,  comment out all the lines under the heading:

# set  a fancy prompt (non-color, unless we know we "want" color)

then add the line:

PS1='\u@\h: \W \\$ '

Best of luck.

---

### Post by panabar on 2005-03-29
Thank You for your advice :)
Now I can work without streching the terminal window until the borders of my screen and still not having enough room for an "ls -l" on the same line.
:)

---

