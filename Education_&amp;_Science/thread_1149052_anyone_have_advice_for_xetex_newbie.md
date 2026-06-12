---
title: "anyone have advice for xetex newbie?"
date: 2009-05-04
forum: Education &amp; Science
---

### Post by MetapostAddict on 2009-05-04
Hi all,

I'd like to learn more about XeTeX, but I'm having trouble getting started, and I'm wondering if anyone has any advice.

I have the full version of texlive installed, and it supposedly has xetex in it, but...

I downloaded some sample tex files for xetex, but I wasn't able to compile them.   I got all sorts of error messages.

Any advice on how to get going with XeTeX?  

many thanks.

---

### Post by bryncoles on 2009-05-06
never heard of XeTeX myself, but im just starting trying to learn LaTeX. i guess its the same. 

i would google for 'a not so short introduction to latex' -p its a free pdf guide to get you started. 

also, i am spending time using TeXmaker, as its as WYSIWYG as you will find with latex. i recommend it while you're getting started.

can you post the error messages you get (not that ill be able to help)?

---

### Post by hugmenot on 2009-05-06
what are the errors?

---

### Post by Garzo on 2009-05-06
I use XeLaTeX regularly for multilingual document preparation. Without knowing what you're doing and what the errors are, this could be any number of things. The process should have spawned a .log file that you could quote. A couple of frequent errors are:
[LIST=1]
[*]Trying to compile a XeTeX or XeLaTeX file without using the commands [COLOR="Magenta"]xetex[/COLOR] or [COLOR="Magenta"]xelatex[/COLOR], but using non-XeTeX engines; this is especially common if you're using a graphical IDE: use the correct command
[*]Compiling a source that someone has written that declares fonts that aren't on your machine: change the script for a system font you know you have, and get its name right
[/LIST]

The main forum for XeTeX help is the mailing list ([http://www.tug.org/mailman/listinfo/xetex](http://www.tug.org/mailman/listinfo/xetex)), which is always busy and helpful.

Gareth.

---

