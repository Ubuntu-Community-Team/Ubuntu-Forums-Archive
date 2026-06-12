---
title: "g++ errors"
date: 2009-05-16
forum: General Help
---

### Post by Sidhiel on 2009-05-16
I installed the g++ packages from Synaptic, but every time I go to compile a program it gives me error messages. cout was not declared in this function. I have the iostream #included, and I can't figure out what's going on...

---

### Post by chellrose on 2009-05-16
Can you post the line of code that's generating the error?

Edit: A thought.  Are you using namespace std?

```

#include<iostream>
using namespace std;

```

If not, then you need to use std::cout.

---

### Post by Sidhiel on 2009-05-16
Yep, that did it...thanks. ^_^'

---

