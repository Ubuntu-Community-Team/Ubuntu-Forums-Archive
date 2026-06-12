---
title: "FreeCiv SDL... change AI difficulty?"
date: 2008-12-16
forum: Gaming &amp; Leisure
---

### Post by earthpigg on 2008-12-16
Hello,

I have played the GTK version of freeciv and you can modify AI difficulty via obvious GUI menus and such.

Unfortunately, freeciv gtk requires more screen space than is available on my dell mini 9 thus forcing me to use the sdl client.

-freeciv does not start the freeciv sdl client (i do not have freeciv gtk installed, it is not a conflict.

-civclient-sdl starts freeciv, but has very limited menu options and the man file does not offer any further options.

-civserver starts the cli to run a freeciv server - this ALSO does not offer the opportunity to modify AI skill level.

-edit: ive tried looking through the config files located in all the directories synaptic tells me freeciv-sdl has files located in... i have found no entries for ai difficulty level.



does anyone have any idea how to set the AI skill level above 'novice' in the sdl version of freeciv?

---

### Post by earthpigg on 2008-12-17
well, this fell off page 1 quickly.

---

### Post by earthpigg on 2008-12-20
bump

---

### Post by mikedep333 on 2008-12-20
Well, the SDL Client is incomplete and under development.

From my windows box with 2.1.8 installed, I thought you would be able to launch the freeciv server and set the ai difficulty through it's command line interface, but I don't see that option.

Your best bet may be to start a game from the GTK client with the right ai difficulty, save it, and then load it in the SDL client.

-Mike

---

### Post by gulaghad on 2009-01-25
Hello,
this is my first post in this forum. I'm actually a debian user and I saw your question while searching for another freeciv issue.

It's been more than one month, since thread started, but in case you still didn't find how to change AI difficulty, writing /AI-skill-level changes difficulty in integrated CLI with both GTK and SDL clients. (eg. /hard, /novice)

It is surprising, /help command shows other commands to display or change game settings but not this one. I too, had difficulty to adjust AI skill level when first tried SDL client.

---

