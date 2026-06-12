---
title: "adding varible on every call to single function"
date: 2011-10-05
forum: Education &amp; Science
---

### Post by yairsuari on 2011-10-05
Hello

i am runing an ecological model in fortran which calls a single subroutine from about 200 different places in  a source code divided to about 50 text files. after ca. 2 days of running i have a devision by zero and the model blows up - this is a tough thing to debug. if i use debug flag on compilation this will take ages.


what i want to do is change every call to this function that currently look like this:
call flux_vector( a,b, c) 
to:
call flux_vector( a,b, c,NUMBER)

Where number contains a different number on each call

And then inside the function change the section that stops execution to print where it was called from

write(6,*)NUMBER
stop

i know this can be done using perl or sed/awk but i am not  experinced enough to do that, can someone please help?


thank for the time
yair

---

### Post by yairsuari on 2011-10-06
This was achived by using -taraceback option when debugging and using compiler function that produces call stack and stops execution

---

