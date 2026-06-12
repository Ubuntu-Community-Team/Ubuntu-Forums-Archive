---
title: "Installing git in Ubuntu errors"
date: 2009-04-06
forum: General Help
---

### Post by alcatraz678 on 2009-04-06
Hi guys, I'm trying to learn how to install through source code. I want to learn this thing when I'm going to stay in Ubuntu forever right?

Anyway, here's an error that I got from the command line:

```
emme@emme-desktop:~/Desktop$ tar xfz git-1.6.2.2.tar.gz
emme@emme-desktop:~/Desktop$ cd git-1.6.2.2
emme@emme-desktop:~/Desktop/git-1.6.2.2$ make
/bin/sh: curl-config: not found
GIT_VERSION = 1.6.2.2
/bin/sh: curl-config: not found
    * new build flags or prefix
    CC fast-import.o
In file included from builtin.h:4,
                 from fast-import.c:142:
git-compat-util.h:104:25: error: openssl/ssl.h: No such file or directory
git-compat-util.h:105:25: error: openssl/err.h: No such file or directory
In file included from builtin.h:6,
                 from fast-import.c:142:
cache.h:8:21: error: openssl/sha.h: No such file or directory
cache.h:16:18: error: zlib.h: No such file or directory
In file included from builtin.h:6,
                 from fast-import.c:142:
cache.h:21: error: expected ‘)’ before ‘strm’
cache.h:22: error: expected ‘)’ before ‘strm’
cache.h:23: error: expected ‘)’ before ‘strm’
In file included from fast-import.c:151:
csum-file.h:10: error: expected specifier-qualifier-list before ‘SHA_CTX’
fast-import.c:279: error: ‘Z_DEFAULT_COMPRESSION’ undeclared here (not in a function)
fast-import.c: In function ‘create_index’:
fast-import.c:849: error: ‘SHA_CTX’ undeclared (first use in this function)
fast-import.c:849: error: (Each undeclared identifier is reported only once
fast-import.c:849: error: for each function it appears in.)
fast-import.c:849: error: expected ‘;’ before ‘ctx’
fast-import.c:885: warning: implicit declaration of function ‘SHA1_Init’
fast-import.c:885: error: ‘ctx’ undeclared (first use in this function)
fast-import.c:890: warning: implicit declaration of function ‘SHA1_Update’
fast-import.c:895: warning: implicit declaration of function ‘SHA1_Final’
fast-import.c: In function ‘store_object’:
fast-import.c:1037: error: ‘SHA_CTX’ undeclared (first use in this function)
fast-import.c:1037: error: expected ‘;’ before ‘c’
fast-import.c:1038: error: ‘z_stream’ undeclared (first use in this function)
fast-import.c:1038: error: expected ‘;’ before ‘s’
fast-import.c:1042: error: ‘c’ undeclared (first use in this function)
fast-import.c:1074: error: ‘s’ undeclared (first use in this function)
fast-import.c:1075: warning: implicit declaration of function ‘deflateInit’
fast-import.c:1085: warning: implicit declaration of function ‘deflate’
fast-import.c:1085: error: ‘Z_FINISH’ undeclared (first use in this function)
fast-import.c:1085: error: ‘Z_OK’ undeclared (first use in this function)
fast-import.c:1087: warning: implicit declaration of function ‘deflateEnd’
fast-import.c: In function ‘parse_progress’:
fast-import.c:2338: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
fast-import.c: In function ‘git_pack_config’:
fast-import.c:2391: error: ‘Z_BEST_COMPRESSION’ undeclared (first use in this function)
make: *** [fast-import.o] Error 1
emme@emme-desktop:~/Desktop/git-1.6.2.2$ make all
/bin/sh: curl-config: not found
    CC fast-import.o
In file included from builtin.h:4,
                 from fast-import.c:142:
git-compat-util.h:104:25: error: openssl/ssl.h: No such file or directory
git-compat-util.h:105:25: error: openssl/err.h: No such file or directory
In file included from builtin.h:6,
                 from fast-import.c:142:
cache.h:8:21: error: openssl/sha.h: No such file or directory
cache.h:16:18: error: zlib.h: No such file or directory
In file included from builtin.h:6,
                 from fast-import.c:142:
cache.h:21: error: expected ‘)’ before ‘strm’
cache.h:22: error: expected ‘)’ before ‘strm’
cache.h:23: error: expected ‘)’ before ‘strm’
In file included from fast-import.c:151:
csum-file.h:10: error: expected specifier-qualifier-list before ‘SHA_CTX’
fast-import.c:279: error: ‘Z_DEFAULT_COMPRESSION’ undeclared here (not in a function)
fast-import.c: In function ‘create_index’:
fast-import.c:849: error: ‘SHA_CTX’ undeclared (first use in this function)
fast-import.c:849: error: (Each undeclared identifier is reported only once
fast-import.c:849: error: for each function it appears in.)
fast-import.c:849: error: expected ‘;’ before ‘ctx’
fast-import.c:885: warning: implicit declaration of function ‘SHA1_Init’
fast-import.c:885: error: ‘ctx’ undeclared (first use in this function)
fast-import.c:890: warning: implicit declaration of function ‘SHA1_Update’
fast-import.c:895: warning: implicit declaration of function ‘SHA1_Final’
fast-import.c: In function ‘store_object’:
fast-import.c:1037: error: ‘SHA_CTX’ undeclared (first use in this function)
fast-import.c:1037: error: expected ‘;’ before ‘c’
fast-import.c:1038: error: ‘z_stream’ undeclared (first use in this function)
fast-import.c:1038: error: expected ‘;’ before ‘s’
fast-import.c:1042: error: ‘c’ undeclared (first use in this function)
fast-import.c:1074: error: ‘s’ undeclared (first use in this function)
fast-import.c:1075: warning: implicit declaration of function ‘deflateInit’
fast-import.c:1085: warning: implicit declaration of function ‘deflate’
fast-import.c:1085: error: ‘Z_FINISH’ undeclared (first use in this function)
fast-import.c:1085: error: ‘Z_OK’ undeclared (first use in this function)
fast-import.c:1087: warning: implicit declaration of function ‘deflateEnd’
fast-import.c: In function ‘parse_progress’:
fast-import.c:2338: warning: ignoring return value of ‘fwrite’, declared with attribute warn_unused_result
fast-import.c: In function ‘git_pack_config’:
fast-import.c:2391: error: ‘Z_BEST_COMPRESSION’ undeclared (first use in this function)
make: *** [fast-import.o] Error 1
emme@emme-desktop:~/Desktop/git-1.6.2.2$ 

```

