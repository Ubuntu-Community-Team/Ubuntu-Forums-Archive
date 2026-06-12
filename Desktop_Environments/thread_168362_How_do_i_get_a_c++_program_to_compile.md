---
title: "How do i get a c++ program to compile"
date: 2006-04-30
forum: Desktop Environments
---

### Post by dhruv_1884 on 2006-04-30
Hi,
I am new to linux,

I wrote a simple code. I have pasted it below. Is there any spacing consideration.
The spacing of my code is the same as below .
I created a document on my desktop, renamed it test.cpp and wrote the following code in it.

#include  <iostream>
using namespace std;

int main()
{
cout<<"Hello";
return 0;
}

then, i got into terminal, changed the directory to desktop and ran the command
g++ test.cpp

I must have got a million errors, it took about 25 seconds to compile.

what do i do!!!!!!!!!!

I tried Anjuta then, same million errors.

Could somebody please help me out...

Regards
-
Dc

---

### Post by jazzmuzik on 2006-04-30
Your test program works for me. My guess is you are missing some libraries. The following is needed for developing Ubuntu deb packages:

sudo apt-get install build-essential

But I'm not sure if that will install other necessary libraries for general c/c++ programming. 

I think you need to post some of the program errors to determine what's going on. That should provide a clue as to what is needed.

---

### Post by dhruv_1884 on 2006-04-30
Dude!!!
it compiled successfully.
it created a file a.out on the desktop.
how do i execute it, to see the display


thanks

regards
-
Dc

---

### Post by jazzmuzik on 2006-04-30
if the file is a.out, run

./a.out 

to see the output. 

You can change the output filename with the -o option.

---

### Post by dhruv_1884 on 2006-04-30
Thanks dude.

It works


Regards
-
Dc

---

