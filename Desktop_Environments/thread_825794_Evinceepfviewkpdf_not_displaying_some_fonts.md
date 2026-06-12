---
title: "Evince/epfview/kpdf not displaying some fonts"
date: 2008-06-11
forum: Desktop Environments
---

### Post by flo2771 on 2008-06-11
Hello all you Ubuntu-gurus,

I've been having this problem for quite a long time and it really annonys me.

Evince does not display some fonts in certain pdf-files. Sometimes whole pages appear blank and only the pictures are displayed, sometimes only the headings are missing. The same happens with epfdview. However, I can select the text, copy it to the clipboard and paste it somewhere.

If I run those two programs with some pdf-file prone to this problem from xterm, they both print the message 
[I]"some font thing failed
Error: failed to load truetype font"
[/I] some hundred times (the beginning of it scrolls away).

There is **no** problem with xpdf.

Even stranger, if I use the option "print to file" of xpdf to convert a pdf file to .ps, it all appears correctly with evince and epdfview.

KPDF gives me some weird letters, as if I was having some sort of charset-problem...

An example pdf is here:
[http://www.agner.org/optimize/optimizing_cpp.pdf]("http://www.agner.org/optimize/optimizing_cpp.pdf")

Evince/Epdfview won't display all the headings. For example, I'm unable to see the 
[I]"2 Choosing the optimal platform
2.1 Choice of hardware platform"[/I] on page 4 in the middle of it.


Please help!!! :( :( :( :( :(

Thanks in advance.

(I also tried a forum search but came up with nothing else than a unanswered thread of June 2007).

---

### Post by jamily on 2010-06-03
I have the same problem.  Certain mathematics symbols (summation sign for instance) display and print as a solid disk (circle) evince.  The rest displays and prints ok.  And everything is fine with xpdf.  Adobe Reader works fine (but it is not open source :(

---

