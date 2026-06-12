---
title: "World of Warcraft Fatal Error"
date: 2006-01-20
forum: Gaming &amp; Leisure
---

### Post by thieves.honor on 2006-01-20
I was able to install and update WOW using wine 0.9.5.  I am able to get to the character selection screen, but when I select my character the load bar will fill all the way, the game will hang, then crash.  I get a message that states: This application has encoutered a critical error.  ERROR #132 Fatal Exception.  The instruction at "0x7E21C3CC" referenced memory at "0x000001C".  The Memory could not be "read".

Any one know what this is or how to fix it??

---

### Post by kidcharles on 2006-01-20
I occasionally get fatal exceptions at the same point (right when the world loads). Often times it is associated with a given character, probably related to their location in the game world. I suggest making a new character if possible, and see if you experience the same problem. This happened to me 2 days ago, and after I successfully loaded a different character, I was able to load all my characters, including those that wouldn't load before.

EDIT: I forgot to specify that I am using Cedega 5.0.1. I think it is still worth a try on Wine.

---

### Post by thieves.honor on 2006-01-21
tried creating a new character.  it didn't work.  the game hung right after the cut scene.  

anyone else have any ideas.

---

### Post by thieves.honor on 2006-01-24
ok update.   i updated to wine 0.9.6 from the repositories.  the problem is intermitent.  i tried loading the character repeatedly and after about the 5th try it loaded succesfully.  logged out and tried again.  after a few more times i was able to get back in.  any clue as to why this is happenning or what i can do to fix it??

---

### Post by auntiestacey on 2009-02-19
I am getting a similar error when loading the game before even getting to the login screen. Launcher.exe comes up with no problems, but pressing play, or runninng wow.exe all i get is this error. I have tried copying the install files from CD, and copied the wow folder from my Windows laptop. But neither will load the game. I have previously run wow on Red Hat but just installed ubuntu this week. Any help would be appreciated.

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\World of Warcraft\Wow.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:00000000

The instruction at "0x00000000" referenced memory at "0x00000000".
The memory could not be "read".

---

