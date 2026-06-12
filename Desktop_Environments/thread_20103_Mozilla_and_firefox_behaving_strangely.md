---
title: "Mozilla and firefox behaving strangely"
date: 2005-03-15
forum: Desktop Environments
---

### Post by Biffy on 2005-03-15
Hi, this problem is very hard to explain for me, but i hope you understand.

This problem only seems to affect web browsers. Sometimes when reading text on a webpage, the fonts gets all blurry, and small. I cant read them. If i scroll down and up to the text again, it looks fine. 

This font issue happens once in a while. Does anybody else have this problem, or is it just me? I dont have a clue how to correct it.

---

### Post by RoccoD on 2005-03-16
Hi Biffy,

I have the same problem. The font on one line seems to be squashed vertically. Selecting redraws the text correctly. 

So, I have seen it, but no solution, sorry.

---

### Post by theProf on 2005-12-04
I know its been a while since you guys posted here, but I'm having the same problem, and it is one of the final bugs to work out with my laptop.

Did you ever find any resolution?  Thanks.

---

### Post by Naneau on 2005-12-07
I experience the same problem under breezy, I do unfortunately not have a fix, though I do remember a time when it wasn't there. It may have something to do with DPI settings, as I changed those recently.

---

### Post by Naneau on 2005-12-08
I think I may have found the solution to this problem. You have to set the dpi (dots per inch) settings in Firefox to whatever your system is using.

to find out what your system's dpi is type the following into a console window:
```
xdpyinfo | grep res
```

you can change the firefox dpi settings under:
```
edit >> preferences >> general >> font&colors >> display resolution
```

hope this helps you

---

### Post by theProf on 2005-12-09
Firefox was set at "system settings" for resolution, but I changed to to 92 dpi, which is what my system is set at.

I'll let you know if that solves the problem.

Thanks for the tip!
Happy Holidays

---

