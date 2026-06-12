---
title: "gnome-terminal character encoding"
date: 2006-10-09
forum: Desktop Environments
---

### Post by sybaritefury on 2006-10-09
I code every day on a server where the geometry has to be 80x25 and the encoding has to be IBM-850 in order to see and edit the characters properly. 

I'm getting kind of tired of having to go up to the menu bar of gnome-terminal and choose the character encoding every time I open the terminal.  I found the --geometry startup command, but is there some similar command, or a line that I can put in my conf file, that will start me with a different character set automatically?

Thanks.

---

### Post by bitzbox on 2006-11-26
I would also like to know the answer to this.

Anyone?

---

### Post by Yango on 2006-11-26
Same here.
I tried changing order of character encodings in configuration editor, and deleting default encoding but it all failed. When I start terminal it's still there and I have to change it manually.
Waiting for some good solution..
The default encoding is "Current regional settings (UTF-8)" if this changes anything.

---

### Post by bitzbox on 2006-12-07
My solution to this problem is to use Konsole instead of gnome-terminal :) 

In Konsole, I selected Western European (ISO 8859-1) and then saved the profile as my default profile and every time I fire up Konsole, it loads my chosen character encoding -- bye bye UTF-8 :D

---

### Post by mcduck on 2006-12-07
can't you just make the settings you want and save it as a new profile, and then in the command line you use to start the gnome-terminal tell it to use that profile..
```

gnome-terminal --window-with-profile=tterminal --geometry 46x18-65+50
```

(I'm not sure if the character set is saved in profile, but I think it should be)

---

### Post by bitzbox on 2006-12-07
No, the character encoding doesn't seem to be saved in the profile (unless we're doing something wrong?), it has to be changed manually every time gnome-terminal is fired up.

---

### Post by Yango on 2006-12-08
"(I'm not sure if the character set is saved in profile, but I think it should be)"

Nope, it's not. I found out in the configure manager. It's in 'global'.
I'll check out Konsole tomorrow and see what happens.

---

### Post by Yango on 2006-12-09
Multi-gnome-terminal solved the problem for me.
You just have to find a font with needed encoding and it's saved in the profile.
Unfortunately it doesn't look very nice. (maybe it can be tweaked somehow)

---

### Post by Ozzee on 2007-10-04
Is there still no real solution to this problem?

You would think that among the many other command line options available there would be one with which to choose character encoding :(

---

### Post by CromagDK on 2007-10-22
i was actually also hoping someone had an answer to this.
I would like to keep using the gnome-terminal, but i may switch though.
Is it only possible to set this through locales maybe ?

---

### Post by CromagDK on 2007-10-24
found this: [http://osdir.com/ml/gnome.usability/2003-09/msg00193.html](http://osdir.com/ml/gnome.usability/2003-09/msg00193.html)
see if it works. Have not tested.

---

### Post by motin on 2008-02-06
My "solution" was to run "konsole" in gnome-terminal... There you can select the encoding to use.

---

### Post by wojnicki on 2008-03-18
Gnome-terminal sets the encoding accoriding to locale settings, you can alter it as:
```

export LANG=pl_PL
gnome-terminal --disable-factory

```

--disable-factory forces gnome-terminal to spawn another instance, only separate instances can have different default char encodings. I hope it helps.

---

### Post by Ozzee on 2008-04-15
I found a solution to this (kind of).

```
env LANG=fi_FI.ISO-8859-1 gnome-terminal --disable-factory
```

The catch is that the locale has to be installed.

Here are the links I used:
[http://brainstorm.ubuntu.com/idea/3466/](http://brainstorm.ubuntu.com/idea/3466/)
[http://tlug.dnho.net/?q=node/237](http://tlug.dnho.net/?q=node/237)

---

