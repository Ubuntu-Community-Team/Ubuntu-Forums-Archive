---
title: "Where is font &quot;courier 10 pitch&quot;?"
date: 2006-04-23
forum: Desktop Environments
---

### Post by dgermann on 2006-04-23
Hi--

Where on the file system can I find the font called "courier 10 pitch."

(It gives darker output on my printer, and I would like to put it on the WinXP box I have so we can all use it.)

Thanks!

---

### Post by Nikusan on 2006-04-24
[QUOTE=dgermann]Hi--

Where on the file system can I find the font called "courier 10 pitch."

(It gives darker output on my printer, and I would like to put it on the WinXP box I have so we can all use it.)

Thanks![/QUOTE]

Try looking in /usr/share/fonts

---

### Post by dgermann on 2006-04-25
Daniel--

Thanks for the quick reply.

I looked there, but there is nothing with that name. Several come up on a grep search for 'cou'--any idea which one it is?

```

doug@doug2:~$ grep -r 'cou'  /usr/share/fonts
Binary file /usr/share/fonts/truetype/msttcorefonts/Courier_New.ttf matches
Binary file /usr/share/fonts/truetype/msttcorefonts/cour.ttf matches
Binary file /usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold.ttf matchesBinary file /usr/share/fonts/truetype/msttcorefonts/courbd.ttf matches
Binary file /usr/share/fonts/truetype/msttcorefonts/Courier_New_Italic.ttf matches
Binary file /usr/share/fonts/truetype/msttcorefonts/couri.ttf matches
Binary file /usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold_Italic.ttf matches
Binary file /usr/share/fonts/truetype/msttcorefonts/courbi.ttf matches
Binary file /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman.ttf matches
Binary file /usr/share/fonts/truetype/msttcorefonts/times.ttf matches
Binary file /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold.ttf matches
Binary file /usr/share/fonts/truetype/msttcorefonts/timesbd.ttf matches
Binary file /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold_Italic.ttf matches
Binary file /usr/share/fonts/truetype/msttcorefonts/timesbi.ttf matches
Binary file /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Italic.ttf matches
Binary file /usr/share/fonts/truetype/msttcorefonts/timesi.ttf matches
Binary file /usr/share/fonts/truetype/ttf-punjabi-fonts/Saab.ttf matches
doug@doug2:~$

```

I'd guess it is not one of the msttcorefonts.

Thanks, Daniel!

---

### Post by Barnabooth on 2008-01-07
Agree, gives a nicer look. Courier 10-pitch is located in fonts:///

Just type "fonts:///" in the nautilus adress bar as root an copy the 4 fonts. They are named Courier 10 Pitch (+Italic, Bold, BoldItalic)

Hope this helps, A.O.

---

### Post by dgermann on 2008-01-09
Barnabooth--

Ahh! You have solved the mystery for me after all this time!

Two questions:

1. Out of curiosity, just where is fonts:/// in the file system, if I use the command line?

2. More to the point of what I want to do, can these fonts be copied, and legally, to a WinXP machine? I have tried but XP complains that the font is broken....

Thanks, Barnabooth! :guitar:

---

