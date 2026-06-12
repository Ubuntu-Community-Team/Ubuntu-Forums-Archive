---
title: "How to execute an Executable?"
date: 2005-07-02
forum: Desktop Environments
---

### Post by Prudentissimus on 2005-07-02
I have this executable called VGB... (not windows type)

... how do I run it in Terminal... if i do VGB, it says command not found.

---

### Post by mohaham on 2005-07-02
open up the terminal(console):
goto the directory where this file is located and type the following:
chmod +x VGB

then type:
./VGB

---

### Post by argux on 2005-07-03
Hi, I'll explain this a bit deeper for those who might wonder why this works. If I'm mistaken about something, please correct me. I'm not at all what you might call a guru!

If you want to execute a program or a script, you need two things. To have permission to execute it, and to tell the shell where it is.

First, you make it executable (have permissions to execute it). You do this with the command chmod. For example, if you are the owner, you can make the file 'foo' executable like this:

```
you~$ chmod +x foo
```

This means, "add executable permissions to foo".

If you want it to be executable only by the owner, or the group, add u or g before the +:

```
you~$ chmod u+x foo
```


Now, to execute your program the shell needs to know where it is. Normally, programs are located in these directories: /bin , /sbin , /usr/bin , /usr/sbin , and others. Because these are almost always where most programs are located, by default they are stored in a variable called $PATH. Like that, everytime you want to execute a program, for example, "less", the shell will for it in all the directories stored in PATH until it finds it (it will find "less" in /usr/bin).

If you want to execute "foo" but it's located in a directory that doesn't appear in $PATH, the shell won't know how to find it and will say so. You can add this directory to your path variable, and everything from that directory that is executable will work by just calling its name, but the quick way is by telling the shell where it is.

```
you~$ /home/you/foo
```

Now that you're telling the shell where your program is, it is happy and will execute it.

In MS-DOS, if there's a program in the same directory where you are, you can execute it like this:


```
C:\> foo
```

and it will work, but in linux,


```
you~$ foo
```

doesn't work, even if you are in that same directory! That's because your current directory isn't in your path. Even if it's right there for you, the shell doesn't care, it's not looking there. In MS-DOS, the directory "." (that's a period) is in the path. The . directory stands for "current directory". So, if . is in your path variable, you can execute anything that is in the directory where you're currently working. 

So, if you want to execute a program that's right there in the same directory as you are, tell it to:


```
you~$ ./foo
```

The shell replaces . with wherever you are.

Why then isn't this directory in your path in Ubuntu? Because it is dangerous. Imagine you or a cracker somebody else downloads a program that wants to delete everything in your hard drive. If you're not careful, you or the cracker could execute it without knowing the path and your hard drive (or at least your home directory) could be deleted. This, fork bombing (which I don't really know much about), and buffer overflows are examples of how adding . to your path could be used against you by malicious people.

This is all I wanted to say. I hope this helps whoever needs it.

More info:
man chmod - changing permissions
man chown - changing owners of files and directories
man bash - very long, but very enlightening

---

### Post by pdpi on 2005-07-03
adding a rather basic reccomendation to the thread: make sure you're capitalizing correctly. Windows handles capitalization in a very lax way -- it keeps it, but doesn't require it. So if you name a file "fOo", it will keep the name "fOo", but you can also refer to it as "foo", "Foo", "FOo", "foO", "FoO", etc.

Linux enforces a strict capitalization scheme. If the file's foo, it only answers to being called foo. Nothing else will work.

---

### Post by Morimando on 2005-07-03
you know, it might be a good idea to add such info to a "basics" sticky. Especially here in the Ubuntu forums, there are many "first timers" in terms of using Linux underways, and well, we could need a small "basic" tutorial..

---

### Post by t2kburl on 2005-07-03
except that a "basic" tutorial on Linux wouldn't be very small at all    lol

---

