---
title: "Sound in Warcraft 3."
date: 2005-04-19
forum: Gaming &amp; Leisure
---

### Post by endoscient on 2005-04-19
I just installed Cedega, and everything works great, except for sound. When the game launches it says cant initialize base sound system and sound is disabled. I searched the forum and took the advice to install lidsdl 1.21 -all but it didn't help at all. Any suggestions? Besides killing ESD (I would like to listen to music while gaming and still hear some ingame sounds).

Also, is there any way you can "Alt-tab" to desktop. I tried all the gnome keys the changed windows but left me where I was.

---

### Post by speedman on 2005-04-19
Here is a workaround for you:

sudo apt-get install esound-clients

Then in a term:

esdctl off

Then run your app/game.

Afterwards in a term:

esdctl on

You could include each of the steps above in a script and then use a custom launcher on your panel so you could just click it to run the game without resorting to a term each time.

Something like this:

#!/bin/bash

esdctl off

/path/to/your/game

esdctl on

HTH


Regards,

SM

---

### Post by endoscient on 2005-04-19
[QUOTE=speedman]Here is a workaround for you:

sudo apt-get install esound-clients

Then in a term:

esdctl off

Then run your app/game.

Afterwards in a term:

esdctl on

You could include each of the steps above in a script and then use a custom launcher on your panel so you could just click it to run the game without resorting to a term each time.

Something like this:

#!/bin/bash

esdctl off

/path/to/your/game

esdctl on

HTH


Regards,

SM[/QUOTE]
 I would like to play the game through Esound. So I can listen to music and hear game sounds at the same time.

---

### Post by speedman on 2005-04-19
[QUOTE=endoscient]I would like to play the game through Esound. So I can listen to music and hear game sounds at the same time.[/QUOTE]

Unfortunately there are some apps that do not play nicely with esd even after modifying the esd config.  That being said, you might get lucky if you change /etc/esound/esd.conf to look like this:

[esd]

# -=CAH=- commented out following line
#auto_spawn=0

# -=CAH=- added following line
auto_spawn=1

# -=CAH=- commented out following line
#spawn_options=-terminate -nobeeps -as 5

# -=CAH=- added following line
spawn_options=-terminate -nobeeps -as 2 -d default

spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=


Regards,

SM

---

