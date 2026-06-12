---
title: "getting bash command not found"
date: 2008-02-29
forum: Desktop Environments
---

### Post by yoavbenarie on 2008-02-29
Hello,

I wrote a c++ program, when ever i try to run it i get bash: filename: command not found
the file has the right permissions.

what can i do to solve the problem? what is the problem?

thanks
yoav

---

### Post by Crooksey on 2008-02-29
How are you running it, please post exact erros.

---

### Post by yoavbenarie on 2008-02-29
I compiled it with a Makefile got an executable file named maze,
then i execute it :

yoav@yoav-desktop:~/workspace/Computer graphics/ex1$ make
g++ -Wall -c -O2 -I/usr/include -I/usr/X11R6/include maze.cpp 
g++ -Wall -Wno-deprecated -L/usr/lib -lm -lglut -lGL -lGLU -ldl -L/usr/X11R6/lib maze.o -o maze
yoav@yoav-desktop:~/workspace/Computer graphics/ex1$ maze
bash: maze: command not found

thanks

---

### Post by taurus on 2008-02-29
```
./maze
```

---

### Post by spupy on 2008-02-29
If you want to run executables from the current directory, you need to append ":." at the end of your PATH. But the command from **taurus** must work.

---

### Post by El Viejo Lobo on 2008-04-04
I am trying to make gilbc work but this is what I got
The file glibc-2.7.tar.gz in saved on desktop
xxxx@yigal-laptop:~$ cd Desktop
xxxc@yigal-laptop:~/Desktop$ tar-zxvf glibc-2.7.tar.gz
***[I]bash: tar-zxvf: command not found*[/I]**
xxxx@yigal-laptop:~/Desktop$ ./maze
bash: ./maze: No such file or directory
@yigal-laptop:~/Desktop$ 
I tryed .-maze and again failed.
Thanks for the help' I know it will come..

---

### Post by mcduck on 2008-04-05
You are missing a space in the command. 

It's "tar -xzvf", not "tar-xzvf" ;)

---

### Post by El Viejo Lobo on 2008-04-05
Thanks a lot    :lolflag:  I may need new Eye glasses

---

