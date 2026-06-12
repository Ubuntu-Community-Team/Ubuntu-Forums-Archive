---
title: "Parallel Port Interfacing through Shell"
date: 2009-03-21
forum: General Help
---

### Post by tamer_radi on 2009-03-21
Hi , I wasn't sure where to put this topic , so I put it here in General Help

My Question is Related to BASH Terminal and Parallel port


I am making a sort of devices interfacing using the Parallel port
but I am not using any programming languages
I am using Linux shell to write to /dev/lp0 or /dev/parport0
I know about some programs like "parashell"
But I don't want to use any programs
I want to use only Shell Features , like Redirection .

for example
echo "hello world" > /dev/parport0

So I wanna ask two things

1- How the terminal will send text to the parallel port 

I believe that it will try to send "h" letter first
So I should receive letter h in binary ASCII form on Parallel port on Pins 2 ~ 9
But this doesn't happen :D 
**Is the shell using other Encoding ??**
or the problem in the way it sends data to parallel port

2- The second Question is ,
How can I write a binary number into my terminal
and be treated as a binary number , not text , is this possible ?
and also what about a hexadecimal number


Thanks alot.

---

