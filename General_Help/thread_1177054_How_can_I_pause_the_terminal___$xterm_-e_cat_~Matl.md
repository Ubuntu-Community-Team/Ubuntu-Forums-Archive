---
title: "How can I pause the terminal?   $xterm -e cat ~/Matlab/gedit/gbug.m"
date: 2009-06-03
forum: General Help
---

### Post by sstecken on 2009-06-03
If I call this... 

$xterm -e cat ~/Matlab/gedit/gbug.m

The terminal appears and disappears as quick as it can.

I've tried these...

$xterm -e more ~/Matlab/gedit/gbug.m && sleep 2
$xterm -e cat ~/Matlab/gedit/gbug.m && sleep 2

How can I get the terminal to appear, spit out what I want, and wait for me to manually close the window?

Thanks.

---

### Post by jocko on 2009-06-03
> **sstecken said:**
> If I call this... 

$xterm -e cat ~/Matlab/gedit/gbug.m

The terminal appears and disappears as quick as it can.

I've tried these...

$xterm -e more ~/Matlab/gedit/gbug.m && sleep 2
$xterm -e cat ~/Matlab/gedit/gbug.m && sleep 2

How can I get the terminal to appear, spit out what I want, and wait for me to manually close the window?

Thanks.
Try this:
```
xterm -e "less /home/[COLOR=Red]username[/COLOR]/Matlab/gedit/gbug.m"

```By some reason it doesn't work with "~/" in the path. "cat" and "more" doesn't work because they are finished when they have shown the file (so the terminal closes), while you have to exit "less" with "q", even when the entire file is shown.

---

### Post by jenkinbr on 2009-06-03
I've tried a lot of different things here for you, and found nothing.  (edit: you may want to try less, as mentioned above) I'd reccomend that you open the xterm window, then enter your command manually.

I would honestly use a different terminal emulator entirely, such as gnome-terminal (I have a script in my /home directory called 'gterm' because I hate typing 'gnome-terminal' out every time.

---

### Post by LondonSteve on 2009-06-26
xterm -e "ls; bash"

or

xterm -e "ls; sh"

or your favorite shell I guess

---

