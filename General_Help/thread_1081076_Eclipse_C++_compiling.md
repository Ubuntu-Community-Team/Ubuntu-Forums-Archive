---
title: "Eclipse C++ compiling"
date: 2009-02-26
forum: General Help
---

### Post by sacredsunder on 2009-02-26
I am trying to use C++ for a class assignment on recursion instead of using Java, and i have installed the CDT for eclipse and I have gcc and g++. Ive spent the last hour or two messing around with eclipse trying to get it to just compile for me and it just wont do it. I finally gave up and used gedit and the command line just to make sure I wasn't crazy. 

Every time I hit run in eclipse it used to bring up the run config window for c/c++ local app. But I think I messed it up, and now when I hit it all it does is start a new instance of eclipse. This is getting kind of frustrating. Does anyone have any help? please?:confused:

---

### Post by dzark on 2009-02-26
Try ```
rm -R ~/.eclipse
```

then ```
sudo aptitude reinstall eclipse
```

---

### Post by sacredsunder on 2009-02-26
```
Exec_tty error:Cannot run /home/***/Recursive/Test.cpp
Exec_tty error:Cannot run /home/***/Recursive/Test.cpp
Exec_tty error:Cannot run /home/***/Recursive/Test.cpp
```

It stopped opening eclipse but now it says this. From what I can tell(probably not that much) its trying to run the .cpp as if it was already compiled... I don't really get it :?

---

### Post by dgoosens on 2009-02-26
I'm no C++ expert... but you might want to give Netbeans 6.5 a try...

Also, are you sure your C++ compiler is not malfunctioning?

---

### Post by jespdj on 2009-02-26
Do you have the C++ compiler installed? Install the package **build-essential**
```
sudo apt-get install build-essential
```
It installs g++, header files for the standard libraries and other tools that are necessary for compiling C and C++ programs.

---

### Post by dulahdaglace on 2009-02-26
im having the same problem/same error message... i tried reinstalling eclipse but nothing changed... there is nothing wrong with my c/c++ compilers because i use them from the command line... i dont know if i have a setting wrong when i try to run it..?

---

### Post by dulahdaglace on 2009-02-26
bah i should have searched the french forums first obiwankennedy said that the problem was that the user is trying to execute a source file and not the makefile... anyways, when i went under debug, i found the one called filename instead of the filename.o that i was trying to execute... hope that helps u

---

### Post by sacredsunder on 2009-02-26
Wow this got a lot of replies, thanks everyone!

Yes I'm sure my compiler is working, I can compile from the command line.(Also I've tried Netbeans before but as much as I wanted to like it I just didn't get along with it)

Yeah, I already had build-essential and g++ installed.

dulahdaglace, could you please explain what you did in a little more detail? I don't even have the filename, all i have is a filename.cpp and a filename.h.

---

### Post by toownzie on 2009-04-05
I had the same error, i fixed it by giving my cpp source file an other name, different from the executable..

---

### Post by qetuR on 2010-07-22
Got the same error, and I just renamed the file. Tried to run it, and it worked. Then I tried to rename the file to the original name, and that worked to.

Wonder what kinda crazy bug that was, but eitherway, it works!

---

### Post by Uatek on 2011-03-23
In my case the problem was that the generated executable had no execution permission, maybe because I use two environments that I synchonize and the executable file was compiled in one environment and when rebuilt on the other one it kept the original permissions after synchronization (without execution permission).

A chmod +x <executable file> solved the problem in my case.

---

