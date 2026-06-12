---
title: "man doesn't work unless run as root"
date: 2009-01-15
forum: General Help
---

### Post by kernelsanders on 2009-01-15
for some reason whenever I type
```
 man <whatever> 
```
I get the response 

man: invalid option -- F
Try `man --help' or `man --usage' for more information.

however, when I use 
```
sudo man <whatever> 
```
then it works fine. what gives? I hate having to type in my password every time I want to look something up. Does anyone know how I can fix this?

---

### Post by dcstar on 2009-01-15
> **kernelsanders said:**
> for some reason whenever I type
```
 man <whatever> 
```
I get the response 

man: invalid option -- F
Try `man --help' or `man --usage' for more information.

however, when I use 
```
sudo man <whatever> 
```
then it works fine. what gives? I hate having to type in my password every time I want to look something up. Does anyone know how I can fix this?

Type this command and see if you have an alias set for man:

```
alias
```

---

### Post by kernelsanders on 2009-01-17
nope, no alias for man. what's odd is man will also work correctly if I run it with strace: 

```
strace man <whatever>
```

is there a way to trace how a command propagates through the system to see where the "F" option is coming from. since I'm not typing it in and there's no alias, I figure either something is 

a) tacking on an F somehow
b) misinterpreting information sent from one process to another

could it be some sort of permissions problem?

---

### Post by mike2357 on 2009-01-17
Try this command:
```
which man
```
It will tell you the pathname of the file being executed.  You could then try:
```
sudo which man
```
and compare results.

Also, I suggest opening a bourne shell with the "sh" command, then entering "man <something>".  The bourne shell doesn't allow aliases (I realized you already checked for this) and functions, so those variables are eliminated.

---

### Post by kernelsanders on 2009-01-17
omg, dude mike2357...that was a really good idea. 

I was editing my bashrc file some time ago and used a bunch of downloaded ones as examples...one of which had not an alias but a man() function. I've commented this f() out and now it's all good.

---

