---
title: "can not execute program unless in directory?"
date: 2009-05-07
forum: General Help
---

### Post by kylegio on 2009-05-07
hello, i am trying to execute a program in ubuntu server edition. the program is located in /usr/local/bin

the program is just a simple little file server used for sharing files around the network. 

now if i change my directory (cd) to /usr/local/bin and execute the program (by simply typing the name) it starts up all is dandy.

however if /usr/local/bin is not my current directory, and i try to execute the program by typing /usr/local/bin/theserver (where theserver is the name of the program i am executing) it will not start.

the program i am trying to execute needs to run some lua scripts, and it returns an error "cannot open core/init.lua: No such file or directory"

the file 
/usr/local/bin/core/init.lua exists, and the program is able to launch so long as /usr/local/bin is my current directory, so i dont know why this problem is coming up, but it is stoping me from being able to launch the program with a demon because (of course) /etc/init.d/theserver start  just gives the "cannot open core....etc" error. 


any suggestions?
thanks in advance!

---

### Post by maheshasolkar on 2009-05-07
Can you try to add /usr/local/bin in your PATH environment variable, if it does not already exist? To do so, run the following:

```
  export PATH=$PATH:/usr/local/bin
```

To find out if it already exists in your path, you can try something like:

```
  echo $PATH
```

If that works, don't forget to add the 'export' line in your ~/.bashrc file, so that it is always set when you start a shell.

---

### Post by 123456789123456789123456 on 2009-05-07
> **kylegio said:**
> hello, i am trying to execute a program in ubuntu server edition. the program is located in /usr/local/bin

the program is just a simple little file server used for sharing files around the network. 

now if i change my directory (cd) to /usr/local/bin and execute the program (by simply typing the name) it starts up all is dandy.

however if /usr/local/bin is not my current directory, and i try to execute the program by typing /usr/local/bin/theserver (where theserver is the name of the program i am executing) it will not start.

the program i am trying to execute needs to run some lua scripts, and it returns an error "cannot open core/init.lua: No such file or directory"

the file 
/usr/local/bin/core/init.lua exists, and the program is able to launch so long as /usr/local/bin is my current directory, so i dont know why this problem is coming up, but it is stoping me from being able to launch the program with a demon because (of course) /etc/init.d/theserver start  just gives the "cannot open core....etc" error. 


any suggestions?
thanks in advance!

I wonder, sounds like for some reason, if you attempt to run the program using the command path, it starts looking for the init.lua file in /, which is file system, main directory., and not in /usr/local/bin/core/, like it should, however if you are in the correct directory, it knows where to look.  This sounds like, for some reason, the program was installed incorrectly, and for one user only.  Try using sudo /usr/local/bin/theserver, and see if it runs.
could you provide me with the permissions?
the output of command
ls -l /usr/local/bin/theserver
and ls -l /usr/local/bin/core/init.lua

---

### Post by kylegio on 2009-05-07
thanks for your replies,


yes the directory is in my $PATH
both /usr/local/bin and user/local/bin/theserver  are in the PATH 



```
ls -l /usr/local/bin/theserver
```
-rwxr-xr-x 1 root root 14195 2009-05-07 22:31 /usr/local/bin/theserver/theserver

```
-l /usr/local/bin/core/init.lua 
```
-rwxr-xr-x 1 root root 5721 2009-05-07 22:31 /usr/local/bin/theserver/core/init.lua



EDIT:
i can get it to work by simply writing a shell script that contains
```

cd /usr/local/bin/theserver
theserver

```

but that doesnt really help me where im trying to write a daemon and not just a startup script.

---

### Post by kylegio on 2009-05-09
this is still killing me its been two days of trying to figure it out and to no avail.


if you think you might have a solution please help!

---

### Post by Hobgoblin on 2009-05-09
Seems to be expecting a folder called core containing a file called init.lua in your current directory.

Try this

```

cd
mkdir core
cp /usr/local/bin/core/init.lua core/init.lua
theserver
```

---

### Post by soro2005 on 2009-05-09
Disregard, no news for you. Sorry!

---

### Post by lloyd_b on 2009-05-09
> **kylegio said:**
> this is still killing me its been two days of trying to figure it out and to no avail.


if you think you might have a solution please help!

Try this:```
export LUA_PATH=/usr/local/bin
theserver
```
As I understand it, the value of LUA_PATH tells Lua where to look for scripts.  If it's not set, *then* it looks for "core" in the current directory.

If this works, you can add that "export..." line to "~/.bashrc" for your convenience.

Lloyd B.

---

### Post by kylegio on 2009-05-09
no avail, i tried many variations of that making LUA_PATH all sorts of different things, none worked
also before doing this i did 

echo $LUA_PATH 

and it was blank, should it have had something to begin with?

i have tried setting LUA_PATH to 
/usr/local/bin
/usr/local/bin/core
...etc variations on that

---

