---
title: "is there a &quot;typewriter-DE&quot;?"
date: 2008-12-01
forum: Desktop Environments
---

### Post by akalos on 2008-12-01
hej!

i was wondering which DE would be the best for the following purpose:
running your laptop on battery-power (i.e. using as little power for unnecessary stuff as possible) and editing TeX-files (i.e. using your computer as a typewriter).
(e.g. writing/correcting your thesis in a train, not needing any pdf etc. open, just one or so TeX file(s) , writing nice comments for already working code etc.)

the limiting factors are:
1) that i dont really like vi for editing (i have tried it, but its a bit ... special :-)
2) command-highlighting would be nice
3) i dont even know how to start a command-line-(console?)-thing without starting gnome/kde/... [i found out how to change sessions though]
4) it would be nice to have some kind of indication how much longer the battery will last.

i guess there is not a unique answer to this question, but i hope for suggestions on what to try.

thx,
akalos

---

### Post by damis648 on 2008-12-01
You could just try exploring some very light DE's and WM's, like OpenBox or Fluxbox.

---

### Post by cmay on 2008-12-01
custom debian base install . i  like flux box as desktop when its on older computers and there is a option when you login in to sessions to choose terminal session which will give you just a terminal when you are at the login promt. which is possible to then start desktop by typing startx if you want to have the desktop started . 
hope it helped

ps:
i by the way also find vi a bit too strange so i recommend nano for small editing purposes but i have not found out how to enable syntaxts highlightning in it yet.

---

### Post by akalos on 2008-12-01
thanks to you both!
fluxbox seems nice and nano also looks very nice.
maybe the terminal-thing could work.

on this system here (not my laptop, but a tower with 2 screens) ive got the problem that if i want to log into a terminal session from the loginscreen i can only select "failsave terminal" (and gnome/kde/xscript/...) which then is only one quater of the on of the 2 screens big...
is there a way to have a fullscreen terminal?

thx,
akalos

p.s.: this worked for me (code-highlighting in nano) [http://tux.50webs.org/tip_nano_highlighting.html](http://tux.50webs.org/tip_nano_highlighting.html)

---

### Post by cmay on 2008-12-02
there should be . i use terminal sessions on debian etch that i build from the base up. using flux-box as desktop. i have however not tried to setup sop i can do this in ubuntu . but  i think i know what the problem is. in configure your sessions options there should be an option to do this. i am not on my own machine right now so i can not remeber how its done but i can not see any reason why it should not be  possible. 

the way i recommend setting up  minimal base install is to get the minimal cd image from debian download. then when installing uncheck desktop and just have set up a standard system. then you can use apt-get to install fluxbbox and then you have a minimal system that can do all these things and you can also use the alterantive ubuntu ubuntu installer to do the same thing. or o use fluxubuntu . 

thanks for the links by the way.

---

