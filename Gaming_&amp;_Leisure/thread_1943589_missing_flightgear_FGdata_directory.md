---
title: "missing flightgear FG/data directory?"
date: 2012-03-19
forum: Gaming &amp; Leisure
---

### Post by gandalf3 on 2012-03-19
I am new to linux and just recently installed Ubuntu 11.10
I downloaded an add on for flightgear 2.6 (bombable3p)
and the readme says to unzip to the Fg/data directory,
but, 

when i go to the /usr/share/games/flightgear/ directory there isn't any such folder..

am I being a total idiot?
or something really missing..?

---

### Post by catlover2 on 2012-03-20
> **gandalf3 said:**
> 
when i go to the /usr/share/games/[color=#ff0000]flightgear/[/color] directory there isn't any such folder..


Filenames are CaSe-sEnsItIve.

"/usr/share/games/[color=#ff0000]flightgear[/color]", which does not exist is not the same thing as
"/usr/share/games/[color=#ff0000]FlightGear[/color]", which is the folder that you are looking for.

 There could be three folders in "/", "boot", "Boot" ,and "BOOT". These three can exist simultaneously because they have different case.

Hope that helps, and welcome to Ubuntu Forums! :)

---

### Post by gandalf3 on 2012-03-20
hmm..
nope.. only one flightgear in /usr/share/games/...
heres some screen shots though if it will help

[IMG]http://http://ubuntuforums.org/attachment.php?attachmentid=214639&stc=1&d=1332268241[/IMG][IMG]http://ubuntuforums.org/attachment.php?attachmentid=214639&stc=1&d=1332268241[/IMG]


no data directory..
is it possible that "flightgear" *is* the data directory, just misnamed? (thats doesn't make much sense..)
or could i fix this by adding a /data/ directory and moving all the files in /usr/share/games/flightgear/ to a data folder in /flightgear/ ?
anyway, here's the rest of the screenshots.. dunno if it will help, but..

/usr/
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=214640&stc=1&d=1332268241[/IMG]

/usr/share/  (all thats in /usr/games/ are the executables)
[IMG]http://http://ubuntuforums.org/attachment.php?attachmentid=214641&stc=1&d=1332268241[/IMG][IMG]http://ubuntuforums.org/attachment.php?attachmentid=214641&stc=1&d=1332268241[/IMG]

/usr/share/games/
[IMG]http://http://ubuntuforums.org/attachment.php?attachmentid=214642&stc=1&d=1332268241[/IMG][IMG]http://ubuntuforums.org/attachment.php?attachmentid=214642&stc=1&d=1332268241[/IMG]
and /usr/share/games/flightgear/ is up at the top.

:confused:

---

### Post by catlover2 on 2012-03-20
I see that you've found /usr/share/games/flightgear. I haven't any idea how to install FlightGear addons; unless someone else chimes in about that, you're on your own.

Instead of posting screenshots of the file manager, simply post the output of (run in terminal)```

ls /path/to/some/folder
```

---

### Post by Sealbhach on 2012-03-21
All the items in your first picture are from the data directory. Looks like they did away with the /data subdirectory in 2.6. So you have unpacked bombable to the right place.

.

---

### Post by gandalf3 on 2012-03-21
oh... i thought it must be something like that..:redface:
unfortunately, bombable still doesn't seem to be working.. flightgear crashes whenever i click "run" 
i removed bombable.nas from nasal, and that seemed to fix it, but now bombable probably won't work (i don't know for sure, because I'm so inaccurate that i never actually hit anything..) i also get a "nasal runtime error: undefined symbol: bombable" but the program still runs.

---

