---
title: "TrueCombat: Elite ubuntu 8.04 64-bit"
date: 2008-11-26
forum: Gaming &amp; Leisure
---

### Post by chessboxing on 2008-11-26
I installed Wolfenstein enemy territory successfully. But I only installed it to play tc:e. So I downloaded it and just, made it executionable, dragged it to the console or whatever. It did a successful archive integrity check. It starts to uncompressing, searching and finding the Castle Wolfenstein: Enemy Territory. And of course at the must crucial part the install part it have to go wrong.
This is what I get (this output as root logged in, it is the same as my default user however):
```

root@suntzu-desktop:/usr/local/games/enemy-territory# '/usr/local/games/enemy-territory/true.combat.elite_0.49b-english-4.run' 
Verifying archive integrity... All good.
Uncompressing True Combat: Elite 0.49b-english-4 Installer...............................
Searching Return to Castle Wolfenstein: Enemy Territory....
Return to Castle Wolfenstein: Enemy Territory found in /usr/local/games/enemy-territory
Installing in /usr/local/games/enemy-territory
Seems like Return to Castle Wolfenstein: Enemy Territory was installed by another user.
You have to install True Combat: Elite as the same user who did install Return to Castle Wolfenstein: Enemy Territory.

```

any suggestions...

---

### Post by chessboxing on 2008-11-26
Ok I once installed it and I found it in the trash folder. So I probably had chosen the wrong folder where WET was.
So I just copied this folder tcetest from the trash to  ~/.wolfensteinmapsomewhere/ and it worked. Does anyone knows how to delete it again. Proper uninstallation?

---

