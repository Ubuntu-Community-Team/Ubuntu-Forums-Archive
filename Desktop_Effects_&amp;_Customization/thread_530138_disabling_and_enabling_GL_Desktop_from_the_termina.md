---
title: "disabling and enabling GL Desktop from the terminal"
date: 2007-08-20
forum: Desktop Effects &amp; Customization
---

### Post by kevinfishburne on 2007-08-20
I found the thread [http://ubuntuforums.org/showthread.php?t=491670](http://ubuntuforums.org/showthread.php?t=491670), which is essentially asking the same question, but it had no adequate answer unfortunately.

I'm prepping the first of hopefully many Linux PCs I'll be selling on ebay and I'm setting up the "perfect" default user profile. Since most PC users are n00bs anyway, much less Linux users, it has to be pretty flawless. So, I want to replace the command in the launchers for all the games with a multi-command line that disables compiz, runs the game, then enables compiz. Here's a made-up example of the command line for a launcher:

compiz-desktop --disable;/usr/games/nexuiz --quiet;compiz-desktop --enable

I'm starting to get a bad feeling about this not being possible, even though with Linux most things usually are possible eventually after much weeping and gnashing of teeth. If necessary I could have each launcher run a script rather than a single command line, which would give me more flexibility, but I still don't know what I'd need to have in the script.

---

### Post by praet on 2007-08-28
well to do what you are trying to do in a single command line you have it right.
Just replace the commands with the relevant ones for your desktop.
For example: 
```
metacity --replace & rungame; compiz --replace &
or
kwin --replace & rungame; compiz --replace &
```

You could also write a single script to accept the game launch command as an argument and launch it that way.

---

