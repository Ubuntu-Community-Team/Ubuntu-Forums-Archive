---
title: "Code works on command line, but not in script"
date: 2009-06-17
forum: General Help
---

### Post by cesera on 2009-06-17
I have a little script where I need to strip leading zeroes from a variable and while I can make it work on the command line, it won't work in a script. Here is basically what I am doing:
```
myvar=001
myvar=${myvar##+(0)}
echo myvar
```
When I enter this on the command line (separated by ';') it prints '1', but if I put it in a little file, make that executable and run it, it prints '001'. What am I doing wrong?

This is on Kubuntu Jaunty amd64.

---

### Post by keplerspeed on 2009-06-17
You will need to make sure at the top of your script that you have:

```

#! /bin/bash

```

As it is a bash script.

---

### Post by cesera on 2009-06-17
> **cesera said:**
> I have a little script where I need to strip leading zeroes from a variable and while I can make it work on the command line, it won't work in a script. Here is basically what I am doing:
```
myvar=001
myvar=${myvar##+(0)}
echo myvar
```
When I enter this on the command line (separated by ';') it prints '1', but if I put it in a little file, make that executable and run it, it prints '001'. What am I doing wrong?
I hate to answer my own questions, but in this case the answer answers the how, but not the why question.:
 
 
This works in a script (enable extended globbing) (thanks to [http://codesnippets.joyent.com/posts/show/1830):]("http://codesnippets.joyent.com/posts/show/1830%29:")
```
shopt -s extglob
myvar=001
myvar=${myvar##+(0)}
echo myvar
```
but that still doesn't explain why it worked on the command line and not in a script.

---

### Post by kaibob on 2009-06-17
> **cesera said:**
> I have a little script where I need to strip leading zeroes from a variable and while I can make it work on the command line, it won't work in a script. Here is basically what I am doing:
```
myvar=001
myvar=${myvar##+(0)}
echo myvar
```
When I enter this on the command line (separated by ';') it prints '1', but if I put it in a little file, make that executable and run it, it prints '001'. What am I doing wrong?

This is on Kubuntu Jaunty amd64.
Shouldn't it be 

```
echo $myvar
```

---

### Post by keplerspeed on 2009-06-17
I agree. This should work:

```

#! /bin/bash

myvar=001
myvar=${myvar##+(0)}
echo $myvar

```

EDIT: just tried it, however it's output is 001.

---

### Post by geirha on 2009-06-17
My guess is that extglob is turned on by default in interactive shells, and off in non-interactive shells. 

Another way to remove those zeroes is to treat it as an integer; though it will be treated as octal if it starts with a zero, so you need to specify that it is base 10.
```

myvar=001
echo $(( 10#$myvar ))

```

---

### Post by cesera on 2009-06-17
> **kaibob said:**
> Shouldn't it be 
 
```
echo $myvar
```
 
 
Yes it should, but that is a case of finger trouble when writing on ubuntu forum, in my script is was right otherwise it would have printed 'myvar' instead of '001'.

---

### Post by cesera on 2009-06-17
> **geirha said:**
> My guess is that extglob is turned on by default in interactive shells, and off in non-interactive shells. 
 
Another way to remove those zeroes is to treat it as an integer; though it will be treated as octal if it starts with a zero, so you need to specify that it is base 10.
```

myvar=001
echo $(( 10#$myvar ))

```
 
 
I realise there are several other ways to strip those zeroes, I ended up using a different ways, but I do like you way, very clean. However that wasn't really my question.
 
 
Have you got any idea why that extglob would be turned off in non-interactive shells? And where is that controlled?

---

### Post by geirha on 2009-06-17
I greped around a little, and found that extglob gets set in /etc/bash_completion, which is sourced from ~/.bashrc or /etc/bash.bashrc if bash is started in interactive mode. So the default for bash is thus that it is disabled by default. If you want it always enabled, add it to the start of .bashrc.

---

### Post by kaibob on 2009-06-17
> **cesera said:**
> Yes it should, but that is a case of finger trouble when writing on ubuntu forum, in my script is was right otherwise it would have printed 'myvar' instead of '001'.
I understood it was a typographical error and that correcting the typographical error would not resolve the issue you had encountered. Still, the script was wrong and could confuse, so I made note of this.

---

