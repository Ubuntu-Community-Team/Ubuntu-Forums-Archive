---
title: "c++ - geany problem?"
date: 2008-12-09
forum: General Help
---

### Post by Len Tyree on 2008-12-09
solved:

installed geany couple months ago; trying to learn c++ language; wrote little c++ program (the usual 'one' for first timers (Hello World)); got error on 'cout' statement?  says 'cout' was not declared in the scope?

coded as:

#include <iostream>

int main()
{
  cout << "Hello World in C++!\n";
  return 0;
}

manual says 'cout' is located in the iostream lib?

so what am i doing/not doing to cause this?
how do i look in iostream to see if it is there?
i would show you the code if i knew how.

thanks for any help.  len tyree.[http://ubuntuforums.org/images/icons/icon5.gif](http://ubuntuforums.org/images/icons/icon5.gif)

---

### Post by phinullfermata on 2008-12-09
I also had this problem with c++.  You should use a namespace.  Like this:

```
#include <iostream>
using namespace std; // this is what you're missing

int main ()
{
  cout << "Hello World!";
  return 0;
}
```

---

### Post by Len Tyree on 2008-12-09
thanks much, phinullfermata.
worked fine.

len tyree.[http://ubuntuforums.org/images/icons/icon7.gif](http://ubuntuforums.org/images/icons/icon7.gif)

---

