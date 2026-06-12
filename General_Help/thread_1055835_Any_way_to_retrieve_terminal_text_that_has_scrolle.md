---
title: "Any way to retrieve terminal text that has scrolled off the screen?"
date: 2009-01-31
forum: General Help
---

### Post by DirtDawg on 2009-01-31
Using gnome-terminal, I had some error messages I wanted to keep, but then I used a command that created massive output and pushed the error message off the 'top' of the terminal screen (that is, beyond where I can scroll up).

Now I'm wondering if it's possible to retrieve that text since I can't easily recreate the error.

Thanks

---

### Post by DirtDawg on 2009-01-31
Pardon my *bump*.

---

### Post by blackgr on 2009-01-31
shift and up arrow

---

### Post by geirha on 2009-01-31
I'm afraid it is gone then. Might be a good idea to increase the number of lines of history in gnome-terminal, so that at least if it happens again, you stand a better chance of retrieving the error message.

---

### Post by kerry_s on 2009-01-31
> **DirtDawg said:**
> Using gnome-terminal, I had some error messages I wanted to keep, but then I used a command that created massive output and pushed the error message off the 'top' of the terminal screen (that is, beyond where I can scroll up).

Now I'm wondering if it's possible to retrieve that text since I can't easily recreate the error.

Thanks

you can output it to text:
```
command > command.txt
```
or
pipe it through more or less:
```
command | more
or
command | less
```

---

### Post by DirtDawg on 2009-01-31
> **geirha said:**
> I'm afraid it is gone then. Might be a good idea to increase the number of lines of history in gnome-terminal, so that at least if it happens again, you stand a better chance of retrieving the error message.

Alright, I figured that might be the case. I'll be more careful next time and juggle tabs. Is there any way to increase the number of lines gnome-terminal keeps in 'storage' apart from the history? That is, rather than increase the number of saved input commands through history, save a larger set of the output? If that makes sense. This is all very hard to Google. 

Btw, the shift + up arrow didn't work. Instead, it made the letter 'A' in my terminal :)

---

### Post by DirtDawg on 2009-01-31
> **kerry_s said:**
> you can output it to text:
```
command > command.txt
```

Right. I wasn't expecting the error or I would have. Thanks though.

---

### Post by howlingmadhowie on 2009-01-31
> **DirtDawg said:**
> Alright, I figured that might be the case. I'll be more careful next time and juggle tabs. Is there any way to increase the number of lines gnome-terminal keeps in 'storage' apart from the history? That is, rather than increase the number of saved input commands through history, save a larger set of the output? If that makes sense. This is all very hard to Google. 

Btw, the shift + up arrow didn't work. Instead, it made the letter 'A' in my terminal :)

edit->profile preferences-> The 5th tab (defilement in french, don't know what it is in english, probably scrolling or something like that)-> lines of history (default value 512)

---

### Post by DirtDawg on 2009-01-31
> **howlingmadhowie said:**
> edit->profile preferences-> The 5th tab (defilement in french, don't know what it is in english, probably scrolling or something like that)-> lines of history (default value 512)

That's the stuff, thanks! It didn't even occur to me to check the GUI preferences :D

EDIT: Now I see that's what geirha was referring to as well. Thanks for all responses.

---

