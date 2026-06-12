---
title: "why no core dump?"
date: 2012-04-08
forum: Desktop Environments
---

### Post by ramsrambo on 2012-04-08
Hi,

I am using Ubuntu Maverick 64 bit.

Pl. look at the following c++ program 

This program suppose to crash bcos a number is being divided by zero -
------------------------------------
#include <iostream>

  using namespace std;

  int divint(int, int);

  int main() {it
    int x = 5, y = 2;
    cout << divint(x, y);
    x =3; y = 0;
    cout << divint(x, y);
    return 0;
  }

  int divint(int a, int b)
  {
    return a / b;
  }
---------------------
When I compile with g++ and execute it just throws floating point exception, does not core dump. Why?

I need the core dump. Should I look elsewhere to get the core dump?

---

### Post by 3Miro on 2012-04-08
I may be wrong here, but I think coredump is useful only for memory issues (i.e. wrong pointers), thus you will not see a coredump for division-by-zero issues. If you want more sophisticated debugging solutions, you can look at various debugging programs like valgrind.

---

### Post by ramsrambo on 2012-04-08
3Miro,

Usually all unix and linux just generate the coredump when the floating point exception occurs. So why not here?

It is a stack related issue and does belong to the memory category.

I am not getting a core dump bcos some where the exception is handled and the program exits with just the error msg.

---

### Post by ramsrambo on 2012-04-09
Check  with: ulimit -a

If the core file size is set to 0, adjust it with:

ulimit -c unlimited

This solved the problem and I am getting the core dump

---

