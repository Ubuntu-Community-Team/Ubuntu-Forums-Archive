---
title: "restricted driver and compiz"
date: 2008-01-09
forum: Desktop Effects &amp; Customization
---

### Post by cgerb on 2008-01-09
i have gutsy installed with an ati 9700pro.  i enabled the restricted driver upon install of gutsy and could not get compiz to work at all.  then i read  forlongs blog saying that the restricted driver is the problem. soooo, i disabled restricted driver and rebooted and poof compiz is working. cube is rotating like a top.    BUT,  (there seems to always be a BUT),  now my window panes, ie application's window, web browser, spreadsheet, etc. locks in the upper left corner and cant be moved.  also the minimize/maximize/close buttons in upper right hand of app window disappears.   i went back and reenabled restricted driver and all is back to normal,  BUT compiz is back to not working.  sorry for post being long,  any ideas.  thanks

---

### Post by Forlong on 2008-01-09
Sounds like a Compiz issue rather than a driver problem.

Please post the output of ```
compiz
``` in a terminal.


btw: if you want to use Compiz with the "restricted" fglrx driver, you have to install Xgl as well:
```
sudo apt-get install xserver-xgl
```

---

### Post by cgerb on 2008-01-12
thanks forlong.  downloading that xgl driver fixed me right up.  allows me to play my games with steam as well as getting compiz to work.  perfect,  thanks again.  
btw  great blogs/tutorials.

cgerb

---

