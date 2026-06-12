---
title: "Launch panel"
date: 2008-02-25
forum: Desktop Environments
---

### Post by moonshield on 2008-02-25
hi all

how can I have  this kind of a launch panel 

[http://img521.imageshack.us/my.php?image=702841gv5.gif](http://img521.imageshack.us/my.php?image=702841gv5.gif)


instead of the default one that comes with ubuntu

[http://img521.imageshack.us/my.php?image=ubuntucz5.jpg](http://img521.imageshack.us/my.php?image=ubuntucz5.jpg)




thanks in advance.

---

### Post by devils3cups on 2008-02-25
This seems to be what your looking for. AWN
[http://wiki.awn-project.org/](http://wiki.awn-project.org/)

---

### Post by santiagoward2000 on 2008-02-25
Hi!
As devils3cups said that's AWN.
There are other options. Personally, I use [Kiba-Dock]("http://www.kiba-dock.org").
You can try them both.
Cheers!

---

### Post by tobydeemer on 2008-02-25
Hi guys-

to piggy back the question (but not to derail at all) is this compatible with xfce? Does it cause any unexpected pitfalls? I've been moving toward xfce from gnome slowly, and I did want to incorporate at least that little bit of eye candy. Thanks for any info too.

---

### Post by santiagoward2000 on 2008-02-25
> **tobydeemer said:**
> Hi guys-

to piggy back the question (but not to derail at all) is this compatible with xfce? Does it cause any unexpected pitfalls? I've been moving toward xfce from gnome slowly, and I did want to incorporate at least that little bit of eye candy. Thanks for any info too.

Hi!
Right now I'm using Kiba-Dock on my Xfce with no problem. I leave you here the guide I used to install it: [http://ubuntuforums.org/showthread.php?t=554127&highlight=kiba]("http://ubuntuforums.org/showthread.php?t=554127&highlight=kiba")
The only thing is you have to add **--enable-xfce** after each **./autogen.sh** command. So the first one would be: ```
./autogen.sh --prefix=/usr --exec-prefix=/usr --enable-xfce
```
while the other 3: ```
./autogen.sh --enable-xfce
```
Just know you must have a composite manager enabled to get it running correctly.
I don't know about AWN (although I guess you can use it on Xfce too).
Good luck!

---

### Post by moonshield on 2008-02-26
Thank you all  for your replies. 

I know It was AWN launch panel that I asked for but after I saw kiba-dock it seemed more eyecany to me and I installed it following the link that santiagoward2000 gave.

:)

Take care...

---

### Post by tobydeemer on 2008-02-27
Well, I tried AWN first, and it was cool for a bit, but then I noticed that it kept grabbing the window focus and not letting anything stay active. I was unable to type or enter anything other than by clicking. So I turned it off.

I think I may have a go at Kiba-Dock. Why not?

---

