---
title: "My time program acts strange"
date: 2009-04-21
forum: General Help
---

### Post by blingo on 2009-04-21
For some reason I can't pass parameters to 'time' without using full path:

```

:~$ time -V
bash: -V: command not found

real    0m0.142s
user    0m0.112s
sys     0m0.036s

:~$ /usr/bin/time -V
GNU time 1.7

:~$ whereis time
time: /usr/bin/time /usr/include/time.h /usr/share/man/man2/time.2.gz /usr/share/man/man7/time.7.gz /usr/share/man/man1/time.1.gz

```

Any idea's?
Thanks :)

---

### Post by jsowoc on 2009-04-21
I believe that is what "time" is supposed to do. Are you looking for the command "date"?

The command "time" calls the program you give it as an argument. The first command is trying (unsuccessfully) to run the command "-V" and tells you it took 0.1 seconds to return the error.

---

### Post by blingo on 2009-04-21
I will explain,
What I want to do is to run 'time -V' that is for the 'time' program to write it's version number.

On the first command I write 'time -V' and instead of writing the version it treats '-v' is if it was a program.

On the second command I write time's full path, that is I write '/usr/bin/time -V' and there I do see the version number.

What's the difference, why does it work only when I write a full path?

On the third command I try to find out what's being run when I write 'time' without full-path. to my knowledge it is /use/bin/time so I'm clueless...

Thanks.

---

### Post by jsowoc on 2009-04-23
That is really interesting. Time should take additional command line arguments (as described in the man page), but simply running "time" does not.

I would postulate that "time" is a built-in function/alias in bash that calls the program /usr/bin/time, but doesn't handle the arguments properly. Would this be a bug in bash? Bug in time? Should we file a bug report?

Slightly off-topic on this forum, but here is how it behaves in Cygwin:

```
$ which time
/usr/bin/time

$ time --version
bash: --version: command not found

real    0m0.017s
user    0m0.015s
sys     0m0.000s

$ /usr/bin/time --version
GNU time 1.7

$ ls -l /usr/bin/time
-rwxr-x---+ 1 *** Users 96843 Aug 15  2008 /usr/bin/time

$ file /usr/bin/time
/usr/bin/time: MS-DOS executable PE  for MS Windows (console) Intel 80386 32-bit

$ cat /usr/bin/time
cat: /usr/bin/time: No such file or directory
```

---

### Post by ostrm on 2009-04-23
This is actually not a bug. jsowoc is right, there's the bash built-in time as opposed to the binary /somewhere/bin/time. The bash manpage states explicitly, that the only parameter to the bash built-in time is '-p':

```
$ man bash
...
If the time reserved word precedes a pipeline, the elapsed as  well as user 
 and  system  time consumed by its execution are reported when the
pipeline terminates.  The -p option changes the output format  to  that
specified  by  POSIX. The  TIMEFORMAT variable may be set to a format
string that specifies how the timing information should  be  displayed;
see the description of TIMEFORMAT under Shell Variables below.
...
```

---

### Post by blingo on 2009-04-30
So you're saying there's also a built-in time, which is called before the usr/bin/time ?

That would explain it..

---

