---
title: "&quot; No such file or directory&quot; for an exisiting executable file"
date: 2009-01-29
forum: General Help
---

### Post by baosheng on 2009-01-29
It really makes me crazy when you see an executable file over there but the shell said "No such file or directory."

I found this problem while running many commercial software,like Cadence Iscape, the package manager of Cadence software. 

For example, I have this executable "java" right under current directory :

```
forrest@fMRI:~/Desktop/iscape/runtime/LNX86/bin$ ls
ControlPanel  java  java_vm  javaws  keytool  kinit  klist  ktab  orbd  pack200  policytool  rmid  rmiregistry  servertool  tnameserv  unpack200

```

But I just can't run it: 
```

forrest@fMRI:~/Desktop/iscape/runtime/LNX86/bin$ ./java
bash: ./java: No such file or directory
```

The Java virtual machine is right over there but Iscape just tell me no such file or directory.
```
forrest@fMRI:~/Desktop/iscape/bin$ sh iscape.sh 
Initializing InstallScape using JVM at /home/forrest/Desktop/iscape/runtime/LNX86/bin/java. This might take some time...
exec: 212: /home/forrest/Desktop/iscape/runtime/LNX86/bin/java: not found

```

Do anyone here know the reason my shell said "No such file or directory" for an existing file?

---

### Post by cariboo on 2009-01-29
When you try to run java it should give you a help screen the java executeable should be located in /usr/bin. To run your script you're missing one thing

[CODEforrest@fMRI:~/Desktop/iscape/bin$ sh ./iscape.sh 
][/CODE]

note the ./

Jim

---

### Post by baosheng on 2009-01-30
No, I don't it's the java's problem since the java VM comes with this package and the shell said no such java VM. 

And, as to the ./,  i tried your idea and it didn't work.

```
forrest@fMRI:~/Desktop/iscape/bin$ sh ./iscape.sh
Initializing InstallScape using JVM at /home/forrest/Desktop/iscape/runtime/LNX86/bin/java. This might take some time...
exec: 212: /home/forrest/Desktop/iscape/runtime/LNX86/bin/java: not found
```

---

### Post by lisati on 2009-01-30
I don't know why but it looks like iscape.sh is looking in the wrong place.....

---

### Post by alphaniner on 2009-01-30
I know you said it's an executable, but are you sure the permissions allow it to be executed?

Do an 'ls -l' in the directory and make sure the permissions include the necessary x's, ie:

```
-rw[COLOR="Red"]**x**[/COLOR]r-[COLOR="Red"]**x**[/COLOR]r-[COLOR="Red"]**x**[/COLOR] 1 ubuntu ubuntu 3152 2009-01-30 04:55 network.sh
```

If any are unset, do 'chmod a+x java' just to be sure that's not the cause.

---

### Post by PointyWombat on 2009-01-30
Hi,
Please post the output of a long listing "ls -l"

Also post output of:

"ls -l /home/forrest/Desktop/iscape/runtime/LNX86/bin/java"

---

### Post by baosheng on 2009-01-30
> **lisati said:**
> I don't know why but it looks like iscape.sh is looking in the wrong place.....

No, I confirmed that iscape.sh is looking at java VM at the right path.

---

### Post by baosheng on 2009-01-30
> **PointyWombat said:**
> Hi,
Please post the output of a long listing "ls -l"

Also post output of:

"ls -l /home/forrest/Desktop/iscape/runtime/LNX86/bin/java"

I even gave it 0777. 

```
forrest@fMRI:~/Desktop/iscape/runtime/LNX86/bin$ ls -l /home/forrest/Desktop/iscape/runtime/LNX86/bin/java
-rwxrwxrwx 1 forrest forrest 65076 2006-11-09 17:03 /home/forrest/Desktop/iscape/runtime/LNX86/bin/java

```

But it doesn't work. I can't believe why.

```
forrest@fMRI:~/Desktop/iscape/runtime/LNX86/bin$ chmod a+x java
forrest@fMRI:~/Desktop/iscape/runtime/LNX86/bin$ ./java
-bash: ./java: No such file or directory
```

---

### Post by lisati on 2009-01-30
> **baosheng said:**
> No, I confirmed that iscape.sh is looking at java VM at the right path.

Hmmmm.... just that something in the path names in the prompt and the error message(s) didn't look right when I first read the posts.... I might come back some other time and have another look. The idea of checking permissions (+X etc) also occurred to me but I forgot to mention it.

Good luck finding a solution.

---

### Post by alphaniner on 2009-01-30
I don't know if it means anything, but I noticed the second time you showed the output of trying to run java it was

```
-bash: ./java: No such file or directory
```

whereas the first time it was

```
bash: ./java: No such file or directory
```

Is that '-' a typo or something?  Weird.

Unfortunately, I don't have anything else to offer you.  Good luck.

---

### Post by PointyWombat on 2009-01-30
Odd.. from that directory, please post output of 'file ./java'

Thanks.

---

### Post by baosheng on 2009-01-31
```
forrest@fMRI:~/Desktop/iscape/runtime/LNX86/bin$ file java
java: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.5, dynamically linked (uses shared libs), stripped

```

---

### Post by baosheng on 2009-01-31
> **alphaniner said:**
> I don't know if it means anything, but I noticed the second time you showed the output of trying to run java it was

```
-bash: ./java: No such file or directory
```

whereas the first time it was

```
bash: ./java: No such file or directory
```

Is that '-' a typo or something?  Weird.