I don't know what the hell happen, I just follow the INSTALL file. Like make command but the command line spat those errors out..

---

### Post by 3Miro on 2009-04-06
Where did you download the thing? What does the INSTALL or README say?

It looks like you need to run a configure script first. Usually you have to do:

```

./configure
make
make install

```

That last one depends, some times it is not needed. Make compiles the files and make install puts the compiled files somewhere in the system. You can choose to keep the files where they are and run them from within the folder where they were compiled.

You know you can install git form the repository right?

---

### Post by alcatraz678 on 2009-04-06
> **3Miro said:**
> Where did you download the thing? What does the INSTALL or README say?

It looks like you need to run a configure script first. Usually you have to do:

```

./configure
make
make install

```

That last one depends, some times it is not needed. Make compiles the files and make install puts the compiled files somewhere in the system. You can choose to keep the files where they are and run them from within the folder where they were compiled.

You know you can install git form the repository right?

I got it from the Git website. It's official. I did those things already. And it doesn't work.

---

### Post by Seq on 2009-04-06
Judging from these errors, it looks like you do not have the required dependancies needed for building:
```
/bin/sh: curl-config: not found
git-compat-util.h:104:25: error: openssl/ssl.h: No such file or directory
cache.h:8:21: error: openssl/sha.h: No such file or directory
cache.h:16:18: error: zlib.h: No such file or directory
git-compat-util.h:105:25: error: openssl/err.h: No such file or directory
```

Is there a reason you are grabbing the git source instead of just installing the packaged version from the repositories?

---

### Post by alcatraz678 on 2009-04-07
> **Seq said:**
> Judging from these errors, it looks like you do not have the required dependancies needed for building:
```
/bin/sh: curl-config: not found
git-compat-util.h:104:25: error: openssl/ssl.h: No such file or directory
cache.h:8:21: error: openssl/sha.h: No such file or directory
cache.h:16:18: error: zlib.h: No such file or directory
git-compat-util.h:105:25: error: openssl/err.h: No such file or directory
```

Is there a reason you are grabbing the git source instead of just installing the packaged version from the repositories?

Yes, there's reasonable reason. I want to learn how to use the command line. You know Linux stuffs. Because I'm just starting to pick things up, and I want to explore deeper into the Linux stuffs and especially command line.

