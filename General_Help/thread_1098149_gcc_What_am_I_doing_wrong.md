---
title: "gcc: What am I doing wrong?"
date: 2009-03-16
forum: General Help
---

### Post by cmdowns on 2009-03-16
I'm staring a project to try and crosscompile **[qGIS](http://www.qgis.org/)** from my Ubuntu machine (running Hardy Heron) to work on my **[Nokia n800 web tablet](http://en.wikipedia.org/wiki/N800)**.

For this process, I will use the **[ Scratchbox ](http://www.scratchbox.org/)** development environment app.

I'm trying to follow this **[simple tutorial](http://www.scratchbox.org/documentation/docbook/tutorial.html)**. After describing the installation process, the tutorial begins introducing the crosscompiling process by using the "Hello World" example. The tutorial uses the following script for the "Hello World" program:
```
#include <stdio.h>

int main(void) { 
    printf("Hello World!\n");
                    
    return 0;
}

```

I cut and pasted that script into a blank file that I started by simply running ```
 $ sudo gedit 
``` and then saved the file as "hello.c". Then I attempted to compile the script using gcc, again following the instructions from the tutorial and using the following code ```
$ gcc -Wall -o hello hello.c
```

For some reason, this doesn't work. When I run that code, xterm tells me 
```
$ gcc -Wall -o hello hello.c
hello.c:1:19: error: stdio.h: No such file or directory
hello.c: In function ‘main’:
hello.c:4: warning: implicit declaration of function ‘printf’
hello.c:4: warning: incompatible implicit declaration of built-in function ‘printf’

```

I would be much obliged if someone could tell me what I'm doing wrong.
Thanks in advance.

---

### Post by hikaricore on 2009-03-16
You're missing the include file!
Have you installed the appropriate packages?

> stdio.h: No such file or directory

I don't code in C so I can't be of more help however. :p

p.s. You shouldn't have to run gedit with **sudo** unless you're editing system config files.

---

### Post by Bapabooiee on 2009-03-16
sudo apt-get install build-essentials

?

---

### Post by cmdowns on 2009-03-16
> **Bapabooiee said:**
> sudo apt-get install build-essentials

?

OK, I run that code and I get
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essentials
cmdowns@cmdowns-laptop:~/Documents$ 
```

Does that mean I'm missing a repository?

---

### Post by oldos2er on 2009-03-16
The correct package name is build-essential

---

### Post by cmdowns on 2009-03-16
> **oldos2er said:**
> The correct package name is build-essential

That did the trick, thanks!

---

