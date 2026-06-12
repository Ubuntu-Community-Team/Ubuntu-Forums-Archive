---
title: "executable file won't run"
date: 2008-12-21
forum: General Help
---

### Post by leonardevens on 2008-12-21
I downloaded the crossword program used for the NY Times web site, called acrossl.   It comes as part of a tar package.   When I try
% acrossl xxx.puz
I get back
bash: acrossl: No such file or directory
On the other hand
% file acrossl
returns
acrossl: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), stripped
ls -l shows that the file has x permission for everyone.  I've also set PATH so the file is in the path.

Can anyone explain what might be going on?   If I understand the syntax, the program acrossl is complaining about not finding a file, but it isn't xxx.puz.  
% ldd acrossl
produces a similar error message.  And I get the same message if I don't include a *.puz argument.

I've also downloaded the same program on my Fedora machine, and the program is recognized, but it doesn't run because of library issues under my current OS, Fedora 9.   I suspect the same problem would happen under Ubuntu, but I wanted to check to be sure.

Is Ubuntu also trying te tell me a library is missing.  Why isn't identifying the library which is normal Unix behavior.

---

### Post by albinootje on 2008-12-21
> **leonardevens said:**
> I downloaded the crossword program used for the NY Times web site, called acrossl.   It comes as part of a tar package.   When I try
% acrossl xxx.puz
I get back
bash: acrossl: No such file or directory


By default the current directory is not in the PATH in Ubuntu.
Can you try :
```

./acrossl xxx.puz

```
or
```

sh ./acrossl xxx.puz

```

---

### Post by leonardevens on 2008-12-21
> **albinootje said:**
> By default the current directory is not in the PATH in Ubuntu.
Can you try :
```

./acrossl xxx.puz

```
or
```

sh ./acrossl xxx.puz

```

That isn't the problem.  Go back and look at what I said.  In fact, orginally, I tried
./acrossl
and got the same result.  I then tried a variety of different things, including adding the directory with acrossl to my path.

I found afterwards that this had been reported before in an Ubuntu forum

ubuntuforums.org/archive/index.php/t-325510.html 

No one came up with a solution, but the original poster found another program  xword, a python script,
which is available as a package under Ubuntu and as a tar file otherwise.

I would still like to know just what is going on under Ubuntu in this case,  but I am happy not to have to rely on acrossl.   I always had to fiddle to get their Linux versions to work, and it appears that they are no longer supporting it for Linux.

---

### Post by albinootje on 2008-12-21
> **leonardevens said:**
> 
I would still like to know just what is going on under Ubuntu in this case,  but I am happy not to have to rely on acrossl.   I always had to fiddle to get their Linux versions to work, and it appears that they are no longer supporting it for Linux.

You write that the binary is in the PATH, can you post the output of the following ?
```

ls -la $(which acrossl)
echo $PATH
ldd -v $(which acrossl)

```

---

### Post by leonardevens on 2008-12-22
> **albinootje said:**
> You write that the binary is in the PATH, can you post the output of the following ?
```

ls -la $(which acrossl)
echo $PATH
ldd -v $(which acrossl)

```

ls -a $(which acrossl)
doesn't make sense as a command,
But
$ ls -a
yields
.  ..  acllinux.smotif.tar.gz  acrossl  LICENSE  man  Puzzles  README

$ echo $PATH
yields
/home/len/bin:/home/len/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/len/src/acrossl.d

Also
$ pwd
yields
$ pwd
yields
/home/len/src/acrossl.d 

ldd -v $(which acrossl)
also doesn't make sense

But
$ ldd -v acrossl
yields
/usr/bin/ldd: line 117: ./acrossl: No such file or directory

The part after `:' is the same as the ouput from just invoking acrossl.




My guess is that the commaend interpreter doesn't see acrossl as an excecutable file for some reason despite the fact that the command 
$ file  acrossl
identifies it as such.

---

### Post by taurus on 2008-12-22
Are you running the x86_64 version?

```
uname -a
```

---

### Post by albinootje on 2008-12-22
> **leonardevens said:**
> ls -a $(which acrossl)
doesn't make sense as a command,
---cut---
ldd -v $(which acrossl)
also doesn't make sense


Tell me why you think those commands don't make sense ?
Did you try it ?

---

