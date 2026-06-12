---
title: "Pypar2 help please"
date: 2014-07-04
forum: Gaming &amp; Leisure
---

### Post by Willpwn on 2014-07-04
I downloaded a game on my computer, extracted the .zip file, an tried to run a .x86_64 file, but it opens with pypar2(cant use any other program) and I can't seem to run the game its self. The pypar2 window just stops( I think it actually may be done), and I'm left with another file in the folder with .par2 at the end of the file name. I can't extract it, or run it. If anyone knows how I can run the game, please help me!:p

Note: I am a complete Linux idiot, so sorry if I sound really dumb.

---

### Post by ubudog on 2014-07-04
What game did you download? And is [this]("http://pypar2.silent-blade.org/") the pypar2 you are talking about?

---

### Post by oldrocker99 on 2014-07-04
I use pypar all the time, and I have noticed a (very) few files open with it; I close it and right-click **Open** to run the program normally. Pypar is used by Linux users mostly for files downloaded from USENET which are protected by .PAR parity files, and, if there are enough "recovery blocks" present, damaged and even missing files can be repaired or recreated.

Your problem may also be that the executable bit isn't set:

```
chmod +x programname.x86_64 
```
 
Try that and see if it works.

---

### Post by Willpwn on 2014-07-05
That command worked! Thanks so much oldrocker):P

---

### Post by oldrocker99 on 2014-07-05
Always glad to help!:-D

---

