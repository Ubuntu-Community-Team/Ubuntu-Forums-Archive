---
title: "Complete n00b / Cannot find compiler"
date: 2006-02-26
forum: Desktop Environments
---

### Post by aqualad on 2006-02-26
Running command:
```
chmod +x configure
sh ./configure
```

I get and error telling me I can't compile C programs, take a look:

```
root@Aqualad:/mnt/shared/Linux Programs/sdl/SDL-1.3.0# sh ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
/bin/sh: /mnt/shared/Linux: No such file or directory
configure: WARNING: `missing' script is too old or missing
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... configure: error: cannot run C compiled programs.
If you meant to cross compile, use `--host'.
See `config.log' for more details.

```

I have gcc and g++ and their dependencies installed via package manager.  I don't know why it can't compile C programs :'(

Tell me if you need to see any part of config.log to help, thanks

---

### Post by nanotube on 2006-02-26
do you have package "build-essential" installed? that contains a bunch of stuff necessary to compile things.

---

### Post by aqualad on 2006-02-26
Yeah, checked package manager and it's marked as installed.

---

### Post by procras on 2006-02-26
> /bin/sh: /mnt/shared/Linux: No such file or directory

Above I see Linux\ Programs
Weird!

Try to rename the directory to Linux_programs 

Just try a simple gcc test program to see if your compiler and linker are working.
--- START hello.c ---
#include <stdio.h>

int
main()
{
	char s[] = "Hello World!";

	printf("%s\n", s);
}
--- END hello.c ---
$ gcc hello.c
$ ./a.out

---

### Post by aqualad on 2006-02-26
I copied your file named hello.c exactly and when I execute the command:
```
root@Aqualad:/mnt/shared/Linux_Programs# sh ./a.out

```

I get this error:

```
./a.out: ./a.out: cannot execute binary file

```

I've programmed in C++ before, so I'm fairly intelligible with it, but your syntax is a little different from my personal preference, but I believe it should compile.

Edit: I tried chmodding hello.c too, just in case and same result

Help?

(and I changed that directory from Linux Programs over to Linux_Programs, sorry bad windows habbit)

---

### Post by xhie on 2006-02-26
> root@Aqualad:/mnt/shared/Linux_Programs# sh ./a.out

get rid of the "sh" before the executable, your confusing it :) Its not a sh script

---

### Post by aqualad on 2006-02-26
I get a permission denied without the sh, i think i have a noexec account or something along those lines (on both the hello.c and the configure file)

---

### Post by aqualad on 2006-02-26
Edit: I've already tried chmodding files

---

### Post by procras on 2006-02-27
hello.c should be a plain file without execute permissions

gcc hello.c should generate a.out and set the permissions autmatically

As mentioned above you should just type
$ ./a.out 
to execute the compiled program

Try 
1) 
$ mkdir testprogram
$ mv hello.c testprogram/
$ cd testprogram
2)
$ gcc hello.c
3) 
$ ls -al

And you should see 
total 24
drwxr-xr-x   2 adrian adrian 4096 2006-02-26 10:43 .
drwxr-xr-x  66 adrian adrian 4096 2006-02-27 21:16 ..
-rwxr-xr-x   1 adrian adrian 9375 2006-02-26 10:43 a.out
-rw-r--r--   1 adrian adrian   84 2006-02-24 01:06 hello.c

Then a simple
./a.out should execute the file

---