---

### Post by Seq on 2009-04-07
> **alcatraz678 said:**
> Yes, there's reasonable reason. I want to learn how to use the command line. You know Linux stuffs. Because I'm just starting to pick things up, and I want to explore deeper into the Linux stuffs and especially command line.

Alrighty. There are some easier ways to learn the command line, though. Note that installing a package from source may be detrimental to your system as you will have untracked files laying about. As long as you don't run the 'make install' step, nothing will be actually installed into your system.


If you still wish to build git, you will need some additional packages. To see a list of all packages git needs for building, you can run the following command:

```
aptitude build-dep git-core -s
```

To install those dependencies, prefix 'sudo' and remove the '-s' from the end (-s is 'simulate', so no actual action will be performed).

**EDIT**: I should note that showing the build-deps like this only works because git already has a package that specifies all of this. If you were building a piece of software that did not have an existing package to inspect, you would have to read the INSTALL file or the website that you got the source from to determine what is needed (or worse -- trial and error guessing)

---

### Post by alcatraz678 on 2009-04-07
> **Seq said:**
> Alrighty. There are some easier ways to learn the command line, though. Note that installing a package from source may be detrimental to your system as you will have untracked files laying about. As long as you don't run the 'make install' step, nothing will be actually installed into your system.


If you still wish to build git, you will need some additional packages. To see a list of all packages git needs for building, you can run the following command:

```
aptitude build-dep git-core -s
```

To install those dependencies, prefix 'sudo' and remove the '-s' from the end (-s is 'simulate', so no actual action will be performed).

**EDIT**: I should note that showing the build-deps like this only works because git already has a package that specifies all of this. If you were building a piece of software that did not have an existing package to inspect, you would have to read the INSTALL file or the website that you got the source from to determine what is needed (or worse -- trial and error guessing)

Ok I tried the sudo aptitude build-dep git-core but it still doesn't work. The error is unable to find the source package for "git-core".

the git-core has a source package already right? because if i run sudo apt-get install git-core it works. but regarding in the aptitude command it doesn't find it?

I tried to experiment but always resulted to the same error:

```
 'source' URIs in your sources.list
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

```

and the make still resulted to the same error after running the aptitude command.

But honestly, thank you very much because I didn't know about the aptitude build-dep command until now. This will definitely be useful. But case unsolved yet..

---

### Post by Seq on 2009-04-07
> **alcatraz678 said:**
> 
```
 'source' URIs in your sources.list
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

```


Is part of this error missing? It looks like you don't have any deb-src repositories in your /etc/apt/sources.list. The easiest way is to go to 'Repositories' from one of the menus in Synaptic and enable source repositories -- it should be labelled in a somewhat identifiable way. I think this dialog is also accessible as 'Software sources' or something similar in the system menu, but I'm at work right now.

If you want to do it manually, here is a sample. The first line adds the main and restricted repositories from distro 'intrepid' within the URL provided. The second line is almost identical, but adds them as source repositories as well.

```
deb http://ca.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ intrepid main restricted
```

Note that using apt you can also do 'apt-get source git-core' and get the actual packaged source code (if you wanted to apply patches and build a new package and/or upload to a ppa).

---

### Post by tsantos on 2009-06-11
In case you haven't become completely de-motivated in trying to compile this yourself:

I recently needed to build this on Hardy and I ran into some of the same compile problems.  I did a:

```
sudo aptitude install zlib1g-dev
```

to get rid of the zlib.h problem.

Your first error looks like it's SSL related so you might try:

```
sudo aptitude install libssl-dev
```

---

### Post by ducksun43 on 2009-06-11
hello, iirc, then [http://sunoano.name/ws/public_xhtml/scm.html](http://sunoano.name/ws/public_xhtml/scm.html) has pretty detailed info on your problem :D

---

### Post by dialectic on 2009-07-07
I had similar problems compiling Git from source ( [http://kernel.org/pub/scm/git/git.git](http://kernel.org/pub/scm/git/git.git) ) in Ubuntu 8.10 - Intrepid 

```
git.git/git$ make
    CC fast-import.o
In file included from builtin.h:4,
                 from fast-import.c:143:
git-compat-util.h:127:25: error: openssl/ssl.h: No such file or directory
git-compat-util.h:128:25: error: openssl/err.h: No such file or directory
...
```


```
sudo apt-get build-dep git-core
```

didn't fix it,

After installing "libssl-dev" it compiled.

thanks tsantos.

---

