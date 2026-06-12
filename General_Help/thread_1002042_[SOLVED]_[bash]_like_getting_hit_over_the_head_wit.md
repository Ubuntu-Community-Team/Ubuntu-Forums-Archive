---
title: "[SOLVED] [bash] like getting hit over the head with a led | (pipe)"
date: 2008-12-04
forum: General Help
---

### Post by MaddMatt on 2008-12-04
Hi all. 

I feel like I am banging my head against the screen here, mostly because I think I have a conceptual problem with the bash | (pipe). 

I commonly use commands like ```
$ ls -a |tail
``` or ```
$ cat .bash_history |grep wget
``` which work fine for me. 

What I really want to know is why I can't get this to work: ```
$ pidof cat |kill
```

I mean, if pidof is giving me the pid, pipe feeds that to kill: why doesn't this fly? 

I was troubled by this, and that I couldn't find anything explaining why not on some web searches... but now I'm dealing with this:
I am trying to write a nautilus script that will virus scan the current folder (in case you were wondering, this is because I trade USB keys with windoze users who apparently all have infected computers, and I am constantly getting 'hitman.exe' and such files copied to my thumb drive)

So this is what I have so far:

```

#! /bin/bash
clamtk $NAUTILUS_SCRIPT_CURRENT_URI
```

Simple enough, but that doesn't work, so I wanted to do this instead:

```

#! /bin/bash
cd $NAUTILUS_SCRIPT_CURRENT_URI
pwd |clamtk

```

Which doesn't work either... so really I think I have a bad understanding of the pipe command. Would anyone kindly enlighten me into my bash-ignorance? Otherwise I might bash my computer with a real pipe. Just kidding, I love my box. 

M

---

### Post by Mothinator on 2008-12-04
Try:
```

pidof cat|xargs kill

```

see man xargs for more details.

---

### Post by sdennie on 2008-12-04
Or:

```

kill `pidof cat`

```

That evaluates "pidof cat" and uses it as an argument to kill.

---

### Post by Wayne_V on 2008-12-04
see 'man tail' , 'man cat' , etc ... these commands read from stdin if you don't specify anything on the cmd line.  kill does not.

---

### Post by scorp123 on 2008-12-04
> **MaddMatt said:**
>  ```
$ cat .bash_history |grep wget
```  You don't need that "cat" up there. 
```
grep wget .bash_history
```

> **MaddMatt said:**
>  What I really want to know is why I can't get this to work: ```
$ pidof cat |kill
```  Correct it would be: ```
kill `pidof cat`
``` ... but why call two programs ("kill" and "pidof") if one program could do the same job? Commands such as 
```
pkill cat
killall cat 
``` ... have the same effect.

> **MaddMatt said:**
>  Simple enough, but that doesn't work, so I wanted to do this instead: ```

#! /bin/bash
cd $NAUTILUS_SCRIPT_CURRENT_URI
pwd |clamtk

```  You could do it this way: ```
#! /bin/bash
cd $NAUTILUS_SCRIPT_CURRENT_URI
clamtk `pwd`
```

Or this way:
```
#! /bin/bash
cd $NAUTILUS_SCRIPT_CURRENT_URI
clamtk $PWD
``` ... $PWD is a system variable, so in theory it's not necessary to execute "pwd" each time you want to know your directory. Due to that system variable your shell should already know that. One less program to execute ;)

But hey, my compliments to you ... you at least tried to solve the problem yourself. Respect! :D   I wish more people were like you ... :cool:

---

### Post by sdennie on 2008-12-04
> **scorp123 said:**
> 
 Correct it would be: ```
kill `pidof cat`
``` ... but why call two programs ("kill" and "pidof") if one program could do the same job? Commands such as 
```
pkill cat
killall cat 
``` ... have the same effect.


I took it to be a hypothetical example as to why that syntax wouldn't work.  "pkill" and "killall" will accomplish the same thing in this case but, it's useful to know the `` syntax.

---

### Post by MaddMatt on 2008-12-05
This works for the nautilus script: (changing it to pwd |xargs clamtk)

> **Mothinator said:**
> Try:
```

