---
title: "How to write a script, that kills a process, while another is running ?"
date: 2009-02-08
forum: General Help
---

### Post by emshains on 2009-02-08
I want to know, how can I make a script for launching games, so every time I launch it, it kills compiz and gnome-do etc. And when I exit the game, it starts them all over again. 
Could You try to help me ? 

I apologize for my bad English.

---

### Post by emshains on 2009-02-09
*bump*

---

### Post by geirha on 2009-02-09
I haven't heard of gnome-do before, but disabling and enabling compiz isn't too hard. If you are using ubuntu with gnome, then you can run ```
metacity --replace
``` before starting the game in order to turn off compiz. Then after the game, run ```
compiz --replace
``` to have compiz take over again.

---

### Post by emshains on 2009-02-10
> **geirha said:**
> I haven't heard of gnome-do before, but disabling and enabling compiz isn't too hard. If you are using ubuntu with gnome, then you can run ```
metacity --replace
``` before starting the game in order to turn off compiz. Then after the game, run ```
compiz --replace
``` to have compiz take over again.

I already have stuff like this, but what I want is a script, you know, like a program which executes other programs at given time, and decide what to do by understanding given circumstances. This would make my system run a bit faster.

---

### Post by glotz on 2009-02-10
Well, well... Open a terminal and chant

```
nano game <enter>
```

You'll now find yourself in the nano editor pointed to ./game file. Then write the actual script, just like what you'd type to a terminal, except you should begin the file with a hashbang and interpreter of of the language,
```

#!/bin/bash
pkill compiz
pkill gnome-do
cd /game
./executable
compiz
gnome-do

```

Hit Ctrl+X once you're done and enter to save to the predefined filename (game).

Finally you make the script executable ```
chmod +x ./game
```

You can then run it with ```
./game
``` or by pointing an icon to it.

I don't know if the suggested commands actually work.

---

### Post by emshains on 2009-02-10
> **glotz said:**
> Well, well... Open a terminal and chant

```
nano game <enter>
```

You'll now find yourself in the nano editor pointed to ./game file. Then write the actual script, just like what you'd type to a terminal, except you should begin the file with a hashbang and interpreter of of the language,
```

#!/bin/bash
pkill compiz
pkill gnome-do
cd /game
./executable
compiz
gnome-do

```

Hit Ctrl+X once you're done and enter to save to the predefined filename (game).

Finally you make the script executable ```
chmod +x ./game
```

You can then run it with ```
./game
``` or by pointing an icon to it.

I don't know if the suggested commands actually work.


THANKS A LOT!!!

I will try this ASAP!

---

