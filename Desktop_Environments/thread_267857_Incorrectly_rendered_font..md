---
title: "Incorrectly rendered font."
date: 2006-09-29
forum: Desktop Environments
---

### Post by quvil on 2006-09-29
Hello everybody.

For programming I use monospaced True Type font called Monaco 
(available from here: [http://www.gringod.com/wp-upload/MONACO.TTF](http://www.gringod.com/wp-upload/MONACO.TTF). I think 
that it is free, but I am not sure. Some time ago it was available for
downloading from many sites, but now most links had disappeared). It looks
very good on Windows, but X (Linux, 0x86) renders that font incorrectly - the 
spacing is wrong, font's width and size is incorrect and additionally, though
the .ttf file includes Regular, Italic, Bold and Bold Italic styles X
is able to extract only Regular style, and when bold font is needed X
emulates boldness, and does it very badly.

Here are some screenshots for comparison:

Windows, 10pt: [http://xt.nm.ru/monaco-win-10pt_2.tif](http://xt.nm.ru/monaco-win-10pt_2.tif)
Linux, 10pt: [http://xt.nm.ru/monaco-lin-10pt_2.tif](http://xt.nm.ru/monaco-lin-10pt_2.tif)
Linux, 9pt: [http://xt.nm.ru/monaco-lin-09pt_2.tif](http://xt.nm.ru/monaco-lin-09pt_2.tif)

and another screnshot (note how bold characters are rendered):

Windows, 10pt: [http://xt.nm.ru/monaco-win-10pt_1.tif](http://xt.nm.ru/monaco-win-10pt_1.tif)
Linux, 10pt: [http://xt.nm.ru/monaco-lin-10pt_1.tif](http://xt.nm.ru/monaco-lin-10pt_1.tif)
Linux, 9pt: [http://xt.nm.ru/monaco-lin-09pt_1.tif](http://xt.nm.ru/monaco-lin-09pt_1.tif)


Now, other monospaced fonts are rendered identically correctly both under 
Windows and under X.

What could be wrong with how X displays Monaco?

---