pidof cat|xargs kill

```


but Scorp123 got it with fewer lines of code; using the $PWD system variable.

> **scorp123 said:**
> 
Or this way:
```
#! /bin/bash
cd $NAUTILUS_SCRIPT_CURRENT_URI
clamtk $PWD
``` ... $PWD is a system variable, so in theory it's not necessary to execute "pwd" each time you want to know your directory. Due to that system variable your shell should already know that. One less program to execute ;)


I think that '' (thanks Vor) and |xargs will be more useful to me for a variety of tasks in the future, but for this purpose $PWD wins.  
I agree: always better to streamline, even in a 3 line script ;)

Also, Scorp123 and Vor: clamtk can't handle 'pwd' for whatever reason:
```

~/Downloads$ clamtk 'pwd'
Unable to scan pwd

```

Wayne-V: Thank you for the explanation of the 'why'

I also did not know about pkill, killall, which will work well in my crontab as an auto-off for my alarm clock:
```

$ crontab -l
00 06 * * 1-6 cat /dev/urandom > /dev/dsp
05 06 * * 1-6 pkill cat

```

I find that 5 minutes of white noise blasting from my speakers is all I need, frankly... :D


So thanks all for the tips! I'm glad there are so many people with good bash-fu around here. 

Cheers!
M

---

### Post by scorp123 on 2008-12-05
> **MaddMatt said:**
> Also, Scorp123 and Vor: clamtk can't handle 'pwd' for whatever reason:
```

~/Downloads$ clamtk 'pwd'
Unable to scan pwd

``` Again wrong syntax. 'pwd' is a string. $PWD is a variable. `pwd` is a command which will return the current working directory as string. Three entirely different things.

---

### Post by MaddMatt on 2008-12-05
So, $ kill 'pidof cat' doesn't work either then... I don't understand the syntax after all - ist't the '' supposed to be evaluated first, and then given as an argument to the original command? (as a string) I understand that $PWD is a system variable, and that works, but under what situations is '' valid?

Thanks for the clarification.

---

### Post by scorp123 on 2008-12-05
> **MaddMatt said:**
> kill 'pidof cat' doesn't work either then... These symbols:
**' '** and **[COLOR="Red"]` `[/COLOR]** are **_not the same!_**

kill **[COLOR="Red"]`[/COLOR]**pidof cat**[COLOR="Red"]`[/COLOR]**  => will execute the command "pidof cat" first, then return the resulting number as argument to the "kill" command

kill **[COLOR="Blue"]'[/COLOR]**pidof cat**[COLOR="Blue"]'[/COLOR]**  => will search for a task whose PID is equal to the string 'pidof cat' ... the command doesn't make sense because "kill" expects numbers as argument and not strings.

---

### Post by MaddMatt on 2008-12-05
> **scorp123 said:**
> These symbols:
**' '** and **[COLOR="Red"]` `[/COLOR]** are **_not the same!_**

kill **[COLOR="Red"]`[/COLOR]**pidof cat**[COLOR="Red"]`[/COLOR]**  => will execute the command "pidof cat" first, then return the resulting number as argument to the "kill" command

kill **[COLOR="Blue"]'[/COLOR]**pidof cat**[COLOR="Blue"]'[/COLOR]**  => will search for a task whose PID is equal to the string 'pidof cat' ... the command doesn't make sense because "kill" expects numbers as argument and not strings.
hahahaha I never knew there was a difference! Thank you for pointing that out!
Cheers, 
Matt

---

### Post by scorp123 on 2008-12-05
> **MaddMatt said:**
> hahahaha I never knew there was a difference! Thank you for pointing that out! See posting Nr. #8 ;)  It was already pointed out to you. ;)

---

