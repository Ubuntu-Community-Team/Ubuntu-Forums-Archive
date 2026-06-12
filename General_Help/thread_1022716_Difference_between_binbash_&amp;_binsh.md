---
title: "Difference between /bin/bash &amp; /bin/sh"
date: 2008-12-27
forum: General Help
---

### Post by paragkalra on 2008-12-27
I know it's a very silly question but could someone please explain the difference between "/bin/bash" & "/bin/sh"

I was under the impression that both are same but following output on my Ubuntu 8.10 is making me raise my eyebrows.

> parag@station3:~$ ls -l /bin/bash ; ls -l /bin/sh
-rwxr-xr-x 1 root root 725136 2008-05-13 00:18 /bin/bash
lrwxrwxrwx 1 root root 4 2008-12-03 21:42 /bin/sh -> dash
parag@station3:~$ 

---

### Post by sdennie on 2008-12-27
Bash is an extended version of the original Bourne shell (sh) and dash (which, on Ubuntu, is sh) is supposed to be faster at running scripts.  I think that sh became dash somewhere around Ubuntu 7.04 or 6.10 to help speed up the boot process.

---

### Post by gTinker on 2008-12-27
> 
 lrwxrwxrwx 1 root root 4 2008-12-03 21:42 /bin/sh -> dash


You will note that /bin/sh is a link to dash


[QUOTE=paragkalra] know it's a very silly question but could someone please explain the difference between "/bin/bash" & "/bin/sh"

I was under the impression that both are same but following output on my Ubuntu 8.10 is making me raise my eyebrows.[/QUOTE]

Perhaps what you are thinking of is that in Debian /bin/sh is a link to bash.

Poster vor has already explained the reason for the change.

---

### Post by paragkalra on 2008-12-27
Thanks guys...I got my answer...so the conclusion is:

1. If am executing the shell script using absolute or relative path, then interpreter used would be the one mentioned as sha-bang header.
2. And if I am using "sh" to invoke the shell script, interpreter used would be the one linked with "/bin/sh"

---

### Post by paragkalra on 2008-12-28
Just to add more info, 3rd way to execute a script is directly through the interpreter. For e.g. consider following python script

#cat /tmp/sha_python
> if 1==1:
	print "Equal"
else:
	print "No"

I can execute it using:
#python /tmp/sha_python
> Equal

The interesting thing to note that is if I add a sha-bang header to it. i.e.

#cat /tmp/sha_bang_python
> #!/usr/bin/python
if 1==1:
	print "Equal"
else:
	print "No"

and if I invoke it using a wrong interpreter say "perl" still the script would work:
#perl /tmp/sha_bang_python
> Equal

---

### Post by dcstar on 2008-12-28
> **paragkalra said:**
> Thanks guys...I got my answer...so the conclusion is:
.......
2. And if I am using "sh" to invoke the shell script, interpreter used would be the one linked with "/bin/sh"

For more understanding, do:

```
man sh
```

---

### Post by Cracauer on 2008-12-28
Bash is a great implementation of the Bourne Shell, no doubt. It has language extensions that are useful but that are not available in bourne shell. 

The one major weakness, or rather the one thing that bash screws up, is that it you can't really turn these extensions off to limit the shell to bourne shell syntax. Sure, there is a switch, but the behavior afterwards isn't close to bourne shell.

There are other concerns:
- bash is GPLed
- bash is pretty slow

Quite a few free Unix distributions use a different implementation for /bin/sh for a variety of reasons:
[list]
[*] They don't want users (or themselves) to accidentally write bash instead of sh scripts (something you practically can't prevent with bash as the default shell
[*] Faster startup (less byzantine scripts would help more, though)
[*] Don't want GPLed stuff in startup relevant areas (mostly the BSDs)
[/list]

So, if you want bash extensions, use
#!/bin/bash

If you want to write a script that runs on different Unixes and is limited to sh syntax, use #!/bin/sh, but keep in mind this isn't enforced on systems with bash as /bin/sh

---