That is not a typo. I did copy + paste from my terminal window.

---

### Post by dcstar on 2009-01-31
> **baosheng said:**
> ```
forrest@fMRI:~/Desktop/iscape/runtime/LNX86/bin$ file java
java: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.5, dynamically linked (uses shared libs), stripped

```

Are you running 32bit or 64bit Ubuntu?:

```
uname -a
```

---

### Post by baosheng on 2009-02-14
I am running 64-bit. But that should not be a reason for unable to find that executable file. Plus, I did the same thing on 64-bit RHEL 4 and it worked fine. So I guess it the problem on file indexing on Ubuntu.

---

### Post by RJARRRPCGP on 2009-02-14
> **baosheng said:**
> 

Do anyone here know the reason my shell said "No such file or directory" for an existing file?

That MAY occur because of no read permission.

---

### Post by baosheng on 2009-02-14
> **RJARRRPCGP said:**
> That MAY occur because of no read permission.

Dude, I have given that file 0777 permission.

---

### Post by RJARRRPCGP on 2009-02-14
> **baosheng said:**
> Dude, I have given that file 0777 permission.

That was ONLY a possibility. I can't confirm it would cause that error.

---

### Post by dcstar on 2009-02-14
> **baosheng said:**
> I am running 64-bit. But that should not be a reason for unable to find that executable file. Plus, I did the same thing on 64-bit RHEL 4 and it worked fine. So I guess it the problem on file indexing on Ubuntu.

No, you are trying to run a 32 bit binary on a 64 bit system - that is probably why you are getting the message.

See what my 64 bit java displays:

dc@dc-master:~$ file /usr/lib/jvm/java-6-openjdk/jre/bin/java
```
/usr/lib/jvm/java-6-openjdk/jre/bin/java: ELF **64-bit** LSB executable, x86-64, version 1 (SYSV), for GNU/Linux 2.6.8, dynamically linked (uses shared libs), stripped
```

---

### Post by FrnndClmb on 2009-03-23
I have the same problem, but with additional info to help experts in solving this drama.

First I've installed Java and Eclipse in my own user (frnnd), and everything worked fine. Then I've installed a device SDK for Linux. This SDK works as follows: it creates a new user called posdev. Then it creates the directory /home/posdev/sdk and inside this directory there is a sort of Linux environment, with usr, bin, sbin, etc, etc.

I have to login with posdev, and I've noticed that my root structure changes to whatever is inside /home/posdev/sdk. Some login script is doing this, I don't know how.

So far, so good. I can call gcc, g++, ls, find, etc. But I really wanted to run Eclipse. So I've copied jdk and eclipse to that /home/posdev/sdk directory, and issued chown -R posdev:posdev to both directories. When I login again to posdev, the root directory now shows /jdk and /eclipse, which correspond exactly to what I've copied to /home/posdev/sdk using root.

Now comes the problem: 

[posdev@uClibc:/jdk/bin]$ uname -a
Linux vboxfc 2.6.24-23-generic #1 SMP Mon Jan 26 00:13:11 UTC 2009 i686 unknown unknown GNU/Linux
[posdev@uClibc:/jdk/bin]$ file java
java: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.5, dynamically linked (uses shared libs), not stripped
[posdev@uClibc:/jdk/bin]$ ls -la java 
-rwxrwxrwx    1 posdev   posdev      47308 Jan 17 07:23 java*
[posdev@uClibc:/jdk/bin]$ ./java
-bash: ./java: No such file or directory
[posdev@uClibc:/jdk/bin]$ echo Don't know what to do.

As you can see, I'm running a 32-bit system (i686), have the correct permissions, etc. I think there's something about that "directory hijacking" making my root looks like /home/posdev/sdk.

Can somebody help us now?

---

### Post by dtbaker on 2010-01-01
Simple fix. Don't know what all these people are on about with permissions etc.. it's clear that was resolved early on and the issue is elsewhere. Just install ia32-libs package. Java that comes with some installers uses shared libs, this borks on most fresh 64bit installs.

Running this should sort it on ubuntu:

$ apt-get install libc6-i386 lib32gcc1 lib32z1 lib32stdc++6 ia32-libs



This happened when trying to install Zend Studio on a 64bit box. The error message was something like 'jre/bin/java: not found' but of course the file was there and did have the correct rwxr-xr-x set. Running manually ./java produced the same error. Hope this helps someone who has this issue.

---

### Post by Astrals on 2010-01-17
Yes the ia32-libs will fix allot of issues, I had a similar issue with avast for linux, by installing the ia32-libs it fixed the issue, and also got the not needed gui working.

Hope this helps.

---

### Post by majedaly on 2012-01-13
> **dtbaker said:**
> Simple fix. Don't know what all these people are on about with permissions etc.. it's clear that was resolved early on and the issue is elsewhere. Just install ia32-libs package. Java that comes with some installers uses shared libs, this borks on most fresh 64bit installs.

Running this should sort it on ubuntu:

$ apt-get install libc6-i386 lib32gcc1 lib32z1 lib32stdc++6 ia32-libs



This happened when trying to install Zend Studio on a 64bit box. The error message was something like 'jre/bin/java: not found' but of course the file was there and did have the correct rwxr-xr-x set. Running manually ./java produced the same error. Hope this helps someone who has this issue.
Thanks dtbaker.... I was banging my head in the wall for hours !

---

### Post by oldos2er on 2012-01-13
Closed, necromancy.

---

