---
title: "Odd message in the console..."
date: 2005-09-11
forum: Desktop Environments
---

### Post by YourSurrogateGod on 2005-09-11
After I openned gedit in order to do some programming, I kept getting the below error for some reason, attempt to put segment into something. Why is this happening? Is gedit screwed up somehow?
```
andrew@ool-182c85b2:~$ cd Desktop/My\ Documents/Programming/C++/making_graph/
andrew@ool-182c85b2:~/Desktop/My Documents/Programming/C++/making_graph$ ls -l
total 244
-rw-r--r--  1 andrew andrew    159 2005-09-09 18:24 graph.cpp
-rw-r--r--  1 andrew andrew    114 2005-09-09 15:12 graph.cpp~
-rw-r--r--  1 andrew andrew   1679 2005-09-09 18:23 graph.h
-rw-r--r--  1 andrew andrew   1670 2005-09-09 16:45 graph.h~
-rwxr-xr-x  1 andrew andrew 221842 2005-09-09 16:39 main
-rw-r--r--  1 andrew andrew    148 2005-09-09 18:24 main.cpp
andrew@ool-182c85b2:~/Desktop/My Documents/Programming/C++/making_graph$ gedit graph.cpp main.cpp graph.h&
[1] 8822
andrew@ool-182c85b2:~/Desktop/My Documents/Programming/C++/making_graph$ *** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice
*** attempt to put segment in horiz list twice

andrew@ool-182c85b2:~/Desktop/My Documents/Programming/C++/making_graph$ ls -l
total 248
-rw-r--r--  1 andrew andrew    153 2005-09-11 13:13 graph.cpp
-rw-r--r--  1 andrew andrew    159 2005-09-09 18:24 graph.cpp~
-rw-r--r--  1 andrew andrew   1674 2005-09-11 13:13 graph.h
-rw-r--r--  1 andrew andrew   1679 2005-09-09 18:23 graph.h~
-rwxr-xr-x  1 andrew andrew 221842 2005-09-09 16:39 main
-rw-r--r--  1 andrew andrew    142 2005-09-11 13:13 main.cpp
-rw-r--r--  1 andrew andrew    148 2005-09-09 18:24 main.cpp~
andrew@ool-182c85b2:~/Desktop/My Documents/Programming/C++/making_graph$ g++ -g -o main main.cpp graph.cpp

```

---

