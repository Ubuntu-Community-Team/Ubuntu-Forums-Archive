---
title: "cairo-clock fonts too narrow"
date: 2009-11-20
forum: Desktop Environments
---

### Post by demagogue11 on 2009-11-20
I am currently using cairo-dock's built-in clock applet, and the analog clocks look great. But when I change it to digital, to match the text-based dock icons (maththias's icon set, which is comes with cairo-dock), the font is too narrow. It makes the numbers look weird. I have tried comparing the numbers with what the should look like, and the applet is definitely squishing them for some reason. I have tried adjusting the size of the clock to no avail. I don't know Python, so I can't fix this myself. All I want is for the digital clock in the clock applet to display text normally without squishing it. Try turning on the clock applet in cairo-dock, switching the look to digital and pull up a parallel Writer window, chose the same font that you selected for the clock, and type the digits you see on the clock and you will see that they are more narrow than in your Writer window. Anybody have any ideas on how to fix this?

---

### Post by fabounet on 2009-11-23
you can set up the size of the clock icon.
the text will adapt to the size of the icon.
I suggest to decrease the height while keeping the width constant.

---

### Post by dannyboy79 on 2009-12-23
i am running karmic with latest ppa cairo-dock. i am using the digital clock and it is so small and very hard to read. I have changed to font several times to even 32 and it still just stays the same size. also, when I set it to non-24 hour time format, there is to AM's or or 2 PM's. so it looks like this 6:36:30 PMPM. ANy thoughts?

---

### Post by fabounet on 2009-12-23
try to change the font, te color, etc, to improve the readability.
normally, with 48x48 icons, it is very readable.

---

### Post by pennstatebadboy on 2010-11-10
Does anyone know if it's possible to have the time on the digital clock NOT display AM or PM in 12-hour format?

Also, in 12-hour format, the digital clock adds a zero before the hours of 1-9. For example: 04:20 PM. That extra zero perturbs me.

I've looked through the config files, but can't seem to find anything related to these two things.

---

