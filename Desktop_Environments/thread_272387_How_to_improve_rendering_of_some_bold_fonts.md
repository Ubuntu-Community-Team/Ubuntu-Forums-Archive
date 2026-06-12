---
title: "How to improve rendering of some bold fonts"
date: 2006-10-06
forum: Desktop Environments
---

### Post by quvil on 2006-10-06
Hello everybody.

Generally, X renders ttf fonts exactly as Windows does, but there is the following problem: usually .ttf file for a particular font contains a number of styles: Regular, Bold, Italic and Bold Italic, so that when application uses bold font, it uses Bold style instead of Regular. But when .ttf doesn't contain Bold style and bold font is required, boldness is emulated. Now, Windows emulates boldness perfectly, but X does it really bad. For example, see the difference between Windows and X in bold font rendering in the following screnshots:

Windows:[monaco-win-10pt_1.tif]("http://xt.nm.ru/monaco-win-10pt_1.tif") 
Linux:[monaco-lin-09pt_1.tif]("http://xt.nm.ru/monaco-lin-09pt_1.tif")

(you can also see that generally X renders that particular font incorrectly, that is - font's width height and size are wrong. Because of that I upgraded to Edgy, and those problems were fixed, but problem with bold remained)

What can be done to fix the problem?

---

