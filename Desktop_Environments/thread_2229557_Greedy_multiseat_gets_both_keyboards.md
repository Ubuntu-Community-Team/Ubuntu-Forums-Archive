---
title: "Greedy multiseat gets both keyboards"
date: 2014-06-13
forum: Desktop Environments
---

### Post by Fisher on 2014-06-13
Hi. I'm using multiseat since Ubuntu 7.04, and it rocks!!
Now, after installing 14.04 amd64 I'm having trouble with one keyboard being attached to both seats.
I'm posting my xorg.conf, lightdm.conf and logs:

My xorg.conf [http://pastebin.com/Z5kde2fB](http://pastebin.com/Z5kde2fB)
My lightdm.conf [http://pastebin.com/wSAyLdU1](http://pastebin.com/wSAyLdU1)
My Xorg.0.log [http://pastebin.com/XG6bjjgp](http://pastebin.com/XG6bjjgp)
My Xorg.1.log [http://pastebin.com/mb6gJGg6](http://pastebin.com/mb6gJGg6)

Any ideas??

---

### Post by Fisher on 2014-06-28
No one!?
I'm really disappointed!! Ubuntu 14.04 seems to be really messed up!!
First this, than, ctrl + c just zaps my X, up arrow does print screen, my keyboard layout is always exchanged to us and no matter what I do I cannot restore to my language (pt_br), pulseaudio does not seems to work per seat as before, if I change my seat output the other seat is changed too!! 
Not to mention that compiz is very cpu intensive. It wasn't like this before!!
I remember to have similar issues in 7.04. Now they're back!! I just wanted to know why!!

---

### Post by Fisher on 2014-09-13
Ok, I've figured it out!!
- to disable the keyboard on the other seat, I used xset. found it's id and xset disable <id>. Had put it on the startup commands of the session.
- to stop killing my X with ctrl-x, I added -keeptty to my xserver command.
- to reenable the arrow keys I just completely disabled printscreen on the shortcuts. Not a nice workaroud, but...
- to workaroud the keyboard layout changes I used ibus-setup. added it to trray and it's fairy easy to make changes.
- to set pulseaudio's default soundcard, I made it start as a daemon and created the ~/.pulse/client.conf with the line "default-sink=<device>", found which device by looking at the device tab on the pulseaudio manager. By the way, padevchooser is a very nice applet to control pulseaudio.
- I have got a better responsive system by installing mate and using it as my default desktop, I disabled compiz too, maybe my videocards are just too old for it!

Hope these solutions can help someone else...
I'm a bit disappointed to be the only one to answer my only question.
Maybe I'm the only one using this kind of configuration around... who knows!!!
Thanks for everyone who have at least read!!
Problems solved, at last!!!
Maybe just till the other updates... who knows!?

---

