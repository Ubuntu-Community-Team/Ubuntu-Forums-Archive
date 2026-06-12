---
title: "Guinea pig for testing Dungeonhack?"
date: 2009-06-05
forum: Gaming &amp; Leisure
---

### Post by del_diablo on 2009-06-05
Hi, i want somebody to build dungeonhack. Over at the DH forum a guy going by the username echo build this script. Its an attempt to autoinstall DH on Ubuntu, and well Debian thus off.
As a simple fact: we need guinea pigs to se if it works :P Tested it a little myself and it seems to work. Report any errors in building if you se them :P


Thus paste this into terminal:
```
cd
wget http://www.gnehp.com/ian-webdav/buildDH
chmod +rwx buildDH
~/buildDH
```

cd, so get get back to the home folder. Just to avoid any minor mess that could already be happening.
wget to fetch the script.
chmod to give a few permissions on it.
and finally the ~/buildDH to execute the script.


Then go to ~/dungeonhack/dungeonhack and run the dungeonhack file, which is the executeable for the game :P

---

### Post by del_diablo on 2009-06-06
Well after a little talk with the leader of DH and echo, we found out that we lacked a little in this tread..........

[quote="Archwyrm"][quote="del_diablo"]I think i got us a few guinea pigs from the Ubuntu forum, echo any disagreements?[/quote]
You might want to include a link to our site [in your post](http://ubuntuforums.org/showthread.php?t=1179458) so that people know what DH is (there is that other Dungeon Hack to be confused with on Google).

[quote="del_diablo"]Then go to ~/dungeonhack/dungeonhack/bin and run the dungeonhack file, which is the executeable for the game :P[/quote]
This is not correct. You should run the script 'dungeonhack' one level up from the bin directory, which does a few important things and *then* runs ./bin/dungeonhack.[/quote]

Dungeonhack wiki: [Here?]("http://dungeonhack.uesp.net/forums/index.php")
Dungeonhack forums(to be used for flaming some people claim): [Here :P]("http://dungeonhack.uesp.net/forums/index.php")

---

