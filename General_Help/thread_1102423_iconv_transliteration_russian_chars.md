---
title: "iconv transliteration russian chars"
date: 2009-03-21
forum: General Help
---

### Post by BabySnake on 2009-03-21
Hi!

I'm trying to convert from utf8 to us-ascii/TRANSLIT (iconv -f utf-8 -t us-ascii//TRANSLIT sometext). It works for french and german etc (removing accents etc). The problem I'm having occurs when I try to convert cyrillic/russian characters to us-ascii/TRANSLIT (i.e &#1090;&#1088;&#1072;&#1082;&#1090;&#1086;&#1088; => traktor). This results in a bunch of questionmarks I'm on Ubuntu 8.10 by the way, I installed russian language on it. Did anyone outhere get it to work with cyrillic/russian characters?

best regards!

---

### Post by olegmd on 2009-09-16
[SIZE=3]Hello. 
You can see this site : **[http://translit.cc/](http://translit.cc/)**

1. Deselect "Auto Convert"
2. Type your word; for example: "**traktor**"
3. Click "[/SIZE][SIZE=3]&#1050;&#1080;&#1088;&#1080;&#1083;&#1083;&#1080;&#1094;&#1072;"
4. And you get : "**&#1090;&#1088;&#1072;&#1082;&#1090;&#1086;&#1088;**"

[/SIZE]   [SIZE=2][SIZE=3]I wold like to have a program that makes same thing off line, without Internet :)

Regards 
Oleg.[/SIZE] 
[/SIZE]

---

### Post by BabySnake on 2009-09-16
ok thanks... i'd rather have it working on my own system though...

/B

---

### Post by 4xel on 2010-01-07
Hi , the best way to get Russian transliteration to work is to install ibus.
 I had to upgrade my Ubuntu to 9.10 (Karmic) though.
Here is some useful advice
[http://ohioloco.ubuntuforums.org/showpost.php?p=8602877&postcount=5](http://ohioloco.ubuntuforums.org/showpost.php?p=8602877&postcount=5)
and here is the instructions on how to install ibus
[http://code.google.com/p/ibus/wiki/Ubuntu](http://code.google.com/p/ibus/wiki/Ubuntu)

Then just add Russian > translit to your Input Methods from an ibus preferences window.

Avoid the ibus-table-translit package its just way too awkward.

---

### Post by BabySnake on 2010-04-18
Thanks, for the tip!

However, there is no real documentation of it as far as I can tell...

What does it do? How do you use it?

---

