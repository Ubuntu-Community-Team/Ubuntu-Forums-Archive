---
title: "Quake 3 key bindings"
date: 2009-01-11
forum: Gaming &amp; Leisure
---

### Post by crazyfuturamanoob on 2009-01-11
I want to bind an action to left arrow key, in Urban Terror.

Would it be like this?

> 
bind left dostuff


How could I know what should I type as key?

Maybe there's somewhere a list of keys **bind** accepts?

---

### Post by minisori on 2009-01-11
Take a look to the .cfg file, there are all the keys listed.

---

### Post by crazyfuturamanoob on 2009-01-11
> **minisori said:**
> Take a look to the .cfg file, there are all the keys listed.

Which one of them, where is it?

---

### Post by minisori on 2009-01-11
If it's the quake3 mod, inside your home you should have a hidden folder called .quake3, if it is a stand alone game probably in a folder called .urban or something similar. Inside of those folders is the cfg saved by the game.

---

### Post by crazyfuturamanoob on 2009-01-12
I found a couple cfg files but nothing that contains full list of keys.

BTW how can I have a one command executing two commands?

---

### Post by minisori on 2009-01-12
Making alias, if my memory does not fail it should be something like this:

alias name_of_the_alias command 1; command 2; ..... ; command N;

Then you can bind that alias to a key.

Also you can make the bind to do one thing while pressing the key and another thing when releasing the key. For that you need to add + or -, respectively, before the alias or command when you are binding it.

I dont remember if there was a command in game to show the keys, but there are a couple to list the binds and alias, probably there is something similar. Anyway you can still use tab completion for the names of the keys, just remember SPACE, ENTER and all those keys are capitalized.

---

