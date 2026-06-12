---
title: "malloc: ../bash/dispose_cmd.c:241: assertion botched"
date: 2009-02-04
forum: General Help
---

### Post by aegl on 2009-02-04
$ uname -a
Linux agluck-desktop 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64 GNU/Linux

I find that shell scripts that work just fine when I am logged in directly to the system mysteriously fail with an assertion error when I use "ssh" to connect to my machine remotely.

Here is a minimal test case:

$ echo "echo hello" > /tmp/hello
$ chmod 755 /tmp/hello
$ /tmp/hello
hello
$ ssh localhost
Linux agluck-desktop 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64
Last login: Wed Feb  4 12:01:31 2009 from localhost
$ /tmp/hello

malloc: ../bash/dispose_cmd.c:241: assertion botched
free: called with unallocated block argument
Aborting...Aborted
$ 


The problem can be worked around by making sure that the shell scripts start with "#!/bin/bash" ... but this shouldn't be necessary.

I tried attaching strace to the shell before trying to run the script. Things look normal to start with.  A child process is created with clone() and then the execve() call fails with ENOEXEC (as expected for the case of a shell script that doesn't start with #!).

Here is the strace output from the execve() on...

17922 execve("/tmp/hello", ["/tmp/hello"], [/* 29 vars */]) = -1 ENOEXEC (Exec format error)
17922 open("/tmp/hello", O_RDONLY)      = 3
17922 read(3, "echo hello\n", 80)       = 11
17922 close(3)                          = 0
17922 pipe([3, 4])                      = 0
17922 close(3)                          = 0
17922 close(4)                          = 0
17922 rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8 ) = 0
17922 rt_sigprocmask(SIG_SETMASK, [], NULL, 8 ) = 0
17922 rt_sigaction(SIGCHLD, {0x43b3c0, [], SA_RESTORER, 0x7f96e7771060}, {SIG_DFL}, 8 ) = 0
17922 rt_sigaction(SIGINT, {0x44f9d0, [], SA_RESTORER, 0x7f96e7771060}, {SIG_DFL}, 8 ) = 0
17922 rt_sigprocmask(SIG_SETMASK, [], NULL, 8 ) = 0
17922 write(2, "\r\n", 2)               = 2
17922 write(2, "malloc: ../bash/dispose_cmd.c:24"..., 54) = 54
17922 write(2, "free: called with unallocated bl"..., 45) = 45
17922 write(2, "Aborting...", 11)       = 11



I tried the same test on a 32-bit machine that also had 8.10 installed. The shell script put my shell into some tight loop burning 98% cpu time until I hit it with a "kill -9"

Another reference point: A 32-bit 8.04 system (GNU bash, version 3.2.39(1)) does not have this problem.

Another workaround:
$ ssh localhost
Linux agluck-desktop 2.6.27-11-generic #1 SMP Thu Jan 29 19:28:32 UTC 2009 x86_64
Last login: Thu Feb  5 11:06:58 2009 from localhost
$ /tmp/hello

malloc: ../bash/dispose_cmd.c:241: assertion botched
free: called with unallocated block argument
Aborting...Aborted
$ exec /bin/bash
$ /tmp/hello
hello
$ 

Yes ... just replacing the initial copy of bash that
was invoked on login with a new copy is enough to perturb
things so that they work!

---

### Post by BigStan23 on 2009-02-11
I have the exact same problem.  I'm on the 64 bit build of 8.10.

This is definitely a recent issue (only started happening in the last week or so), because I frequently log into my system via ssh.

---

### Post by aegl on 2009-02-11
Interesting that it just broke for you.  Do you remember whether you downloaded updates (does apt-get keep a logfile of which new packages were installed, and when).

I think the cause is in some combination of environment, or library link order.  I pulled a binary of an older version of bash from a 8.04 install disk (bash version 3.1.17) and installed that as /bin/bash.  Didn't help at all.  Exactly the same assertion error.

If I get time, I may pull the sources for bash and see if I can make any sense of what this assertion is checking for ... I'm out of ideas for other ways to figure out what causes this.

---

### Post by aegl on 2009-02-23
I grabbed the source for bash 4.0 from  [http://ftp.gnu.org/gnu/bash/bash-4.0.tar.gz](http://ftp.gnu.org/gnu/bash/bash-4.0.tar.gz) and built it with:

$ ./configure
$ make
$ sudo cp bash /bin

[I made a backup copy of /bin/bash first :-)]

This seems to fix the problem ... shell scripts run quite happily when I use "ssh" to connect to the machine.

---

### Post by aegl on 2009-02-23
Sadly bash4.0 (as configured & built by me) seems to have some serious problems running on 8.10.  It keeps hanging.  Seems to go into infinite loops when sub-processes complete.

---

### Post by capscrew on 2009-02-23
Are you sure this is a bash problem?  I see that sh is not sym-linked to bash, but rather dash.  See below:

```
me@there/bin$ ll|grep sh
-rwxr-xr-x 1 root root 686K 2007-10-05 07:37 bash
-rwxr-xr-x 1 root root  79K 2007-09-29 05:47 dash
lrwxrwxrwx 1 root root    4 2008-05-16 16:31 rbash -> bash
lrwxrwxrwx 1 root root    4 2008-05-16 16:31 sh -> dash
lrwxrwxrwx 1 root root    4 2008-05-16 16:31 sh.distrib -> bash

```

---

### Post by aegl on 2009-02-24
"Are you sure this is a bash problem?"

@capscrew:  Well, the assertion botched message says "bash".  And when I played around with bash4.0 I didn't touch the /bin/sh & /bin/dash links, yet the behavior of the system changed.  So I'm pretty confident that this is a bash problem.

---

### Post by rengalan on 2009-02-26
Hi

I just came across this issue, I'm pretty sure what I did to cause it. I ran this command:

> usermod -s /bin/bash myusername

intending to set my default shell to bash as this user somehow didn't get defaulted to bash but just sh. This did in fact make bash the default but then caused the quoted issue. 

I too am on 64-bit Intrepid. I always access the machine via ssh as it runs headless.

**Update**: wow. that was quick. I seem to have resolved my issue by simply exiting putty and starting a new session, hope it is this easy for the rest of you.

---

### Post by Phkillah on 2009-04-30
Ok, Intrepid 64bits here.

Simply run "/bin/bash my_script" instead of only "my_script"

Solved it for me ;)

Cheers

---

### Post by aegl on 2009-04-30
Just upgraded to 9.04 (Jaunty Jackalope) and the problem no longer occurs. :)

---

### Post by kumud1973 on 2011-01-30
Hi 
   I have installed Ubuntu 9.04  and upgraded to Ubuntu 9.10. While executing shell(bash) script, I observe frequently following error message.
-----------
#<script>
#!/bin/bash

MAXCONCURRENT=20 ./paralellAll
-----------
# error message

SIGINT EXITING

malloc: ../bash/parse.y:1594: assertion botched
free: called with already freed block argument
Aborting..../runapmgt1x: line 17:  4994 Aborted                 MAXCONCURRENT=20 ./paralellAll
-----------

---

