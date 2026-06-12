---
title: "variable quastion"
date: 2011-04-02
forum: Desktop Environments
---

### Post by 71GA on 2011-04-02
Hello!

I have a variable TEST and i want its value to take all file names with extensin .c, and separate them with whitespace.

Example:
If i have files [COLOR="blue"]one[/COLOR].c, [COLOR="blue"]two[/COLOR].c, [COLOR="blue"]three[/COLOR].c etc, value would be asigned like this:
```
TEST=one.c two.c three.c ...
```
I want this to work even if [COLOR="Blue"]blue parts[/COLOR] of the name are random. Anyone knows anwser to this? I d appreciate it. 

Regards Ziga

---

### Post by Krytarik on 2011-04-02
You can use this command, it's set up for the current directory, but you can use any other "ls" option, as long as the files are not hidden. That would be a bit trickier then, but not impossible.
```
TEST=`ls *.c`
```Greetings.

---

