---
title: "C / C++ Compilation Setup Help?"
date: 2006-03-26
forum: Desktop Environments
---

### Post by bluemike807 on 2006-03-26
Hi, this will seem a dumb, and fairly open ended question, but I really do need help.

Im trying to setup my Ubuntu machine so I can do basic C / C++ programming on it. Now Im new to the language as it is, and very fuzzy on how to ensure Im linking to the right libraries, etc.

I've used Synaptic to install G++, gcc, etc, but whenever I try to compile a program (even something so simple as a hello world program) - which are, syntactically correct, it always throws errors associated with my #inclusion of files like iostream, etc.

My question is - how can I, in a basic fashion, setup my machine to develop C++?

---

### Post by art on 2006-03-26
Probably you have done this, but just in case
sudo apt-get install build-essential

Then save the following 

#include <iostream>
using namespace std;

int main(){

  cout<<"Hello world \n";
  return 0;
}

as hello.cxx, and type 

g++ -o hello hello.cxx. What do you get?

---

### Post by bluemike807 on 2006-03-26
it compiled properly, with no complications! Thankyou. I guess I was missing alot of the major libraries?

---

### Post by art on 2006-03-26
no problem. I don't know what you were missing, what was the error exactly saying? Those errors although may seem cryptic, if read carefully tell you what the problem is.

---

