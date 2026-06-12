---
title: "Dell Inspiron N5110, Unity is gone!"
date: 2013-08-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Black_ExS on 2013-08-23
[FONT=verdana][COLOR=#333333]First of all, I am new to these forums
so I'm not sure if this is the right place to post this
if it isn't, I'm very sorry

anyways:
I am using a Dell Inspiron N5110
It has intel shared graphics and an nVidia GeForce GT 525M graphics card
Running Ubuntu 13.04 64-Bit[/COLOR]
[COLOR=#333333]I installed drivers for the nVidia card from the Xorg Edgers[/COLOR]
[COLOR=#333333]
Huge mistake
because now, unity won't appear
I can only see my desktop and the files on it
which sucks because I can't really run any programs
The only reason I'm able to use Chrome to write this is because I have an html page on the desktop
I open it, then it opens in chrome
other than that, the launcher and top bar are gone
I can only close chrome by closing all tabs
and have to shutdown from terminal[/COLOR]
[COLOR=#333333]
I installed bumblebee, nvidia drivers
removed them
reinstalled them again
NOTHING CHANGED[/COLOR]
[COLOR=#333333]
I have used the following commands[/COLOR]
[COLOR=#333333]```
dconf reset -f /org/compiz/
unity --reset-icons &disown
```

to get unity to reappear
the launcher doesn't have my old icons, it has the default ones
and when I run it through the terminal, it produces a giant list of errors
I don't want to have to run this every time I start Ubuntu!!

and the additional drivers tab is empty, while the about system dialog shows the intel shared graphics only
it doesn't even know about the nVidia card from what I can tell

is there someway I can use the nVidia card AND keep unity ?
because I want to play amnesia using wine, and it will be better with the card

I HAVE asked on the askubuntu website, but I thought I should also ask here
anything to fix this laptop[/COLOR][/FONT]

---

