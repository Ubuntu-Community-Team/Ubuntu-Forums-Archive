---
title: "Geany/G++ problems"
date: 2009-05-17
forum: General Help
---

### Post by brianfast on 2009-05-17
Ok - 2 problems

When I compile a C++ file in geany and then execute it from within genay doesn't run. Some script error. Anyone run into this? I am using ubuntu 64.

```
./geany_run_script.sh: 5: ./untitled2: not found


------------------
(program exited with code: 127)
Press return to continue



```

Also, on the command line when I try an run my programs I get "permission denied error" wtf?

---

### Post by mjheagle8 on 2009-06-04
i am having the same problem with the first one. 
for the second, sounds like you haven't made it executable.  try ```
chmod +x <filename>
```

---

### Post by Mirge on 2009-06-04
Make sure you "build" the C/C++ source rather than just compiling. Compiling will generate a .o file... building will generate the executable.

---

### Post by Niedzwiadek on 2012-10-30
I have got the same problem.  I think this is about directories configuration in Geany.

The simple cpp program has been successfully** build (F9) **in Geany.  The status window said:
[FONT=Courier New]
[COLOR=PaleTurquoise][COLOR=Blue]g++ -g -Wall -o "cpp-hello" "cpp-hello.cpp" (in directory: /home/pawel/Programs/cpp/nida)
Compilation finished successfully.[/COLOR]
[/COLOR][/FONT]
Then when I tried to execute it from IDE (using F5) I 've got the message:

[FONT=Courier New][COLOR=Blue]./geany_run_script.sh: 5: ./cpp-hello : not found
[/COLOR][/FONT]
Obviously  [FONT=Courier New]cpp-hello[/FONT] file **existed** and was located in the same directory as source [FONT=Courier New]cpp-hello.cpp[/FONT] 

I wrote and build a similar program  [FONT=Courier New]c-hello [/FONT]in C. 
[FONT=Courier New][COLOR=Blue]gcc -Wall -o "c-hello" "c-hello.c" (in directory: /home/pawel/Programs/cpp/nida)
Compilation finished successfully.
[/COLOR][/FONT]
Source and executable files were in the same folder and I could execute it from IDE with no errors.
So my question is where and how should I configure Geany in order to be able to execute cpp programs from IDE?

---

