---
title: "First BASH Script - having problems!"
date: 2009-01-14
forum: General Help
---

### Post by dm993 on 2009-01-14
I'm new to Linux and scripting and I think I'm missing something simple with a bash script I'm trying to write to print "Hello World"

If the script file is simply as below
[I]# A Script File
echo "Hello world"[/I]

I can execute it fine using the command
*$./helloworld*

If the file contains the location of the bash interpreter
[I]#!/bin/bash
#A script File
echo "Hello World"[/I]

If I then execute the program
*$./helloworld*

I get the following message
*-bash: ./helloworld: /bin/bash^M: bad interpreter: No such file or directory*

If I edit the script file to be as below (removing bash location)
[I]clear
echo "Hello World"[/I]

I get a *Command Not found message *for the 'clear' command but *echo "Hello World"* executes fine.

Can anyone tell me what I'm missing, it must be something simple?? I used NANO to create the file on Ubuntu Linux 8.10

---

### Post by hangfire on 2009-01-14
> **dm993 said:**
> 
I get the following message
*-bash: ./helloworld: /bin/bash^M: bad interpreter: No such file or directory*

That Control-M at the end of the line is the problem. It is an MSDOS end of line marker, and has no place in a shell script. Your invocation shell is looking for a file named:

"/bin/bash^M"

which does not exist.

Try the following:

```
sudo apt-get install tofrodos
dos2unix *filename*
```


-HF

---

### Post by dm993 on 2009-01-14
Superb advice Hangfire, thanks! :p

I was suspicious of the ^M but very confused how using Nano would cause this, should I use a more suitable editor to create scripts in the future, I find Vi a bit of a grind compared to nano.

---

### Post by hangfire on 2009-01-14
> **dm993 said:**
> Superb advice Hangfire, thanks! :p

I was suspicious of the ^M but very confused how using Nano would cause this, should I use a more suitable editor to create scripts in the future, I find Vi a bit of a grind compared to nano.

You're welcome. VI is "expert friendly" :p

Nano is usually OK for Linux type text files, it may have thought it was invoked on a DOS partition, or the file already had on CR/LF combination in it, so it switched to DOS file mode.

Don't forget to mark thread as Solved!

-HF

---

