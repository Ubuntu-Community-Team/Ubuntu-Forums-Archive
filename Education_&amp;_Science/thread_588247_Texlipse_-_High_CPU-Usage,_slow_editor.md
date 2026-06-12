---
title: "Texlipse - High CPU-Usage, slow editor"
date: 2007-10-23
forum: Education &amp; Science
---

### Post by muh2k4 on 2007-10-23
Hey there.

Iam working with Texlipse, a LateX-Editor for Eclipse, to write my Diploma.
I encounter the problem that it is really CPU-consuming. I work on an CoreDuo 1.66Ghz with 1.5GB Ram. When writing a new paragraph its ok, but when it starts getting longer the cursor starts to fall behind my typingspeed. 
Then things go fast an i sometimes have to wait over 30 seconds for the editor to catch up. Its like he parses the document with every new letter i type.
The document isn't even long, maybe 3 pages. =(

Now i tried the following:
Under Window -> Preferences -> Texlipse -> Editor i disabled Automatic Parsing and Content Assist

But this totally made no impact on the performance. The compilation on the other hand is really fast ... it doesn't take longer than a second.

Maybe you have some idea. I really want to hold on to this editing platform, since it integrates the CVS-Client so well!

thx David

---

### Post by muh2k4 on 2007-10-24
OH cmon ...

It cannot be that iam allways a singular person having such problems!

---

### Post by muh2k4 on 2007-10-25
After wasting three days of experimental time i figured it out.
As it seems eclipse didn't like the used JavaRuntime-Environment.
Switching to sun-java1.6 saved the day.

---

### Post by feynmandiagram on 2008-03-18
Hey,

you aren't the only one. I am facing this problem currently, too. Almost half a year after you. I'll try your solution, thank you for posting it!

feynmandiagram

---

### Post by feynmandiagram on 2008-03-18
Solution was replacing iced tea jre with sun java jre, which is faster! However it wasn't really faster, which I consider the soft wrapping as responsible. I switched to KILE, damn.

---

