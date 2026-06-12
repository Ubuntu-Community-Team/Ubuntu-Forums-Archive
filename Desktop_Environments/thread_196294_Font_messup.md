---
title: "Font messup"
date: 2006-06-14
forum: Desktop Environments
---

### Post by tonyisntcreative on 2006-06-14
I just got done installing two truetype fonts.  After I got done with the second one, everything started to look really....funny.  It seems that somehow all of my default fonts have been deleted and I'm left with only ttf fonts.  Things don't look BAD, they just don't look the same, and I don't particularly like it.  My /usr/share/fonts/type1 folder (where I assume my default fonts were) is empty.

Any ideas?

Edited with a picture to give you an idea what I'm looking at.  It's just...too thin.

---

### Post by caserio on 2006-06-14
Hi,

Did you try sudo fc-cache  ?

---

### Post by tonyisntcreative on 2006-06-14
Yeah.  I shouldn't say that the folder is empty, because it's not.  I think I've found all the fonts, they just don't seem to be recognized.

It turns out most of the fonts were in the /usr/share/fonts/truetype folder inside sub-directories.  The problem is, unless root you can't access any of the fonts.  I don't know how that happened.  I attatched a picture of how the files appear in Nautilus in my own account.

---

### Post by tonyisntcreative on 2006-06-14
I think I've fixed the problem.

---

### Post by kuad on 2006-06-14
I think I have a similar problem, except its with the font in the terminal, everywhere else is ok.

What was your solution?

---

### Post by tonyisntcreative on 2006-06-14
Well, I was told that fonts needed to have sudo chmod 644 done to them.  I accidentally 644's everything in my truefont folder, and almost all of them stopped working.  I made them 777 and viola!

Does anyone actually know if you NEED to make them 644?  I don't think you do...or it doesn't seem like it.

---

