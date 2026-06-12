---
title: "Can't cross-compile"
date: 2009-01-26
forum: General Help
---

### Post by Amaroq on 2009-01-26
Hey guys, I'm trying to compile executables than can run on windows/wine. I installed the three mingw32 packages, but when I try to compile the simplest of code, the compiler gives me errors.

Code:
```
#include <stdio.h>
using namespace std;

int main()
{
        cout << "Hello World!" << endl;
        return 0;
}
```

Errors:
```
i586-mingw32msvc-g++ -o test test.cpp
test.cpp: In function ‘int main()’:
test.cpp:6: error: ‘cout’ was not declared in this scope
test.cpp:6: error: ‘endl’ was not declared in this scope
```

---

### Post by Taras.M.K on 2009-02-07
cout has nothing to do with <stdio.h>
try to add
#include <iostream>

---

### Post by Amaroq on 2009-02-07
HAHA! Wow, I'm rusty. Thank you, it worked.

---

