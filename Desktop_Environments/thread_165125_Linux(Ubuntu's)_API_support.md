---
title: "Linux(Ubuntu's) API support"
date: 2006-04-24
forum: Desktop Environments
---

### Post by index_0@ya.com on 2006-04-24
Hi thr,

is thr any way to browse thru linux api docs ,
like  MS gives to Windows in MSDN ,

i am a newbie in programming in linux , and was looking for a method to 
fork a process in C++,  like "system()" method in visual c++ for windows

Unfortunately, i could nt find the header files that gives me support 
to this problem.

So , i thr a way to browse thru all header files and thier supported methods,
(like the java documentation) ?

Cheers.

---

### Post by Nikusan on 2006-04-24
[QUOTE=index_0@ya.com]Hi thr,

is thr any way to browse thru linux api docs ,
like  MS gives to Windows in MSDN ,

i am a newbie in programming in linux , and was looking for a method to 
fork a process in C++,  like "system()" method in visual c++ for windows

Unfortunately, i could nt find the header files that gives me support 
to this problem.

So , i thr a way to browse thru all header files and thier supported methods,
(like the java documentation) ?

Cheers.[/QUOTE]

Are you familiar with boost? There is boost threading stuff in the repositories.

try installing libboost-thread-dev

---

### Post by index_0@ya.com on 2006-04-24
Hi ..
 well i am not with my ubuntu desktop right now here, 
 can u tell me wht it is ?

thx

---

### Post by Nikusan on 2006-04-24
[QUOTE=index_0@ya.com]Hi ..
 well i am not with my ubuntu desktop right now here, 
 can u tell me wht it is ?

thx[/QUOTE]

Boost is a set of c++ libraries that do a lot of cool stuff not in the STL, such as greorian calendars, more containers, iterators and algorithms.

You might be interested in [Boost.Threads]("http://www.boost.org/doc/html/threads.html").

---

### Post by index_0@ya.com on 2006-04-24
ok .. 
it seems boost have thier own version of wrapper to compile c++ .
But, i was asking looking for documentation for built-in header files like linux.h, stdlib.h  and so on

(it seems boost libs doesnt have api to fork a process from code,i mean to run a executable file .!)

---

### Post by index_0@ya.com on 2006-04-24
any suggestions ? pls ...

---

### Post by cleric on 2006-04-24
Yes, depending on what you want to do.  First there is fork() this is obviously for recursion and there's exec().  exec() allows you to call a different program from inside a first program.

Try doing man 2 fork and man 3 exec and you'll recieve the full rundown on both functions.

---

### Post by nanotube on 2006-04-24
hmm, but that still does not answer the basic question - where is the big api reference for the linux environment? i, too, am interested to know if there is anything like that.

---

### Post by index_0@ya.com on 2006-04-25
yep, ur right , 
sorry for one more silly question..

 in which header is it declared to use it ?

and doesnt thr exist any api manual for linux ?

cheers

---

### Post by nanotube on 2006-04-26
hmm, i was looking around... maybe this: [http://www.linux.org/docs/ldp/howto/HOWTO-INDEX/programming.html](http://www.linux.org/docs/ldp/howto/HOWTO-INDEX/programming.html)
will be helpful.

---

### Post by nanotube on 2006-04-26
or also this free ebook:
[http://www.advancedlinuxprogramming.com/](http://www.advancedlinuxprogramming.com/)

---

### Post by mgol on 2008-04-19
> **cleric said:**
> Try doing man 2 fork and man 3 exec
Where to look for these manuals in Ubuntu 7.10? When I try to do "man 3 exec" I get sth like: "There is no manual for man in chapter 3".

---

### Post by nanotube on 2008-04-22
> **mgol said:**
> Where to look for these manuals in Ubuntu 7.10? When I try to do "man 3 exec" I get sth like: "There is no manual for man in chapter 3".

it looks like these come in separate packages - but i'm not sure which ones... but as soon as you figure out which, i'm sure they are just a quick "apt-get install" away :)

---

### Post by mgol on 2008-04-22
OK, I already know. Most of manuals are in manpages and manpages-dev, or in their localized versions.

---

