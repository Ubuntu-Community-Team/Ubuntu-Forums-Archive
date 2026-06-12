---
title: "help, need bash script that runs a file every hour"
date: 2009-04-22
forum: General Help
---

### Post by Anxious Nut on 2009-04-22
Hello there, i have an exam tomorrow, and i think i might sleep while studying tonight so i need your help, i think it's easy...
  
I need a bash script that runs a file(sound file) every our

so that if i slept without knowing i'd get up again!

Thanks in advance, please help i need this ASAP

---

### Post by sdennie on 2009-04-22
You probably want to use cron.  It's meant for these kinds of things.  This has an example of what you are trying to do: [http://www.clickmojo.com/code/cron-tutorial.html](http://www.clickmojo.com/code/cron-tutorial.html).

---

### Post by Godly on 2009-04-22
there's a talking time keeper too. google it.

---

### Post by Anxious Nut on 2009-04-22
Thanks sdennie, ... but i got it, i already have KALARM and whatdoyouknow it has that thing, i'd like to use the one you've told me about but i dont have time to waste gotta study, thanks again, bye

---

### Post by kerry_s on 2009-04-22
yeah, crontab can do it.

crontab -e
put>
 0 */1 * * * $HOME/alarm

try my script and alarm here:
[http://ubuntuforums.org/showthread.php?p=7114879#post7114879](http://ubuntuforums.org/showthread.php?p=7114879#post7114879)

you can replace "alsaplayer" with what ever you want.
example:
xterm -e aplay ~/alarm.wav
totem ~/alarm.wav
vlc ~/alarm.wav
gnome-mplayer ~/alarm.wav

whatever you prefer. test it first.

---

