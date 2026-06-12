---
title: "How to shift screen to left upon login?"
date: 2005-09-14
forum: Desktop Environments
---

### Post by rosslaird on 2005-09-14
Every time I login (and indeed, even in gdm, though I can't fix it from there), I have the problem that the active part of my screen is shifted to the right about an inch. There'a just a black strip on the left. Then I use xvidtune to shift the active part back to the left. Everything works perfectly at that point. But then when I login again it reverts back to the blaxk strip.. How can I change xorg.conf (or whatever) to make the changes from xvidtune permanent?

Ross

---

### Post by Hairy_Palms on 2005-09-14
i remember i had this problem when i used suse, but unfortunately i didnt learn how to do it manually i just used sax2.

---

### Post by heimo on 2005-09-14
Doesn't xvidtune output a modeline? (lots of numbers) You can put that in Monitor section of xorg.conf and match the name (first column on that line) with modes line in screen section. 

Some related instructions:
[http://ubuntuforums.org/showpost.php?p=129379&postcount=21](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)

---

### Post by rosslaird on 2005-09-14
Thanks for the help. I had seen something about a modeline but didn't know how to get it, because when you run xvidtune from the GUI (by using alt-f2, for example), it doesn't show a modeline. You have to run it from a terminal within X, then click on "show" and it will output the modeline to the terminal.

Cheers.

Ross

---

