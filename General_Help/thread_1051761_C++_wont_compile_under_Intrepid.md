---
title: "C++ wont compile under Intrepid"
date: 2009-01-27
forum: General Help
---

### Post by piratebill on 2009-01-27
Ok, this is more than likely me not being able to get away with poor coding habits than a bug.  I just installed intrepid on my laptop today (along with build-essentials).  I have a few c++ programs that I had created in the past and wanted to compile them for the new system.  the code looks something like this:

#include <iostream>
#include <string>
using namespace std;

int main(int argc, char* argv[])
{
    system("clear");
    string cmd;
 /*
   ....................
not going to include the until app for time
...........................
etc. */
}

In the past (Hardy, fiesty and so forth code like this would compile just fine.  Now it tells me, "‘system’ was not declared in this scope"

I have never had to declare system before.  I have a few c++ programs that use the system call.  I could (and probably should) just turn these apps into perl scripts, but that is besides the point.  Other programs I have written that don't use system compile fine.  Did something break C++ or is intrepid just not letting me get away with crap?

I am also seriously tired right now, so it is very possible that I am just missing something simple

---

### Post by Captain Giraffe on 2009-01-27
#include<cstdlib>


/Captain

---

### Post by piratebill on 2009-01-27
Thanks Captn'
Worked like a charm.

---

