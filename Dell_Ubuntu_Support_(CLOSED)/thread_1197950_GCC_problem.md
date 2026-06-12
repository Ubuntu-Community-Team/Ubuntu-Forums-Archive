---
title: "GCC problem"
date: 2009-06-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by delogren on 2009-06-26
Howdy,

The Inspiron 15n  arrived on our doorstep 3 days ago.  One of my first goals was to get GCC installed and working.  It seems to be installed, but something ain't right...  Here's a typical bash session:



del@dell-desktop:~/src$ cat hello.c
#include <stdio.h>

main ()
{
    printf ("hello world/n");
}

del@dell-desktop:~/src$ bcc hello.c
del@dell-desktop:~/src$ ./a.out
bash: ./a.out: cannot execute binary file
del@dell-desktop:~/src$



What am I missing here?  Why can't the shell run a.out?

tnx,
--del

---

### Post by coffeeaddict22 on 2009-06-27
Gidday,
IANMOAP (I Am Not Much Of A Programmer :-) ) but 


**del@dell-desktop:~/src$ bcc hello.c** //Shouldn't this be gcc?
**del@dell-desktop:~/src$ ./a.out **  // I think what you're missing is the file needs to be changed to an executable. Try doing ```
chmod u+x
``` first.

---

### Post by delogren on 2009-06-27
> **coffeeaddict22 said:**
> Gidday,
IANMOAP (I Am Not Much Of A Programmer :-) ) but 


**del@dell-desktop:~/src$ bcc hello.c** //Shouldn't this be gcc?
**del@dell-desktop:~/src$ ./a.out **  // I think what you're missing is the file needs to be changed to an executable. Try doing ```
chmod u+x
``` first.


Wow!, Thanks!..

Talk about early-onset senile dementia...  Even though I installed GCC, I typed in bcc.  That's because, back in my ms-dos/windoze days I was using the Borland C compiler.  It turns out that "bcc" is a part of the Ubuntu release of Linux.  It's Bruce's C Compiler for some Intel chip...  No wonder the a.out it produced didn't run....

Now, the next question is, how do I set my path so I can run a.out without the ./  ??

--del

---

### Post by coffeeaddict22 on 2009-06-28
3 ways you can do it, depending on how permanent and widespread you want the change to be.

1) for just the login you're on at the moment, just type```
export PATH=$PATH:/xxxx/xxxx/xxxx
``` into the terminal, where xxx is your path.  As soon as you logout, that'll disappear, so if you're doing something short- term, it'd work well.  
2) If you want to keep the changes and for all users, you'll need to edit the /etc/environment file.
3)if you want it to only affect your login, put the additions in the ~/.bashrc file.
The syntax is PATH = $PATH (this keeps the existing path)
          :/xxxx/xxxx (and you know this bit anyway).

---

### Post by McNils on 2009-06-28
use make when compiling small simple programs like this

```
make hello
```

Creates hello from hello.c

---

### Post by delogren on 2009-06-28
> **coffeeaddict22 said:**
> 3 ways you can do it, depending on how permanent and widespread you want the change to be.

1) for just the login you're on at the moment, just type```
export PATH=$PATH:/xxxx/xxxx/xxxx
``` into the terminal, where xxx is your path.  As soon as you logout, that'll disappear, so if you're doing something short- term, it'd work well.  
2) If you want to keep the changes and for all users, you'll need to edit the /etc/environment file.
3)if you want it to only affect your login, put the additions in the ~/.bashrc file.
The syntax is PATH = $PATH (this keeps the existing path)
          :/xxxx/xxxx (and you know this bit anyway).


Thanks,  

--del

---

### Post by delogren on 2009-06-28
> **McNils said:**
> use make when compiling small simple programs like this

```
make hello
```Creates hello from hello.c


Oh, yep,  make files...

It'll be a while befor I get that nuts...

But, they're useful...


--del

---

### Post by niteshifter on 2009-06-30
> **coffeeaddict22 said:**
> 
3)if you want it to only affect your login, put the additions in the ~/.bashrc file.
The syntax is PATH = $PATH (this keeps the existing path)
          :/xxxx/xxxx (and you know this bit anyway).

Easier still: just create a bin folder in your home folder and put your programs or links to programs there:

```
del@dell-desktop:~$ **mkdir ~/bin**
```

No need to edit files this way. The ~/.profile script will setup $PATH for you.

---

### Post by kixome on 2009-06-30
or just sudo when you execute

---

