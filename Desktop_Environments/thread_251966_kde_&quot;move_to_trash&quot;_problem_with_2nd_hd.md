---
title: "kde &quot;move to trash&quot; problem with 2nd hd"
date: 2006-09-06
forum: Desktop Environments
---

### Post by Pietro Pizzi on 2006-09-06
Hi,

I have 2 HDs. Nr.1 with the system and my home dir. Nr.2 with additional data. The 2nd HD (ext3) is mounted under /media/extrahd and in my ~/Data dir is a link to a folder on it. Since last week the "move to trash" on the 2nd HD woked as i expect, fast. I think it moved the data in a trash place on the same HD.

Now my problem:
On the 1th HD the "move to trash" is still as fast as it should be. But on the 2nd it is extremly slow. The problem is that it moves the data on the 1th HD, but i think it should leave it on the 2nd? I don't where the trash place (folder) should be, if it exitst (on the 2nd HD) and how i can fix that problem.

I hope anybody can help me.
Thanks, Pietro

---

### Post by Jucato on 2006-09-06
The Trash Can puts the deleted files in a hidden directory in your /home directory. and since your /home directory is on the 1st HD, deleting files from the 2nd HD, wether or not it's linked to a folder in your /home directory (1st HD), means that the files have to be moved from the 2nd HD to the 1st one. I think that would be causing the slowness. Unfortunately, I don't know of a way around this. :(

---

### Post by Pietro Pizzi on 2006-09-14
That sounds Strange becaus i used that system since the First Ubuntu come out and with Kubuntu i switched to KDE and i don't have this behavioral ever.

An additional info to my 1th post: the problem starts since i copyed my whole system to another disk becaus of pc problems and at the same time i changed the data partition from raiser to ext3. It's possible that i lost an important dir for deleting under KDE during this task.

Could anyone help me?
Thanks, Pietro

---

