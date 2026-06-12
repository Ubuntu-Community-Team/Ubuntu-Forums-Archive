---
title: "Installing CMDiag"
date: 2008-12-15
forum: General Help
---

### Post by GISJason on 2008-12-15
Anyone have any ideas what could be going wrong here... I'm trying to get cmdiag0.2 installed but it won't work for some reason... It ends without a error code or telling me what's wrong...


```

slim@devlap:~/Desktop/cmdiag-0.2$ make
g++ -Wall -O2  -c cmdiag.cpp
cmdiag.cpp: In function ‘int main(int, char**)’:
cmdiag.cpp:28: warning: deprecated conversion from string constant to ‘char*’
cmdiag.cpp:29: warning: deprecated conversion from string constant to ‘char*’
cmdiag.cpp:30: warning: deprecated conversion from string constant to ‘char*’
cmdiag.cpp:31: warning: deprecated conversion from string constant to ‘char*’
cmdiag.cpp:45: warning: deprecated conversion from string constant to ‘char*’
cmdiag.cpp:45: warning: deprecated conversion from string constant to ‘char*’
cmdiag.cpp:211: error: ‘strstr’ was not declared in this scope
make: *** [cmdiag.o] Error 1
slim@devlap:~/Desktop/cmdiag-0.2$

```

Does it look like some lib  / dependant is missing? if so please give me a clue.... As I'm still a linux n00b...

thx!!

---

