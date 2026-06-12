---
title: "Switch to virtual desktop with shell command?"
date: 2014-04-24
forum: Desktop Environments
---

### Post by lunix2 on 2014-04-24
Is there a bash command to switch to a numbered virtual desktop?  I have four virtual desks.  What would I type into bash to switch to desktop number 3, for example?

---

### Post by Lars Noodén on 2014-04-24
You can install the packag [wmctrl](http://manpages.ubuntu.com/manpages/trusty/en/man1/wmctrl.1.html) and use that to switch.  The count starts at 0 so to get to the third virtual desktop you would use**wmctrl -s 2**  That works in Lubuntu, so it might work also in Ubuntu.

---

### Post by lunix2 on 2014-04-24
BEAUTIFUL!  Many thanks!

---

### Post by grumblebum2 on 2014-04-24
As you say **virtual** desktops I assume you are using compiz in which case you really only have 1 desktop so the wmctrl
command won't work.
You would have to use **wmctrl -o** with x,y values to change to a specific workspace.

With compiz each added virtual desktop increases these values by your screen resolution.

 eg Using my resolution(1680x1050) and 4 horizontal desktops these commands will switch...
[LIST=1]
[*]wmctrl -o 0,0
[*]wmctrl -o 1680,0
[*]wmctrl -o 3360,0
[*]wmctrl -o 5040,0
[/LIST]

This command will give each of your x,y values, when run in a terminal on that particular desktop.
```
wmctrl -d | awk '{print $6}'
```

---

### Post by lunix2 on 2014-04-24
Thanks for your answer.  Fortunately, the simpler syntax worked for me.   Though I do use vritual desktops, each spanning two monitors wide.  I  certainly appreciate the time and effort you put into helping me.  I  should've marked this as "solved", something I just found out about.  Now if I could just see where to do that.  I'll get it.

---

