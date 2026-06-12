---
title: "[SOLVED] Path"
date: 2006-06-15
forum: Desktop Environments
---

### Post by dstein on 2006-06-15
In Windows, I am familiar with the path variable which allows a user to setup which folders programs are always accessible from the command prompt. I imagine there must be similar setup in Linux, cause when I type gedit at any time at the command prompt, a text editor opens. Can someone either refer me to an article about this is achieved in Linux, in case I wanted to add a directory to path. Thanks.

---

### Post by taurus on 2006-06-15
You can do that by adding these two lines to the end of your ~/.bashrc.
```

PATH=$PATH:/new_path:/another_path
export PATH

```

---

### Post by dstein on 2007-02-02
How can I see what programs are in what I am referring to Path (I am not sure what it is called in Linux). As a newbie, the preceding instructions are a little unclear to me, as I do not know why or what the suggestion actually does. Thanks.

---

### Post by tcrroadie on 2007-02-02
Maybe this will help explain the PATH variable a little more for you.  

**Taken from [Debian User Reference Manual, Chapter 6]("http://www.debian.org/doc/manuals/user/ch6.html")**

6.2.2 How Linux finds commands

When you type in a command name, Linux has to find the file which contains the program you want to run. This is how it does it:

The first word of what you type in is the command[3] itself. If this contains a slash character (/) the whole command is taken to be a path, either absolute (if it starts with /) or relative to the current directory. The file indicated by that path is used, provided that it exists, that it is executable and (in the case of a script) that it is readable.

If the command does not contain a slash, the shell searches for it in your current search path. This is a list of directories, separated one from another by colons. The command search path is held in the environment variable PATH: type echo $PATH to see what it is. For example,

     
     $ echo $PATH
     /usr/bin:/bin:/usr/bin/X11:/usr/local/bin:/usr/games:/home/olly/bin

Each directory is searched in turn, starting at the beginning of the list. If a match for the name is found, the shell also considers whether the file found is executable (and readable, if it is a script). As soon as such a match is found, the search stops[4]. This is why new programmers often have trouble getting their first program to run. They frequently call it test and run it without a path; the shell finds the system program test first and runs that instead.

If you need to change your path, you should add the new directories to the end of the list; the current directory (.), if it is included at all, should go last of all[5]. The command to use is export PATH=$PATH:new_directory[6] . 

Hope this helps to answer your question.

---

