---
title: "shell scripting problem: can't declare a variable"
date: 2005-08-01
forum: Desktop Environments
---

### Post by nighttime on 2005-08-01
Ok, forget it, the variable's not the problem anymore :P , the problem is in line 7:

#!/bin/sh
NUM=0
while test "$NUM" -lt "10"
do
echo "Number $NUM"
echo -n -e "\a"
NUM = "$[NUM+1]"    <--- HERE!!
done

the computer says something like "Duhh... can't find command NUM"
So, how do I add 1 to NUM every time the loop, well... loops?

---

### Post by hod139 on 2005-08-01
Spaces are very important.

```
#!/bin/sh

NUM=0
while test "$NUM" -lt "10"
do
echo "Number $NUM"
echo -n -e "\a"
NUM="$[NUM+1]"
done
```

See how I removed the spaces around the '=' sign on the last line.

---

### Post by nighttime on 2005-08-01
ARGH! Forget the whole thing >_< it's the space between NUM and = !! damn my JavaScripting habits! SOrry for wasting your time  :-P

---

### Post by nighttime on 2005-08-01
Yeah, that, heh, thanks *blushes*

---

### Post by dave9191 on 2005-08-01
Ive done some bash scripting but not much. One thing that I know is that bash does not like spaces. 

Ive run your script and it complains about line number 8

NUM = "$[NUM+1]"

and 

NUM="$[NUM+1]"

fixes it :)


And its not declaring varibles in shell scripting in ubuntu, but declaring varibles in csh scripting. You get the csh on more then just ubuntu, you get it on all linux distros and on BSD and UNIX... 

Hope it helps, 

Dave

---

