---
title: "Chocolate Doom can't find my iwads"
date: 2015-09-25
forum: Gaming &amp; Leisure
---

### Post by concreteghost on 2015-09-25
I have installed Chocolate Doom according to these instructions:

[http://www.chocolate-doom.org/wiki/index.php/Building_Chocolate_Doom_on_Debian](http://www.chocolate-doom.org/wiki/index.php/Building_Chocolate_Doom_on_Debian)

But now that I have it installed and set up with the Git repository, I can't get it to find my iwads. I have put them in the .chocolate-doom folder, the doom folder in /usr/local/games/doom and in /usr/share/games/doom. I even put them inside the chocolate-doom folder itself, but still no luck. I know there's environment variables DOOMWADDIR and DOOMWADPATH, but I have no idea how to set these. There's no config file or anything. It's probably something I overlooked but any and all help is appreciated. Thank you!

---

### Post by R33D3M33R on 2015-09-26
The config files for chocolate-doom should be located in a hidden folder named .chocolate-doom in your home directory ([see here]("http://manpages.ubuntu.com/manpages/vivid/en/man6/chocolate-doom.6.html#contenttoc10")).
BTW: Why don't you use the chocolate-doom from repositories?

---

