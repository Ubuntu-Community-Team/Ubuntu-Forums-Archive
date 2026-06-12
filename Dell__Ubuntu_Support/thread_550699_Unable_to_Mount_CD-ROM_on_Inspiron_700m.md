---
title: "Unable to Mount CD-ROM on Inspiron 700m"
date: 2007-09-14
forum: Dell  Ubuntu Support
---

### Post by cheever on 2007-09-14
Perhaps I should post this in the Absolute Beginner Forum, because I am.

Anyway, I am using an Inspiron 700m and whenever I try to open the CD-ROM, it just blinks at me,  When I try to access the drive, I receive the following message:

> Unable to mount the selected volume

"show more details" reveals

> mount: no medium found

I have searched for a solution on other forums.  Some suggest "right-click > mount volume", but that doesn't do anything.  Some suggest a few terminal commands, which I tried.  They didn't work, but I am not familiar with most of the terminal commands, so maybe its my fault.

Any suggestions would be greatly appreciated.  Thank you.

---

### Post by rmjokers on 2007-09-14
A few questions for you:

1. What kind of CD are you trying to mount?
2. Have you tried reading it in another system?
3. Are there any CD related errors appearing in /var/log/messages

---

### Post by cheever on 2007-09-14
> 1. What kind of CD are you trying to mount?

None.  The CD-ROM tray won't open.  It just blinks at me.  Actually, its a DVD-RW drive that came with the laptop.  If it would open, I might try to look at some jpegs from my sister's wedding, or maybe go through some of my old docs I have saved from college. Or maybe listen to some music.  Or watch a movie.  But it won't open at all, so I can't even try to mount anything.  I might think it was a hardware problem, but it opened and closed just fine with Windows XP.  Stopped working as soon as I installed Ubuntu.  I would reinstall Windows XP, or even Ubuntu if I thought that might fix the drive, but the drive won't work, so I can't.

I think that also answers your other questions.

---

### Post by Linicks on 2007-09-14
You don't 'mount' to open the cd tray.

Try running a console and type:

eject

Nick
P.S.  You can also open it with a paper clip in the little hole.  That at least will alow you to test a few things.

---

