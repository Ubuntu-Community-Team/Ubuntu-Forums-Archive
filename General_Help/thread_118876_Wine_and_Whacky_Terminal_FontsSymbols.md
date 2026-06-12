---
title: "Wine and Whacky Terminal Fonts/Symbols"
date: 2006-01-17
forum: General Help
---

### Post by bluevoodoo1 on 2006-01-17
Recently installed Finale 2003 with Wine, works well (minus MIDI), except terminal fonts have gone crazy. Here's a screenshot. Any ideas to remedy this?

---

### Post by lucaflea on 2006-01-31
hi. 2 questions: can you print with finale? how do you do it? second one: how did you put the music-player on the bottom-application-bar???

luca

---

### Post by bluevoodoo1 on 2006-01-31
[QUOTE=lucaflea]hi. 2 questions: can you print with finale? how do you do it?[/QUOTE]

Hmm, actually, I haven't tried printing with it, but I would have to assume that it doesn't work. I don't have Finale or wine installed now (because of the font problem) so I can't test it.

> 
second one: how did you put the music-player on the bottom-application-bar???

You mean the finale icon on the application bar?? I googled "finale icon" and came to this site. (it's long, you'll have to copy+paste it)

```
http://images.google.com/imgres?imgurl=http://www.wellesley.edu/Computing/Finale/FinaleIcon.jpg&imgrefurl=http://www.wellesley.edu/Computing/Finale/&h=39&w=37&sz=2&tbnid=1BayJy4TrZPmsM:&tbnh=39&tbnw=37&hl=en&start=44&prev=/images%3Fq%3Dfinale%2Bicon%26start%3D40%26svnum%3D10%26hl%3Den%26lr%3D%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-US:official%26sa%3DN"]http://images.google.com/imgres?imgurl=http://www.wellesley.edu/Computing/Finale/FinaleIcon.jpg&imgrefurl=http://www.wellesley.edu/Computing/Finale/&h=39&w=37&sz=2&tbnid=1BayJy4TrZPmsM:&tbnh=39&tbnw=37&hl=en&start=44&prev=/images%3Fq%3Dfinale%2Bicon%26start%3D40%26svnum%3D10%26hl%3Den%26lr%3D%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-US:official%26sa%3DN
```

Then I used the GIMP to adjust its size. Then I put it in the pixmap folder (/usr/share/pixmaps) then created a custom command. Something like... 

```

wine .wine/c_drive/program\ files/FINALE/FINALE.exe

```

Something like that. (it's just the exact path to the .exe finale file). Again, I don't have either installed so I can't remember the exact path.

---

### Post by bluevoodoo1 on 2006-02-09
[QUOTE=lucaflea]can you print with finale? how do you do it?[/QUOTE]

I tested it today, and the printing does work. Once I go to File > Print it will print. I can't change any of the printer settings though. Oh well. Is your printer set up to work with other, 'normal' Linux applications?


Oh and I solved my font problem...

I just copied and pasted a bunch of the true type fonts from 

/usr/share/fonts/truetype/freefont 

to 

.wine/drive_c/windows/fonts

no more whacky terminal fonts

---

