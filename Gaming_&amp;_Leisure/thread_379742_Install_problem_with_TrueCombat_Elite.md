---
title: "Install problem with TrueCombat: Elite"
date: 2007-03-08
forum: Gaming &amp; Leisure
---

### Post by bravemosquito on 2007-03-08
```
chmod +x true.combat.elite_0.49b-english-2.run
root@a-desktop:/home/a/tce# ./true.combat.elite_0.49b-english-2.run
Verifying archive integrity... All good.
Uncompressing True Combat: Elite 0.49b-english-2 Installer...............................
./search.sh: 36: Syntax error: Bad substitution
```

Of course, I've already installed ET, working with sound. Has anybody a workaround for this?

---

### Post by DiamondX on 2007-03-08
I had the same problem. Instead of installing 0.49b, install 0.49 (works), then install the 0.49b patch. The patch is a tar.gz file. Just copy the files in the tar.gz file to /usr/local/games/enemy-territory/tcetest/. You need to sudo to do this.

---

### Post by bravemosquito on 2007-03-09
Thank you, it works now

---

### Post by mudguts on 2007-12-22
so I must be a complete tool at this...
I have this true.combat.elite_049-english.run file in a 'games' directory that I made.

now what?

This is when I miss my .exe files.

---

### Post by wzwilliam on 2008-02-08
i'm having problems with true combat too. i have enemy territory working fine, downloaded the file true.combat.elite_0.49-english.run through wget, but when i try to install i have this error:

```
Verifying archive integrity... All good.
Uncompressing TrueCombat Elite: 0.48-english.................................................................................................................
Please visit http://www.liflg.org
Searching Return to Castle Wolfenstein: Enemy Territory....
Return to Castle Wolfenstein: Enemy Territory found in /usr/local/games/enemy-territory
-e 
ERROR!
You need Return to Castle Wolfenstein: Enemy Territory version 2.60!

md5sum: /home/william/Downloads/Enemy: No such file or directory
Return to Castle Wolfenstein: Enemy Territory found in /home/william/Downloads
[: 71: !=: argument expected

```

the install screen apears properly but it doesn't let me change the destination folder for installation. any ideas?

---

### Post by LT1Caprice57L on 2010-05-20
Bump.  Same problem as above, here.  Says "found in /usr/local/games/enemy-territory" then tells me I don't have it/need to install it.  What gives?

---

