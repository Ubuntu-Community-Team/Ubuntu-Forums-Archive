---
title: "Octave 3.0 - Can't run .m files"
date: 2009-05-06
forum: Education &amp; Science
---

### Post by rg_stephens on 2009-05-06
I can't get even the simplest program to run in Octave 3.0. Version 2 seemed ok. It runs most of the files I created in school last year in MATLAB, but if I try to write a file it doesnt' run, regardless of the file extension. 

For example, I open Kate, or any other editor and type:
```
% Test file
disp('This is a test')
```

I save the file as *testfile*, and this is the result I get when I try to run it:

```
octave:1> testfile
error: `testfile' undefined near line 1 column 1
```

---

### Post by Gilabuugs on 2009-05-06
[PHP]% test file
disp('This is a tester File::::!')
A = [3 4 5
     6 7 8
     9 2 1]
[/PHP]

```
$ octave -q test.m 
This is a tester File::::!
A =

   3   4   5
   6   7   8
   9   2   1

```
**Does testfile.m at the prompt work?**

Also make sure you are in the directory you saved it in pwd and cd work like normal in octave

---

### Post by rg_stephens on 2009-05-06
Hey, it almost worked that time. Sometimes it works, and sometimes it doesn't. Last night I spent hours and couldn't get anything to run unless I copied and pasted into the octave window.

```
octave:1> testfile.m
This is a tester File::::!
A =

   3   4   5
   6   7   8
   9   2   1

error: can't perform indexing operations for <unknown type> type
```

---

### Post by rg_stephens on 2009-05-07
Ok, this time I'm certain that I'm in the correct directory. I type a file using gedit, save it to the 'octave' folder, run 'ls' to make sure it's there, and when I try to run it, ...

```
% Test file
m = 1
x = m+1;
disp(x) 
```

```

octave:3> Adding.txt 
error: `Adding' undefined near line 3 column 1
```

Also, the *exist* command doesn't work. Am I missing something?
octave:5> exist Adding.txt
parse error:

  syntax error

>>> exist Adding.txt
               ^

---

### Post by ahmatti on 2009-05-09
M-files need to have .m extension... Name your file to Adding.m and it should work.

---

### Post by stallinux on 2011-01-28
Might be a problem with the **file extension**. Octave does not run **.M** files. Must be **.m**
I consider this 'system feature' an (annoying) bug. (My DOS based data acquisition system unavoidably generates .M files).
People from the W#%dows environment will have more difficulty with getting used to this this. Linux is case sensitive, also in the file extension.

---

