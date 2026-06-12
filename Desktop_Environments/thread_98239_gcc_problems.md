---
title: "gcc problems"
date: 2005-12-02
forum: Desktop Environments
---

### Post by alikali on 2005-12-02
I'm new to linux and new to ubuntu. Anyway, I have some gcc problems. 

1)I've installed gcc via apt-get => not all the libraries are in /usr/lib/gcc-lib/ ...
   there are just 10 or so
2) I've installed build-essential => the same result


************
if I try to run a simple c hello world using gcc -o name name.c I get a "No such file or directory error"

If I use in the include section limits.h (installed in /usr/ ... )
                In file included from /usr/lib/gcc-lib/i486-linux/3.3.5/include/syslimits.h:7,
                 from /usr/lib/gcc-lib/i486-linux/3.3.5/include/limits.h:11,
                 from l2.c:15:
/usr/lib/gcc-lib/i486-linux/3.3.5/include/limits.h:122:75: limits.h: No such file or directory

if I try reinstalling gcc
               gcc is already the newest version.
               0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

can anyone give me a solution 'cause I'm puzzled

Thanks, alikali

---

### Post by cwaldbieser on 2005-12-02
[QUOTE=alikali]
if I try to run a simple c hello world using gcc -o name name.c I get a "No such file or directory error"
[/QUOTE]
What is the exact command line you are entering,  and what is the exact error message.

---

### Post by alikali on 2005-12-03
sudo gcc -o l l.c
Password:
l.c:1:20: stdlib.h: No such file or directory
l.c:2:20: unistd.h: No such file or directory
l.c: In function `main':
l.c:7: error: stray '`' in program
l.c:7: error: stray '`' in program
l.c:7: error: `Files' undeclared (first use in this function)
l.c:7: error: (Each undeclared identifier is reported only once
l.c:7: error: for each function it appears in.)
l.c:7: error: syntax error before "in"
l.c:7: error: stray '\' in program
l.c:7:48: empty character constant
l.c:8: error: stray '`' in program
l.c:8: error: syntax error before '/' token
l.c:8:32: empty character constant
l.c:8: error: stray '`' in program
l.c:8: error: stray '`' in program
l.c:8:39: empty character constant
l.c:8: error: stray '`' in program
l.c:8: error: stray '`' in program
l.c:8:47: empty character constant
alikali@kalli:/home$


**********
the file is :

#include <stdlib.h>
#include <unistd.h>
main()
{ printf(``Files in Directory are:$\backslash$n'');
		 execl(`/bin/ls'',``ls'', ``-l'',0);
}

---

### Post by GeneralZod on 2005-12-03
This is rather odd.  Try appending

```

-I /usr/include

```

to the GCC call (this is where stdlib.h is located on my system).

Also, why are you using `` instead of " in your printf?

Edit:

Also, why are you using sudo?

---

### Post by cwaldbieser on 2005-12-05
[QUOTE=alikali]sudo gcc -o l l.c
Password:
l.c:1:20: stdlib.h: No such file or directory
l.c:2:20: unistd.h: No such file or directory
l.c: In function `main':
l.c:7: error: stray '`' in program
l.c:7: error: stray '`' in program
l.c:7: error: `Files' undeclared (first use in this function)
l.c:7: error: (Each undeclared identifier is reported only once
l.c:7: error: for each function it appears in.)
l.c:7: error: syntax error before "in"
l.c:7: error: stray '\' in program
l.c:7:48: empty character constant
l.c:8: error: stray '`' in program
l.c:8: error: syntax error before '/' token
l.c:8:32: empty character constant
l.c:8: error: stray '`' in program
l.c:8: error: stray '`' in program
l.c:8:39: empty character constant
l.c:8: error: stray '`' in program
l.c:8: error: stray '`' in program
l.c:8:47: empty character constant
alikali@kalli:/home$


**********
the file is :

#include <stdlib.h>
#include <unistd.h>
main()
{ printf(``Files in Directory are:$\backslash$n'');
		 execl(`/bin/ls'',``ls'', ``-l'',0);
}[/QUOTE]

General Zod is correct.  Your program should look like this:
```

#include <stdlib.h>
#include <unistd.h>
main()
{ 
	printf("Files in Directory are:$\backslash$n");
	execl("/bin/ls","ls", "-l", 0);
}


```
The strange quoting you are using is causing most of your errors.  This compiles on my PC, but since you are havin problems finding "stdlib.h" on your PC, I would suggest you open up synaptic and search for the build-essentials package.  I would try re-installing that and see if the standard library includes are copied to where they are supposed to be, then.

---

### Post by alikali on 2005-12-06
I've reinstalled build-essentials and everything is up and running. 

Thanks a lot

---

