---
title: "Commands for Home, End, PgUp, PgDn"
date: 2017-01-16
forum: Desktop Environments
---

### Post by peyre on 2017-01-16
Of all things, my laptop is missing Home, End, PgUp, and PgDn keys.  The only way to do those functions is to hold down the Fn key and press the arrow keys--which works, but it's pretty annoying.  I spend a lot of time on my laptop reading articles, so the lack of those keys (coupled with a bit of tendonitis) has been an inconvenience.  (I know I can use Spacebar to PgDn in a browser, but still I'd really like to have the functionality of all four buttons if I can manage it.  Now my laptop has Play, Stop, FFwd, and Rvs buttons available, and I could use the Keyboard utility in Settings to repurpose those as Home, End, PgUp, and PgDn keys, but I have to know the commands to assign them to.  Anyone have any idea?

---

### Post by Keith_Helms on 2017-01-19
Unfortunately, I don't think you can do anything with the Keyboard option under settings except assign keys to commands.  You can't make a keypress return a different key.  One thing I was playing with that does do that is to dump the x keyboard settings, edit them, and then reload them
```

xkbcomp $DISPLAY xkb.dump
gedit xkb.dump
xkbcomp xkb.dump $DISPLAY

```
I used this to change the F11 and F12 keys to work as PgUp and PgDn.  Don't change the top part where the keypress numbers are associated with an alpha key name, change the part below where the alpha key name is associated with an action.  I added a couple of lines for F11 and F12 and then deleted the blocks where their actions were previously defined.
```

**    key <FK11> {         [           Prior ] };**
    key <LEFT> {         [            Left ] };
    key <RGHT> {         [           Right ] };
    key  <END> {         [             End ] };
    key <DOWN> {         [            Down ] };
    key <PGDN> {         [            Next ] };
**    key <FK12> {         [            Next ] };**


```

In order to get the remapping to load automatically at startup/login, I created an .xsessionrc file in my home directory and put the following in it:
```

#!/bin/sh

xkbcomp /home/keith/xkb.dump $DISPLAY


```

---

### Post by peyre on 2017-01-19
Thanks Keith!  That would certainly explain why I couldn't find anything onine via google or ubuntuforums search for changing keymappings.

I might tinker with your suggestion, but it's a little involved for the sort of thing I usually like to do with my system.

---

### Post by KJKJKJ on 2017-01-22
Be brave, but cautious. Here's one way to do it. The response time is 300ms so hammering keys will fail. Skip to the end for 'monkey see monkey do' file you can edit and run.

xbindkeys is a program that grabs keys and mouse button events in X and starts associated shell command.

Use it to find the names of the keys you want to use. Like this:

> xbindkeys -k
Press combination of keys or/and click under the window.
You can use one of the two lines after "NoCommand"
in $HOME/.xbindkeysrc to bind a key.
"(Scheme function)"
m:0x0 + c:95
F11

xdotool  lets you ... simulate keyboard input and mouse activity, ...    
Example: Send the keystroke "F2"
            xdotool key F2
[COLOR=#3E3E3E]
[/COLOR]Now you have what you need. Tell xbindkeys to use xdotool to type the desired key when you press the assigned key
[COLOR=#3E3E3E]
[/COLOR]Here's a lightly tested example (14.04 LTS) ~/.xbindkeysrc file that makes F12 do what Home does, but it needs a small annoying delay to work.


# -*- shell-script -*-
#
# dot-xbindkeysrc
#

# ----

"sleep 0.3; xdotool key Home"
  F12 

# ----

---

### Post by KJKJKJ on 2017-01-22
Actually you can skip the xbindkeys part and use the GUI keyboard mapper you mentioned, so you just need the xdotool part as the command to run. Try reducing the sleep command delay or even removing it.

---

