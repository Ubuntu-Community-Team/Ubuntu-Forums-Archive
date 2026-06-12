---
title: "latex-cjk-chinese on English computer"
date: 2008-03-22
forum: Education &amp; Science
---

### Post by mathiasv on 2008-03-22
Hey. I would like to be able to write simplified Chinese on an otherwise English computer with Kubuntu 7.10 Gutsy Gibbon - Release amd64

I followed [these directions]("http://ubuntuforums.org/showthread.php?t=452018") and my scim works fine in both bash, vim, kate and in openoffice. Open office can even produce pdf-files.

But I would like to use the latex-cjk package, so I followed the description of the latex-cjk-chinese and installed the fonts in hbf-jfs56 ("if you want to use bitmap fonts in simplified Chinese").

I have tried to compile [this utf8-file]("http://ubuntuforums.org/showthread.php?t=350101&highlight=chinese+latex+cjk") as well as GB.tex and CJKutf8.tex from /usr/share/doc/latex-cjk-common/examples different variations from the web with different encodings (utf8, gbk, gb2312 etc) in vim and kate. But when latex reaches the chinese characters in the file I get this:
```
 
! Undefined control sequence.
try@size@range ...extract@rangefontinfo font@info
                                                  <-*>@nil <@nnil
l.42   &#26412;
          &#24120;&#38382;&#38382;&#31572;&#38598;~(FAQ list)~&#26159;&#20174;&#19968;&#20123;&#32463;&#24120;&#34987;&#38382;&#21040;&#30340;&#38382;&#39064;&#21450;...

```

Anyone knows how to make this work? Thanks.
Mathias.

---

### Post by mathiasv on 2008-05-21
Nobody has any idea how to do this? Openoffice works, but not happy with it: Formatting, things jumping around... 

How do I do do it in Latex? Help really appreciated.

---

### Post by pabix on 2008-06-28
Hello, I have posted a method for use of Chinese fonts with LaTeX:

[http://ubuntuforums.org/showthread.php?t=350101]("http://ubuntuforums.org/showthread.php?t=350101")

---

