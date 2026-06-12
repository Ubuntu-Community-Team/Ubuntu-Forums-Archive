---
title: "can't compile with gcc"
date: 2010-07-20
forum: Desktop Environments
---

### Post by jesaisrien on 2010-07-20
Hi experts!

I too have one of those nagging "stdio.h file or directory not found" things when I try to compile with gcc.

I do the following:

gcc hello.c

which gives:

hello.c:1:20: error:  stdio.h: No such file or directory
hello.c: In function &#8216;main&#8217;:
hello.c:5: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;

I have reinstalled libc6-dev.

I have reinstalled build-essential.

"Locate stdio.h" pulls up the following;

/home/fredx/Downloads/stellarium/stellarium-0.10.4/src/external/kdewin32/stdio.h
/usr/include/stdio.h
/usr/include/bits/stdio.h
/usr/include/boost/iostreams/filter/stdio.hpp
/usr/include/c++/4.2/tr1/stdio.h
/usr/include/c++/4.4/tr1/stdio.h
/usr/include/glib-2.0/glib/gstdio.h
/usr/include/unicode/ustdio.h
/usr/lib/perl/5.10.0/CORE/nostdio.h

echo $PATH gives the following:

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

I've added "/usr/include" to the end of $PATH,

PATH=$PATH:/usr/include

giving:

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/include

but that doesn't change the results.

Using ubuntu jaunty 9.04

I'm lost. Any suggestions?

I should add that hello.c looks like this;

#include < stdio.h>

void main()
{
    printf("\nHello, World!\n");	
}

---

### Post by lkjoel on 2010-07-20
> **jesaisrien said:**
> Hi experts!

I too have one of those nagging "stdio.h file or directory not found" things when I try to compile with gcc.

I do the following:

gcc hello.c

which gives:

hello.c:1:20: error:  stdio.h: No such file or directory
hello.c: In function ‘main’:
hello.c:5: warning: incompatible implicit declaration of built-in function ‘printf’

I have reinstalled libc6-dev.

I have reinstalled build-essential.

"Locate stdio.h" pulls up the following;

/home/fredx/Downloads/stellarium/stellarium-0.10.4/src/external/kdewin32/stdio.h
/usr/include/stdio.h
/usr/include/bits/stdio.h
/usr/include/boost/iostreams/filter/stdio.hpp
/usr/include/c++/4.2/tr1/stdio.h
/usr/include/c++/4.4/tr1/stdio.h
/usr/include/glib-2.0/glib/gstdio.h
/usr/include/unicode/ustdio.h
/usr/lib/perl/5.10.0/CORE/nostdio.h

echo $PATH gives the following:

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

I've added "/usr/include" to the end of $PATH,

PATH=$PATH:/usr/include

giving:

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/include

but that doesn't change the results.

Using ubuntu jaunty 9.04

I'm lost. Any suggestions?

I should add that hello.c looks like this;

#include < stdio.h>

void main()
{
    printf("\nHello, World!\n");    
}
```
echo "
PATH=$PATH:/usr/include" >> ~/.bashrc
source ~/.bashrc
```
Try that and see if it works.

---

### Post by jesaisrien on 2010-07-21
Thank you lkjoel for your help, but that did not work.

Since I don't really know what I'm doing that didn't surprise me though. I tried running your suggestion as one line, then as two with the second line being, "source ~/.bashrc.

Please excuse my ignorance, but I think what your code does is add,"/usr/include" to the end of PATH in .bashrc, which it did do. I don't know what, " source ~/.bashrc" does however.

In any case, I'm still getting the same thing:

hello.c:1:20: error: stdio.h: No such file or directory
hello.c: In function ‘main’:
hello.c:5: warning: incompatible implicit declaration of built-in function ‘printf’

---

### Post by lkjoel on 2010-07-21
"source ~/.bashrc" will just make the changes applied.

---

### Post by 3Miro on 2010-07-21
> **jesaisrien said:**
> 
#include < stdio.h>

void main()
{
    printf("\nHello, World!\n");	
}

You have a space between < and stdio.h>, Try removing it. If this doesn't help, try going with 
```
#include "stdio.h"
```

---

### Post by jesaisrien on 2010-07-21
Wow!! Removing the space did it.

Very cool! Thank you 3Miro. I think including, "/usr/include" onto the end of BASH in ~/.bashrc was probably essential too, but removing that space finally did it.

Just for the record, using, " #include "stdio.h" instead of, " #include <stdio.h>" also worked.

I have so much to learn!

It's always something so simple; but not really.

---

### Post by 3Miro on 2010-07-21
> **jesaisrien said:**
> Wow!! Removing the space did it.

Very cool! Thank you 3Miro. I think including, "/usr/include" onto the end of BASH in ~/.bashrc was probably essential too, but removing that space finally did it.

Just for the record, using, " #include "stdio.h" instead of, " #include <stdio.h>" also worked.

I have so much to learn!

It's always something so simple; but not really.

<stdio.h> is the correct way, not I am sure about the difference. You should use "myfile.h" for files that you make and <...> for system files like stdio.h, stdlib.h, iostream and so on.

Catching things like the space comes with practice, nothing more, which I guess is the good news, however, the bad one is that after a decade or so of professional programming I am still learning myself and there doesn't seem to be an end to it.

---

