---
title: "Beryl is ok, but I lost the Alt Gr characters"
date: 2006-11-02
forum: Desktop Environments
---

### Post by didobuntu on 2006-11-02
Hi all,

I make this post because I have a small problem I guess.

I installed Beryl on my laptop with ATI Mobility X1600.
Things go ok but on my keyboard I lost the characters I used to obtain with the "Alt Gr" command such like: ~, #, {, [, |, `, \, ^, @, ], }.

Any Idea of how I can fix this issue?

Thanks,

P.S. I use a French keyboard.

---

### Post by dolarsrg on 2006-11-03
I've the same problem with my spanish keyboard, does anybody have some way to go around this?

---

### Post by Waeggles on 2006-11-04
Hello all,

I was looking for a solution to this exact problem and came across a german site that solved it for me:
[http://friederschueler.de/tag/kubuntu](http://friederschueler.de/tag/kubuntu)
This is for KDE, not sure if that's where you are having this problem...
My german is not exceptional but here's a quick translation of the important stuff:

The solution:
First, test the solution once in a terminal:

xmodmap -e "keycode 22 = BackSpace"
xmodmap -e "keycode 113 = Mode_switch" 

Second add it to a start up script:
echo 'keycode 22 = BackSpace' >> ~/.Xmodmap
echo 'keycode 113 = Mode_switch' >> ~/.Xmodmap
echo '#!/bin/sh' >> ~/.kde/Autostart/xmodstart
echo 'xmodmap ~/.Xmodmap' >> ~/.kde/Autostart/xmodstart
echo 'xprop -root -f _XKB_RULES_NAMES 8s -set _XKB_RULES_NAMES xorg' >> ~/.kde/Autostart/xmodstart
echo 'setxkbmap -model pc105 -layout **_de_** -variant nodeadkeys' >> ~/.kde/Autostart/xmodstart
chmod 755 ~/.kde/Autostart/xmodstart

The "de" I have underlined needs to be changed to your keyboard layout. So for spain "es", for France "fr".

Hope this helps!

---

### Post by didobuntu on 2006-11-04
Thank you Waeggles,

This resolved the problem. Now the "Alt Gr" runs under Beryl.
I am under gnome, so the only thing I understood is that I have to create the .Xmodmap file in my home directory with the two lines:

xmodmap -e "keycode 22 = BackSpace"
xmodmap -e "keycode 113 = Mode_switch"

If I use only Xgl/Beryl this is sufficient. But in this case "Alt Gr" is out under metacity, so there I have to remove .Xmodmap file.

I am sure the equivalent workaround under gnome of the following lines under kde could solve this issue. I means those lines you posted to modify the xmodstart file under the directory ~/.kde/Autostart:

echo '#!/bin/sh' >> ~/.kde/Autostart/xmodstart
echo 'xmodmap ~/.Xmodmap' >> ~/.kde/Autostart/xmodstart
echo 'xprop -root -f _XKB_RULES_NAMES 8s -set _XKB_RULES_NAMES xorg' >> ~/.kde/Autostart/xmodstart
echo 'setxkbmap -model pc105 -layout de -variant nodeadkeys' >> ~/.kde/Autostart/xmodstart
chmod 755 ~/.kde/Autostart/xmodstart.

However, for me the problem is solved at 95% since now I know a way to how to use "Alt Gr" under Beryl.

Thank you very much.

---

### Post by didobuntu on 2006-11-04
Hello,

In fact under KDE you must add the precedent commands and create files like described above.

Under Gnome is simpler :D . You simply have to add the following in the windows session: I mean in the Menu-->  System --> preferences --> starting programs.

Add the command line, "xmodmap /usr/share/xmodmap/xmodmap.**fr**"

change fr by **es** for spanish keyboard, by **de** for deutch keyboard and so one ..

---

