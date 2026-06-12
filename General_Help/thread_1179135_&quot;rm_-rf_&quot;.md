---
title: "&quot;rm -rf /&quot; ?"
date: 2009-06-05
forum: General Help
---

### Post by stuart.reinke on 2009-06-05
I was curious about the infamous "rm -rf /" command. So, just to see what would happen I entered the command "ls -rf /". 

Wow, seeing what could be potentially deleted was neat.

I know that rm is the delete command and / means to start in the root directory, but I can't seem to find what the -rf is for.

Which leaves me with two questions:

1. What does -rf mean?

2. Is there any useful application for this command, or is it just something that a jerk uses to trick someone into messing up their computer?

---

### Post by Tibuda on 2009-06-05
1. You can use the man command to see the help for any terminal command.
[QUOTE="man rm"]
       -f, --force
              ignore nonexistent files, never prompt

       -r, -R, --recursive
              remove directories and their contents recursively
[/QUOTE]
2. It is useful when you know what you are doing. Suppose I have a /tmp/dir directory with many files. If you run **rm /tmp/dir** it won't be removed because of the files, but if you run **rm -r /tmp/dir** all the files will be deleted. The f option is useful in scripting when you create a temporary directory, but you have to delete it before the script. If you run **rm -r /tmp/dir** and the directory does not exists, your script will stop running, but if you run **rm -rf /tmp/dir** the script won't stop.

---

### Post by krotus on 2009-06-05
man rm

-f, --force
              ignore nonexistent files, never prompt

-r, -R, --recursive
              remove directories and their contents recursively

---

### Post by Legace on 2009-06-05
Type in the following and scroll down to see what it means:
```
rm --help
```

>        -r, -R, --recursive
              remove directories and their contents recursively


       -f, --force
              ignore nonexistent files, never prompt


---

### Post by stuart.reinke on 2009-06-05
Thanks to everyone who replied to my questions. I know about the man pages but didn't think to look there. I'll get this stuff through my thick head sooner or later.  Thanks again.

---

### Post by abhilashm86 on 2009-06-05
maybe you can try this command in live cd, or install ubuntu in pendrive and watchout.........but after effects will be nasty to recover:)

---

### Post by bacardiandwatermelon on 2009-06-05
Someone on the forum, forget who it was suggested adding the following lines to the end of your bashrc file, so when you do use rm it adds the -i automatically..

```
alias rm='rm -i'
```

---

### Post by benj1 on 2009-06-05
> **bacardiandwatermelon said:**
> Someone on the forum, forget who it was suggested adding the following lines to the end of your bashrc file, so when you do use rm it adds the -i automatically..

```
alias rm='rm -i'
```

that won't work with rm -rf though

---

### Post by blueridgedog on 2009-06-05
> **stuart.reinke said:**
> I was curious about the infamous "rm -rf /" command. So, just to see what would happen I entered the command "ls -rf /". 

Wow, seeing what could be potentially deleted was neat.



The actual files deleted would be far fewer as it would be limited to the files your account could delete, versus list.  That is the big reason that people try and use sudo rather than root sessions.

---

### Post by Tibuda on 2009-06-05
> **abhilashm86 said:**
> maybe you can try this command in live cd, or install ubuntu in pendrive and watchout.........but after effects will be nasty to recover:)

Good idea. I'll try it later.

---

### Post by eldragon on 2009-06-05
do not think that doing it on a livecd is entirely harmless.

if you previously mounted a partition, it will be anhilitated too.

---

### Post by Tibuda on 2009-06-05
Yeah, I see. Thanks. I'll do in a Virtual Box machine.

---

### Post by Locutus_of_Borg on 2009-06-05
```
[void@null ~]$ rm -rf /
rm: cannot remove root directory `/'
```

why it no work? :(


maybe 
find / -exec rm -rf '{}' +
would work better...

DONT DO THE ABOVE COMMAND

---

### Post by Krupski on 2009-06-05
> **stuart.reinke said:**
> I was curious about the infamous "rm -rf /" command. So, just to see what would happen I entered the command "ls -rf /". 

Wow, seeing what could be potentially deleted was neat.

I know that rm is the delete command and / means to start in the root directory, but I can't seem to find what the -rf is for.

Which leaves me with two questions:

1. What does -rf mean?

2. Is there any useful application for this command, or is it just something that a jerk uses to trick someone into messing up their computer?

WOW! The "-r" option means "recursive" (that means "dig down the entire directory tree, right to the end").

The "-f" option means "force" as in "delete it, even if it doesn't want to be deleted".

In Linux / UNIX, command options can be strung together. Rather than typing "command -r -f", you can just type "command -rf".

And of course, DO NOT EVER, EVER, EVER type the "rm" (remove, delete) command with those switches, unless you want to lose all your files and have to reinstall from scratch!

NEVER EVER EVER EVER!!! EVER!!!

:)

-- Roger

---

### Post by Krupski on 2009-06-05
> **blueridgedog said:**
> The actual files deleted would be far fewer as it would be limited to the files your account could delete, versus list.  That is the big reason that people try and use sudo rather than root sessions.

There are some people who always run Ubuntu as root (as I shamefully hang my head in guilt)  :)

---

### Post by Tibuda on 2009-06-05
> **Locutus_of_Borg said:**
> ```
[void@null ~]$ rm -rf /
rm: cannot remove root directory `/'
```

why it no work? :(
You forgot the sudo, but I think the message should be somehting about permissions.

---

### Post by blueridgedog on 2009-06-05
> **Krupski said:**
> There are some people who always run Ubuntu as root (as I shamefully hang my head in guilt)  :)

I evolved as a system admin who routinely worked from a root shell, sometimes on 5 systems at once, or via ssh chains inside companies and hopping form box to box.  I like the lack of a root account on Ubuntu, though it too a while to get accustomed to sudo versus su.  Desktop Linux has reached more people who now and sudo is part of the success.

Not using a root shell has also forced me to clean up my work.  There is no need to have the files I need to work on all over the file system, and all owned by root, when I can just as easily make my user account work with some slight changes in how I do things (putting my custom stuff in my own bin directory rather than /usr/local/bin or doing web development free of the need for root.  Learn to work with it.

---

### Post by Locutus_of_Borg on 2009-06-05
> **danielrmt said:**
> You forgot the sudo, but I think the message should be somehting about permissions.
it's not a permissions problem, you simply cannot delete the root directory in bash

---

