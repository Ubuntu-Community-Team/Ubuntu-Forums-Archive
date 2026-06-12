---
title: "root crash !"
date: 2006-01-13
forum: General Help
---

### Post by drfalkor on 2006-01-13
I turned off the computer the "wrong way" (pulled out the power cable), and when I turned it on again, it started to check the root file system, but everything failed and bla bla bla bla - So I had to reformat, lucky I did not have anything important then, but.. here is the thing - Is ubuntu breezy "weak" ? I mean, It is Linux we're talking about .

---

### Post by 23meg on 2006-01-13
What filesystem are (sorry, were) you using, and what error did you get?

---

### Post by drfalkor on 2006-01-13
ext3

---

### Post by southernman on 2006-01-13
[QUOTE=drfalkor]I turned off the computer the "wrong way" (pulled out the power cable), and when I turned it on again, it started to check the root file system, but everything failed and bla bla bla bla - So I had to reformat, lucky I did not have anything important then, but.. here is the thing - Is ubuntu breezy "weak" ? I mean, It is Linux we're talking about .[/QUOTE]

IMHO ubuntu is just the opposite of weak, just as *nix is as a whole. The vast majority of servers, serving the internet are using some variant of *nix.

The I-D-10-T errors were recoverable with fsck (just to name one way to have restored your system). I've made a few of those type errors myself. 

I guess it's always easier to blame the OS, instead of the user! ;)

---

### Post by 23meg on 2006-01-13
It's a journaling file system and should be as resistant to failure as they get; pulling the power cable out in the midst of a write operation is likely to get you into trouble with any OS and any filesystem though. I've had many power failures using Breezy and haven't noticed any particular "weakness" in this department; it seems you were less lucky.

---

### Post by traherom on 2006-01-13
[QUOTE=southernman]I-D-10-T errors[/QUOTE]Took me a minute to figure out what sort of error that was... at least they're the fixable ones. Physical hardware ones are a lot worse. :)

---

### Post by drfalkor on 2006-01-13
hehe, jepp - this is the first time this has happened to me, by the way.. it was something with the fsck(thnx for reminding me) :p

---

### Post by southernman on 2006-01-13
> Took me a minute to figure out what sort of error that was... at least they're the fixable ones. Physical hardware ones are a lot worse.
Roger that! :)

> hehe, jepp - this is the first time this has happened to me, by the way.. it was something with the fsck(thnx for reminding me)
It's likely to happen at least one more time, if your as lucky as I. ;)

Your welcome. Just glad you didn't take offense to my original post.

FWIW, you should only run fsck in "read only mode"

---

### Post by nihilocrat on 2006-01-13
I don't know if it was during a file write, but I've had plenty of times where I suddenly lost power, or I came back to my desktop to find it was abruptly shut down. Usually, when it boots up again, fsck will check the disks, and sometimes it will get scared and ask for a root password to manually run fsck. All I do is login and run fsck, occasionally pressing "y" when it spits out some question that I can't understand. When it's all done, my system seems to work fine.

---

### Post by iraklirost on 2006-01-14
I have same problmems:
* checking  Root file systems 
/ contains the file system whith errors, check forced 
Inode 673.... blablalbla

I wrote command: fsck -y 

but now my OS has other problmes:

Failed to start X server (your grafical Interface)
fatal server error(cannot open log file /var/log/Xorg.0.log )

---

