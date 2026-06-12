---
title: "Problem with *.tex after transferring from Windows"
date: 2010-10-01
forum: Education &amp; Science
---

### Post by UlrihRekkenin on 2010-10-01
Good time!

I have the problem. Two weeks ago I setted up for my laptop Ubuntu 10.04 instead WindowsVista. In Windows I have written my thesis in TeX notation using TeXnicCenter2.7. 
Now I have a good look at  .tex files and I`m *terrified!!!  *It*`s *stranger things instead Russian letters... I`m sure the problem is in windows code, `cause I can see without any difficulties English letters in surroundings (i.e. \begin{equation} etc) or in equations, but I dunno the correct solution  :(
**It is not good idea to rewrite all(!) files all over again...

Oleg.

---

### Post by radioboy on 2010-10-08
Sounds like an encoding problem.
Check this:
[http://chr15t0ph.wordpress.com/2010/06/04/file-encoding-problems-tex-files-windows-to-mac-os-x/]("http://chr15t0ph.wordpress.com/2010/06/04/file-encoding-problems-tex-files-windows-to-mac-os-x/")
That's for Mac OS X, but the problem is the same, and the iconv and recode packages exist in Linux.

Of course in this case you install them using:
```
sudo apt-get install recode iconv
```

---

