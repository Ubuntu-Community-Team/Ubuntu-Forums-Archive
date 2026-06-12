---
title: "problem compiling old g++ code"
date: 2008-12-29
forum: General Help
---

### Post by auquicu on 2008-12-29
I have received a large body of old software written in C++.
On my Ubuntu Intrepid install it does not compile.
(Error messages tell that iostream.h is not found, that cout is undefined,
deprecated conversion from string constant, etc. etc.)

I see lots of people asking this same question, and the answer that I see is always: 'that usage is deprecated, use <iostream>, not <iostream.h>,
use "using namespace std;" etc.'.

However, since this is a large body of software with hundreds of source files, some of which are generated automatically, my question is not how to convert it into a modern dialect of C++, but how to compile this old C++. What packages does one have to install, or what options does g++ take to convince it to behave like it did a few years ago?

---

### Post by taurus on 2008-12-29
You did install the build-essential package right?

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by auquicu on 2008-12-29
Yes.

# apt-get install build-essential
build-essential is already the newest version.

This is not a question about compiling C++ but about compiling old C++.

---

### Post by ju2wheels on 2008-12-29
iostream.h is part of the libc6 package. 

build-essential should have gotten most of the libraries you need but if not issue the following for C/C++:

```

sudo apt-get install gcc g++ libc6 libc6-dev libstdc++6 libstdc++6.4.3-dev

```

> **auquicu said:**
> 
This is not a question about compiling C++ but about compiling old C++.

Not really, its a question of 1 - compiling C++ code that uses C libraries or 2- compiling C++ code that uses deprecated libraries. Case 1 is simple enough, just make sure you have the C libraries installed, however case two may require modifying the includes by removing the .h and adding the standard namespace to your code files.

---

### Post by auquicu on 2008-12-29
Hmm - looks like you did not read my original question.
That is precisely the answer of which I said that I had seen it many times.
I need something else.

(And after correcting libstdc++6.4.3-dev to libstdc++6-4.3-dev I found that all packages you mention were already at the latest version.)

On the other hand, maybe I can answer my own question. After installing gcc-4.1 and g++-4.1 I see that
 export CXX="g++-4.1"; ./configure; make
is fairly successful, and only requires minor source tweaks.
So gcc/g++-4.1 still works where gcc/g++-4.3 fails.

---

