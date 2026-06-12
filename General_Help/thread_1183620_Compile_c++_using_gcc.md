---
title: "Compile c++ using gcc"
date: 2009-06-10
forum: General Help
---

### Post by wbest on 2009-06-10
Alright team, here's the challenge:
I need to compile a c++ using gcc, so I need the options to do so.  I can't seem to find them online as everything only talks about g++.
g++ is not an option for use, only gcc.  The long and short of why is that the network security at my work won't let me download the necessary packages.

---

### Post by ActiveFrost on 2009-06-10
Where's the problem ? If you can't install gcc ( download/install ), you can't compile it - isn't that clear enough ?

---

### Post by abhilashm86 on 2009-06-10
i guess you don't have sufficent headers and package information........
in terminal type 
```

sudo apt-get install build-essential

```

in ubuntu 8.10 and jaunty, most of compilers are in built, so do it in this way...............

---

### Post by abhilashm86 on 2009-06-10
maybe better to compile c++ programs using g++,
c programs using gcc or cc

so whats your intention of compiling c++ using g++??

---

### Post by nikhilk on 2009-06-10
You can use gcc to compile and link C++ apps but you MUST have the required C++ libraries and headers.
You can explicitly instruct gcc to use the C++ standard library when compiling C++ apps (assuming the library and header paths are correctly setup)
e.g.
```
gcc t.cpp -o test -lstdc++
```

---

