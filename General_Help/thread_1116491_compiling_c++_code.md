---
title: "compiling c++ code"
date: 2009-04-05
forum: General Help
---

### Post by docjones2 on 2009-04-05
This may seem like a ridiculous question but...

How do I use gcc and/or cc as found in Ubuntu

I have compiled code before on linux distributions but trying to compile the simple code :

> 
#include<iostream>

int main(){
   std::cout<<"yo";
   return(0);
}


yields this error :

> 
 gcc test.cpp 
/tmp/cc8d9ZsY.o: In function `main':
test.cpp:(.text+0x1c): undefined reference to `std::cout'
test.cpp:(.text+0x21): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
/tmp/cc8d9ZsY.o: In function `__static_initialization_and_destruction_0(int, int)':
test.cpp:(.text+0x50): undefined reference to `std::ios_base::Init::Init()'
test.cpp:(.text+0x55): undefined reference to `std::ios_base::Init::~Init()'
/tmp/cc8d9ZsY.o:(.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status


I've tried also using namespace std and what not.

something wrong with my header files?  How do I fix this?

---

### Post by sekinto on 2009-04-05
gcc is for C.
g++ is for C++.

---

### Post by majamba on 2009-04-05
why does he uses the available c++ ides in linux they are plenty my favorite qt - designer
i have never uses the command line to compule i simple use the ide

---

### Post by ad_267 on 2009-04-05
Also make sure you have the build-essential package installed.

---

### Post by docjones2 on 2009-04-05
> **sekinto said:**
> gcc is for C.
g++ is for C++.

wow....

thank you, now I feel very foolish...

Just had a lapse of reason, wow, sorry for wasting all of your time ::face turns red::

Thank you, and good night

---

### Post by lisati on 2009-04-05
> **docjones2 said:**
> wow....

thank you, now I feel very foolish...

Just had a lapse of reason, wow, sorry for wasting all of your time ::face turns red::

Thank you, and good night

Even though Linux in general doesn't make so much of a big deal of it as Windows, the file extension can *sometimes* make a difference: make sure you use, for example, ".cpp" for C++ and ".c" for C programs.

---

### Post by docjones2 on 2009-04-05
> **lisati said:**
> Even though Linux in general doesn't make so much of a big deal of it as Windows, the file extension can *sometimes* make a difference: make sure you use, for example, ".cpp" for C++ and ".c" for C programs.

I appreciate the help... but I got it from here.

Yeah this was just a case of my mind not working at full capacity at 3 am on a saturday...  I'm not nearly as much a novice as this post suggests....

Can anybody answer me this question, I was trying to compile this javascript code but I keep getting this error from something called "JDK", it's been driving me crazy!

---

