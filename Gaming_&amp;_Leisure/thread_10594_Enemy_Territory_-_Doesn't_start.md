---
title: "Enemy Territory - Doesn't start"
date: 2005-01-09
forum: Gaming &amp; Leisure
---

### Post by NEtX on 2005-01-09
Hi,

I've downloaded the "et-linux-2.55.x86.run" file and could install it with any errors. I've also installed the nvida driver with apt-get and it's working fine with ut2004, but when I try to start et gnome has an error and reboots. So I don't even know how to find out why it does.

System:
Athlon XP Barton
nForce2Ultra
Asus 6800GT 128DDR

Drivers:
No AA and AF

Thanks for helping,
Nikolaus

---

### Post by runenes on 2005-01-09
What was the error message?

---

### Post by crane on 2005-01-09
[QUOTE=NEtX]Hi,

I've downloaded the "et-linux-2.55.x86.run" file and could install it with any errors. I've also installed the nvida driver with apt-get and it's working fine with ut2004, but when I try to start et gnome has an error and reboots. So I don't even know how to find out why it does.

System:
Athlon XP Barton
nForce2Ultra
Asus 6800GT 128DDR

Drivers:
No AA and AF

Thanks for helping,
Nikolaus[/QUOTE]


Yea try to find an error message, either in gnome or system logs (check /var/log although I'm not sure where in there it would be.

Are you running if from a shortcut or menu or terminal?

---

### Post by DDL on 2005-01-10
Did you try this ?

[http://ubuntuforums.org/showpost.php?p=35109&postcount=23](http://ubuntuforums.org/showpost.php?p=35109&postcount=23)

[QUOTE=NEtX]Hi,

I've downloaded the "et-linux-2.55.x86.run" file and could install it with any errors. I've also installed the nvida driver with apt-get and it's working fine with ut2004, but when I try to start et gnome has an error and reboots. So I don't even know how to find out why it does.

System:
Athlon XP Barton
nForce2Ultra
Asus 6800GT 128DDR

Drivers:
No AA and AF

Thanks for helping,
Nikolaus[/QUOTE]

---

### Post by Dreamflame on 2005-01-16
I have the same problem... tryed that DDL, didnt help :(

---

### Post by DDL on 2005-01-17
Could you post there your XF86Config-4 file ?

[QUOTE=Dreamflame]I have the same problem... tryed that DDL, didnt help :([/QUOTE]

---

### Post by jdodson on 2005-02-04
ok i had the same problem.  after an hour of searching and headscratching i tried the following.  

kill the gnome desktop so all you have running is a terminal(consult the web on how to do that).

type in the following commands in your personal home directory:

"vi .xinitrc"

then put this into the file

"exec ./bin/et"

ok well substitute ./bin/et with the location of your enemy territory starter, in my case i have a bin directory with the softlink.

it should run enemy territory as the window manager and it "should" run.  setup your player information, make sure to turn punkbuster on.  

now delete the .xinitrc file by typing "rm .xinitrc"

i would recommend running enemy territory using fluxbox as it seems to not crash.  running it in gnome seems to crash the whole works.... hope this gets worked out in hoary.  good luck! :-&

---

