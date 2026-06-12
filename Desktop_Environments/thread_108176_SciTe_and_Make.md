---
title: "SciTe and Make"
date: 2005-12-25
forum: Desktop Environments
---

### Post by larry on 2005-12-25
Dear All,
I am starting to program in C++. For my needs, something as easy as SciTe would be probably fine. As a complete beginner to C++, I am now working with Gedit as a pure editor and the terminal.
I am also using this make file compiling the source code and linking it against the librecipes.a library (which is to be found in the same directory as the source code):

g++ -c -O2 run_all_examples.cc
g++ run_all_examples.o   -L. -lrecipes  -o run_all_examples
./run_all_examples


but SciTe would rather use as a default the command:

g++ -pedantic -Os -fno-exceptions -c run_all_examples.cc -o run_all_examples.o


How do I change that to the make I need? How can I do the same with other IDE (Kdevelop, Anjuta) and Emacs?

Best Regards and merry Xmas to everybody.

Larry

---

