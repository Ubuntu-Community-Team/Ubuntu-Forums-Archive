---
title: "Sort directories by month name"
date: 2008-12-03
forum: General Help
---

### Post by Adriweb on 2008-12-03
I have photos sorted in directories according to year and month. So,for example,I have a 2008 dir with January, February, March etc dirs inside it.

How do I sort in File Browser so it shows them in order? It shows them alphabetically etc and i can do them manually but does Ubuntu 8.10 understand month names?

---

### Post by iaculallad on 2008-12-03
When in the Nautilus window: select "View as List" on the upper right-corner, then, you could click on "Data Modified" column to sort you folder by date modification.

---

### Post by mdebusk on 2008-12-04
> **Adriweb said:**
> I have photos sorted in directories according to year and month. So,for example,I have a 2008 dir with January, February, March etc dirs inside it.

If I wanted that, I wouldn't use month names. I'd use two-digit numbers, padded with zeros, i.e.:
[INDENT]~/Pictures/2008/01
~/Pictures/2008/02
~/Pictures/2008/03[/INDENT]

If I really wanted the month names, I'd do this:
[INDENT]~/Pictures/2008/01_January
~/Pictures/2008/02_February
~/Pictures/2008/03_March[/INDENT]

---

### Post by Adriweb on 2008-12-04
Thanks to both of you. I like this idea:

~/Pictures/2008/01_January
~/Pictures/2008/02_February
~/Pictures/2008/03_March



Why can't OS's understand Month names?!

---

### Post by mdebusk on 2008-12-05
> **Adriweb said:**
> Thanks to both of you. I like this idea:

~/Pictures/2008/01_January
~/Pictures/2008/02_February
~/Pictures/2008/03_March

If you prefer, you could do it in hexadecimal:
[INDENT]~/Pictures/2008/0_January
~/Pictures/2008/1_February
~/Pictures/2008/2_March
~/Pictures/2008/3_April
~/Pictures/2008/4_May
~/Pictures/2008/5_June
~/Pictures/2008/6_July
~/Pictures/2008/7_August
~/Pictures/2008/8_September
~/Pictures/2008/9_October
~/Pictures/2008/A_November
~/Pictures/2008/B_December[/INDENT]


> Why can't OS's understand Month names?!

Well, for sake of clarity, it's the "ls" command, the shell, or the file manager, not the OS. Operating systems don't need to care about month names.

The answer to your question, though, I would imagine, is that nobody wants it badly enough to make it happen. It may seem a trivial enough project at first blush, but consider all the special cases. How, for example, would we sort a directory containing January2005, January2006, January2007, January2008, February2005, February2006, February2007, February2008, and so on? Or how about one containing March, mArch, maRch, marCh, and marcH?

One of the foundational beliefs of a good programmer is this: **"The user will find a way to break it."** With anything regarding dates, there is a near-infinite number of ways to break even the best code.

No, the best approach is to habituate yourself to the use of [the ISO 8601 date format]("http://en.wikipedia.org/wiki/ISO_8601") whenever you're at a computer.

---

