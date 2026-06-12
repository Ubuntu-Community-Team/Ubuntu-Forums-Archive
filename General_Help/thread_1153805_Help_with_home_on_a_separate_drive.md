---
title: "Help with /home on a separate drive"
date: 2009-05-09
forum: General Help
---

### Post by olskar on 2009-05-09
Hi, I recently ordered a 1TB so now I have one 250GB and one 1TB. I want to use the 1TB as my "Home" and the 250GB as /. Is this how I should do it?

[LIST]
[*]Format the 1TB as Ext3
[*]This step I am a bit unsure of, should I simply just create folders like Music and Pictures in the root of the harddrive or should I first create a folder named as my username and then put Music and Pictures in there
[*]Move Music, Pictures etc from the 250GB to the 1TB
[*]Boot with latest Ubuntu CD
[*]Here I am a bit unsure as well, I should choose to have the 1TB mount as /home (or /home/username?) and not format? And format the 250GB and let it be /?
[/LIST]

---

### Post by kidders on 2009-05-10
Hi there,

> **olskar said:**
> [LIST]
[*]Format the 1TB as Ext3[/LIST]That depends on what you intend to use your home directory for. Ext3 is a good general purpose choice, but does have certain disadvantages.

> **olskar said:**
> [LIST][*]This step I am a bit unsure of, should I simply just create folders like Music and Pictures in the root of the harddrive or should I first create a folder named as my username and then put Music and Pictures in there
[*]Here I am a bit unsure as well, I should choose to have the 1TB mount as /home (or /home/username?) and not format? And format the 250GB and let it be /?[/LIST]Conventionally, people tend to mount additional filesystems to at /home, rather than /home/username. Your personal preference is all that really matters though.
> **olskar said:**
> [LIST][*]Move Music, Pictures etc from the 250GB to the 1TB[/LIST]Only if **lsof | grep /home** (or "/home/username", depending on what you're doing) returns nothing, and you're not logged in as the user whose files you're moving.
> **olskar said:**
> [LIST][*]Boot with latest Ubuntu CD[/LIST]This is unnecessary unless you intend to reformat your root filesystem as well. Reasons to do that include concern about fragmentation, and changing the filesystem type.

I hope that helps.

---

### Post by unutbu on 2009-05-10
Here is a guide on moving your current /home to a separate partition: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

