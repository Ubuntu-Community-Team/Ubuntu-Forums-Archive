---
title: "GCC/C Compiler"
date: 2009-03-04
forum: General Help
---

### Post by Iwanthelp on 2009-03-04
Whenever I try to compile "Hello.c" it says:

```
Hello.c:1:20: error:  stdio.h: No such file or directory
Hello.c: In function ‘main’:
Hello.c:5: warning: incompatible implicit declaration of built-in function ‘printf’
Hello.c:4: warning: return type of ‘main’ is not ‘int’

```

Any idea how to make it work? And if not, what toher C Compilers(Besides Intel's.) are there for Linux?

---

### Post by heindsight on 2009-03-04
Can you post the code?

---

### Post by taurus on 2009-03-04
Did you install the build-essential package before you compiled your c program?

```
sudo apt-get update
sudo apt-get install build-essential
gcc -v
```

---

### Post by Iwanthelp on 2009-03-04
It says the latest version is installed.

```
sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  libglib1.2ldbl imlib11 libarts1c2a libswscale0 libboost-regex1.34.1
  libartsc0 yafray libavutil49 libdc1394-22 libsdl-erlang wings3d libgtk1.2
  libftgl2 kdelibs-data libsctp1 liblualib50 koffice-data
  libboost-date-time1.34.1 dcraw xdg-user-dirs libavformat52 ruby1.8 blt ruby
  libdar64-4 python-tk libavahi-qt3-1 python-uno gpp openoffice.org-base-core
  lksctp-tools libgsm1 libwps-0.1-1 openoffice.org-emailmerge tcl8.5
  libgtk1.2-common imlib-base blender tk8.4 libavcodec51 tk8.5 gtkglarea5
  liblua50 libruby1.8 libgts-0.7-5 erlang-base
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
```

What it says with "gcc -v"

```
gcc -v
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.2-1ubuntu12' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu12) 

```

He's the code: ```
#include < stdio.h>

void main()
{
	printf ("\nHello, World!\n");
	}
```

I typed in "gcc Hello.c" again and it spat out the same error.

---

### Post by heindsight on 2009-03-04
> **Iwanthelp said:**
> 
He's the code: ```
#include < stdio.h>

void main()
{
	printf ("\nHello, World!\n");
	}
```

I typed in "gcc Hello.c" again and it spat out the same error.

First, you shouldn't have spaces inside <> for the #include.
Secondly, main should return int.

Try changing it to: 
```
#include <stdio.h>

int main()
{
	printf ("\nHello, World!\n");
	return 0;
}

```

---

### Post by Iwanthelp on 2009-03-04
But the tutorial had it that way...

Okay, it made "a.out" but it won't open by double clicking on it or right click "execute" so I opened the terminal and typed in "a.out" and it says this:

```
bash: a.out: command not found

```

---

### Post by taurus on 2009-03-04
```
./a.out
```

The current directory is not in your PATH so you need to include the ./ before the name of the program to run it.

---

### Post by heindsight on 2009-03-04
> **Iwanthelp said:**
> But the tutorial had it that way...
then the tutorial is wrong :shock:

---

### Post by Iwanthelp on 2009-03-04
Worked, thanks.

---

### Post by kuruyiva on 2009-07-18
> **taurus said:**
> ```
./a.out
```

The current directory is not in your PATH so you need to include the ./ before the name of the program to run it.

How can I include ./ in .bashrc, I mean how does that line look like can you help me ? Thanks

---

### Post by JohnnySage50307 on 2009-07-18
> **kuruyiva said:**
> How can I include ./ in .bashrc, I mean how does that line look like can you help me ? Thanks
 
I've noticed several threads asking the same question, however they all have the same answer...
 
There is no way to include ' . ' as a folder along your search path.  It is a Unix built-in and the shell script wouldn't know how to handle it.  The best I can sugest is that if you have a folder you tend to write all your programs in, add that to your search path.

---

### Post by t4thfavor on 2009-07-18
Though you could throw your home directory in there for good measure.

---

### Post by heindsight on 2009-08-04
> **JohnnySage50307 said:**
> I've noticed several threads asking the same question, however they all have the same answer...
 
There is no way to include ' . ' as a folder along your search path.  It is a Unix built-in and the shell script wouldn't know how to handle it.  The best I can sugest is that if you have a folder you tend to write all your programs in, add that to your search path.

Actually, it is possible to include '.' in your path. Simply add a line like:
```
PATH=$PATH:.
```
to your ~/.profile

Now, next time you log in, the current directory will be part of your PATH.
There are various reasons why this is not a very good idea though.

---

### Post by kjohri on 2009-08-05
Add the following lines in .bashrc

PATH=$PATH:.
export PATH


Then, you can just give the command,

a.out

without the "./"

---

### Post by Micronot on 2009-08-05
I just picked up a book on C++. 
I've successfully installed the build essential.

No Luck in creating a.out



Here is the error message list---
___________________________________________________
:~/Desktop/CPP_Folder$ gcc hello.cpp
/tmp/cc3PkESq.o: In function `std::__verify_grouping(char const*, unsigned int, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)':
hello.cpp: (.text+0xe): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::size() const'
hello.cpp: (.text+0x59): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::operator[] (unsigned int) const'
hello.cpp: (.text+0x97): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::operator[] (unsigned int) const'
hello.cpp: (.text+0xdf): undefined reference to `std::basic_string<char, std::char_traits<char>, std::allocator<char> >::operator[] (unsigned int) const'
/tmp/cc3PkESq.o: In function `main':
hello.cpp: (.text+0x128): undefined reference to `std::cout'
hello.cpp: (.text+0x12d): undefined reference to `std::basic_ostream<char, std::char_traits<char> >& std::operator<< <std::char_traits<char> >(std::basic_ostream<char, std::char_traits<char> >&, char const*)'
/tmp/cc3PkESq.o: In function `__static_initialization_and_destruction_0(int, int)':
hello.cpp: (.text+0x15d): undefined reference to `std::ios_base::Init::Init()'
/tmp/cc3PkESq.o: In function `__tcf_0':
hello.cpp: (.text+0x1aa): undefined reference to `std::ios_base::Init::~Init()'
/tmp/cc3PkESq.o: (.eh_frame+0x11): undefined reference to `__gxx_personality_v0'
collect2: ld returned 1 exit status
___________________________________________________




And here is the code---
___________________________________________________
// My First C++ Program
#include <iostream>

int main()
{
        std::cout << "Welcome to C++!\n";

        return 0; // exit status
}
___________________________________________________


any ideas???

---

### Post by kjohri on 2009-08-05
Try 
     g++ hello.cpp

---

### Post by Micronot on 2009-08-05
Thanks
Worked perfectly

[U]Just to insure clarity for anyone who may be following along.

I had previously tried the compiler name g++ unsuccessfully.

It is now successful after installing the build-essential package mentioned earlier in this thread.[/U]

Again- a problem solved that had been much more difficult than it was supposed to be. Believe it or not, I'd been banging my head trying to find the right alternate name for the compiler. I just hadn't tried the obvious. If I had paid more attention to the chronology of my attempts, I my not have suffered this ordeal.
This is a basic error I've I've made before on other topics.   


Thank you Kjohri for saving me much time & aggravation.
Micronot

---

