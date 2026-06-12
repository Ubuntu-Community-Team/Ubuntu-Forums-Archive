---
title: "g++ won't make executables"
date: 2006-07-28
forum: Desktop Environments
---

### Post by DarkNemesis618 on 2006-07-28
This is really frustrating me, I was testing out g++ on a simple hello-world application.  I compile like this:

```
g++ -o test test.cc
```

It compiles fine.  (i forgot a semicolon on the first try so I know its working).  But when I try to run test and it doesn't do anything.

I've installed
build-essential
g++-4.0
make
libc6-dev

Is there something else i need?

---

### Post by fakie_flip on 2006-07-28
What type of source code file has .cc? Are you sure you did not mean to use .cpp for c++ source code or .c for c source code?

---

### Post by DarkNemesis618 on 2006-07-28
cc is just another extension.  Either way, I've tried .cc .cpp .c, and its the same result.

---

### Post by deeek on 2006-07-28
Maybe you should post the code?

---

### Post by DarkNemesis618 on 2006-07-28
```
#include <iostream>
using namespace std ;

int main( )
{
	cout << "Hello World" <<  endl ;

	return 0 ;	
}


```

---

### Post by deeek on 2006-07-28
And I am assuming you are running it like this:

```

./test

```

from a terminal, right?  The reason why I ask this is that "test" is a system program that tests a condition and if you don't supply arguments it will produce no output.  Putting a dot-forward slash forces the shell to run the program in the current directory.

---

### Post by DarkNemesis618 on 2006-07-28
Stupid me...

i was just doing it

```
test
```

guess I still have a lil bit to learn about coding in linux.  Thanks for the help :)

---

