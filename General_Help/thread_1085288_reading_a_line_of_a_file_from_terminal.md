---
title: "reading a line of a file from terminal"
date: 2009-03-02
forum: General Help
---

### Post by 65daysofstatic on 2009-03-02
hi,
Is there a command in the terminal to read a line of a *.txt?
something like cat but only displaying the first line ..

---

### Post by Locutus_of_Borg on 2009-03-02
head -n 1 <file>

---

### Post by 65daysofstatic on 2009-03-02
thank you man for the fast answer

hehe sorry but I have another question, is it possible to read only the first word of every line of the file?

for example I have:
John Locke
Daniel Faraday

and I want to display only John and Daniel

---

### Post by Locutus_of_Borg on 2009-03-02
head -n 1 <file> | awk '{print( $1 ) }'

---

