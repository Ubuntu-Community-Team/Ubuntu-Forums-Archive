---
title: "imaxima and emacs"
date: 2008-08-25
forum: Education &amp; Science
---

### Post by evillan on 2008-08-25
I'm trying to get [imaxima]("http://members3.jcom.home.ne.jp/imaxima/Site/Welcome.html") and emacs 22.1.1 to play together, but it does not work.

I suspect it has something to do with the code snippet from [this .emacs]("http://members3.jcom.home.ne.jp/imaxima/Site/Set_up_your_Emacs.html"). More specifically, I can't find the path in this code:
```
;;; add to load-path the directory where maxima.el is installed.

;;; If you change the install directory of maxima, the first argument of push must be

;;; changed accordingly.

(push "/usr/local/share/maxima/5.15.0/emacs" load-path)
```

This is what happens:
```

xxx:~$ ls /usr/local/share/
applications/        games/               mime/
desktop-directories/ icons/               ppd/
emacs/               info/                sgml/
fonts/               man/                 xml/
xxx:~$ ls /usr/local/share/

```
(I pressed TAB)

I tried to find something similar:
```

xxx:~$ ls /usr/share/maxima/5.13.0/
demo/    doc/     share/   src/     tests/   xmaxima/ 

```
... but no emacs directory?

I've tried with imaxima 0.99 and 1.0b, nothing works. The output should be like this
[IMG]http://members3.jcom.home.ne.jp/imaxima/Site/Tutorial_of_Imaxima_files/p2.png[/IMG]

When I input that, it outputs
```
(%i2) integrate(f(x),x,minf,inf);
LaTex error in: \int_{ -\infty }^{\infty }{f\left(x\right)\;dx}
(%i3) 
```
so the LaTeX code is there, it is just not rendered to something pretty.

Anybody with experience in imaxima?

---

### Post by fdekens on 2009-02-11
Ahhh! I have the exact same problem on both my Mac and my Ubuntu machine. Can any one figure out what the problem is? I've spend over two hours surfing the web, but can't figure out what the problem is. Note that in both cases, I'm trying to use pdflatex, though LaTeX is installed (it's pdfTeXk, V 3.141592-1.40.3)
Thanks,
Frank

---

