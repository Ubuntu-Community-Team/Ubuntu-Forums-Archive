---
title: "Move Shank 2 game saves to Steam?"
date: 2013-10-20
forum: Gaming &amp; Leisure
---

### Post by dannyboy79 on 2013-10-20
Hey guys, I had purchased the humble bundle 7 and downloaded/installed some of the games through the Ubuntu Software Center (I didn't use the steam codes), i had played Shank 2 past half way through. The game saves and settings are located in ~/.klei/shank2/users/.

Recently I moved my steam library off to another drive using a symlink and it worked so now I installed many more games, shank 2 being 1 of them but when I start it up through Steam it doesn't have the progress I made. I can't seem to locate where steam shank 2 stores the game saves so that I can copy the save from ~/.klei/shank2/users/ so that steam sees the progress and gives me the achievements and I don't have to play the game over. 

Any thoughts?

---

### Post by Ranko Kohime on 2013-10-21
Play the game briefly, at least long enough for it to create a new save file.  Now search in ~/.local/share/Steam for any uniquely-named file that exists in ~/.klei/shank2/users.

This is just a shot in the dark, really, as I suspect, since the Steam version is not picking up the old saves, that it keeps them in either the program directory, (like some Valve games tend to do), or in the "userdata" folder.

---

### Post by dannyboy79 on 2013-10-21
good idea. i just tried that, played through the whole first board through the steam version of the game and still the only savegame.sav file is only located within ~/.klei/shank2/users
Hmmmmm, guess i'll just have to play it over. It's fun anyway, oh well.

---

