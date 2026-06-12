---
title: "How to make Internet borwser to open automatically html files"
date: 2008-03-16
forum: Desktop Environments
---

### Post by Acunga on 2008-03-16
I get an ask windwos what I want HTML file to do - run, excute in terminal or display and when I cluck display I open it with the Firefox.So I want when I doublclick it to open in Firefox and when I rightclick - open in Text editor to open in text editor.SO how can I remove this stupid ask windwos?

---

### Post by chewearn on 2008-03-17
Right-click on html file > Properties > Permissions > uncheck "Execute" checkbox.

---

### Post by scramasax on 2008-03-17
So this would perhaps be a file the O.P. has moved over on USB stick.  That would be formatted as FAT32, and that filesystem doesn't understand permissions ... as a consequence, the executable bit gets set when files are copied off it.

But if you wrote an HTML file on the machine, it would be set to rw-r--r-- (i.e. 644) when it was created, so the problem wouldn't arise.

---

### Post by Acunga on 2008-03-18
worked great!But I alone would never even think about such option

---

