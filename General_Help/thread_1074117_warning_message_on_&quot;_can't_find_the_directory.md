---
title: "warning message on &quot; can't find the directory&quot;"
date: 2009-02-18
forum: General Help
---

### Post by poonam on 2009-02-18
i have included the following header files...........
#include<unistd.h>
#include<stdlib.h>
#include<curses.h>
#include<string.h>
#include<ctype.h>
when i run my program in linux it says "can't find the path"
plz tell me what may be the problem :(

---

### Post by poonam on 2009-02-18
i have included the following header files...........
#include<unistd.h>
#include<stdlib.h>
#include<curses.h>
#include<string.h>
#include<ctype.h>
when i run my program in linux it says "can't find the path"
plz tell me what may be the problem

---

### Post by snova on 2009-02-19
Install the **build-essential** and **libncurses5-dev** packages.

If that doesn't work, please post the precise error.

---

