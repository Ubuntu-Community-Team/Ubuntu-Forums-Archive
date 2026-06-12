---
title: "right click open in terminal"
date: 2013-01-03
forum: Desktop Environments
---

### Post by tock on 2013-01-03
I've recently upgraded to 12.04.  I am trying to find how to re-instate the "open in terminal" right click option.  The only thing I find when searching is the script that works to open a terminal with right click.

I am looking to START a APPLICATION in the TERMINAL.  This has in the past been a way to see why a application isn't starting when left clicking on it.  I used to simply right click on the file and choose to "open in terminal"  The terminal window would spit out info describing why the file is unable to open. this is also handy when opening a video..  It makes it easy to see the decoding details.

So anybody know how to make this option re-appear in the right click menu while hovering above a file?

---

### Post by stinkeye on 2013-01-04
Did the old open in terminal open files and applications in terminal?

There is this ppa but the action only opens a directory in terminal. 
Add the nautilus-actions-extra ppa to your sources and install **nautilus-open-terminal-here**
```
sudo apt-add-repository ppa:nae-team/ppa
sudo apt-get update
sudo apt-get install nautilus-open-terminal-here
```

The ppa includes other right click nautilus actions such as **nautilus-open-as-root **

---

### Post by tock on 2013-01-04
Yes the old one would allow you to right click on a program and open it in a terminal window.

---

