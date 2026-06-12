---
title: "AWN Manager not working after installing AWN"
date: 2009-11-05
forum: Desktop Environments
---

### Post by Locke03 on 2009-11-05
Hello I am new to this and I'm not sure how to fix this. I am running Ubuntu 9.10 Kirmac. After installing AWN the AWN-manager stopped working and I can't edit AWN-dock. The following is what came out when I ran it in the terminal. 

Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 220, in <module>
    awnmanager = AwnManager()
  File "/usr/bin/awn-manager", line 136, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 109, in __init__
    self.setup_look(defs.BAR, defs.BAR_ANGLE, self.wTree.get_widget("look"))
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 363, in setup_look
    self.changed_look(dropdown)
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 377, in changed_look
    self.reload_look(0, dropdown)
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 368, in reload_look
    if self.client.get_int(defs.BAR, defs.BAR_ANGLE) == 0:
glib.GError: Type mismatch: Expected `int' got `float' for key /apps/avant-window-navigator/bar/bar_angle

---

### Post by enrich on 2009-11-06
open a terminal and type gconfig-editor

then go into "/apps/avant-window-navigator/bar"
on the right side you should see "bar_angle"
forget about the value shown on the right and just right-click on the "bar_angle" and choose the modify option

if you see in the central box "float" that's your problem, you should set it to "integer"
unfortunately i couldn't click on that box so i just did:

right click on "bar_angle" > reset key      
(or maybe it's "reset value"... i'm on the italian version of 9.10 i don't know the exact translation ^^ just hit the reset one)

it worked for me, i've found it on a german forum (thanks google translator hehe)

i don't know if there's a way to make it from terminal (i'm another linux noob user ^^; )

i hope this will be helpful for you ;)

---

### Post by Locke03 on 2009-11-07
Thanks a bunch! after running the command I was able to reset everything. After resetting all the configuration I was able to gain access to the awn-manager via the system preference instead of through the terminal. Once again thanks!

---

### Post by jleaman on 2009-12-02
> **enrich said:**
> open a terminal and type gconfig-editor

then go into "/apps/avant-window-navigator/bar"
on the right side you should see "bar_angle"
forget about the value shown on the right and just right-click on the "bar_angle" and choose the modify option

if you see in the central box "float" that's your problem, you should set it to "integer"
unfortunately i couldn't click on that box so i just did:

right click on "bar_angle" > reset key      
(or maybe it's "reset value"... i'm on the italian version of 9.10 i don't know the exact translation ^^ just hit the reset one)

it worked for me, i've found it on a german forum (thanks google translator hehe)

i don't know if there's a way to make it from terminal (i'm another linux noob user ^^; )

i hope this will be helpful for you ;)



I just tried this and the command could not be found :( 


jase@jase-desktop:~$ gconfig-editor
gconfig-editor: command not found
jase@jase-desktop:~$ 


How can i fix this so i can get awn working, This is a fresh install of ubuntu 9.01, a friend said i should go back to 9.04

---

### Post by jleaman on 2009-12-02
ok so i got this working Kinda, 

the correct command is,


gconf-gedit  In terminal.

---

### Post by ciaastek on 2009-12-03
The correct command is 

**gconf-editor** ;) and you can type it after alt+f2

---

