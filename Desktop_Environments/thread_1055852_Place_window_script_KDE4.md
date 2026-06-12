---
title: "Place window script KDE4"
date: 2009-01-31
forum: Desktop Environments
---

### Post by crispy_chunks on 2009-01-31
Hello,

Im quite new to KDE, but im starting to like it a lot despite some bugs etc. I especially like how easy it is to control where windows are put and what size etc etc. when you start up a program. But I got this program where I need to make a script to place the window at different locations on the desktop in different states, like minimized and fullscreen. It is enough with a script that toggles through three different modes:

Fullscreen at location 0x0
Fullscreen at location 1680x0
Minimized.

It doesnt have too be a script, but it would be very useful since i also need the script to check it the program is running, and if not, start it. I would  then bind the script execution to a key so I can control it easily. Like the key should execute: './toggle-script toggle' for example.

So the question is, what options do I have to make this script? Im very inexperienced in bash scripting, but I can code a little java, so Im not totally oblivious to what you might be talking about :)

Oh I should probably add Im running KDE4.2

---

### Post by crispy_chunks on 2009-02-17
So. I finally figured out how to deal with this thanks to some guys in the #kde channel on freenode.

Basically you need to edit the ~.kde/share/config/kwinrulesrc file according to your wishes and kwin will control the window placement. This would seem like a trivial task if it was not for kwin overwriting all your settings while it runs. So you need to kill kwin and then restart if to make these settings. Needless to say, this is not a very elegant solution as you lose your wm in the process for a brief period of time, which in my case luckily doesnt matter.

Here is a sample script i have made

> killall kwin
cd /home/media/
ps -e >> .processes
if grep -q xbmc.bin .processes
        then echo 'xbmc here'
        else echo 'xbmc not here' && xbmc &
fi
cp .kde/share/config/kwinrulesrc.lcd .kde/share/config/kwinrulesrc
sleep 1
kwin --replace --nocrashhandler &
rm .processes

First I kill kwin, then I check if my application is running, and if not start it - this is my script, edit yours accordingly - you probably don't want this check. Then I copy my kwinrulesrc.lcd (whith the settings I want changed) and overwrite the original one, and restart kwin. Dunno if this --nocrashhandler is a good thing, but it prevents the crashhander dialog from sometimes appearing.

Well it works now. But this is not very nice, and there is probably a nicer solution, if not, I would wish the kwin people would implement a nicer solution for this kind of feature.

---

