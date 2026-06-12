---
title: "cp- command help"
date: 2009-03-06
forum: General Help
---

### Post by ninja123 on 2009-03-06
I am a newbie.

I need to know how to copy contents of Dir1 into Dir2.

I did man cp but dint quite understand.

I googled it too.


The thing is:

I have Dir1 with files f1, f2 f3.

I made a new directory Dir2.

I want to move f1, f2 and f3 to Dir2.

when i used 

>cp -dpr Dir1 Dir2

or 

>cp -pr Dir1 Dir2

I can see Dir1 as a folder inside Dir2..however I need only the files.


Please help

---

### Post by stumbleUpon on 2009-03-06
if you want to copy the contents

cp Dir1/* Dir2/

or if you want to move completely from Dir1 to Dir2

mv Dir1/* Dir2/

---

### Post by ninja123 on 2009-03-06
thanks a lot!!

---

