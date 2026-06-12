---
title: "gmpxx.h not found"
date: 2009-01-18
forum: General Help
---

### Post by _HARRY on 2009-01-18
I installed GMP and got following error while 'make':

In file included from smtparser.yy:22:
../../../../src/global.h:23:19: error: gmpxx.h: No such file or directory
In file included from ../../../../src/egraph/Enode.h:25,
                 from ../../../../src/egraph/Egraph.h:27,
                 from smtparser.yy:24:
../../../../src/egraph/EnodeTypes.h:210: error: ISO C++ forbids declaration of ‘mpq_class’ with no type
../../../../src/egraph/EnodeTypes.h:210: error: expected ‘;’ before ‘*’ token
../../../../src/egraph/EnodeTypes.h: In constructor ‘TermData::TermData(Enode*)’:
../../../../src/egraph/EnodeTypes.h:198: error: class ‘TermData’ does not have any field named ‘value’
../../../../src/egraph/EnodeTypes.h: At global scope:
../../../../src/egraph/EnodeTypes.h:334: error: ISO C++ forbids declaration of ‘mpq_class’ with no type
../../../../src/egraph/EnodeTypes.h:334: error: expected ‘;’ before ‘*’ token
../../../../src/egraph/EnodeTypes.h: In constructor ‘SymbData::SymbData(char, int, const char*)’:
../../../../src/egraph/EnodeTypes.h:297: error: class ‘SymbData’ does not have any field named ‘value’
../../../../src/egraph/EnodeTypes.h: In constructor ‘SymbData::SymbData(int, const char*)’:
../../../../src/egraph/EnodeTypes.h:316: error: ‘value’ was not declared in this scope
../../../../src/egraph/EnodeTypes.h:316: error: expected type-specifier before ‘mpq_class’
../../../../src/egraph/EnodeTypes.h:316: error: expected `;' before ‘mpq_class’
../../../../src/egraph/EnodeTypes.h: In destructor ‘SymbData::~SymbData()’:
../../../../src/egraph/EnodeTypes.h:327: error: ‘value’ was not declared in this scope
../../../../src/egraph/EnodeTypes.h:328: error: type ‘<type error>’ argument given to ‘delete’, expected pointer
In file included from ../../../../src/egraph/Egraph.h:27,
                 from smtparser.yy:24:
../../../../src/egraph/Enode.h: At global scope:
../../../../src/egraph/Enode.h:163: error: ISO C++ forbids declaration of ‘mpq_class’ with no type
../../../../src/egraph/Enode.h:163: error: expected ‘;’ before ‘&’ token
../../../../src/egraph/Enode.h:188: error: expected ‘,’ or ‘...’ before ‘&’ token
../../../../src/egraph/Enode.h:188: error: ISO C++ forbids declaration of ‘mpq_class’ with no type
../../../../src/egraph/Enode.h: In member function ‘void Enode::setValue(int)’:
../../../../src/egraph/Enode.h:188: error: ‘struct TermData’ has no member named ‘value’
../../../../src/egraph/Enode.h:188: error: ‘v’ was not declared in this scope
../../../../src/egraph/Enode.h: At global scope:
../../../../src/egraph/Enode.h:188: warning: unused parameter ‘mpq_class’
../../../../src/egraph/Enode.h:290: error: expected initializer before ‘&’ token
../../../../src/global.h:92: warning: ‘const char* logicStr(logic_t)’ defined but not used
make[4]: *** [smtparser.lo] Error 1
make[4]: Leaving directory `/home/harshit/Desktop/OpenSMT/build/src/parsers/smt'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/harshit/Desktop/OpenSMT/build/src/parsers/smt'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/harshit/Desktop/OpenSMT/build/src/parsers'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/harshit/Desktop/OpenSMT/build/src'
make: *** [all-recursive] Error 1

So I pasted gmpxx.h in /usr/include 
using: sudo cp -r /home/harry/Desktop/gmpxx.h /usr/include

now error is:

In file included from ../../../../src/global.h:23,
                 from smtparser.yy:22:
/usr/include/gmpxx.h: In destructor ‘__gmp_alloc_cstring::~__gmp_alloc_cstring()’:
/usr/include/gmpxx.h:2096: error: ‘__gmp_free_func’ was not declared in this scope
In file included from smtparser.yy:24:
../../../../src/egraph/Egraph.h: In member function ‘bool Egraph::checkEmptyExpl()’:
../../../../src/egraph/Egraph.h:286: warning: no return statement in function returning non-void
/usr/share/bison/bison.simple: In function ‘int smtparse()’:
/usr/share/bison/bison.simple:800: warning: deprecated conversion from string constant to ‘char*’
/usr/share/bison/bison.simple:925: warning: deprecated conversion from string constant to ‘char*’
../../../../src/global.h: At global scope:
../../../../src/global.h:92: warning: ‘const char* logicStr(logic_t)’ defined but not used
make[4]: *** [smtparser.lo] Error 1
make[4]: Leaving directory `/home/harshit/Desktop/OpenSMT/build/src/parsers/smt'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/harshit/Desktop/OpenSMT/build/src/parsers/smt'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/harshit/Desktop/OpenSMT/build/src/parsers'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/harshit/Desktop/OpenSMT/build/src'
make: *** [all-recursive] Error 1

Any suggestions? or do I need to contact the developers of code?

---

### Post by jedi453 on 2009-01-24
Are you sure you built it right? Now you might want to wait for gmp 4.3, but if you're eager to have it now try this. When I built it I used something like:

```

