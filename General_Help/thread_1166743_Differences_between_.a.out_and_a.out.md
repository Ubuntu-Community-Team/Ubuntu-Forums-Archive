---
title: "Differences between ./a.out and a.out"
date: 2009-05-22
forum: General Help
---

### Post by gasto on 2009-05-22
Hi there,

I am trying to execute a recently compiled .c file, which is the classical helloworld example. I have the a.out. Somewhere I saw to execute it:

chmod +x a.out ./a.out

Can someone explain this?

Thanks in advance.

---

### Post by keplerspeed on 2009-05-22
./ before an executiblle will execute that file in that directory. ./just means 'in this directory'. If you just run a.out, the terminal will see that as a command, and look in your path for that file, ie /bin. For example, the ls command to list the files in a directory is just a little program. when u issue the ls command, ubuntu looks in your path, and the ls program is in the /bin/ directory, of which is in your path. If u want to add a directory to your path, add it  to the file /etc/environment

Cheers

---

### Post by CatKiller on 2009-05-22
Those are two separate commands. It might have been ```
chmod +x a.out
./a.out
``` or ```
chmod +x a.out && ./a.out
```The first command makes the file executable. The second runs it. To run an executable, you need to specify its full path, like /usr/bin/command. A list of commonly-used locations is stored as the $PATH environment variable, so if the executable is in one of those locations the system will expand the path to include the location of the executable, meaning that you can just type the name of the file. ./ is a shortcut that expands to "the current directory." /../ expands to "the parent directory." ~/ expands to "this user's Home directory."

---

### Post by keplerspeed on 2009-05-22
Sorry, just re read your post. I believe the command:

chmod +x a.out ./a.out

will make the file a.out executible, and then run it. so,

chmod +w a.out ** this will change the permissions of the file, making it executible
./a.out ** this will run the executible

doing it in one line is just easier!

---

### Post by ymo on 2009-05-22
**$** chmod +x a.out ./a.out

should actually read

**$** chmod +x a.out ; ./a.out

if you want to do both commands on the same line or

**$** chmod +x a.out
**$** ./a.out

on two lines

---

### Post by colau on 2009-05-22
./ means the current directory.
For 
```

chmod +x ./a.out

```
The a.out file must be on the current directory.
```

chmod +x a.out

```
There a.out would be searched in the $PATH ?

---

### Post by CatKiller on 2009-05-22
> **colau said:**
> ./ means the current directory.
For 
```

chmod +x ./a.out

```The a.out file must be on the current directory.
```

chmod +x a.out

```There a.out would be searched in the $PATH ?

No. Without a path most commands will interpret a file name variable to be in the current directory. The commands that you've listed will both be interpreted the same way.

The $PATH is just for locating executable files easily.

---

### Post by gasto on 2009-05-22
Thanks for the tips ladies.

---

