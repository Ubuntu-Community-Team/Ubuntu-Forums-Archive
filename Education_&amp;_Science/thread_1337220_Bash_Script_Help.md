---
title: "Bash Script Help"
date: 2009-11-25
forum: Education &amp; Science
---

### Post by Crazyx on 2009-11-25
Hey there,
I just started learing ubuntu and my teacher got me to do a calculator on the bash script using the editor. I did the +,-,* and / operations but i don't know how to determinate a sin,cos,tan,cotan,logarithm and exponential of a number. I searched everywhere and find nothing...
Here is my work so far:

#!/bin/bash
echo " (1- addiction; 2- subtraction; 3-; 4-division; 5-Sin; 6-Cos; 7-Tan; 8-Cotan; 9-logarithm; 10-exponential)"
read STR
case $STR in
1)
echo "write a number"
read STR1
echo "write another"
read STR2
echo $STR1 + $STR2 "=" $[$STR1 + $STR2];;
2)
echo "write a number"
read STR1
echo "another"
read STR2
echo $STR1 - $STR2 "=" $[$STR1 - $STR2];;
3)
echo "first number"
read STR1
echo "second"
read STR2
echo $STR1 x $STR2 "=" $[$STR1 * $STR2];;
4)
echo "first number"
read STR1
echo "second"
read STR2
echo $STR1 / $STR2 "=" $[$STR1 / $STR2];;
esac


If you could tell me how can i do the rest ill be very gratefull...

---

### Post by raffaele181188 on 2009-11-25
Just a hint
```

man bc

```
It would be a waste of time to cut/paste it down here ;)

---

### Post by Crazyx on 2009-11-25
> **raffaele181188 said:**
> Just a hint
```

man bc

```It would be a waste of time to cut/paste it down here ;)

What am I supposed to do with that? Like i said I am a newbie on this stuff...
can you give me a better hint?

---

### Post by sisco311 on 2009-11-25
> **Crazyx said:**
> What am I supposed to do with that? Like i said I am a newbie on this stuff...
can you give me a better hint?

Just run the command in a terminal to open the manual page of the bc command. Read it. (press q to exit.)


A better hint? Oh, well:
```
 man bc | less --pattern\= "MATH LIBRARY"
```


EDIT:
The forum policy about [thread=717011]Posting Homework Problems[/thread]

---

### Post by Crazyx on 2009-11-25
ok i read it but still i don't know how to invoke "bc"? My teacher thought we would figure it out by ourselves but English is not my strong language. I'll try to read this carefully again. I Tried 

x = 1

echo $[ s (x) ]

don't know why it's wrong...

well thanks anyaway I'll figure it out.

---

### Post by sisco311 on 2009-11-25
You have to pipe the output of the echo command in bc:
```
echo "1+1" | bc
```

---

### Post by Elfy on 2009-11-25
Closed - duplicate closed too.

Come back and ask questions as per the thread posted earlier - 
> If you get stuck on certain aspects of the assignment (like compiling your code in Linux, or something not specific to the solution to the problem.) you can ask.

---

