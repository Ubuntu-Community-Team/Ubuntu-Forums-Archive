---
title: "Compiz resize plugin causes 100% cpu usage!"
date: 2007-10-23
forum: Desktop Effects &amp; Customization
---

### Post by trv4gr on 2007-10-23
Well, the title says it all.

I have an ATI card, and i managed to get compiz to work in gutsy (in feisty i could not).

Everything works just fine, and i have tested everything!


EXEPT the resize plugin.

When i try to resize a window, the cpu usage jumps instantly (even before the resize finishes) to 100% and everything slows down!

It doesnt matter what resize mode I choose (outline, rectangle etc).

When it happens, the only thing i can do is to reach a console and type killall compiz.real so to kill compiz.

Then everything works fine.

Any ideas? It's unusable!

---

### Post by trv4gr on 2007-10-26
is there anyone else with the same problem ?

---

### Post by My Lost Shadow on 2007-10-26
I have this issue too but I managed to fix it by selecting Normal in the Default Resize Mode under CompizConfig Settings Manager.

My hardware is a Dell Inspiron 6400 with 2GB of RAM, an ATI Mobility X1400 and an Intel Core2Duo proc @ 2GHz running Ubuntu 7.10.

---

### Post by sullenx on 2007-10-26
I had the same problem, i just selected "stretch" for the resize plugin and it stop doing it.  Obviously not a fix but it doesn't bother me much. Someone should fix this bug, it's been like this since Dapper Drake with beryl!

---

### Post by MidBSD on 2007-11-25
Not sure if you're still having this problem but I recently started having this problem too. Fortunately I remembered that I'd recently changed some Compiz settings and realised what had changed.

I'd turned on the Blur module about a week ago. It didn't seem to do anything so I left it on. It was only days later (when I'd forgotten all about turning it on) that my CPU usage would hit 100% every time I resized a window.

Anyway, turning it off resolves the problem for me.

Hope it works for you.

---

### Post by Mwiti on 2008-06-09
I had same problem, normal and strech works fine, outline and rectangle causes 100% cpu usage until reload compiz.

---

