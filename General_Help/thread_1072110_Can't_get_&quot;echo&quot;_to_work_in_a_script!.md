---
title: "Can't get &quot;echo&quot; to work in a script!"
date: 2009-02-17
forum: General Help
---

### Post by foobster on 2009-02-17
Hello,

I'm trying to use echo in a script and it isn't working according to the man page. My demo script is as follows:
```
#! /bin/sh

echo -e -n "hello\nworld\n"
echo -n -e "hello\nworld\n"
echo -n  "hello\nworld\n"
echo -e  "hello\nworld\n" 
```

And it outputs:
```
-e -n hello
world

-e hello
world
hello
world
-e hello
world


```

According to the manpage, I would expect -e to be a valid option and to be turned off by default (both of these things seem to be false here). Furthermore if I do the same in an interactive shell I get:
```
$ echo -e -n "hello\nworld\n"
hello
world
$ echo -n -e "hello\nworld\n"
hello
world
$ echo -n  "hello\nworld\n"
hello\nworld\n$ echo -e  "hello\nworld\n"
hello
world 

```
just as I would expect. Piping the commands into bash also works as I would expect.

The command "which echo" returns "/bin/echo" from the script and from the interactive shell. I'm sure that I'm missing something here, but I can't for the life of me figure it out. Does anybody have any input? Thanks!

---

### Post by cdtech on 2009-02-17
What do you get running it in this manor?
```
echo -ne "hello\nworld\n"
```

---

### Post by mikewu on 2009-02-17
Change the #! /bin/sh to #!/bin/bash

I then get 

> 
hello
world
hello
world
hello\nworld\nhello
world

Not exactly sure why sh and bash are interpreting it differently, but it does fix it.

---

### Post by foobster on 2009-02-17
In the interactive shell I get what I would expect (-ne = -en = -e -n = -n -e). From the script I get:

```
-en hello
world

-ne hello
world


```

It doesn't like that e for some reason.

---

### Post by foobster on 2009-02-17
Thanks for the reply, I'm glad to have it working now. I'm still a little confused as to why it's like this. Also odd is that "echo --help" and "echo --version" don't work even though the man page says they should.

---

### Post by foobster on 2009-02-17
If anyone finds this post, here is a relevant link: [https://bugs.launchpad.net/ubuntu/+source/dash/+bug/78116](https://bugs.launchpad.net/ubuntu/+source/dash/+bug/78116).

Here is another: [https://bugs.launchpad.net/ubuntu/+source/dash/+bug/61463](https://bugs.launchpad.net/ubuntu/+source/dash/+bug/61463)

The problem is just that most people are used to /bin/sh being linked to bash while in Ubuntu it is linked to dash. In dash, "-e" is not a valid option and escape characters are interpreted by default.

---

### Post by cdtech on 2009-02-17
Great find........Thanks.

---

### Post by foobster on 2009-02-17
Sorry, one more thing and I'll let this post die.

I found this link ([https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)) and it does a really great job of explaining why the /bin/sh link was changed to dash and what it means. It also explains some differences in syntax that you might get caught on if you're expecting it to be bash (echo for example). Also interesting is that "~" won't expand in dash. Interesting.

---

### Post by kerry_s on 2009-02-17
yeah, times have changed. i no longer use "/bin/sh" in my scripts, i use "/bin/dash" or "/bin/bash" depending on the script.
example, for something simple like a launcher:
```

#!/bin/dash
exec xmessage " Loading..... " -center -timeout 10 -buttons , | firefox &

```

i think it's better to just not assume and do it the right way. ;)

---

### Post by geirha on 2009-02-17
There are three echos on your system.
1. The built-in echo in bash. Read its syntax in builtins(7) or bash(1).
```
$ bash
$ type echo
echo is a shell builtin

```
2. The built-in echo in dash. Read its syntax in dash(1)
```
$ sh
$ type echo
echo is a shell builtin

```
3. The separate command /bin/echo, which is the one explained by the man-page echo(1), and do accept --help and --version
```
/bin/echo --help
/bin/echo --version
```

---

### Post by heindsight on 2009-02-17
> **kerry_s said:**
> yeah, times have changed. i no longer use "/bin/sh" in my scripts, i use "/bin/dash" or "/bin/bash" depending on the script.


/bin/sh is supposed to be a POSIX compliant shell and that any script you write for should run on any POSIX compliant operating system (assuming all the commands you use are available). 

Putting a #!/bin/dash shebang in your script is quite silly if you ask me, since it's going to cause errors and confusion when someone tries to run it on a system that doesn't have dash.

If you use #!/bin/sh instead then your script will be interpreted by dash on ubuntu, bash on systems where /bin/sh points to bash and whatever is used as /bin/sh on other Unix variants. And on all those different shells on different operating systems, your script should behave in the same manner.

---

### Post by kerry_s on 2009-02-17
> **heindsight said:**
> /bin/sh is supposed to be a POSIX compliant shell and that any script you write for should run on any POSIX compliant operating system (assuming all the commands you use are available). 

Putting a #!/bin/dash shebang in your script is quite silly if you ask me, since it's going to cause errors and confusion when someone tries to run it on a system that doesn't have dash.

If you use #!/bin/sh instead then your script will be interpreted by dash on ubuntu, bash on systems where /bin/sh points to bash and whatever is used as /bin/sh on other Unix variants. And on all those different shells on different operating systems, your script should behave in the same manner.

true, but i think if it's a true bash script it should have "#!/bin/bash" instead of "#!/bin/sh", but your right if it was a script that i was sharing i would most likely use "#!/bin/sh".
on my computers, i've stopped using /bin/sh though.

---

### Post by heindsight on 2009-02-17
> **kerry_s said:**
> true, but i think if it's a true bash script it should have "#!/bin/bash" instead of "#!/bin/sh", but your right if it was a script that i was sharing i would most likely use "#!/bin/sh".
on my computers, i've stopped using /bin/sh though.

Yes of course, if it's a bash script and it uses bash specific features then it must be interpreted by bash and you should put a #!/bin/bash at the top. But using #!/bin/dash is rather pointless, since a script that can be interpreted by dash should work on any other sh compatible shell.

EDIT:
portability isn't the only reason for using sh instead of bash. bash is quite big, so it requires a lot more memory and is slower to start up than dash and other smaller shells.

---

### Post by kerry_s on 2009-02-17
> **heindsight said:**
> Yes of course, if it's a bash script and it uses bash specific features then it must be interpreted by bash and you should put a #!/bin/bash at the top. But using #!/bin/dash is rather pointless, since a script that can be interpreted by dash should work on any other sh compatible shell.

EDIT:
portability isn't the only reason for using sh instead of bash. bash is quite big, so it requires a lot more memory and is slower to start up than dash and other smaller shells.

well i'm using arch, so /bin/sh is linked to /bin/bash and if it's changed to /bin/dash it breaks things, so it's not pointless to me, for scripts that don't need bash i want to use the faster dash, i only got 450mhz 256mb ram so every little bit helps.  ;)

---

