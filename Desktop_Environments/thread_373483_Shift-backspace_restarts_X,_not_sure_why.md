---
title: "Shift-backspace restarts X, not sure why"
date: 2007-03-01
forum: Desktop Environments
---

### Post by pcraven on 2007-03-01
Shift-backspace restarts my XSession, just like Ctrl-Shift-Backspace does. I'm not sure why, although it doesn't happen when I don't have XGL going. If beryl is not working, it will still shut down.

Shift-backspace is an easy key combination to accidentally hit. Any ideas on how I can un-map this reset button?

---

### Post by soul814 on 2007-03-11
I came across this, maybe this will help you. There is also some keyboard that seems to fix it. PC something something, 1? 

[http://customisinglife.wordpress.com/2006/11/13/disable-shift-backspace-restarting-xgl/](http://customisinglife.wordpress.com/2006/11/13/disable-shift-backspace-restarting-xgl/)

---

### Post by pcraven on 2007-03-12
That is exactly what I needed! This will save me so much headache, thanks.

For the record: I went into System...Preferences...Keyboard and changed my keyboard off the default 101 keyboard to my Logitech keyboard. Another possible solution I found on that link:
----------
Ok, this is how i do it

enter the following

xmodmap -e "keycode 22 = BackSpace BackSpace"

then to make it a permanent change create or edit the ~/.Xmodmap file to contain the following

keycode 22 = BackSpace BackSpace

---

### Post by Cuppa-Chino on 2007-03-30
where do I create this file :

> An easier way is to create ~/.Xmodmap containing the line:

keycode 22 = BackSpace BackSpace Terminate_Server

It's still just a workaround. Wonder when it will be fixed...

---

### Post by ArukiRei on 2007-04-04
Cuppa-Chino

~/.Xmodmap is the equivalent to /home/username/Xmodmap.

you can also use the following in a terminal to create the file.
Note: The "#" is used to indicate the prompt. Copy everything after the "#".

#echo "keycode 22 = BackSpace BackSpace Terminal_Server" > ~/.Xmodmap

---

### Post by Cuppa-Chino on 2007-04-04
thanks done that lets see

---

### Post by annihilus06 on 2007-04-05
This is what finally worked for me

xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"

Make sure that you use the " and not the ', at least that is what made it work for me finally.  Hope this helps!

---

### Post by What_the_deuce on 2007-04-08
Just changing the keyboard layout under System-Preferences-Keyboard was enough to fix this for me.

---

