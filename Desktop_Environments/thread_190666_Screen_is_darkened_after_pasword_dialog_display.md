---
title: "Screen is darkened after pasword dialog display ?"
date: 2006-06-06
forum: Desktop Environments
---

### Post by Vilius on 2006-06-06
Screen is darkened after pasword dialog display.
How do I remove that efect ?

thanks
Vilius

---

### Post by Ramses de Norre on 2006-06-06
Yeah I don't like it neither, you can't use any other app untill you entered your password. Anyone who knows how to disable it?

---

### Post by Vilius on 2006-06-07
I'ts ok that when you enter pass you can't interfere with other ui, I think there are logical reasons for that. But I want only pass dialog to be displayed without any graphical darkening efects.(sometimes it looks like my screen 'flicks' becouse of that)

---

### Post by underwater on 2006-06-07
I vote that it is a feature not a bug.  I was surprised by it at first, but I've grown to like it very quickly as I now immiedately know what application might need my attention.  For example, the wireless manager immiedately prompts me for a password so it can load and auto connect my wireless.  Things like that.  I like it.

---

### Post by DoktorSeven on 2006-06-07
```
gksudo -g appname
```

> 
(from **man gksudo**)
       --disable-grab, -g

              Disables the "locking" of the keyboard, mouse, and focus done by
              the program when asking for password


So whatever's calling gksudo, add that -g to it.

---

