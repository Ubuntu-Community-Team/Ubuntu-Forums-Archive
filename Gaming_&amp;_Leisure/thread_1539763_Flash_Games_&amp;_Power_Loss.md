---
title: "Flash Games &amp; Power Loss"
date: 2010-07-26
forum: Gaming &amp; Leisure
---

### Post by Diya on 2010-07-26
There is a Flash Game called MARDEK on a gaming website which consists of 3 chapters linked together through save files. I went through chapter 1 and 2, and during chapter 3 I experienced a brief power loss while I was playing. When I came back, I had to re-download the game and the save files were not there which means I've to play chapter 3 with no items from the prior chapters. :(

Good news, I found 3 files here:
.macromedia/Flash_Player/#SharedObjects/688V3NNM/chat.(gaming website)

MARDEKv3__master.sol
MARDEKv3__options.sol
MARDEKv3__sg_0.sol (Autosave file according to another website)

so maybe there is still hope with a hex editor on hand, but I lose power a lot while playing Flash Games, and this is not the only time it ruins my gaming experience. What should I do about this in order to prevent further data loss? :S

I have the latest Firefox and Adobe Flash Player

---

### Post by aidenscool09 on 2010-07-26
Are you using a laptop or desktop?

---

### Post by Diya on 2010-07-27
> **aidenscool09 said:**
> Are you using a laptop or desktop?
Desktop

---

### Post by aidenscool09 on 2010-07-27
Ah, well it might be anything, is it only on this particular game?

---

### Post by Diya on 2010-07-27
> **aidenscool09 said:**
> Ah, well it might be anything, is it only on this particular game?

All games. It's due to power loss because they are having troubles at the electric power company at the moment.

---

### Post by Diya on 2010-07-27
The autosave file is empty. Looks like I'll have to start over :/

---

### Post by Deiz on 2010-07-27
You could set up a cronjob to backup ~/.macromedia, if it's really important to you.

It seems rather odd that files that aren't being written (e.g. saves for other games) would be touched at all, let alone zeroed.

Since it's not limited to what was currently being written, you can likely chalk it up to a Flash issue, though I've never experienced anything similar.

---

