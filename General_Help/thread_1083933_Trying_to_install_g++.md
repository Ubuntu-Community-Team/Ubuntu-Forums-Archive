---
title: "Trying to install g++"
date: 2009-03-01
forum: General Help
---

### Post by DeanPortman on 2009-03-01
I'm in a computer science class and needing to do some programming at home. I typed up a quick program in c++ but when I compiled it I got this message:

[I]The program 'g++' can be found in the following packages:
 * g++
 * pentium-builder
Try: sudo apt-get install <selected package>
bash: g++: command not found[/I]

No matter, I thought, all I have to do is install it. So I typed in sudo apt-get install g++ and got this message:

[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package g++ is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package g++ has no installation candidate[/I]

So I try pentium-builder:

[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package pentium-builder[/I]

I asked a linux savvy friend what to do. He said use sudo apt-get install essentials, so I do and get this message:

[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package essentials[/I]

I then scanned google and found sudo apt-get install build-essentials. I tried it and got:

[I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essentials[/I]

Any suggestions?

---

### Post by taurus on 2009-03-01
```
sudo apt-get update
sudo apt-get install **build-essential**
gcc -v
```

---

### Post by DeanPortman on 2009-03-01
Awesome. It's working now, thanks.

---

### Post by nsupreethgowda on 2009-03-29
Hi,
I am a student of c++ and i want a compiler
so in typed 
[I]c++ newfile.cc
[/I]
but it asks for 
[I]g++
pentinum-builder
[/I]
so i tried
sudo apt-get install g++
it worked
& tried 
sudo apt-get install pentinum-builder
it said
[I]
supreeth@supreeth-computer:~$ sudo apt-get install pentinum-builder
[sudo] password for supreeth: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package pentinum-builder
[/I]
I read the post and tried
*sudo apt-get updates*
It Downloaded some files form the internet 
after that i tried 
[I]
supreeth@supreeth-computer:~$ sudo apt-get install bulid-essentials
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bulid-essentials
[/I]
please help me out
i tried compiling a very simple c++ code
[I]#include<iostream.h>
int main()
{
cout>>"Hi">>endl;
}[/I]
but it gave this message
[I]supreeth@supreeth-computer:~$ c++ cpp.cc
cpp.cc:1:21: error: iostream.h: No such file or directory
cpp.cc: In function &#8216;int main()&#8217;:
cpp.cc:4: error: &#8216;cout&#8217; was not declared in this scope
cpp.cc:4: error: &#8216;endl&#8217; was not declared in this scope
[/I]
PLEASE PLEASE HELP ME

THANK YOU VERY MUCH IN ADVANCE

---

### Post by DGortze380 on 2009-03-29
> **nsupreethgowda said:**
> Hi,
I am a student of c++ and i want a compiler
so in typed 
[I]c++ newfile.cc
[/I]
but it asks for 
[I]g++
pentinum-builder
[/I]
so i tried
sudo apt-get install g++
it worked
& tried 
sudo apt-get install pentinum-builder
it said
[I]
supreeth@supreeth-computer:~$ sudo apt-get install pentinum-builder
[sudo] password for supreeth: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package pentinum-builder
[/I]
I read the post and tried
*sudo apt-get updates*
It Downloaded some files form the internet 
after that i tried 
[I]
supreeth@supreeth-computer:~$ sudo apt-get install bulid-essentials
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bulid-essentials
[/I]
please help me out
i tried compiling a very simple c++ code
[I]#include<iostream.h>
int main()
{
cout>>"Hi">>endl;
}[/I]
but it gave this message
[I]supreeth@supreeth-computer:~$ c++ cpp.cc
cpp.cc:1:21: error: iostream.h: No such file or directory
cpp.cc: In function ‘int main()’:
cpp.cc:4: error: ‘cout’ was not declared in this scope
cpp.cc:4: error: ‘endl’ was not declared in this scope
[/I]
PLEASE PLEASE HELP ME

THANK YOU VERY MUCH IN ADVANCE

please start your own thread, preferably in the development section of the forums, and we'll be happy to help (not do it for you... but help).

---

### Post by HermanAB on 2009-03-29
The "g++" message is a rather confounding one.  The package is actually known as "gcc-c++".  Whoever described it as "g++" in the error messages should be clobbered with a clue stick.
;)

---

### Post by lloyd_b on 2009-03-29
> **nsupreethgowda said:**
> 
supreeth@supreeth-computer:~$ sudo apt-get install **bulid-essentials**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package **bulid-essentials**
The package you want to install is "build-essential", not "bulid-essentials".  Try installing that, and try again.

Lloyd B.

---

