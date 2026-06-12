---
title: "Remap keys for specific window/app?"
date: 2015-06-16
forum: Desktop Environments
---

### Post by pingaan on 2015-06-16
Hi,

What the topic says basicly.

I am some what familiar with xev, xmodmap and xdotool.
Is it possible to remap some keys on the keyboard using those tools (or any other tool) for specific windows or specific apps?

My keyboard has no left shift and with that being a key a really rely on in MMO gaming I need to remap the "<>|" key. As you all know that key is needed when running certain commands in the terminal, also my favoirite smiley is :< (!), so I need to remap the key to it's original function upon leaving the window, alt. exiting the app.

A work-around would be simply to map the key to some other key that isn't frequently used but that's nothing I'm interested in.

Regards.

---

### Post by pingaan on 2015-06-16
[COLOR=#000000][FONT=sans-serif]It's launched via PlayOnLinux which has a "exec on launch" option. It's possible to add the key remap command therw and then but then it's changed through out Ubuntu, allt together of course.
I thought building a script and launch thst might do the trick, but I would need lots of help doing just that.


Containing something like;
```
#!/bin/bash


PID=`pidof Wow.exe`
$PID
``` 
And then a command (if there is anything for it) running state 0x10, keycode 110 (keysym 0xff55, Shift_L), same_screen YES, only when that pid is focused...


Then again since it's X based using "xdotool getactivewindow" would make more sense.


Actually I should shut up, since I have no idea how to get what I actually want! :-P


Anyone with experience with scripts, please help! 
[/FONT][/COLOR]

---

### Post by tgalati4 on 2015-06-17
It looks like you are trying to define a custom keyboard layout in WINE, which is what you are running World of Warcraft on.  I'm not familiar with how to do that, but here's a link with a suggestion:

[http://askubuntu.com/questions/34596/change-keyboard-layout-in-wine](http://askubuntu.com/questions/34596/change-keyboard-layout-in-wine)

---

### Post by pingaan on 2015-06-17
Yes, correct. Wine via PlayOnLinux, I guess. It looks like this could be of help! I'll check it out and report back.

---

### Post by pingaan on 2015-06-18
The keyboard layout tab is gone in 15.04, I used a shortcut command instead.

---

### Post by tgalati4 on 2015-06-18
Please describe exactly what you did so that others can follow your example.

---

### Post by pingaan on 2015-06-22
Oh, of course..
In keyboard settings you can setup custom shortcuts. I used ctrl+alt+m to launch a script containing:
[COLOR=#000000][FONT=sans-serif]```
0x10, keycode 94 (keysym 0xff55, Shift_L), same_screen YES
```
To swap back to the original layout I simply click the desired layout via the GUI button, top right of the screen.
The layout is also back to normal when you boot up. The key remap is only temporary.

Hope the work-around can be of help!

Cheers.[/FONT][/COLOR]

---

