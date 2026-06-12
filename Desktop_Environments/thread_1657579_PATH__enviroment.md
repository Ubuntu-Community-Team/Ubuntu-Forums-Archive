---
title: "PATH  enviroment"
date: 2011-01-01
forum: Desktop Environments
---

### Post by 71GA on 2011-01-01
Hello! 

I have been playing with enviroment variables and have messed up with PATH variable. I think it had 3 paths included and i have to add them back. Can anyone tell me how can i add more paths under enviroment variable PATH?


Ty

---

### Post by nebileix on 2011-01-01
```
PATH=<Path u wanna add>:"${PATH}"
```

Example: PATH=~/bin:"${PATH}"

---

### Post by 71GA on 2011-01-01
> **nebileix said:**
> ```
PATH=<Path u wanna add>:"${PATH}"
```Example: PATH=~/bin:"${PATH}"

Sooo :"${PATH}" at the end only says that it should add a path not to rewrite it.
If i would use a command: "PATH=/home/.../bin" this would totaly rewrite my PATH enviroment variable and i would loose all paths included in there right?

I think i understand now :)


TY

---

### Post by AlphaLexman on 2011-01-01
> **71GA said:**
> Sooo :"${PATH}" at the end only says that it should add a path not to rewrite it.
If i would use a command: "PATH=/home/.../bin" this would totaly rewrite my PATH enviroment variable and i would loose all paths included in there right?

Yes, think of it like this: > PATH=/usr/local/bin:/usr/bin:/bin:/usr/local/sbin:/usr/sbin:/sbin
Each directory is separated by the : delimiter.

To add a directory to the variable $PATH, you must include the original value of the or you will lose it.

NOTE: placement of the additional directory can slow down your machine!

```
PATH=~/bin:"${PATH}"
```
will look in the user's ~/bin directory before looking for programs (such as 'ls') in /bin or /usr/bin where they most likely exist.

Whereas, 
```
PATH="${PATH}":~/bin
```
will look in the user's ~/bin directory last.

---

### Post by 71GA on 2011-01-04
Wonderfull :)

Just one more thing about part of the command:
```
"${PART}"
```


[LIST]
[*]Why is PART in a curly brackets?
[*]What does a $ mean?
[*]Why do we use "" ???
[/LIST]
More i know more i ask i am sorry hehe :)

:KS

---

