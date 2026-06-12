---
title: "[SOLVED] Strange characters in .txt"
date: 2009-01-07
forum: General Help
---

### Post by afeasfaerw23231233 on 2009-01-07
When I use gedit to create a .txt and copy it to a windows machine, notepad would display some strange characters like this:

How can I fix it? Thanks.

---

### Post by kbuel on 2009-01-07
hmmm,  you might want to use the unix2dos command on that file:

unix2dos myfile


unix and dos use different line terminators.

---

### Post by CoffeyW on 2009-01-07
It does seen to be the new line characters however you should be able to open the file in wordpad and save it as a .txt that notepad will be able to open fine. gedit doesn't have any problems opening .txt files from wordpad.

---

### Post by afeasfaerw23231233 on 2009-01-07
Thanks! Both suggestions work. Problem solved.

---