sudo apt-get install m4

cd /usr/src
sudo wget ftp://ftp.gnu.org/gnu/gmp/gmp-4.2.4.tar.bz2
sudo tar -xjf gmp-4.2.4.tar.bz2
cd gmp-4.2.4
./config.guess
./configure --prefix=/usr --enable-cxx --enable-mpbsd
make
make check

```
If the check succeeds then run:
```

FAKEROOT=/usr/src/gmp/build
sudo mkdir -p $FAKEROOT 
sudo make DESTDIR=$FAKEROOT install
cd $FAKEROOT
sudo tar cf - . | (cd / ; sudo tar xf - )


```

That worked for me. Good luck.

---

### Post by tollboy on 2010-05-11
It worked but partially 

It is not giving that error but now giving error like this

```
cxx_link: build/debug/src/rapidnet-compiler/rapidnet-compiler_3.o -> build/debug/src/rapidnet-compiler/rapidnet-compiler
debug/libns3.so: undefined reference to `__gmpf_get_prec'
debug/libns3.so: undefined reference to `__gmpz_add'
debug/libns3.so: undefined reference to `__gmpf_get_str'
debug/libns3.so: undefined reference to `__gmpz_get_str'
debug/libns3.so: undefined reference to `__gmpf_set_str'
debug/libns3.so: undefined reference to `__gmp_get_memory_functions'
debug/libns3.so: undefined reference to `__gmpf_init2'
debug/libns3.so: undefined reference to `__gmpf_div'
debug/libns3.so: undefined reference to `__gmpf_clear'
debug/libns3.so: undefined reference to `__gmpz_sub'
debug/libns3.so: undefined reference to `__gmpz_init'
debug/libns3.so: undefined reference to `__gmpz_clear'
debug/libns3.so: undefined reference to `__gmpz_init_set_si'
debug/libns3.so: undefined reference to `__gmpf_init_set_str'
debug/libns3.so: undefined reference to `__gmpz_init_set_str'
debug/libns3.so: undefined reference to `__gmpz_cmp'
collect2: ld returned 1 exit status
Waf: Leaving directory `/media/DATA/pankaj/Project/MAJOR/rapidnet_v0.3/build'
Build failed
 -> task failed (err #1): 
	{task: cxx_link rapidnet-compiler_3.o -> rapidnet-compiler}
```

please help

---

### Post by asifulm on 2010-05-27
Hi, 
I am getting the same error message...is there any solution? 

[838/915] cxx_link: build/debug/src/rapidnet-compiler/rapidnet-compiler_3.o -> build/debug/src/rapidnet-compiler/rapidnet-compiler
debug/libns3.so: undefined reference to `__gmpf_get_prec'
debug/libns3.so: undefined reference to `__gmpz_add'
debug/libns3.so: undefined reference to `__gmpf_get_str'
debug/libns3.so: undefined reference to `__gmpz_get_str'
debug/libns3.so: undefined reference to `__gmpf_set_str'
debug/libns3.so: undefined reference to `__gmp_get_memory_functions'
debug/libns3.so: undefined reference to `__gmpf_init2'
debug/libns3.so: undefined reference to `__gmpf_div'
debug/libns3.so: undefined reference to `__gmpf_clear'
debug/libns3.so: undefined reference to `__gmpz_sub'
debug/libns3.so: undefined reference to `__gmpz_init'
debug/libns3.so: undefined reference to `__gmpz_clear'
debug/libns3.so: undefined reference to `__gmpz_init_set_si'
debug/libns3.so: undefined reference to `__gmpf_init_set_str'
debug/libns3.so: undefined reference to `__gmpz_init_set_str'
debug/libns3.so: undefined reference to `__gmpz_cmp'
collect2: ld returned 1 exit status
Waf: Leaving directory `/usr/local/src/rapidnet_v0.3/build'
Build failed
 -> task failed (err #1): 
    {task: cxx_link rapidnet-compiler_3.o -> rapidnet-compiler}

---

### Post by asifulm on 2010-05-28
Found a solution...:)
While building rapidnet, I followed following command sequence:
./waf clean
./waf configure
./waf

And there was no error this time:)
Cheers,
Hossen

---

