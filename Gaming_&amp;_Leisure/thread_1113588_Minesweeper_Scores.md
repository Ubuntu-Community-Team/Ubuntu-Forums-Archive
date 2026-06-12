---
title: "Minesweeper Scores"
date: 2009-04-01
forum: Gaming &amp; Leisure
---

### Post by JordanMcSwifty on 2009-04-01
Ive searched everywhere but does anyone know how to reset the scores for minesweeper?

Thanks.

---

### Post by some_random_noob on 2009-04-02
If it's not in any of these sorta places then I have no idea:

/etc
/usr/games
/usr/share/games
/usr/share/gnomegames
/usr/share/*insert game name here*

... I'm not running Ubuntu atm so that's just a stab in the dark. Maybe you should try a search based on file content.

---

### Post by _Purple_ on 2009-04-02
The scores are stored in the following files:

/var/games/gnomine.Large.scores
/var/games/gnomine.Medium.scores
/var/games/gnomine.Small.scores
/var/games/gnomine.Custom.scores

Delete these files using:
```
sudo rm /var/games/gnomine*
```

Create the files again and save them:

```
sudo nano /var/games/gnomine.Large.scores
sudo nano /var/games/gnomine.Medium.scores
sudo nano /var/games/gnomine.Small.scores
sudo nano /var/games/gnomine.Custom.scores
```

Then change the permissions:

```
sudo chown root.games /var/games/gnomine*
sudo chmod 664 /var/games/gnomine*
```

---

