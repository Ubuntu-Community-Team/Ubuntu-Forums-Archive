---
title: "Enemy Territory:True Combat: Install permissions"
date: 2007-04-24
forum: Gaming &amp; Leisure
---

### Post by rukie on 2007-04-24
Ok, I successfully installed Enemy-Territory, twice, 2.60b. However, I can't seem to get truecombat to install. When I execute the .run file, I get

> 
rukie@ubuntu-desktop:~/Desktop$ sudo ./true.combat*
Verifying archive integrity... All good.
Uncompressing True Combat: Elite 0.49b-english-3 Installer...............................
Searching Return to Castle Wolfenstein: Enemy Territory....
dirname: missing operand
Try `dirname --help' for more information.
md5sum: /et.x86: No such file or directory
Return to Castle Wolfenstein: Enemy Territory found in /
[: 65: e612c922bec7d8f4d7a8dfbbea3dade3: unexpected operator
Installing in /
Seems like Return to Castle Wolfenstein: Enemy Territory was installed by another user.
You have to install True Combat: Elite as the same user who did install Return to Castle Wolfenstein: Enemy Territory.


I tried installing it as my username, rukie, as root, and with sudo. None of which worked. I also tried doing a chmod a+rwx /usr/local/games/enemy-territory -R

which failed...

Any ideas?

---

### Post by crimsontide on 2007-04-25
I had the same thing happen to me yesterday when trying to install True Combat: Elite 0.49b. I had to install True Combat: Elite 0.49 then apply the True Combat: Elite 0.49b patch to get it to work.

---

### Post by nille on 2007-05-07
I found the answer on a spanish (?) site, after some hours spent trying...
[http://nicofo.tuxfamily.org/dotclear/index.php/2007/03/18/28-true-combat-elite]("http://nicofo.tuxfamily.org/dotclear/index.php/2007/03/18/28-true-combat-elite")

Do this:
**cd /to/download/directory**
**sh true.combat.elite_0.49b-english-3.run --target tce --noexec**
**cd tce**
**gedit search.sh** <-- I prefer **vim**  :D

Find row 105, it looks like this:
GAMEPATH=`dirname $GAMEDIRFOUND`

Change it to:
GAMEPATH=`dirname /usr/local/games/enemy-territory/et.x86`

Saven and then run (as root):
**./search.sh**




Same thing with ETF (well, change eferything to something that etf), if anyone are having problems with that one..

---

### Post by mr_niceguy on 2007-05-10
Much thanks!

---

### Post by Mr.NiceGuy on 2007-05-15
yea mucho thank i just got that problem today

ty ty:) :) :) :)

---

### Post by fakie_flip on 2007-05-16
What??????? I tried to download from that link. I went here.

[http://liflg.org/?what=dl&catid=6&gameid=52&filename=true.combat.elite_0.49b-english-2.run](http://liflg.org/?what=dl&catid=6&gameid=52&filename=true.combat.elite_0.49b-english-2.run)

I got this message.

File not found

---

### Post by appeltje on 2007-05-23
Great info, yeah. I just installed tce and ran into this problem, saved my sorry ***

fakie, english-2 is no longer newest file from loki, english-3 is.

Here is the link:

[http://liflg-tracker.death-row.org/torrents/true.combat.elite_0.49b-english-3.run.torrent](http://liflg-tracker.death-row.org/torrents/true.combat.elite_0.49b-english-3.run.torrent)

---

