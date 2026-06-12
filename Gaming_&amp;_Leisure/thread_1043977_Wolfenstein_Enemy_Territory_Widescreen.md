---
title: "Wolfenstein: Enemy Territory Widescreen"
date: 2009-01-19
forum: Gaming &amp; Leisure
---

### Post by stchman on 2009-01-19
Hello all, I installed the .deb files for my 64 bit Hardy.  I got the .deb files from playdeb.net and am using V2.60.  I however cannot get the game to play in widescreen.  I have edited the following file:

~/.etwolf/etmain/etconfig.cfg

I changed the following lines to use my 1920*1200 monitor

```

seta r_customheight "1200"
seta r_customwidth "1920"

seta r_mode "-1"

```

Still no go.  Does Wolfenstein:ET have problems with that resolution.  I play my other games like Openarena play at that res.

Thanks.

---

### Post by rotor_of_the_internet on 2009-01-19
try entering those commands in the console and follow it by /vid_restart

---

### Post by stchman on 2009-01-21
> **rotor_of_the_internet said:**
> try entering those commands in the console and follow it by /vid_restart

Tried that and no dice.  I wonder what is going on?  Other games play at that res.

---

### Post by Fernando Negro on 2009-11-08
You're editing the wrong file.


The file to be edited is the:

**~/.etwolf/etmain/profiles/<your-nickname>/etconfig.cfg**


Don't forget to update PunkBuster ([http://www.evenbalance.com/index.php?page=pbsetup.php](http://www.evenbalance.com/index.php?page=pbsetup.php)) in your "/usr/games/enemy-territory/" directory and also on your "~/.etwolf/" one. If you update PunkBuster for your home directory also as root, change the owner of the files created from "root:root" to "<your-name>:<your-name>" to be able to enable PunkBuster in the game.


For any sound problems check:

[https://help.ubuntu.com/community/EnemyTerritory](https://help.ubuntu.com/community/EnemyTerritory)



[http://adammichaelroach.com/blog/050409-wolfenstein-enemy-territory-ubuntu-linux-jaunty-jackalope-904](http://adammichaelroach.com/blog/050409-wolfenstein-enemy-territory-ubuntu-linux-jaunty-jackalope-904)

---

### Post by devguy on 2009-11-08
What works for me is to do it in-game at the console.  For me, I type:
set r_customHeight "1152"
set r_customWidth "2048"
set r_mode "-1"
(notice the camelHump capitalization and use of "set" vs "seta")
Then I restart Wolf:ET and everything is great!

---

