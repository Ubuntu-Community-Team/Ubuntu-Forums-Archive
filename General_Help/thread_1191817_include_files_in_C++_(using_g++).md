---
title: "include files in C++ (using g++)"
date: 2009-06-19
forum: General Help
---

### Post by wbest on 2009-06-19
Okay, so I don't want to do a whole 
g++ -I /path/for/include1 /path/for/include2 /path/for/include3... program.cpp
 
Just to compile a c++ program.  So I was hoping that there may be a file or folder in which I can place multiple include paths.  I think I probably have several header files to include over severaly programs, all of which may have to be compiled together (one big project) and I don't want to set up an extensive -I set of tags and such.
 
So yeah, is there one file or folder that I can create or edit to put all the paths to check so it will do it all automatically?

---

### Post by DGortze380 on 2009-06-19
> **wbest said:**
> Okay, so I don't want to do a whole 
g++ -I /path/for/include1 /path/for/include2 /path/for/include3... program.cpp
 
Just to compile a c++ program.  So I was hoping that there may be a file or folder in which I can place multiple include paths.  I think I probably have several header files to include over severaly programs, all of which may have to be compiled together (one big project) and I don't want to set up an extensive -I set of tags and such.
 
So yeah, is there one file or folder that I can create or edit to put all the paths to check so it will do it all automatically?

I don't know about having automatically include a directory, but to cut down on the paths...

... put all the file you want to include into a folder. Any folder. You choose.

cd to that directory

now you only need to type the file names for each include and not a full path.

EDIT: After a quick google search, looks like you may be looking for /usr/local/gcc.../include ??

---

### Post by wbest on 2009-06-19
Yeah, what I did was to create a folder in the current working directory that I called *include*
I then just said g++ -I incldue foo.cpp
 
That seems to be workin all well now.

---

