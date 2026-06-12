---
title: "can't aim left in Abuse"
date: 2007-10-19
forum: Gaming &amp; Leisure
---

### Post by LogicalDash on 2007-10-19
I'm trying to play Abuse. The game runs just fine, except that when I move the target to the left of my character, he will not aim straight left. He will always aim diagonally up-left or down-left. How can I fix this problem?

---

### Post by Les_Caesars on 2007-11-10
Yes, there really IS a problem with the aiming (having made crappy games in junior high myself. I'd say that bad math in the code is probably the cause). It makes what would be a fun game unplayable. For something as sophisticated as a port of a classic shoot-em-up, this is a pretty fundamental goofup to overlook and not fix. I'm really surprised that the developers didn't notice this! It's not even like it's a difficult bug. Just look at the bloody line that calculates the inverse sine of the displacement from the player's position to the cursor's, and the lines that flip the angle if it's on the wrong side (these two steps determine the angle between the player and cursor). That's it. Done. If I wasn't too stupid to find the source code, I'd fix the bug myself! It's as of nobody even played the game before it was released.

---

