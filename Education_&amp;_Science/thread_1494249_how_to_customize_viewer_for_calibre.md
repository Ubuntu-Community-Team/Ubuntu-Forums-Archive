---
title: "how to customize viewer for calibre"
date: 2010-05-26
forum: Education &amp; Science
---

### Post by tanyeun on 2010-05-26
hi guys,

I don't really like the default viewer for calibre
can I customize specific viewer for specific format?

thx,

David

---

### Post by tanyeun on 2010-05-28
thx to everyone who offer help in Mobile read
[http://www.mobileread.com/forums/showthread.php?p=930899&posted=1#post930899](http://www.mobileread.com/forums/showthread.php?p=930899&posted=1#post930899)

I finally be able to solved the issue

calibre use xdg-open to open files instead of 
it's own viewer

as expected
$ xdg-open file1.pdf
opens file1.pdf using xpdf
after I customise it with
$ xdg-mime default evince.desktop application/pdf
it doesn't help at all
then I figured that
$ gnome-open file1.pdf
did the task I want

finally, I add "export DE=gnome" to ~/.bashrc
the problem solved

:D

---

