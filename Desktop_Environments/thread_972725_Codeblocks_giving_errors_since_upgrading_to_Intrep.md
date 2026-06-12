---
title: "Codeblocks giving errors since upgrading to Intrepid"
date: 2008-11-06
forum: Desktop Environments
---

### Post by SimbaSpirit on 2008-11-06
Alright, I know this sounds like I'm asking for c++ help, but this only started after I updated to Intrepid (which updated codeblocks and a couple of its corresponding libs).

Real simple test:

```

#include <iostream>
#include <string>
#include <sstream>
#include <cmath>
using namespace std;

int main(){
system("clear");
cin.ignore( numeric_limits <streamsize> ::max(), '\n' );
    return 0;
}

```

Errors:
```

=== Debug ===
In function ‘int main()’:
error: ‘system’ was not declared in this scope
error: ‘numeric_limits’ was not declared in this scope
error: expected primary-expression before ‘>’ token
error: no matching function for call to ‘max()’
=== Build finished: 4 errors, 0 warnings ===|

```

This all worked prior to intrepid. I tried uninstalling codeblocks, re-downloading codeblocks and libs from the website, and reinstalling (ignoring the "newer version exists" warnings).

Is anyone else having this problem, or does anyone else know enough about the way codeblocks works to suggest a fix? 
Everything compiles and runs fine in windows still.

Thanks,
-SS

---

### Post by SimbaSpirit on 2008-11-07
Can anyone verify this problem??

I went as far as completely formatting/reinstalling ubuntu, and installing everything via apt-get from official repositories, so as far as I can tell there isn't much I could have done to fubar anything.

Also worth mentioning: I installed geany from apt-get and it returns the same problem, so I really don't think it's a code::blocks problem.

If anyone needs a log or anything let me know, I'll be glad to give it to you. I hate having to boot into windows just to learn c++ =P

---

