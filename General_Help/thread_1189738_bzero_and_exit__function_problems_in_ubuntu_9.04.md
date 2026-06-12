---
title: "bzero and exit  function problems in ubuntu 9.04"
date: 2009-06-17
forum: General Help
---

### Post by b_n_reddy224 on 2009-06-17
I have a problem when using bzero and exit() functions in socket programming. When I have compiled the program I'm getting the error.  
I'm using gcc compiler on ubuntu 9.04

Even when I have given   **man bzero** , it is showing nothing.

any help on this will be appreciated....

---

### Post by abhilashm86 on 2009-06-17
what all libraries you included?? actually <stdlib.h> contains exit and other functions..........

---

### Post by b_n_reddy224 on 2009-06-17
why it is not showing any information when I have given **man exit **and **man bzero** ?

---

### Post by PmDematagoda on 2009-06-17
You probably haven't installed the man pages which could be done with:-
```
sudo apt-get install man
```

---

### Post by lloyd_b on 2009-06-17
> **PmDematagoda said:**
> You probably haven't installed the man pages which could be done with:-
```
sudo apt-get install man
```

The "man" package is part of the standard install, and just provides the "man" program (among other things).  The "manpages" package provides many man pages, and is part of the standard install, but does not contain the pages the OP is looking for.

man(2) (system calls) and man(3) (standard library functions) are contained in the package "manpages-dev".  So ```
sudo apt-get install manpages-dev
``` should take care of this.

I've never understood why "manpages-dev" isn't included in "build-essential".

Lloyd B.

---

### Post by lloyd_b on 2009-06-17
> **b_n_reddy224 said:**
> I have a problem when using bzero and exit() functions in socket programming. When I have compiled the program I'm getting the error.  
I'm using gcc compiler on ubuntu 9.04

Even when I have given   **man bzero** , it is showing nothing.

any help on this will be appreciated....

It would help us a lot if you told us what the error was, and if possible include the code where you're using bzero() and exit()...

Lloyd B.

---

### Post by b_n_reddy224 on 2009-06-17
after installing manpages-dev, it is working fine
I have given the following command to resolve this issue.

[HTML]sudo apt-get install manpages-dev[/HTML][FONT=monospace]

thanks every one for helping me.
[/FONT]

---

