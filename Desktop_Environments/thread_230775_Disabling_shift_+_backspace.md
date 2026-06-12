---
title: "Disabling shift + backspace"
date: 2006-08-06
forum: Desktop Environments
---

### Post by bmonkey on 2006-08-06
This is really annoying.. shift + backspace does the same as ctrl + alt + backspace and it gets me cos when im programming and make a mistake i am usually holding shift by the time i press backspace and then boom all my work is lost.. Can someone please tell me how to disable just shift + backspace and not ctrl + alt + backspace..

Will be greatfully appreciated.
Thanks ;)

---

### Post by _simon_ on 2006-08-06
create an empty document and paste this in and save.

```

xmodmap -e "keycode 22 = BackSpace BackSpace Terminate_Server"

```

make it executable

place it in /usr/local/bin/

add it to session startup

---

### Post by bmonkey on 2006-08-06
Thanks :D When i add it to session start up the command would be

/usr/local/bin/filename  ? 

Just to double check that will just remove the shortcut(shift + backspace) to restart gnome and not ctrl alt backspace?

---

### Post by _simon_ on 2006-08-06
yes that's the right command and yes only disables shift + backspace :)

---

### Post by bmonkey on 2006-08-06
How exactly do i make it executable? 

> sudo chmod 755 /usr/local/bin/disableShift

Like that? Or +x ?

---

### Post by _simon_ on 2006-08-06
I just right click -> permissions and tick the execute boxes ;)

I can never remember chmod usage ](*,)

---

### Post by bmonkey on 2006-08-06
I did that :D but when i check the permissions after i copied it to the /usr/local/bin it is only read/write.. maybe im reading way too deep into this :P

EDIT
--------
Nevermind.. Didnt reload Nautilus :/ heh 

Ty simon for ur help :D really appreciate it

---

### Post by bmonkey on 2006-08-06
p.s It works like a charm :) ty again

---

### Post by _simon_ on 2006-08-06
no problem :)

---

