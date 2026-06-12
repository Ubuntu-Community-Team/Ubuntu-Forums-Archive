---
title: "Create a Script to Batch-Check SFV Files"
date: 2009-03-03
forum: General Help
---

### Post by bbarcelo on 2009-03-03
From another [thread]("http://ubuntuforums.org/showthread.php?t=877461") I have located the necessary terminal command to batch-check SFV files in Ubuntu.
```
find /home/user/packed-files/ -type f -name '*.sfv' -execdir cfv -f {} 2>/dev/null \;
```
I would like to take this one step further and create a script you can execute anywhere that allows a directory to be passed to it. The intended use would look something like this:
```
user@computer:/home/user$ batch-check-sfv directory/
```
or
```
user@computer:/home/user$ batch-check-sfv .
```
I'm a bit new to creating scripts though and don't 100% understand the original command, specifically:
```
{} 2>/dev/null \;
```
Anyone who helps out gets a cup of Ubuntu.

---

### Post by ibuclaw on 2009-03-03
Run:
```
gedit ~/.bashrc
```
and put at the bottom:
```

function batch-check-sfv {
    [ -z "$1" ] && \
        find . -type f -name '*.sfv' -execdir cfv -f {} 2>/dev/null \; || \
        find $1 -type f -name '*.sfv' -execdir cfv -f {} 2>/dev/null \;
}

```
Save+Quit, then run:
```
source ~/.bashrc
```
And you are all set to go with the functionality you asked for.

As for your second question:
```
{} 2>/dev/null \;
```
[LIST]
[*]{}  = the file that find matches.
[*]2>/dev/null   = redirect all stderr text to /dev/null, so it isn't displayed on the console screen.
[*]\;  = is the terminating characters for the -execdir switch in find.
[/LIST]

Regards
Iain

---

### Post by samosamo on 2009-03-03
what the hell?  cfv has a recursive function.  i run it with cfv -irVV

try "man cfv" next time, before you waste all your time reinventing the wheel

---

### Post by bbarcelo on 2009-03-04
tinivole: Thanks for both creating the function and answering my question. Understanding the functionality was an important part of my question.

samosamo: Nice tip to point out but there was more to my question. I wasn't "re-inventing the wheel", I was trying to understand how the wheel was invented. tinivole's function will allow me to create similar functions whose commands may not support the recursive option.

---

### Post by samosamo on 2009-03-05
umm if that's the way you want to look at it :)

always read the man pages first.  always.  and lose the "batch script" mentality of a windows admin.

---

